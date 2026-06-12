---
title: "How do I file a bug in this OS?"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ranch hand on 2012-02-14
Have a cups installation bug to report.  Will not install correctly in a chroot environment.

So;
```

tom@Pervert:~$ ubuntu-bug cups

```
gets me a popup;
> 
The problem cannot be reported:

This is not an official Ubuntu package. Please remove any third party package and try again.

Don't have any non Ubuntu packages.

So
```

tom@Pervert:~$ ubuntu-bug apport

```
Gets the same result.

So now what does a feller do?

I had not fixed the install yet which I am going to do now.  The next cups package will do the same and dpkg --configure -a straightens it right out when I come over here to the install.

But the devs may want to know that the install script seems to be faulty.  Might be nice to know.  Kind of hard for someone to use, say a headless printer server, with out doing upgrades with chroot.

---

### Post by mc4man on 2012-02-14
Does the ubuntu-bug cups not  work after you've 'fixed' the package install?

---

### Post by ranch hand on 2012-02-14
No.  It is still not an Ubuntu package.

I can see that it possibly could have come from someplace else, mine didn't, but it could be done.

Apport is also, it seems not an Ubuntu package.  That one is a little tough to write off as a reasonable mistake.  I am pretty sure that Ubuntu is the only one using that.

---

### Post by dino99 on 2012-02-14
Reporting against dev package:

go to the source package url:  [https://launchpad.net/ubuntu/+source/mypackage](https://launchpad.net/ubuntu/+source/mypackage)
you'll find on the right top side : report a bug

about the report title: begin it with the version number (like:  2.3.0 : my title). That way the bug directly goes into the good queue to be reviewed.
its a good idea to add that version number into Tags (latest line of description report)

---

### Post by ranch hand on 2012-02-14
> **dino99 said:**
> Reporting against dev package:

go to the source package url:  [https://launchpad.net/ubuntu/+source/mypackage](https://launchpad.net/ubuntu/+source/mypackage)
you'll find on the right top side : report a bug

about the report title: begin it with the version number (like:  2.3.0 : my title). That way the bug directly goes into the good queue to be reviewed.
its a good idea to add that version number into Tags (latest line of description report)
Yes I suppose I am going to have to do that.  Was hoping this was a problem that someone had had and there was a simple fix.

Apport needs to be working.

I think I will wait for tomorrow and go back over there and see if I can goose apport up a bit with dpkg.  Might work if no one else is having this problem.

If not I will file on it, cups and thunar custom actions.

---

### Post by dino99 on 2012-02-14
> **ranch hand said:**
>  see if I can goose apport up a bit with dpkg.  

i've not read the manpage about possible workaround, guess im too lazy :)

---

### Post by ranch hand on 2012-02-14
> **dino99 said:**
> i've not read the manpage about possible workaround, guess im too lazy :)
Me too.  Guess I will though.

---

### Post by juancarlospaco on 2012-02-14
ubuntu-bug -w


Click the window (widget, panel, or whatever) with the bug

---

### Post by Ibidem on 2012-02-14
> **ranch hand said:**
> Have a cups installation bug to report.  Will not install correctly in a chroot environment. .... But the devs may want to know that the install script seems to be faulty.  Might be nice to know.  Kind of hard for someone to use, say a headless printer server, with out doing upgrades with chroot. I blame upstart. Maybe it should be service in sysv-?-utils, or the upstart tools.  They have some hook for EVERY SINGLE DAEMON that insists on restarting on install. Naturally this kills chroot upgrades. In my case, it was udev.  The obvious way would be  -check for chroot -if not detected, adjust services  Or it could be: check if service is running in current env. (/run/*?) If so, restart.  This also fixes issues where one service is disabled, but gets started on package upgrade. It does cause issues with daemons that watch config files (picture samba3 loading an empty config file on delete, then loading a configfile for samba4), so you'd need to set up something along these lines: ```
 service cups status >>/var/log/dpkg/daemons service cups stop #Uninstall #Install next version was_running cups && service cups start
```

---

### Post by ranch hand on 2012-02-16
Reinstalled but did not fool with apport.

Installed the current daily.  Probably get an update for something cups related pretty quick and will check it then.

Could be that the stuff will install now.  Had a problem with Thunar not taking custom actions.  Does now.

Even if the cups stuff installs I will go over and try apport and see if it recognizes itself as an Official Ubuntu package.

---

### Post by ranch hand on 2012-02-17
Apport is working fine on the fresh install.

---

