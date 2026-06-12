---
title: "Crashes on Ultra 5"
date: 2006-07-13
forum: Sun Sparc Users
---

### Post by chansiuming on 2006-07-13
Under quite heavy memory (and swap) usage Ubuntu 6.06 LTS died on my Ultra 5 machine. The last messages in syslog were a bit alarming:

Buffer I/O error on device hda2, logical block 4294967295
attempt to access beyond end of device
hda2: rw=0, want=34359738368, limit=28965195

About a ten of these and then it died. Not answering PINGs or anything. Is Ultra 5 even officially supported?

---

### Post by allnameswereout on 2006-07-16
> **chansiuming said:**
> Under quite heavy memory (and swap) usage Ubuntu 6.06 LTS died on my Ultra 5 machine. The last messages in syslog were a bit alarming:

Buffer I/O error on device hda2, logical block 4294967295
attempt to access beyond end of device
hda2: rw=0, want=34359738368, limit=28965195

About a ten of these and then it died. Not answering PINGs or anything. Is Ultra 5 even officially supported?

I don't know how come or how to solve but I wonder what makes you think this is a software problem and not a hardware problem? Do you understand what is happening here? How often did it crash w/this message in the log? After you verified its a software error consider to add this in the Bugzilla DB or report it on the  ML.

Re, your question: the Sun Ultra 5 is well supported by Linux and userland. Debian GNU/Linux has supported it well for ages. Even its hardware, including for example the sound card. Ubuntu includes all this support as well. However, the Ubuntu/SPARC port is not an official release (yet). So in essence by running this port you are a beta tester and should not run the port in a production environment. That said, I'd say that minus a few known bugs which you may or may not stumble upon the port works stable and is usable. YMMV.

---

### Post by chansiuming on 2006-07-17
> **allnameswereout said:**
> I don't know how come or how to solve but I wonder what makes you think this is a software problem and not a hardware problem? Do you understand what is happening here? How often did it crash w/this message in the log? After you verified its a software error consider to add this in the Bugzilla DB or report it on the  ML.


Well, the box had over a year of uptime with Debian sarge, using 2.6.11 kernel. I ran heavy hard disk grindin' compilations on it and it never crashed. Of course, I've no real way of verifying whether it's a hardware or software problem. And no, I don't understand what is happening there, the block layer gets/generates an odd request, but where that comes from is beyond me. I've had this crash only once (and I'm not going to repeat the circumstances that caused it), and just thought to post in the forum in case there are others with problems on Ultra 5, which would confirm to me, that there might be a problem - then I could go for Solaris, or something.

---

