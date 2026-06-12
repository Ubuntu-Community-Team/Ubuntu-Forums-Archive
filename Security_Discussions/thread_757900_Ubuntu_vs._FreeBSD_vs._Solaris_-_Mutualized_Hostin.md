---
title: "Ubuntu vs. FreeBSD vs. Solaris - Mutualized Hosting Server Architecture"
date: 2008-04-17
forum: Security Discussions
---

### Post by cookie971 on 2008-04-17
Hey there fellow Ubuntu-Fans !!!

I'm a fan of Ubuntu, I think Ubuntu is the next thing next to Microsoft and Apple, I give lots of love to this system.

Now, I'm a Junior Systems Engineer for an ISP at my place and I'm rethinking our mutualized hosting service. Currently it's based on Ubuntu with a not so functionnal Grsec kernel that hangs every now and then so  it had to be deactivated. 

Okay so here I rethinking the service, and here I go with the reflection :

1. Jailed userpaces, FreeBSD style or Containers Solaris style. Verio vhosts are using FreeBSD Jails and/or Chroot for their hosting service quite secure for them.

2. Solaris style containers for the overall Apache instance with 2 zones, a datazone the read+write accesible only to ftp/ftps sevices and a public webzone with read-only privileges accesible to surfers.

3. FreeBSD and Solaris style event auditing to log each and every action on the server made by admins and users.

4. Solaris style Predictive Self Healing, oooooohh! This is a sweet feature in Solaris.

I know that Ubuntu implements some of features up there if not all via third party software. But here I am torn between my love for Ubuntu and these two OSes that wish to conquer my heart and I'm here like a married man in front of his first temptation. Any of you guys have some best practices to share with me for this ?

Thanks,

CookieMonster

---

