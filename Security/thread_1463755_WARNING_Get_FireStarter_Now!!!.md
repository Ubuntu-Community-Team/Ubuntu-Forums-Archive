---
title: "**WARNING** Get FireStarter Now!!!"
date: 2010-04-27
forum: Security
---

### Post by Ghettodragon on 2010-04-27
I have an Asus 900 laptop that I put Ubuntu 9.10 on.I know it was made by the Chinese, but why are they trying to hack my pc?I currently put FIRESTARTER a linux firewall on board you can go here to get it[  http://www.fs-security.com/]("http://www.fs-security.com/").Now I can see everyone's IP address and find out where they are and who they are!!:)

---

### Post by bowens44 on 2010-04-27
what makes you think someone is trying to hack your PC?

---

### Post by CharlesA on 2010-04-27
> **bowens44 said:**
> what makes you think someone is trying to hack your PC?

Paranoia.

EDIT: Also Firestarter isn't being maintained any longer. Use GUFW.

---

### Post by cariboo on 2010-04-27
Almost all computer components are made in China, what makes you think that they are targeting you specifically? As CharlesA said Firestarter hasn't been maintained, except for a few bug fixes, the world has changed quite a bit since 2005, Do you really trust it now?

---

### Post by Soul-Sing on 2010-04-27
Even some firestarter bugs are left alone....really.
On debian this bug still affects my desktop: [https://bugs.edge.launchpad.net/ubuntu/+source/firestarter/+bug/42759](https://bugs.edge.launchpad.net/ubuntu/+source/firestarter/+bug/42759)

---

### Post by Soul-Sing on 2010-04-27
Ghettodragon "they" are [COLOR="Red"]not[/COLOR] after you, believe me.

---

### Post by bodhi.zazen on 2010-04-27
IP addresses are easily spoofed and some OS are easily cracked.

It would be a sloppy cracker who used his or her actual ip address.

By default, there are no open ports, so configuring your firewall, via iptables, firestarter, or ufw does very little to increase your security.

You do not need firestarter, simply :

```
sudo ufw enable
```

firestarter conflicts with ufw, so you would need to purge it

```
sudo apt-get purge firestarter
```

Speaking of un-fixed firestarter bugs, I reported the conflict between firestarter and ufw some time ago 

[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/404600)

---

### Post by uberlinuxnerd on 2010-04-27
This thread made me chuckle! Respect to the thread starter :P

---

### Post by R.Bucky on 2010-04-28
They are coming! Everyone to the Community Center!!!

---

### Post by misterfixit on 2010-04-28
> **R.Bucky said:**
> They are coming! Everyone to the Community Center!!!

Fools!!!  Don't you realize that it is THEY who WANT you to go to the Community Center!  Quickly now, so no one else knows, put your left index finger into your right nostril, touch your LEFT nipple with your right hand and breathe deeply saying the words: Innagaddadavidahunny ...

There, all better now?  You think!

Heh, you've just voluntarily given me your SOUL!  Squirm like the tiny insepct you are! Squirm!

---

