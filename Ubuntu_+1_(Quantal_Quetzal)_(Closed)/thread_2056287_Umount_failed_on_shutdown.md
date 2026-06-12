---
title: "Umount failed on shutdown"
date: 2012-09-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Richard on 2012-09-11
Hello,

I get some errors on Quantal shutdown, killing all process failed then /var is still busy and umount failed. So on startup /var isn't clean.
I couldn't find in logs more information, rsyslogd seems stopped before this error occured.

Thank you.

---

### Post by dino99 on 2012-09-11
maybe try to clean the system as much you can :

- clean/autoclean/autoremove/bleachbit(as root)
- look at orphans (sudo gtkorphans)

and run : sudo dpkg-reconfigure -phigh -a
( can take a while, be patient)

---

### Post by Richard on 2012-09-11
I clean old packages and reconfigure all, I don't find orphaned package.
Issue on umount /var persist.

---

### Post by dino99 on 2012-09-11
so what looking next : upstart & initscripts

[http://doc.ubuntu-fr.org/upstart](http://doc.ubuntu-fr.org/upstart)
[http://manpages.ubuntu.com/manpages/precise/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/precise/man8/update-rc.d.8.html)

---

### Post by Richard on 2012-09-13
Hello,


I just tried on a new installation from a daily iso, I get the same issue. It seems there is something wrong with /var on a dedicated volume.
I find some similar closed bugs on launchpad with older releases.

---

### Post by dino99 on 2012-09-13
> **Richard said:**
> Hello,


I just tried on a new installation from a daily iso, I get the same issue. It seems there is something wrong with /var on a dedicated volume.
I find some similar closed bugs on launchpad with older releases.

Do you mean that this system is a server or the installation made with unusual ubuntu(debian) rules ?

---

### Post by Richard on 2012-09-13
This is the default desktop installation from daily live with dedicated volumes for /, /home and /var.

---

### Post by dino99 on 2012-09-13
> **Richard said:**
> This is the default desktop installation from daily live with dedicated volumes for /, /home and /var.

I'm confused, there is no "dedicated" /var, only the one ubuntu always have set. So what is different now that could push that issue and was not existing before ? (usb plugged, new appp) Look at htop or system monitor to know (before shutting down) if something is hanging around)

---

