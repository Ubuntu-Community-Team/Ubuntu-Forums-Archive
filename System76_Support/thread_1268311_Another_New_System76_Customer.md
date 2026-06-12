---
title: "Another New System76 Customer"
date: 2009-09-16
forum: System76 Support
---

### Post by HotShotDJ on 2009-09-16
I finally pushed the "add to cart" button and submitted my order for a Pangolin.  I may need sedatives to get any sleep between now and when it arrives in my office.  Rather silly at my age, but I'm excited about it.

I cannot thank Tom Aaron enough for his pre-sales help.  Normally I'm very nervous when I drop this amount of money on any purchase, but I'm feeling alarmingly comfortable with my decision to buy a PanP5.

For the record, here are the specs that I ordered:

WSXGA+ High-Res Screen (YEAH! [They had one left]("http://ubuntuforums.org/showthread.php?t=1257479"))
Core 2 Duo P8700
4 GB RAM
320 GB 7200 RPM Hard Drive
Intel Wi-Fi Link 5300

If only they sold [THIS]("http://shop.canonical.com/product_info.php?products_id=123") laptop bag, I might have added it to my order as well. :)

---

### Post by samalex on 2009-09-17
Congrats!  And awesome you were able to get the upgraded display, that honestly makes all the difference.  

When I ordered my system it took 7 days, as they estimated, from order to ship, then another 3 to make it to me.  So I bet you'll have it next week sometime if things are still the same on their end.

As for the bag, the one you linked to from Canonical looks awesome, but I've always been partial to the [Timbuk2]("http://www.timbuk2.com") messenger bags.  [Here's a link]("http://twitpic.com/i1n9g") to mine which I bought about 6 years ago for my iBook, and what's nice is my PanP5 fits great!  I'm glad I went with the larger bag back then :)  They're not inexpensive, but I figured it's worth the cost to be sure it's protected, and the number of times I've dropped or bumped the bag it's always left my laptop unharmed, even when traveling.

Post some updates when your laptop comes in though, and any questions after it arrives.  

Take care..

Sam

---

### Post by HotShotDJ on 2009-09-24
Well... We're at the 5 business day (7 real-life day) mark, and my Pangolin is still in "Manufacturing."  Of course, they DID say 10 business days (14 real-life days) so I have absolutely nothing to complain about. :)

Is it just my imagination, or does my Dell Inspiron E1505 somehow KNOW it is about to be replaced?  It seems to have slowed down.  Until the very day that I placed my order, it ran my software adequately, if not optimally.  Now, I can't seem to get any work done.

Nah... must be psychological (those who know what I do for a living may stop laughing out loud now!).

/me mutters to self... "I wants my precious...it's mine...don't bother Mandy or Tom... don't bother Mandy or Tom... they SAID 10 business days... my preciousssssss...get a grip on yourself, man!"

---

### Post by macabrem on 2009-09-24
Yeah, the waiting is the hardest part.  My Starling has shipped but now I am waiting for UPS!  I can hardly stand the wait.  :)

---

### Post by Scotty Bones on 2009-09-24
> **macabrem said:**
> Yeah, the waiting is the hardest part.  My Starling has shipped but now I am waiting for UPS!  I can hardly stand the wait.  :)

Yep, like a crack addict who can't get their fix! :) I wasn't able to sleep for two days after placing the order for my precious...uhh, I mean PanP5. (Yes, I've been accused of that)

In my case, there was a week delay in manufacturing. To make things worse; the day it was to arrive, literally 20 minutes before the UPS truck usually swings by my house, we had a really bad storm with winds clocked at 106 mph come through that delayed the shipment 3 more days. The most painful part: although the power was out for two days, I had purchased a car adapter for it...doh!

I absolutely love this thing. And let me say, the screen upgrade is definitely worth it. Oh, did I mention I love this thing.

---

### Post by japhyr on 2009-09-24
Ditto on the WSXGA+ screen making all the difference.

---

### Post by HotShotDJ on 2009-10-07
> **macabrem said:**
> Yeah, the waiting is the hardest part.  My Starling has shipped but now I am waiting for UPS!  I can hardly stand the wait.  :)ARGH!!!!!  I've watched it drive past me (figuratively speaking) twice on [PackageMapping]("http://www.packagemapping.com"). First it drove right past on its way to Shrewsbury, MA.  Now, it went right past me again (in the OTHER direction) to get to Watertown, CT.   It should be at the university's mail room sometime Wednesday morning.  I'm SUPPOSED to wait for them to deliver it to the department secretary on Thursday morning.  Yeah... right... no chance of THAT happening. :)

---

### Post by HotShotDJ on 2009-10-07
I received my PanP5 today -- unfortunately, I couldn't show it off at work because it wouldn't boot properly. :confused:   All I could get was low-res mode and an icon on the gnome desktop that said something to the effect of "Prepare to Ship to Customer"  (I didn't write down the exact wording).  When I clicked on it, it asked for the Administrator's password, which I didn't know, since I hadn't set it up.

I suspect somebody forgot a step for setting up the hard drive before shipping it.  No big deal... I just popped in a Jaunty Desktop AMD64 install disk and did a complete install and then restored using the System76 Driver.  The only disappointment was that I wasn't able to show off the coolness of a computer with Ubuntu pre-installed.

Other than that, this laptop pretty much rocks.  I'll have to play with it for a few days to get a good feel for it.

---

### Post by thomasaaron on 2009-10-08
Yep, it sounds like somebody forgot to click the "Prepare for End" User icon. I could've given you the password! (...but I shouldn't have had to, right?)

Anyway, make sure you download and install the System76 Driver. Read this...

> The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

Also, make sure you go to System > Administration > Hardware Drivers and activate the recommended nVidia driver.

---

### Post by HotShotDJ on 2009-10-08
> **thomasaaron said:**
> Yep, it sounds like somebody forgot to click the "Prepare for End" User icon. I could've given you the password! (...but I shouldn't have had to, right?)I thought about calling or emailing you, but it really was one of those "no harm - no foul" situations.  I knew I was going to reinstall anyway (to get ext4 and to increase the swap to 1.5 x RAM -- I'm still pretty old-school on that).
> **thomasaaron said:**
> Anyway, make sure you download and install the System76 Driver. Read this... Also, make sure you go to System > Administration > Hardware Drivers and activate the recommended nVidia driver.The first thing I did was carefully read the "Restoring Your System" instructions and followed it to the letter.  It worked as advertised.  I was also able to get easily get the proper nVidia driver installed and got it working perfectly with my external monitor.  The irony of that is that my external monitor looks HORRIBLE next to the laptop monitor -- nothing wrong with the external monitor or settings, its just this WSXGA+ laptop monitor is absolutely spectacular!

There are a couple of things that I haven't been able to work out (finger print reader, suspend when I close the lid on battery power), but I'll do a little more searching and start a new thread if I need help on those.

---

### Post by thomasaaron on 2009-10-09
```
I knew I was going to reinstall anyway (to get ext4...
```

If you have any filesystem stability problems, suspect the ext4 first. See...

[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
```

...I haven't been able to work out (finger print reader, suspend when I close the lid on battery power)... 
```

Someone else told me the fingerprint reader tutorial on the wiki wasn't working properly. I'll try to check that out today.

As for suspending on lid close, I assume you have set it up to do so via System > Prefs > Power Management?

Will it suspend via the shutoff icon?

---

### Post by HotShotDJ on 2009-10-09
> **thomasaaron said:**
> If you have any filesystem stability problems, suspect the ext4 first.Yes.  I've been following the saga of ext4 and will have only myself to blame if I run into issues (I'm meticulously backing up data and keeping critical files on an external drive until Karmic is released)
> **thomasaaron said:**
> As for suspending on lid close, I assume you have set it up to do so via System > Prefs > Power Management?

Will it suspend via the shutoff icon?Yes, I have it set up to suspend when the lid is closed via System -> Preferences -> Power Management.  I have tested both Suspend and Hibernate using the shutoff icon and they both work as expected.  I read that the issue is related to how the kernel is compiled in Jaunty and that suspending via the laptop lid is working again under Karmic, so I have filed that issue under "wait for Karmic." However, if you know anything else about getting it to work with Jaunty, that would be great.

---

### Post by Aggzza on 2009-10-30
is the manufacturing plant in colorado? or somewhere else?

why i buy one it'll ship to california "by ground"

---

### Post by thomasaaron on 2009-10-30
Our manufacturing facility is in California.

---

