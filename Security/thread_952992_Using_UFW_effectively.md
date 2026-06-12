---
title: "Using UFW effectively"
date: 2008-10-19
forum: Security
---

### Post by Neo Adventist on 2008-10-19
Hello.  I've never used Uncomplicated Firewall before, mostly because I've used Firestarter instead, but I re-installed Hardy yesterday, and I wanted to give UFW a try.

The rules I want are pretty simple:

Block *all* incoming and outgoing traffic *except* that which involves Firefox, Thunderbird, Transmission, and Aptitude

I have yet to find a howto that effectively details how to use UFW.  Even a simple description of *blacklist everything* seems to elude me.

Any assistance would be greatly appreciated.

---

### Post by kostkon on 2008-10-19
> **Neo Adventist said:**
> Hello.  I've never used Uncomplicated Firewall before, mostly because I've used Firestarter instead, but I re-installed Hardy yesterday, and I wanted to give UFW a try.

The rules I want are pretty simple:

Block *all* incoming and outgoing traffic *except* that which involves Firefox, Thunderbird, Transmission, and Aptitude

I have yet to find a howto that effectively details how to use UFW.  Even a simple description of *blacklist everything* seems to elude me.

Any assistance would be greatly appreciated.
Maybe a [GUI frontend]("http://www.getdeb.net/app/gufw") would be helpful...

---

### Post by jerome1232 on 2008-10-19
Transmission... don't most torrent clients use random outgoing ports?

UFW doesn't manipulate outgoing rules only incoming.

---

### Post by Nepherte on 2008-10-20
> **jerome1232 said:**
> Transmission... don't most torrent clients use random outgoing ports?

UFW doesn't manipulate outgoing rules only incoming.
You can filter outgoing traffic by editing /etc/ufw/before.rules, but it's not an ideal solution.

---

### Post by nubdora on 2008-10-21
I don't see a reason why a normal user would want to block all outgoing traffic, but the rule for denying most incoming is:

sudo ufw default deny

Specifically, 

sudo ufw deny (#port)/(protocol)

Example,

sudo ufw deny 6328/tcp

---

### Post by sethvath on 2008-10-21
Gufw simplies everything for you, you can set it to use the proconfigured settings for transmission. 

One thing I noticed is that transmission downloads faster when I have ufw enabled.

---

### Post by nubdora on 2008-10-23
> **sethvath said:**
> Gufw simplies everything for you, you can set it to use the proconfigured settings for transmission. 

One thing I noticed is that transmission downloads faster when I have ufw enabled.

Traffic is faster using Transmission when you have your IP Tables firewall configured for TCP via ufw since Ubuntu's default IP Tables configuration does not have rules enabled for services to listen to traffic. **

Not trying to be a prick, but the technical part of my brain was spanking every thing else when I read that.

---

### Post by kevdog on 2008-10-23
> Ubuntu's default IP Tables configuration does not have rules enabled for services to listen to traffic

Can you explain this more?  I don't follow what you are saying.

---

### Post by jerome1232 on 2008-10-23
iptables allows all traffic by default, there's no configuring to be done. I don't see any way that configuring iptables would speed up transmission, only slow it down if it's blocking certain ports.

---

### Post by nubdora on 2008-10-23
> **kevdog said:**
> Can you explain this more?  I don't follow what you are saying.

Neither do I. By reading various things I inferred iptables denied traffic by default, but after quick research of my own I stand corrected. iptables is permissive by default and every thing I stated before is irrelevant to iptables, but completely relevant if it denied by default. So, I am incorrect as is the poster whom stated, "Transmission is faster with ufw enabled". In fact, there are a lot of things incorrect with that statement.

---

