---
title: "kindle book reader app (without a kindle)"
date: 2011-06-14
forum: The Cafe
---

### Post by memilanuk on 2011-06-14
Hello,

I have a few books in my Amazon Kindle account, and local installs of the Kindle book reading app on my PC laptop, my desktop PC, and my Macbook.  Thus the books are available to me thru the Kindle reader app no matter which machine I'm at or have with me.  Now that my PC laptop is dual-booting Ubuntu 11.04, I'd like to be able to connect to my Kindle account to read those same texts.  Problem is, Amazon doesn't seem to make a Kindle reader app for Linux, and I don't have a 'physical' Kindle device - so how do I connect to Amazon and d/l those texts to my Ubuntu computer for reading?

I though Calibre might be able to do it, as everyone seems to recommend it as the go-to Kindle app for Linux, but if it has the ability to connect to my Amazon account, its well hidden...

Any help or suggestions would be welcome...

TIA!

Monte

---

### Post by LowSky on 2011-06-14
Tested and Works

[http://www.redshirtlinux.com/?p=163](http://www.redshirtlinux.com/?p=163)

---

### Post by Eldera on 2011-06-14
I was able to get the Kindle for PC app to work with Lucid 10.04 in Wine version 1.3.21 which I downloaded from the wine website

[http://www.winehq.org/download](http://www.winehq.org/download)

Following these instructions

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

After installing this version of wine, all I had to do was download the Windows version of Kindle for PC from Amazon's site, right-click and select open with Wine.No tweaks.

I notice the Wine version is now 1.3.22, but it might still work. Worth a try.

I previously tried installing Kindle for PC with a version of Wine in the Ubuntu repository (don't remember the number) and It did not work.

Happy Reading, Eldera

PS I have found the various versions of wine to be inconsistent as to what they will and will not do. I have a tiny separate partition on my computer set up with an older version of Wine so that I can run a Mobipocket reader which will not run in the newer versions of Wine. Go Figure.

---

### Post by kabloink on 2011-06-14
On my Debian wheezy desktop after installing wine 1.3.22, both the latest Nook and Kindle Window applications appear to work. It should work with Ubuntu with the same wine version.

No tweaks, just a straight install using wine.

I only tested it by downloading already purchased books and opening the book in the application.

---

### Post by akavir on 2011-06-14
I realise it doesn't solve the imidiate problem, but start buying books from Google books.  They are generic pdf.  I love being able to read Google books on any platform with a pdf reader,(which is basicly everything!)

---

### Post by timZZ on 2011-06-14
Not constructive: You are the first person I have come across who has an amazon kindle account but not a kindle.

---

### Post by LowSky on 2011-06-14
> **timZZ said:**
> Not constructive: You are the first person I have come across who has an amazon kindle account but not a kindle.

I dont own own either.. i use it on my android tablet and phone

---

### Post by Eldera on 2011-06-14
[quote=timZZ]Not constructive: You are the **first** person I have come across who has an amazon kindle account but not a kindle.[/quote]

You did not count carefully. So far in this thread there are **four** people who are using the Kindle app without a Kindle.

Edit: For curiosity I just installed Wine from the site in my previous post and Kindle for PC from Amazon.com to Natty 11.04. Working install; no tweaks necessary.

(I am dual booting a couple of Lucid partitions and a Natty partition until I get comfortable with Natty) That is how I learn things. To each his own.

---

### Post by memilanuk on 2011-06-14
Thanks, guys.  I'll install WINE and give it a try sometime in the next day or so.  It's probably been 10+ years since I tried WINE; I'm assuming it works somewhat better nowadays? ;)

---

### Post by memilanuk on 2011-06-15
Sweet... added the Ubuntu WINE ppa, installed WINE, and one of the default apps available to install was... Kindle ;)

Thats two or three books I don't have to pack on my upcoming vacation!

Thanks,

Monte

---

### Post by 3rdalbum on 2011-06-15
New idea: Install the Android emulator and install the Android Kindle program directly from Amazon's market.

---

### Post by whwilliams on 2011-09-25
> **memilanuk said:**
> 
I have a few books in my Amazon Kindle account, and local installs of the Kindle book reading app on my PC laptop, my desktop PC, and my Macbook.  Thus the books are available to me thru the Kindle reader app no matter which machine I'm at or have with me.  Now that my PC laptop is dual-booting Ubuntu 11.04, I'd like to be able to connect to my Kindle account to read those same texts.  Problem is, Amazon doesn't seem to make a Kindle reader app for Linux, and I don't have a 'physical' Kindle device - so how do I connect to Amazon and d/l those texts to my Ubuntu computer for reading?


Just an update for those who are looking for a Kindle reader for Linux and don't like installing wine or have had problems installing from wine. 

Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using Chrome. 

[https://read.amazon.com/](https://read.amazon.com/)

Enjoy! :D
Howard

---

### Post by gregb49 on 2011-09-25
> **whwilliams said:**
> Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using ChromeThanks. Having failed with wine 1.2 and 1.3.28 and Kindle reader, the Cloud Reader works well.

---

### Post by Dennis N on 2011-09-25
> **whwilliams said:**
> 

Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using Chrome. 



Works with Chromium too, as you might expect.

---

### Post by earthpigg on 2011-09-26
> **whwilliams said:**
> Just an update for those who are looking for a Kindle reader for Linux and don't like installing wine or have had problems installing from wine. 

Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using Chrome. 

[https://read.amazon.com/](https://read.amazon.com/)

Enjoy! :D
Howard

that is phenomenal, thank you for sharing this.

---

### Post by Copper Bezel on 2011-09-26
Indeed. This is excellent. I had to disconnect my Wifi just to prove to myself that it was actually working offline. = D So I have a Kindle now. Yay.

---

### Post by needhelpplease on 2011-09-26
> **Eldera said:**
> I was able to get the Kindle for PC app to work with Lucid 10.04 in Wine version 1.3.21 which I downloaded from the wine website

I also got the Windows Kindle app to work perfectly within Wine.  I'm on 11.04 and using the latest version of Wine 1.3, installed from the Ubuntu package manager (apt-get install wine13).  Works perfectly.

---

### Post by Eldera on 2011-09-27
The installation of my Kindle for PC in Wine later broke during a routine update of Wine. I had another Kindle for PC on a different partition, so did not bother to troubleshoot the broken one. Wine can be undependable. It is good to know that an alternative, the Cloud App, is available.

Thank you, whwilliams

---

### Post by duranl on 2011-10-04
> **whwilliams said:**
> Just an update for those who are looking for a Kindle reader for Linux and don't like installing wine or have had problems installing from wine. 

Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using Chrome. 

[https://read.amazon.com/](https://read.amazon.com/)

Enjoy! :D
Howard


This just saved me 80 dollars on a textbook!  Thanks!  :guitar:

---

### Post by CrystalWitch on 2012-03-13
> **whwilliams said:**
> Just an update for those who are looking for a Kindle reader for Linux and don't like installing wine or have had problems installing from wine. 

Amazon has a Kindle Cloud Reader available so you can view your Kindle books on or off line using Chrome. 

[https://read.amazon.com/](https://read.amazon.com/)

Enjoy! :D
Howard

Thank you - just what I needed!  :D

---

