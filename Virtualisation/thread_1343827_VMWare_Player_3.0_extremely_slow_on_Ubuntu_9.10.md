---
title: "VMWare Player 3.0 extremely slow on Ubuntu 9.10"
date: 2009-12-02
forum: Virtualisation
---

### Post by pdwOnline on 2009-12-02
I upgraded ubuntu to 9.10 and VMware player to 3.0. Now, my VM images are runnung extremely slow. They used to run twice as fast hosted by Ubuntu that Windows XP, but the same images now run way faster hosted by Windows XP. (so VM image runs oke)

have 4Gig ram and apply 2g to the VM image. Re-installed Ubuntu and VMware from scratch but the VM's are unworkable slow. (sometimes even hangs Ubuntu for 15 minutes..)

AnyOne?

---

### Post by smithji2005 on 2009-12-14
Having the same problem here, 4GB of RAM - 2GB dedicated to VM and it's intermittantly locking up and slow to respond.

---

### Post by stephenzho on 2009-12-15
I have the similar but worse problem. 

Right after I started the VMPlayer with the guest OS win7, the whole Ubuntu 9.10 system frozen. I could not move the mouse; could not even ssh into the Ubuntu system. 

The only thing left for me to do is press the power button.

I have a brand new Dell Optiplex 960 (with 4GB memory), and the guest os (wiun7) has 2GB memory.

Should be an ideal environment for the VMware, but it turned out be a disaster.

I could not using the VMware at all.

Any solution?

THanks.

---

### Post by fjgaude on 2009-12-15
Well, I  have no suggestons since my system, with 4 GB and only 512 MB dedicated to the VM WinXP, works perfectly, and very fast with Player 3.0.

---

### Post by bturrie on 2010-03-22
My winxp virtual machine was lagging badly. So, I tried several things mostly focusing on virtual machine temporary storage files. I added the following to my *.vmx file

## new stuff
mainmem.backing = "named"
MemTrimRate=0
sched.mem.pshare.enable = "FALSE"
mainMem.useNamedFile = "FALSE"
prefvmx.minVmMemPct = "100"

## end addons

This helped a little--maybe. 

After poking around a bit I discovered that my virtual machine's disk was nearly full and badly fragmented. I had so little space left I couldn't even defragment. Okay I should have caught this earlier.

Anyway I increased the disk size following the stems on the vmware site, then defragmented. Just for grins I cleaned the registry as well. The virtual machine is running just fine now.

---

### Post by moontumbo on 2010-12-29
Thanks for the info.  It really helped me.  I was looking all over, and hadn't thought to look inside the VM.  I was thinking it would've given me some "disk full" type of messages inside, but it looks like I need to keep a closer eye on it manually.
Thanks again!

---

