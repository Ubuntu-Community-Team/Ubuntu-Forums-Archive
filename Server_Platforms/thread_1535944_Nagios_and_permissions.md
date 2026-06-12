---
title: "Nagios and permissions"
date: 2010-07-21
forum: Server Platforms
---

### Post by MacGoose on 2010-07-21
I need help with Nagios and permissions.  I get one critical error in Nagios regarding disk.  It says: DISK CRITICAL - /home/administrator/.gvfs is not accessible: Permission denied

I guess Nagios need a permission to access the administrator folder.  How can I set up a permission to fix this error?

TIA!

, MacGoose

---

### Post by pytheas22 on 2010-07-21
Not even root can read the .gvfs directory.  I suspect this is a Nagios configuration problem, not an issue with configurations.  What exactly do you have Nagios trying to do?

---

### Post by MacGoose on 2010-07-21
> **pytheas22 said:**
> Not even root can read the .gvfs directory.  I suspect this is a Nagios configuration problem, not an issue with configurations.  What exactly do you have Nagios trying to do?
Nothing but the default.  This is releated to the Disk Space service, and it doesn't seem to work as it tries to access something it gets a permission denied on...

---

### Post by pytheas22 on 2010-07-21
It probably is getting permission denied when it tries to look in the .gvfs directory, but no one--not even root--is allowed to look there, so you will have to change the Nagios command so that it avoids trying to read that directory.

I haven't used Nagios on Ubuntu 10.04 so I'm not familiar with the default configuration, but do you know which command it's using to run the disk check?  Or could you post the host file that you're using?  I think this should be in /etc/nagios3/conf.d.

---

### Post by pytheas22 on 2010-07-21
Take a look at the bottom of [this page]("https://help.ubuntu.com/community/Nagios3").  I think this is the solution.

---

### Post by MacGoose on 2010-07-21
> **pytheas22 said:**
> Take a look at the bottom of [this page]("https://help.ubuntu.com/community/Nagios3").  I think this is the solution.
Thanx!  That did it at least for me.  Must be some sort of miss that Nagios is checking for a file even the root doesn't have access to.  And this with the default setup installed from the repository.

---

### Post by pytheas22 on 2010-07-21
.gfvs isn't just a file; it's actually a mountpoint on which Gnome mounts its virtual file system.  So it makes sense that Nagios thinks it should check it, because from Nagios's perspective it looks like a disk.  But you're certainly right that someone should make sure Nagios is smart enough to know that .gfvs is not a real file system, because I'm pretty sure all Gnome-based Linux distributions have had .gfvs for a couple years now.  I've always dealt with Nagios on servers where this wouldn't be an issue because Gnome isn't installed, but I'm sure you're not the first person to run into this.

In any case, glad you got it sorted it out.

---

