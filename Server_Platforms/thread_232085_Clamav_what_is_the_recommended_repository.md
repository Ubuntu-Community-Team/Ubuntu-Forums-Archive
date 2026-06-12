---
title: "Clamav: what is the recommended repository?"
date: 2006-08-08
forum: Server Platforms
---

### Post by Robert S on 2006-08-08
I am looking at replacing my debian server with dapper LTS (because of the "LTS").

I have just installed clamav from the Universe repository.  Unfortunately this version is quite seriously out of date.  When I run freshclam I get:

$ sudo freshclam
ClamAV update process started at Tue Aug  8 22:03:09 2006
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.2 Recommended version: 0.88.4
DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
main.cvd is up to date (version: 39, sigs: 58116, f-level: 8, builder: tkojm)
daily.cvd is up to date (version: 1640, sigs: 6574, f-level: 8, builder: ccordes)

On my debian system I use the "official" volatile mirror to keep this package up-to-date without breaking my system.  Is there a similar repository for ubuntu, or can I safely use the debian repository without risking my setup at some stage in the future?  Shoud I use the sarge or the etch repository?

---

### Post by fago on 2006-08-09
I have the same problem. Currently I'm also a sarge and volatile user (for servers) and thinking about replacing it by dapper.

However this outdated clamav packages in universe are no option.. :( (security!)
Would be really great if clamav would be included in main - as it's often used on mailservers.

---

### Post by Robert S on 2006-08-09
From the length of time it took to get a reply to my posting it would appear that there isn't much demand for this.  Maybe ubuntu is used mainly on desktops (and maybe LAMP servers).

Looks like I'll stay with debian, which has done me very well for the last three years without any need for reinstallation.

I suppose I could manually compile clamav (which I used to do in the past) but I don't want to do this on a work server.

---

### Post by jacrider on 2006-08-09
I will try tonight to install on my server and report back.

Somewhere I have some documentation to help with this install.  I will let you know what worked or didn't work.

---

### Post by russelld on 2006-08-13
Maybe its got to do with clamav dependencies?

Upgrading clamav from debian sid makes Synaptic want to upgrade the libc6 family.

As libc6 is essential part of Ubuntu, I don't have the courage to do this .  It is not easy to back out of and I *Do* *Not* recommend this.  I've done this in the past and backing out of using libc6 from Debian Sid very nearly borked my Ubuntu system, and in the the process put me through two weeks of insanity. #-o 

Hopefully the Ubuntu devs are onto this!

If its any consolation I make sure my Ubuntu box is running freshclam to update virus signature database.

And plan to put together a Debian Sid server to get the latest clamav!

---

### Post by Robert S on 2006-08-14
> **russelld said:**
> Maybe its got to do with clamav dependencies?

Upgrading clamav from debian sid makes Synaptic want to upgrade the libc6 family.

As libc6 is essential part of Ubuntu, I don't have the courage to do this .  It is not easy to back out of and I *Do* *Not* recommend this.  I've done this in the past and backing out of using libc6 from Debian Sid very nearly borked my Ubuntu system, and in the the process put me through two weeks of insanity. #-o 

Hopefully the Ubuntu devs are onto this!

If its any consolation I make sure my Ubuntu box is running freshclam to update virus signature database.

And plan to put together a Debian Sid server to get the latest clamav!

I've had the same problems with libc6 in the past with mix-and-matching debian versions.  Not recommended for a server at work where I would have to incur the wrath of irate workmates!

I wonder about the usefulness of using a virus database with an outdated version of clamav.

Its hard to get away from the conclusion that ubuntu is not the first choice for a server distro if you want to run a mailserver with virus filtering - until somebody comes up with an appropriate repository with clamav security updates etc (a la volatile in debian).

---

### Post by stock99 on 2006-08-15
well you can always manually compile from source file and install it. But last time i did it , it does give me little hassle for compilation. I hope ubuntu community come out their repository for clamav soon too. Was waiting for this since breeze.....

---

### Post by lotusleaf on 2006-08-27
I've compiled the latest version of ClamAV on Dapper without any problems.

---

### Post by peter07 on 2006-09-02
> I've compiled the latest version of ClamAV on Dapper without any problems.

Compilation is easy, but I have problem with configuration. Have you created *.conf files manualy or you've just copied the old files ( from ubuntu deb ) ??

---

