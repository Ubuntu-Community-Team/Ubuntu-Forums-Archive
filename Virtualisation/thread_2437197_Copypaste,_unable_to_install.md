---
title: "Copy/paste, unable to install"
date: 2020-02-19
forum: Virtualisation
---

### Post by ubantunovice2 on 2020-02-19
I dabbled with Ubuntu awhile back and have now returned to try again, but I find I've forgotten a lot and I'm now very frustrated. I just need a little help to get me going.

I'm on a fast W10 laptop and installed Ubuntu budgie in a virtualbox VM. Ubuntu is up and running but I have 2 frustrating things I need help with.

1. I can copy/paste within Ubuntu, but I cannot copy/paste from W10 to Ubuntu or reverse. How do I enable that? I need to do that to access some files on the Windows side.

2. I tried to install the kodi app within Ubuntu and failed.
If I used the graphic software interface it just would not install. Just stayed there no matter how long I waited after clicking on install.

If, in a terminal, I used 
     sudo apt install kodi
It also failed with:

      E: could not get lock /var/lib/dkpg/lock-frontend - open (11: Resource temporarily unavailable)
      E: Unable to acquire the dpkg frontend lock (/var/lib/dkpg/lock-frontend), is an other process using it?

As far as I know nothing else is running and I don't know what /var/lib/dkpg/lock-frontend is or how to unlock it.

It's very frustrating for a beginner. Can someone please help?

Thanks.

---

### Post by wildmanne39 on 2020-02-19
> E: could not get lock /var/lib/dkpg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dkpg/lock-frontend), is an other process using it?

That means exactly what is says there is almost always another process running, most likely if it is shortly after you boot automatic updates are running in the background you will need to wait for that to finish, if after quite some time it does not allow you to install the app you wish rebooting should remove that lock but if the updates have not installed it may start the update process again.

> I can copy/paste within Ubuntu, but I cannot copy/paste from W10 to Ubuntu or reverse. How do I enable that? I need to do that to access some files on the Windows side.

You have to have guest additions installed to be able to do that, take a look here:

[https://www.virtualbox.org/](https://www.virtualbox.org/)

It has a wealth of information.

Thread moved to virtualisation.

---

### Post by ubantunovice2 on 2020-02-20
Thank you very much for helping. 

About the problem with another process running, I would think that linux could multitask several processes, or at least reprioritize processes so as not to cause this error. Maybe it's hampered because it is running in a VM.

Thank you for replying. I truly appreciate it.

---

### Post by ajgreeny on 2020-02-20
> **ubantunovice2 said:**
> Thank you very much for helping. 

About the problem with another process running, I would think that linux could multitask several processes, or at least reprioritize processes so as not to cause this error. [COLOR="#FF0000"]**Maybe it's hampered because it is running in a VM.**[/COLOR]

Thank you for replying. I truly appreciate it.

No, nothing to do with a VM.
Even running a bare metal install you can not use more than one instance of anything using **apt** or **dpkg** in the background.  For example you can not run **sudo apt update** in terminal if you have the **Software GUI** open as well

---

### Post by ubantunovice2 on 2020-02-20
> **ajgreeny said:**
> No, nothing to do with a VM.
Even running a bare metal install you can not use more than one instance of anything using **apt** or **dpkg** in the background.  For example you can not run **sudo apt update** in terminal if you have the **Software GUI** open as well
Thanks. That's good to know.
Seems like a limitation bound to confuse and frustrate newbies like me. I'm sure there's a good reason for it being that way. I will explore it more after I've gotten going with Ubuntu. 
Thanks for the explanation. I appreciate your taking the time to explain.

---

### Post by CelticWarrior on 2020-02-21
Regarding #2 - Kodi - it doesn't work in VMs. In a VM you're using virtualized hardware, not the real one, and Kodi doesmn't support the virtual graphics card.

---

### Post by TheFu on 2020-02-22
> **CelticWarrior said:**
> Regarding #2 - Kodi - it doesn't work in VMs. In a VM you're using virtualized hardware, not the real one, and Kodi doesmn't support the virtual graphics card.

Yep, KODI demands direct access to the GPU and needs a specific openGL level to work. Had an old Via C6 CPU that didn't have support for a high enough opengl version. Wanted to use it as a media player.

---

