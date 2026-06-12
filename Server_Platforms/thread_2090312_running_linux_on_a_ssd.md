---
title: "running linux on a ssd"
date: 2012-12-01
forum: Server Platforms
---

### Post by Vegan on 2012-12-01
any problems running the latest releases of Ununtu off a SSD for a web appliance?

the standard LAMP stack with SAMBA is what I use

:guitar:

---

### Post by rubylaser on 2012-12-02
Nope, SSDs work great. The [Arch Linux Wiki]("https://wiki.archlinux.org/index.php/Solid_State_Drives") has a bunch of good tips.

---

### Post by Vegan on 2012-12-02
I wonder if Linux can use a SSD and a HD in a hybrid setup so that logs etc can live on the hard disk and the invariant programs can live on the SSD

this is probably the best bet until SSD technology can deal with the wearout problem.

---

### Post by darkod on 2012-12-02
The wearout problem was a big problem in the very first generations, which you probably won't buy now if we are talking about fairly recent manufacturing dates.

After all, most manufacturers give 3 years warranty. If it fails, you get a new one. The biggest problem might be data loss, but you should have regular backups anyway.
And when it reaches 3 years of age, you will probably want a new one in most cases.

As for SSD + HDD setup, you probably know that linux works with mount points and is extremely flexible. Put what ever you want, where ever you want it. No problem... :)

---

### Post by haqking on 2012-12-02
> **darkod said:**
> The wearout problem was a big problem in the very first generations, which you probably won't buy now if we are talking about fairly recent manufacturing dates.

After all, most manufacturers give 3 years warranty. If it fails, you get a new one. The biggest problem might be data loss, but you should have regular backups anyway.
And when it reaches 3 years of age, you will probably want a new one in most cases.

As for SSD + HDD setup, you probably know that linux works with mount points and is extremely flexible. Put what ever you want, where ever you want it. No problem... :)


an SSD is really a glorified USB thumb drive, i have never had one of those fail and they are in and out of various machines here and there all the time.

I have had some for 10 years or so, one of which has been i the washing machine twice and still work, though i dont think the warranty will cover it if i phone up about my SSD and said it went through a spin cycle...LOL

SSD and HDD work fine there is no difference to the OS, I use 2x256 GB SSD along with with a few HDD for data and all work awesome.

There are some good things to do if not already such as enable trim, I personally move /tmp to memory which also speeds up firefox which is handy and various other SSD enhancements which can be made to improve longevity and performance.

Peace

---

### Post by Vegan on 2013-01-07
how can I move /tmp to RAM, I would love to see the browser get all the help it can get

---

### Post by haqking on 2013-01-07
edit /etc/fstab

```
tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
```


to enable FF to use /tmp

[http://smallbusiness.chron.com/set-ram-cache-firefox-41282.html](http://smallbusiness.chron.com/set-ram-cache-firefox-41282.html)

---

### Post by MSPdwalt on 2013-01-07
> **haqking said:**
> edit /etc/fstab

```
tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
```


to enable FF to use /tmp

[http://smallbusiness.chron.com/set-ram-cache-firefox-41282.html](http://smallbusiness.chron.com/set-ram-cache-firefox-41282.html)

This is cool, is there a limit on how large that ramdisk can grow to?

---

### Post by haqking on 2013-01-07
> **MSPdwalt said:**
> This is cool, is there a limit on how large that ramdisk can grow to?

[https://www.kernel.org/doc/Documentation/filesystems/tmpfs.txt](https://www.kernel.org/doc/Documentation/filesystems/tmpfs.txt)

---

### Post by spynappels on 2013-01-07
I'm also intending to do a complete re-install on to a 128GB SSD for my work laptop, I currently use about 30GB of the 320GB HDD in there , so space will not be an issue.

@Haqking: Can you give some details on enabling trim in Ubuntu?

---

### Post by haqking on 2013-01-07
> **spynappels said:**
> I'm also intending to do a complete re-install on to a 128GB SSD for my work laptop, I currently use about 30GB of the 320GB HDD in there , so space will not be an issue.

@Haqking: Can you give some details on enabling trim in Ubuntu?

trim = discard

for example

from /etc/fstab
```

UUID=2e19524f-b028-4ef3-93a5-bed6757708fc /               ext4    defaults,noatime,discard,errors=remount-ro
```

see here for more information:

[https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu](https://sites.google.com/site/lightrush/random-1/howtoconfigureext4toenabletrimforssdsonubuntu)

[https://www.youtube.com/watch?v=9kl0bYLFXSg](https://www.youtube.com/watch?v=9kl0bYLFXSg)

---

### Post by spynappels on 2013-01-07
Great, thanks!

---

### Post by Pjotr123 on 2013-01-07
You may find my how-to for SSD's in Ubuntu helpful:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

My desktop PC has only an SSD for hard drive, and it works fine (and it's fast as lightning). :)

---

