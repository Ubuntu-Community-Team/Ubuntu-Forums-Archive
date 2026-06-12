---
title: "VMware"
date: 2008-01-14
forum: Virtualisation
---

### Post by Javawag on 2008-01-14
Hi all,

No idea where to post this on here, so move this thread if necessary! It's more a problem with VMware and Windows XP mainly... but maybe someone knows here?

I've recently started properly considering switching away from my Windows installation to Ubuntu, but I need Windows for some apps... so I tried using VMware using my existing XP installation. I followed a tutorial on how to do this, setting up the .vmx and .vmdk files with information about my hard drive's geometry and extracting the .mbr file... no problem. I set the RAM to 192MB as I only have 512MB RAM in my system in total... Anyway, I booted Windows through it, and as I logged into Windows, it told me Windows needed to be activated again (I assume as it sees the RAM as a hardware change?) and it would not let me do this and logged me out again!! I have a legal version of Windows, so any suggestions on how to get round this (other than formatting and doing a full Ubuntu install XD)?!

- Javawag

---

### Post by rechick on 2008-01-15
If you go to the vmware web site there is a convert utility you can install. It will actually create a VMWare machine based on your existing computer complete with all installed programs, etc., Then run this in VMWare on the same physical machine. Since the CPU and mainboard will match it shouldn't complain about the license. Memory changes don't trigger a license update but CPU, mainboard and HDD identification do.

---

### Post by Javawag on 2008-01-15
That sounds great! Although my Windows PC takes up around 100GB and my Linux partition is only 4GB... so do I need an extra 100GB to store it as a virtual machine?

- Javawag

---

### Post by Javawag on 2008-01-15
Sorry to double post. Just to say, I re-activated Windows using my product key on my computer and it was fine... however, when I next loaded Windows up, it told me my "hardware had change significantly" and that I needed to re-activate. I put in my key and it now tells me that I've used the key on too many computers (just the one...?!). It gives the option to have it remind me later, but when I click that, Windows crashes... usefully. So I'm in Ubuntu again... how do I get back into my Windows install?!

- Javawag

---

### Post by veloce on 2008-01-16
> **Javawag said:**
> Sorry to double post. Just to say, I re-activated Windows using my product key on my computer and it was fine... however, when I next loaded Windows up, it told me my "hardware had change significantly" and that I needed to re-activate. I put in my key and it now tells me that I've used the key on too many computers (just the one...?!). It gives the option to have it remind me later, but when I click that, Windows crashes... usefully. So I'm in Ubuntu again... how do I get back into my Windows install?!

- Javawag

You've run into the traditional Windows activation problem.  Yes, every time you switch the way you use windows on your machine the activation software will think you are using a different machine.

I've never managed to get around this with the convert tool and have only FOAF stories that it has ever worked.  YMMV.

Otherwise you have three choices:
1. Ring up M$ every time you switch and get an activation code.  
2. Get an illegal copy of XP that bypasses the activation system
3. Pick one way of using XP and stick with it.

I chose 3.

---

### Post by Javawag on 2008-01-16
Grr, I hate the activation system on Windows!! While 2 sounds almost tempting, I can't go with 3 because I often use Windows for games development using Direct3D... and that's something that VMware doesn't support as it lacks video hardware support... AFAIK. 

I've decided that M$ won't be very useful if I phone them up, and my hard drive is almost full and my Linux partition is only 3GB... thus i figured a reformat and repartition would do it good... And then I'll use Linux and Windows separately and wait for wine to catch up.

Unless I borrow someone's XP install disc (I only have a recovery disc not an XP install disc) and install XP to a virtual machine... that could work too for simple Windows things inside Linux...

Anyways, this post is long enough already XD! Thanks for your help and I'll be wiser for next time... now to get to backing up 140GB of files... fuuun!

- Javawag

---

