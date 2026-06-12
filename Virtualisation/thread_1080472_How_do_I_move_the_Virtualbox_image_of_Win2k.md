---
title: "How do I move the Virtualbox image of Win2k"
date: 2009-02-25
forum: Virtualisation
---

### Post by Robbyx on 2009-02-25
I have little space left on the drive where .virtualbox resides. I would like to move it or at least the image to a new location. Is it possible?


Robin

---

### Post by Jose Catre-Vandis on 2009-02-25
You should just be able to move it.

You will have to edit the settings on your machine to point to the new location

I have just tested this by moving an XP vdi from one partition to another and it worked OK. I even opened it up in a different XP machine once I had changed the hard disks around.

This was done on Xubuntu 8.10 with VBox 2.14

NB I only moved the vdi file, the rest of the stuff in .virtualbox hardly consumes any space.

---

### Post by Robbyx on 2009-02-25
What did you copy over to the new location. 

In order to be careful, I copied over the win2knew.vdi to the new location and renamed it in its old location to *.vdi.old.

In virtual media manager the win2knew.vdi still shows at the old location and deleting it in the manager is greyed out.



My current structure is 

.virtualbox
Compreq.dat
virtualbox.xm
win2knew.vdi
xpti.dat
    Machines
        Win2k
             Logs
                 Snapshots
                 {xxxetc}.vdi
                 {yyyetc}.vdi
                 ditto .sav

---

### Post by Jose Catre-Vandis on 2009-02-26
Copy won't work. If for safety's sake you want to make a copy, you have to hit the command line and use the clonevdi command like so:
```
VBoxManage clonevdi         <uuid>|<filename> <outputfile>
```
a real life example would be:
```
VBoxManage clonevdi ~/.VirtualBox/VDI/Win2K.vdi ~/Win2K_Clone.vdi
```
the new location of the cloned vdi can be anywhere you like. (You won't want to clone to $HOME, seeing as it is filling up!)

Once cloned, you can edit the machine settings to point to the clone. Once it's all working you can delete the original. :)

---

