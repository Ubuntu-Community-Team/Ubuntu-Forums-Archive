---
title: "probleme de virtualbox"
date: 2009-05-02
forum: Tunisia Team
---

### Post by micronet on 2009-05-02
salut à tous

j'était obligé d'installer virtualbox afin d'avoir winXp. Mais, je me trouve face a un problème d'affichage: ma carte graphique(intel x3100) n'est pas reconnue. alors, je me trouve incapable de travailler en plein écran car ma résolution(1280x800) est introuvable dans la liste des résolution de windows. Je travaille donc avec la résolution 1024x768 qui ne rempli pas la totalité de l'écran.

Que dois-je faire S.V.P ?

---

### Post by a.med on 2009-05-02
Tu n'as pas précisé qui (Ubuntu ou VBox ou xp) qui ne reconnait pas ta carte!
Si c'est Ubuntu, tu dois chercher un module (driver) qui prend en charge ta carte.
Pour les autres cas, ce n'est pas nécessaire du tout.
VirtualBox n'utilise pas ta vraie carte graphique mais une carte virtuelle.
Tu n'as donc pas à t'inquiéter . Il te suffit:
- de régler les préférences de ta machine virtuelle dans VBox AVANT de démarrer xp virtuel
- Installer les Guest additions dans xp (regarde l'aide de VBox)
- pour switcher entre le plein ecran et la fenêtre fait (Ctrl + F) ou utilise le menu
=================
Remarque:
Si tu as installé VBox OSE (open source) et ci tu n'es qu'un utilisateur comme moi (tu ne vas pas examiner le code source) Désinstalle-la et installe la Versio Deb. Elle est plus à jour et contient plus de nouveautés.
Le lien suivant t'expliquera comment faire:
[http://doc.ubuntu-fr.org/virtualbox](http://doc.ubuntu-fr.org/virtualbox)

---

### Post by omrisaber on 2009-05-02
> **micronet said:**
> salut à tous

j'était obligé d'installer virtualbox afin d'avoir winXp. Mais, je me trouve face a un problème d'affichage: ma carte graphique(intel x3100) n'est pas reconnue. alors, je me trouve incapable de travailler en plein écran car ma résolution(1280x800) est introuvable dans la liste des résolution de windows. Je travaille donc avec la résolution 1024x768 qui ne rempli pas la totalité de l'écran.

Que dois-je faire S.V.P ?

[SIZE="3"]ok pour voir les choses clairement, Virtualbox "crée" une nouvelle carte graphique pour le système virtualisé , càd que votre "vraie" cartet graphique n'a rien à voir !
pour cette carte "virtuelle", vous devez installer les additions invités !
Pour le faire, quand tu démarres ton windows virtualisé :
Menu "périphérique" --> "installer les additions invité.."

il te demande (ou non suivavt votre version) d'installer un fichier iso de 26Mo (à peu près!) , confirmez !

J'attends votre commentaire.[/SIZE]

---

### Post by dark of angel on 2009-05-03
d abord virtualbox n utilise pas votre vrai carte donc ce n est pas question de s inquiété de virtualbox le problème est sur cote ubuntu donc détermine ta carte  puis installe driver s il existe (existe pour ton cas)si non vérifie la compatibilité de la carte avec ubuntu 8.10
nb : je te conseil de installer 9.04
et install les additions invite

---

### Post by micronet on 2009-05-03
> **omrisaber said:**
> [SIZE="3"]ok pour voir les choses clairement, Virtualbox "crée" une nouvelle carte graphique pour le système virtualisé , càd que votre "vraie" cartet graphique n'a rien à voir !
pour cette carte "virtuelle", vous devez installer les additions invités !
Pour le faire, quand tu démarres ton windows virtualisé :
Menu "périphérique" --> "installer les additions invité.."

il te demande (ou non suivavt votre version) d'installer un fichier iso de 26Mo (à peu près!) , confirmez !

J'attends votre commentaire.[/SIZE]


merci pour ta reponse mais, lorsque je passe par Menu "périphérique" --> "installer les additions invité..", il ne me donne rien. ça peut etre parceque j'utilise la derniere version de virtualbox, la 2.2.2 

Je sais que virtualbox n'utilise pas ma carte reelle, je pense que je dois avoir dans la liste des materiels dans le win émulé un peripherique du genre vbox graphic(ou quelque choe comme ça), alors que moi je trouve un peripherique inconnu(vga compatible)avec cette fameuse point d'interrogation jaune. 

Alors???

---

### Post by micronet on 2009-05-03
> **dark of angel said:**
> d abord virtualbox n utilise pas votre vrai carte donc ce n est pas question de s inquiété de virtualbox le problème est sur cote ubuntu donc détermine ta carte  puis installe driver s il existe (existe pour ton cas)si non vérifie la compatibilité de la carte avec ubuntu 8.10
nb : je te conseil de installer 9.04
et install les additions invite

merci pour ta repose. bon, je pense que sur ubuntu, ma carte fonctionne parfaitement, mais je peut pas l'affirmer.je suis satisfait du resolution de l'ecran, des couleurs, de la lecture des videos, ....

mais bon, peut tu me donner la methode pour s'assurer de la fonctionnalité des differents peripheriques(comme le gestionnaire de peripheriques de Win)

---

### Post by omrisaber on 2009-05-03
> **micronet said:**
> merci pour ta reponse mais, lorsque je passe par Menu "périphérique" --> "installer les additions invité..", il ne me donne rien. ça peut etre parceque j'utilise la derniere version de virtualbox, la 2.2.2 
Alors???

Quand vous faites Menu "périphérique" --> "installer les additions invité..", il "monte" un fichier "iso" (image d'un CD) que tu dois les exécuter depuis ton poste detravail dans Win XP (lecteur CD-Rom), tu dois avoir l'icône de virtualbox addons dans le lecteur du win virtualisé :)

---

### Post by micronet on 2009-05-05
Merci à tous ceux qui m'ont  aider a resoudre ce probleme. En faite tout est regler en installant les additions clients. j'ai voulu signaler ce sujet comme resolu mais j'ai pas trouver comment le faire.

---

