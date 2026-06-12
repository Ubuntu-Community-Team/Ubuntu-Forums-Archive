---
title: "software updates security question"
date: 2006-09-17
forum: Server Platforms
---

### Post by sportman1280 on 2006-09-17
just wondering why we ask for a security password to upgrade the security patches for our machines.  It seems to me we should ask for the admin password for installing with symantec, but why ask it when upgrading the versions already installed?  its just one more password promt that seems unneeded.  

Dont get me wrong, im not ranting or anything.  I just am curious why we ask for the admin password to make our machines more secure.  anyone know?

---

### Post by daxelrod on 2006-09-17
Basically, this is a system-level security mechanism, and subverting it isn't worth it.

The program installing the updates needs to overwrite system files. Any program that changes system files is not allowed to do so by the operating system until it gains the appropriate privilages. The mechanism by which the program gains those privilages requires your password for authorization.

If we wanted to forego passwords for updates to existing software, we'd need to make the updater program run with higher privilages all the time. Then the program would have to be very carefully designed to only update existing packages when an administrative user asked it to, whithout allowing other system files to be modified and without anybody else using it to modify system files. It's not impossible, but it's a huge undertaking, and the operating system gives us the current security model for free.

I understand from a pure usability perspective why your suggestion may be good, but the underlying security foundation of the operating system means it would probably not be worth implementing.

---

### Post by sportman1280 on 2006-09-18
ah.... it all makes sense now :). thanks for the VERY good information. :)

---

