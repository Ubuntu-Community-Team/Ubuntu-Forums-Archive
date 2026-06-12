---
title: "UbuntuStudio-Audio apps not installed?"
date: 2011-01-25
forum: Ubuntu Studio
---

### Post by BurtaN on 2011-01-25
Hi!

I've just token a look on the UbuntuStudio-Audio package list and realized that at least JACK is not installed and I think the other packages neither, though I haven't checked it yet. So is this normal or did I do a mistake while setting up UbuntuStudio?

Thanks in advance,
BurtaN

---

### Post by Pablo_F on 2011-01-26
Hi, 

Unfortunately, there is a package called jack that has nothing to do with the jack we are talking about. See the description. The server is called jackd (jack daemon) and the gui frontend (Jack Control) is called qjackctl. 

Just to confirm, take a look at the terminal output of:

dpkg -l | grep jack

(to see the installed packages related to jack)

or 

dpkg -l |less

(to see all the installed packages in your system)

ii means installed.

Cheers, Pablo

---

### Post by BurtaN on 2011-01-26
Thanks, that explains some missunderstandings for me. Anyway I'm reffering to [this site.]("https://wiki.ubuntu.com/UbuntuStudio/PackageList") The part ubuntustudio-audio also lists qjackctl, but it doesn't seem to be installed.

```
frederik@frederik-desktop:~$ dpkg -l | qjackctl
Die Anwendung »qjackctl« ist momentan nicht installiert. Sie können es durch folgende Eingabe installieren:
sudo apt-get install qjackctl

```

Do I have to use this to get all the stuff?
```
 sudo apt-get install ubuntustudio-audio 
```

BurtaN

---

### Post by Pablo_F on 2011-01-26
Yes.

---

