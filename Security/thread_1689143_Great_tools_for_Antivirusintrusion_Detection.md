---
title: "Great tools for Antivirus/intrusion Detection?"
date: 2011-02-16
forum: Security
---

### Post by FlurrYx on 2011-02-16
Hi there, I'm quite new to Linux and I'm wondering if you guys have any personal favourite software to use against Intrusion and such. I've been up to some researching for a while and as you probably know it's a bit of a jungle :roll:

The thing is that I don't want to have several anti virus programs running at the same time due to collision.


(sorry if I posted anything wrong or anything similar) ;)

---

### Post by uRock on 2011-02-16
Hello and welcome to the forums.

Unless you are running a server, you don't really need either.

If you have folders that are being shared with Windows machines, then an AV may be warranted. In that case I would use Avast or BitDefender. I haven't used Avast, but I have used BitDefender and I was pleased with it.

If you really feel that you need an intrusion detection, then SNORT is easily install via the Ubuntu Software Center.

Regards,
uRock

---

### Post by andy8 on 2011-02-16
I started using Ubuntu less than a week ago and love it! 
Decided to take windows off completely :D
The thing that drew me here was the understanding that there would be less chance of getting a virus/spy-ware. 
However, you can, like I done download several things to help tame your fears, you have carried forward from windows!

Open **Ubuntu software centre** and type in **KlamAV** you might run into a few problems with the updates so I suggest you read this page: [http://ubuntuforums.org/showthread.php?t=1547713](http://ubuntuforums.org/showthread.php?t=1547713)
 The **replace dophin with 'nautilus' ** worked for me.

Open **Ubuntu software centre** and type in**firestarter** a good firewall.


Open **Ubuntu software centre** and type in **BleachBit** runs a little like ccleaner without the reg cleaner as Ubuntu has no reg!

Andy

---

### Post by FlurrYx on 2011-02-16
> **uRock said:**
> Hello and welcome to the forums.

Unless you are running a server, you don't really need either.

If you have folders that are being shared with Windows machines, then an AV may be warranted. In that case I would use Avast or BitDefender. I haven't used Avast, but I have used BitDefender and I was pleased with it.

If you really feel that you need an intrusion detection, then SNORT is easily install via the Ubuntu Software Center.

Regards,
uRock
Thanks alot!

yeah I figured, but still. One might have evil enemies ;)

I've heard about both Avast and SNORT so I think I'll try em'. 
Furthermore is there any chance that they both will collide and "take  each other out"? I've read something about lock files in Linux, does  that have anything to do with this at all, or is that only when you're  installing things?

Pardon if that's a silly question :D

---

### Post by FlurrYx on 2011-02-16
> **andy8 said:**
> I started using Ubuntu less than a week ago and love it! 
Decided to take windows off completely :D
The thing that drew me here was the understanding that there would be less chance of getting a virus/spy-ware. 
However, you can, like I done download several things to help tame your fears, you have carried forward from windows!

Open **Ubuntu software centre** and type in **KlamAV** you might run into a few problems with the updates so I suggest you read this page: [http://ubuntuforums.org/showthread.php?t=1547713](http://ubuntuforums.org/showthread.php?t=1547713)
 The **replace dophin with 'nautilus' ** worked for me.

Open **Ubuntu software centre** and type in**firestarter** a good firewall.


Open **Ubuntu software centre** and type in **BleachBit** runs a little like ccleaner without the reg cleaner as Ubuntu has no reg!

Andy
Oh! Thanks for the tip and the fast replies :D

---

### Post by uRock on 2011-02-16
You don't want to install Firestarter. It hasn't recieved updates for quite a few years. If you need a firewall, then you can install GUFW via the Ubuntu Software Center or if you don't need to set any special port allowances, then you can just open a terminal and run the following command to activate the already built in firewall, ```
sudo ufw enble
```

If you are using Ubuntu and want the AV that is in the repos for Ubuntu, then search for and install ClamAV, KlamAV is for Kubuntu. I have used this in the past and had false positives.

---

### Post by andy8 on 2011-02-16
> **uRock said:**
> You don't want to install Firestarter. It hasn't recieved updates for quite a few years. If you need a firewall, then you can install GUFW via the Ubuntu Software Center or if you don't need to set any special port allowances, then you can just open a terminal and run the following command to activate the already built in firewall, ```
sudo ufw enble
```

If you are using Ubuntu and want the AV that is in the repos for Ubuntu, then search for and install ClamAV, KlamAV is for Kubuntu. I have used this in the past and had false positives.

Thanks for that, didn't know that. Will give GUFW a go.

---

### Post by uRock on 2011-02-16
> **andy8 said:**
> Thanks for that, didn't know that. Will give GUFW a go.
You will need to uninstall, then purge Firestarter before installing GUFW or there will be problems with configurations.
```
sudo apt-get purge firestarter
```

---

### Post by FlurrYx on 2011-02-16
All this was easier than I thought :)

Avast was kinda Lame, you needed to register your mail and stuff to get a license key- Kinda cheap price to pay though for free-ware I guess :)

---

### Post by uRock on 2011-02-16
> **FlurrYx said:**
> All this was easier than I thought :)

Avast was kinda Lame, you needed to register your mail and stuff to get a license key- Kinda cheap price to pay though for free-ware I guess :)
BitDefender is the same way, but they only give free licenses to Linux users, which I like.

---

### Post by andy8 on 2011-02-16
Thanks done that. Quick question, Could you just remove it from the software centre or is purge better? Also will Avast work with 64bit Ubuntu?

---

### Post by uRock on 2011-02-16
> **andy8 said:**
> Thanks done that. Quick question, Could you just remove it from the software centre or is purge better? Also will Avast work with 64bit Ubuntu?
You have to uninstall and purge Firestarter.

Avast's site seems to only have a 32bit version.

---

### Post by handy on 2011-02-16
**@FlurrYx:** Have a read of this page, it may help bring some security to your understanding of Ubuntu:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You may find many of the other tutorials on the site very helpful also.

All the best.

---

### Post by FlurrYx on 2011-02-17
Thanks! That was a nice read. Many good links as well.

But according to that, Ubuntu seems to be ultra safe which I find hard to believe (probably just an old windows damage)

Yet, the more you know :)

The main thing I found out here is that the Operating system itself is really well configured when it comes to security. Damn I've fallen in love with Linux overall, great community and great people result in a supra great OS

---

### Post by handy on 2011-02-17
> **FlurrYx said:**
> Thanks! That was a nice read. Many good links as well.

But according to that, Ubuntu seems to be ultra safe which I find hard to believe (probably just an old windows damage)

Yet, the more you know :)

The main thing I found out here is that the Operating system itself is really well configured when it comes to security. Damn I've fallen in love with Linux overall, great community and great people result in a supra great OS

I haven't run anti-virus on my Linux boxes ever (well over 5 years now), or our OS X, boxes (over 10 years on the oldest).

Though I did run ClamAV on my Linux IPCop firewall/router box for maybe a year, not that I needed it, just to look at it really & because for some strange reason it didn't slow down our computers(?), I haven't been running ClamAV for over a year now as it was always completely unnecessary here.

You really don't need to worry about anti-virus software unless your Linux box is serving data to Windows machines.

That is the bottom line.

---

