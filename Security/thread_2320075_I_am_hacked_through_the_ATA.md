---
title: "I am hacked through the ATA"
date: 2016-04-10
forum: Security
---

### Post by leclerc65 on 2016-04-10
This is my sad story:
Somebody (must use a computer, I guess) poll my ATA every 3-5 minutes, They use IP from all over the world, but mostly from France and Germany.
Whenever I log in they launch the attack right away. I have several computers, but strangely they know exactly what is my main one and pwn it. Passwords, firewall (both UFW & Firewalld) are completely
useless.
In desperation I even run several combinations of virtualbox host/guest like Ubuntu/Windows 7, Mint/Windows 7, Mint/Open Suse ...
If the cannot access the guest they destroy files on the host.

I think of getting a separate line for my phone, but that involve extra expense for me.

Please help.

---

### Post by coldraven on 2016-04-10
> Somebody (must use a computer, I guess) poll my ATA
What is ATA?

---

### Post by leclerc65 on 2016-04-10
My Cisco SPA112 phone adapter.

---

### Post by QIII on 2016-04-10
Can you describe, in greater depth, the exact details of what you believe to be an attack?

---

### Post by leclerc65 on 2016-04-11
Phone sometimes rings but no people on the other side. Sometimes I cannot call , or I call and hear people talk but they cannot hear my reply.
The phone come back normal one minute or two later.
Here is a sample of my router log (xx.x.x.m = my SPA112, xx.x.x.n = my computer). It's too loong so I post only a portion. The hacking goes 24h except the periods when I turn off the SPA112.
```

[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 15:09:07
[LAN access from remote] from 76.10.133.4:27438 to xx.x.x.m:16410 Sunday, Apr 10,2016 15:05:49
[LAN access from remote] from 76.10.133.4:27884 to xx.x.x.m:16408 Sunday, Apr 10,2016 15:05:09
[LAN access from remote] from 61.182.170.38:36786 to xx.x.x.n:22 Sunday, Apr 10,2016 15:03:56
[LAN access from remote] from 199.217.115.71:5096 to xx.x.x.m:5060 Sunday, Apr 10,2016 15:02:52
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:59:48
[LAN access from remote] from 89.163.242.82:5080 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:56:43
[LAN access from remote] from 76.10.133.4:27530 to xx.x.x.m:16404 Sunday, Apr 10,2016 14:56:32
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:55:20
[LAN access from remote] from 124.195.211.218:57605 to xx.x.x.n:23 Sunday, Apr 10,2016 14:53:15
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:47:00
[LAN access from remote] from 188.138.75.160:5126 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:44:34
[LAN access from remote] from 76.10.133.4:27686 to xx.x.x.m:16394 Sunday, Apr 10,2016 14:40:12
[LAN access from remote] from 76.10.133.4:27742 to xx.x.x.m:16392 Sunday, Apr 10,2016 14:38:26
[LAN access from remote] from 76.10.133.4:27960 to xx.x.x.m:16390 Sunday, Apr 10,2016 14:36:46
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:36:37
[LAN access from remote] from 76.10.133.4:27980 to xx.x.x.m:16388 Sunday, Apr 10,2016 14:34:34
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:27:04
[LAN access from remote] from 89.163.242.82:5072 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:22:47
[LAN access from remote] from 200.87.123.4:35715 to xx.x.x.n:23 Sunday, Apr 10,2016 14:21:32
[LAN access from remote] from 76.10.133.4:24650 to xx.x.x.m:16384 Sunday, Apr 10,2016 14:19:35
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:18:11
[LAN access from remote] from 76.10.133.4:24170 to xx.x.x.m:16480 Sunday, Apr 10,2016 14:18:11
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:16:31
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:14:22
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:09:39
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:08:47
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:07:04
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:05:19
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:03:06
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 14:01:46
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:57:46
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:56:26
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:56:00
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:55:34
[LAN access from remote] from 89.163.242.82:5081 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:55:07
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:51:10
[LAN access from remote] from 89.163.242.82:5076 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:50:44
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:50:18
[LAN access from remote] from 52.37.236.94:61856 to xx.x.x.n:22 Sunday, Apr 10,2016 13:49:06
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:46:19
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:44:59
[LAN access from remote] from 189.218.115.179:3211 to xx.x.x.n:23 Sunday, Apr 10,2016 13:42:40
[LAN access from remote] from 185.130.5.86:36451 to xx.x.x.n:22 Sunday, Apr 10,2016 13:41:22
[LAN access from remote] from 89.163.242.82:5074 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:40:05
[LAN access from remote] from 81.163.35.21:36088 to xx.x.x.n:23 Sunday, Apr 10,2016 13:39:59
[LAN access from remote] from 89.163.242.82:5070 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:39:38
[LAN access from remote] from 89.163.242.82:5071 to xx.x.x.m:5060 Sunday, Apr 10,2016 13:39:11

```

---

### Post by ian-weisser on 2016-04-11
If your Ubuntu system has really been compromised, take it offline immediately and reinstall.
Restore your data from your backups (you do backups, of course?). Do not reuse old keys nor old passwords. Change all your online passwords, etc.
Prevent future intrusions by using keys instead of passwords, and being careful with your internet-facing services.

One assumes your SPA-112 connects directly to the router, and is relevant only for broadcasting your IP upon connection. Report the abuse to your VOIP provider - they need to know that somebody is misusing their service. Consider changing VOIP providers.

One assumes your router's firewall is turned on and properly configured. If not, then do so.

---

### Post by leclerc65 on 2016-04-11
My ISP technician refused to help. He said the log(s) look normal.
Maybe I have to use a cell phone. I regret to loose our home phone number that we have owned for years.
I am replying you, Ian, with my old PC that is protected by Iptables to the max of my knowledge. The router and the pwned
PC just don't stand a chance.

---

### Post by CharlesA on 2016-04-12
So you are using this ATA device as a router? I've never exposed this type of hardware directly to the Internet.

You should have an actual router/gateway and connect everything to it.

Main router
      v
Main PC, ATA device, other PC

---

### Post by leclerc65 on 2016-04-12
No.
It's hooked up to the router as you show.
They dial my phone number every few minutes, the phone does not ring, somehow they know right away when a device is online. This laptop is on all the time, and well protected, but other devices (printer, iPad, smart phone are
defenceless) are at their mercy. They use this modus operandi to hack all computers and devices in my house, which  I don't care, except my main desktop.

The strange thing is as soon as I turn it on they get control of the thing with ROOT privilege. No matter how many times I reinstall, install other distros they still hack thru. It seems that Puppy or OpenSuse are more sustainable, but I don't like Puppy, and I am not at ease with OpenSuse. The iptables is setup the same as the laptop.
Does it help if I replace the NIC card ?

It's going on for two years now. I changed ISP the first year and they keep following me up to now. I drop using the
phone number which I own for so many year.

---

### Post by sammiev on 2016-04-12
Likely wrong, but it sounds like they are on your computer dialing out.

Then again a fresh install would kill that which it hasn't unless you are adding the malware or hack into the OS yourself.

---

### Post by The Cog on 2016-04-12
> The strange thing is as soon as I turn it on they get control of the thing with ROOT privilege.
What evidence do you base this on? What happens?

The reason I ask is that a new Ubuntu install should be impervious to hacking from outside as there are no listening TCP ports and only one or two listening UDP ports. I wonder if something else might be happening.

The log you posted looks like a combination of occasional normal hacking attempts, to port 22 (SSH) and 23(telnet) for instance, and  lot of attempts to connect to ports 5060 and and 16384 which are SIP and RTP used for voice calls. Unless you enable SSH on your Ubuntu without access restrictions, it should not be susceptible to anything in that log.

---

### Post by leclerc65 on 2016-04-12
Just a guess.
Once I issue a command (as root)
```

iptables-save > /root/working.iptables.rules

```
and the PC is on a loop , waiting forever, it's an i7 3770.
They deleted (randomly) my files at will.
More other weird pheomena but I cannot remember them all. 
I take it offline now.

---

