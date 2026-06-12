---
title: "Password at start up"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by OlavRB on 2012-03-29
Hi

I can't seem understand one thing about log in:
If you write correct password, you immediately get loged in. Like a blink of an eye.
But if you are to write wrong pw, it takes several seconds for Ubuntu to check wheter the password entered was the correct or not. 
How is that?

Windows 7 acts the same way. Is it a delay made by the creators, or does it simply take that long? How/why?


Cheers, Olav

---

### Post by amauk on 2012-03-29
Purely a guess, but it may be sending out a network broadcast message looking for remote auth-servers

Something like
- Can I authenticate user locally? instant no
- Is there a central auth-server on the network? few seconds timeout, no
- Can't log in

dunno, just a guess really

---

### Post by WasMeHere on 2012-03-29
Hi Olav,

Welcome to the Ubuntu Forums!

I think it is good, because it takes much longer time to find your password by simply testing a huge number of candidate passwords (think also of automatic log in via for example ssh).

Have fun finding out about Ubuntu :-)
Olle

---

### Post by amauk on 2012-03-29
> **Olle Wiklund said:**
> I think it is good, because it takes much longer time to find your password by simply testing a huge number of candidate passwords (think also of automatic log in via for example ssh).But anyone with physical access to the machine could just boot from CD/USB and be able to mount disk partitions, so adding an artificial delay to the login wouldn't really gain you any extra security

---

### Post by WasMeHere on 2012-03-29
> **amauk said:**
> But anyone with physical access to the machine could just boot from CD/USB and be able to mount disk partitions, so adding an artificial delay to the login wouldn't really gain you any extra security
That's right, unless the home folders are encrypted. So either it is made to be slow, or slow because it is doing something, as you suggested in your first post. Anyway, it *does* make it harder to find the password by brutal number-crunching force.

---

### Post by bobman321123 on 2012-03-29
I always assumed that it was an artificial wait for security. 
There are several Mac's in my house, and they all make the wait longer and longer with each successive unsuccessful attempt. 
So, my guess is security.

---

