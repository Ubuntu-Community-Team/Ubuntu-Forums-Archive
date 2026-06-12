---
title: "ubuntu servers hacked"
date: 2007-08-21
forum: The Cafe
---

### Post by jonathan21 on 2007-08-21
whats everyone think about the recent story about some ubuntu servers been hacked.does this mean that soon symantec will be offering us security software soon:).what is you take and could this have been prevented

---

### Post by bluenova on 2007-08-21
> These servers were found to have a variety of problems including, but not limited to, missing security patches, FTP (not sftp, without SSL) was being used to access the machines, and no upgrades past breezy due to problems with the network cards and later kernels.

Yes I think it could have been prevented.

---

### Post by original_jamingrit on 2007-08-21
I think this is it:  [http://ubuntuforums.org/showthread.php?t=527020&highlight=ubuntu+server+hacked](http://ubuntuforums.org/showthread.php?t=527020&highlight=ubuntu+server+hacked)

It was way out of date security, on servers running "lots of web software".

---

### Post by fuscia on 2007-08-21
didn't some openbsd servers get hacked a while back?

---

### Post by Spr0k3t on 2007-08-21
> **original_jamingrit said:**
> It was way out of date security, on servers running "lots of web software".

+1 ... not to mention unsupported.

---

### Post by eentonig on 2007-08-21
> **bluenova said:**
> Yes I think it could have been prevented.

No, it couldn't have been prevented. No matter which OS you throw at a problem. If the administrators are lazy, foolish and non-security aware... it will always get hacked.

Security is not a technological issue. It's a mindset.

---

### Post by PartisanEntity on 2007-08-21
It's really a non-story isn't it? Regardless of OS, using an obsolete and no longer supported system without the latest patches is a security risk begging to happen. I fail to see what is 'news' about this. It's like saying "Humans need oxygen to live".

---

### Post by Dragonbite on 2007-08-21
> **eentonig said:**
> No, it couldn't have been prevented. No matter which OS you throw at a problem. If the administrators are lazy, foolish and non-security aware... it will always get hacked.

Security is not a technological issue. It's a mindset.I think part of the issue here is WHY they did not update/patch. > From the Article (read [[COLOR="Blue"]here[/COLOR]]("http://www.eweek.com/article2/0,1895,2171318,00.asp"))
the servers have not been upgraded past breezy due to problems with the network card and later kernels.This *IS* a technological issue.

In the computer club I am a part of they wanted to install CentOS (a RedHat clone) on the server but could not because of the RAID drivers ( I believe).  They tried Fiesty but that didn't work either. Dapper was successful so in the end they went with it.

Yes, they could have done more but that's a lot of work for something the system should have been able to do.

---

### Post by n.aggel on 2007-08-21
> **fuscia said:**
> didn't some openbsd servers get hacked a while back?
no way this could have happen....openbsd is by far the more ssecure os in this planet......

---

### Post by qpieus on 2007-08-21
jonathan21 - you do understand that these servers were NOT Canonical production servers, right? They were local community servers that were not well maintained, security-wise. Canonical had no control of these servers. The people running the servers are at fault for not keeping their servers up to date and secure, not Canonical or Ubuntu. As someone earlier in this thread said, bad lazy admins could make just about any server insecure.

---

