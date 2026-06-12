---
title: "virtualbox and shared folders. Can't access them"
date: 2007-12-01
forum: Virtualisation
---

### Post by lime4x4 on 2007-12-01
I've tried the following command within windows and it fails no such name

net use t: \\vboxsvr\home/john

if i browse the network i can c the gusty computer but can't connect

Running gusty with xp as the vitrual machine

---

### Post by StuipedandUgly on 2007-12-01
put in
net use t: \\vboxsvr\john
and that should work

---

### Post by lime4x4 on 2007-12-02
Thanks you. That worked like a charm.

---

### Post by Delvien on 2007-12-02
you can also use "Map network drive" to have it automount :).

---

### Post by kamitsukai on 2007-12-02
sorry to hijack your post but  as your sorted now...ive used the above command and it works ok but i get an error box pop-up and then explorer has to restart! but only when i open the folder :( !?

---

### Post by lime4x4 on 2007-12-02
It works great on my end. I reboot and there there. I can browse them with no problem

---

### Post by sh4d0w808 on 2008-04-04
I have some problems, maybe somebody have experience in it:

The host is WinXP 32 SP2, the newest (1.5.6) VirtualBox installed and an Ubuntu 7.04 run in a virtual machine. All the possible updates installed, VirtualBox Additions are also installed.
I have set up a folder to use it as Shared Folders, but I do not know, where to find it in the guest Ubuntu.

Do anybody knows the right answer?

---

### Post by sh4d0w808 on 2008-04-04
Okay, guys, I have found it:

sudo mount -t vboxsf <share_on_host> <mountpoint> .

---

### Post by freqhack on 2008-05-17
> **StuipedandUgly said:**
> put in
net use t: \\vboxsvr\john
and that should work


Thanks. worked like a charm.

If these instructions are anywhere in the actual VirtualBox manual, I must be blind! ](*,)

---

### Post by irungk on 2008-06-25
guys, I've problem when accessing the shared folder
Host: Ubuntu 7.10
Guest: Win XP

I use :
net use t: \\vboxsvr\installer

and I got this error:
System error 1231 has occurred.

The network location cannot be reached. For information about network troublesho
oting, see Windows Help.

It's connected with the host.. even I post this message using guest os, but I can't access the shared folder.
Could you tell me how to do it?

Thanks

---

### Post by Ghuloomo on 2008-07-29
I have the same problem too

Ubuntu 8.4 host
windows xp guest
i just want to see all my partitions in the guest OS. I added them to the shared folder, but net use t: \\vboxsvr\Sony doesn't work, not even the net use x:
I have a partition that contains all my software, and Sony Vegas is in there. I want to access it so i install it :(
I have VirtualBox 1.6.2

---

### Post by gillberk on 2008-09-17
What is VirtualBox

VirtualBox is a virtual pc emulator like vmware. It has many of the features vmware has, as well as some of its own.
 Editions

VirtualBox is available in two editions: VirtualBox (OSE) and VirtualBox (Personal Use and Evaluation License (PUEL))
 VirtualBox (OSE)

VirtualBox (OSE) is the open source version of VirtualBox, which can be found in the community repository. It lacks some features such as USB device support and the built-in RDP server.

-------------

gillberk

[Internet Marketing]("http://www.drivenwide.com")

---

### Post by catalin.soare on 2009-08-01
Guys, does anybody know if this problem has anything to do with the physical location of the shared folder/partition file?
I mean I've got WinXP X64 installed on a .vdi file in a removable drive. So the location of the image file is like "/media/HDD/VM/X64.vdi".
The folder that I want to make accessible is /media. I also tried to make shared my home folder and this didn't work either...
Last time it worked was when the virtual partition was located in my home folder, and added /media as shared.

(I tried installing and reinstalling the Guest additions but nothing seems to work at all.) :(

---

### Post by guvnr on 2010-01-12
maybe it's my pc but, then again, it's quite a monster .. just had to wait a while (10 minutes!) and eventually my windows xp guest picked up on the Linux host shares.

did reboot, but that in itself didn't make any difference.

have had this before .. and it was the same deal.

---

### Post by abdusamed on 2010-05-18
i can't connect to my shared folder! my folder path is... which displays on the shared folder option when i select share... /home/bahie/Downloads

then in the xp virtual machine.. i type this in 'run'

net use t: //vboxsvr/Downloads
[error.. path not found]

then i try this

net use t: //vboxsvr/home/bahie/Downloads
[error..path not found]

like..what else am i suppose to do? runnin the latest updates...

---

