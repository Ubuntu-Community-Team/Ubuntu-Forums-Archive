---
title: "Finally making the jump to 10.04..."
date: 2010-06-30
forum: System76 Support
---

### Post by samalex on 2010-06-30
Hi Everyone,

Last week I ordered a [1TB USB drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136469") from NewEgg, which should hopefully arrive today or tomorrow, so this weekend I've set aside some time to backup everything and install 10.04 from scratch.  

So my PanP5 will finally be running the 'latest and greatest' of Ubuntu :)  Just to double-check, the biggest thing after installing Ubuntu and all updates is to download the latest driver package from [http://planet76.com/repositories/?](http://planet76.com/repositories/?)  After that is there anything else I'll need to do?

Just double-checking for the sake of paranoia since this is my main system and once it's down I'll have no simple way to get online until it's back up.

Also there had been some problems reported with suspend and bluetooth in other threads, but looking back I didn't find any solutions, though I could've overlooked them.  Have these been resolved with updates from either Ubuntu or System76?  Just curious.  

Thanks again --

Sam

---

### Post by isantop on 2010-06-30
That's right. Fresh install, then install updates, then install the System76 Driver. Don't forget to click the restore button in the restore tab to get everything up.

Also, about the issues you mentioned. I believe they're all ironed out with the latest updates. You'll have to check, and may need proposed and backports enabled to install them, but I believe everything is good.

---

### Post by Eldera on 2010-06-30
The panp5 still has the NVidia graphics card, does it not? If so, and you want the propriatary driver System > Administration > Hardware Drivers.

Also, I installed the restricted extras from [http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats) after doing what Isantop said: Install, update, 76 driver, nVidia driver, restricted extras. Worked very nicely on the panp4. Hope the panp5 does as well. Good Luck.

Edit: I don't use suspend or Blutooth, so can't comment on those.

---

### Post by marshmallow1304 on 2010-07-01
When I installed Lucid (a couple weeks after launch), I had to install the latest kernel from backports to fix bluetooth.  I've had a couple newer kernels since then (not from backports), so bluetooth should work fine after running updates.

---

