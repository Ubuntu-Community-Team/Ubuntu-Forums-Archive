---
title: "Firestarter fails to started"
date: 2008-07-15
forum: Security
---

### Post by kidman on 2008-07-15
I have just downloaded and installed Firestarter (firewall for Ubuntu). 
When I started the Firestarter, it fails to start and give message like this.


<Failed to start the firewall

The device wifi0 is not ready.

Please check your network devices settings and make sure your Internet connection is active>

I am on the Internet using my workplace wireless network. I was able to access the Internet but why the message stated that "make sure your Internet connection is active.

Help please:(

---

### Post by Dr Small on 2008-07-15
Have you tried running it from the terminal with:
```
gksudo firestarter
```

???

Dr Small

---

### Post by kevdog on 2008-07-15
wifi0 is not your device -- it has to be something else like ath0 or wlan0.

---

### Post by kidman on 2008-07-15
I managed to get Firestarter to start by making some changes to the network setting in preference menu which I don't know what I have done. But the problem is Firestarter blocked all web accesses including Ubuntu Web forum. So I have to disable it to the access the web.:confused:

---

### Post by kevdog on 2008-07-16
Are you using Firestarter to set the default Output policy to DROP rather than accept?  Again not knowing your rules, this is what I am guessing what is happening.

---

### Post by Sn3ipen on 2008-07-16
I found firestarter to be buggy and sometimes it closed for no reason.

If you are using Hardy i would recommend you to use Uncomplicated firewall instead.

It's so easy to manage it and it does exactly the same thing.

[http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html#more-418](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html#more-418)

---

### Post by WSmart on 2008-11-06
I had the same thing and it suddenly started working after I hit the Accept button on the firestarter preferences.  I'm sure I've seen this before.  I also toggled the System>Administration>Network Tools devices from loopback to my internet, just before it started working.  That's just a viewer, so I don't know. Just a thought. Hope you solved this.


Love has to be more then a feeling or love is as nothing at all.  NK

---

