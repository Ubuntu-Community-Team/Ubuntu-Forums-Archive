---
title: "Ubuntu the safest Linux Distro?"
date: 2006-07-27
forum: The Cafe
---

### Post by kleeman on 2006-07-27
This interesting study:

[http://searchsecurity.techtarget.com/originalContent/0,289142,sid14_gci1202417,00.htm](http://searchsecurity.techtarget.com/originalContent/0,289142,sid14_gci1202417,00.htm)

suggests that it is the safest in that security patches tend to be released faster than other distros. Interesting! I guess that's what highly paid developers gets you...

---

### Post by Brunellus on 2006-07-27
Fedora guys should be coming by any second to remind us that SELinux is not enabled by default in ubuntu

---

### Post by win_zik on 2006-07-27
> **Brunellus said:**
> Fedora guys should be coming by any second to remind us that SELinux is not enabled by default in ubuntu

And it isn't. ;-D
There are also other pro-active security messures missing and even the author of the article says that his little survey was unsientific.

That said, thanks to the devs for apparantly doing such a good job when it comes to security patches, but the title of this thread is misleading at best .

---

### Post by Swab on 2006-07-27
Although that bug in breezy that left your password in a plain text, world readable file was really unforgivable....

---

### Post by ComplexNumber on 2006-07-27
> **Brunellus said:**
> Fedora guys should be coming by any second to remind us that SELinux is not enabled by default in ubuntu
it isn't :D. on the otherhand, whenever i do a clean install of fedora, the sunrpc port is always open inbetween my pc and the router. if i didn't have a router that has every port stealthed,  that would be a security risk. each time, i have to uninstall portmapper....just in case.
so even fedora is not without its faults. its as close as one can find to a secure system, though IMO.

---

### Post by Lord Illidan on 2006-07-27
I don't think so... The lack of SE or AppArmor is not very encouraging.

---

### Post by givré on 2006-07-27
> **Swab said:**
> Although that bug in breezy that left your password in a plain text, world readable file was really unforgivable....
right, so weird... :D

---

### Post by kleeman on 2006-07-27
> **win_zik said:**
> , but the title of this thread is misleading at best .
You missed the question mark after the title and the elaboration to the effect that this was only about the speed of patching in the OP.

---

### Post by prizrak on 2006-07-27
> **Swab said:**
> Although that bug in breezy that left your password in a plain text, world readable file was really unforgivable....

Yes a security issue that is only an issue if you already have access to a computer is SUCH a huge problem. No offense but that wasn't much of a security issue there.

Ubuntu is a pretty secure distro but hardly the most secure one. I think Debian would have that title.

---

### Post by Swab on 2006-07-28
> **prizrak said:**
> Yes a security issue that is only an issue if you already have access to a computer is SUCH a huge problem. No offense but that wasn't much of a security issue there.

Ubuntu is a pretty secure distro but hardly the most secure one. I think Debian would have that title.


OK, I know we all love Ubuntu... but dismissing a security issue as bad as that does nobody any good.  It was a huge oversight, and makes you wonder what other issues might exist.   

You know what people are like, they use the same password for everything.  Leaving a password in plain text is really bad.

---

### Post by agger on 2006-07-28
> **prizrak said:**
> Yes a security issue that is only an issue if you already have access to a computer is SUCH a huge problem. No offense but that wasn't much of a security issue there.

Ubuntu is a pretty secure distro but hardly the most secure one. I think Debian would have that title.

Leaving the password in a plain text *is* a really huge security problem. Many Ubuntu installations run in a multiuser environment, and if you're running a campus network (say) where students could just swipe each other's passwords ... 

Passwords should never ever be stored in plain text and that's final :-)

---

### Post by prizrak on 2006-07-28
ANY security issue that is exploitable ONLY by someone with access to the system is a non issue. I happen to have a friend in the trade (computer security) who called people concerned about that particular issue idiots. (yes his quite blunt). Anybody with access to a machine and malicious intent will be able to do just about anything they want (limited by their knowledge). There was no way to discover that log by accident, not to mention that if the system was properly administered there would be no way whatsoever to get to that log because properly administered systems chroot their users in their home directory. To make it worse the password was only saved if you run updates. In a multiuser environment no user but the sys admin would be a sudoer, hence he would be the only one to run the update. This wouldn't allow any other user steal other users' passwords only admin's.

> Passwords should never ever be stored in plain text and that's final
That part I agree with but there is also context.

---

### Post by asimon on 2006-07-28
I found it interesting that RHEL got a lower score than Fedora.

---

