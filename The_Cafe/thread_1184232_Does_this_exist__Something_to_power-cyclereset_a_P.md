---
title: "Does this exist:  Something to power-cycle/reset a PC via TCP/IP?"
date: 2009-06-10
forum: The Cafe
---

### Post by diablo75 on 2009-06-10
Ok...  Here's what I'm looking for.  I just don't know what it's called.

I want something I can plug into a router.  Have a particular port forwarded to it.  Something I can login to over the Internet, through the router.  It's purpose is to await for me to connect to it solely for the purpose of doing power cycles (power off and then back on) or reset a PC.  Come to think of it, this PC is a Dell and I don't think it even has a reset button on it...

Anyway, there's got to be something out there that does this.  If not.... WHY NOT?  There's probably some good money to make off this invention.  I'd buy one!.......  Where can I buy one?  :D

---

### Post by FuturePilot on 2009-06-10
ssh?

---

### Post by LookTJ on 2009-06-10
SSH does this job well in Linux.

---

### Post by diablo75 on 2009-06-10
Well yeah, I know SSH is good in MOST cases, but....

I just want that extra measure.  A plan C.

---

### Post by conundrumx on 2009-06-10
In short, yes, it does exist.  There are hardware+firmware/BIOS solutions that allow the level of control you want.  Unfortunately, they're all used almost exclusively for enterprise customers.  Intel's vPro comes to mind as the most recent product.

As far as waking/booting a machine remotely, there's always Wake On LAN.  Do some googling, there's plenty of software to send the magic packet.

---

### Post by cariboo on 2009-06-11
Ssh in and then:

```
sudo shutdown -r now
```

the -r in the above command stands for reboot,
although why you want to restart a linux server is beyond me.

---

### Post by kevdog on 2009-06-11
I think this question may be more involved.  Ever had a computer still technically receiving power -- turned on -- but for some reason you couldn't log into it?  A black screen that wouldn't respond?  I think this may be what the user meant by a backup plan.

---

### Post by MaxIBoy on 2009-06-12
[http://thedailywtf.com/Articles/ITAPPMONROBOT.aspx](http://thedailywtf.com/Articles/ITAPPMONROBOT.aspx)

---

### Post by diablo75 on 2009-06-13
> **MaxIBoy said:**
> [http://thedailywtf.com/Articles/ITAPPMONROBOT.aspx](http://thedailywtf.com/Articles/ITAPPMONROBOT.aspx)

That's pretty funny!

---

