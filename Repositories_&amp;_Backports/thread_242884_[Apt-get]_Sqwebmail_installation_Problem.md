---
title: "[Apt-get] Sqwebmail installation Problem"
date: 2006-08-24
forum: Repositories &amp; Backports
---

### Post by lulux on 2006-08-24
Hi Everyone, 


I'va a problem with Apt.

Few days ago i installed sqwebmail package with APT-get (Cmd line, i dont have any X server). Then, i had some Configuration problem with sqwebmail, so i decided to remove it (still with Apt-get cmd), and this worked fine. 

Then,  i did something really stupid i guess :p. I noticed there was a file called "sqwbemaild" in /etc/courier/. I decided to remove this file with "rm". And for this moment i can't install anymore sqwebmail package. i got the error : (i'm on a french distrib... sorry, but ou should understand the error msg which is  in english.)

```
 root@Eckmul:~# apt-get install sqwebmaild
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
E: Impossible de trouver le paquet sqwebmaild
root@Eckmul:~# apt-get install sqwebmail
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Paquets suggérés :
  courier-doc courier-pcp
Les NOUVEAUX paquets suivants seront installés :
  sqwebmail
0 mis à jour, 1 nouvellement installés, 0 à enlever et 3 non mis à jour.
Il est nécessaire de prendre 769ko dans les archives.
Après dépaquetage, 2458ko d'espace disque supplémentaires seront utilisés.
Réception de : 1 http://security.ubuntu.com dapper-security/universe sqwebmail 0.47-13ubuntu5.1 [769kB]
769ko réceptionnés en 1s (614ko/s)
Préconfiguration des paquets...
Sélection du paquet sqwebmail précédemment désélectionné.
(Lecture de la base de données... 86761 fichiers et répertoires déjà installés.)
Dépaquetage de sqwebmail (à partir de .../sqwebmail_0.47-13ubuntu5.1_i386.deb) ...
Paramétrage de sqwebmail (0.47-13ubuntu5.1) ...
 * Starting Courier webmail daemon...                                    
/usr/sbin/webmaild: line 14: /etc/courier/sqwebmaild: no such file exists[fail]
invoke-rc.d: initscript sqwebmail, action "start" failed.
dpkg : erreur de traitement de sqwebmail (--configure) :
 le sous-processus post-installation script a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution :
 sqwebmail
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I guess the init script is looking for this file.. which is not install with Apt-get.

DPKG error log looks like
```
root@Eckmul:~# tail -100 /var/log/dpkg.log

2006-08-23 16:56:48 status half-configured sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:57:14 status half-configured sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:57:46 status half-configured sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:58:02 remove sqwebmail 0.47-13ubuntu5.1 0.47-13ubuntu5.1
2006-08-23 16:58:02 status half-configured sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:58:02 status half-installed sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:58:04 status config-files sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:58:04 status config-files sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:31 install sqwebmail 0.47-13ubuntu5.1 0.47-13ubuntu5.1
2006-08-23 16:59:31 status half-installed sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:31 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:31 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status unpacked sqwebmail 0.47-13ubuntu5.1
2006-08-23 16:59:32 status half-configured sqwebmail 0.47-13ubuntu5.1
```



Does anyone know what the **status half-configured** means ?  (in the last line of the log). Is there any way i can get back the file 'sqwebmaild' (maybe from the ubuntu Cd ? .. but i don't know where to find it ).




Thnx

Lulux

---

### Post by crackseller on 2006-08-24
You could remove it yet again with the --purge option (note: this will remove all it's config files as well!) or try "orphan", a tool to remove orphaned packages. At least, that is what came to my mind when I read your prob.

---

### Post by lulux on 2006-08-24
WOOOOOT !


It did work !

Thnx a lot crackseller :D .

I didn't know the "--purge" option. First it did not work because apt couldn't find the sqwebmaild file. So i just did a "touch /etc/courrier/sqwebmaild" and then the apt-get remove --purge & re- install worked fine.

Thnx again.

Lulux

---

