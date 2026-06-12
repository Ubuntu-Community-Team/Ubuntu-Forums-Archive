---
title: "first steps to convergence"
date: 2016-04-22
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-04-22
This link explains that snaps and deb packages will be able to be installed , side by side and work together. This  , perhaps, is one of the first examples of working convergence and it is fully automated up to a point.

[http://www.pcworld.com/article/3056668/linux/ubuntu-1604-will-support-snaps-alongside-deb-packages-for-improved-software-installation.html](http://www.pcworld.com/article/3056668/linux/ubuntu-1604-will-support-snaps-alongside-deb-packages-for-improved-software-installation.html)

---

### Post by ventrical on 2016-04-22
I had read a post from grahammechanical in another thread and it leads me to a question; Would we be able to use a minimal system on older metal where a user can just install snaps .. say ... a clock, a calendar and a web-browser? since snappy core is 32bit capable I wonder if Lubuntu alternate could suffice in providing for such a scenario?

Regards..

---

### Post by grahammechanical on 2016-04-22
There is only one way to find out. Give me a couple of hours & I will report back. I am downloading the Lubuntu 32 bit 16.04 Alternate ISO image right now. It should work as it should have snapd by default. But there is nothing better that an actual experiment.

I have already done this with Xubuntu core. Firefox (deb version), the 2 snap apps and precious little else. Not even a software centre. So, if disk space is really tight then the Mini ISO is the way to go. Get a truly tailored OS to fit the user.

Imagine, snappy Ubuntu core with a DE & GUI + snap packaged Firefox & just a few useful utilities also as snaps. It would be a minimal, secure OS where an update to the OS never breaks the OS. Just the thing some users need. Protection from themselves. And not just senior citizens. 

Am now about to burn the Lubuntu alternate ISO to disc.

Regards.

---

### Post by ventrical on 2016-04-22
I am to do the same thing here.

Regards..

---

### Post by Cavsfan on 2016-04-22
I just checked and snap is installed already.

I'll have to try some stuff I guess.

```
cavsfan@cavsfan-le-beast:~$ apt-cache policy snapd
snapd:
  Installed: 2.0.2
  Candidate: 2.0.2
  Version table:
 *** 2.0.2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

I see the actual command is indeed snap though as I entered **man snap** and got a lot of info. Pretty kewl!

---

### Post by cariboo on 2016-04-22
Snap packages may not be as secure on the desktop as Canonical has led us to believe, see this [article]("http://www.zdnet.com/article/linux-expert-matthew-garrett-ubuntu-16-04s-new-snap-format-is-a-security-risk/")

---

### Post by Cavsfan on 2016-04-22
Thanks for that article! I was looking at **man snap** and couldn't figure out very much about it anyway.

I guess that's a good thing.

---

### Post by grahammechanical on 2016-04-22
Well, this is what I got. With Lubuntu 16.04 32 bit Alternate ISO image 

> graham@sda6-Lubuntu:~$ sudo snap install ubuntu-calculator-app
61.70 MB / 61.70 MB [====================================] 100.00 % 848.35 KB/s 

error: cannot perform the following tasks:
- Download snap "ubuntu-calculator-app" from channel "stable" (snap not found)

graham@sda6-Lubuntu:~$ sudo snap install ubuntu-clock-app
61.70 MB / 61.70 MB [====================================] 100.00 % 777.67 KB/s 

error: cannot perform the following tasks:
- Download snap "ubuntu-clock-app" from channel "stable" (snap not found)


I do not think this would happen if it was the 64 bit ISO image. We will need to research "channels." Do we need to install the ubuntu-core snap first? It should all be part of the app installation process.

This works
> 
graham@sda6-Lubuntu:~$ snap find
Name                Version                  Summary
canonical-dragon    0.7.1                    The gadget snap for the dragonboard
canonical-i386      3.1                      The gadget snap for generic i386 systems
canonical-pc        3.1                      AMD64 generic package
canonical-pc-linux  4.4.0-21+20160420.05-05  The ubuntu-core kernel snap
canonical-pi2       3.2                      Raspberry Pi 2 support package
hello-world         6.0                      Hello world example
http                4.6692016                HTTPie in a snap
tor-middle-relay    0.2.7.6-6                Essential infrastructure node for Tor network
ubuntu-core         16.04+20160420.05-02     The ubuntu-core OS snap
xkcd-webserver      16.04-5                  Show random XKCD compic via a build-in webserver

Regards.

---

### Post by Cavsfan on 2016-04-22
> **grahammechanical said:**
> Well, this is what I got. With Lubuntu 16.04 32 bit Alternate ISO image 

> graham@sda6-Lubuntu:~$ sudo snap install ubuntu-calculator-app
61.70 MB / 61.70 MB [====================================] 100.00 % 848.35 KB/s 

error: cannot perform the following tasks:
- Download snap "ubuntu-calculator-app" from channel "stable" (snap not found)

graham@sda6-Lubuntu:~$ sudo snap install ubuntu-clock-app
61.70 MB / 61.70 MB [====================================] 100.00 % 777.67 KB/s 

error: cannot perform the following tasks:
- Download snap "ubuntu-clock-app" from channel "stable" (snap not found)                      

I do not think this would happen if it was the 64 bit ISO image. We will need to research "channels." Do we need to install the ubuntu-core snap first? It should all be part of the app installation process.

This works


Regards.

I guess it is already on the 64 bit installs.
```
cavsfan@cavsfan-le-beast:~$ snap find ubuntu-core
Name         Version               Summary
ubuntu-core  16.04+20160419.20-55  The ubuntu-core OS snap
```

---

### Post by grahammechanical on 2016-04-22
> **cariboo said:**
> Snap packages may not be as secure on the desktop as Canonical has led us to believe, see this [article]("http://www.zdnet.com/article/linux-expert-matthew-garrett-ubuntu-16-04s-new-snap-format-is-a-security-risk/")

Well, if we did not know X11 was insecure by now, then we should have known. Was he installing his snap in dev mode? Did he get his snap into the snap store?

> You can install a snap using *"snap install --devmode ..."*.  The presence of *--devmode* switches confinement, for that snap only, from *enforcing mode* **where the application is rejected from accessing certain things** (or killed, depending on access pattern) to *complain mode*  **where the application is allowed to do anything**, as the local user  could, but appropriate messages are logged to let developers know that  something would not normally work.

Development mode is aimed at snap developers to let them understand what  their application (or application toolkit) is doing under the hood. We  are working on a separate tool that works along --*devmode* applications, analysing log files and offering suggestions as to which interfaces to use.

[http://www.zygoon.pl/2016/04/snap-install-devmode.html](http://www.zygoon.pl/2016/04/snap-install-devmode.html)

Regards.

---

### Post by grahammechanical on 2016-04-22
> **Cavsfan said:**
> I guess it is already on the 64 bit installs.
```
cavsfan@cavsfan-le-beast:~$ snap find ubuntu-core
Name         Version               Summary
ubuntu-core  16.04+20160419.20-55  The ubuntu-core OS snap
```

That command just finds the snap on some server. This is the command to search for snaps installed

> graham@sda6-Lubuntu:~$ snap list
error: no snaps found

Regards.

---

### Post by ventrical on 2016-04-22
I think it is this here that has to be installed. I am in the process now.

```


snap find


canonical-i386         3.1                      The gadget snap for generic i386 systems

```

So that would be for 32bit system.

---

### Post by ventrical on 2016-04-22
The calculator and calendar are currently not options that are available on 32bit systems... but snapd is working just fine on an old Compaq Presario:)

Regards..

---

### Post by ventrical on 2016-04-22
> **grahammechanical said:**
> Well, this is what I got. With Lubuntu 16.04 32 bit Alternate ISO image 



I do not think this would happen if it was the 64 bit ISO image. We will need to research "channels." Do we need to install the ubuntu-core snap first? It should all be part of the app installation process.

This works


Regards.

Do...

```


snap install hello-world


```

and it will successfully install ubuntu-core .. then it is wait and see what they put up in the (stable)s :)

---

### Post by mc4man on 2016-04-22
> **cariboo said:**
> Snap packages may not be as secure on the desktop as Canonical has led us to believe, see this [article]("http://www.zdnet.com/article/linux-expert-matthew-garrett-ubuntu-16-04s-new-snap-format-is-a-security-risk/")
I read that article also (served up by google-now) & the [orig. blog]("https://mjg59.dreamwidth.org/42320.html") 
What stood out more on znet was the "headline feature.." Not sure if that's media or media with a little help from Canonical, but not much there headline worthy..
Certainly highlights the direction Canonical is heading , (and Windows), there's no real money in the Os, the money is in the software (apps) & devices

---

