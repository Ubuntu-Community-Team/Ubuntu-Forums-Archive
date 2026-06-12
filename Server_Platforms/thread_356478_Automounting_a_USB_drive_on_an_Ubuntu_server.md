---
title: "Automounting a USB drive on an Ubuntu server?"
date: 2007-02-08
forum: Server Platforms
---

### Post by ZephyrXero on 2007-02-08
Is there a way I can set my Ubuntu server (aka...no desktop environment) so that it will automount a USB hard drive when it is connected?

This machine actually has a full Xubuntu install on it, but I have disabled GDM from loading at startup. When I'm in XFCE my drives will automount, but not when there is no desktop running, so I assume it happening at the DE level. This machine is acting as a simple file server, and I don't want to have to ssh in to it to manually mount my external drive everytime I connect it.

---

### Post by golfing22 on 2007-02-10
I beleive theres a way to do it in /etc/fstab but I'm not exatly sure what the right syntax is.
EDIT: Sorry, I read your question wrong, I thought you meant automount on startup.

---

### Post by jtc on 2007-02-11
Well, I can imagine one very ugly solution.

That is running a repeated crontab every minut, checking for the existens of device associated with the usb-drive. But, as I said, that is a very ugly solution and there should be some better way.

---

### Post by ZephyrXero on 2007-03-08
Well I think I'm just gonna have to have XFCE loaded so my boss can easily mount and eject the drive when I'm not there...he's not too friendly with command line :/

---

### Post by streeto on 2007-03-08
Install the package ivman, then find a way to start it at power-up (maybe /etc/rc.local). Note this does not require X to be running.

After running ivman, insert the usb drive, and it should be mounted at /media/usbdisk or something like that.

**Edit:** *That stuff about /etc/rc.local is wrong, corrected in my reply below.*

---

### Post by jtc on 2007-03-08
> **streeto said:**
> Install the package ivman...
Ahh, useful program to know about. Thank you for the tip!

---

### Post by rennen01 on 2007-03-08
I am going to try that as well.   Thanks for the info.

---

### Post by ashembers on 2007-03-12
Did ivman work for you?

---

### Post by streeto on 2007-03-12
Forget what I said about adding ivman to /etc/rc.local. It already has a init script, /etc/init.d/ivman. Just make sure it starts at boot time.

Then, a fast way to check if ivman is working is inserting a cdrom. If it does mount, but your usb drive doesn't, it is likely that you have a driver/module problem.

-st.

---

