---
title: "Ubuntu 11.04 Server Login Problems"
date: 2012-01-18
forum: Server Platforms
---

### Post by natski on 2012-01-18
Hi all,

I bought my first server recently preinstalled with Ubuntu 11.04 Server. To my surprise, there was no GUI so I installed a GUI using sudo apt-get install ubuntu-desktop

After startup, I get a login screen with options 'default user', 'other user' and 'guest'. When I click default user and type in a random (i.e. wrong) password a message flashes up that the password is invalid as expected. When I type in the correct password for the only user registered on the system the monitor turns off for a second then turns back on with the same screen as before on. i.e. there is no 'invalid password' message or anything. The same thing happens when I click 'other user' and type in my username and password.

As a result, I can't login! The only way I can get in is a guest but then I can't sudo anything or really do anything on the system, so it's useless.

What's going on here?

natski

---

### Post by HazKO on 2012-01-18
error: unknown filesystem.
grub rescue>
 
plz help i cant use my laptop, i need 2 hand in work for my university

---

### Post by arrrghhh on 2012-01-18
> **natski said:**
> Hi all,

I bought my first server recently preinstalled with Ubuntu 11.04 Server. To my surprise, there was no GUI so I installed a GUI using sudo apt-get install ubuntu-desktop

After startup, I get a login screen with options 'default user', 'other user' and 'guest'. When I click default user and type in a random (i.e. wrong) password a message flashes up that the password is invalid as expected. When I type in the correct password for the only user registered on the system the monitor turns off for a second then turns back on with the same screen as before on. i.e. there is no 'invalid password' message or anything. The same thing happens when I click 'other user' and type in my username and password.

As a result, I can't login! The only way I can get in is a guest but then I can't sudo anything or really do anything on the system, so it's useless.

What's going on here?

natski

a) I would do a complete reinstall.

b) Choose wisely this time - if you want a server, install 10.04LTS and keep your server on LTS releases.  If you want a desktop, install Ubuntu Desktop.  There's no point, whatsoever, in installing Ubuntu Server, then doing an apt-get install ubuntu-desktop.  Waste of time, resources, and probably a lot of other things :p.

> **HazKO said:**
> error: unknown filesystem.
grub rescue>
 
plz help i cant use my laptop, i need 2 hand in work for my university

Don't threadjack, make your own thread.  This couldn't be more off-topic.

---

### Post by natski on 2012-01-18
Thanks, I kinda suspected you say exactly that! I will indeed download the ubuntu 10.04 desktop disk image now, burn it to a disc, and then reboot with the disk in to install the new version.

---

### Post by arrrghhh on 2012-01-18
> **natski said:**
> Thanks, I kinda suspected you say exactly that! I will indeed download the ubuntu 10.04 desktop disk image now, burn it to a disc, and then reboot with the disk in to install the new version.

You got it.

You can install 10.04 on server or desktop, then you only **have** to upgrade every 2 years.  Although, be warned... Upgrades can be difficult even if you stay on the 6 month release schedule, so quite often a full rebuild is in order.

Just food for thought.  A fresh rebuild will always be easier to setup than an upgrade.  Enjoy!

---

### Post by mlinux on 2012-01-18
You bought a server version and try to run as desktop?

If you are going to use it as server, best not to install GUI. Install webmin through putty and continue setup from your desktop pc.

---

