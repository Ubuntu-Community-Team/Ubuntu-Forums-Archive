---
title: "Upgrade kernel in Ubuntu server"
date: 2009-06-19
forum: Server Platforms
---

### Post by reswob on 2009-06-19
I have a question.  I am currently running Server 8.04 with kernel 2.6.24-24-server and I am required to upgrade the kernel to 2.6.30.  I've been searching for the command line syntax to make that happen, but short of compiling from source, I haven't found a way.  sudo apt-get dist-upgrade doesn't seem to do it and I don't want to upgrade to 9.04 yet unless that is the only way to get 2.6.30.  

Is there a command line option to upgrade the kernel?  Do I need to add a certain repository?

Is there a link to someplace that already gives the right syntax?

Thanks.

Craig

---

### Post by jerrrys on 2009-06-19
this may be what your looking for

[http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/)

found it here

[http://www.google.com/search?q=command+line+option+to+upgrade+the+kernel+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=command+line+option+to+upgrade+the+kernel+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Bachstelze on 2009-06-20
> **jerrrys said:**
> this may be what your looking for

[http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/)

found it here

[http://www.google.com/search?q=command+line+option+to+upgrade+the+kernel+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=command+line+option+to+upgrade+the+kernel+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

This is not correct, as it will only let one upgrade to a kernel that is in the Ubuntu repositories. Since the OP needs to upgrade to a 2.6.30 kernel, and this version of the kernel is not in the Ubuntu repositories, he will have to compile it. [Here]("http://ubuntuforums.org/showthread.php?t=311158")'s a guide on compiling the kernel on Ubuntu.

---

### Post by jerrrys on 2009-06-20
ok, i stand corrected, but that is why i said this MAY be what your looking for...later

---

