---
title: "Any performance improvement if I double ram?"
date: 2010-10-27
forum: Virtualisation
---

### Post by Quackers on 2010-10-27
I am running Maverick in the laptop below. I am also running VirtualBox 3.2.10 r66523 and Windows 7 is the guest OS. I am new to virtualization so if I miss anything out just ask.
I have allocated 1 core to VB and 960MB of ram (of 2GB in total). Performance is a little bit slow, although everything works.
I was wondering whether an increase of ram, say to 4GB total and 2000MB allocated to VB would see an increase in performance. 
Also is it normal for the allocated cpu to be maxed out while the system is loading? I would imagine that it is normal, and I'm suspecting the increase in ram would reduce this time, but as I'm not certain where the bottleneck is I'm looking for advice please.
Thanks

---

### Post by yesrno on 2010-10-27
Kinda depends what you're doing or trying to do on the Windows 7 guest. And is the guest 32 or 64 bit ? If your using it for heavy photoshop-like applications or something than yes, it would help. If your just using it for some test thingy's to play around with than i'm not sure if it's worth upgrading. But thats just my opinion.

---

### Post by Quackers on 2010-10-27
The host is 64 bit Maverick but the guest is 32 bit Windows 7. I am not using the guest for anything really resource intensive. No photoshop or video editing, nothing like that. Mostly playing poker :-)
Thanks for you input.

---

### Post by mr chip on 2010-10-28
Windows 7 likes to have at least 2GB of RAM, so you should notice less degraded performance with more RAM.  That said, Windows 7 also like to do plenty of disk I/O, so having the virtual disk image on a separate HDD to your host operating system will help.  

I notice that some variants of your laptop have two HDD bays, which is unusual for a laptop but could prove handy in your situation.  A HDD upgrade might also help, if your system has slow 4200rpm drives.  

FWIW, I run 3 VMs for dev work, and each one of those has its own 10k RPM HDD.

---

### Post by the8thstar on 2010-10-28
If you can dedicate 2Gb of RAM to Vista/7 VM, then you can deactivate the swapfile and put it all to RAM. Especially if you are only running a fe programs at a time, you should notice an improvement in speed.

For the record I did just that on my Core Solo laptop with a 'real' Windows 7 install. It runs perfectly fine.

---

### Post by Quackers on 2010-10-28
Yes, my laptop has 2 hard drives (originally set up as raid 0 ) and yes they are slow, at 4200 rpm. Apparently Sony puts a big emphasis on not wasting space :-) That is the main letdown to the whole laptop (except for a locked bios). I have considered HDD upgrades, particularly as I have gone through 3 sets of hard drives in less than 3 years (all replaced by Sony free of charge, forunately) but am somewhat concerned with the power requirement of faster drives. Is that likely to be a problem?

---

### Post by Quackers on 2010-10-28
Monsieur le huitieme etoile how would I do that please? :-)

---

### Post by mr chip on 2010-10-28
Generally, newer HDDs are more efficient than older ones.  If they're 7200rpm drives, you may need to consider their heat dissipation.  HDD manufacturers should provide technical info for current and past models on their websites, so you can look up the current HDDs and make sure the replacements don't draw more power, and are the same physical dimensions.

I'd look at disabling the Windows 7 Superfetch service before disabling the page file (google those terms, you'll find info on how to do it).  Superfetch will continually cache stuff in the background, generating disk I/O that can bog down a low powered VM (it was superfetch being too aggressive that made Vista seem to thrash the HDD).

---

### Post by Quackers on 2010-10-28
Thanks for that mr chip :-)

---

### Post by mr chip on 2010-10-28
no worries - have fun :)

---

### Post by Googleler on 2010-10-28
Windows 7 works pretty well with just 1GB of RAM. I think you'll see an improvement if you add memory modules. However, if you need high performance, I think it's better to keep the computer as it is.

---

### Post by the8thstar on 2010-10-30
> **Quackers said:**
> Monsieur le huitieme etoile how would I do that please? :-)

Sure thing! I'm not a 100% sure of the name of each actions since I'm using a French version of Windows 7, however the path I'm giving you is correct:

[LIST]
[*]Click on the Orb
[*]Select Computer
[*]In the window, select "System Properties"
[*]In the next window, click on "Advanced System Properties"
[*]Yet another window pops up, select "Performance"
[*]In the window, choose the "Advanced" tab
[*]Click to select "Modify" under "Virtual Memory"
[*]Uncheck the automatic management of the Virtual Memory and set the size to "No Swap File", then "Set" and "OK"
[/LIST]

Next time you restart you should be good to go.

Please PM me to tell me how it went.

---

### Post by DanPerecky on 2010-11-03
Had 2G, added 2G by discarding both 1Gs and buying 2 - 2Gs = 4G total. Problem is that XP and Linux both use 3G max.

It looks to me like a BIOS limitation.... No BIOS sw updates to be had.

=================================================

Laptop- Toshiba A105 c. 2006.

---

### Post by NightwishFan on 2010-11-03
You need the PAE kernel to use 32-bit linux with more than 3gb of RAM. Search "PAE" in synaptic.

---

