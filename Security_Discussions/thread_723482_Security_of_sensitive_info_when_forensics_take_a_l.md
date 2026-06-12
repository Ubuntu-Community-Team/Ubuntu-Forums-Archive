---
title: "Security of sensitive info when forensics take a look at ubuntu PC?"
date: 2008-03-13
forum: Security Discussions
---

### Post by sneax on 2008-03-13
Hello, I'm wondering how safe sensitive data would be when forensics take a look at your computer.

This is the setup:
Ubuntu installed on hard drive, swap partition also on hard drive. One of the different user directories is mounted from a usb stick. Let's say /home/josh.

Imagine josh does some online banking, emailing with thunderbird, etc... which NOBODY is allowed to find out. If shuts down the computer and takes out the USB stick with his home directory, what info can forensics find on the computer itself.

- Is the SWAP retrievable, maybe having some firefox cache in it?
- Does some network components make logs of what ip's they visited or maybe what ip's they resolved into domain names?
- Basicaly, what user based data is their dat ubuntu stores in / (exluding /home/* )

Thank you,
Thomas

---

### Post by The Tronyx on 2008-03-13
I like this post a lot.  To be honest, forensic analysis of machines is a pretty cool field of study.  There's been some even cooler stuff being done by Princeton regarding cold boot attacks on encryption keys.

While I clearly see your post isn't directly related to encryption, this info might be of some help regarding what is and what is not left behind in RAM.

Hope this helps.

[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)

---

### Post by handydan918 on 2008-03-13
I believe that if the whole drive is encrypted, you should be cool, including the swap partition.
I'd be more concerned about that pesky thumbdrive....
And I agree with 2point0...the whole field of forensics is cool. The research on the cold ram hackage is really an eye-opener...it totally doesn't matter what the O/S is or anything....

---

