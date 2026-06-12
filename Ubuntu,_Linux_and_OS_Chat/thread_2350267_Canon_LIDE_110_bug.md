---
title: "Canon LIDE 110 bug"
date: 2017-01-23
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-01-23
Canon LIDE 110 give i/o error in sane_start with scanimage[URL="https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/1655814"]
https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/1655814[/URL]

I'd like to give attention to this bug, because it has affected me since updating to Xubuntu 16.04, which was 10 months ago. This scanner has worked out of the box since Xubuntu 12.04 and 14.04, but doesn't work in 16.04, even after adding ppa:rolfbensch/sane-git to my system.

My workaround to the issue was to install Windows XP on Virtualbox and use my scanner there, however, this workaround only works if one has a Windows CD laying around, but for those who don't have any Windows CD, this is a big issue.

If you are affected by this bug, please report it over at the bug link, because this bug needs more attention.

---

### Post by DuckHook on 2017-01-23
Not a technical support request. *Thread moved to **Ubuntu, Linux and OS Chat** as the more appropriate forum.*

---

### Post by mörgæs on 2017-01-23
Thanks for posting but I don't think anyone pays attention to 16.04. Focus is on creating 17.04.

If you can test 17.04 in a fresh install it will be more relevant to the developers.

---

### Post by c-gobletee-gook on 2017-06-04
I tested the Canon LIDE 110 on 17.04 and there is an error.   It used to work on earlier versions of Ubuntu

---

### Post by mörgæs on 2017-06-04
The same error as described in original post?

---

### Post by c-gobletee-gook on 2017-06-04
yes, same error with 17.04 i686.  NO ERROR with 17.04 [COLOR=#333333][FONT=monospace]x86_64 on different pc[/FONT][/COLOR]
presume this is the original post:  [https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/1655814](https://bugs.launchpad.net/ubuntu/+source/sane-frontends/+bug/1655814)
posted more details there

---

### Post by ardouronerous on 2017-06-04
As the OP of the thread, this is still an issue on Xubuntu 16.04.2.

---

### Post by mörgæs on 2017-06-04
- and it might stay like that. If it will be solved then it will be in the development release (17.10 for now). 

The best the two of you can do is testing whether or not the bug is in 17.10. If so then please add the findings in the report.

---

### Post by ardouronerous on 2017-06-04
would installing libsane from 14.04 be a good workaround? Because I've tested by LIDE 110 on Xubuntu 14.04 via virtualbox and it works.  would there be any problems with that workaround?

---

### Post by mörgæs on 2017-06-04
I don't know if the dependencies allow that. Anyway the long term solution is to try to fix the bug in the development release - if it's not fixed already.

---

### Post by smajchl on 2017-09-17
I did this workarround already by installing 14.04 repositary and installing libsane version from this repository... I used following versions for following packages:

```
libsane 1.0.23-3ubuntu3
sane-utils 1.0.23-3ubuntu3

xsane 0.998-5ubuntu1
xsane-common 0.998-5ubuntu1
simple-scan  3.12.0-0 
```

and you also need to install:

```
 libcolord1 1.0.6-1
liblcms1 1.19
```


And my Canon LiDE 110 works now on Ubuntu 16.04
You can tell apt-get to lock the versions you want...

---

