#  Devops Project 2 
## Objectif

Déploiement d'une application Node.js dans un pipeline Jenkins

# Introduction

# La Philosophie DevOps

Le DevOps offre un framework conçu pour dynamiser et améliorer le développement d'applications et accélérer la mise à disposition de nouvelles fonctionnalités, de mises à jour logicielles ou de produits.

Il favorise la communication, la collaboration, l'intégration, la visibilité et la transparence continues entre les équipes chargées du développement d'applications (Dev) et celles responsables des opérations IT (Ops).

Cette relation plus étroite entre Dev et Ops se reflète dans chaque phase du cycle de vie DevOps : planification logicielle initiale, codage, développement, test, publication, déploiement, opérations et surveillance continue. Elle génère de façon constante des retours clients, ce qui renforce le potentiel d'amélioration lors du développement, des tests et du déploiement. La publication accélérée et permanente des modifications ou ajouts de fonctionnalités en est un exemple.

Les objectifs du DevOps s'articulent autour de quatre catégories : culture, automatisation, mesure et partage. Dans chacun de ces domaines, les outils DevOps améliorent la rationalisation et la collaboration des workflows de développement et d'opérations en automatisant les tâches chronophages, manuelles ou statiques des phases d'intégration, de développement, de test, de déploiement ou de surveillance.

# Notre Pratiques du DevOps

Notre pratiques DevOps nous permet d'amélioré en continu en automatisent les processus sur plusieurs phases du cycle de développement :

* Développement continu. Cette pratique couvre les phases de planification et de codage dans le cycle de vie DevOps et peut inclure des mécanismes de contrôle des versions.

* Tests continus. Cette pratique prévoit des tests automatisés, planifiés et continus lors de l'écriture ou de la mise à jour du code de l'application qui accélèrent la livraison du code en production.

* Intégration continue. Cette pratique rassemble des outils de gestion de la configuration, de test et de développement pour assurer le suivi de la mise en production des différentes portions du code. Elle implique une collaboration étroite entre les équipes responsables des tests et du développement pour identifier et résoudre rapidement les problèmes de code.

* Livraison continue. Cette pratique automatise la publication des modifications du code après la phase de test, dans un environnement intermédiaire ou de préproduction. Un membre de l'équipe peut décider de publier ces modifications dans l'environnement de production.

* Déploiement continu. À l'instar de la livraison continue, cette pratique automatise la publication d'un code nouveau ou modifié dans l'environnement de production. Les entreprises peuvent être amenées à publier plusieurs fois par jour des modifications du code ou des fonctionnalités. Dans un contexte de déploiement continu, les technologies de conteneur comme Docker et Kubernetes assurent la cohérence du code entre plusieurs plateformes et environnements.

* Surveillance continue. Cette pratique prévoit une surveillance continue du code exécuté et de l'infrastructure sous-jacente. Les développeurs reçoivent des retours sur les bogues ou sur les problèmes.



## Nos outils DevOps

* Nous allons gérer le code source à l'aide de l'outil du système de contrôle de version Git.
* Automatisez le processus de création de code à l'aide d'outil CI Jenkins.
* Scannez le code pour détecter les failles de sécurité SonarQube.
* Créez une image et la déployez avec une technologie conteneurisée Docker.
* Faires évoluer l'application à l'aide de l'outil d'orchestration de conteneurs Kubernetes.

# Qu'est-ce que Terraform ? 
Terraform est l'offre d'infrastructure en tant que code de HashiCorp. C'est un outil pour construire, modifier et gérer l'infrastructure de manière sûre et reproductible. Les opérateurs et les équipes d'infrastructure peuvent utiliser Terraform pour gérer les environnements avec un langage de configuration appelé HashiCorp Configuration Language (HCL) pour des déploiements automatisés lisibles par l'homme.

# Jenkins 
Pipeline Jenkins  est un serveur d'automatisation autonome et open source utilisé pour automatiser les tâches associées à la création, aux tests et à la livraison/déploiement de logiciels. Jenkins Pipeline implémente des pipelines de livraison continue dans Jenkins grâce à l'utilisation de plugins et d'un fichier Jenkins. Le fichier Jenkins peut être déclaratif ou scripté et contient une liste d'étapes à suivre par le pipeline.

# Infrastructure en tant que code 

il s'agit du processus de gestion de l'infrastructure dans un ou plusieurs fichiers plutôt que de configurer manuellement les ressources dans une interface utilisateur. Une ressource dans cette instance est toute pièce d'infrastructure dans un environnement donné, telle qu'une machine virtuelle, un groupe de sécurité, une interface réseau, etc.

À un niveau élevé, Terraform permet aux opérateurs d'utiliser HCL pour créer des fichiers contenant les définitions de leurs ressources souhaitées sur presque tous les fournisseurs (AWS, GCP, GitHub, Docker, etc.) et automatise la création de ces ressources au moment de la candidature. 

Dans cette piste, nous couvrirons les fonctions de Terraform pour créer une infrastructure sur AWS.

# Le role des environnements



# Prérequis 

Compte GitHub 
Compte AWS
Installer Terraform
Installer docker
Installer docker-compose
Installer Kubernetes
Utilisateur AWS avec des autorisations d'administrateur


# Architecture 

Dans ce projet, nous allons créer 3 instances AWS:

* Jenkins
* Pré-production
* Production
* S3 Bucket

Normalement, ce type d'architecture prendrait un certain temps à configurer dans la console AWS, mais grâce à Infrastructure as Code, le déploiement ne devrait prendre qu'environ 3 minutes après l'application du code Terraform.


# Aws
# Création d'une instance EC2 pour Jenkins:

* t2.large
* lancer docker compose
* SSD 20 Go
* Sécurity Group : 22 / 80 /  8080

![Screenshot](images\aws\a.png)
![Screenshot](images\aws\b.png)
![Screenshot](images\aws\c.png)
![Screenshot](images\aws\d.png)
![Screenshot](images\aws\e.png)
![Screenshot](images\aws\i.png)
![Screenshot](images\aws\g.png)

# Instance Ec2 Jenkins
## Nom et ID de mon 

* Nom de mon instance Ec2 : `projetgrp3-ec2-jenkins`
* ID de mon instance Ec2 :	    ` i-04ce15266a590e510`
* IPv4 publique de mon instance Ec2 :	`54.174.144.82`

## Déverrouillage de Jenkins
http://54.174.144.82:8080/

![Screenshot](images\Jenkins\1.png)

```txt
L'assistant de configuration post-installation démarre.
Lorsque vous accédez pour la première fois à une nouvelle instance Jenkins, vous êtes invité à la déverrouiller à l'aide d'un mot de passe généré automatiquement. Accédez à http://54.174.144.82:8080 et attendez que la page Déverrouiller Jenkins apparaisse.

À partir de la sortie du journal de la console Jenkins, copiez le mot de passe alphanumérique généré automatiquement.
```

* La commande suivante imprimera le mot de passe sur la console:
```bash
=>sudo cat /var/lib/jenkins/secrets/initialAdminPassword
6384c868fe614bd3ac72b3495daf7ae3
```
Nom d'utilisateur:	Administrator
mdp:	Umanis-2022

on installe les plugins suggérés et on crée un utilisateur

![Screenshot](images\Jenkins\2.png)
![Screenshot](images\Jenkins\3.png)
![Screenshot](images\Jenkins\4.png)
![Screenshot](images\Jenkins\5.png)
![Screenshot](images\Jenkins\6.png)
![Screenshot](images\Jenkins\7.png)

# Backend
##  Créer un backend de compartiment S3 

C'est une bonne pratique de traiter notre fichier d'état comme un secret et de le stocker à distance. 

Cela ajoute une sécurité accrue, mais permet également la collaboration entre les membres de l'équipe. Si le fichier d'état est stocké localement sur notre ordinateur, notre équipe n'y a évidemment pas facilement accès. Une chose à garder à l'esprit est le verrouillage d'état. 

Nous voulons nous assurer que notre option backend verrouille notre état lorsque quelqu'un met en service des ressources. Si deux membres de l'équipe tentent d'apporter des modifications en même temps, le fichier d'état peut être corrompu. Nous disons cela parce que bien que la plupart des options backend le fassent automatiquement, S3 ne le fait pas. Pour ce projet, nous ne l'avons pas activé le verrouillage d'état car nous travaillons sur le projet en équipe et il n'y avait aucun risque que mes modifications entrent en collision avec quelqu'un d'autre. 

Si nous souhaitions ajouter un verrouillage d'état à notre backend S3, veuillez consulter cette documentation Terraform:

https://www.terraform.io/language/settings/backends/s3


Créez un compartiment S3 à l'aide sur l'AWS. Assurez-vous de créer un nom unique. 

![Screenshot](images\aws\j.png)
![Screenshot](images\aws\k.png)
![Screenshot](images\aws\l.png)
![Screenshot](images\aws\m.png)
![Screenshot](images\aws\n.png)
![Screenshot](images\aws\o.png)







### Liste des installations sur notre instance Jenkins:
* Java
* Docker
* Docker-compose
* Terraform
* Kubernetes

### Les commandes d'installation:
```sh
#install Jenkins
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y

#Installation of Java
sudo apt-get install -y jenkins
sudo apt install -y openjdk-11-jdk

#Start Jenkins
sudo systemctl daemon-reload
sudo systemctl start jenkins

#Install docker
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
sudo usermod -aG docker ubuntu
sudo usermod -aG docker jenkins

#Install docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose


#Install TERRAFORM
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

# Install Minikube Ubuntu
sudo apt-get update && sudo apt-get install -y apt-transport-https
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

# Dockerfile

* lien :
https://github.com/projetajc-group3/docker_node.git

```ruby
FROM node:14.16
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production
# Bundle app source
COPY . .
EXPOSE 3000
CMD [ "node", "./bin/www" ]
```

- FROM: indique au docker quelle image utiliser comme image de base. Ici, nous utilisons la version 14.16 du node
- WORKDIR: indique à docker le répertoire de travail de notre image (dans notre cas, il s'agit de /usr/src/app. 
Les commandes CMD ou RUN s'exécutent dans ce dossier

- COPY signifie copie ; Ici, nous copions le fichier package.json dans home
- RUN exécute une commande sur le répertoire de travail défini ci-dessus. La commande npm install installe les dépendances requises définies dans le package.json, que nous venons de copier dans le répertoire /app

- CMD signifie commande, et ici nous exécutons node 

#(index.js comme nous l'avions vu au début de cet article pour démarrer le serveur NodeJS ou exécuter le fichier. Nous avons index.js dans le répertoire de l'application de la dernière étape et nous démarrons notre serveur à partir du fichier index.js.)

- EXPOSE : L'instruction EXPOSE informe Docker que le conteneur écoute sur les ports réseau '3000' lors de l'exécution. 

# kubernetes (minikube)

## Gestion Réseau

## Configurer Ingress sur kubernetes


## Objectifs
```Txt
• Nous allons créer un deployment avec 02 replicas de notre application node app
• Créez un service de type "nodeport" pour exposer notre deployement précédemment crées
• Activer l’ingress controller dans notre cluster minikube
//Configurez une règle ingress permettant de consommer notre applications en utilisant les paramètres suivants:
//Host: www.votreprenom-webapp.com
//Et ajoutez convenablement notre host dans le fichier /etc/hosts
```
* Nodeport

Expose le service sur une IP externe au cluster. Le choix de cette valeur rend le service uniquement accessible à partir du cluster. Il s'agit du ServiceType par défaut.

Nous allons crée un nouvel objet Service nommé «service-nodeport, qui cible le port TCP 80 sur n'importe quel pod avec l'étiquette «app=node-app».

port : port du service
tareget port : port du pod a utiliser (doit correcpondre à l'application)
nodeport : port utilisavle depuis l'extrieur du cluster (un genre de routeur)


###################################
kubectl create deploy node --image projetajcgroup3/node:1.0 --port 3000 --replicas=2
kubectl expose deploy node --name node-svc --type NodePort --port 30001

kubectl create deploy node --image projetajcgroup3/node:1.0 --port 3000 --replicas=2
kubectl expose deploy node --name node-svc --type NodePort --targetPort 3000 --port 3000 --nodePort 30001
kubectl expose deployment source-ip-app --name=clusterip --port=80 --target-port=8080
###################################

###################################
apiVersion: v1
kind: Service
metadata:
  name: nodeport
spec:
  type: NodePort
  selector:
    app: nodeapp
  ports:
  #port du pod a utiliser
    - targetPort: 3000
    #port du service
      port: 3000
      #port utilisable depuis l'extrieur du cluster
      nodePort: 30001

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nodeapp
  labels:
    app: nodeapp
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nodeapp
  template:
    metadata:
      labels:
        app: nodeapp
    spec:
      containers:
      - env:

        
      - name: webappprod
        image: projetajcgroup3/node:1.0
        ports:
        - containerPort: 3000
########################################
# Déploiement dans Kubernetes

## Définir le fichier YAML pour le déploiement dans le cluster Kubernetes
YAML est un langage de balisage extensible lisible par l'homme. Il est utilisé dans Kubernetes pour créer un objet de manière déclarative.


=> vi nodeapp.yml
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nodeport
spec:
  type: NodePort
  selector:
    app: nodeapp
  ports:
  #port du pod a utiliser
    - targetPort: 3000
    #port du service
      port: 3000
      #port utilisable depuis l'extrieur du cluster
      nodePort: 30001

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nodeapp
  labels:
    app: nodeapp
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nodeapp
  template:
    metadata:
      labels:
        app: nodeapp
    spec:
      containers:
      - name: {{ name_containers }}
        image: {{ image_containers }}
        ports:
        - containerPort: 3000
```
# Répartition de notre fichier YAML

- apiVersion: 
La version de l'API que vous utilisez pour créer cet objet, c'est-à-dire le déploiement - nous utilisons apps/v1 

- kind: 
Quel type d'objet créez. Dans notre cas, c'est le déploiement. 

- metadata: 
Les métadonnées sont utilisées pour organiser l'objet. Le nom de notre déploiement est nodejs-deployment 

- spec: 
est utilisé pour définir la spécification de l'objet. 

- replicas: 
Combien de pods vous souhaitez déployer dans le cluster sous ce déploiement. 

- template: 
matchLabels nous souhaitons déployer deux pods exécutant des conteneurs à partir de notre image "nodeapp"

- Le modèle est utilisé pour définir comment faire tourner le nouveau pod et la spécification du pod. 

- metadata: 
Métadonnées du pod nouvellement créé avec ce déploiement 

- labels:
Nous avons une étiquette - la clé est app et la valeur est nodeapp 

- spec:Spécifications des conteneurs 

- name:
Nom du conteneur 

- image
L'image qui peut être utilisée par le conteneur 

Quelle option de port utiliser Nous utilisons containerPort 3000



Comme nous avons créé le fichier YAML, nous pouvons continuer et créer un déploiement à partir de ce fichier YAML.

kubectl create -f deploy.yaml

Kubectl est le client de Kubernetes qui est utilisé pour créer des objets. Avec kubectl create, vous pouvez créer n'importe quel objet -f indique que nous utilisons un fichier et deploy.yaml est le fichier qui sera utilisé pour créer un objet. Vous pouvez vérifier le déploiement avec la commande suivante :

# Les commpandes de lancement

- minikube start --driver=none

![Screenshot](images\kubectl\1.jpg)

- kubectl delete --all svc,deployments.apps,pod
- kubectl apply -f nodeapp.yml 
- kubectl describe services

![Screenshot](images\kubectl\2.jpg)

- kubectl describe deployments.apps
![Screenshot](images\kubectl\3.jpg)

- kubectl get pods
- kubectl get service
- kubectl get deployments.apps

![Screenshot](images\kubectl\4.jpg)


ansible-playbook -i kubernetes_role_deploy/hosts.yml kubernetes_role_deploy/kubernetes.yml --extra-vars "name_containers=webappprod image_containers=projetajcgroup3/node:1.0" || true