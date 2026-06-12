---
title: "Missing libipt_INBOUND.so and libipt_OUTBOUND.so"
date: 2008-11-14
forum: Security
---

### Post by mongobongo on 2008-11-14
Not sure if this is the right forum or not, but my libipt_INBOUND.so and libipt_OUTBOUND.so target extensions are missing from /lib/iptables/

I am running Ubuntu 8.04 on linux-2.6.24-21-generic with iptables v1.3.8 and all the latest updates applied.

I often call OpenVPN and my config file from the terminal.  My config file loads my up/down scripts as well.  

In order to successfully pass traffic across the tunnel (in the past) I would update my iptables by issuing (from the terminal)

sudo iptables -I OUTPUT 12 -o tun0 -j OUTBOUND
sudo iptables -I INPUT 16 -i tun0 -j INBOUND

This all worked fine for allowing traffic across the tunnel... up until a few days ago (which was the last time I used OpenVPN).  Now all of a sudden my iptables errors out with the following messages:

iptables v1.3.8: Couldn't load target `INBOUND':/lib/iptables/libipt_INBOUND.so: cannot open shared object file: No such file or directory

iptables v1.3.8: Couldn't load target `OUTBOUND':/lib/iptables/libipt_OUTBOUND.so: cannot open shared object file: No such file or directory

This has me wondering if a bad patch escaped into the wild and has removed those files?  Reason I say this, is because my floater-laptop (which is just as up to date as this laptop) is missing those files as well. 

If this is the case.  How do I get those files back or fix the issue?

Any help would be greatly appreciated.  Life without OpenVPN is difficult to say the least.  

:(

---

### Post by mssever on 2008-11-15
Try reinstalling the relevant packages.

---

### Post by uljanow on 2008-11-15
The user-defined chains INBOUND and OUTBOUND don't exist.

```
iptables -A INPUT -j foobar
iptables v1.4.0: Couldn't load target `foobar':/lib/iptables/libipt_foobar.so: cannot open shared object file: No such file or directory
```

---

### Post by mongobongo on 2008-11-16
> **mssever said:**
> Try reinstalling the relevant packages.

I did that yesterday with apt-get, and it still didn't work.  Tried it again just a few minutes ago and now everything works fine.  

> **uljanow said:**
> The user-defined chains INBOUND and OUTBOUND don't exist.

```
iptables -A INPUT -j foobar
iptables v1.4.0: Couldn't load target `foobar':/lib/iptables/libipt_foobar.so: cannot open shared object file: No such file or directory
```

They still don't.  [Question is though]("http://faultgame.com/images/twilzone.wav")... Did they Ever?  Anyways, everything is working, so I am not going to sweat it.  

Now I can stop using my XP VM for OpenVPN.

Thanks everyone.

---

