---
title: "Sun xVM VirtualBox bigger screen then 800 x 600?"
date: 2008-05-08
forum: Virtualisation
---

### Post by artrbinfo on 2008-05-08
Hi!
 I know this question if discussed often, but my case is different, because other solve this problem by installing Guest OS Additions, I installed it, but there is no bigger resolution then 800x600...
 How could I fix it and get for example 1024 X 768 or 1280 X 1024?

---

### Post by artrbinfo on 2008-05-08
Bump...

---

### Post by brendan.lefoll on 2008-05-08
considered waiting more than 2.30 hrs before bumping?

What's your host OS, what's the guest OS, and how much memory have you allocated to the graphics card?

Allocate somethign reasonable like 24MB and if guest additions is on there and the OS is supported it should work fine.

---

### Post by artrbinfo on 2008-05-08
Ok.
Currently host OS is Windows XP and guest is Ubuntu 8.04.
Video ram size is 64Mb

---

### Post by p_quarles on 2008-05-08
Moved to Virtualization. 

You may need to reconfigure the X server in the guest OS to get a higher resolution.

---

### Post by Doktor Jones on 2008-07-08
I found the trick is to install the Guest Additions.  Start up your Ubuntu VM and mount the VBoxGuestAdditions.iso as a CDROM (it should be in the VirtualBox program folder).  Open a terminal and change to the CDROM (on my system it was /media/cdrom0) and use sudo to execute VBoxLinuxAdditions.run.

For the technically uninclined, open the terminal (Applications > Accessories > Terminal) and type the following (case sensitive!):
```

cd /media/cdrom0/
sudo ./VBoxLinuxAdditions.run
```

After it finishes it will tell you to restart.  Restart Ubuntu and when it comes up again, you'll have full resolution control.  To change your VM resolution, just resize the VirtualBox window and Ubuntu will automatically adjust to it!  The screen resolution control panel will also have 1280x800, 1280x768, and 1024x768 available as standard resolutions (on top of 800x600 and 640x480 of course).

---

### Post by Masoris on 2008-07-10
That's a bug. Read this: [http://www.virtualbox.org/ticket/1689](http://www.virtualbox.org/ticket/1689)

---

### Post by Spandangle on 2008-10-29
Big thanks to Doktor Jones. worked a treat.

---

### Post by demiyanto on 2010-04-29
I've prepare my final assignment, which is making video tutorial on using Ubuntu for Begginer. Dude it's work to me too. Big thanks too...:)

---

