---
title: "Software RAID without a RAID card?"
date: 2006-12-30
forum: Server Platforms
---

### Post by koolguynet on 2006-12-30
I would like to know if it is possible to do a software RAID 1 setup without a PCI RAID card or a RAID enabled motherboard.  If so, are there any instructions out there you can point me to?

---

### Post by baastie on 2006-12-30
Hi,

You could use mdadm ( man mdadm for the help file ) 

and maybe this link wil get you going

[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

cheers,

---

### Post by Martin-Robert on 2006-12-30
Hi

As a relative newbie on linux, just having set up my first server (Dapper Drake 6.06.1 (LTS)), I can tell you what I just learned: 

Linux generally supports software RAID, You just need two hard disks on your box, usually of equal size. Do not use any type of controller with Linux software RAID, that would confuse Linux, because the software RAID is meant to fully take over the function of such a controller.

How do you set it up?  Luckily, the setup-program in the Dapper Drake server edition fully supports installing software RAID, so you don't have to learn the mdadm commands (For the desktop edition, try with the so called "alternate CD"). You just have to learn the concepts, terms and abbrevations used by that setup. It is not a master of user friedliness, but after some experimenting, even I managed to finish the installation.  

You can also install LVM (Logical volume manager) on top of the virtual device (i.e. hard disk) created by the software RAID, which is a good thing because it gives you partitions which you can resize very easily.  

Tips:
- During setup of RAID / LVM there was an error message about the kernel not knowing about some setup changes, I ignored that error. Just check that all the settings are complete, I had to reenter some of them.
- First I used mount options which I found somewhere with google, after that I had errors during package installations. I started again, left all mount options at their default value, then these errors did not show anymore. 

[http://users.piuha.net/martti/comp/ubuntu/raid.html]("http://users.piuha.net/martti/comp/ubuntu/raid.html")

This is the first time I try to give help in the Ubuntu-Forum, so please give  feedback about usefulness.

Happy new year, I wish you and your Ubuntu-Installation good health.

---

### Post by Mike'sHardLinux on 2006-12-30
You **can** use Linux software RAID along with a RAID controller. Some of the RAID cards are not true hardware RAID, and if you have one of these, software RAID is probably your only choice. Also, You can build something like a RAID 10 array from a mix of hardware and software RAID.

I strongly recommend that you learn mdadm if you are going to use software RAID. You'll need those commands in the event you have to replace a drive or rebuild the array for any reason.

Basically, you can do what you want, but there's a lot more to know about the subject. For example, if you are thinking of building a RAID 1 with 2 drives that are on the same channel of your motherboard's IDE controller, you need to know that, often, when a drive in a RAID array fails, it can take out the whole channel. So if this happens, and both your drives are on the same channel,  well, then the RAID array didn't do much good. So keep your RAID drives on separate channels. (There is another reason to do this.)

[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID]("http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID")

[http://en.wikipedia.org/wiki/RAID]("http://en.wikipedia.org/wiki/RAID")

I just found this link, but haven't tried the how to:
[http://www.howtoforge.com/linux_software_raid]("http://www.howtoforge.com/linux_software_raid")
Keep in mind they are talking about Ubuntu 5.10. 

Good luck!

---

### Post by koolguynet on 2007-01-02
Thank you to all.  I will let you know what comes of it.

---

### Post by gregor171 on 2007-01-03
hi to add what i found about "fake" RAID controllers:
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

[http://www.linuxquestions.org/questions/showthread.php?t=470437]("http://www.linuxquestions.org/questions/showthread.php?t=470437")

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

I decided to buy na new "real" raid controller for my 2 sataII discs, since the preformance of the server is also important...

---

### Post by edafe on 2007-01-08
Software RAID-1 on Ubuntu 6.06:

[http://www.edafe.org/ubuntu/index.html#raid](http://www.edafe.org/ubuntu/index.html#raid)

Regards,
Edafe

---

