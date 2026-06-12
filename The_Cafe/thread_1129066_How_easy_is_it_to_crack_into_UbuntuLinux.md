---
title: "How easy is it to crack into Ubuntu/Linux?"
date: 2009-04-18
forum: The Cafe
---

### Post by Pasdar on 2009-04-18
I'm wondering about this because a Windows PC can be put at the mercy of a cracker with only a few lines of code in an executable.

Today when I was downloading a program for my Ubuntu I wondered, just how easy/difficult is it to crack this system. What if I download from an untrustable site? As I don't have time attempt anything myself at this moment, maybe someone with experience in programming for Linux can answer this.
When I download a tar.gz/deb/whatever and attempt to install this software through the normal procedures, is it at all possible that the software can attempt to do anything that I would not like it to do, without me approving/knowing? For example, can it open ports, add exceptions, use other programs that are already on the system? For example to send information to another PC, to collect info on the PC itself?

---

### Post by billgoldberg on 2009-04-18
> **Pasdar said:**
> I'm wondering about this because a Windows PC can be put at the mercy of a cracker with only a few lines of code in an executable.

Today when I was downloading a program for my Ubuntu I wondered, just how easy/difficult is it to crack this system. What if I download from an untrustable site? As I don't have time attempt anything myself at this moment, maybe someone with experience in programming for Linux can answer this.
When I download a tar.gz/deb/whatever and attempt to install this software through the normal procedures, is it at all possible that the software can attempt to do anything that I would not like it to do, without me approving/knowing? For example, can it open ports, add exceptions, use other programs that are already on the system? For example to send information to another PC, to collect info on the PC itself?

Sure it's possible.

Stick to the repos or trusted sources.

---

### Post by Pasdar on 2009-04-18
On Windows some of these attempts are stopped by the firewall or It will notify the user saying, X application is attempting to do Y, proceed YES/NO? Isn't there anything like that for Linux?

---

### Post by Nepherte on 2009-04-18
> **Pasdar said:**
> On Windows some of these attempts are stopped by the firewall or It will notify the user saying, X application is attempting to do Y, proceed YES/NO? Isn't there anything like that for Linux?
The firewall or anything else will not warn you if there's somthing malicious going on. If you give permission to install something, you declare that you know what you're doing. That's why you have to make sure you do know what you're doing ;) If you don't understand a command for example, simply don't execute it. If you don't trust a source, then don't use it. Et cetera.

---

### Post by NightwishFan on 2009-04-18
There is SELinux, which restricts what an application can do. Firestarter, a front end to netfilter firewall. Ubuntu requires the ability to grab your mouse in order to run administrator programs, you can test this by opening a root program like synaptic, and quickly opening up the menu at the top left before the password prompt appears. As for more security you should read the stickies here:

[http://ubuntuforums.org/forumdisplay.php?f=338]("http://ubuntuforums.org/forumdisplay.php?f=338")

---

