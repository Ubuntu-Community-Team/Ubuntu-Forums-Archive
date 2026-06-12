---
title: "port scans"
date: 2010-09-20
forum: Security
---

### Post by ahbart on 2010-09-20
Hello,
I'm very worried about a lot of potential threats from the internet.

My ADSL modem is configured so that it will send an e-mail if there is something wrong or if there is a potential thread. It is a Netgear DG834N adsl wireless modem.

Since a week I receive exponential groing lot of e-mails now with the subject: NETGEAR Security Log.

Last night I received 76 of these. They contain a lot of lines like:
```

Mon, 2010-09-20 01:17:20 - TCP Packet - Source: (ip-address from far away),12200 Destination:(my ip-address),27977 - [Any(ALL) rule match]
Mon, 2010-09-20 01:17:20 - TCP Packet - Source:(ip-address  from far away),12200 Destination:(my ip-address),8085 - [Any(ALL) rule match]

Mon, 2010-09-20 02:18:22 - TCP Packet - Source:(ip-address from far away),9477 Destination:(my ip-address),22 - [Any(ALL) rule not match]
Mon, 2010-09-20 02:41:59 - UDP Packet - Source:(ip-address from far away),1271 Destination:(my ip-address),1434 - [Any(ALL) rule not match]
```

As far as I can see in the log files on my Ubuntu server (10.04) or Ubuntu desktop (10.04) they did not get access to my systems. But I'm not sure. Don't they need a reason to suspect my system is interesting?
Do I really have to worry? Is there anything I can do about this?
Please some advise.

---

### Post by BkkBonanza on 2010-09-20
It's just a waste of your time sending you emails like that. The internet is awash with people scanning for systems to hack. They don't even know who you are - they just scan blocks of IPs in either random or numeric order. 

It doesn't matter if they scan you - only if they can find a way in. Your router forms a first barrier to this stuff so let it do it's job of blocking 99% of it, but don't have it send you emails about what it's blocking. 

The first step is to follow some of the info in the sticky posts at the top of this forum. That will guide you in pretty much what you need to do. After that you can work on tightening things up as you learn more. Just know that port scanning, finding target systems and then attempting to login is rampant on the net. That's why using strong passwords (or keys) and not exposing anything you don't need to, is basic good sense.

(It looks like your router is set to send email on ANY/ALL match. It's bound to send you heaps of garbage email.)

---

### Post by ahbart on 2010-09-20
Thanks BKKBonanza, that is helping me a lot. I've just read the security posts and I will further secure my systems. (I did use keys for ssh but did not disable password login. I will install rkhunter and denyhost). I will also have a look at the modem logging settings, or might disable this function at all.

---

### Post by pricetech on 2010-09-20
> **ahbart said:**
> Thanks BKKBonanza, that is helping me a lot. I've just read the security posts and I will further secure my systems. (I did use keys for ssh but did not disable password login. I will install rkhunter and denyhost). I will also have a look at the modem logging settings, or might disable this function at all.

I used to get emails from my router too.  After studying them for a while I realized that indeed the scans were random.  I turned off the emails.

Having said that, it doesn't hurt to take a look at them from time to time.  Just know that as long as your router is dropping them, you won't look interesting to anybody.

---

### Post by BkkBonanza on 2010-09-20
Probably the simplest way to assess your router from the outside is to do your own scan and make sure that only the ports you expect are open and the others stealth/closed.

The ever popular ShieldsUp scan can do that for you in just a few seconds, and gives you some idea what scanners are likely to find,

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by scottuss on 2010-09-20
Don't worry too much, you'll get scanned all the time. It's the nature of the public network.

---

### Post by Velnias on 2010-09-20
> I did use keys for ssh but did not disable password login

Bad idea. Its not safer than running password only authentication.

---

### Post by perspectoff on 2010-09-20
> **Velnias said:**
> Bad idea. Its not safer than running password only authentication.

Depends on the password, of course. But a 128-bit generated key is indeed likely safer than 99.9% of passwords that any user can easily remember. 

Besides, keyloggers love it anytime that passwords are entered manually (or can be intercepted as virtual keyboard inputs). I do know of users that script their SSH passwords, but that sure is easy to find out for anyone that sits down at their computer (unlike keys that can be hidden from prying eyes). 

Besides, password authentication invites brute-force password cracking attempts, whereas I haven't seen that many crackers willing to brute-force-guess 128-bit keys.

Every brute-force attempt slows down the server, similar to a Denial of Service attack, and brute-force password attackers would love it if all of us left SSH at password authentication, right?

For ultimate security, use knockd.

---

### Post by perspectoff on 2010-09-20
> **BkkBonanza said:**
> Probably the simplest way to assess your router from the outside is to do your own scan and make sure that only the ports you expect are open and the others stealth/closed.

The ever popular ShieldsUp scan can do that for you in just a few seconds, and gives you some idea what scanners are likely to find,

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Or simply:

 sudo nmap localhost

(After installing nmap, that is:

 sudo apt-get install nmap)

If your LAN were 192.168.0.1, you could find out the open ports on all the computers of the LAN:

 sudo nmap 192.168.0.1/24

And yes, definitely turn off the email notifications from the router. That's probably a very old router.

Lastly, many ISPs which provide internet access over DSL use Dynamic IP addressing. On Wednesday you may be assigned an IP address that on Tuesday was used by someone trading files. That IP address might have been very high-profile for that reason and you may be getting probed by lots of computers that think they are still trying to access the file-trader's computer.

Sometimes this drives me nuts if I happen to be doing something on a port that was used by the previous day's user, and I get a lot of spurious attempts to connect. In this instance, I will disconnect (through the router) and then reconnect, thereby obtaining a fresh IP address (by DHCP) that hopefully isn't as high profile as the previous one.

---

### Post by BkkBonanza on 2010-09-20
> **perspectoff said:**
> Or simply:

sudo nmap localhost
sudo nmap 192.168.0.1/24

In addition to ShieldsUp, because it won't tell you anything about your router from the public side, which is the first thing you need to check.

---

