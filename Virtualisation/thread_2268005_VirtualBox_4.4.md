---
title: "VirtualBox 4.4"
date: 2015-03-05
forum: Virtualisation
---

### Post by v3.xx on 2015-03-05
I normally do not ask, but I got bit by an upgrade a few weeks ago and a little reluctant to mess with my 4.3 install.

So the question is 'any glitching'?

---

### Post by slickymaster on 2015-03-05
> **v3.xx said:**
> I normally do not ask, but I got bit by an upgrade a few weeks ago and a little reluctant to mess with my 4.3 install.

So the question is 'any glitching'?

VirtualBox 4.4?!

I updated mine last Tuesday to VirtualBox 4.3.24, and I'm almost sure that's the last available version.

---

### Post by v3.xx on 2015-03-05
I update from the vBox site and 4.4 came out today I think.

---

### Post by slickymaster on 2015-03-05
You mean from [https://www.virtualbox.org/wiki/Downloads?](https://www.virtualbox.org/wiki/Downloads?)

That's odd. I'm just seeing this:

[ATTACH=CONFIG]260473[/ATTACH]

 Do you mind to post the output you get from```
apt-cache policy virtualbox
```

---

### Post by v3.xx on 2015-03-05
I think I need a reading lesson :)
```
apt-cache policy virtualbox
virtualbox:
  Installed: (none)
  Candidate: 4.3.10-dfsg-1ubuntu2
  Version table:
     4.3.10-dfsg-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
     4.3.10-dfsg-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Package
```

Not installed, yet its running.  This could be due to [ram_booster]("http://ubuntuforums.org/showthread.php?t=1594694&page=6&p=13239427&viewfull=1#post13239427").

---

