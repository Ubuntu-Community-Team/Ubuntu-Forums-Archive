---
title: "UFW Block all Outgoing"
date: 2009-06-25
forum: Security
---

### Post by Chaplipman on 2009-06-25
Is it possible to block all outgoing traffic with UFW? Would I need another program? Please let me know. :)

---

### Post by lovinglinux on 2009-06-25
> **Chaplipman said:**
> Is it possible to block all outgoing traffic with UFW? Would I need another program? Please let me know. :)

I guess not without editing some files. I never tried tho.

I think Firestarter can do that, but ufw is the recommended one.

You can also learn iptables commands instead of using a firewall manager like UFW and Firestarter. Is actually simple to achieve what you want with iptables commands.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Why do you need to block outgoing connections anyway?

---

### Post by Chaplipman on 2009-06-26
> Why do you need to block outgoing connections anyway?

Paranoia.

> You can also learn iptables commands instead of using a firewall manager like UFW and Firestarter. Is actually simple to achieve what you want with iptables commands.

I have been avoiding learning iptables for a long time, maybe I need to get with the program.

> I think Firestarter can do that, but ufw is the recommended one.

Is there a way to do this through the GUI?  Anyone? Much thanks BTW.:)

---

### Post by Agent ME on 2009-06-27
If you block all outgoing, then you've killed your internet connection. Why not just unplug your computer from the internet?

---

