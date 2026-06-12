---
title: "Testing slipstreamed XP installation cds"
date: 2009-07-27
forum: Virtualisation
---

### Post by adempewolff on 2009-07-27
Hello, I am in the process of creating a slipstreamed xp installation cd for unattended install and ahci support (with the goal of eventually creating a a dvd that will install a multi-boot with ubuntu and diagnostic tools as well).

In order to avoid wasting a lot of cd-r's the howto I have been following recommends using virtual box or something like it to test the iso.  I have no experience with any sort of virtualization but am willing to give it a try but have a couple questions:

-would it be relatively easy (will it save me time from burning a new cd-r every time and installing on a reformated partition) to set up a virtualization that I could test install xp into?  I ask because it seems people use it to test how software runs on other configurations, whereas I just need it to run on my configuration, I just don't particularly want to waste CD-rs and am at a lack of ideas as to how I could otherwise install windows from an image.

-In the sticky threads it seems openvm is recommended in one but then not even mentioned in the Jaunty thread.  Which would people recommend in Jaunty?  I stumbled across the documentation for KVM in the ubuntu help pages would this work for me?

-how much free space will I need free to download and install virtualization software and run the virtualization to install a copy of xp?

-any other thoughts any thinks I should take into consideration?

Thanks!

---

### Post by stlsaint on 2009-07-27
well i will speak from experience from windows as i have yet to do ubuntu virtual yet...but i too am into slip streaming and unattended installs and i can tell you that YES a vm would serve your purpose as you want it to. I test all software on a vm before i put it on any of my machines for good. yes all you have to do is point the vm to boot from your iso( which is done during the setup of your vm) and it will boot and install just as if it was from a disc( as long as you make the disc bootable correctly)!! you dont need much space( you can set how big you want the hard drive to be and how much memory will be given to this vm machine, etc etc...just remember that you are sharing resources with your host os so you cannot run more than one vm at a time! DO NOT RUN TWO VM'S AT A TIME WITH THE HOST!!! THAT WILL BE BAD FOR BUSINESS!! thats if you are working of 2gb ram...4 and above you should be good depending on how much ram you give your vm's!

hope this helps!!!

---

