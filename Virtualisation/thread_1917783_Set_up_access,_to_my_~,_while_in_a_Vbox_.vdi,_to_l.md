---
title: "Set up access, to my ~, while in a Vbox .vdi, to listen to my music, while in it?"
date: 2012-01-30
forum: Virtualisation
---

### Post by mikodo on 2012-01-30
I'll do the reading, if anyone suggests any... I can do that!

I plan to clean install Xubuntu 12.x and bring my  ~ data forward (docs, pics, FF and TB profiles, etc., by cp from a backup)... I can do that!

I am thinking of installing Vbox, into my next install (Xubuntu) and setting up a .vdi of Alpha and Beta versions of Xubuntu and Xfce, for testing, in a separate mounted partition... I can do that!

I want to file bugs for Xubuntu and Xfce, Alpha and Beta versions... I can do that!

How would it be best to:

Set up access, to my Hosts' ~, while in a Vbox .vdi, to listen to my music and such, while in it.


**Information Found: **


A couple of options are: **VirtualBox Shared Folders** (Optimized Samba), or **Samba** (alone), to share the folders from Xubuntu host -> Xubuntu Alpha/Beta  guest.


**VirtualBox Shared Folders:** Appears, to be the least amount of learning and the most direct to follow. 

[Shared Folders & Mounting guide]("http://www.virtualbox.org/manual/ch04.html#sharedfolders") (VirtualBox Documentation).

[Guest Additions]("https://forums.virtualbox.org/viewtopic.php?f=29&t=15679&sid=8f3c78111132689abd8beb50a6d5caab")   [Shared_Folders]("https://forums.virtualbox.org/viewtopic.php?f=29&t=15868&sid=8f3c78111132689abd8beb50a6d5caab")   (VirtualBox Forums).

[Virtualbox]("https://help.ubuntu.com/community/VirtualBox") [  VirtualBoxSharedFolders]("https://help.ubuntu.com/community/VirtualBox/SharedFolders")  (Ubuntu Community Documentation).


**Samba** **Shares:** Appears, would take more learning. Bodhi, disagrees but, I am not him. :>)

[Samba]("http://www.samba.org/") (Web-site).

[Samba 3.5]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/") (Official Reference).
     
[Samba]("https://help.ubuntu.com/community/Samba") (Ubuntu Documentation).

---

### Post by japzone on 2012-01-31
Definitly try to use VirtualBox Shard Folders first. It's the easiest to use. To use it you have to Setup and Boot your VM and then while the VM is running goto "Devices-->VirtualBox Guest Editions", a CD will be mounted and you need to run the Installer script(*.sh) from it in Terminal with Root permission(sudo). Shared Folders should appear in "/media"

Only use Samba if you can't get the other to work. Installing Samba is simple enough, setting it up can somtimes be a pain(especially in Unity in Ubuntu 11.10+) but it works fine. For Xubuntu just follow these directions for both your Host and Guest OSs([**here**]("http://www.youtube.com/watch?v=0gdt8dVYXzM")), They are for an older version of Xubuntu but not much should have changed however you can skip the last password part as you won't need it. The Shared Folders should appear in "Network-->Windows Shares-->WORKGROUP" With Samba there's also the possibilty of accessing your Guest from other PCs on your Network, to do so open the VM settings and in "Network" change NAT to Bridged and select your Network Device, this will allow you're Guest to appear as a Standalone PC on your Network.

---

### Post by haqking on 2012-01-31
shared folders, it takes like 5 seconds to setup with a few mouse clicks.

---

### Post by mikodo on 2012-01-31
It's settled then. Vbox shared folders, first!

Thanks guys, for your advice.

---

### Post by mikodo on 2012-01-31
japzone,

Too bad the link doesn't work. Do you have any others?

Thanks.

---

### Post by japzone on 2012-01-31
> **mikodo said:**
> japzone,

Too bad the link doesn't work. Do you have any others?

Thanks.

Woops, sorry. The link got messed up somehow, but I fixed it.

---

### Post by mikodo on 2012-01-31
> **japzone said:**
> Woops, sorry. The link got messed up somehow, but I fixed it.
Great! Thanks. That is so cool, the way that guy shows it. I'll have to look for more of his.

:>)

---

