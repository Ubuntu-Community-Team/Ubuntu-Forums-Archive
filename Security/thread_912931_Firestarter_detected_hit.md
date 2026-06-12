---
title: "Firestarter detected hit"
date: 2008-09-07
forum: Security
---

### Post by ratmandall on 2008-09-07
Time: Sep  7 21:58:17 Source: 208.69.148.102 Destination: 192.168.0.101 In IF: wlan0 Out IF:  Port: 80 Length: 68 ToS: 0x00 Protocol: ICMP Service: HTTP
[http://whois.domaintools.com/208.69.148.102](http://whois.domaintools.com/208.69.148.102)

Should I be worried?

---

### Post by rogeriopvl on 2008-09-07
Well, a hit is just a blocked attempt to something. You should not worry about it, only if you see several attempts from one IP address, and even in that case, if you have no services listening for outside connections you have no reason to worry.

---

### Post by kevdog on 2008-09-07
Looks like an ping request -- I wouldn't be worried.

---

### Post by hyper_ch on 2008-09-07
are you sure that you actually need to alter the default firewall rules?

---

### Post by ratmandall on 2008-09-08
> **hyper_ch said:**
> are you sure that you actually need to alter the default firewall rules?

Are you saying I did?

---

### Post by hyper_ch on 2008-09-08
yes did by insatlling firestarter.

---

### Post by 1Michael1 on 2010-07-14
I've the same issue, it pops up a detected hit quite often since I've started the firestarter.

This is how it looks like, should I be worried? Look at the time stamps, it's coming quite frequently.

[[IMG]http://a.imageshack.us/img248/4608/60407432.png[/IMG]](http://img248.imageshack.us/i/60407432.png/)

---

### Post by 1Michael1 on 2010-07-14
Sorry for the double post but it keeps coming every second now.

I ain't running any programs.

[[IMG]http://img215.imageshack.us/img215/7317/40872745.png[/IMG]](http://img215.imageshack.us/i/40872745.png/)

---

### Post by bodhi.zazen on 2010-07-14
Are you running a torrent ?

---

### Post by 1Michael1 on 2010-07-14
No, I don't run anything besides Pidgin and Chrome.

---

### Post by bodhi.zazen on 2010-07-14
Post the output of 

```
sudo lsof -i -n -P
```That should give us insight.

If you really want to know, install wireshark (do not run wireshark as root) and capture a few packets.

If you are causally asking, IMO Dropped packets are almost always meaningless.

---

### Post by xpod on 2010-07-14
> **bodhi.zazen said:**
> Post the output of 

```
sudo losf -i -n -P
```

That should give us insight.

If you really want to know, isntall wireshard (do not run wireshark as root) and capture a few packtes.

If you are causally asking, IMO Dropped packets are almost always meaningless.

Bit of a typo in that command bodhi. 
I think you actually mean "lsof" and not "losf". :)

As far as Firestarter itself is concerned that events tab seems to cause more problems than it solves. People see all the *blocked* connections in that events tab and dont seem to realize it`s actually just doing it`s job....hopefully anyway.

---

