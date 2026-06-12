---
title: "This is a false positive, right?"
date: 2012-04-18
forum: Security
---

### Post by aligator12 on 2012-04-18
So I ran ClamTK and it said 12 of my flv from youtube were infected, that is a false pos, right?

---

### Post by ottosykora on 2012-04-18
> **aligator12 said:**
> So I ran ClamTK and it said 12 of my flv from youtube were infected, that is a false pos, right?

probably, but you can upload them to virustotal and let them to be checked there

---

### Post by rookcifer on 2012-04-18
> **ottosykora said:**
> probably, but you can upload them to virustotal and let them to be checked there

Really no point in even doing that.  I assume the OP is using Ubuntu and not Windows, thus these "infected" files wont make any difference one way or the other.

---

### Post by Grenage on 2012-04-18
> **aligator12 said:**
> So I ran ClamTK and it said 12 of my flv from youtube were infected, that is a false pos, right?

Maybe, maybe not - we don't have the files.  Clam scans for Windows viruses, so as written by the fellow before me, it's not much to worry about.

---

### Post by aligator12 on 2012-04-18
> **Grenage said:**
> Maybe, maybe not - we don't have the files.  Clam scans for Windows viruses, so as written by the fellow before me, it's not much to worry about.
I uploaded it to Jotti's malware scan and the only one that detected it was ClamAV. lol

---

### Post by ottosykora on 2012-04-18
yes , this is the right procedure as you see

---

### Post by aligator12 on 2012-04-23
> **ottosykora said:**
> yes , this is the right procedure as you see
So its a false pos, right? And does anyone know if anything better then ClamTK? It kinda sucks.

---

### Post by Grenage on 2012-04-23
There aren't really any alternatives that are much better; the bottom line is that due to the lack of real viruses for Linux, the offerings are both scarce and impotent.

---

### Post by rookcifer on 2012-04-23
> **aligator12 said:**
> So its a false pos, right? And does anyone know if anything better then ClamTK? It kinda sucks.

It likely really is some malicious piece of javascript code meant to do something funky to your browser (probably just redirect your browser to a malicious site).  Since browsers work the same on all platforms, it probably *could* work on Linux (browser languages like javascript are platform independent, so it doesn't matter the OS it is being ran on).

However, that's still no cause for concern.  Why? Because even though javascript works the same on Linux, a real attack would target the browser, then break-out of browser space and then target the system to do whatever malicious deed it is supposed to do.  The browser is just the avenue of getting in (known in IT speak as the "attack vector").  The real attack would be after.  So, when it gets to the system it would need to be written to target Linux, which is highly unlikely.  And even if it did, it would never get root unless you specifically gave it root permission (it could do some things without root like spam or connect to a remote host, but it would never get control of your entire system without root which means once discovered it would be trivial to fix).

So, basically, it is safe to pretty much ignore this stuff.  As long as you keep your browser updated (and preferably use Apparmor which is on by default in Ubunty) you should make the risk almost zero on Linux.  Nothing is 100%, but the chances of this being a successful attack on you is near zero.  

So, bottom line, it may or may not be a false positive.  If it isn't, then it's probably just a piece of malicious javascript code targeted at Windows.  This is why it is really just a better idea to get rid of the virus scanner.  It does nothing but scan for Windows viruses and does nothing to help with Linux security.  So many people get caught up in this mindset of thinking "I have a virus scanner, I am safe."  That is completely wrong headed and unhelpful in tackling real security vulnerabilities.  Viruses and malware are not a Linux attack vector, but there are other vectors that you should be more concerned with.  AV scanners, especially on Linux, give you a false sense of security.  Get rid of it.

---

### Post by aligator12 on 2012-04-23
> **rookcifer said:**
> It likely really is some malicious piece of javascript code meant to do something funky to your browser (probably just redirect your browser to a malicious site).  Since browsers work the same on all platforms, it probably *could* work on Linux (browser languages like javascript are platform independent, so it doesn't matter the OS it is being ran on).

However, that's still no cause for concern.  Why? Because even though javascript works the same on Linux, a real attack would target the browser, then break-out of browser space and then target the system to do whatever malicious deed it is supposed to do.  The browser is just the avenue of getting in (known in IT speak as the "attack vector").  The real attack would be after.  So, when it gets to the system it would need to be written to target Linux, which is highly unlikely.  And even if it did, it would never get root unless you specifically gave it root permission (it could do some things without root like spam or connect to a remote host, but it would never get control of your entire system without root which means once discovered it would be trivial to fix).

So, basically, it is safe to pretty much ignore this stuff.  As long as you keep your browser updated (and preferably use Apparmor which is on by default in Ubunty) you should make the risk almost zero on Linux.  Nothing is 100%, but the chances of this being a successful attack on you is near zero.  

So, bottom line, it may or may not be a false positive.  If it isn't, then it's probably just a piece of malicious javascript code targeted at Windows.  This is why it is really just a better idea to get rid of the virus scanner.  It does nothing but scan for Windows viruses and does nothing to help with Linux security.  So many people get caught up in this mindset of thinking "I have a virus scanner, I am safe."  That is completely wrong headed and unhelpful in tackling real security vulnerabilities.  Viruses and malware are not a Linux attack vector, but there are other vectors that you should be more concerned with.  AV scanners, especially on Linux, give you a false sense of security.  Get rid of it.
Well I rescaned the files it said was infected and it no longer detects it.

---

