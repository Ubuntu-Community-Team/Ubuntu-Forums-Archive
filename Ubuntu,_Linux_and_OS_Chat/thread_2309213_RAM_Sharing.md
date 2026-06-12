---
title: "RAM Sharing"
date: 2016-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by zergling on 2016-01-08
Hello everyone,

I am opening this thread because I would like to know if is possible to share the System RAM from one PC to another.
This is my configuration

**PC 1**
```

OS: Debian
RAM: 16GB
IP: 192.168.1.50

```

**PC 2 -Odroid-**
```

OS: Ubuntu
RAM: 2GB
IP: 192.168.1.47

```

They are both connected via LAN network with NFS

Is it possible to tell at the **PC 2 -Odroid-** to use the RAM from **PC 1** when available?

I added a swap partition on the PC 2 -Odroid- on a microsd card, but it really sloooooow :(

Bye and thank you in advantage. ^_^

---

### Post by QIII on 2016-01-08
In a word: No.  The hardware doesn't work that way.  Even if it did, you'd not be better off than using swap (or even worse) with even a gigabit ethernet connection. It's actually a much slower transfer rate than the USB3 connection to the drive inside my CloudShell. 

What are you doing on the Odroid (I have an XU4 I use as a web development platform) that consumes that much RAM?  SBCs are not really designed for really heavy lifting.

---

### Post by zergling on 2016-01-08
Hello QIII,

I usually compile crypto wallets and other linux applications.

So, do you suggest to use an external HD via USB 3?

---

### Post by QIII on 2016-01-08
What model of ODROID are you using?

---

### Post by zergling on 2016-01-08
I am using an odroid XU4

The problem about running out of memory occurs when I compile most of the applications by using 4 or more cores.

---

### Post by QIII on 2016-01-08
OK.  Here's what I have done with my XU4 (take a look at my blog, The Left Coast Geek in my signature)

eMMC and microSD are both painfully, painfully slow.  So swap is almost useless.

Your XU4 has a couple of USB3 ports.  The theoretical data transfer rate (limited by the drive, of course) is 5 Gbps.  That's not too far off the SATA rev 3 theoretical rate of 6 Gbps.  Given the mediocre performance of the ARM processor, that's hardly noticeable.  Real-world speed, of course, is a lot less than theoretical.

I have set up my XU4 to boot initially from the SD (you have to, that's how the thing is designed) and then transfer the boot immediately to an HDD one one of the USB3 ports.  The CloudShell pictured in one of my posts on my blog has a USB3 to SATA adapter built in.  The other USB port is used with a panel mount USB port coming out of the side of the case (had to do some mods).

Anyway, what happens is that the OS actually runs on the HDD inside the case -- at the USB3 transfer rate.  That is much faster than either eMMC or SD.  That will get your swap transfers moving along at nearly the rate you would expect in a desktop.

A good, but inexpensive, USB3 HDD enclosure could be used the same way if you have your board in the breeze or in a smaller case.  Run the OS from an HDD, have your swap partition on it and you should improve your performance substantially.

---

