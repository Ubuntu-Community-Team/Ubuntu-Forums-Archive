---
title: "New Linux Command"
date: 2007-03-22
forum: The Cafe
---

### Post by elephant007 on 2007-03-22
here's my new linux command

```
echo 'blacklist microsoft' | sudo tee -a /etc/modprobe.d/blacklist
```


:lolflag:

---

### Post by BLTicklemonster on 2007-03-22
I hate to ask, but what does that do?

---

### Post by elephant007 on 2007-03-22
> **BLTicklemonster said:**
> I hate to ask, but what does that do?

there's no need to hate to ask, it does nothing, It was my futile attempt at humor.

I have dumped Microsoft and will only, from now on, run Linux.  Vista pushed me to that decision.

---

### Post by H.E. Pennypacker on 2007-03-22
> **BLTicklemonster said:**
> I hate to ask, but what does that do?

The echo part makes the terminal spit out whatever is in quotes (you can alter the quotes).  It doesn't actually do anything other than that.  I don't know what the second part does.

---

### Post by Nikron on 2007-03-22
> **H.E. Pennypacker said:**
> The echo part makes the terminal spit out whatever is in quotes (you can alter the quotes).  It doesn't actually do anything other than that.  I don't know what the second part does.

it appends the echoed line to /etc/modprobe.d/blacklist for whatever reason.  I really didn't get the joke.  By the way, if you don't like Vista, you can always run Xp.  You also gotta wonder why you just didn't 

echo 'blacklist microsoft' >> /etc/modprobe.d/blacklist

---

### Post by elephant007 on 2007-03-22
oh, what the command actually does is this

Instead of having to ```
sudo gedit /etc/modprobe.d/blacklist
```

to open up 'blacklist' and then scroll to the bottom to add 'blacklist microsoft' 
save>close

you can just use that command to add the blacklisted module to the blacklist
this would block a driver from being loaded
an example would be if you have a Broadcom Wireless Card, you would want to blacklist the existing bcm43xx module from loading so it will not cause corruption or confusion with the driver you will have ndiswrapper using.

Nikron: 
  Running XP would defeat the purpose of me not using a Microsoft product.  That is my intention, to not run Microsoft products.  Plus I want to make computing fun again.  And as I said, it was my *futile* attempt at humor... he he

when you boycott a company you don't just boycott one of their products and give them your money using a different product they offer.


"in a world without fences, who needs gates"

---

### Post by Wolki on 2007-03-22
> **Nikron said:**
> You also gotta wonder why you just didn't 

echo 'blacklist microsoft' >> /etc/modprobe.d/blacklist

Probably because output redirections and sudo don't go together well, tee is the proper solution then.

---

