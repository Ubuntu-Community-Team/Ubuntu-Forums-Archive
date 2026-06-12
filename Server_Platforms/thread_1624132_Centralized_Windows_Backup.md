---
title: "Centralized Windows Backup?"
date: 2010-11-17
forum: Server Platforms
---

### Post by kevin11951 on 2010-11-17
Does anyone know of an easy to use centralized Windows backup method?  Preferably Linux based, but its not required...

I am currently freelancing for a local high school, and they need a system to do incremental backups of the personal data from all of the computers...  They run a mix of Windows XP, Vista, and 7...

---

### Post by arrrghhh on 2010-11-17
Clonezilla, Bacula... depends do you want bit-for-bit backups?

---

### Post by kevin11951 on 2010-11-17
> **arrrghhh said:**
> Clonezilla, Bacula... depends do you want bit-for-bit backups?

Well, we want to do backup of personal files, like Firefox settings, documents, stuff like that...

---

### Post by arrrghhh on 2010-11-17
> **kevin11951 said:**
> Well, we want to do backup of personal files, like Firefox settings, documents, stuff like that...

Bacula I've heard is pretty good.

Amahi is pretty slick, but runs on Fedora.

---

### Post by Medwyyn42 on 2010-11-17
Bacula works well - but - it can and will take a while to set up. I've got it running at home to back up 2 Win Vista clients and 2 Ubuntu clients, one is the server it's running on. I've got Bacula's BAT application running on the server but do most of the maintenance via the BWeb website that is an optional install. I will admit I spent hours crafting the configure files to my liking and dabbled with the base job (data de-duplication) feature, but stopped using it due to the fact that you can't currently restore from a base job very easily. Now I just do a rotation of full and incremental backups. You do need to set up the server to access the Windows clients in VSS mode to get "open" files backed up. Works well, fairly fast and seems to be reliable. BWeb is nice because it tells you when and why something didn't back up. I did also use the available Webmin module to do some of the initial setup work. If you need a breakdown of what I did, let me know and I can get the config files for you.

---

### Post by kevin11951 on 2010-11-17
> **Medwyyn42 said:**
> Bacula works well - but - it can and will take a while to set up. I've got it running at home to back up 2 Win Vista clients and 2 Ubuntu clients, one is the server it's running on. I've got Bacula's BAT application running on the server but do most of the maintenance via the BWeb website that is an optional install. I will admit I spent hours crafting the configure files to my liking and dabbled with the base job (data de-duplication) feature, but stopped using it due to the fact that you can't currently restore from a base job very easily. Now I just do a rotation of full and incremental backups. You do need to set up the server to access the Windows clients in VSS mode to get "open" files backed up. Works well, fairly fast and seems to be reliable. BWeb is nice because it tells you when and why something didn't back up. I did also use the available Webmin module to do some of the initial setup work. If you need a breakdown of what I did, let me know and I can get the config files for you.

Wait, how hard is it to setup?  

I have the school running a customised OCS Inventory, and a FOG based imaging server, is it harder to set up than those?

---

