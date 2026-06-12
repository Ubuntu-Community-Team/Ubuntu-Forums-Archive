---
title: "Installing of Jupiter on Ubuntu 13.04"
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by kobras on 2013-03-20
Hello
Today I have installed newest vesrion of Ubuntu 13.04.
The first program which I have tried to install was a [Jupiter]("http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html").
I have done everything as it was written in that article, but in the end I got next error:

E: unable to locate package jupiter

what the problem?

---

### Post by oldos2er on 2013-03-20
Moved to Ubuntu +1 (Raring Ringtail).

---

### Post by mc4man on 2013-03-21
> **kobras said:**
> 
I have done everything as it was written in that article, but in the end I got next error:

E: unable to locate package jupiter

what the problem?
When you used add-apt-repository the source was added as raring, like - 
```
http://ppa.launchpad.net/webupd8team/jupiter/ubuntu raring main
```

Seeing as though there are no raring packages in the ppa 'apt-get update' will ignore the source, so no jupiter available

You can wait till such time as there is a raring package or install the quantal version & see, whether you should do that, **I've   no idea at all..**
If inclined to try you could either download the quantal jupiter package from ppa page directly & install or  edit your sources list as in screen, update, ect.

---

### Post by JMB74 on 2013-03-21
Jupiter has been retired and is not compatible with kernel 3.7 onwards.

---

### Post by rrnbtter on 2013-03-21
Greetings,
It's been there for me and doing fine.

rrnbtter-Satellite-L305 3.9.0-030900rc3-generic #201303171935 SMP Sun Mar 17 23:44:49 UTC 2013 i686 i686 i686 GNU/Linux

---

### Post by JMB74 on 2013-03-21
Maybe it behaves a bit better with 3.9?

[https://bugs.launchpad.net/jupiter-project/+bug/1091510](https://bugs.launchpad.net/jupiter-project/+bug/1091510)

It has still been retired though. 

[http://www.fewt.com/2012/12/an-important-announcement-about-jupiter.html](http://www.fewt.com/2012/12/an-important-announcement-about-jupiter.html)

---

### Post by cariboo on 2013-03-21
fewt commented about retiring Jupiter in the Fuduntu thread [here]("http://ubuntuforums.org/showthread.php?t=1637104&highlight=fubuntu")

---

### Post by kobras on 2013-03-21
ok, thank you. I have decided to install ubuntu 12.10

---

### Post by Hum137 on 2013-04-30
Hi!, I get the same problem, but did you try with gnome-power-manager or bumblebee? maybe that can do the job while Jupiter release a new version

---

### Post by cariboo on 2013-04-30
> **Hum137 said:**
> Hi!, I get the same problem, but did you try with gnome-power-manager or bumblebee? maybe that can do the job while Jupiter release a new version

There won't be a new version of Jupiter, according to the author, improvements have been made in the kernel and most distributions, so it isn't needed any more.

---

### Post by monkeybrain2012 on 2013-04-30
Jupiter is no more. But there may be a replacement
[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

---

### Post by montag dp on 2013-04-30
> **monkeybrain2012 said:**
> Jupiter is no more. But there may be a replacement
[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)Yup, I've been using TLP with good results since Jupiter went away.  It certainly saves some watts.

---

### Post by kevpan815 on 2013-04-30
This is a Ubuntu + 1 Forum! Only Discuss 13.10 in this Forum! Just FYI!

---

