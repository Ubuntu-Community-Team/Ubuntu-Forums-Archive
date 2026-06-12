---
title: "googleearth et Lucid Lynx"
date: 2010-05-10
forum: Tunisia Team
---

### Post by saladin_hs on 2010-05-10
bonsoir tout le monde,
j'ai installé googleearth sous lucid du dépôt medibuntu mais je n'arrive pas à me connecter au serveur donc j'ai juste un écran noir (pas de globe)
si quelqu'un à rencontré et résolu le même problème ça serait sympa de m'indiquer la solution
merci

---

### Post by Nizarus on 2010-05-10
un message d'erreur particulier ? essaye de désactiver compiz.

---

### Post by saladin_hs on 2010-05-10
avec compiz désactivé même erreur

 "googleearth n'a pas pu connecter [http://kh.google.com:80/](http://kh.google.com:80/)

puis on m'oriente vers le lien suivant [http://earth.google.com/support/bin/answer.py?answer=20717&hl=fr](http://earth.google.com/support/bin/answer.py?answer=20717&hl=fr)

sans apport de solution

---

### Post by Neo31 on 2010-05-11
Si tu essaye de se connecter depuis une institut (normalement qui passe par les proxies CCK) tu doit assurer que tu passe par leurs proxy et que tu utilise du HTTP pas un autre protocole. sinon si t'es dans une entreprise ou autre place tu doit verifier aussi qu'il y a pas un parfeux ou un proxy qui bloque ce ci.
essaye de lancer Google Erath depuis la console et de voir le prompt sur l'ecran. (tu doit ecrire le nom du programme google earth sur ta console, commence par taper google et apuie sur tab 2 fois) ou cherche le nom de l'executable google earth dans les menus.
Désactivez la fonction **Atmosphère** en ouvrant le menu **Affichage** et en cliquant sur **Atmosphère** pour qu'elle ne soit plus cochée. Si cette option n'est pas cochée, vous pouvez ignorer cette étape.
 Essayez de [vider votre cache Google Earth]("http://earth.google.com/support/bin/answer.py?answer=20712").

---

### Post by saladin_hs on 2010-05-11
> **Neo31 said:**
> Si tu essaye de se connecter depuis une institut (normalement qui passe par les proxies CCK) tu doit assurer que tu passe par leurs proxy et que tu utilise du HTTP pas un autre protocole. sinon si t'es dans une entreprise ou autre place tu doit verifier aussi qu'il y a pas un parfeux ou un proxy qui bloque ce ci.
essaye de lancer Google Erath depuis la console et de voir le prompt sur l'ecran. (tu doit ecrire le nom du programme google earth sur ta console, commence par taper google et apuie sur tab 2 fois) ou cherche le nom de l'executable google earth dans les menus.
Désactivez la fonction **Atmosphère** en ouvrant le menu **Affichage** et en cliquant sur **Atmosphère** pour qu'elle ne soit plus cochée. Si cette option n'est pas cochée, vous pouvez ignorer cette étape.
 Essayez de [vider votre cache Google Earth]("http://earth.google.com/support/bin/answer.py?answer=20712").


j'utilise une machine chez moi avec un modem ADSL Gnet
je n'ai pas installé de firewall
le lancement au terminal ne donne rien de du tout le programme se lance normalement mais ne peut pas connecter au serveur des images satellite
pas de serveur => rien dans le cache

---

