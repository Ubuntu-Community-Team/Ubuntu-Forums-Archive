---
title: "Hacked, guessing a dhclinet vulneratbility"
date: 2013-12-01
forum: Security
---

### Post by e.rietmeijer on 2013-12-01
I was recently hacked, probably due to visiting a not-so-friendly website. From reading my logs I am guessing a dhclient vulnerability was used (see [http://www.kb.cert.org/vuls/id/107886](http://www.kb.cert.org/vuls/id/107886) ). I am not sure it is this, but in any case I can't find any information on closing this vulnerability on Ubuntu Server. 

Any suggestions? Also, does anyone have tips on preventing other common exploits to DHCP/DNS/etc services?

---

### Post by wildmanne39 on 2013-12-01
*Thread moved to **Security Discussions**.*

---

### Post by bab1 on 2013-12-01
> **e.rietmeijer said:**
> I was recently hacked, probably due to visiting a not-so-friendly website. From reading my logs I am guessing a dhclient vulnerability was used (see [http://www.kb.cert.org/vuls/id/107886](http://www.kb.cert.org/vuls/id/107886) ). I am not sure it is this, but in any case I can't find any information on closing this vulnerability on Ubuntu Server. 

Any suggestions? Also, does anyone have tips on preventing other common exploits to DHCP/DNS/etc services?

These reference is not for current versions of Ubuntu.  The solution was instituted in 2011.  See: [http://www.ubuntu.com/usn/USN-1108-1/]("http://www.ubuntu.com/usn/USN-1108-1/").  See the note at the bottom of the page```
To update your system, please follow these instructions: [https://wiki.ubuntu.com/Security/Upgrades](https://wiki.ubuntu.com/Security/Upgrades).

**In general, a _standard system update_ will make all the necessary changes.**
```

Most likely this is not the reason you got hacked. 

 By default Ubuntu Server doesn't have a Web Browser, in fact it doesn't have a GUI interface at all.  Did you modify your server?

---

### Post by e.rietmeijer on 2013-12-02
No, I use the server as both a multi-purpose server and a firewall with 2 ethernet interfaces (WAN/LAN). I know the risks of not dedicating a machine for a single purpose like fire walling, but at the moment this should be adequate for me to learn Linux on. I browse on my mac, which runs behind the firewall, and of course one of the malicious sites I visited was informed of the existence of my server (no more pirating for me). I am guessing I picked up some bad code somewhere. I was also running transmission-daemon, this is probably also a liability.

---

### Post by CharlesA on 2013-12-02
Stupid question, but what makes you think you got hacked?

There is no way I would put a multipurpose server as a gateway machine. That's a bit like putting all your eggs in one basket, so to speak.

If you lack a regular router, you can pick one up, or you could try a running a virtualized copy of something like pfSense or M0n0wall.

---

### Post by bashiergui on 2013-12-02
I've got the same stupid question.
Also what did you see in the logs that landed you on that particular vulnerability?
If you've been torrenting pirated media then yeah, you probably did pick up some bad code.

---

### Post by e.rietmeijer on 2013-12-04
I got alot of DNS queries from loo1 . ru, and a few single ones from doc . gov, dnsscan . shadowserver .org and a few others. I have gotten 2 new dns queries today, needless to say I am somewhat paranoid as to what is going on or who is querying my server. Any BIND security tips?

---

### Post by e.rietmeijer on 2013-12-04
I want to implement a pfSense firewall in the future, but have no funding at the moment.

---

### Post by bab1 on 2013-12-04
Are you running a public facing DNS server?  How many DNS names do you need resolved?  You shouldn't control who requests DNS resolution on a public facing server.  No firewall will help if you are allowing public use of your DNS services.

As far as security, I would check out the BIND forums and Google [BIND DNS security]("https://www.google.com/search?q=secure+dns&btnG=Go!#q=bind+dns+security")

---

