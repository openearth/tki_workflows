# Argo Workflows for TKI

Deze repository bevat alle Argo workflows die zijn ontwikkelt als onderdeel van werkpakket WP3 - Cloud computing als onderdeel van het TKI project: https://publicwiki.deltares.nl/pages/viewpage.action?pageId=185140218

Het doel van het project D-HYDRO GUI, Visualisatie & Cloud is om GUI essentiële componenten te ontwikkelen voor de modules van de D-HYDRO Suite 1D2D, nieuwe vormen van visualisatietechnieken te ontwikkelen voor de D-HYDRO Suite 1D2D simulatieresultaten én om een workflow te ontwikkelen waarmee D-HYDRO Suite 1D2D simulatieberekeningen tezamen met de juiste voor- en nabewerking “cloud ready” worden.

De GUI componenten die we in dit project willen ontwikkelen zijn de functies en interfacing scripts van de D-HYDRO Suite 1D2D modules. Dit betreft essentiële modules zoals D-Flow FM, D-Hydrology en D-RTC, die we via de grafische user-interface (GUI) van D-HYDRO Suite 1D2D voor de eindgebruiker toegankelijk maken.

De visualisatietechnieken die we in dit project willen ontwikkelen bestaan uit innovatieve visualisatietools waaronder 3D web visualisatie en mogelijke AR/VR weergave van modelresultaten van D-HYDRO Suite 1D2D. Daarnaast breiden we huidige visualisatie en inspectiefunctionaliteiten uit in de D-HYDRO Suite 1D2D GUI.

Met de ontwikkelingen rondom het “cloud ready” maken, verkennen we de essentiële bouwstenen om D-HYDRO Suite 1D2D technisch geschikt te maken voor Cloud simulaties. Figuur 1 toont 6 bouwstenen die noodzakelijk zijn voor een succesvolle inzet van D-HYDRO Suite 1D2D in een cloud omgeving. Voor elk van deze aspecten verkennen we de configuratieruimte voor optimale inzet van de simulatiesoftware. Dit vereist gedetailleerde analyse van het functioneren van D-HYDRO Suite 1D2D in een publieke cloud omgeving en een kader om zorgvuldig een afweging te maken tussen bijvoorbeeld kostenbeheersing versus performance.

# Requirements

Voor de Argo workflows zijn een aantal requirements voor het kunnen draaien van 

Kubernetes Cluster: Zorg ervoor dat je een werkende Kubernetes-cluster hebt waarop je Argo Workflows kunt uitvoeren. Dit kan een lokale cluster zijn, bijvoorbeeld Minikube, of een cloudgebaseerde oplossing zoals Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), of Microsoft Azure Kubernetes Service (AKS). Deze workflows maken gebruik van AWS EKS maar kunnen relatief makkelijk omgezet worden voor andere cloud vendors.

Argo geïnstalleerd: Zorg ervoor dat Argo geïnstalleerd is in je Kubernetes-cluster. Dit omvat zowel Argo Workflows voor het beheren van workflows als Argo Events (indien nodig) voor het afhandelen van gebeurtenissen die triggers kunnen zijn voor workflows: https://argoproj.github.io/workflows/

Container Images: Zorg ervoor dat alle containerimages die in je workflows worden gebruikt, beschikbaar zijn voor het Kubernetes-cluster waarop je ze wilt uitvoeren.

Resource Nodes: Zorg er voor dat er geschikte processing nodes zijn die genoeg geheugen hebben om je applicaties te kunnen draaien. Overweeg de resourcevereisten en -limieten voor je workflows en zorg ervoor dat je Kubernetes-cluster voldoende resources heeft om deze uit te voeren. Dit omvat zaken als CPU, geheugen en opslagruimte. Voor de Argo workflow die gebruik maakt van Spot nodes in AWS EKS moeten deze nodes eerst toegevoegd worden: https://ec2spotworkshops.com/using_ec2_spot_instances_with_eks.html

# Het uitvoeren van een Argo Workflow

Workflow indienen: Gebruik het argo submit-commando om je workflow in te dienen bij het Argo-systeem. Dit commando neemt het pad naar je YAML-bestand als argument. Bijvoorbeeld:

argo submit my-workflow.yaml

Workflow status controleren: Gebruik het argo list-commando om de status van je workflow te controleren. Hiermee kun je zien of je workflow succesvol is ingediend en wordt uitgevoerd. Bijvoorbeeld:

argo list

Workflow-uitvoer bekijken: Gebruik het argo logs-commando om de uitvoer van je workflow-stappen te bekijken. Hiermee kun je zien welke acties zijn uitgevoerd en eventuele fouten opsporen. Bijvoorbeeld:

argo logs <workflow-naam>

Workflow verwijderen (optioneel): Als je je workflow wilt stoppen of verwijderen, kun je het argo delete-commando gebruiken. Hiermee wordt de workflow gestopt en worden eventuele bijbehorende resources vrijgegeven. Bijvoorbeeld:

argo delete <workflow-naam>
