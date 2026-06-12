---
title: "Firefox and Chromium ..... both are getting bloated"
date: 2014-02-24
forum: The Cafe
---

### Post by linuxyogi on 2014-02-24
Hi,

I assembled my PC in 2010. Since then I have tried most of the DEs. All used to run quite fast but now the latest version of KDE runs too slow so use MATE and sometimes XFCE. Both performs well.

The issue is Firefox takes a long time to launch and if I multi task with FF and Chromium the system becomes very slow. 

If FF and Chromium keeps getting resource hungry like this I will have to look for alternatives soon.

I know there are other open source browsers and I have tried them but none of are as nice as FF.

I am not a fan of Chromium. I use it coz I have 2 facebook accounts.

Its tough to beat FF's superiority for 2 reasons, a) security (which is further enhanced with addons like noscript, adblockplus, etc) and b)tons of highly useful addons.

I wanna ask ask guys who have similar specs like mine. What's your plan ? Is  upgrading the only solution ?


Athlon 64X2 5600+ Ram: 2GB

---

### Post by tgalati4 on 2014-02-24
Since you have 2GB of RAM, try setting up firefox to use a RAM disk.  Or buy a faster spinning disk or SSD.  Yes, the browsers are getting fat, but that is because the plug-in frameworks have gotten bigger, tab containers and multi-threading add to the bloat, not to mention html5 engine.

---

### Post by SurfaceUnits on 2014-02-24
Try 
         [img]http://i-cdn.phonearena.com/images/articles/97650-thumb/firefox-os-mobile.jpg[/img]

---

### Post by linuxyogi on 2014-02-24
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=241895")**@[[B][COLOR=#000000]tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") [/B]Thanks lot for the suggestion. I just configured both FF and Chromium to use ramdisk and they are running quite faster in comparison.

@**SurfaceUnits** Sorry .... what are you suggesting ? You want me to install the Firefox OS on desktop ?

---

### Post by monkeybrain20122 on 2014-02-25
Not sure if both are getting bloated or your machine is getting old.  Can't help it, it rhymes. :)

---

### Post by linuxyogi on 2014-02-25
> **monkeybrain20122 said:**
> Not sure if both are getting bloated or your machine is getting old.  Can't help it, it rhymes. :)

My hardware is definitely getting old but the fact is the specs are not decreasing by any chance. So by that logic I guess the browsers are demanding more resources than they used to.

BTW its not only the browsers. I was facing issues while using Chromium, FF and Thunderbird. I found a easy workaround by switching to Clawsmail.

---

### Post by lykwydchykyn on 2014-02-25
You can try midori, it's not my favorite browser but it's a bit lighter.  There are a few other "minimalist" browsers out there that might perform a bit better, like jumanji, uzbl, luakit, or conkeror.  Ultimately they all depend on either webkit or gecko to render pages, though; so I don't know how much faster they'll be.

Honestly I think part of the problem is that "web browsing" isn't what it used to be.  There's more and more JS, more images, more video, more webGL.  Remember when blinking text was a cool feature?  Maybe you don't...

---

### Post by monkeybrain20122 on 2014-02-25
midori is light but many sites don't show properly, at least when I tried it a year ago, now it may have improved. How about Opera? I used it a bit but stopped around Ubuntu 11.04 when it became very buggy, it may have improved now too.

---

### Post by SeijiSensei on 2014-02-25
I suggest increasing the physical memory from 2 GB to 4-8 GB.  If you have an empty slot that supports 4 GB, I would buy a single 4 GB stick and expand the memory to 6 GB overall.

Software developers, especially developers of large, multi-platform applications, seem intent on eating up all the memory available to them as technologies decline in price.  

Because Linux uses nearly all unallocated memory as a dynamic disk cache, expanding memory provides two distinct benefits -- more room for the applications themselves, and faster disk access via the cache.  Applications that write large temporary files to disk especially benefit from caching.  Using lsof, this instance of Firefox has opened about 50 files in my home directory; the separate plug-in container task owns a few more.  If I watch a Flash video, that number increases substantially.

---

### Post by buzzingrobot on 2014-02-25
Adding 2-4 gigs of RAM would probably pay dividends.

Midori is the default browser in Elementary OS. The folks over there might have posted some useful advice.

---

### Post by Tar_Ni on 2014-02-25
From my personal experience, Adblock Plus does slow down the browser considerably. Just try firefox without it and you'll immediatly see the difference.

You should consider using Blue Hell Firewall, a lightweight adblocker for firefox. You may gain some loading speed.

[https://addons.mozilla.org/fr/firefox/addon/bluhell-firewall/](https://addons.mozilla.org/fr/firefox/addon/bluhell-firewall/)

Else you could give a try to seamonkey, I heard it's lighter on older hardwares than firefox. I am not sure how much though.

---

### Post by linuxyogi on 2014-02-26
Where I live DDR 2s ate very tough to find and even if I find one they are super expensive. I remember that the same thing happened with DDR 1 when DDR 2 was introduced.

I have installed Elementary OS so in a way I have downgraded from 13.10 to 12.04. AFAIK LTS releases are lighter than the regular ones.

Midori is the default browser so I am using it in place of Chromium. Last time I used Midori it failed to zoom Facebook properly but that issue is gone now.

Multitasking with FF and Midori is working . The only issue is the FF launching time. Its taking about half a minute but once its loaded it works just fine.

I guess I will have to cope with that. Opera is closed source so I dont wanna use it. I tried disabling AdblockPlus but frankly that didnt make any difference. I am pretty okay with the current setup and 12.04  will reach EOL  in 2017 so this install is good for 3 more years.

---

### Post by kurt18947 on 2014-02-26
Once 14.04(LTS) has been released for a few weeks,  it might be worth trying it.  14.04 seems faster than 12.04 to me.  I believe there has been some speed optimization as a result of Canonical's efforts in the mobile arena.  I have two machines of similar performance, Core2Duo 1.5ghz Thinkpad/w 2GB. RAM & AthlonII X2 desktop w/4 GB. RAM.  I have no plan to upgrade due to performance issues.  I haven't tried running Firefox & Chromium at the same time though I have both installed.

Re purchasing additional RAM, is Ebay or something like it an option for you?  DDR2 costs more than DDR3 there as well but the price difference is not as great as at retail.  I've purchased RAM on Ebay but made sure it was returnable.  As soon as I received it, I installed it and ran memtest86 for a few hours.  The RAM tested with no errors and seems to work with no problem.

---

### Post by SeijiSensei on 2014-02-26
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145098](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145098)

2 x 1 GB DDR2 667:  $50

---

### Post by lykwydchykyn on 2014-02-26
> **linuxyogi said:**
> . The only issue is the FF launching time. 

Do you see a lot of disk activity when firefox launches?  That could be the bottleneck.  You could try installing something like "preload".  Preload loads up libraries for your most-used applications in the background, so they have less to load up into RAM when you actually launch them.  The cost, of course, is RAM.

It's only worthwhile if you launch a small set of applications often, have a slowish disk,  and aren't hurting for RAM.  Might be worth a try, though, you can always uninstall it.

---

### Post by Tar_Ni on 2014-02-26
2GB RAM is more than enough to perform basic tasks such as web browsing, word processing, watching videos and listening musics which is what most people use a PC computer for.

For optimal performance in multi tasking you should consider using a lightweight OS alternative such as Xubuntu or even Lubuntu. If you do no more than that, I do not think you really need to pay for extra RAM.

Depends on you and what you do with your computer. ;)

We have a laptop with 4GB RAM at home and Firefox is not so fast to launch as well. The add-ons are the main reason why it's slower than he should be. Especially AdblockPlus which we no longer use but instead Blue Hell Firewall (30KB instead of 700KB). It's making a small but noticable difference.

---

### Post by linuxyogi on 2014-02-26
Preload is already installed. Removed adblockplus and installed Bluhell Firewall.

---

### Post by vasa1 on 2014-02-27
> **monkeybrain20122 said:**
> ... How about Opera? ...
From what I understand there's no recent Opera for Linux after they switched to WebKit/Blink.

---

### Post by vasa1 on 2014-02-27
> **linuxyogi said:**
> Preload is already installed. Removed adblockplus and installed Bluhell Firewall.
Do you have slow start with a clean Firefox profile?

---

### Post by mattlach on 2014-02-27
As software gets more mature, and computers get more capable, it is pretty typical for the software to expand to make better use of the machine.

No offense, but the computer you are running on is somewhat stone age by modern standards.

An SSD instead of a hard drive and a RAM upgrade would do you a lot of good.  (I usually put at least 8 gigs in all of my builds.  Even my HTPC has 8 gigs of RAM).

Truth be told, before buying RAM though, I would just upgrade to something newer, as the DDR2 in your system is getting more and more expensive with time, as the production volumes have gone down as it is a mostly obsolete technology.   

These days DDR3 RAM is dirt cheap, and it makes no sense to go small.   Due to all the VM's I run I put 32gigs in mine.

---

### Post by linuxyogi on 2014-02-27
> **vasa1 said:**
> Do you have slow start with a clean Firefox profile?

Yes its almost the same with a new profile.

---

### Post by motang on 2014-02-28
I have a pretty old notebook that I have done my share of DE hoping once Unity became a bloated and sluggish.  But recently I have installed Ubuntu 14.04 daily builds, and Unity is snappy and very fast. Everything just pops and it a joy to use.  My notebook's spec is 1.6 GHz AMD64 single-core processor with 3GB of RAM.  One trick I do is install z-ram on it.  You can do this by running the command ```
sudo apt-get install zram-config
```

Reboot you machine and you wll be a space that is managed by the OS for disk RAM.  

You can check to see if it running and being used with this command ```
cat /proc/swaps
```

Hope this helps you.


[source]("http://www.webupd8.org/2011/10/increased-performance-in-linux-with.html")

---

