---
title: "before installing OS questions"
date: 2007-11-30
forum: Server Platforms
---

### Post by vsiege on 2007-11-30
If Im planning on booting from an RAID 1 array - do I need to have a RAID driver disk ready when installing the OS? ever? I am using the RAID controller off of the MOBO (yes I know)

Should I have the computer's network cable in while installing? does it need to DL anything for the install?

Im hoping to have LAMP, remote mangement and file server services up and running when the OS is installed.

---

### Post by prodezigner on 2007-11-30
Just make sure you have RAID turned on in your BIOS settings and you can try the install without the driver disk. Often times you won't need it.

As for the ethernet being plugged in, it's always a nice idea, because it will setup the DHCP for you, and then you'll know what to change in the conf file.

---

### Post by vsiege on 2007-11-30
thanks again! I'm going to burn the ISO right now and begin the process - wish me luck

---

