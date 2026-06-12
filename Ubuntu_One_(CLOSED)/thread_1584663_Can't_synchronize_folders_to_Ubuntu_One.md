---
title: "Can't synchronize folders to Ubuntu One"
date: 2010-09-29
forum: Ubuntu One (CLOSED)
---

### Post by Yahoé on 2010-09-29
On Ubuntu 10.10 x64, when trying to sync via right click "Ubuntu One/Synchroniser ce dossier" Synchronize to Ubuntu One, nothing happens.
When within the "Documents" folder I select "Synchroniser ce dossier" Synchronize this folder from the upper right section of the window I get an error message:
"Erreur lors de l'activation du dossier. Impossible d'activer la synchronisation du dossier /home/ao/Documents avec Ubuntu One"

ao@Ordi-AO-Ubuntu:~$ u1sdtool --list-folders
No folders

ao@Ordi-AO-Ubuntu:~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE


Within the Ubuntu One app, my computer is identified and connected.

---

### Post by Yahoé on 2010-09-29
Think I found the reason why, Ubuntu One cannot synchronize Links, these two were links to actual folders in a different location outside of the home folder.

---

