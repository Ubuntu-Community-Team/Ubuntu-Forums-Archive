---
title: "Hardy Multiboot Realtime kernel question"
date: 2009-10-13
forum: Ubuntu Studio
---

### Post by pedrocortez on 2009-10-13
Hi 

I have a multiboot set up on my old P4 1.8Ghz system with 3 boot options.....

1) Hardy 8.04 LTS - for net, songbird, and trying out all things Linux , and mainly experimenting with audio apps and settings before commiting them to UbuntuStudio set up below ..
2) UbuntuStudio 8.04 rt - my stable recording DAW system which is currently very stable running Jack, Ardour, Rosegarden Linuxsampler and other bits and pieces. 
I use this for songwriting and recording my band demos. 
3) Windoze XP ( never use it now really ) 

Ive been trying to get the no.(1) Hardy LTS system to have an -rt kernel to try out audio apps and settings before committing them to boot option no (2) above. 

but even though i try to  install rt kernel and headers for the Hardy kernel via synaptic , the -rt option just doesn't show in my GRUB menu at boot time.  I've done all the usual things to install and set @audio prio , memlock in etc/security/limits.conf  but if I run uname -r , output is just the generic 2.6.24-24 generic kernel not the -rt kernel i'm hoping will show up. 

?  what should i check / do next ? 

cheers
Pete

---

### Post by c00kie55 on 2009-10-15
dont realy know if this applyes to you but i have to diffrent karmic setups 64 bit and a 32 bit  i installed 32 bit first then the 64 bit so i think the 64bit version is now controlling grub 
anyway after installing rt-kernel on the 32 bit i didnt show up in grub ??
i had to boot up my 64bit partition and do a sudo update-grub then reboot now the new realtime kernel was showing up in grub

---

