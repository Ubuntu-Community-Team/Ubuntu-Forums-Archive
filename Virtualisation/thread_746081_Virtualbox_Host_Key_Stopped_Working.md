---
title: "Virtualbox Host Key Stopped Working"
date: 2008-04-05
forum: Virtualisation
---

### Post by Kiri on 2008-04-05
I had XP running in vbox perfectly before. Seamless, everything.
Now after I have updated the linux kernel, I cannot use my keyboard in the XP VM. Actually I cannot use the host key to do anything!
At first I was stuck in seamless fullscreen mode and couldn't get out. Finally I managed to, but the host key and indeed ALL the keys do not work in the VM.

I have run :
/etc/init.d/vboxdrv setup after upgrading the kernel. 


Does anyone else have this problem or have an idea how to fix it ?
(besides deleting the VM and clean installing) ?

---

### Post by rdoolen on 2008-04-05
I think the virtualbox kernel modules haven't been updated yet.

I have the same issue with the latest Hardy kernel.

I am going to wait to see if they apear soon.

---

### Post by Kiri on 2008-04-06
OK, good to know its at least not just me. 
I guess we just have to wait then?
Thats frustrating, because I just bought new RAM yesterday so I could use VMs more -_-

---

### Post by rdoolen on 2008-04-06
This thread seems to be following the progess

[http://ubuntuforums.org/showthread.php?t=654808](http://ubuntuforums.org/showthread.php?t=654808)

---

### Post by rdoolen on 2008-04-07
I installed the kernel modules for the latest kernel and it still doesn't work.

The funny thing is, everything works fine if I am logged in from NX client. This makes me think there is an issue with my drivers; most likely NVIDIA, which doesn't run in NX.

What is your video driver/card? Have you got your virtualbox working?

---

### Post by nidal22 on 2008-04-07
I&#609;ot same problem, keyboard does not work at all in the VM after I updated to the new kernel

---

### Post by Kiri on 2008-04-08
I ended up just re-installing virtualbox from the deb package (Im using the non-ose version), and now it seems to work with the new kernels... 
It kept my VM in there with all the settings so it really wasnt a problem

---

### Post by a.janke on 2008-05-26
This reply might be late but I have found that this problem might have something to do with GNOME.  In my case if I change the host key to anything but Ctrl (say the windows 'menu') key things work fine.

What alerted me to this is that I have the "Show mouse on Ctrl" enabled and when I press the host key the little orange flashy target thing appears....

I would guess that GNOME is getting in the way.


a

---

### Post by pizpot on 2008-05-26
Reboot ubuntu and choose the old kernel, until virtualbox gets updated:

Ubuntu 8.04, kernel 2.6.24-16-generic

(Ubuntu 8.04, kernel 2.6.24-17-generic, and Ubuntu 8.04, kernel 2.6.24-16-386 both fail)

---

### Post by ktakasmanov on 2008-07-15
if you use SCIM, this might be a problem
I have installed the scim-bridge-client-qt package and it worked

Hope this will work for you

---

### Post by khughitt on 2008-08-20
> **ktakasmanov said:**
> if you use SCIM, this might be a problem
I have installed the scim-bridge-client-qt package and it worked

Hope this will work for you

I lost keyboard input functionality after installing SCIM as well. This did the trick for me.

Thanks!

---

### Post by rotts on 2008-11-14
> **a.janke said:**
> This reply might be late but I have found that this problem might have something to do with GNOME.  In my case if I change the host key to anything but Ctrl (say the windows 'menu') key things work fine.

What alerted me to this is that I have the "Show mouse on Ctrl" enabled and when I press the host key the little orange flashy target thing appears....

I would guess that GNOME is getting in the way.


a


I had the same issue, I just never realized I caused it with setting the "Show mouse on Ctrl"
because I upgraded VirtualBox the same day I enabled "Show mouse on Ctrl"

i disabled it and now the host key works as expected, about to change the host key to most likely
the "windows menu key"

thanks for bringing this to my attention!

---

