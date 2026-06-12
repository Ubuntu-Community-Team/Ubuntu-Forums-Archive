---
title: "samba server issue"
date: 2011-11-20
forum: Server Platforms
---

### Post by zoobie on 2011-11-20
Hi everybody,

I'm using a samba serve installed on my NAS server which is running under Ubuntu 11.10.

I'm administering this server through Webmin.

The issue is that if I want to be able to connect on the samba server from my other PCs I need each time after a boot/reboot of NAS server to restart manually the samba server. I would like to have this step automated therefore i'm seeking for help.

As you can see below I have ran the command net view from another PC on the same network, when the NAS server is offline, the samba server is not detected, when the NAS server is online the Samba server could be seen by other PC (i.e. \\SAMBA_RESO_29) which is good

```
C:\Users\Manu>net view
Nom de serveur         Remarque
-------------------------------------------------------------------------------
\\FREEBOX              (null)
\\G73-PC
\\PCHC
La commande s'est terminée correctement.

C:\Users\Manu>net view
Nom de serveur         Remarque
-------------------------------------------------------------------------------
\\FREEBOX              (null)
\\G73-PC
\\PCHC
**\\SAMBA_RESO_29**        Serveur Fichier Samba pour RESO_29
La commande s'est terminée correctement.
C:\Users\Manu>
```

But when I'm trying to access the samba server whith windows explorer under favorite network I have the following error message : System Error: 53 - Network Path not found

When I'm trying to access the IP adress of my samba server with net view command (i.e. 192.168.1.9)I have the same error message

```
C:\Users\Manu>net view 192.168.1.9
L'erreur système 53 s'est produite.
Le chemin réseau n'a pas été trouvé.
C:\Users\Manu>
```

But when i'm restarting the Samba server whith Webmin I have another error message (System Error 5 – “Access Is Denied”)  which is fine as my samba server is protected by userid and password 

```
C:\Users\Manu>net view 192.168.1.9
L'erreur système 5 s'est produite.
Accès refusé.
C:\Users\Manu>
```

When i'm trying agon with windows explorer after populating userid and password everything works.

I don't understand why I need to restart mannually the samba server under webmin each time in order to have the whole thing to work properly.

I'm interested in any help to solve the manual work turnaround

Thanks for your help

Zoobie

---

### Post by zoobie on 2011-12-01
+1 Help I need help

---

