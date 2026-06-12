---
title: "Do I need to run firestarter always??"
date: 2010-02-26
forum: Security
---

### Post by x64banana on 2010-02-26
Hello I am new to the new world :D so forgive me if this post is in the wrong place.

I installed ubuntu a few weeks ago and ever since I've been reading all kinds of articles and different websites about security in linux. 

I just want to have a simple firewall to keep me stealth in internet ( like ZoneAlarm by keeping all ports stealth so that i can pass something like the ShieldsUp test )

I installed FireStarter, enabled ICMP filtering (whatever ICMP is :D I just know I should not respond to anything to remain stealth ) and the rest of the settings are default.

By doing so I actually did pass the ShieldsUp test ( with the fresh install of ubuntu 910 it was failing  with all the ports being closed, rather than stealth )

Now the question is, do I have to run FireStarter in the background everytime?? cause the software had no option for minimizing it to somewhere.

---

### Post by FuturePilot on 2010-02-26
No. Firestarter is just a GUI to Iptables. It doesn't need to be running to be protected.

---

### Post by cdenley on 2010-02-26
First of all, firestarter is no longer maintained, and I suggest you don't use it at all. Secondly, the GUI interface actually requires root privileges, if I recall correctly, which means you should have it running as little as possible since there is almost certainly some unpatched vulnerability in an old application like that, and if it gets compromised, the attacker has root access to your system. Lastly, there are no real benefits to having your ports "stealthed" rather than "closed". The only difference is when it is closed, your system rejects connection attempts rather than ignoring them. As long as there is no listening process on your system to accept connection attempts, it doesn't really matter.

---

### Post by mkvnmtr on 2010-02-26
Read the stickys at the top of this page. They contain the absolute best advise aon Ubuntu security you can find. Firestarter is not recomended.

---

### Post by bodhi.zazen on 2010-02-26
> **x64banana said:**
> Hello I am new to the new world :D so forgive me if this post is in the wrong place.

I installed ubuntu a few weeks ago and ever since I've been reading all kinds of articles and different websites about security in linux. 

I just want to have a simple firewall to keep me stealth in internet ( like ZoneAlarm by keeping all ports stealth so that i can pass something like the ShieldsUp test )

I installed FireStarter, enabled ICMP filtering (whatever ICMP is :D I just know I should not respond to anything to remain stealth ) and the rest of the settings are default.

By doing so I actually did pass the ShieldsUp test ( with the fresh install of ubuntu 910 it was failing  with all the ports being closed, rather than stealth )

Now the question is, do I have to run FireStarter in the background everytime?? cause the software had no option for minimizing it to somewhere.

I also advise you do at least a little background reading on IPTables.

At least the first 3 sections here : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The concept of a "Stealth" port is not a good one.

It is the difference between DROP and REJECT in iptables.

Both options are, IMO, equally secure.

If you are using a router you can almost certainly use Ubuntu without enabling your firewall.

There is nothing wrong with using firestarter, so long as it works. 

By default, however, Ubuntu now uses ufw and the graphical front end is gufw:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

So a potential problem is a conflict between ufw and/or gufw and firestarter (they aere both trying to configure iptables at the same time).

So , I advise you remove firestarter

```
sudo apt-get purge firestarter
```And if you must enable your firewall with 

```
sudo ufw enable
```The default settings of ufw are rock solid regardless of what "ShieldsUP" may tell you and 99.99 % of Desktop users are just fine with the default settings.

Monitoring is more complex. Although it may be "cool" to have a graphical application flash when a packet is rejected, the reality is that if you are interested you can test your firewall yourself, without shields up (also note that Shields up scans your router, not your Ubuntu box). For details on how to do this, see the  first link I gave you.

In addition my firewall rejects thousands of packets without any kind of visual flash.

Linux is not Windows, relax and enjoy :

[Ubuntu Forums - View Single Post - General Security ?]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236")

---

### Post by x64banana on 2010-03-01
> **bodhi.zazen said:**
> I also advise you do at least a little background reading on IPTables.

At least the first 3 sections here : [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The concept of a "Stealth" port is not a good one.

It is the difference between DROP and REJECT in iptables.

Both options are, IMO, equally secure.

If you are using a router you can almost certainly use Ubuntu without enabling your firewall.

There is nothing wrong with using firestarter, so long as it works. 

By default, however, Ubuntu now uses ufw and the graphical front end is gufw:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

So a potential problem is a conflict between ufw and/or gufw and firestarter (they aere both trying to configure iptables at the same time).

So , I advise you remove firestarter

```
sudo apt-get purge firestarter
```And if you must enable your firewall with 

```
sudo ufw enable
```The default settings of ufw are rock solid regardless of what "ShieldsUP" may tell you and 99.99 % of Desktop users are just fine with the default settings.

Monitoring is more complex. Although it may be "cool" to have a graphical application flash when a packet is rejected, the reality is that if you are interested you can test your firewall yourself, without shields up (also note that Shields up scans your router, not your Ubuntu box). For details on how to do this, see the  first link I gave you.

In addition my firewall rejects thousands of packets without any kind of visual flash.

Linux is not Windows, relax and enjoy :

[Ubuntu Forums - View Single Post - General Security ?]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236")


Thanks for the reply and the tutorials. I am gonna have to do a whole  lot of reading and research on networking.

I dont want to argue, but I'd like to take the "Stealth vs Closed"  debate a bit further just for learning.


> 
 The concept of a "Stealth" port is not a good one.

 can u plz explain why it is not good -- 

I only have a very high-level understanding of it so I may be wrong, but  if i am stealth on the internet shouldn't the fact that person x can't  really confirm whether I exist or not provide a bit more security  WHEREAS if they know, for instance ip 70.70.70.70 is online and has all  ports closed, they may be able to take time and watch me ( for example  intercept outgoing packets if possible and collect more info ) which may  or may not put us in some risk.

But i dont think there is any need for us to return an error message..
I mean if we drop all the packets and not return any error, does it  cause any tradeoff for us ??

---

### Post by x64banana on 2010-03-01
BTW is there any difference between 

sudo apt-get purge firestarter

and uninstalling it through the software center, i mean does it differ in terms of leaveing  any settings or other files or do they do the exact same job??


 thanks

---

### Post by bodhi.zazen on 2010-03-01
> **x64banana said:**
> can u plz explain why it is not good -- 

I only have a very high-level understanding of it so I may be wrong, but  if i am stealth on the internet shouldn't the fact that person x can't  really confirm whether I exist or not provide a bit more security  WHEREAS if they know, for instance ip 70.70.70.70 is online and has all  ports closed, they may be able to take time and watch me ( for example  intercept outgoing packets if possible and collect more info ) which may  or may not put us in some risk.

But i dont think there is any need for us to return an error message..
I mean if we drop all the packets and not return any error, does it  cause any tradeoff for us ??

IMO it is not good because it does not explain the difference between DROP and REJECT. There is not such thing as a Stealth port, IMO one should use proper terminology. Improper terms cause confusion.

It sounds as if you understand proper terminology, so that is good.

IMO DROP and REJECT are equally secure, they both deny access to a port.

It depends on if you feel security through obscurity add much, IMO it does not.

To use your example, how would someone "watch" you ? They would need a packet sniffer. If such a packet sniffer is available, neither DROP or REJECT add much as they are watching your traffic either way.

Your presence on the internet is not, IMO, obscured because you use DROP over REJECT, but so long as you understand the terminology, there is nothing wrong with your preference. My point is one of semantics, "Stealth" is not, IMO a good term. IMO, better to use and explain REJECT (vs DROP).

---

### Post by d3v1150m471c on 2010-03-01
> **cdenley said:**
> First of all, firestarter is no longer maintained, and I suggest you don't use it at all. Secondly, the GUI interface actually requires root privileges, if I recall correctly, which means you should have it running as little as possible since there is almost certainly some unpatched vulnerability in an old application like that, and if it gets compromised, the attacker has root access to your system. Lastly, there are no real benefits to having your ports "stealthed" rather than "closed". The only difference is when it is closed, your system rejects connection attempts rather than ignoring them. As long as there is no listening process on your system to accept connection attempts, it doesn't really matter.

I disagree. I run firestarter (no, I don't leave the GUI open) but it still serves well to adjust IP tables, which is all it's supposed to do. Thus saying it's vulnerable because it's no longer supported is saying you're more vulnerable because you don't adjust your firewall setting in the terminal. Leave the gui closed when not making alterations or adding rules. Second, stealthing your ports is in fact better than the traditional closing of ports because it makes you invisible on the internet to ip trollers, probers, and scans.

---

### Post by cariboo on 2010-03-01
I use the default rules on my netbook, they say nothing about stealthing anything,, but running nmap -PN 192.168.1.101 on my internal network, nmap gives up after 300 seconds saying it can't find anything of interest. I think that is a glowing result for the default iptables rules.

---

### Post by uRock on 2010-03-01
I have completed port scans against Ubuntu machines with UFW enabled and 0 ports were found to be open and nmap could not identify the OS. See those results [here]("http://ubuntuforums.org/showthread.php?t=1408074").

WHen behind a router on your own network a firewall is not really needed, but if you are sharing a network especially wireless, you should run UFW.

---

