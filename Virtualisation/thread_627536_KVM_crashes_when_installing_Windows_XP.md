---
title: "KVM crashes when installing Windows XP"
date: 2007-11-30
forum: Virtualisation
---

### Post by Oguz286 on 2007-11-30
Hello everyone,

I have a problem with installing windows xp using kvm. I followed the ubuntu wiki on using kvm (like pressing F5 and selecting Standard PC). I do everything it says there but kvm segfaults  when windows is trying to format the virtual drive. I just get Segmentation Fault(core dumped) and that's it.

The funny thing is that this worked before on my previous Ubuntu Studio  7.10 installation. I reinstalled everything because i wanted to use lvm2 so that should be the only difference between my current and previous Ubuntu installations. Using just qemu works fine (but offcourse slow). After the initial copying of the installation files, i can use kvm to install winxp just fine so my guess is that i can't format the virtual drive with kvm for some reason.

I have a Q6600 and i've got the kvm-intel module loaded and my user is added to the kvm group which works fine.

Does anyone have a clue?

EDIT: I just found out another thing. When using kvm all my programs crash randomly (opera, exaile, etc.) so i guess there is something seriousely wrong with my kvm. Could it be because of lvm? All my partitions are lvm (except for /boot). Maybe that has something to do with it. If i can find out what's wrong i could file a bugreport, but i'm not sure what is going wrong.

---

### Post by giampierosalvi on 2008-04-07
Hi,
I get the same problem on a Vaio VGN-SZ3HP/B. Everything goes fine if I run with the -no-kvm option (software emulation): I can install and run windows XP. However, when I run with hardware virtualization, it gives me segfault right after formatting the NTFS partition (the last thing I see is 100% progress report).

I also tried to run the image that I installed using software emulation without the -no-kvm option. In this case I get segfault at the screen showing Windows XP logo and a progress bar that moves back and forward sidewise.

Any suggestions?
Thank you
Giampiero

---

### Post by giampierosalvi on 2008-04-07
I forgot to say: I'm using kernel 2.6.22-14-rt (real time). I tried to boot into the 2.6.22-14-generic to check if that made any difference, but 2.6.22-14-generic does not boot anymore.

Giampiero

---

### Post by Morimando on 2008-08-08
Try not to use the Quick Format Option.
Mine crashed as well, but when i formatted the drive using the normal option, it worked just fine.

---

### Post by ktulu73 on 2008-08-09
I never had such problems.
I yesterday installed a win2k3 server and a winxp, I always use quick format.
But I compiled kvm from latest source (kvm72).

---

### Post by Yann2 on 2008-08-10
Is usual, I got the same problem here. Starts the install with virt-install *without* hardware acceleration. At some point it will reboot in graphical mode to continue the install. At this stage, you can edit the XML definition, replace qemu with kvm, redefine the VM (using define in virsh), and your VM will be accelerated.
I got one accelerated XP machine running on KVM/Ubuntu 8.04, works fine :)

---

