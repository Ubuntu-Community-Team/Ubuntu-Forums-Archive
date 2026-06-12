---
title: "Seperate partition for /home?"
date: 2009-02-02
forum: System76 Support
---

### Post by Maverick1712 on 2009-02-02
Hi All,

I've been using Linux for awhile now,mostly on my laptop and a refurbbed desktop (neither of which were preconfigured for Linux). In that time, I got used to having a seperate /home partition because I like to have more than one distro going at once (I haven't found the perfect fit, but this might be because of hardware incompatibilities). I am finally going to be buying the system76 model I've wanted for awhile and was wondering if /home was on a seperate partition by default or if this is something I am going to need to do when I get the laptop (Just in-case I get a case of Distro wanderlust again). Thanks in advance for answering my question and for doing what you guys do.

Cheers,
Adam

---

### Post by jeamer on 2009-02-02
Hey Adam, 

Sure is (separate partition on /home)!

I think you'll find that all the hardware works with sys76. Trust me, they wouldn't sell a lappy model that they couldn't have working perfect outta the box. Great choice on the company Adam!

Jordan (2 yr happy PanV user!)

---

### Post by AusIV4 on 2009-02-02
I got my Gazelle 2 years ago next Thursday, but I don't recall a separate home partition. Sounds like this might have changed since then, and regardless migrating to a separate home partition is pretty easy.

---

### Post by Lee_Machine on 2009-02-03
The only thing that currently does not work is Audio over HDMI. Now this is in no a way S76 issue, but rather the sound drivers. This issue has been resolved but wont be in Ubuntu until the next version due out in April.

Beside that everything work as it should on my Pangoline Performance.

---

### Post by jdb on 2009-02-03
> **Maverick1712 said:**
> Hi All,

I've been using Linux for awhile now,mostly on my laptop and a refurbbed desktop (neither of which were preconfigured for Linux). In that time, I got used to having a seperate /home partition because I like to have more than one distro going at once (I haven't found the perfect fit, but this might be because of hardware incompatibilities). I am finally going to be buying the system76 model I've wanted for awhile and was wondering if /home was on a seperate partition by default or if this is something I am going to need to do when I get the laptop (Just in-case I get a case of Distro wanderlust again). Thanks in advance for answering my question and for doing what you guys do.

Cheers,
Adam

Better than a separate home partition is a separate data partition.

Put all YOUR stuff in directories in the data partition and link those directories to your home directory.

Move things like mail repositories to the data partition & link them back to where they were in you home directory.

You can easily tarball the data partition for backup, you can use it from any Linux flavor or OS, & you don't run into compatibility problems with all the configuration files in your home directory.

jdb

---

### Post by thomasaaron on 2009-02-03
We definitely create separate home partitions.

AUSIV4, we didn't do them back when you got your machine. I think we've been doing it for... maybe 9 months or a year.

---

