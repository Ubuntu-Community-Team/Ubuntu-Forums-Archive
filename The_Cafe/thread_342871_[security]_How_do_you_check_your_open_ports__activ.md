---
title: "[security] How do you check your open ports / active connections to protect you?"
date: 2007-01-20
forum: The Cafe
---

### Post by burek on 2007-01-20
netstat -plntu 
lsof -i -n -P
host 
nmap -sS -sV 127.0.0.1
wireshark

...
stuffs like that ...
 
Which one can tell you the active connections and lot of details ?](*,)

---

### Post by scrooge_74 on 2007-01-23
just open firestarter and you can see a lot of info on what is open and what connections you have

---

### Post by emarkay on 2007-01-23
What about the online test - "Shields Up"?
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Aetherius on 2007-01-23
```
sudo apt-get install iftop
iftop
```

terminal stats for all active network connections

---

### Post by scrooge_74 on 2007-01-23
> **emarkay said:**
> What about the online test - "Shields Up"?
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

They say I have a very secure windows computer  :lolflag: 

your Internet port 139 does not appear to exist!
One or more ports on this system are operating in FULL STEALTH MODE! Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.
	Unable to connect with NetBIOS to your computer.
All attempts to get any information from your computer have FAILED. (This is very uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be VERY SECURE since it is NOT exposing ANY of its internal NetBIOS networking protocol over the

But since I am not using a windows computer :lolflag:

---

### Post by Aetherius on 2007-01-23
"Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice."

---

### Post by maniacmusician on 2007-01-23
now someone try this with a Windows computer; what does it say if you do that? :)

---

### Post by emarkay on 2007-01-23
I didn't think ports were OS specific ..

[now where's that cynical smirking smiley???]

---

### Post by puppy on 2007-01-23
I was going to recommend Steve Gibson's Shield's Up too :)

I would also recommend Steve Gibson and Leo Laporte's weekly Security Now podcast - available on the [www.twit.tv](www.twit.tv) network - very, very good if you're at all interested in surfing safely etc :)

---

### Post by GStubbs43 on 2007-01-23
> **maniacmusician said:**
> now someone try this with a Windows computer; what does it say if you do that? :)

Mine says (with the "All service ports" test, AND with my (Windows, Comodo, and Router) firewall disabled)

> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.


And with the Common Ports Probe, still with Firewall disabled:

I get the same message with > There is NO EVIDENCE WHATSOEVER that a port (or even any computer) exists at this IP address!
bext to each port.

and for the File Sharing test:

> 	Attempting connection to your computer. . .
Shields UP! is now attempting to contact the Hidden Internet Server within your PC. It is likely that no one has told you that your own personal computer may now be functioning as an Internet Server with neither your knowledge nor your permission. And that it may be serving up all or many of your personal files for reading, writing, modification and even deletion by anyone, anywhere, on the Internet!
	Your Internet port 139 does not appear to exist!
One or more ports on this system are operating in FULL STEALTH MODE! Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.
	Unable to connect with NetBIOS to your computer.
All attempts to get any information from your computer have FAILED. (This is very uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be VERY SECURE since it is NOT exposing ANY of its internal NetBIOS networking protocol over the Internet.

Cool. :D

---

### Post by scrooge_74 on 2007-01-23
I was taking the test again and it says I have the telnet port open, but I am sure is close, I am thinking is my ISP's router which has that port open.  Any comments?

---

### Post by Crashmaxx on 2007-01-23
Is ICMP ping really that bad? I have all my ports stealthed, even though 2442 is forwarded, so I'm suprised it didn't show. I can disable ICMP ping in my router, but why?

---

### Post by Voxxi on 2007-01-24
Ach, I've failed *miserably*.

Solicited TCP Packets: RECEIVED (FAILED) &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active user community.

It looks like port 22 is open. But thats a bit weird, because all port 22 requests from outside my LAN are blocked. 

This is gonna bug me *all night*.

EDIT:

Worked it out, seems my router has a built-in ssh server, plus theres no option to turn it off. 
Anyone know how to turn the ssh server off on a Dlink G604T router?

My gosh, I did an ls, guess what turned up?

bin      dev      etc      lib      proc     sbin     usr      var 

This thing runs Linux! You know what I'm thinking B1? I sure am B2, its **Experimentation time**!

---

### Post by budgie9 on 2007-01-24
Shields-Up is a good site, but are you aware that if you are behind a NAT then it gives incorrect information. 
Has anyone found a working alternative that actually shows the real situation behind a NAT?

---

### Post by BeachBum on 2007-02-01
> **budgie9 said:**
> Shields-Up is a good site, but are you aware that if you are behind a NAT then it gives incorrect information. 
Has anyone found a working alternative that actually shows the real situation behind a NAT?

Either physically wire that computer to the wall, or in your router configuration, put your computer in the DMZ (DeMilitarized Zone), where you're supposed to be "exposed" to the outside world.  

[http://en.wikipedia.org/wiki/Demilitarized_zone_%28computing%29](http://en.wikipedia.org/wiki/Demilitarized_zone_%28computing%29)

---

### Post by shining on 2007-02-01
I have a http server running, and shields up doesn't even detect it. It says the port 80 is in stealth mode.
Running nmap -P0 myip detected the 80 port was open though, so it seems nmap is more reliable in this case. (it also took much more time)
But I believe I always get different results, and they often don't reflect the reality. I'm very confused about this stuff.

---

