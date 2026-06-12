---
title: "My firewall replies to ping"
date: 2011-04-29
forum: Security
---

### Post by BUSTERGONAD42 on 2011-04-29
Hi everyone,im a ubuntu virgin so be gentle,ive installed ubuntu and got ufw firwall running(wel  i think so anyhow) ive gone on a site to test my firewall,the ports come up as stealthed so i think they are ok but it says ive replied to a ping and could be used by hackers,basically how do i stop it from doing this please,or could you suggest a better firewall? im not very techie-so bear that in mind lol ,basically i want to get away from windows cos im sick odf all the constant updates and crap,thanks in advance....

---

### Post by sj1410 on 2011-04-29
please check if the firewall is running

```

sudo ufw status

```

for more information please visit

[http://blog.swapnil.me/2011/04/ubuntu-uncomplicated-firewall.html](http://blog.swapnil.me/2011/04/ubuntu-uncomplicated-firewall.html)

---

### Post by Lars Noodén on 2011-04-29
ping is good, it should be available for at least on your LAN.

---

### Post by bodhi.zazen on 2011-04-29
The debate on ping is as old as the debate on DROP vs REJECT.

Personally I do not think responding to a ping is something for the average desktop user to worry about and blocking a response to ping really dos not slow down would be intruders as modern cracking techniques do not rely on ping.

With that said, you need to configure ufw so as to not respond to ping:

Scroll down just a bit on this page to the ping section

[https://help.ubuntu.com/community/UFW#Advanced%20Syntax](https://help.ubuntu.com/community/UFW#Advanced%20Syntax)

---

### Post by BUSTERGONAD42 on 2011-04-30
hi fellas,thanks for replying to me,firstly for bodhizazen,i found the link cheers,bit stumped tho,where it says  change-accept to drop,do i have to type all of it in also does the  #ok ip codes just above it have to be typed too,soz for being dumb, but like i said earlier only just tried ubuntu so not used to typing commands,(used to being babysat by windows lol),thnaks to the other fellas for hlping too,much appreciated

---

### Post by bodhi.zazen on 2011-04-30
You need to edit that file as root:

```
gksu gedit /etc/ufw/before.rules
```

Scroll or search through the file, and yes change the accept to drop, so they look like this:

> # ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

You do not need to cahnge other lines. Save the file/changes and reload the rule changes

```
sudo ufw disable
sudo ufw enable
```

---

