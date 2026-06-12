---
title: "Psyb0t"
date: 2009-03-30
forum: Security
---

### Post by mlnease on 2009-03-30
Hello,

I've just read about a botnet called Psyb0t at [http://www.linux-magazine.com/online/news/psyb0t_attacks_linux_routers_update](http://www.linux-magazine.com/online/news/psyb0t_attacks_linux_routers_update) .  According to this article, Psyb0t attacks Linux routers.  I'm not sure what this means.  Do I have anything to worry about connecting to the internet with Hardy using a Linksys cable router/wireless PCI adapter?

Thanks,

mike

---

### Post by SunnyRabbiera on 2009-03-30
Possibly, if you use strong passwords in your router then you should be fine.

---

### Post by mlnease on 2009-03-30
> **SunnyRabbiera said:**
> Possibly, if you use strong passwords in your router then you should be fine.

Thanks for the quick response, Sunny.  I installed this router years ago and have no recollection of using a password for the installation.  I'll have a look at the router documentation and see if I can figure it out.

mike

---

### Post by sisco311 on 2009-03-30
If I understand the article correctly, your system is vulnerable only if you allow (root) access to your router and/or computer through the internet. 

[list]
[*]remote access to the router (if it's supported) is probably turned off by default.  

[*]if you are using telnet, then switch to ssh. :)

[*]if you are using ssh, then use public key authentication instead of passwords. ;) [/list]

Please correct me if I'm wrong.

---

### Post by dacorr on 2009-03-30
It refers to routers running linux based firmware such as dd-wrt.

having a strong password will help but the botnet (network of psyb0t compromised machines) roll is to brute force root passwords as root login does not lock after a number of incorrect password attempts.

you could use a 32 character HEX pass phrase wich would slow it down and cause the botnet operator to bypass it but most of these attacks are automated.

Dac

---

### Post by mlnease on 2009-03-30
> **sisco311 said:**
> If I understand the article correctly, your system is vulnerable only if you allow (root) access to your router and/or computer through the internet. 

[list]
[*]remote access to the router (if it's supported) is probably turned off by default.  

[*]if you are using telnet, then switch to ssh. :)

[*]if you are using ssh, then use public key authentication instead of passwords. ;) [/list]

Please correct me if I'm wrong.

Thanks sisco311,

Hmm, it's been years since I've used telnet.  Pardon my ignorance but I'm not sure if I'm using ssh or not--again I'll have to refer back to my router documentation and review my installation--I guess?

I'll post back here (for the sake of other elementary users) if and when I get this figured out.

mike

---

### Post by mlnease on 2009-03-30
> **dacorr said:**
> It refers to routers running linux based firmware such as dd-wrt.

having a strong password will help but the botnet (network of psyb0t compromised machines) roll is to brute force root passwords as root login does not lock after a number of incorrect password attempts.

you could use a 32 character HEX pass phrase wich would slow it down and cause the botnet operator to bypass it but most of these attacks are automated.

Dac

Thanks, dacorr.

mike

---

