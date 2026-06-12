---
title: "help with proftpd"
date: 2008-12-10
forum: Server Platforms
---

### Post by rstange on 2008-12-10
Hello !

I am trying to set up an Ubuntu Server with Proftpd. Proftpd works fine on version 1.3.1
Have tried to set up the server with FTPS, have used days to get it work but no luck, before I found out that it is a bug in 1.3.1 that gives me the message that the TLS did not shut down properly in filezilla. So I found the 1.3.2rc3 but I just do not figure out how to install the package. Have downloaded the file, unzipped it ant used ./config make and make install. No errors, but after a restart the server still has 1.3.1
Have also tried to install the 1.3.2rc3 without having the 1.3.1 installed but I can not find out how to start or use it.

Have used a week on this project but still I can't figure out what I am doing wrong. Have searched all over the internett to find guides, but nothing have helped me so far.

Is there someone who could tell me how to install the 1.3.2rc3?

- thanks ! and yes, I have just started to use linux :)

---

### Post by m_l17 on 2008-12-10
Compiling Easy How To:

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

This one is more advanced, Compiling Software:

[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

or

Instead of compiling Proftpd 1.3.2.rc3, try with an older version of Filezilla until the error goes away. That only happens with new versions of Filezilla. And when Proftpd 1.3.2 gets into the repos you will be able to install it just like 1.3.1 and be able to use new versions of Filezilla.

or

Install vsftpd:

[http://ubuntuforums.org/showthread.php?t=518293&highlight]("http://ubuntuforums.org/showthread.php?t=518293&highlight")

Info:

[http://vsftpd.beasts.org/]("http://vsftpd.beasts.org/")

---

