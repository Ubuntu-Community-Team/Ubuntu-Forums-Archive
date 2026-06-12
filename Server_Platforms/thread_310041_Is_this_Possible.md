---
title: "Is this Possible ???"
date: 2006-11-30
forum: Server Platforms
---

### Post by psycho78 on 2006-11-30
Hi,
I just wonder if it is possible to build a Server system with samba installed where the data is on one encrypted harddrive (access should only be granted after entering a valid password at boottime) and a second encrypted removable harddrive for backups (also only access with the correct password at boottime or when inserting the harddrive) The System should boot only from a live cd...! The idea behind is to install little fileservers for windows machines.... Right now we are using windows 2003 machines with an encryption software (system only boots after correct password) ... in this case the system is installed on promise sata raid 1. Backups are made on a removable sata disk on which are enrypted containers. The users have to enter a password each day to open up a container (this is done via a script) . At night we have a scheduled task to copy the data from the encrypted system disk into the opened encrypted container... This way we can guarantee that the data is safe even if the server or the removable harddrive gets stolen. 
My idea is to have the os on a live cd because we would not have to care about harddrive failures for the system, security updated would be as easy as inserting a new CD we send to the server... would do you think about this?
All the new machines we use for this come with 2GB of RAM and also have to 80GB Sata drives... 
We always have to have a removable drive because the team which uses the server brings in the harddrive once a week so that we can put the data on our real fileservers in the office.

---

### Post by bernied on 2006-11-30
I believe all this is possible, try starting with one of the adaptable live-cds - I made a recovery live-cd for a headless server out of slax, I believe it would have been easy to add samba to it. And the filesystem encryption is out there, but I've never done it. You would have to restart to do your updates though.

---

### Post by psycho78 on 2006-12-01
sounds good, I would like to this with ubuntu server if possible .... I remember that there is a package out there to make a live cd from your current installation.... maybe this would be worth a try....

---

### Post by psycho78 on 2006-12-01
sorry for forgetting some words sometimes... I typed too fast without re-reading....

---

