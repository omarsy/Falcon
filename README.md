# Configuration réseau :

Afin de permettre la communication entre le robot et l'application mobile, nous avons mis en place un server web Flask qui va communiqué via une connexion wifi.

WIFI : Contrairement à l’interface Ethernet, le WIFI est utilisé pour L’accès client.

Le WIFI doit être configurer en point d’accès, d’où la nécessite d’installer hostapd.

On modifie le fichier de configuration "/etc/hostapd/hostapd.conf". 

Ce fichier a pour but de lancer le point d’accés avec les paramétrés voulus (BSSID, mot de passe, canal, etc..).
Et enfin, pour lancer le point d’accès au démarrage du système, on rajoute cette ligne RUN\_DAEMON=yes, au fichier de configration suivant : /etc/default/hostapd.

# Gestion des capteurs :

Pour éviter les obstacles nous avons des capteurs qui permet de détecter la position. Ainsi on doit identifier les capteurs de manière unique et on doit s'assurer que chaque capteur s’exécute dans un processus à part.

La distance qui sépare le véhicule et le capteur doit être observable par les composants qui se sont inscrit au préalable.

Le capteur un processus exécuté dans un thread notifie à chaque fois qu'il récupère la distance entre lui et l'obstacle les composants qui se sont inscrit au préalable pour être informé de la distance.

# Gestion de la camera :
Nous disposant d'un module de caméra Raspberry Pi NoIR v2 qui est un capteur d'images 8 mégapixels Sony IMX219 pour Raspberry Pi, doté d'une lentille à focale fixe. Il permet de prendre des images statiques de 3280 x 2464 pixels et supporte également les formats vidéo 1080p30, 720p60 et 640x480p60/90. 

Il se raccorde au Pi par le biais de l'un des petits connecteurs sur la surface supérieure de la carte et utilise l'interface CSI dédiée, spécialement conçue pour les caméras. 
La carte est de petite dimension, d'environ 25mm x 23mm x 9mm. Elle pèse à peine plus de 3g.

Pour pouvoir récupérer les images de la caméra nous avons du installer le module \textbf{RPI CAM web interface}.

c'est une interface Web pour le module Raspberry Pi Camera qui peut être utilisé pour une grande variété d'applications, y compris la surveillance, l'enregistrement DVR et la photographie en accéléré. 
Il est hautement configurable et peut être étendu avec l'utilisation de scripts de macro.

Il nous a permit de mettre en place le \textbf{streaming}, via une \textbf{url} sur laquelle il envoie le flux vidéo de la camera du robot.