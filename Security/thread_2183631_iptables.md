---
title: "iptables"
date: 2013-10-25
forum: Security
---

### Post by hectorenowel on 2013-10-25
Hi,

So I'm hosting a game server on a Windows Server 2008 OS (there are some reasons I'm not directly using linux but that doesn't matter), the application is srcds.exe and it uses the port 27015. I recently got some DDoS attacks and decided to create a virtual ubuntu server as windows' firewall sucks.
Basically it sends packets to srcds.exe and I would like to filter them using iptables. I'm posting here hoping to get some help about it because I couldn't manage to stop the attack yet (all my apologises if it isn't really related to ubuntu, link me if there is a more proper place).

I don't have any knowledge about packets and all but I used wireshark to record the attack and here's an example : [http://uppix.net/1zgnP1.png](http://uppix.net/1zgnP1.png) (I can upload the record)
They all have in common the "[Z" and "pB" but dropping them also drops valid packets.
They also have in common the "&" and "i" in the third row, I also tried dopping packets containing them but it didn't seem to do anything. I think I'm using string matching wrong :
```

iptables -A INPUT -p udp -m string --algo bm --from 33 --to 33 --string "&" -j secondarystring
iptables -N secondarystring
iptables -A secondarystring -p udp -m string --algo bm --from 38 --to 38 --string "i" -j DROP

```

So, any ideas? Thanks in advance!

---

### Post by Doug S on 2013-10-25
Hi and welcome to Ubuntu forums.

You need to be careful when trying to use string matching in iptables, it is rather CPU intensive. There was a time when one had to compile the kernel to be be able to use it, a sort of barrier to entry.
Anyway, maybe there is another way to do this. Is packet 42 a legitimate packet? If yes, it has a longer length, so maybe length check could be used? How about source ports of the bad guys verses source ports of good guys? It is hard to say for sure with just a 12 packet screenshot and not knowing which of those 12 are good or bad. We (at least I) would need to see probably several thousand raw captured packets to zero in on a good bad guy DROP method, if there is one.

Edit: Hmmm... I think those source IP addresses are forged and packets 43 to 54 are bad guy packets.

---

### Post by hectorenowel on 2013-10-25
The length of the bad packets are different, so maybe 67 is also from a bad guy. The attacks are inactive the morning so I will record good packets and compare them as suggested, I'll also post them here. Thanks!

---

### Post by Doug S on 2013-10-25
Also have a look [here]("http://forums.alliedmods.net/showthread.php?t=151551").

---

