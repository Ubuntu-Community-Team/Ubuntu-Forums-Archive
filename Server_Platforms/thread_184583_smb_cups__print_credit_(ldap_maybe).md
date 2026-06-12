---
title: "smb cups / print credit (ldap maybe)"
date: 2006-05-30
forum: Server Platforms
---

### Post by oly on 2006-05-30
i am looking for a solution to setting up a linux print server i have cups and samba set up but any one can print and as much as they like is there anyway i can setup some sort of logging / credit system.

preferably using ldap if possible but i am open to any suggestions this will be running on dapper but i need to know what software there is available for doing this.

the server is for a school if you are intrested so credit system will be needed

---

### Post by patrick295767 on 2006-05-30
[QUOTE=oly]i am looking for a solution to setting up a linux print server i have cups and samba set up but any one can print and as much as they like is there anyway i can setup some sort of logging / credit system.

preferably using ldap if possible but i am open to any suggestions this will be running on dapper but i need to know what software there is available for doing this.

the server is for a school if you are intrested so credit system will be needed[/QUOTE]
 
In my school there was a folder in $HOME 
owned by root  
~/.print/remainingprintingpages
  
I dont know how they did it ... if via special program... 
  
I am also very interested !! :-)

Greetz

---

### Post by oly on 2006-05-31
no one know of some software to make this possible, disk quotaing is also something i will need at some point.

---

### Post by patrick295767 on 2006-05-31
[QUOTE=oly]no one know of some software to make this possible, disk quotaing is also something i will need at some point.[/QUOTE]
  
We need to work on it !!
  
I can access my school linux server and tell you how they do ... via listing the / hdd programs or /usr/bin ... 

Let's keep in touch via email or gaim ! You can remind me in the evening to list the disk ...
  
  
2/ is there any : 
```
ls /* >> /myhddlistfiles.txt
```
kind of to list the full harddisk ??
U know what I mean ?
  
Greetz !!!

---

### Post by patrick295767 on 2006-06-04
When you install the printer with KDE, it's asking for quota stuffs for users
```
apt-get -f -y install kicker
```
   then kicker &
and select addprinter ... 

Greetz

---

### Post by oly on 2006-06-05
okay i will try this out thanks :)

---

### Post by patrick295767 on 2006-06-06
[QUOTE=oly]okay i will try this out thanks :)[/QUOTE]
  
There is also a config file in the /etc/cups   (extension: conf)
you can set up loot of things there too ... 

Greetz

Sorry, it's in french... 
> Je vous invite donc a lire [http://doc.ubuntu-fr.org/generalite/reseau](http://doc.ubuntu-fr.org/generalite/reseau) si besoin est. (auteur jrev) 
Installation côté serveur 
1 Après avoir installé les pilotes hpijs, hplip-base, hplip-data, hplip-ppds par synaptic, installez l'impri-mante locale (par syst/admin/impression) et choisissez le pilote adéquat 
2 Modifiez le fichier de configuration cupsd.conf afin d"autoriser le partage de l"imprimante sur le réseau 
Editez (avec gedit sour Ubuntu ou kate sous Kubuntu) le fichier /etc/cups/cupsd.conf avec les droits de super-utilisateur. 
Déplacez vous à la ligne contenant Port 631 ligne 450 environ (pensez à la fonction recherche. Décommentez alors la ligne en enlevant le # qui précède. 
Déplacez vous à la ligne contenant <Location /> ligne 796 environ. Vous allez y rajouter l"accès aux machines du réseau local et vous aurez besoin de connaître la configuration de celui-ci. Ajoutez alors les adresses de votre réseau local dans la section : sous Allow From 127.0.0.1, ajoutez la ligne Allow From <adresse ip>/<masque> où l"<adresse ip> est souvent 192.168.10.x et le <masque> est 255.255.255.0. 
Redémarrez le serveur d"impression CUPS avec la commande 
$ sudo /etc/init.d/cupsys restart 
Installation côté client 
Ouvrez Système &#8594; Administration &#8594; Impression et double-cliquez sur Nouvelle imprimante. 
Selectionnez Imprimante réseau, puis Imprimante CUPS IPP et dans le champ URL entrez ipp://<serveur_imprimante>/printers/<nom_imprimante&g t;. 
1.<serveur_imprimante> peut être l"adresse ip de la machine serveur ou son nom. 
2.<nom_imprimante> est le nom de l"imprimante déjà configurée sur le serveur. 
Choisissez ensuite le pilote de votre imprimante puis validez. 
Exemple : 
Si votre serveur est 192.168.10.1 et les 2 clients sont 192.168.10.2 et 192.168.10.3 le contenu du fichier /etc/cups/cupsd.conf du serveur d'imprimante peut être remplacé par ce qui suit : 
ConfigFilePerm 0600 
DefaultCharset notused 
LogLevel info 
Printcap /var/run/cups/printcap 
eeded. 
RunAsUser Yes 
Port 631 
Include cupsd-browsing.conf 
BrowseAddress @LOCAL 
<Location /> 
Order Deny,Allow 
Deny From All 
Allow From 192.168.10.* 
</Location> 
<Location /jobs> 
AuthType Basic 
AuthClass User 
</Location> 
<Location /admin> 
AuthType Basic 
AuthClass System 
Order Deny,Allow 
Deny From All 
Allow From 127.0.0.1 
Allow From 192.168.10.2/255.255.255.0 
Allow From 192.168.10.3/255.255.255.0 
</Location> 

Notes : 
1 Quand une page est envoyée par une application d'un client elle est filtrée successivement par le spooler 
client puis par le spooler du serveur 
2 les pilotes nécessaires à l'imprimante doivent être installés sur chaque PC, bien que seul le serveur dialogue directement avec la machine 

  
To be continued ... (need more time)
-----
[http://forum.ubuntu-fr.org/viewtopic.php?pid=287547#p287547](http://forum.ubuntu-fr.org/viewtopic.php?pid=287547#p287547)

---

### Post by oly on 2006-06-07
i have found something called pyKota which looks like it does what i want it supports ldap which is what i really wanted. not had a chance to try it yet though.

---

### Post by patrick295767 on 2006-06-08
[QUOTE=oly]i have found something called pyKota which looks like it does what i want it supports ldap which is what i really wanted. not had a chance to try it yet though.[/QUOTE]
  
I think we are both very busy and both really no time to look at it ... :-) :D
for the moment only ... time will come !

---

### Post by oly on 2006-06-09
yeah i am a bit, plus i want to setup the print server with dapper previously it was breezy hopefully soon i can give it ago also want to move the ldap server to dapper as well.

---

### Post by patrick295767 on 2006-06-09
[QUOTE=oly]yeah i am a bit, plus i want to setup the print server with dapper previously it was breezy hopefully soon i can give it ago also want to move the ldap server to dapper as well.[/QUOTE]
  
I "ll also soon move to dapper as soon as much more time
i got some troubles with the server dapper cd , not able to recognize my hardware
pc rebooting all time ... :-(
i have to try now the desktop dapper iso cd... 
  
which dapper cd distro desktop/ server / LAMP / ... are u planned to install ?

 Greetings to you  !!

---

### Post by oly on 2006-06-09
i was planning to use the server cd for 64bit, but am currently using the breezy desktop verion.

the hardware i have here seems to work perfectly with ubuntu especially considering its all quite new amd 64 x2 chips and pci-e express motherboards.

i am not planning to use lamp because its more ldap samba and other servers like web server backup server etc, 

i am also very familiar with setting up php mysql and apache2 done it quite a few times so takes me no time at all.

---

