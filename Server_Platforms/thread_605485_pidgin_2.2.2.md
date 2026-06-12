---
title: "pidgin 2.2.2"
date: 2007-11-07
forum: Server Platforms
---

### Post by Pedric on 2007-11-07
Now that with Gutsy, Ubuntu packages a recent Pidgin version, I have been waiting 2 weeks now for Ubuntu to put 2.2.2 into the official repos. It fixes a remote crash (DoS), see:

[http://pidgin.im/news/security/?id=24](http://pidgin.im/news/security/?id=24)

nothing critical, but their website recommends "you should upgrade right away"...

---

### Post by robrmd9 on 2007-11-07
I'm also interested to see if they update it, I hope so!

---

### Post by potentia on 2007-11-07
I have been running it since the release day, on Windows. 

Ubuntu must mean "waiting 6 months to get your install broken by dist upgrade" to get new releases.

I don't know what the problem is, even getdeb and debuntu doesn't have it.

---

### Post by LavianoTS386 on 2007-11-08
It's in some 64 bit 3rd party repos, but not any 32-bit ones that I am aware of.

---

### Post by mivo on 2007-11-10
> **LavianoTS386 said:**
> It's in some 64 bit 3rd party repos, but not any 32-bit ones that I am aware of.

Which third party repository has the 64-bit version, please?

---

### Post by 1337455 10534 on 2007-11-10
Ya, I'm seriously pissed that there is no mention of deb in the Pidgin home page. I'm running 2.2.1 on Ubuntu, and 2.2.2 on XP and besides that crash, FILE TRANSFERS WORK, perfectly (at least on XP). You dont have to disable that encryption and use ICQ (i think that was teh name) protocol to file transfer anymore.
So I just uninstalled Pidgin .1, I need a deb for 2.2.2.

I'm OK with compiling it (in fact I'd love to give it a shot, but I need directions. Suppose I get the source, Is it:
```

cd (the src dir)
make
sudo make install

```
or something?

---

### Post by robrmd9 on 2007-11-10
```
./configure
make
sudo make install
```

---

### Post by Pedric on 2007-11-10
I'm actually aware of building pidgin myself, but hey, here's a program that's in the official repos and even part of the software installed by default. You shouldn't need to build this piece of software for security updates yourself...

---

### Post by robrmd9 on 2007-11-10
> **Pedric said:**
> I'm actually aware of building pidgin myself, but hey, here's a program that's in the official repos and even part of the software installed by default. You shouldn't need to build this piece of software for security updates yourself...

I think we all agree with that, but it has been a couple weeks and the Ubuntu folks haven't updated the official packages.

---

### Post by 1337455 10534 on 2007-11-10
Yikes, I know. Haven't got any updates in forever...
Anyone know of a sources.list for Gutsy that can rival Trevinos for Feisty?

---

### Post by dmber on 2007-11-22
what's up with this?  i see i'm still running 2.2.1 with Gutsy as well...

---

