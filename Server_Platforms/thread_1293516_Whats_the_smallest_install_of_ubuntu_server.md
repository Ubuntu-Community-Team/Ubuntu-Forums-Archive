---
title: "Whats the smallest install of ubuntu server?"
date: 2009-10-17
forum: Server Platforms
---

### Post by dv-design on 2009-10-17
Im considering using Ubuntu Server to run a custom NAS, but im wondering what the smallest required space needed for such an install is. Is it possible to get it under 256mb?

---

### Post by hal10000 on 2009-10-17
If you want to make it as small as possible, you should think about using another distribution, such as gentoo (or a similae one) which lets you full control about the packages you need to get your only NAS working

I remember some years ago i had a special debian server distribution, which had a menu to install only special services, but i can't remember if NAS was one of them.

---

### Post by kerry_s on 2009-10-17
the ubuntu base is pretty big as far as base installs go, just give is a go & see if it's as tied together as the desktop.

you could try debian much smaller to start & not as tied together package wise.

a little tip, to keep the size down:
**sudo apt-get install --no-install-recommends**

---

### Post by volkswagner on 2009-10-17
If you just need NAS, you may consider [FreeNAS]("http://www.freenas.org/").

From the FreeNAS site: "FreeNAS takes less than 32MB once installed on Compact Flash, hard drive or USB key." 

I know it's not Ubuntu, it's not Debian, heck it isn't even Linux, but it sure is small.

---

### Post by dv-design on 2009-10-19
> **volkswagner said:**
> If you just need NAS, you may consider [FreeNAS]("http://www.freenas.org/").

From the FreeNAS site: "FreeNAS takes less than 32MB once installed on Compact Flash, hard drive or USB key." 

I know it's not Ubuntu, it's not Debian, heck it isn't even Linux, but it sure is small.

Yea ive taken a look at FreeNAS and similar things, im just afraid that its too little and Ubuntu is too much. Was hopeing that Ubuntu server would be smaller, or that there might be a stripped down version of it.

---

### Post by hal10000 on 2009-10-19
Yes, of course ubuntu server is smaller than an ubuntu desktop installation.
But why do you say that FreeNAS is too small, iwould'nt care about it's size if it fits my needs.

---

### Post by dv-design on 2009-10-19
> **hal10000 said:**
> Yes, of course ubuntu server is smaller than an ubuntu desktop installation.
But why do you say that FreeNAS is too small, iwould'nt care about it's size if it fits my needs.

When i said FreeNAS was too little and Ubuntu too much, i didnt mean in size i meant in features.

My concern for size is based on the desire to install the linux software on a 256mb flash rom, so that all the drives are purely storage.

Just curious if there is a linux distro out there thats stripped down to under 256mb, is kept current, and allows for using webmin, mdadm, and samba.

---

### Post by hal10000 on 2009-10-20
Maybe you are happy with damn small linux: [http://www.damnsmalllinux.org/index.html](http://www.damnsmalllinux.org/index.html)

---

### Post by dv-design on 2009-10-20
DamnSmallLinux looks interesting, have you used it before, which linux distro is it based on?

Can it support things like webmin, mdadm, samba?

---

### Post by hal10000 on 2009-10-20
I have it running on a ten thirteen year old ibm notebook, it's main purpose is as a desktop system for harware-limited computers, but i guess you can run it without a graphical desktop and with almost any linux-software you like.

You may take a look at  [http://distrowatch.com/](http://distrowatch.com/), where you can look for other distributions to fit your needs.

---

### Post by juancarlospaco on 2009-10-20
**chroot**

---

### Post by The Real Dave on 2009-10-23
+1 for FreeNAS, its a tiny, but great OS :) Whole thing is admined through a Web GUI. I have it running on two NAS server's, the main one of which does file, printer and media sharing. FreeNAS also lets you do stuff like bittorrent, and both my servers use software RAID. 


The thing I reckon though, is that it doesn't have to take up any space on your HDD at all. In my servers, FreeNAS boots from a CD, which loads itself into RAM (uses maybe ~60Mb), and takes it configuration file from a USB drive, though a floppy can be used too. That means that all of my harddrive space is available for files, and, more importantly, since the OS is running in RAM, the disks can spin down when not in use, lowering their temperatures, giving better lifespan, and making my server quieter because I don't need as many fans to cool it :) 

I seriously reccomend FreeNAS. Its got a load of features, in a tiny packages, which is all access through a GUI. What more could you need?

---

### Post by windependence on 2009-10-24
> **dv-design said:**
> When i said FreeNAS was too little and Ubuntu too much, i didnt mean in size i meant in features.

My concern for size is based on the desire to install the linux software on a 256mb flash rom, so that all the drives are purely storage.

Just curious if there is a linux distro out there thats stripped down to under 256mb, is kept current, and allows for using webmin, mdadm, and samba.

It is certainly NOT small on features. You do not need webmin (a security risk) because it runs it's own web GUI, and runs any service you can imagine, even a torrent server if you want. It runs on FreeBSD which IMHO is much more stable and robust than any flavor of Linux. I have been running production storage on it for more than 4 years even though I probably shouldn't and I have had zero problems. It is easily installed on a 256MB flash card. You can bind almost any number of NICs together to increase bandwidth and you can do RAID right from the GUI. It even monitors your HD temps. It's definitely NOT lacking in features.

-Tim

---

