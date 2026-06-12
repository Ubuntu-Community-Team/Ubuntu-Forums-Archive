---
title: "installing MySQL-4.0.4-0.i386.rpm installing MySQL-client-4.0.4-0.i386.rpm"
date: 2007-05-08
forum: Server Platforms
---

### Post by magpy on 2007-05-08
Hello all

I am having difficulty trying to install the above packages on ubuntu.  I heard that a file with the file extension .rpm is native to the red hat package management tool.  But I also heard that many linux distros have made rpm cross functional.

I tried to install the file: At 1st I did not know where to begin, so after a bit of googling I found out the above. (from the following links: (1) [http://monkeyblog.org/ubuntu/installing.html#rpm](http://monkeyblog.org/ubuntu/installing.html#rpm) (2) [http://www.tuxfiles.org/linuxhelp/rpminstall.html](http://www.tuxfiles.org/linuxhelp/rpminstall.html) )  I also found out that one could convert the file into a .deb extension using alien.  I was still at a loss after trying these suggestions I tried to install the package using:

rpm -i MySQL-4.0.4-0.i386.rpm MySQL-client-4.0.4-0.i386.rpm

In short the result was that the ubuntu server machine told me that rpm was unknown to the computer.  So I wondered if it was included on the OS iso that I burned; but before I did that I checked "man rpm" which returned no entry.  After that I ran:

sudo apt-get install rpm

this worked and I thought I was making progress, I checked: "man rpm" for an entry which gave some information.  Then I ran the same command:

rpm -i MySQL-4.0.4-0.i386.rpm MySQL-client-4.0.4-0.i386.rpm

and I got an error about failed dependencies:

I was told I the needed files:


"sh-utils" and "file-utils"

and the directories:

"/bin/sh" and "/usr/bin/perl"

I looked for these on line, but before that I ran the "whereis" command which revealed that I had all the needed files save, "sh-utils" and "file-utils".  I tried looking online for them and found what might be "sh-utils" at:

[http://mirror.anl.gov/pub/gnu/sh-utils/](http://mirror.anl.gov/pub/gnu/sh-utils/)

and what might be  "file-utils"  at:

[http://mirror.ne.gov/ubuntu/pool/main/d/desktop-file-utils/](http://mirror.ne.gov/ubuntu/pool/main/d/desktop-file-utils/)

Any ideas or help greatly appreciated

---

### Post by ohgod on 2007-05-08
I'm just curious, but why install rpms for mysql?  There are .deb packages in the ubuntu repositories for mysql, and it'd be much easier to install those.

---

### Post by magpy on 2007-05-08
Thanks sounds like a good idea, the reason why is that I am following a help guide called, "(Ebook - Chm) Sams - Teach Yourself Php Mysql And Apache In 24 Hours - 2003.pdf which was located at", located at:

[http://torrentz.ws/torrent/133478/Ebook-Chm-Sams-Teach-Yourself-Php-Mysql-And-Apache-In-24-Hours-2003-pdf](http://torrentz.ws/torrent/133478/Ebook-Chm-Sams-Teach-Yourself-Php-Mysql-And-Apache-In-24-Hours-2003-pdf)

it gives an overview of starting with LAMP from scratch, (could you forward the link for the .deb repositories?)
Also my worry is that if I use the .deb files then the instructions will not match the tutorials in the e-book.

---

### Post by ohgod on 2007-05-08
I'd install the packages in the Ubuntu repository like so:
```

sudo apt-get install mysql-server mysql-client

```

The guide you're using should still apply.  

Here's some documentation on setting up the mysql server in Ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MYSQL_Database_Server")

---

