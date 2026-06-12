---
title: "Dell Computer ID Number"
date: 2008-10-01
forum: Security
---

### Post by dgoddard1 on 2008-10-01
When I boot my Dell Studio 1535 Laptop, I get a screen asking me for a password (My preference that I set in the bios setup).  What bothers me is that this screen shows an identification number which is the same as the Dell "service tag number" plus a space and a few more characters.  

I am wondering if this is some sort of a number identifying my compter that can be accessed by others via the internet.  I would ask Dell but I would not necessarily trust the answwer that they would give me, based on the way that Intel tried to slip this sort of thing into their pentimum chips a few versions ago.  A number that serves their convenience might be more of a security hole than I would care to have.

Anybody got any background on this.

---

### Post by stmurray on 2008-10-01
This number doesn't make the machine any more vulnerable to attack.  It is just stored in the Bios (and as stickers on the case).  You set the hostname of the machine and (probably) your ISP will set it's IP address and domain name, which are the ways a remote host find your machine on the Internet.  The service number can be read by (Dell) software once you are booted, but if an attacker can run that, it is already game over.  

However, the service tag number does give a ton of info about the machine (at least as it was when it was purchased) if you go to Dell's service website, so there is perhaps some privacy issues there.

---

