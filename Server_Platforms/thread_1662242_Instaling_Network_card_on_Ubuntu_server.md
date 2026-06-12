---
title: "Instaling Network card on Ubuntu server"
date: 2011-01-07
forum: Server Platforms
---

### Post by BradNowacki on 2011-01-07
Alright im totally new to UNIX terminal, but im learning quick, and im trying to use this as an ssh server but i need to some how install drivers for my WMP600N V1.1 network card from linksys. so how would i go about this, and if someone can give me a link or tell me what they are doing that would be nice :D

---

### Post by CharlesA on 2011-01-07
Wireless card?

---

### Post by BradNowacki on 2011-01-07
Yes it is wireless here is the store page [http://www.linksysbycisco.com/UK/en/products/WMP600N](http://www.linksysbycisco.com/UK/en/products/WMP600N)

---

### Post by psusi on 2011-01-07
Either the kernel knows how to use it and it will just work, or it doesn't and you need to return it and get one with Linux support.

---

### Post by BradNowacki on 2011-01-07
well it works on lunix mint so it should work then right?

---

### Post by psusi on 2011-01-07
> **BradNowacki said:**
> well it works on lunix mint so it should work then right?

Yea.

---

### Post by BradNowacki on 2011-01-07
Ok so now that i have the server installed how do i connect to the internet?

---

### Post by psusi on 2011-01-07
Plug in the cable?

---

### Post by BradNowacki on 2011-01-07
yet again this goes back to the whole wireless internet but i guess ill lug my computer down stairs

---

### Post by psusi on 2011-01-07
Oh yea, then click on the wireless icon and connect to a network.

---

### Post by BradNowacki on 2011-01-07
> **psusi said:**
> Oh yea, then click on the wireless icon and connect to a network.
 
Ubuntu Server, no GUI

---

### Post by Vegan on 2011-01-07
what is this click nonsense, we server users do not use point & click

look in /etc/interfaces

which has the ethernet settings.

if there is a RJ-45 then that usually is eth0 and the wireless one is eth1

---

### Post by psusi on 2011-01-07
Check out the wpasupplicant package... I think that's how you do it without the gui.

---

### Post by BradNowacki on 2011-01-08
> **Vegan said:**
> what is this click nonsense, we server users do not use point & click

look in /etc/interfaces

which has the ethernet settings.

if there is a RJ-45 then that usually is eth0 and the wireless one is eth1


lol you made me laugh but i have gone through the settings and it was recognizing the Wlan0
but from there how would i connect to my network?

---

### Post by CharlesA on 2011-01-08
> **BradNowacki said:**
> lol you made me laugh but i have gone through the settings and it was recognizing the Wlan0
but from there how would i connect to my network?
Setting up wireless without a GUI can be tedious, which is why I use only wired connections for my servers.

Check here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

