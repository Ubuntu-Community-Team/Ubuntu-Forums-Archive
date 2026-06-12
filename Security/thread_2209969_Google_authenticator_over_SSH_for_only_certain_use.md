---
title: "Google authenticator over SSH for only certain users/ports"
date: 2014-03-08
forum: Security
---

### Post by izziere on 2014-03-08
Is there a way of getting Google Authenticator to be required only when using certain users or accessing SSH server by certain ports? I only want to provide a challenge code when accessing SSH from outside of LAN.

Many thanks.

I

---

### Post by izziere on 2014-03-10
The answer is, of course, to run two instances of SSH, pointing to different ports with only one enabling Google Authenticator.  There is a useful howto here:

[http://ubuntuforums.org/showthread.php?t=1497376]("http://ubuntuforums.org/showthread.php?t=1497376")

One point that seems obvious with hindsight but is not stated is that in Step 3a you also need to change sshd to sshd2.

---

