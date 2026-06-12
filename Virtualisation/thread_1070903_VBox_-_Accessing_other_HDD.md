---
title: "VBox - Accessing other HDD"
date: 2009-02-15
forum: Virtualisation
---

### Post by marcgh on 2009-02-15
My Host OS is Ubuntu 8.10 / Guest is windows XP SP3.
I have installed Sun Virtual box 2.1.2 with Guest Additions.

All is working perfectly but I would have one more facility:

I have 3 other harddisks + the one where Ubuntu & Vbox is installed on.

When I am in Ubuntu I can access all 4 disks ( mount) but in Vbox / XP I can only 'see' the current XP disk of 10 Gb.

I there any way to access the data on all the hard disks?

Thank you for your help,
Marc

---

### Post by marcgh on 2009-02-17
Anybody?

---

### Post by konqueror7 on 2009-02-17
have you tried adding them as permanent shared folders in vbox?

---

### Post by marcgh on 2009-02-18
Hi konquerror7,

Thanks for your suggestion.
I am afraid I have to ask you a, maybe, dumb question: How do I do this, I can't even see this other HDD once I am in XP / Virtual box ?

Many thanks,
Marc

---

### Post by ubersolid on 2009-02-18
You need to edit the setting for you virtual machine. Close it if it is running. and open upp virtualbox, select your guest and click settings --> Shared Folders, click on the folder icon to the right and browse to a folder you want to maek available. You can later find it in our guest OS by browsing the network and virtualbox... forgot the exact name.

---

### Post by marcgh on 2009-02-19
Hi ubersolid,

This fixed my problem!

Thanks man,
Marc

---

### Post by Brigrat on 2009-02-19
Has anyone got active sync to work through Vbox?  My WM6.1 phone is fighting every other possible way that I have tried to set up a sync.

---

