---
title: "Serious print server problems (6.06, HP9050"
date: 2006-06-22
forum: Server Platforms
---

### Post by kroxic on 2006-06-22
I just installed 6.06 server today and proceeded with many google searches and manuals to try and get samba, cups, and my printer ready for network sharing at work.  I have failed horribly.  I have no idea how to install the printer on the command line before i can even share it.  I did manage to get to the web admin page for cups but then when i tried to use a PPD file to install my printer (HP IJ9050) it would redirect me from the ip address to the hostname lj9050server.qtmaster.loc and it would fail to find it every time.  I have no idea what I am doing here and need some guidance.  Thanks

---

### Post by Iowan on 2006-06-23
There's another "driver" called **hplips**.  It reportedly doesn't play nice with CUPS - at least on Breezy.

---

### Post by NeoGreen on 2006-06-23
Is there a How-To page on setting up a print server?:confused:

---

### Post by ahobbs on 2006-06-25
I'm a noob myself, but I think at minimum you need to **apt-get install** the following packages:
**cupsys hplip* hpijs foomatic-filters**

Also, I believe you need to add cupsys to the shadow group if you want to use the cups web interface:
**sudo addgroup cupsys shadow**

A

---

### Post by Vogateer on 2006-06-25
:-D 

Thank you ahobbs!

I had configured printer sharing pretty easily with a desktop install of Ubuntu, but I tried to switch over everything to my server in the closet (hidden and out of the way), and had failed miserably.  Apparently I was missing one of the packages you mentioned, since once I installed those packages, the printer started right up, and every computer on the network is now printing to it!

Thank you, thank you.

---

