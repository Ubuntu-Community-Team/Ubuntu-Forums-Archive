---
title: "Issue with installs referencing the cdrom"
date: 2006-08-20
forum: Server Platforms
---

### Post by Niczi on 2006-08-20
I know that this is problem listed here somewhere but for the life of me, I have not been able to find the fix/answer.

When I try to install some packages, I get an error that it was not able to fetch info from the cdrom.  Here is the error I got when trying to install apache2 and php5.

> Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/pool/main/p/php5/php5-common_5.1.2-1ubuntu3.1_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/pool/main/p/php5/libapache2-mod-php5_5.1.2-1ubuntu3.1_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I need to get around this due to not having a working cdrom in the box this is setup on.  I have to pull one out of my main machine to do anything and it is starting to get a little tiring...

Thanks for any hints or info.

Niczi

---

### Post by meng on 2006-08-20
Try:
sudo vim /etc/apt/sources.list
(or use the editor of your choice)

and comment out the cdrom repository.

then
sudo apt-get update

---

### Post by Niczi on 2006-08-20
> **meng said:**
> Try:
sudo vim /etc/apt/sources.list
(or use the editor of your choice)

and comment out the cdrom repository.

then
sudo apt-get update

ahh meng, you are a genius...i got to looking and i had forgot to comment out one of the cdrom repositories...

my thanks...

<bow>[-o< [-o<

---

