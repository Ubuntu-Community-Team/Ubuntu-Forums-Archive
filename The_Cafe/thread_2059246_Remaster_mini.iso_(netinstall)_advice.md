---
title: "Remaster mini.iso (netinstall) advice?"
date: 2012-09-17
forum: The Cafe
---

### Post by mips on 2012-09-17
Ok I don't even know where to start. From the bit I've googled most of these remastering utils seem to be for livecd/desktop images.

Let me explain a bit more.

I did a minimal install of Ubuntu 12.10 from the [mini.iso]("http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/") so the base system was essentially pulled of the net.

What I would like to do when 12.10 gets released is to copy all the packages I have install lying in my /var/cache/apt to the mini.iso.
I would also like for the installer to know the packages are on the cd and there is no need to download them from the net unless something is missing.

I do NOT want to re-download any of the packages I already have lying in my cache unless maybe there are newer versions available but I can live without this. Oh and I don;t want to create a desktop/livecd of my current install.

Any advice is welcomed.

---

### Post by Paqman on 2012-09-17
[APTonCD]("http://aptoncd.sourceforge.net/")?

The other alternative is to host your own mirror, but that's like using a sledgehammer to crack a walnut. Or you could just install your base system using the mini.iso, then simply copy all your .debs into the new /var/cache/apt/archive.

FWIW, most of the packages will be different in 12.10, so there's not a lot to be gained by doing this, but if you've got severe bandwidth restrictions I can see why you'd want to reduce your download.

---

### Post by mips on 2012-09-17
Thanks but that does not meet my needs. I specifically want to remaster the mini.iso

---

### Post by Lightstar on 2012-09-17
[http://www.remastersys.com/]("http://www.remastersys.com/")

Seems like a popular choice.

You can install your stuff, and save your whole system as a .iso.
You can choose to include or excluse your personal /home and data.

---

### Post by mamamia88 on 2012-09-17
> **mips said:**
> Ok I don't even know where to start. From the bit I've googled most of these remastering utils seem to be for livecd/desktop images.

Let me explain a bit more.

I did a minimal install of Ubuntu 12.10 from the [mini.iso]("http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/") so the base system was essentially pulled of the net.

What I would like to do when 12.10 gets released is to copy all the packages I have install lying in my /var/cache/apt to the mini.iso.
I would also like for the installer to know the packages are on the cd and there is no need to download them from the net unless something is missing.

I do NOT want to re-download any of the packages I already have lying in my cache unless maybe there are newer versions available but I can live without this. Oh and I don;t want to create a desktop/livecd of my current install.

Any advice is welcomed.why not just look up what you have installed and then make a bash script to reinstall in on a fresh install?   or just upgrade?  certainly should be possible.

---

### Post by cariboo on 2012-09-18
I understand what you are trying to do, and it looks more like a scripting matter than anything else. I'd suggest you have a look how the alternative iso for previous versions is setup, and use it as a guide. 

Aren't you trying to defeat the purpose of the mini/netisnt iso, which is to get the latest packages, and not have to update when you are done?

BTW which should see wireless support in the mini/netinst iso within the next week or so, if it hasn't been added already.

---

### Post by mips on 2012-09-18
> **cariboo907 said:**
> 
Aren't you trying to defeat the purpose of the mini/netisnt iso, which is to get the latest packages, and not have to update when you are done?


Yes I probably am, I'm more trying to create my own alternate installer in a way with the functionality of both.

I do intend to have the latest packages on the iso as of the time of release for 12.10

I know nothing about scripting but I'll take your advice and start comparing the contents of the mini and alternate installers. I was hoping there might be tool out there to do this similar to what is being used for the livecd images. I'll probably have a look at this as well [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

This is gonna involve a lot of googling and reading :biggrin:

---

