---
title: "Ubuntu Server 11.10 Default power saving features"
date: 2011-10-21
forum: Server Platforms
---

### Post by arkaxandai on 2011-10-21
Hey everybody,

I have a fresh install of Ubuntu 11.10 Server. After a period of time (maybe ten minutes or so) my monitor goes to sleep. I would like it to stop doing that. I don't have a single package installed though I have updated Aptitude and updated the packages that are installed by default. I selected nothing from the installer's list of packages either (like SSH or LAMP, etc).

I'm fairly certain the monitor itself doesn't have any power saving features. The hardware is a late 2006 Mac Mini. The monitor is a Dell E152FPb.

As may be apparent I'm new to Linux in general and really just don't know where to go and look for scripts or config files. If anyone can help me look in the right direction I would appreciate it. I'm not particularly interested in installing any particular packages for this. I'm hoping there is just a boolean flag somewhere I can just toggle and be done with this.

Any replies are much appreciated. I'm in learning mode here and the advice of the community is of great value to me.

---

### Post by duke.tim on 2011-10-26
If You have a desktop UI installed such as Unity.
On the left hand side of the screen there should be an icon for
system settings.

Click on it and you will get a variety of settings to choose from.
Choose Power. The options should be there :)

Also You can go into screen and find additional settings there.

---

### Post by oldos2er on 2011-10-26
Thread moved to Server Platforms.

---

### Post by duke.tim on 2011-10-26
o.0 I totally missed the Ubuntu Server part :oops:

The power setting config files should be in
/etc/default/acpi-support

---

