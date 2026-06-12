---
title: "Why command line?"
date: 2006-07-11
forum: Server Platforms
---

### Post by lugos on 2006-07-11
Hello,

I just installed Ubuntu 6.06 server and I'm getting a command line.  Forgive me for my ignorance, but is that supposed to happen?  Does the server edition come as a gui?  Or is it strictly command line?

Thanks,
lugos

---

### Post by Dr. Nick on 2006-07-11
server eidtion is command line, you can install a gui by running

sudo aptitude install ubuntu-desktop

you should also install a desktop kernel if you plan to use it as a desktop computer and not a server.

The instructions are out thier, I forget exaclty how, if i find them again ill post it here

---

### Post by lugos on 2006-07-11
Hello Dr. Nick,

I tried running that command but it said that it couldn't find any packages with the name 'ubuntu-desktop.'

Thanks,
lugos

---

### Post by Dr. Nick on 2006-07-11
Hmm.. Do you want just a regular desktop system? It may just be better to start over with the live cd.

does this work?

sudo apt-get install ubuntu-desktop

---

### Post by nkassi on 2006-07-11
Check the the apt sources.list (/etc/apt/sources.list) You might have the repository you need enable. Remove the # in front of every line that starts with deb http:...... 

Then sudo apt-get update
Then sudo apt-get install linux-image-386 (choose 686 if you have a p4 or k7 if you have an athlonxp or better)
Then sudo apt-get install ubuntu-desktop

Should work. (I did it before I just not sure if I did anything else)

Nic

---

### Post by houstonbofh on 2006-07-12
> **nkassi said:**
> Check the the apt sources.list (/etc/apt/sources.list) You might have the repository you need enable. Remove the # in front of every line that starts with deb http:...... 

Then sudo apt-get update
Then sudo apt-get install linux-image-386 (choose 686 if you have a p4 or k7 if you have an athlonxp or better)
Then sudo apt-get install ubuntu-desktop

The 686 kernel is for PPro or better, not just P4.  The 386 is only needed for Pentium, K6, Cyrix/Via C3, and other embededs.

Do you have inet connectivity?  If not, you will need a desktop CD and manually install the desktop packages.  Otherwise, if the repositories are correct, *sudo apt-get install* Ubuntu *ubuntu-desktop* Xubuntu *xubuntu-desktop* or Kubuntu.  Xubuntu is lightest, but Ubuntu has some better admin tools.  You can then remove the *buntu-desktop meta package, and remove the unneeded components such as open office.

---

### Post by ExMachina on 2006-07-12
i had a problem like this. It seem ubu didnt ahve proper drivers for my eth card. So i just switch ti and it was fine.

When i tried to isntall ubuntu desktop i kept gettign errors. I guess ther server was just beign bad that day. So I installed. 

```
sudo apt-get install xubuntu-desktop
```

---

