---
title: "I want to share folder between Host: XP, Guest: Ubuntu (in VirtualBox)"
date: 2009-01-18
forum: Virtualisation
---

### Post by spystalker on 2009-01-18
hello,
im newbie here.
Could anyone help me please.

I really really need help here
I follow the instructions on how to install the shared folder between ubuntu as Guest and XP as host , using VirtualBox.
i mount the ubuntu 8.10 into virtualBox . then after finished installing it, i run it again to use the ubuntu.

first , i clicked : Devices -> Install Guest Additions.
then i run it.
it seems it automatically mount the VBOXADDITIONS_2.1.0_41146 (25.9 MB)
BUT it doesn't work!
it said : Error autorunning software. Cannot find the autorun program.

anyone know what's the problem i got?

Thank you in advance anyone please help me!

---

### Post by spystalker on 2009-01-18
sorry  everyone, i solved it ;)
thanks!

---

### Post by Dedoimedo on 2009-01-18
Please elaborate on your solution so others can learn from it.
Likewise, you may want to mark the thread as solved.
Dedoimedo

---

### Post by spystalker on 2009-01-19
> **spystalker said:**
> hello,
im newbie here.
Could anyone help me please.

I really really need help here
I follow the instructions on how to install the shared folder between ubuntu as Guest and XP as host , using VirtualBox.
i mount the ubuntu 8.10 into virtualBox . then after finished installing it, i run it again to use the ubuntu.

first , i clicked : Devices -> Install Guest Additions.
then i run it.
it seems it automatically mount the VBOXADDITIONS_2.1.0_41146 (25.9 MB)
BUT it doesn't work!
it said : Error autorunning software. Cannot find the autorun program.

anyone know what's the problem i got?

Thank you in advance anyone please help me!

alright, i'll try explain it here. ;)
sorry for my english :D

first, i click the "Install Guest Additions"
then it will automatically mount the vboxadditions iso (25.9MB)

after that i manually go to the terminal and type in:
sudo /media/cdrom/VBoxLinuxAdditions-x86.run

so that it will install the additional tools for linux as guest in virtual box such as : shared folder & mouse integration.

then i go to Sun xVM VirtualBox tab Machine>Settings>Shared Folders. here i add a new shared folder. let's say the folder name as "ubuntu"
but it hasn't finished yet.

so i created an empty folder inside the ubuntu (to make it easy, i created the empty folder in my home folder, i name it as "shared") before mounting.

in the end, i just easily go to the terminal (as in terminal it will start from home) and type in:
sudo mount -t vboxsf ubuntu shared

it will prompt the password of current user that i'm using.

so finally i can use it ;) but i think i should manually type the "sudo mount -t vboxsf ubuntu shared" everytime i turn on my ubuntu virtual machine :(

---

### Post by spystalker on 2009-01-21
actually i refer to dedoimedo's website :oops:
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)
thank you dedoimedo:D

---

