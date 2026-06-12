---
title: "No Wireless in Starling"
date: 2010-05-24
forum: System76 Support
---

### Post by Ian505 on 2010-05-24
I followed the instructions on [this]("http://ubuntuforums.org/showthread.php?t=1464846") sticky to the letter (after installing the System76 drivers and finding I lost wireless functionality) and am now again with a netbook with a fresh install of UNR - sans Wifi. I can connect via wired connection (that's how I updated the machine prior to installing the driver) but that's all. The NetworkManager applet doesn't act as if a wireless device exists on the machine at all.

Also, in case it is relevant, I don't get a splash screen at bootup- just a blinking underscore. After a while it moves to the desktop without much of a problem, but it is odd.

OS: Ubuntu Netbook Remix 10.04
System76 Driver: 2.4.9

Any ideas?

Thanks!
Ian

---

### Post by thomasaaron on 2010-05-25
Please establish a wired connection. Then open a terminal and run this command...

```
sudo apt-get install build-essential
```

Then run your System76 Driver again.

Then reboot.

---

### Post by Ian505 on 2010-05-25
Tried that, but it appears everything 76 is down. System76.com, Planet76.com... all inaccessible and unresponsive to pings.

-Ian

EDIT: Tried again today, with Planet76 up, and it worked! Thank you!

Now, would you mind explaining why that worked? I am trying to learn as much as possible so I can be of more help to those I know who are considering switching to Ubuntu.

---

### Post by thomasaaron on 2010-05-26
Sure.

We just found a bug in the System76 Driver. In order to compile the wireless driver for the Starling, it requires a package called build-essential.

However, the latest drive does not install that package when you install the driver -- an oversight on our part. (Very sorry.)

So, when you ran the driver previously, even though it looked like it worked, it didn't compile the driver.

---

