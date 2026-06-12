---
title: "ufw disable ping / icmp"
date: 2008-04-28
forum: Security
---

### Post by frediE on 2008-04-28
anyone know how to disable(drop) ping(icmp) requests with uncomplicated firewall (ufw)?

i am using ubuntu 8.04 and the ufw seems really easy to use but that one is being sneaky.  :-) 

let me know your thoughts.

---

### Post by Monicker on 2008-04-28
> **frediE said:**
> anyone know how to disable(drop) ping(icmp) requests with uncomplicated firewall (ufw)?

i am using ubuntu 8.04 and the ufw seems really easy to use but that one is being sneaky.  :-) 

let me know your thoughts.

I think this will do the trick:

[https://answers.launchpad.net/ufw/+question/26585]("https://answers.launchpad.net/ufw/+question/26585")

---

### Post by The Tronyx on 2008-04-28
> **frediE said:**
> anyone know how to disable(drop) ping(icmp) requests with uncomplicated firewall (ufw)?

i am using ubuntu 8.04 and the ufw seems really easy to use but that one is being sneaky.  :-) 

let me know your thoughts.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

If you scroll down a bit, it looks like you can do something like:

> 
sudo ufw deny <insert protocol here (ICMP)>


---

### Post by frediE on 2008-04-28
```
Yes, but not with the ufw front-end. Look in /etc/ufw/before.rules and comment out this line:
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```


hey! i searched all over for that.  :-)  oh well.. super thanks that did the trick!


side note:  that seems a like a huge missed the mark?  why would i want to enable a firewall if it doesn't block ping?  a taunt to all the script kiddies out there?  i know you can see meeeee but just try to get in.

maybe the powers that be should implement a "ufw deny icmp" or it should be automatically dropped when you do a "ufw enable".

oh well... just my nickel.
thanks.

---

### Post by hggdh on 2008-04-29
There are some quite strong misunderstandings on ICMP usage. Before blindly blocking ICMP, it might be a good idea to look up what ICMPs are useful, what are potentially dangerous, and what are the risks.

See, for example, [http://www.sys-security.com/archive/papers/ICMP_Scanning_v3.0.pdf](http://www.sys-security.com/archive/papers/ICMP_Scanning_v3.0.pdf).

Another source, more up-to-date, is [http://www.gont.com.ar/drafts/icmp-attacks/draft-ietf-tcpm-icmp-attacks-03.txt](http://www.gont.com.ar/drafts/icmp-attacks/draft-ietf-tcpm-icmp-attacks-03.txt).

---

### Post by frediE on 2008-04-29
i am not sure "misunderstandings" is really the right word.  i admit i did  not read the entire 218 pages :-), and i would like to think i have a good understanding of security..... but all of the "useful" icmp features could also be extremely damaging (at least the info that is collected).

so i still believe leaving icmp open is an invitation for trouble.


i guess what i am trying to say that Ubuntu does a GREAT job,  in leaving ufw disabled by default 99% of the people out there behind a hardware firewall do not need it.  but for those that find a terminal and know how to enable ufw, it should be set by default to protect.... or easy to configure (sudo ifw disable icmp).

---

