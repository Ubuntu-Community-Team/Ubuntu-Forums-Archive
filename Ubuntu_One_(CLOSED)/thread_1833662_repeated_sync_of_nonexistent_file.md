---
title: "repeated sync of nonexistent file"
date: 2011-08-26
forum: Ubuntu One (CLOSED)
---

### Post by Docaltmed on 2011-08-26
U1 is trying to sync a file which doesn't exist on any of the devices attached to the account nor in the cloud folder. I've tried using U1sdtool to stop it, including the following commands:

u1sdtool --refresh-shares
u1sdtool --refresh-volumes

u1sdtool --rescan-from-scratch

I've also tried actually creating a file of the same name that it keeps trying to sync in the hopes that it will latch onto that one instead, but no go. I tried deleting that file, but no go. It constantly loops through the same nonexistent file, over and over and over and over and over...

It also only does this on one device. It does not do that on the other devices.

And, yes, I've done u1sdtool --waiting, and there is the nonexistent file, on the list, with all of the real files that actually do need to be synced backed up behind it.

What do I do?

---

### Post by Docaltmed on 2011-08-27
Can anybody tell me how to clear the queue?

---

### Post by sffvba[e0rt on 2011-08-28
I am just replying in the hopes of getting a lollipop or ice cream (cool that you got Ubuntu One to work under Kubuntu btw...)

Sorry for having no idea what the problem is or how to fix it :/

I assume you used the info here ([https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl](https://wiki.ubuntu.com/RomanYepishev/UbuntuOne/ClientControl)) to do all the stuff in the OP... from this I can't see any commands you haven't tried yet.  Could you maybe just remove the Ubuntu One File Sync from the offending device.  Then delete any hidden folders under home and then re-install and re-start and see if you have better luck?!


404

---

### Post by dniMretsaM on 2011-08-28
> **Docaltmed said:**
> U1 is trying to sync a file which doesn't exist on any of the devices attached to the account nor in the cloud folder. I've tried using U1sdtool to stop it, including the following commands:

u1sdtool --refresh-shares
u1sdtool --refresh-volumes

u1sdtool --rescan-from-scratch

I've also tried actually creating a file of the same name that it keeps trying to sync in the hopes that it will latch onto that one instead, but no go. I tried deleting that file, but no go. It constantly loops through the same nonexistent file, over and over and over and over and over...

It also only does this on one device. It does not do that on the other devices.

And, yes, I've done u1sdtool --waiting, and there is the nonexistent file, on the list, with all of the real files that actually do need to be synced backed up behind it.

What do I do?

Ok, did the file ever actually exist? Or did it just randomly get the file name from somewhere? (btw lollipops and ice cream sound really good).

---

### Post by Docaltmed on 2011-08-31
The solution turned out to be really weird. Though the file did not exist on *either* of the devices connected to U1, it existed *only* in the cloud (and from its name, I'm pretty sure that it did actually exist on one of the devices at some point). 

What I did not realize is that the U1 client, when you click on the "cloud folders" tab, does not show you the actual cloud folders. It shows you the synced folders ON YOUR COMPUTER. To actually see the cloud folders, you have to log in via a browser and look from there...

...which is where I found an empty file with the name of the file that was repeatedly downloading to my computer. I deleted it via the browser interface, and after a couple more shots at trying to download it, my U1 syncdaemon kicked it off the queue and started working on the other files.

Now back to normal.

EDIT: Thank you for your help, my friends. Let me know where you would like the lollipops delivered...would a local homeless shelter suffice?

---

### Post by sffvba[e0rt on 2011-09-01
> **Docaltmed said:**
> EDIT: Thank you for your help, my friends. Let me know where you would like the lollipops delivered...would a local homeless shelter suffice?

Sounds like a plan (glad you got it sorted out in the end BTW...)


404

---

