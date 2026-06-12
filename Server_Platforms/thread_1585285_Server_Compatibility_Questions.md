---
title: "Server Compatibility Questions"
date: 2010-09-30
forum: Server Platforms
---

### Post by ts230 on 2010-09-30
So, I have a friend that owns [this server]("http://www.supermicro.com/products/system/2U/6023/SYS-6023P-i.cfm"), and is willing to sell it to me. What parts of it are not compatible with Ubuntu, and what does work? And, most importantly, will it make a good server? I really would like all the sensors to be readable by Ubuntu, so I can monitor the server's temps from home, as this is gonna go into a data center.

Thanks for any help!

---

### Post by lukeiamyourfather on 2010-09-30
Everything should work fine on it in Linux (network, graphics, etc.) though temperature monitoring is not something I've done in Linux before. Monitoring the temperature is likely possible but you'll have to do some research on that one. Hopefully you're getting a good deal on it!

---

### Post by lukeiamyourfather on 2010-09-30
> **ts230 said:**
> And, most importantly, will it make a good server?

I forgot to answer that part. It depends. What processors are in the machine? Are both processor sockets filled or just one? How much memory is installed? How big are the hard disks? What do you plan to do with the server?

---

### Post by ts230 on 2010-09-30
> **lukeiamyourfather said:**
> I forgot to answer that part. It depends. What processors are in the machine? Are both processor sockets filled or just one? How much memory is installed? How big are the hard disks? What do you plan to do with the server?

There's two Intel Xenon clocked at 3.0 GHz, 16 GB of RAM, and there's 4 250 GB drives, but I will be buying myself a SATA 2TB one as soon as I get some money. I plan to do some shared web hosting on there, and host my own site.

---

### Post by Nizumzen on 2010-09-30
> **ts230 said:**
> There's two Intel Xenon clocked at 3.0 GHz, 16 GB of RAM, and there's 4 250 GB drives, but I will be buying myself a SATA 2TB one as soon as I get some money. I plan to do some shared web hosting on there, and host my own site.

Xeon not Xenon :).

It depends what generation of Intel Xeon it is as to whether it is a good server or not.

---

### Post by ts230 on 2010-09-30
> **Nizumzen said:**
> Xeon not Xenon :).

It depends what generation of Intel Xeon it is as to whether it is a good server or not.

And that's what happens when you are half asleep! All I know is that that server has been upgraded in late 2008 and that both CPU's run at 3.05 GHz. I'm getting it tomorrow anyways, so then I can throw on Ubuntu and see how it reacts.

---

### Post by Vegan on 2010-09-30
If the machine your procuring has been in service a while. It might be an idea to clean the CPU HSF and re-grease it so that it remains serviceable for a long time to come.

When I moved my CPU from my old MB to the one I have now, I cleaned my CPU and HSF and used new grease, and it runs cool as a cucumber.

---

### Post by CharlesA on 2010-09-30
Should work fine.

+1 to cleaning out the HSF and reapplying thermal grease.

---

### Post by ts230 on 2010-10-01
> **Vegan said:**
> If the machine your procuring has been in service a while. It might be an idea to clean the CPU HSF and re-grease it so that it remains serviceable for a long time to come.

When I moved my CPU from my old MB to the one I have now, I cleaned my CPU and HSF and used new grease, and it runs cool as a cucumber.

It has mostly been in service for about 1 year, and then just been sitting for 2 years, but being powered on occasionally. I might just visit my local Fry's and get some new thermal paste for the CPU.

I will be sure to clean all 8 fans in that beast and re-apply the thermal paste. What's a good amount for these kinds of servers? I don't want to put it on too thick or else I read it might be less effective. I'm going to apply a short film of it, not too thick, but just thick enough that you can barely see the bare CPU top, but not completely covered. Feel free to suggest alternate amounts :)

---

### Post by trundlenut on 2010-10-01
> **ts230 said:**
> There's two Intel Xenon clocked at 3.0 GHz, 16 GB of RAM, and there's 4 250 GB drives, but I will be buying myself a SATA 2TB one as soon as I get some money. I plan to do some shared web hosting on there, and host my own site.

By the looks of that spec it won't accept a SATA drive, only PATA.

---

### Post by CharlesA on 2010-10-01
> **trundlenut said:**
> By the looks of that spec it won't accept a SATA drive, only PATA.

Yep. That could be a bit of a headache if you want to find drives for it.

---

### Post by ts230 on 2010-10-01
> **CharlesA said:**
> Yep. That could be a bit of a headache if you want to find drives for it.

I actually noticed that the day after the hard drive was ordered >_>
Anyone know of any good PCI SATA cards with Ubuntu support?

---

### Post by lukeiamyourfather on 2010-10-01
> **ts230 said:**
> I actually noticed that the day after the hard drive was ordered >_>
Anyone know of any good PCI SATA cards with Ubuntu support?

That probably won't help. All the Super Micro servers I've worked with have the connectors at the back of a bay for the drive. In order to use a SATA drive you'd need an external disk of some sort (rack mount array typically), or a drive bay adapter for the single 5.25" bay but that would support only one drive.

---

### Post by ts230 on 2010-10-01
> **lukeiamyourfather said:**
> That probably won't help. All the Super Micro servers I've worked with have the connectors at the back of a bay for the drive. In order to use a SATA drive you'd need an external disk of some sort (rack mount array typically), or a drive bay adapter for the single 5.25" bay but that would support only one drive.

Hmm, I might be able to throw out the CD drive once I'm done installing everything, and then put in that adapter that I still have from a long, long time ago. I gotta head off to school, but I'll let you know how it goes when I get it.

---

### Post by ts230 on 2010-10-01
OK, so I got the server and it runs awesomely on there. The only issue I have is that all fans always run at full blast, and I would like to run them temperature regulated. It can read all the RPMs and temps fine as well, but I have just no idea how do to throttling of the fans.

---

### Post by lukeiamyourfather on 2010-10-02
> **ts230 said:**
> OK, so I got the server and it runs awesomely on there. The only issue I have is that all fans always run at full blast, and I would like to run them temperature regulated. It can read all the RPMs and temps fine as well, but I have just no idea how do to throttling of the fans.

That depends on if the motherboard has PWM fan controllers or not. Only very recent servers have this feature. My guess is that one probably doesn't. Glad everything is up and working!

---

### Post by ts230 on 2010-10-02
> **lukeiamyourfather said:**
> That depends on if the motherboard has PWM fan controllers or not. Only very recent servers have this feature. My guess is that one probably doesn't. Glad everything is up and working!

Would there be some way to check for such? It can get the Fan RPMs nice and good, which I like, just with the voltages and temps as well. Is there some kind of script that'll graph these over time?

I had to wrestle with Apache and PHP once more, stupid userdirs, but then eventually figured it out.

---

### Post by lukeiamyourfather on 2010-10-02
> **ts230 said:**
> 
Would there be some way to check for such?


Look in the BIOS, typically there will be something like thermal profile or quiet mode. If you don't find anything then it doesn't have PWM fan controllers.

> **ts230 said:**
> 
It can get the Fan RPMs nice and good, which I like, just with the voltages and temps as well. Is there some kind of script that'll graph these over time?


Search the repositories for something, or search the net. I'm sure there's something but I don't know of one off the top of my head.

Honestly, why do you care so much about the status of everything? If it breaks, you'll know. There's no point in logging every little thing especially when the server is in a remote data center that you can't do anything about. You should be more concerned with securing the install and services. I'd guess you're far more likely to get hacked than have a fan go out in a server.

---

### Post by ts230 on 2010-10-02
> **lukeiamyourfather said:**
> Look in the BIOS, typically there will be something like thermal profile or quiet mode. If you don't find anything then it doesn't have PWM fan controllers.



Search the repositories for something, or search the net. I'm sure there's something but I don't know of one off the top of my head.

Honestly, why do you care so much about the status of everything? If it breaks, you'll know. There's no point in logging every little thing especially when the server is in a remote data center that you can't do anything about. You should be more concerned with securing the install and services. I'd guess you're far more likely to get hacked than have a fan go out in a server.

You got a point there - what I mean by that was that it'd be nice to have a graph of disk usage and possibly network traffic,and load averages. I'm interested in tracking how this thing works over time. 

I've also heard from a friend that I should change the SSH port to a non-standard port, such as 9952, and change it twice a year to prevent SSH attacks. Any other ideas to make my system more secure?

---

### Post by CharlesA on 2010-10-02
> **ts230 said:**
> You got a point there - what I mean by that was that it'd be nice to have a graph of disk usage and possibly network traffic,and load averages. I'm interested in tracking how this thing works over time. 

I think [landscape]("https://landscape.canonical.com/") can do that, but you'd have to pay for it.

> I've also heard from a friend that I should change the SSH port to a non-standard port, such as 9952, and change it twice a year to prevent SSH attacks. Any other ideas to make my system more secure?

As long as you use key auth, you don't really need to move the ssh port to a non-standard one. If someone really wants to get in, they'll just do a port scan and find which port ssh is running on.

---

### Post by ts230 on 2010-10-02
> **CharlesA said:**
> I think [landscape]("https://landscape.canonical.com/") can do that, but you'd have to pay for it.



As long as you use key auth, you don't really need to move the ssh port to a non-standard one. If someone really wants to get in, they'll just do a port scan and find which port ssh is running on.

Key auth... what's that? I've never heard of it.

---

### Post by CharlesA on 2010-10-02
> **ts230 said:**
> Key auth... what's that? I've never heard of it.

Using public and private keys for auth instead of passwords.

See [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

---

### Post by lukeiamyourfather on 2010-10-03
> **ts230 said:**
> You got a point there - what I mean by that was that it'd be nice to have a graph of disk usage and possibly network traffic,and load averages. I'm interested in tracking how this thing works over time. 


Check out RRDtool and Cacti. RRDtool is used for graphing things over time like disk usage and bandwidth, though you'd have to create what you want from scratch. Cacti uses RRDtool to record things and provide a web interface. Primarily SNMP is used to record information for Cacti.

> **ts230 said:**
> 
I've also heard from a friend that I should change the SSH port to a non-standard port, such as 9952, and change it twice a year to prevent SSH attacks. Any other ideas to make my system more secure?

That's one way to go about it. Though running a security audit and keeping things up to date is probably a better idea. Security audits will run automated tests on common vulnerabilities and let you know how to fix them. Some are free and some are commercial depending on how serious you want to get with it.

---

### Post by ts230 on 2010-10-03
> **lukeiamyourfather said:**
> Check out RRDtool and Cacti. RRDtool is used for graphing things over time like disk usage and bandwidth, though you'd have to create what you want from scratch. Cacti uses RRDtool to record things and provide a web interface. Primarily SNMP is used to record information for Cacti.



That's one way to go about it. Though running a security audit and keeping things up to date is probably a better idea. Security audits will run automated tests on common vulnerabilities and let you know how to fix them. Some are free and some are commercial depending on how serious you want to get with it.

Thanks for all the advice so far. I ran top for a while, and saw cpuset. Doesn't that have something to do with CPU stepping? I really don't need that in a server.

---

### Post by ts230 on 2010-10-03
> **ts230 said:**
> Thanks for all the advice so far. I ran top for a while, and saw cpuset. Doesn't that have something to do with CPU stepping? I really don't need that in a server.


[s]Also, I have installed Cacti and set it up just how I like, but it just displays a broken image for  Interface - Traffic (bits/sec, 95th Percentile) and Host MIB - CPU Utilization.

Also, it seemed to have stopped gathering data after a reboot.[/s]

I have used a webmin module for the above now, but a 95th percentile filter would be nice.

---

### Post by ts230 on 2010-10-03
.

---

### Post by ts230 on 2010-10-05
Today I emailed the support guy about the case intruder switch, as I plan to put the server into a complete lockdown when it's opened. After all, I'll be selling web hosting on there. He emailed me this info:
```
Bus Type = SMBus
One WindBond W83627HF, and one ADM1027 Please refer to W83627HF and ADM1027 documents.

Windbond W83627 HF, Slave Address=0x2d (0x5A in 8-Bit format)
=============================================================
CPU1 Chassis Fan Speed, Offset 0x28
CPU2 Chassis Fan Speed, Offset 0x29
+12V Voltage, Offset 0x24
+5V Voltage, Offset 0x23
+3.3V Voltage, Offset 0x22
3.3SBV Voltage, Offset 0x21
VCCP Voltage, Offset 0x20
-12V Voltage, Offset 0x25
-5V Voltage, Offset 0x26
Chassis Intrusion, Offset 0x42
System Temperature, Offset 0x27

ADM1027, Slave Address=0x2e (0x5C in 8-Bit format)
=============================================================
Chassis Fan 1 Speed, Offset 0x28
Chassis Fan 2 Speed, Offset 0x2a
Chassis Fan 3 Speed, Offset 0x2c
Chassis Fan 4 Speed, Offset 0x2e


1st CPU, Salve Address=0x18 (0x30 in 8-Bit format)
=============================================================
CPU1 Temperature, Offset 0x01

2nd CPU, Salve Address=0x1a (0x34 in 8-Bit format)
=============================================================
CPU2 Temperature, Offset 0x01

Power Supply Failure, GP12(From W83627HF)
```

lm-sensors seems to read most of them all, but I need a way to somehow add the Case Intruder Switch entry so it can be recognized, same with the CPU temps.

What would be the best way to add a sensor to a specific chip, in means of editing config files?

EDIT: Before I forget forever, what would be the best way to provide virtual servers to people? I plan to get a RAM upgrade sometime soon, and will then likely offer virtual servers that are capped around 128 -350 MB of RAM, depending on the price. I really wanna make use of all this xeon-ny power that this server has, and I figured this might be the best way to do it, and some people might want root access, so yes, I'd much rather have the VMs break down that my entire system.

---

