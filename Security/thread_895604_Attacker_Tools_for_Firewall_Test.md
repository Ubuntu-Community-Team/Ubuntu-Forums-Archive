---
title: "Attacker Tools for Firewall Test"
date: 2008-08-20
forum: Security
---

### Post by Paris Heng on 2008-08-20
I wanna test the following attack on the firewall,

Land Attack
Fraggle
Large ICMP
IP Spoofing
Route-record
Source-record
Winnuke
Port Scan
Address Scan
Syn Flood
ICMP flood
UDP flood

Any tools can be use?

---

### Post by Titan8990 on 2008-08-20
You should look in to backtrack 3 for pentesting: [http://www.remote-exploit.org/](http://www.remote-exploit.org/)

---

### Post by firsttimeuser on 2008-08-20
I think hping and tcpreplay can do all the things you listed here. 

hping can customize and craft packet anyway you want, and tcpreplay comes hand when generating and playback traffic.

Just google them

---

### Post by Paris Heng on 2008-08-21
Danke!

---

### Post by Titan8990 on 2008-08-21
Danke?

---

### Post by DrMelon on 2008-08-21
Means "thankyou" in German, don't yar know.:)

---

### Post by Titan8990 on 2008-08-21
No I didn't :).

---

### Post by pcmann2004 on 2008-08-21
please help
i have a home network,  modem>firewall>cisco(5vlans)>servers>terminals/users.

what tools can i use to put the ultimate test on my network for vulnerabilities. on all ports and all protocols etc.
thanks in advance.
i mean i need to make sure my network is hack proof etc.

---

### Post by cariboo on 2008-08-21
Look at Titan8990 first post, he suggested the tool needed for penetration testing, backtrack 3, it is available here:

[http://www.remote-exploit.org/backtrack_download.html](http://www.remote-exploit.org/backtrack_download.html)
 
Jim

---

### Post by pcmann2004 on 2008-08-22
thanks ill give backtrack 3 a try,  also anyone has tips on linux on  itronix gobook or itronix hacks/tricks/mods
thanks again

---

### Post by The Tronyx on 2008-08-23
You may also want to look into an program called firetest.  It can be found at [http://dev.inversepath.com/trac/ftester](http://dev.inversepath.com/trac/ftester)

---

### Post by Paris Heng on 2008-08-23
Yeah, just using the back track 3. It is really a nice penetration testing tools. But I can't really simulate the testing on Smurf Attack. Did anyone know how to do it? Any How-to?

---

### Post by Paris Heng on 2008-08-23
> **pcmann2004 said:**
> thanks ill give backtrack 3 a try,  also anyone has tips on linux on  itronix gobook or itronix hacks/tricks/mods
thanks again

What is the *itronix gobook or itronix hacks/tricks/mods* all about?

---

### Post by Paris Heng on 2008-08-23
> **2point0 said:**
> You may also want to look into an program called firetest.  It can be found at [http://dev.inversepath.com/trac/ftester](http://dev.inversepath.com/trac/ftester)

What a good introduction here! Thanks alot. 

How to get the following modules? 

> Requirements: 
The following perl modules are required: Net::RawIP, Net::PcapUtils, NetPacket 

---

### Post by Paris Heng on 2008-08-23
Did anybody know the way to install the BackTrack 3 into the USB/HD? I found some document on the how-to. But in the BackTrack 3, it seem doesn't have any application to install BackTrack.

---

### Post by Titan8990 on 2008-08-23
It does have a spot to install it. I forget where, but it says (not tested) next to the install icon.

---

### Post by cariboo on 2008-08-23
To install perl modules, in a terminal type:

```
sudo perl -MCPAN -e shell
```

Then at the prompt 

```
install Bundle::CPAN
```

answer yes to all the question, and once it's done you can install the modules you need.

Jim

---

### Post by Paris Heng on 2008-08-23
Thanks.

---

