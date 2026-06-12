---
title: "Is wireless network bug fixed on newest Netbook remix ?"
date: 2010-02-01
forum: Ubuntu Moblin Remix
---

### Post by mrpenguin on 2010-02-01
I would like to Install Ubuntu Netbook Remix on my Asus Aspire Netbook but has heard there is lots of problems especially with wireless networking .... can anybody tell me is this has been resolved in the latest version ?

---

### Post by aljoriz on 2010-02-05
Better wait for Lucid Lynx I think that there is a ACER specific ubuntu distro called Linux4One, you might do well by giving it a try.

---

### Post by nuwave on 2010-02-15
I suggest still trying out the latest version of UNR even if there is any wifi issues. I installed on my Dell Mini 10v with no wifi out of the box but it was not difficult to get it working. Plus I also got my USB modem to work easily, so give it a try so you can get your feet wet;)

---

### Post by Cushie on 2010-02-19
> **mrpenguin said:**
> I would like to Install Ubuntu Netbook Remix on my Asus Aspire Netbook but has heard there is lots of problems especially with wireless networking .... can anybody tell me is this has been resolved in the latest version ?

I have been using Ubuntu 9.10 UNR since first released and the wifi worked absolutly painlessly on my [COLOR="Red"]**Acer Aspir One**[/COLOR] just enter the encryption key.  Have had automatic connection since. Give it a go! :D

---

### Post by sevenX on 2010-02-19
I installed ubuntu netbook remix 9.10 and it worked fine at first but all of a sudden out of blue it stopped cant connect to internet.  Couldnt find solution so Im going to re-install now see how it goes.. this was on my hp mini

---

### Post by Cushie on 2010-02-20
Sevenx, there are plenty of checks to make to sort this out without reinstalling the whole system.  You may only have one line of error in the config but you need to give more information to get some help.

1 Does the network icon show the signal 'stepped bars' if it does not first switch off the router and  after a few minutes back on again. Then switch off the wifi adapter on the netbook little switch on the front edge. Then maybe run network-manager again.

2 If it does show the icon (on the top bar) right click and check 'connection information' and see what is missing, that gives a clue to the next step. Have a look at my 'screenshot' attached. 
Right click and 'edit connection' If you are connected to the network but not on line check the 'gateway address' of your router (mine is 192.168.1.1)

3 If you are not connected but the driver info is shown, reset the parameters DHCP and the encryption key.

4 In one rare occasion, the driver info was missing in the 'connection info' the wireless driver got 'blacklisted' so deleting that line in the 'modprobe' sorted it.

I have played around with wireless quite a bit over the years and can say that the latest release 9.10 has the best function ever. In the netbook case the OS is designed for the hardware we have , and it works!

---

### Post by wael_hossam on 2010-02-20
I installed Remix on my HP Mini 2133 and then Wireless card was not detected at all. Also sound doesn't appear to be working.
Is there any guid to setup Remix on HP Mini?:confused:

---

### Post by bama7474 on 2010-02-20
I installed UNR 9.10 (Karmic) on my Toshiba NB305 and the wireless worked right out of the box...I did have to setup a backport to get past a weak wireless problem I was having.  I can't get my WIFI Function key to turn on/off my wireless though, I have to mouse to the connection and right click to disconnect, not a big deal but would like to have all my function keys to work like they did with XP.

---

### Post by mrpenguin on 2010-02-20
I eneded up installing remix on my asus aspire netbook and I have no problems at all with connecting to a network ... love it !!
I do seem to have a problem with Empathy on remix where it is working no problem on my laptop with ubuntu

---

### Post by Cushie on 2010-02-22
> **wael_hossam said:**
> I installed Remix on my HP Mini 2133 and then Wireless card was not detected at all. Also sound doesn't appear to be working.
Is there any guid to setup Remix on HP Mini?:confused:


Try here;

[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

or search alternative.

---

### Post by Aduntu on 2010-02-26
I recently installed UNR 9.10 on my Asus Eee PC and everything worked perfectly right out of the box -- wireless included.  Couldn't be happier.

---

### Post by xe1ufo on 2010-02-26
Maybe this will help somebody else. I was going crazy trying to keep my WiFi up and running on both WindowsXP and Ubuntu 9.10 (both the normal, and the Netbook Remix versions). The WiFi would suddenly cut out, on either Windows or Ubuntu operating system, for no reason whatsoever.  Then over on the Acer Aspire One forums, I discovered I was not the only one having problems with the Mickey Mouse Atheros modem chosen by Acer. Apparently this is a glitch in the Atheros' internal bios.

So on reccomendation of several others, I searched Ebay, found me a good Intel 3945ABG mini PCI WiFi card. (WARNING: THERE ARE OTHER VERSIONS THAT ARE NOT MINI PCI ON EBAY! THEY WON'T FIT!)

(See [http://www.aspireoneuser.com/forum/viewtopic.php?f=34&t=10788&p=111170#p69294](http://www.aspireoneuser.com/forum/viewtopic.php?f=34&t=10788&p=111170#p69294))

I have never had a problem since I switched, neither in Windows, nor Ubuntu. I also feel that the signal strength is much better.

Hope this helps somebody!

---

### Post by skittles86 on 2010-03-09
> **bama7474 said:**
> I installed UNR 9.10 (Karmic) on my Toshiba NB305 and the wireless worked right out of the box...I did have to setup a backport to get past a weak wireless problem I was having.  I can't get my WIFI Function key to turn on/off my wireless though, I have to mouse to the connection and right click to disconnect, not a big deal but would like to have all my function keys to work like they did with XP.


can you give me the commands for that? i also have a toshiba nb305 and im having problems connecting, it will act as though it is connecting but never follow through. and after i click disconnect to quit tring my network manager disappears.

---

### Post by practic on 2010-03-09
> **xe1ufo said:**
> So on reccomendation of several others, I searched Ebay, found me a good Intel 3945ABG mini PCI WiFi card. (WARNING: THERE ARE OTHER VERSIONS THAT ARE NOT MINI PCI ON EBAY! THEY WON'T FIT!) I have never had a problem since I switched, neither in Windows, nor Ubuntu. I also feel that the signal strength is much better.

Yes, that's what I did with a couple Acer AspireOne's also...replace the Atheros wireless card with Intel 3945. They're only about $10...not much to pay to say goodbye to wireless problems (although you do have to take the netbook apart to get at the wireless card).

---

### Post by kbundies on 2010-08-10
> **Cushie said:**
> Sevenx, there are plenty of checks to make to sort this out without reinstalling the whole system.  You may only have one line of error in the config but you need to give more information to get some help.

1 Does the network icon show the signal 'stepped bars' if it does not first switch off the router and  after a few minutes back on again. Then switch off the wifi adapter on the netbook little switch on the front edge. Then maybe run network-manager again.

2 If it does show the icon (on the top bar) right click and check 'connection information' and see what is missing, that gives a clue to the next step. Have a look at my 'screenshot' attached. 
Right click and 'edit connection' If you are connected to the network but not on line check the 'gateway address' of your router (mine is 192.168.1.1)

3 If you are not connected but the driver info is shown, reset the parameters DHCP and the encryption key.

4 In one rare occasion, the driver info was missing in the 'connection info' the wireless driver got 'blacklisted' so deleting that line in the 'modprobe' sorted it.

I have played around with wireless quite a bit over the years and can say that the latest release 9.10 has the best function ever. In the netbook case the OS is designed for the hardware we have , and it works!

Cushie,

in the mean time I am on 10.4 with my hp mini2133
Wireless Networking is working thanks to Broadcom STA proprietary wireless driver - though the icon shows an error (see attached picture).
I did have the same problem under 9.10 (wireless network ok. - icon not ok.)
Can you suggest a solution or fix for this?
Thank you in advance.

---

### Post by cariboo on 2010-08-12
> **kbundies said:**
> Cushie,

in the mean time I am on 10.4 with my hp mini2133
Wireless Networking is working thanks to Broadcom STA proprietary wireless driver - though the icon shows an error (see attached picture).
I did have the same problem under 9.10 (wireless network ok. - icon not ok.)
Can you suggest a solution or fix for this?
Thank you in advance.

I get the same thing when connected to my Linksys wrt310n, I also use a SMC2804WBR as an access point, the icon shows full power when connected to it. All other access points I've connected to when I'm out and about show the correct icon, so I'm thinking it is something with the linksys router that causes the problem.

---

