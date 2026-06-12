---
title: "Upgrading PHP on Dapper via SSH"
date: 2009-02-08
forum: Server Platforms
---

### Post by jim0203 on 2009-02-08
I'm administering a "Virtual Private Server" which is hosted by [www.webfusion.co.uk](www.webfusion.co.uk) (who I would never send my business at, but I'm stuck with for my current project).

The server is running Dapper, which means it is limited to PHP 5.1 through the standard channels. I need to upgrade to PHP 5.2 to run a particular app.

I have root SSH access to the server. How should I go about upgrading PHP? Should I upgrade Ubuntu to a later release, or should I just upgrade PHP? In both cases, how do I do this over the command line/SSH?

---

### Post by punx45 on 2009-02-08
so php is limited to 5.1 in the Dapper repositories?   you should probably be able to find a .deb of 5.2 and install it with dpkg.  or you could always compile from source.   but if it is held back in the repos, it is probably for a reason, so you may break something installing 5.2

---

### Post by jim0203 on 2009-02-08
> **punx45 said:**
> but if it is held back in the repos, it is probably for a reason, so you may break something installing 5.2

So should I upgrade to a distribution that ships with PHP 5.2, rather than just upgrading PHP? And how do I perform this upgrade via SSH?

---

### Post by punx45 on 2009-02-08
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
see here for info on upgrades.

   everything should be doable through commandline.   keep in mind doing this remotely with no physical access to the machine may cause headaches.

i recommend doing all important tasks through screen. its in the repos.
[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

---

### Post by jim0203 on 2009-02-15
Thanks, those instructions worked great! It did end up borking my server, but that was the host's fault: Webfusion.co.uk. I'm going to transfer to nethosted.co.uk; their customer service seems much better and they're running PHP 5.2, which is what I wanted in teh first place.

---

