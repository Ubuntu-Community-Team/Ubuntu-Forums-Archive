---
title: "How is the ATI Mobility Radeon 4570 graphics support on 10.04?"
date: 2010-05-16
forum: System76 Support
---

### Post by compu73rg33k on 2010-05-16
I've been looking to purchase a new laptop for the past couple weeks and the System76 Pangolin is on the verge of being put in my cart. My only reservation is the ATI Mobility Radeon HD 4570 graphics support. I've asked around a couple forums and many people have warned against ATI with Linux. My brother has an integrated ATI Radeon HD 3200 GPU and to the best of my knowledge hasn't had any issues with compiz or watching 720p videos. However, I plan on using Compiz and watching 1080p videos on a projector with this Pangolin. Can I get word on the support of the Radeon HD 4570 in Ubunu 10.04? I don't want to deal with video issues and I expect that if the computer ships with the Radeon 4570 + Ubuntu it will work without any issues. I've read of a few issues with this card but all the posts I saw were from a year+ ago.

Is the ATI Mobility HD Radeon 4570 supported well in Ubuntu 10.04? Specifically for Compiz + 1080p video playback? I hope for a quick response, I'm itching to buy it! :-D

---

### Post by compu73rg33k on 2010-05-16
I found this thread which makes me a bit nervous: [http://ubuntuforums.org/showthread.php?t=1476531](http://ubuntuforums.org/showthread.php?t=1476531)

Is there anything I need to worry about? :|

---

### Post by MG37221 on 2010-05-16
Like you, I have always been apprehensive with regard to ATI.  In fact, when I made the change to linux several years ago, I changed from ATI to nVidia for the same obvious reasons.  My Pan7 came with ATI and worked quite nicely.  It shipped with Ubuntu 9.10.  I've since upgraded to 10.04 (clean install), followed the directions posted [_[COLOR="Blue"]here[/COLOR]_]("http://knowledge76.com/index.php/Restoring_Your_System") and everything (compiz, screenlets, everything I need anyway) works perfectly.  These guys (System76) know what they're doing.

I don't boot windows nor play any games so if those are among your goals, somebody else will need to chime in here.  For Ubuntu computing however, I'm a very satisfied customer.

---

### Post by compu73rg33k on 2010-05-16
> **MG37221 said:**
> Like you, I have always been apprehensive with regard to ATI.  In fact, when I made the change to linux several years ago, I changed from ATI to nVidia for the same obvious reasons.  My Pan7 came with ATI and worked quite nicely.  It shipped with Ubuntu 9.10.  I've since upgraded to 10.04 (clean install), followed the directions posted [_[COLOR="Blue"]here[/COLOR]_]("http://knowledge76.com/index.php/Restoring_Your_System") and everything (compiz, screenlets, everything I need anyway) works perfectly.  These guys (System76) know what they're doing.

I don't boot windows nor play any games so if those are among your goals, somebody else will need to chime in here.  For Ubuntu computing however, I'm a very satisfied customer.
I'm actually curious how the Pangolin runs in Windows7 because it'd be nice to dual boot...but really every time I install Windows I only boot into it like once every month or every other month so if it didn't work with Windows I wouldn't lose any sleep.

Thanks for the positive review for this ATI card. I couldn't imagine that they would ship it with a card that didn't work perfectly but given some random issues posted I figured I'd double check for a testimonial.

---

### Post by shebaw on 2010-05-29
I have the same graphics card and I'm pretty happy with it. Installing the proprietary driver on 9.10 almost trashed my desktop and I always experienced tearing when watching 720p movies! But the open source driver on 10.04 is way better than the proprietary driver, I can now watch movies and have all those fancy desktop effects out of the box.

---

### Post by re1d on 2010-05-29
> **shebaw said:**
> I have the same graphics card and I'm pretty happy with it. Installing the proprietary driver on 9.10 almost trashed my desktop and I always experienced tearing when watching 720p movies! But the open source driver on 10.04 is way better than the proprietary driver, I can now watch movies and have all those fancy desktop effects out of the box.

I've heard the same things about ATI/Linux, but recently have read some negatives with regard to nVidia too - guess it all comes down to the driver.

I have a new Pan P7 with 10.04 and all the System76 drivers installed. It plays movies perfectly on that gorgeous screen and the desktop has everything enabled and is fast and smooth. Just my experience, maybe. . . all machines have personalities! But I've had zero problems with 10.04 and the ATI card in my Pangolin.

Good to know the Ubuntu driver works well, too - something to fall back on if problems do crop up. :popcorn:

---

### Post by shebaw on 2010-05-31
> **re1d said:**
> I've heard the same things about ATI/Linux, but recently have read some negatives with regard to nVidia too - guess it all comes down to the driver.

I have a new Pan P7 with 10.04 and all the System76 drivers installed. It plays movies perfectly on that gorgeous screen and the desktop has everything enabled and is fast and smooth. Just my experience, maybe. . . all machines have personalities! But I've had zero problems with 10.04 and the ATI card in my Pangolin.

Good to know the Ubuntu driver works well, too - something to fall back on if problems do crop up. :popcorn:
Does it work well with 1080p hd videos?

---

### Post by MadCookie on 2010-05-31
I have this card, and it works out of the box! To get the ATI control center you will have to install the ati driver that appears in Hardware Drivers.

---

### Post by marrusl on 2010-05-31
ATI video was the single thing that made me apprehensive about getting a Pangolin.  I knew, and personally experienced how much better the NVIDIA binary driver seemed to work compared with ATI's, especially with regard to dual displays.

I have to tell you, so far so great.  Not only have I had no problems on my primary display, I've also had very smooth sailing while driving an external Samsung at 2048x1156.  Heck I didn't even have to disable Compiz.  In the past, regardless of monitor setup, I found that I had to disable Compiz to view movies in full screen using Totem (actually, it would work once per boot but then Totem would segfault the 2nd time, every time).  Mind you that was on openSUSE 11.2, but I have the feeling it was a driver issue.

So far on my Pangolin, I've found no reason at all to disable Compiz, and the ATI control panel seems to give nearly as good "plug and play" support as `nvidia-settings`.

One thing I read recently that also impressed me is that Phoronix seems to have determined that ATI's proprietary Catalyst driver takes almost no performance hit with Compiz enabled, unlike the NVIDIA driver:
[http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1](http://www.phoronix.com/scan.php?page=article&item=compiz_speed_test&num=1)

There must be some horrible awful bug I haven't hit yet... but so far I'm very happy.  Dare I say, almost GLAD.  Wasn't expecting that.

Great job by s76 and ATI/AMD.

---

