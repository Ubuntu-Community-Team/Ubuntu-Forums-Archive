---
title: "Virtualbox disable auto-pause"
date: 2017-03-06
forum: Virtualisation
---

### Post by kianwilliam on 2017-03-06
Greetings:
My guest is a vm ubuntu 16.04 on Virtualbox with host windows.
Once I start vm, it goes to pause automatically several times.
Without changing the amount of memory for guest, is there a way to disable auto-pause ? (This state is a warning from VB to let me know windows might experience lack of memory)
Kian William

---

### Post by howefield on 2017-03-06
How much memory have you given to host and guest ?

Try turning off the power options in the guest.

---

### Post by kianwilliam on 2017-03-07
The syntax to turn off power options in virtualbox 5.1.0 starts with: VboxManage controlvm "nameofvm" ... and I do not know the rest.
Could you tell me the exact syntax?
Regarding ram, 1024MB for guest, my laptop has 2GB ram totally, to make it up I am using readyboost 4096MB.
Thanks ahead
Kian William

---

### Post by deadflowr on 2017-03-07
> The syntax to turn off power options in virtualbox 5.1.0 starts with: VboxManage controlvm "nameofvm" ... and I do not know the rest.
No need to run that as that power settings is not the problem, you need to check your power settings in the guest.
Look in System Settings >> Power.
Also look at Brightness and Lock and turn off the screensaver feature.

---

### Post by howefield on 2017-03-07
For extra context for anyone else contributing to the thread : [https://www.cnet.com/forums/discussions/virtual-box-ram/](https://www.cnet.com/forums/discussions/virtual-box-ram/)

---

### Post by kianwilliam on 2017-03-07
Yes, but the problem is that I run into black screen when I turn it on. Once I get rid of this auto-pause , chances of running the guest which is ubuntu 16.04 will be more
Then I have access to power management and screen saver. But now, I can not run it, most of the times I get black screen. In between few times that I could run the guest, I downloaded and  installed guest additions, but next time when I wanted to run VBoxadditions to finish the process to install guest additions, I got black screen again and installation of guest additions is still not complete. So the first step is to get rid of auto-pause from VBoxManage command prompt. Guest used to work perfect, these things happened recently. All I did was to download ZendServer and ZendStudio.

---

