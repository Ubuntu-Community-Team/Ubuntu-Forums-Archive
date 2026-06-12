---
title: "Dual boot virtualization?"
date: 2008-05-22
forum: Virtualisation
---

### Post by And6ate9 on 2008-05-22
Hello everyone I have setup a dual boot with XP and Hardy. I would like to be able to virtualize the hardy partition in windows and vice versa. How  do i go about doing this? I read some Vmware tutors but it seem liek they are having you do a whole new install into each os. I jsut want the virtualize the partition i have already.

---

### Post by bmwman on 2008-05-22
You cant do vice versa. You have to pick which OS do you prefer for Host and which one for guest. If you're mainly XP user, make that your main system, install VMware Workstation 6.03 in XP(non free) and import the Ubuntu partition as a new virtual machine. I have done the other way around- imported XP as a virtual inside Ubuntu and it's pretty straight forward.

Good luck.

---

### Post by And6ate9 on 2008-05-22
ok thanks, but the vmware is not free? that sucks. I cant do the same thing with vmplayer or vmserver? or maybe the ms virtual box?

---

### Post by dccrens on 2008-05-22
VirtualBox is free and works well. I am using 1.5.6. Version 1.6 seems to have some issues with Hardy though.

---

### Post by barnex on 2008-05-22
I very nice alternative, in my opinion, is using VirtualBox under ubuntu to virtualize windows. It's free and in the universe repository so it's trivial to install: ```
sudo aptitude virtualbox-ose
``` On my machine it seems a lot faster than vmware, and the 'seamless' mode, which integrates the 'windows' windows along you linux windows, is also very nice.

---

### Post by bmwman on 2008-05-22
Didn't know there is Virtual box for Windows. VMware server is free but I haven't really used it before and I'm not sure if it has all the features as VM Workstation. You can download it from here and try it [http://register.vmware.com/content/download-a.html](http://register.vmware.com/content/download-a.html) . As far as Virtual box, I have used it for a while and I do like too but i find it a lot harder to work with using bridged network, USB  drives, etc.

---

### Post by And6ate9 on 2008-05-22
well i having trouble setting up my wireless usb in linux so i cant veritualize xp in linux so i have to go linux in windows till I fix that problem.

sorry i ment virutal pc from MS

---

### Post by Sand Lee on 2008-05-22
Check out the sticky thread at the top of the forum, "Virtualization: Tips and Tutorials." You'll find a tutorial on how to virtualize a partition with VirtualBox.

---

### Post by bradmkjr on 2008-05-22
The issue lies with how you choose to setup grub. This may not be related, but I think it is the biggest issues in your situation.

If grub or lilo is installed on the XP partition, then you will need to mount the XP partition inside of the virtual machine, wait for grub to load and choose Ubuntu (inside of the virtual machine). If you happen to have a seperate boot partition then you might not have any issues. The ideal setup would be as follows:
1st part: boot
2nd part: ubuntu
3rd part: swap
4th part: windows
5th part: shared data

The virtual machine inside of windows could mount the 1st, 2nd, 3rd, and 5th partition.

The virtual machine inside of ubuntu could load the 1st, 4th and 5th partition.

Anyone else understand this? I'm I right or wrong?

Also as a side note, there is reported issue with Virtual PC 2007 working with the current 8.04 Ubuntu Kernel. The installer crashes, so just a heads up.

Thanks,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by And6ate9 on 2008-05-22
ok after doing some more reading in the tip section and online I have found 3 truths:

No tutorials about virtualizing a existing linux partition in windows. 

brad just blew my mind with his grub reasoning.


I need to go back to nintendo. One button handled it all. Power

---

### Post by bmwman on 2008-05-22
You can always reinstall Ubuntu inside of a VMware or Virtual box. It would be the easiest thing to do. Just a thought ;)

---

