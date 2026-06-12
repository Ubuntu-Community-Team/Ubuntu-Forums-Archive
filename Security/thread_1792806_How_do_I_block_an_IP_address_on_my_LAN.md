---
title: "How do I block an IP address on my LAN?"
date: 2011-06-28
forum: Security
---

### Post by Libertydude on 2011-06-28
Hi, I  use Ubuntu and I would like to know how to block a computer's ip address that is on my LAN.

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> Hi, I  use Ubuntu and I would like to know how to block a computer's ip address that is on my LAN.

a little unclear but i presume you mean an IP address of a machine on your lan from accessing your machine ?

the simplest way would be through the firewall and just set up a rule to deny inbound from that IP

if you dont have firewall installed it in the software centre

search for ufw, there are a few but ufw does the job.

there are more ways and alot more complicated but this takes about 1 minute to do.

if it doesnt do the job then come back for more options

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> a little unclear but i presume you mean an IP address of a machine on your lan from accessing your machine ?

the simplest way would be through the firewall and just set up a rule to deny inbound from that IP

if you dont have firewall installed it in the software centre

search for ufw, there are a few but ufw does the job.

there are more ways and alot more complicated but this takes about 1 minute to do.

if it doesnt do the job then come back for more options
Hi, thanks for the reply. What you said above is correct.

I have already installed GUFW, and when I search for "UFW" it says it is already installed.

Where do I go to block the ip?

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> Hi, thanks for the reply. What you said above is correct.

I have already installed GUFW, and when I search for "UFW" it says it is already installed.

Where do I go to block the ip?

it is on system>administration>firewall configuration

click add to add a rule, choose advanced then choose deny from drop down, in, both (for tcp,udp, hhen the ip address  then last part you can put in a port if you like or leave it blank for all

---

### Post by Dangertux on 2011-06-28
> **Libertydude said:**
> Hi, thanks for the reply. What you said above is correct.

I have already installed GUFW, and when I search for "UFW" it says it is already installed.

Where do I go to block the ip?

The quickest way would be in a terminal

sudo ufw deny from 192.168.0.5 to 192.168.0.6

where .5 is the ip address you want to block it from and .6 is your ip address.

---

### Post by haqking on 2011-06-28
> **Dangertux said:**
> The quickest way would be in a terminal

sudo ufw deny from 192.168.0.5 to 192.168.0.6

where .5 is the ip address you want to block it from and .6 is your ip address.

yeah this too, but i was keeping him in GUI seeing as he seemed new to it ;-)

but yeah CLI is the way to go

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> yeah this too, but i was keeping him in GUI seeing as he seemed new to it ;-)

but yeah CLI is the way to go
How do I find it's ip address? (It uses windows 7).

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> How do I find it's ip address? (It uses windows 7).

if you have access to the machine then on it go to command prompt and type ipconfig

or you know its name then ping the  name from your linux machine and it will resolved if your lan offers those services

do you have access to the machine ?

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> if you have access to the machine then on it go to command prompt and type ipconfig

or you know its name then ping the  name from your linux machine and it will resolved if your lan offers those services

do you have access to the machine ?
Not know, but I will in a couple hours. :)

Thanks for your help, if I have any problems I will post back. :D

---

### Post by Libertydude on 2011-06-28
Okay, I just ran ipconfig on the other laptop and under ipv4 it said it's ip address was 10.0.0.2. Is this the right one to block?

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> Okay, I just ran ipconfig on the other laptop and under ipv4 it said it's ip address was 10.0.0.2. Is this the right one to block?


well yeah sounds like it, it is a private class A address.

most people tend to run class c on the home networks.

is it your lan ? and do you have rights and permissions to be blocking IP addresses ?

---

### Post by slooksterpsv on 2011-06-28
> **Libertydude said:**
> Okay, I just ran ipconfig on the other laptop and under ipv4 it said it's ip address was 10.0.0.2. Is this the right one to block?

That would be it. That is a local IP though so yeah it should be, unless there's another IPv4 address that your network is giving.

---

### Post by d3v1150m471c on 2011-06-28
arp is your friend
```

arp -a

```

additionally you can use `host' to pull a hostname from the ip's found:
```

host 192.168.xxx.xxx

```

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> well yeah sounds like it, it is a private class A address.

most people tend to run class c on the home networks.

is it your lan ? and do you have rights and permissions to be blocking IP addresses ?
Yeah, it's my router. And I am under the impression that blocking the ip address will only prevent it from having access to my computer. Is this correct? I don't want it being blocked from the internet.

---

### Post by d3v1150m471c on 2011-06-28
> **Libertydude said:**
> Yeah, it's my router. And I am under the impression that blocking the ip address will only prevent it from having access to my computer. Is this correct? I don't want it being blocked from the internet.

see above ^^^. blocking it from gufw/ufw will block it from your pc, not internet. if you need to block internet you'd need mac filtering or some clever hackery

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> Yeah, it's my router. And I am under the impression that blocking the ip address will only prevent it from having access to my computer. Is this correct? I don't want it being blocked from the internet.

yeah which is what i assumed hence i steered you towards the GUFW route.

So if you have blocked that IP that will stop it from accessing your machine.

However remember this might cause issued depending on the lan and how it works.

As it is your router i am guessing it is not too much of an issue.

---

### Post by Libertydude on 2011-06-28
So if I type:

> sudo ufw deny from 10.0.0.2

That will only block it from my computer? (That is all I want).

---

### Post by haqking on 2011-06-28
> **haqking said:**
> it is on system>administration>firewall configuration

click add to add a rule, choose advanced then choose deny from drop down, in, both (for tcp,udp, hhen the ip address  then last part you can put in a port if you like or leave it blank for all

> **Dangertux said:**
> The quickest way would be in a terminal

sudo ufw deny from 192.168.0.5 to 192.168.0.6

where .5 is the ip address you want to block it from and .6 is your ip address.

as already mentioned earlier on ;-)

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> as already mentioned earlier on ;-)
Ah, okay thanks. :D

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> Ah, okay thanks. :D

once you have set the deny, you can go to offending or whatever machine ;-) and try to ping the ip address of yours, the ping should be returned with no response where as before you should get a response, play around a little until you it works. ;-) dont play too much though unless you know what you are doing ;-)

---

### Post by Libertydude on 2011-06-28
I have one other question, what if it changes it's ip address? Could it access my computer now?

---

### Post by haqking on 2011-06-28
> **Libertydude said:**
> I have one other question, what if it changes it's ip address? Could it access my computer now?


think about it ?

you are blocking a certain IP address, so if it changes then yes of course.

you could block the mac address with iptables

iptables -A INPUT -m mac --mac-source aa:bb:cc:dd:ee:ff -j DROP

where the aa: etc is the mac address of the offender.

you can use man iptables from terminal to find other options

i would encourage the use of the man pages on everything ;-)

---

### Post by Libertydude on 2011-06-28
> **haqking said:**
> think about it ?

you are blocking a certain IP address, so if it changes then yes of course.

you could block the mac address with iptables

iptables -A INPUT -m mac --mac-source aa:bb:cc:dd:ee:ff -j DROP

where the aa: etc is the mac address of the offender.

you can use man iptables from terminal to find other options

i would encourage the use of the man pages on everything ;-)
Ah, okay. Thanks for the info. :D

---

