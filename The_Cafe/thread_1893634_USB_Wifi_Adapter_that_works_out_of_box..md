---
title: "USB Wifi Adapter that works out of box."
date: 2011-12-10
forum: The Cafe
---

### Post by donniezazen on 2011-12-10
Are their any USB wifi adapters that will require no specific installation but will have drivers automatically installed with Ubuntu installation?

Thanks.

[http://www.amazon.com/s/ref=nb_sb_ss_i_0_6?url=search-alias%3Daps&field-keywords=wifi+adapter&sprefix=wifi+a](http://www.amazon.com/s/ref=nb_sb_ss_i_0_6?url=search-alias%3Daps&field-keywords=wifi+adapter&sprefix=wifi+a)

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=-1&IsNodeId=1&Description=wifi%20adaptor&bop=And&Order=REVIEWS&PageSize=20](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=-1&IsNodeId=1&Description=wifi%20adaptor&bop=And&Order=REVIEWS&PageSize=20)

PS:Sorry if it's a repost. Other threads look really old.

---

### Post by Thewhistlingwind on 2011-12-10
For which version of Ubuntu? Theres been quite a few devices added since 10.04.

My wireless adapter that didn't work in 10.04 is now supported.

---

### Post by donniezazen on 2011-12-10
> **Thewhistlingwind said:**
> For which version of Ubuntu? Theres been quite a few devices added since 10.04.

My wireless adapter that didn't work in 10.04 is now supported.

I have a Dell Inspiron E1505. It's hooked up to my TV and it's LCD does not work. So, I was thinking about removing the LCD (which has wifi antenna) and permanently hook the laptop to the TV. Last time i checked bcmwl-kernel-source version 100 does not work with it but version 60 works fine. It is just too much hassle to make it work. I am thinking about running XBMC front-end on Ubuntu-Server Natty or Oneiric.

[Medialink - Wireless N USB Adapter]("http://www.amazon.com/Medialink-Wireless-Adapter-802-11n-Compatible/dp/B002RM08RE/ref=sr_1_1?ie=UTF8&qid=1323552021&sr=8-1") has a handful of Ubuntu review mostly working out of box.

Thanks.

---

### Post by Thewhistlingwind on 2011-12-10
> **donniezazen said:**
> [All that stuff you said]
  Thanks.

EDIT: Oh, you said it at the end.

Well, I know that my USB wireless adapter works. (Linksys WUSB100 ver.2) And since I've never used it on this machine that I can remember, I'm assuming that the support is OOTB.

In 10.04 however, I couldn't even get it to work with NDISwrapper.

---

### Post by beew on 2011-12-10
[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

Nothing to install, just plug in and I am online (it has a mini cd with the Windows drivers, but in Linux it works ootb) Works on 10.04, 10.10 and 11.04. Never use it with 11.10 but I think it should work.

---

### Post by donniezazen on 2011-12-10
> **beew said:**
> [http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

Nothing to install, just plug in and I am online (it has a mini cd with the Windows drivers, but in Linux it works ootb) Works on 10.04, 10.10 and 11.04. Never use it with 11.10 but I think it should work.

It's not available anymore and is a G router.

---

### Post by Dennis N on 2011-12-10
I've used this one - it works 'out of the box':

[Belkin Wireless G MIMO]("http://www.belkin.com/IWCatProductPage.process?Product_Id=277475")

---

### Post by lancest on 2011-12-10
Using one now in fact. Works OFTB
TP-LINK TL-WN322G+
(TL-WN422G v2 802.11g [Atheros AR9271])

---

### Post by F.G. on 2011-12-10
i've used the rt73, rtl8187 (eg the ALFA AWUS036h) and rtl8187b out of the box with ubuntu 10.04. although i think there can still be complications if you have other wireless cards involved.

eg. the classic ALFA AWUS036h which work fine for me (and loads of other people, including most of the Backtrack wifi cracking types) didn't work for this person, who had a driver conflict:

[http://ubuntuforums.org/showthread.php?t=1891914](http://ubuntuforums.org/showthread.php?t=1891914)

---

### Post by kurt18947 on 2011-12-10
I have 3 wireless adapters


[LIST=1]
[*]The oldest but just works with every distro I've tried is an RealTek RTL8187B based adapter.  TrendNet TEW-424UB v.3.x.  It's useful for the 10.xx distros because it is plug & play.  I can use it to download updates & software for newer faster adapters that will work with 10.xx after some work.
[*]Netgear WNA1100.  Uses an ATH9K chip and work OOB with Ubuntu 11.xx.  Needs some work with 10.xx
[*]TrendNet TEW-649UB is a small USB adapter based on a RealTek 8192SU chip.  It also is plug & play on Ubuntu 11.xx but needs some firmware installed for 10.xx
[/LIST]
Working OOB depends on the chipset.  Every manufacturer will use different chip suppliers.  What can be tricky is when manufacturers use different chipset with different versions of the same model #.  I praised the TrendNet TEW-424UB ver.3.x above.  The TrendNet TEW424UB ver **2.x **uses an SiS chipset and I'm not even sure it work with NDISwrapper.  Just some things I've learned along the way.  As the old saying goes "learn from the mistakes of others.  You'll never live long enough to make 'em all yourself.":)

---

### Post by donniezazen on 2011-12-12
[http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=cm_srch_res_rtr_2](http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=cm_srch_res_rtr_2)

This one has pretty good Ubuntu reviews.

Thanks for commenting guys.

---

### Post by kurt18947 on 2011-12-12
> **donniezazen said:**
> [http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=cm_srch_res_rtr_2](http://www.amazon.com/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002WBX9C6/ref=cm_srch_res_rtr_2)

This one has pretty good Ubuntu reviews.

Thanks for commenting guys.

It looks like a close relative to the Netgear WNA1100.  Atheros 9k chip family seems to get along well with Linux.  it's certainly worth a shot.  You can return it if it turns out to be a problem child but I doubt it'll be a problem.

---

### Post by donniezazen on 2011-12-12
> **kurt18947 said:**
> It looks like a close relative to the Netgear WNA1100.  Atheros 9k chip family seems to get along well with Linux.  it's certainly worth a shot.  You can return it if it turns out to be a problem child but I doubt it'll be a problem.

I am thinking of getting MediaLink Wireless N Adapter. It seems to have best reviews and it's a N adapter. 

[http://www.amazon.com/Medialink-Wireless-Adapter-802-11n-Compatible/dp/B002RM08RE/ref=sr_1_1?ie=UTF8&qid=1323736143&sr=8-1](http://www.amazon.com/Medialink-Wireless-Adapter-802-11n-Compatible/dp/B002RM08RE/ref=sr_1_1?ie=UTF8&qid=1323736143&sr=8-1)

---

### Post by kurt18947 on 2011-12-13
> **donniezazen said:**
> I am thinking of getting MediaLink Wireless N Adapter. It seems to have best reviews and it's a N adapter. 

[http://www.amazon.com/Medialink-Wireless-Adapter-802-11n-Compatible/dp/B002RM08RE/ref=sr_1_1?ie=UTF8&qid=1323736143&sr=8-1](http://www.amazon.com/Medialink-Wireless-Adapter-802-11n-Compatible/dp/B002RM08RE/ref=sr_1_1?ie=UTF8&qid=1323736143&sr=8-1)

I didn't read many of the reviews of the MediaLink adapter.  Here is something that would give me pause 
 [http://www.wikidevi.com/wiki/Medialink_MWN-USB150N](http://www.wikidevi.com/wiki/Medialink_MWN-USB150N)
It seems like the Ralink 3070 appears pretty frequently in the networking & wireless forum and not necessarily in a positive way.

---

### Post by 3rdalbum on 2011-12-13
The Alfa AWUS050NH works out-of-the-box on Ubuntu 11.10.

---

