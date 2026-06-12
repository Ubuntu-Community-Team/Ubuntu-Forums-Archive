---
title: "Why are some saucy packages newer than trusty packages?"
date: 2013-12-27
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2013-12-27
Currently Firefox for saucy: [http://packages.ubuntu.com/de/saucy/firefox](http://packages.ubuntu.com/de/saucy/firefox) (26.0+build2-0ubuntu0.13.10.2)
And for trusty: [http://packages.ubuntu.com/de/trusty/firefox](http://packages.ubuntu.com/de/trusty/firefox) (25.0+build3-0ubuntu0.13.10.1)

Interestingly this is also not the first time and seems not to be very rare. I have here just the same opinion as in the extras-repository thread: Maybe it would be the best if a package of a development release points to the previous release if it has a newer package. But such a behavior must be implemented first (if this feature doesn't already exist).

---

### Post by mc4man on 2013-12-27
re: firefox
> $ apt-cache policy firefox
firefox:
  Installed: 26.0~b6+build1-0ubuntu1
  Candidate: 26.0+build2-0ubuntu2
  Version table:
     26.0+build2-0ubuntu2 0
        500 [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) trusty-proposed/main amd64 Packages
 *** 26.0~b6+build1-0ubuntu1 0
        100 /var/lib/dpkg/status
     25.0+build3-0ubuntu0.13.10.1 0
        500 [http://mirror.cs.umn.edu/ubuntu/](http://mirror.cs.umn.edu/ubuntu/) trusty/main amd64 Packages


---

### Post by Sworddragon on 2013-12-27
```
sworddragon@ubuntu:~$ apt-cache policy firefox
firefox:
  Installed: 26.0+build2-0ubuntu0.13.10.2
  Candidate: 26.0+build2-0ubuntu0.13.10.2
  Version table:
 *** 26.0+build2-0ubuntu0.13.10.2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ saucy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     25.0+build3-0ubuntu0.13.10.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
     24.0+build1-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
```


Firefox 26 is only available in saucy-security, saucy-updates and trusty-proposed. Now the question is why is it only in -proposed on trusty if it is declared as stable on saucy?

---

### Post by cariboo on 2013-12-27
Packages in proposed have nothing to do with stability problems, they are there while waiting for dependencies to catch up. If you are aware of the problems you might run into, you can still enable the proposed repositories, although it is advised not to, as it may break you system.

---

### Post by Sworddragon on 2013-12-28
I know about the dependency policy which I was refering with "stable" to. But I'm still wondering why Firefox 26 on trusty has to wait for the dependencies as Firefox 26 on saucy does already fit with these (Firefox 26 on saucy can also be installed on trusty without dependency issues).

---

### Post by deadflowr on 2013-12-28
Do you expect trusty to have to the same package versions as saucy?
Probably not.
So most likely, they're awaiting newer versions of the needed dependencies to come down the pipe.

---

### Post by Elfy on 2013-12-28
ff26 installs fine from proposed - just enable and select the 2 firefox packages

---

### Post by ekerazha on 2013-12-28
_I don't know if this still apply_, but I remember that Ubuntu LTS versions (i.e. 10.04) were based on Debian testing while non-LTS versions were based on Debian sid. Maybe some packages in Debian testing are still older than the Debian sid packages which Saucy used.

---

### Post by Sworddragon on 2013-12-28
> **deadflowr said:**
> Do you expect trusty to have to the same package versions as saucy?
Probably not.
So most likely, they're awaiting newer versions of the needed dependencies to come down the pipe.

Often the packages are identical and even if not they could use the saucy one first and replace it with the trusty one as ubuntun+1 if it is ready.


> **ekerazha said:**
> _I don't know if this still apply_, but I remember that Ubuntu LTS versions (i.e. 10.04) were based on Debian testing while non-LTS versions were based on Debian sid. Maybe some packages in Debian testing are still older than the Debian sid packages which Saucy used.

If this is true it would maybe explain this behavior.

---

### Post by grahammechanical on 2013-12-28
I think that it is one thing to package an upstream application for a Ubuntu code base that was set, more or less, on release day and another thing to package that same upgrade to an application on a code base that is being changed on a daily basis. It might be possible for Firefox 26 to be packaged for Trusty as the code base now stands but what if the dependencies are broken by some package upgrade that comes in the next day or a week later? It would be like repainting the Forth bridge. A job that once finished has to be started again.

There has been this intention for more than a year that the development branch be stable so developers could work on bringing their applications to Ubuntu on the latest code instead of waiting until release day or after. Bringing in applications like Firefox 26 too early in the development cycle could lead to perceptions that Trusty Tahr is buggy.

Regards.

---

### Post by kansasnoob on 2013-12-28
This is exactly why I've repeatedly said that dev releases should NOT be used for security critical operations like on-line banking :)

I was recently contradicted here:

[https://lists.launchpad.net/ubuntugnome-qa/msg00113.html](https://lists.launchpad.net/ubuntugnome-qa/msg00113.html)

At the end of the day it all comes down to personal choice :)

---

### Post by d-cosner on 2013-12-31
I upgraded Saucy to Trusty last night, the newer Firefox packages do work fine in Trusty. I noticed a few other packages were newer too and switched them to the Trusty packages. I have had Firefox crash unexpectedly while running Saucy on my main computer a couple of times and wondered if maybe the developers were waiting for a point release or a new version of Firefox before including it by default in the Trusty repos.

If someone really has to have the newer version of Firefox on their development install you can have it but it is probably better to wait for it to make it into the main repo. It kind of defeats the purpose of testing by using packages that are not in the main repos. Just my two cents.

---

### Post by QDR06VV9 on 2014-01-01
Firefox PPA works for Trusty.
[https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next)
Been using for awhile now.

---

