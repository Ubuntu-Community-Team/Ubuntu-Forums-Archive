---
title: "Wireless card and Lan card"
date: 2016-03-27
forum: Ubuntu/Debian BASED
---

### Post by Chris_hrobak on 2016-03-27
I have a hp g6-2292nr and I just installed backtrack 4 after windows 8 capped out and doesn't load. My problem is bt4 won't recognize most of my hardware including my usb ports ethernet card or wireless and can't seem to get it working which in turn I can't update any of the packages any assistance would  be appreciated

---

### Post by kc1di on 2016-03-27
could you go to a terminal and enter the following command```
inxi -F
```
and post the output here.

---

### Post by Chris_hrobak on 2016-03-27
Bash: inxi-f:command not found

---

### Post by PaulW2U on 2016-03-27
> **Chris_hrobak said:**
> Bash: inxi-f:command not found
You need to type:
```
inxi -F
```
exactly as quoted, i.e. a capital F after a space. :)

---

### Post by Chris_hrobak on 2016-03-27
Using linux console I enter command and get the same result. Root@bt:~# inxi -F bash: inxi: command not found

---

### Post by kc1di on 2016-03-27
maybe it's not installed in backtrack, try installing it.```
sudo apt-get install inxi
```

---

### Post by weatherman2 on 2016-03-27
> **kc1di said:**
> maybe it's not installed in backtrack, try installing it.```
sudo apt-get install inxi
```

And how is that going to work with no LAN or WAN working?

---

### Post by weatherman2 on 2016-03-27
For the network cards, type these:

```

sudo lshw -C network

```

---

### Post by Chris_hrobak on 2016-03-27
That worked told me what I had for my wireless and wired

---

### Post by X-RED_Tech on 2016-03-27
> **Chris_hrobak said:**
> That worked told me what I had for my wireless and wired

People asked you to run those commands not to confirm they work (they/we already know they do) but to know what hardware are you dealing with andf tailor the response accordingly. Please provide the results.

Also read this: [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/)
A Windows 8 computer is certainly much newer than the obsolete distro you decided to install so it's not surprising newer hardware isn't supported. And Kali (former Backtrack) is designed for very specific usages. It isn't a regular desktop distro. Why didn't you chose a normal thing like everybody else? And are you aware Kali has its own forums? Well, now you know.

---

### Post by Chris_hrobak on 2016-03-28
Any recommendation on a distributor to install

---

### Post by X-RED_Tech on 2016-03-28
> **Chris_hrobak said:**
> Any recommendation on a distributor to install

Really?
You're at the Ubuntu forum. Easy math.

---

### Post by howefield on 2016-03-28
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Chris_hrobak on 2016-03-28
I installed ubuntu but now more problem on boot may try and reinstall. Just installed from virtual drive since I don't have any blank dvds

---

