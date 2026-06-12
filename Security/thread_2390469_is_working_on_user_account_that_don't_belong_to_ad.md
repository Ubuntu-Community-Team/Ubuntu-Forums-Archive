---
title: "is working on user account that don't belong to adm group more safe?"
date: 2018-04-29
forum: Security
---

### Post by arapaho on 2018-04-29
Does it makes sense to create a normal_user account for daily use for safety reasons on desktop PC (not server)? An account that would not belong to adm group?

id for normal_user (the second account created for daily use)

```
uid=1001(normal_user) gid=1001(normal_user) groups=1001(normal_user),24(cdrom),46(plugdev),102(netdev),1000(user that was created during install=first user)
```

id for user that was created during install=first user=belongs to adm group

```
uid=1000(first user) gid=1000(first user) grupy=1000(first user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),102(netdev),108(lpadmin),124(sambashare),1001(normal_user)
```

Does it increase safety when I browse internet only on normal_user account? If someone want to attack me is it for him more difficult when I work on normal_user account or no difference?

To sum up: is it worth a trouble to set a normal_user account, taking into consideration that I am the only one physical person who access this PC and no other physical users use it, so privacy is not an issue?

---

### Post by kurt18947 on 2018-04-29
I do have two users, 'admin' and normal or desktop user. Does it help? I don't know but I have had the desktop user account become wonky due to my tinkering. If I can't fix the wonkishness (is that a word?) I can create another desktop account and remove the misbehaving desktop account.

---

### Post by TheFu on 2018-04-29
Allowing access to fewer resources is always a good idea, provided the userid has sufficient access to complete the required tasks.  Excess rights on a system are bad for security.

It can be slightly less convenient, so most people wouldn't bother.

Whether this mitigation strategy is require, suggested, or totally optional is a personal decision.

---

### Post by deadflowr on 2018-04-29
Do you want others to be able to access log files to read or not?
That's all the adm group is for.
Kick the user out of sudo if you want them to have more limited rights.

---

### Post by arapaho on 2018-04-29
> **deadflowr said:**
> Do you want others to be able to access log files to read or not?
That's all the adm group is for.

I see. So it is not very important for me as no physical persons have access to this PC. And access from Internet by some kind of scripts through a browser and reading important logs is not possible? Correct?

> **deadflowr said:**
> Kick the user out of sudo if you want them to have more limited rights.

[COLOR=#000000]User that was created during install=first user belongs to sudo group but I don't have root account - I made it inactive. So I can't k[/COLOR]ick him out of sudo. The question is: is it safe to work on this account and use Internet or is it better to create another account not belonging to sudo and work within this account for daily use and Internet? 

As I understand creating another layer with less privileges is better but in this case is it worth bothering?

I ask because I have no idea how dangerous are scripts and Internet or just browser bugs for Linux. I am aware that in case of direct human attack additional layer made by creating another account would be not a problem to hack but what is a situation in case of malicious Internet sites?

---

### Post by HermanAB on 2018-04-30
Well, the more important the machine you work on, the more paranoid you should be.  If it is a personal machine, then you can relax a bit.

The main reason for user privilege separation is to prevent malicious programs, or good ole fat finger mistakes, from ruining your setup.

As for malicious programs, there are not many on Linux.  Since 1985, I only encountered one rootkit and it was made by Sony, for Windows machines and the one Linux virus I encountered, didn't actually work.

---

