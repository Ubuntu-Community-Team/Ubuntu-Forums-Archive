---
title: "avast"
date: 2009-12-08
forum: Security
---

### Post by pvplahing138 on 2009-12-08
i wonder can i download firewall and avast antivirus system to my ubuntu?
then i feel little safer can someone post avast for linux link and some good firewall software.
thanks.

---

### Post by staf0048 on 2009-12-08
Ubuntu comes pre-installed with a firewall all set and running.  You can configure it if you like with a program called Firestarter.  Search for it in Synaptic.

As for Avast! check out their website, they have a Linux version here:  [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Get the .deb file and double click to install.

---

### Post by pvplahing138 on 2009-12-08
> **staf0048 said:**
> Ubuntu comes pre-installed with a firewall all set and running.  You can configure it if you like with a program called Firestarter.  Search for it in Synaptic.

As for Avast! check out their website, they have a Linux version here:  [http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Get the .deb file and double click to install.

ok thanks for help!

---

### Post by Soul-Sing on 2009-12-08
> Ubuntu comes pre-installed with a firewall all set and running
iptables is indeed installed, but not up and running/try: 
```
sudo iptables -L
```
Ubuntu comes with a zero-open-port policy by default, which is enough for a desktop environment.(imho)
If you want to "start" iptables, use a frontend as:
- firestarter
- ufw or gufw (sudo apt-get install gufw)==> deny all.

---

