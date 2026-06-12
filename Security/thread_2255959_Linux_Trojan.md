---
title: "Linux Trojan?"
date: 2014-12-08
forum: Security
---

### Post by kansasnoob on 2014-12-08
Not sure what to make of this:

[http://arstechnica.com/security/2014/12/powerful-highly-stealthy-linux-trojan-may-have-infected-victims-for-years/](http://arstechnica.com/security/2014/12/powerful-highly-stealthy-linux-trojan-may-have-infected-victims-for-years/)

---

### Post by C.S.Cameron on 2014-12-08
More here:
[http://www.theregister.co.uk/2014/12/09/deadly_snake_lurks_in_watering_hole_bites_linux/](http://www.theregister.co.uk/2014/12/09/deadly_snake_lurks_in_watering_hole_bites_linux/)

---

### Post by Habitual on 2014-12-09
interesting reads.

---

### Post by HermanAB on 2014-12-09
BS mostly.  There are umpteen programs in any standard Linux system that could act as a backdoor: ssh, nc, ncat, telnetd, ftpd...

However, these things are only really useful if you have escalated privileges and SELinux or AppArmor will limit damage.

---

### Post by Lars Noodén on 2014-12-09
> **HermanAB said:**
> BS mostly.  There are umpteen programs in any standard Linux system that could act as a backdoor: ssh, nc, ncat, telnetd, ftpd...

However, these things are only really useful if you have escalated privileges and SELinux or AppArmor will limit damage.

AppArmor currently only limits file access not network connections and even with the files the default profiles, when they exist, are often so loose as to not be much help.

---

### Post by bashiergui on 2014-12-09
> **HermanAB said:**
> BS mostly.  There are umpteen programs in any standard Linux system that could act as a backdoor: ssh, nc, ncat, telnetd, ftpd...

However, these things are only really useful if you have escalated privileges and SELinux or AppArmor will limit damage.What? The article says the malware can execute remote commands without elevated privileges. Don't know why you're calling BS. Sounds perfectly plausible for a nation state to produce.

This is nation state stuff which means that they're not going to burn it on any old guy. The article says "For at least four years, the campaign targeted government institutions, embassies, military, education, research, and pharmaceutical companies in more than 45 countries." So unless you're in those fields, and then only if you're into secret intellectual property stuff, you shouldn't worry.

That said, once the code becomes public then expect your average bad guy to start using/repurposing it. It's not public yet, I wouldn't expect that for a while.

---

### Post by HermanAB on 2014-12-10
Well, without elevated privileges, the malicious program will only be able to access a subset of the data belonging to the specific user that the program is executing as.  Therefore the damage would be limited by the normal user:group access control and SELinux/AppArmor.

---

### Post by C.S.Cameron on 2014-12-11
This is 2 days old, has the problem been fixed yet?

---

### Post by Non_Given on 2014-12-11
> **HermanAB said:**
> Well, without elevated privileges, the malicious program will only be able to access a subset of the data belonging to the specific user that the program is executing as.  Therefore the damage would be limited by the normal user:group access control and SELinux/AppArmor.   I.e. on a typical laptop/desktop system all the users data...

---

### Post by kansasnoob on 2014-12-11
> **C.S.Cameron said:**
> This is 2 days old, has the problem been fixed yet?

I don't think so. There have been a number of security updates but I've read the various CVE's and not seen this trojan mentioned.

---

### Post by schragge on 2014-12-12
I find [comments on LWN](http://lwn.net/Articles/625190) quite informational.

---

### Post by kagashe on 2014-12-12
> **schragge said:**
> I find [comments on LWN](http://lwn.net/Articles/625190) quite informational.

Thanks.

Kamalakar

---

### Post by fonsi2099 on 2014-12-15
What do we need to do to clean the trojan (turla)?

Howto detect if my system is infected? 

Thanks
Working Ubuntu 14.10

---

