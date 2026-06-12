---
title: "GnuPG 1 vs. 2"
date: 2008-12-03
forum: Security
---

### Post by strange_cathect on 2008-12-03
Hello,

I'm running Intrepid and it came with GnuPG 1. But GnuPG-2 is in the repositories. 

Why is this not the default and how can I begin using GnuPG-2 with enigmail and Thunderbird?

Or is there some kind of problem with this?

---

### Post by kevdog on 2008-12-04
There is no difference in gpg1 vs gpg2 to the end user.  Gpg2 is compiled against external libraries, whereas with gpg1, the are no external libraries -- all is built into the program.  Both offer the same functionality, same encryption algos, same ciphers, etc.  Both adhere to the RFC8440 standard.  I believe the main reason gpg2 was created was that it could be compiled against an external gnupglib library that contained all the encryption and cipher schemes.  It would be possible to change these schemes by simply reinstalling a new version of the library, rather than the entire gpg installation.

I would suggest if you really want cutting edge, that you compile gpg from svn sources: [http://ubuntuforums.org/showthread.php?t=649466](http://ubuntuforums.org/showthread.php?t=649466)

Ive verified the build instructions for gnupg for Intrepid, although the idea link is broken.  Ive yet to verify gnupg2 built instructions -- this should be done later today.

---

### Post by mrand on 2009-10-01
> **kevdog said:**
> There is no difference in gpg1 vs gpg2 to the end user.(many months later) I believe this is no longer true... gpg2 has transitioned to defaulting to RSA keys because DSA keys (and SHA-1, by the way) are no longer recommended by the security community.  Here is one of many decent writeups: [http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key](http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key)

So because of this, I want to generate a key using 2.0.12 of gpg2, which appears to be what Karmic is pointing to.  Except it seems to resist installing on my beta (today) based Karmic Mythbuntu install:  when I type gpg2, it says I need to use apt-get to install it, but when I try to use apt-get or aptitude, it says it can't find it.  Synaptic turns up zero hits, but shows all the repositories enabled.  *puzzle*

[INDENT]Marc[/INDENT]

---

### Post by rookcifer on 2009-10-01
> **mrand said:**
> (many months later) I believe this is no longer true... gpg2 has transitioned to defaulting to RSA keys because DSA keys (and SHA-1, by the way) are no longer recommended by the security community.  Here is one of many decent writeups: [http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key](http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key)

So because of this, I want to generate a key using 2.0.12 of gpg2, which appears to be what Karmic is pointing to.  Except it seems to resist installing on my beta (today) based Karmic Mythbuntu install:  when I type gpg2, it says I need to use apt-get to install it, but when I try to use apt-get or aptitude, it says it can't find it.  Synaptic turns up zero hits, but shows all the repositories enabled.  *puzzle*

[INDENT]Marc[/INDENT]

You don't need gpg2 to generate RSA keys.  At the command prompt type:

```
gpg --gen-key --expert
```

This will put you in "expert" mode and will allow you to create an RSA key that both signs and encrypts.

---

### Post by kevdog on 2009-10-01
For a clarification point -- since its been months since the thread is opened, I believe the default on both gnupg(1) and (2) is know to generate RSA keys as opposed to DSA keys.  This became official sometime in July or August 2009.  To get the exact date, the gnupg mailing lists can be consulted.

There are many ways of generating a key.  The use of the expert switch is one option.  I used to generate rsa keys with the use of:
gpg --gen-key -t rsa -b <bits either 1024,2048 or 4096>

I recommend at least 2048 bits on the key since I believe 1024 is still the default.

To re-answer the original question, gpg2 crypto libraries are dll's or modular.  With gpg the libraries are not dynamically linked.  Gpg1 has gone through more rigorous testing by the security community, and is generally excepted to be the default.  If in doubt I would choose gpg over gpg2.  This has been discussed several times on the gpg mailing lists and this is the general consensus.  YMMV.

---

### Post by nutznboltz on 2011-08-18
In this message:
The gpg 1.x series refers to 1.4.x
The gpg 2.x series refers to 1.9.x - 2.0.x

Here we are in 2011 in the eighth year since a gnupg 2.x was first released and there's still no single source stating all the differences between the 1.x and 2.x series.

If I'm wrong about this please post a link to it since it will be appreciated.  The NEWS file in the source doesn't have a true summary; if a feature was added and then removed you have to track it across versions to get a true feature summary.  For instance support for OpenSC was removed and re-added and replaced with pcs#15 and so on.

---

### Post by Soul-Sing on 2011-08-18
> **mrand said:**
> (many months later) I believe this is no longer true... gpg2 has transitioned to defaulting to RSA keys because DSA keys (and SHA-1, by the way) are no longer recommended by the security community.  Here is one of many decent writeups: [http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key](http://www.jroller.com/robertburrelldonkin/entry/openpgp_generating_a_strong_key)

So because of this, I want to generate a key using 2.0.12 of gpg2, which appears to be what Karmic is pointing to.  Except it seems to resist installing on my beta (today) based Karmic Mythbuntu install:  when I type gpg2, it says I need to use apt-get to install it, but when I try to use apt-get or aptitude, it says it can't find it.  Synaptic turns up zero hits, but shows all the repositories enabled.  *puzzle*

[INDENT]Marc[/INDENT]

[https://answers.launchpad.net/ubuntu/+question/167790](https://answers.launchpad.net/ubuntu/+question/167790)

---

### Post by Matt 6:27 on 2011-10-27
> **nutznboltz said:**
> In this message:
The gpg 1.x series refers to 1.4.x
The gpg 2.x series refers to 1.9.x - 2.0.x

Here we are in 2011 in the eighth year since a gnupg 2.x was first released and there's still no single source stating all the differences between the 1.x and 2.x series.

If I'm wrong about this please post a link to it since it will be appreciated.  The NEWS file in the source doesn't have a true summary; if a feature was added and then removed you have to track it across versions to get a true feature summary.  For instance support for OpenSC was removed and re-added and replaced with pcs#15 and so on.


The GnuPG site suggests gnupg2 includes the ability to deal with X.509 certificates where the earlier version doesn't.   What I'd like to know is if I upgrade to gnupg2, will that kill all my current keys I created with gnupg?  Or will this be a smooth transition?  Any advice on how to execute the upgrade (e.g., add gnupg2 before removing gnupg)?  Thanks in advance.

---

### Post by TechZilla on 2011-12-09
I use GPG2, and used to use GPG1.  I brought my keys over and back a couple times, without consequence. I think my main DSA2 key was originally created in GPG1, My RSA in GPG2.  Keeping compatible keys was one of the project goals, because otherwise there would most likely orphaned data.

All GPG1 standards are supported in GPG2, it just so happens almost all GPG2 standards are support in GPG1.

So you are safe, notwithstanding any distro related issues.

---

### Post by Matt 6:27 on 2011-12-28
Good to know.  Thanks!

---

