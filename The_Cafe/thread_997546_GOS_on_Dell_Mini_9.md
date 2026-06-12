---
title: "GOS on Dell Mini 9?"
date: 2008-11-29
forum: The Cafe
---

### Post by kevin11951 on 2008-11-29
I tried to put gos onto my dell mini 9, but the wireless doesn't work, and the Ethernet isn't helping...

any help?

---

### Post by zmjjmz on 2008-11-29
Assuming gOS is 8.10 (I think it is), you can download the b43-fwcutter package and get wifi working.
The wifi chip is a bcm4310.

---

### Post by kevin11951 on 2008-11-29
> **zmjjmz said:**
> Assuming gOS is 8.10 (I think it is), you can download the b43-fwcutter package and get wifi working.
The wifi chip is a bcm4310.

i have no Internet of any kind, so how will it fetch the firmware?

edit: its based on 8.04...

---

### Post by damis648 on 2008-11-29
> **kevin11951 said:**
> i have no Internet of any kind, so how will it fetch the firmware?

edit: its based on 8.04...

APTonCD
```
sudo apt-get install aptoncd
```

---

### Post by kevin11951 on 2008-11-29
> **damis648 said:**
> APTonCD
```
sudo apt-get install aptoncd
```

how does that help me?

---

### Post by damis648 on 2008-11-29
You can use it to create a repository of the required firmware on a CD, and then install it on the eee.

---

### Post by zmjjmz on 2008-11-29
> **kevin11951 said:**
> 
edit: its based on 8.04...
Then you should refer to guides for setting up the card on Hardy.

I'm honestly not sure what compelled you to install gOS by the way. Dell's pre-installed OS isw perfectly fine, and if you want Google Desktop you can just install it.

---

### Post by kevin11951 on 2008-11-29
> **damis648 said:**
> You can use it to create a repository of the required firmware on a CD, and then install it on the eee.

that didnt work :(
the post install script ask's for the internet, which there isnt any :(

---

### Post by zmjjmz on 2008-11-29
> **kevin11951 said:**
> that didnt work :(
the post install script ask's for the internet, which there isnt any :(

You're supposed to install it on another computer, then put the repo on a CD (or a flash drive in this case).

---

