---
title: "Windows-route attack hypothesis"
date: 2010-11-17
forum: Security
---

### Post by zhaotianwu on 2010-11-17
This is just a hypothesis:
Because today there are more and more dual-system (e.g. Windows + Ubuntu) computers around, and usually the two operating systems share the same physical hard-disk. This present a unique weak point. The Hacker now can follow this route: Windows--->GRUB--->Ubuntu.
First, the hacker attempts to compromise your windows when you are running it. Because windows is basically garbage, so it can easily be compromised. Now the hacker gain the total control of your computer, and he implants the powerful Trojan malware sniffing out there is Ubuntu residing in the same hard-disk! Since Ubuntu is a big challenge and the hacker wants to prove himself, so he modifies the GRUB file and implants a keylogger that was exactly designed for Linux, so the next time when you use your Ubuntu, your Ubuntu becomes infected too.

Oh my god, I cannot help damning the weak Windows!!!:confused:

Anyone can prove false of this hypothesis?

---

### Post by wilee-nilee on 2010-11-17
Yes, but you will have to figure it out yourself.;)

Or maybe somebody will help you out.

---

### Post by cariboo on 2010-11-17
It could be possible in the right circumstances, but it's a lot of work for no gain.

---

### Post by zhaotianwu on 2010-11-18
> **cariboo907 said:**
> It could be possible in the right circumstances, but it's a lot of work for no gain.

So do you think if I do not install Windows at all, things will be a lot safer?
Or if you have to install Windows, create and use a separate user account rather than administrator will help?

---

### Post by uRock on 2010-11-18
Windows + Common Sense = Secure System

Don't install untrusted software, if you didn't buy it or download from a secure site, then chances are that it is not secure.

Use a non-administrative account when not administering the system.

Keep your system up to date. 

Keep your anti-malware up to date. I recommend MS Security Essentials for this, as it is free and high quality.

Windows is only easily compromised when the operator does not do his/her part in being a responsible administrator. Windows' OSes have a very decent EAL rating for its security perimeters. It is just a matter of learning and applying them. There are very few desktop operating systems that have a higher security rating.

I prefer Ubuntu over Windows on my home system, but I have confidence in the security of my Windows systems when I run them.

---

### Post by cariboo on 2010-11-18
> **zhaotianwu said:**
> So do you think if I do not install Windows at all, things will be a lot safer?
Or if you have to install Windows, create and use a separate user account rather than administrator will help?

Windows needs additional software in order to access partitions other that Windows partitions, in other words, Windows can't access ext2/3/4 partitions without 3rd party software.

If you are dual-booting, you can try it yourself.

Instead of wondering if something could happen, ask yourself why it would happen, what have you got on your hard drive that a cracker would want. Why would someone want to take over your Linux system to use in a bot-net, when there are much easier targets out there.

---

### Post by lisati on 2010-11-18
As others have pointed out, it can take a lot of work that might make the exercise not worth the effort.

The only time I recall [malware]("http://lisati.homelinux.com/wiki/index.php/Malware") causing a serious problem on one of my Windows installations had an element of [pebcak]("http://en.wikipedia.org/wiki/User_error"). I don't recall any problems (malware related or otherwise) on my Ubuntu machines that *didn't* have a pebcak component.

In other words, for something nasty to get on to Windows and then do some some mischief to the Ubuntu installation, it is likely to require help from the Ubuntu installation's user(s).

---

