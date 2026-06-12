---
title: "Help Installing MySQL 4.0.27"
date: 2006-09-22
forum: Server Platforms
---

### Post by gfd on 2006-09-22
hello,

I need to install MySQL 4.0.27 on dapper.
I have not been able to find any packages or how tos for this.

I tried using the rpms from MySQL's website (with alien) but I can't get it to work properly. 
It does actually install, but the files are scattered across various non-standard directories which makes it very difficult to troubleshoot.

Could someone help me to compile it from source?

I have found [this how to]("http://www.ubuntuforums.org/showthread.php?t=93725") on compiling and installing MySQL 5 from source but according to the posts many people have found it problematic.

Thanks in advance

---

### Post by spp on 2006-09-22
I am not sure what exactly you are trying to accomplish. Do you wish to have MySQL installed? A particular version perhaps? My confusion stems from the 4.0.27 in the subject line and you trying to install MySQL 5 in the body of your post.

If you could let us know your ultimate goal, a proper solution could be formulated :)

SP

---

### Post by gfd on 2006-09-22
> **spp said:**
> I am not sure what exactly you are trying to accomplish. Do you wish to have MySQL installed? A particular version perhaps? My confusion stems from the 4.0.27 in the subject line and you trying to install MySQL 5 in the body of your post.

If you could let us know your ultimate goal, a proper solution could be formulated :)

SP

You're right SP.
I apologise for the confusion.

I would like to install MySQL 4.0.27.

I only wanted to point out that I found a how to on compiling MySQL v5, which I could perhaps use as a basis to compile v4.0.27, by making  appropriate changes.
However, since other people had problems with that how to, I thought it was best to not even try.

Thanks

---

### Post by spp on 2006-09-22
Try this guide. I used it awhile back for 4.1. 4.1 is a hell of a lot closer to 4.0.27 than 5. 

[MySQL 4.1]("http://www.devside.net/guides/linux/mysql")

It has been awhile since I compiled MySQL so I can't gurantee anything but this guided me through it.

SP

---

### Post by gfd on 2006-09-22
Ok,

I found a [sitepoint article]("http://www.sitepoint.com/print/php-amp-mysql-1-installation") which describes MySQL installation on Linux.

It uses a standard tar.gz from MySQL instead of compiling from source and the author states that the installation should work on debian installations.

Do you think that this could work on ubuntu or will I end up messing my system?

If you believe I should try, is the "Linux (x86, glibc-2.2, "standard" is static, gcc)" package in the "Linux (non RPM package)" section on MySQL's v4.0 [download page]("http://dev.mysql.com/downloads/mysql/4.0.html") the right one?

---

### Post by gfd on 2006-09-22
> **spp said:**
> Try this guide. I used it awhile back for 4.1. 4.1 is a hell of a lot closer to 4.0.27 than 5. 

[MySQL 4.1]("http://www.devside.net/guides/linux/mysql")

It has been awhile since I compiled MySQL so I can't gurantee anything but this guided me through it.

SP

Great timing!! 
Looks like we posted simultaneously.

I'll look into that right away.

Don't worry about my last post.
The 2 articles are pretty similar and I should be able to figure it out.

Thanks for your helpful and quick responses.

---

