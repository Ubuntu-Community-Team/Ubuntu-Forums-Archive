---
title: "OpenSSH and Neatx"
date: 2010-06-08
forum: Security
---

### Post by lucacerone on 2010-06-08
Hi all,
I just installed OpenSSH and NeatX to access
my work computer from remote.
I just would like to know how I can check that the
connection is actually encrypted.
I also would like to configure something
like the number of simultaneous connection and this kind of stuff.
Is this possible?
Thanks a lot in advance,
Cheers, -Luca

---

### Post by bodhi.zazen on 2010-06-08
> **lucacerone said:**
> Hi all,
I just installed OpenSSH and NeatX to access
my work computer from remote.
I just would like to know how I can check that the
connection is actually encrypted.
I also would like to configure something
like the number of simultaneous connection and this kind of stuff.
Is this possible?
Thanks a lot in advance,
Cheers, -Luca

If you want to "know" your traffic is encrypted, install Wireshark and look at the packets.

You will need to be more specific re: "configure something". You may limit connections with iptables, but I am not sure what you are wanting, so hard to know what to advise.

---

