---
title: "Starting X as root, is this a security related issue?"
date: 2011-09-11
forum: Security
---

### Post by towheedm on 2011-09-11
This happened to me by accident.  I booted into recovery mode, selected the last item (drop to root shell) from the recovery menu.

Did what I had to do and forgot I was in recovery mode (totally ignored the console prompt).  I issued the 'startx' command to start X.  When the desktop appeared, I realized I was logged in a s root.  Walla, I now had access to everything and if I was not the only user on my system, I could have just as easily deleted anything from the filesystem or even introduce a virus, trojan etc, or simply have added myself to the sudoers list for later use.  Of course, I could have also done it before starting X.

I tried this with Fedora 15 but when I attempted to start X, it gave a permission denied error and exited.  I could not start X from the recovery console.

Is this a security bug in Ubuntu or is this normal?

Anyone can drop to the recovery console as root without being asked for root's password and do as they please, or am I missing something here?

---

### Post by haqking on 2011-09-11
> **towheedm said:**
> This happened to me by accident.  I booted into recovery mode, selected the last item (drop to root shell) from the recovery menu.

Did what I had to do and forgot I was in recovery mode (totally ignored the console prompt).  I issued the 'startx' command to start X.  When the desktop appeared, I realized I was logged in a s root.  Walla, I now had access to everything and if I was not the only user on my system, I could have just as easily deleted anything from the filesystem or even introduce a virus, trojan etc, or simply have added myself to the sudoers list for later use.  Of course, I could have also done it before starting X.

I tried this with Fedora 15 but when I attempted to start X, it gave a permission denied error and exited.  I could not start X from the recovery console.

Is this a security bug in Ubuntu or is this normal?

Anyone can drop to the recovery console as root without being asked for root's password and do as they please, or am I missing something here?


Physical access is root access.

Yes it is normal, you didnt need to startX to carry out those actions, you could of done them from the CLI

Root is disabled by default , the recovery console exists for physical access to help recover your system.

If others use your machine or have access to it then you need to secure your machine in other ways.

---

### Post by towheedm on 2011-09-11
> Root is disabled by default , the recovery console exists for physical access to help recover your system.

Ok so while in the recovery console I do 'whoami' and it returns 'root'.

Could you explain the difference between 'physical access' and 'root access'?

Thanks.

---

### Post by haqking on 2011-09-11
> **towheedm said:**
> Ok so while in the recovery console I do 'whoami' and it returns 'root'.

Could you explain the difference between 'physical access' and 'root access'?

Thanks.


It means if you physically have access to a machine then it is deemed root (superuser) access due ot the ability to boot to LiveCD and access data and various other methods of compromising the machine.

That is why servers are kept in secure server rooms.

recovery console allows you to do what you can so you recover things in the event you mess things up.

It can be changed by giving the root user a password which in turn enables the account globally on the system.

---

### Post by towheedm on 2011-09-11
> It can be changed by giving the root user a password which in turn enables the account globally on the system.

Excuse my ignorance, but I'm always willing to learn something new.
Fedora allows you to specify a password for root, but it still does not ask for it when dropping to the recovery console.

---

### Post by haqking on 2011-09-11
> **towheedm said:**
> Excuse my ignorance, but I'm always willing to learn something new.
Fedora allows you to specify a password for root, but it still does not ask for it when dropping to the recovery console.


if you drop to a recovery console in fedora you can still have do the same, thats what recovery console exists.

[http://www.go2linux.org/fedora-centos-root-password-recovery](http://www.go2linux.org/fedora-centos-root-password-recovery)

see here for [Rootsudo]("https://help.ubuntu.com/community/RootSudo") explanation of how things are in Ubuntu.


and here for [fedora]("http://www.fedorafaq.org/basics/") use of su or [here]("http://fedorasolved.org/post-install-solutions/sudo") for sudo use in fedora

---

### Post by towheedm on 2011-09-11
thanks for the links.

---

### Post by haqking on 2011-09-12
> **towheedm said:**
> thanks for the links.

no problem, i know it can be confusing.

You are welcome.

peace

---

### Post by towheedm on 2011-09-12
It's not really confusing, as I regularly use sudo and su (in Fedora).  I try to do everything from the CLI, except for the times that I'm feeling to lazy to type.

Now that I think of it, as insecure as it may be, Windows always ask for the Administrator's password before dropping to it's recovery console.  Why not Linux then?  It could be considered another level of security, IMHO.

---

### Post by haqking on 2011-09-12
> **towheedm said:**
> It's not really confusing, as I regularly use sudo and su (in Fedora).  I try to do everything from the CLI, except for the times that I'm feeling to lazy to type.

Now that I think of it, as insecure as it may be, Windows always ask for the Administrator's password before dropping to it's recovery console.  Why not Linux then?  It could be considered another level of security, IMHO.

if dropping to recovery console to reset your root password becasue you forgot it required a root password how would you ?

;-)

recovery console is for recovery, physical access is root access, even more so in a windows machine.

You can boot a windows machine with many variants of a live CD and reset the admin or any other user password, access files etc etc

PHYSICAL = ROOT

---

