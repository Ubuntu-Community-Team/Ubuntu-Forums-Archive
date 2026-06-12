---
title: "can't rsync between juju built servers"
date: 2015-03-17
forum: Ubuntu Cloud and Juju
---

### Post by rmustakos on 2015-03-17
octave-controller machine attempts to rsync directories with octave machines, gets "Permission denied (publickey)."
This includes machine attempting to rsync with itself.  

It seems counter intuitive that a controller is not able to communicate with the systems it is supposed to control.

The octave controller log doesn't mention anything since install.
auth.log says <date time> <machine name> sshd:[13053]: Connection closed by <ip> [preauth]

I can't rsh into any of the juju controlled machines as "ubuntu", I get the same error signature.
If I try to rsh into the machine I'm on, I get the same signature.

Everything I have read on this problem says that ssh is not set up right, but it was set up by either juju or maas, which is confusing the crap out of me.

I am new to linux, so, while i know there is data I can check to understand this better, I just don't know what it, and any help is appreciated.

---

