---
title: "Ship hardy with firestarter"
date: 2007-12-20
forum: Ubuntu Brainstorm
---

### Post by zenkaon on 2007-12-20
Hello everyone, merry Christmas,

I think that firestarter should be installed as defualt on hardy.

I doesn't take up much space on the CD and has a great GUI, a firewall that even n00bs can understand.

I understand that some people think that linux is very secure and that it doesn't need a firewall. I'm not so sure about this, people from all around the world are activly trying to hack into Linux systems.

The other day I came back to my pc and someone from Nottingham was asking permission to share my desktop (No prizes for guessing which button I pressed). I installed firestarter and after a day of running the log said that I had had 25 ssh attacks, 18 of which were from china! 

My ISP is virgin media. Other ISPs will be better, others will be worse. I think that most people would agree that ssh attacks, desktop sharing requests and all the windows botnot rubbish is only going to increase, not decrease.

My request for hardy is that firestarter should be installed as default and that the user should set it up on the install, or on first boot. 

Whats your Opinion?

---

### Post by PriceChild on 2007-12-20
Ubuntu ships with no open ports by default... so what is there to firewall against?

If you are then going to install servers which open and listen on ports then you should know what you're doing.

---

### Post by sq377 on 2007-12-21
Plus, have you ever tried firestarter with multiple interfaces?  It woks decently on a desktop, but try using it on a laptop where you frequently change from wireless to wired.  Maybe I was doing something wrong but I had to reconfigure it every time I wanted to switch from eth1 to eth0.  Also like Pricechild said, no open ports by default so it really isn't that necessary.

---

### Post by 23meg on 2007-12-21
If Ubuntu ever ships with a firewall, it's almost certainly going to be this way:

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-firewall](https://blueprints.launchpad.net/ubuntu/+spec/ubuntu-firewall)

---

### Post by harold4 on 2007-12-21
I skimmed the link, so I may be off base here, but the blueprint sounds like what the firehol project is doing.

---

### Post by tech9 on 2007-12-21
> **zenkaon said:**
> Hello everyone, merry Christmas,

I think that firestarter should be installed as defualt on hardy.

I doesn't take up much space on the CD and has a great GUI, a firewall that even n00bs can understand.

I understand that some people think that linux is very secure and that it doesn't need a firewall. I'm not so sure about this, people from all around the world are activly trying to hack into Linux systems.

The other day I came back to my pc and someone from Nottingham was asking permission to share my desktop (No prizes for guessing which button I pressed). I installed firestarter and after a day of running the log said that I had had 25 ssh attacks, 18 of which were from china! 

My ISP is virgin media. Other ISPs will be better, others will be worse. I think that most people would agree that ssh attacks, desktop sharing requests and all the windows botnot rubbish is only going to increase, not decrease.

My request for hardy is that firestarter should be installed as default and that the user should set it up on the install, or on first boot. 

Whats your Opinion?

Merry Christmas zenkaon,

I agree, even though firestarter is merely a GUI interface to the IP Tables, but it's a good idea because I like to tweak my firewall for certain clients and firestarter makes that easy.

Take Care,

T9

---

### Post by Johnsie on 2007-12-28
Ubuntu already comes with a Firewall called iptables. However a GUI for iptables would be useful for people who want to customise their firewall. I think Firestarter does that quite well, but it is certainly not the best firewall configuaration interface that I have used. Some of the Windows firewalls are really good and very eay to use. Outpost firewall is probably my favourite firewall.

---

