---
title: "[SOLVED] VirtualBox"
date: 2008-06-05
forum: Virtualisation
---

### Post by RMD94 on 2008-06-05
Hello,

Can someone tell me how can i install XP Professional on VirtualBox through a CD.

---

### Post by deltaprime on 2008-06-05
yes you can . i did the same, there are limitations like it wont read your usb ports from linux but you can transfer files through a mapped network drive in vista which is a folder in ubuntu. It absolutely works. I  use it for mic soft one note and generaly office 07 and just save my files to the mapped network drive to print them in ubuntu. it is fast safe and neat to have, you can surf the internet, download...... even install vista =)

good luck 

delta

---

### Post by RMD94 on 2008-06-05
Thank You but that doesn't quite answer my question..
I didn't ask if i can or if i can't, i asked how can i????

-Rajas

---

### Post by swoll1980 on 2008-06-05
> **deltaprime said:**
> yes you can . i did the same, there are limitations like it wont read your usb ports from linux but you can transfer files through a mapped network drive in vista which is a folder in ubuntu. It absolutely works. I  use it for mic soft one note and generaly office 07 and just save my files to the mapped network drive to print them in ubuntu. it is fast safe and neat to have, you can surf the internet, download...... even install vista =)

good luck 

delta

If yo u get it from Sun it has usb support

---

### Post by swoll1980 on 2008-06-05
> **RMD94 said:**
> Thank You but that doesn't quite answer my question..
I didn't ask if i can or if i can't, i asked how can i????

-Rajas

[here's]("www.flickr.com/photos/createavirtualmachine/") a how to you can find more on google

---

### Post by RMD94 on 2008-06-05
thanks but i can't figure out how to boot the virtual drive from the CD

---

### Post by swoll1980 on 2008-06-05
> **RMD94 said:**
> thanks but i can't figure out how to boot the virtual drive from the CD

you mean boot the cd from the virtual drive? in settings you will see a setting for cd drive you have to enable it while your there enable sound too

---

### Post by RMD94 on 2008-06-05
i am so confused, all i want to do is install xp pro in my virtual box. I have a cd of xp pro and i want to install it on the virtualbox...........  i wish u understand what i am tring to say.............

---

### Post by Xavier_To on 2008-06-05
It's relatively easy. In the configuration of the virtual machine you created for XP, just add CD-Rom support to your physical drive and when the VM boots, just press F12 and select the CD-Rom Drive so the VM will boot from the CD.

If that doesn't work, you can always make an iso image of your XP CD, specify to the VM to use the iso file as the CD drive. Boot from the CD inside your VM and you should be able to install Windows XP on the VM

---

### Post by K.Mandla on 2008-06-05
Moved to Virtualization.

---

### Post by RMD94 on 2008-06-05
i did my best ...................................................    but i am still getting errors:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Help!!

-Rajas

---

### Post by RMD94 on 2008-06-05
I am really sorry but i don't understand what is virtulization......

---

### Post by Xavier_To on 2008-06-09
Well from what I've understood from other posts, the new kernel update broke the vboxdrv... It stopped working for me after the new update. Apparently we have to wait for the Virtual Box Devs to release their update.

Can someone confirm this ?

---

