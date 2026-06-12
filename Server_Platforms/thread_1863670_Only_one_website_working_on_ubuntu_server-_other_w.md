---
title: "Only one website working on ubuntu server- other works fine"
date: 2011-10-18
forum: Server Platforms
---

### Post by 2kan on 2011-10-18
I've recently installed the latest version of ubuntu server and everything has been going fine. Except for the fact that one out of two of my client's websites just wont connect.

I type in the url on another computer and it just says "connecting" for about a minute before it fails. The other one works perfect though. I've checked the apache2.conf file and things seem normal there aswell. I even duplicated the working config file in "sites-available" and replaced the urls with the one that wasn't working.

Any ideas? If you need more information just ask

---

### Post by lisati on 2011-10-18
Is the DNS PTR for the second website pointing to the correct IP address?

---

### Post by 2kan on 2011-10-18
> **lisati said:**
> Is the DNS PTR for the second website pointing to the correct IP address?

:shock: Woah that fixed it. That's embarrassing :/ I accidentally typed the number 8 instead of 9 in the ip. Thanks :D

Sorry for the dumb question :P

---

### Post by lisati on 2011-10-18
> **2kan said:**
> Sorry for the dumb question :P
Don't sweat it: the only dumb questions are the ones which go unasked. Sometimes it's the little things that trip us up.

---

