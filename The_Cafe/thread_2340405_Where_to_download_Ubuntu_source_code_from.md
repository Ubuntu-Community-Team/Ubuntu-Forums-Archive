---
title: "Where to download Ubuntu source code from"
date: 2016-10-18
forum: The Cafe
---

### Post by tech291083 on 2016-10-18
Hi friends,

I often download and install new versions of Ubuntu, but if someone with proper programming knowledge wants to read and possibly modify the actual source code of Ubuntu OS itself (its open-source, so code is made available free of cost, I guess) where can he download the same from? There must be millions of lines of code, with comments thrown in to make it easier for a developer to identify as to what a particular piece of code does. There must be some suggested way of going through these millions of lines of code as well.

Thanks a lot.

---

### Post by Y^2om&amp;#7sgP on 2016-10-18
Try this

[http://cdimage.ubuntu.com/releases/16.04/release/source/]("http://cdimage.ubuntu.com/releases/16.04/release/source/")

---

### Post by colmax on 2016-10-20
Hi T
Maybe go settings>software&updates>ubuntu software & tick source code
Cheers

---

### Post by yetimon_64 on 2016-10-20
> **colmax said:**
> Hi T
Maybe go settings>software&updates>ubuntu software & tick source code
Cheers

OP, the suggestion above should give you access to the system package sources.

Once you have the access to the source code, here are a couple of links regarding how to compile a package ... the first one is specifically about building a java runtime environment, but the commands used are typical for building packages. The second howtogeek link is a more general guide about building from a downloaded tar archive using pidgin as an example (it is an older guide from 2012)...
[http://askubuntu.com/questions/246690/how-to-use-apt-to-get-source-code-and-then-do-separate-compile](http://askubuntu.com/questions/246690/how-to-use-apt-to-get-source-code-and-then-do-separate-compile)
[http://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/](http://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/)

These next 2 are Ubuntu documentation links for compiling from source, both contain sections for "getting the software you want" or "obtaining the sources" ...
[CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")
[CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

Regards, yeti.

---

### Post by tech291083 on 2016-12-14
Thanks a lot friends and sorry for the delayed response.

---

### Post by oldos2er on 2016-12-16
You simply run ```
apt-get source <package name>
``` in a terminal.

---

### Post by tech291083 on 2017-04-29
> **oldos2er said:**
> You simply run ```
apt-get source <package name>
``` in a terminal.

Brilliant, thanks a lot.

---

