---
title: "Virtual PC Recommendation"
date: 2008-05-01
forum: The Cafe
---

### Post by Green Tree Python on 2008-05-01
To any newbies to Ubuntu, such as myself. To get used to working within the Linux environment,I just successfully installed both Kbuntu 6.06 and Ubuntu 6.06 in MS Virtual PC. 

If your wanting to use Virtual PC, the 6.06 versions on these distros are the only ones that work in Virtual PC, because of a "slight" mouse integration issue that MS either refuses to fix or programmed into the software on purpose.

There are other choices of virtualization software, such as VMware and Virtualbox that work great with all distros of Linux

Good luck,

GTP

---

### Post by diablo75 on 2008-05-01
Or you could just dual boot your PC with Windows and Ubuntu **8.04** with ease, thanks to the new Windows-based Ubuntu installer Wubi.  If you don't like Ubuntu, just open your Control Panel>Add/Remove Programs, and uninstall Ubuntu.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Green Tree Python on 2008-05-01
Diablo

You can do that, but the virtualization software is a little safer bet. Because if you were to dual boot the GRUB could cause a corrupted boot sector. Which would make it impossable to boot either 8.04 or Windows.

Thnxs,

GTP

---

### Post by kk0sse54 on 2008-05-01
Although you can use the liveCD without doing any harm to your computer VMware was the deciding factor for me to switch to linux as it allowed me to add/remove software and use it as my main desktop for a few weeks and i highly recommend it to anyone thinking about switching to linux but they are still unsure.

---

### Post by Foghornleghorn on 2008-05-01
> **C!oud said:**
> Although you can use the liveCD without doing any harm to your computer VMware was the deciding factor for me to switch to linux as it allowed me to add/remove software and use it as my main desktop for a few weeks and i highly recommend it to anyone thinking about switching to linux but they are still unsure.

Or...like me a complete noob to Linux you could just be brave and dual boot with windoze.Loving it!!! Loving it!!!:)

---

### Post by aysiu on 2008-05-01
I recommend VirtualBox and have a tutorial on how to install Ubuntu within XP (any version, not just 6.06):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by maniacmusician on 2008-05-01
> **aysiu said:**
> I recommend VirtualBox and have a tutorial on how to install Ubuntu within XP (any version, not just 6.06):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
ditto

---

### Post by FuturePilot on 2008-05-01
> **aysiu said:**
> I recommend VirtualBox and have a tutorial on how to install Ubuntu within XP (any version, not just 6.06):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

+1 VirtualBox is great.

Virtual PC is horrible especially with a Linux guest.

---

### Post by maniacmusician on 2008-05-01
[yuck] it's horrible, period.

---

### Post by FuturePilot on 2008-05-01
> **maniacmusician said:**
> [yuck] it's horrible, period.

yes, that too:lolflag:

---

### Post by SuperSon!c on 2008-05-02
> **aysiu said:**
> I recommend VirtualBox and have a tutorial on how to install Ubuntu within XP (any version, not just 6.06):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

winnar!

---

### Post by riccaliolio on 2008-05-06
Hi All! I am new here in this forums but I am not really completely unfamiliar with Linux (been using it for some time now).

I am actually an MS XP user with a virtual machine running Ubuntu Hardy Heron. I was doing a search what Ubuntu users think is the best VM application, and I think 80% are using Virtual Box. .: below is my own cup of opinion:

-1 to Virtual PC because:
[INDENT]- not open-source[/INDENT]
[INDENT]- It IS Microsoft. .: I don't think they will make it work well with Linux because MS users will then appreciate Linux, thus reducing their revenue.. Hehe. ^_^[/INDENT]

+1 to Virtual Box because:
[INDENT]- works well with Linux[/INDENT]
[INDENT]- open-source[/INDENT]
[INDENT]- I use it![/INDENT]

Cheers!

---

### Post by inportb on 2008-05-06
> **diablo75 said:**
> Or you could just dual boot your PC with Windows and Ubuntu **8.04** with ease, thanks to the new Windows-based Ubuntu installer Wubi.> **Green Tree Python said:**
> You can do that, but the virtualization software is a little safer bet. Because if you were to dual boot the GRUB could cause a corrupted boot sector. Which would make it impossable to boot either 8.04 or Windows.

I'm afraid that is not so, Green Tree Python. Wubi makes use of the WinNT boot manager, not GRUB. It does not mess with the bootsector/MBR at all. I don't think you can get any safer than Wubi for dual-booting. There's a pretty significant disk access performance hit, though.

---

### Post by AK Dave on 2008-05-06
I use VirtualBox the other way around, running HH and using Vbox to launch XP. Fastest and most stable XP that I've ever seen, which isn't saying a whole lot. Its like putting lipstick on a pig: its still a pig.

---

### Post by maniacmusician on 2008-05-06
> **AK Dave said:**
> I use VirtualBox the other way around, running HH and using Vbox to launch XP. Fastest and most stable XP that I've ever seen, which isn't saying a whole lot. Its like putting lipstick on a pig: its still a pig.
I do the same. Or well, I used to -- I accidentally deleted my XP VM last year, and didn't notice until last week. :rolleyes: shows how much I depended on it though.

---

### Post by disconap on 2008-05-30
6.10 works as well.  Just got it to install and boot; the graphics issue can be sorted with these instructions:

[http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/](http://arcanecode.wordpress.com/2007/02/26/installing-ubuntu-610-on-virtual-pc-2007-step-by-step/)

They're for MS VPC 2007, but they apply to OSX VPC 7.0.3 as well...

EDIT:  Also, Virtual Box does not seem to have a PPC build, so those of us with G3s, G4s, and G5s are stuck with crappy MS VPC for now.

---

