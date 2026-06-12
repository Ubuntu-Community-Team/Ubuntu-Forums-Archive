---
title: "Extremely slow 802.11n connection after upgrade to Ubuntu 10.04"
date: 2010-05-04
forum: System76 Support
---

### Post by |Porsche on 2010-05-04
Hello,
I was just wondering if anyone else is having issues when connecting to a Wireless-N network. Ever since the update, if I select my Wireless-N network the connection is so slow that everything times out. However, there are no issues when I connect to my Wireless-G. The wireless routers are bridged together. This is on a Panp6.

Any ideas?

---

### Post by eddietours on 2010-05-04
me too i can"t even connect to n only g

---

### Post by |Porsche on 2010-05-04
I am glad to know that I am not alone. I was starting to get worried. A Google search didn't point me to anything!

---

### Post by thomasaaron on 2010-05-05
What wireless card do you guys have?

```
lspci | grep -i wireless
```

---

### Post by lnxguit on 2010-05-05
I had the same problem. It was cured by rebooting my cable modem, wireless router and all my computers.

---

### Post by eddietours on 2010-05-05
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by |Porsche on 2010-05-05
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

### Post by thomasaaron on 2010-05-06
OK, is it possible to set your router to n-only mode, instead of mixed mode (your router might call it something else)?

---

### Post by eddietours on 2010-05-06
am going to try that ones i get home thanks i got the Belkin n+

---

### Post by |Porsche on 2010-05-06
I will try that later tonight. I am running DD-WRT on a Linksys WRT320N.

---

### Post by |Porsche on 2010-05-06
Ok. I switched my AP to N only mode. The results are the same. Very slow connections bursty at times. See the attached screenshots of Mixed Mode and N only mode.

Any idea what we are dealing with?

---

### Post by eddietours on 2010-05-07
same for me too :confused:

---

### Post by thomasaaron on 2010-05-07
Looks like some others are having this issue too...
[http://ubuntuforums.org/showthread.php?t=1349271](http://ubuntuforums.org/showthread.php?t=1349271)

There is a bug report open on it too...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491362](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491362)

There is a new kernel update for Lucid. Please run your updates and reboot to see if the problem persists.

---

### Post by eddietours on 2010-05-08
no luck

---

### Post by thomasaaron on 2010-05-10
What kind of encryption are you using on your router? 

Also, please try removing encryption and see if you get n-speeds. (I don't expect you to keep it like that, I'm just trying to home in on exactly what we're dealing with.)

---

### Post by uwe lars on 2010-05-13
Same problem: with Ubuntu 09.10 all was o.k.; with Ubuntu 10.04, the 802.11n connection is highly unstable; I've a Lenovo SL510 notebook with "Network controller: Intel Corporation WiFi Link 1000 Series".
Router configuration change to 802.11b+g only completely helped.

---

### Post by |Porsche on 2010-05-13
I have been busy so I have not been able to troubleshoot the issue any further. I suggest that anybody else that is having this issue goes to the bug report and tell them that you are also affected. Perhaps System 76 can submit patch once we find the issue if nobody else is able to do anything.

The bug report is located at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491362](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/491362)

---

### Post by |Porsche on 2010-05-13
Just turned WPA2 Personal off and the issue persists. Any other info you need?

---

### Post by thomasaaron on 2010-05-14
OK, can you go into your router and try to set it to G mode, or maybe abg mode, or something like that... something that doesn't include N.

That might actually make your connection faster while we're trying to figure this one out.

---

### Post by JohnDoe365 on 2010-05-18
Please take a look if it is related to
[http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)
ie disable and re-enable wireless. Is speed (much) faster now?

---

### Post by lapinope on 2010-05-18
Samething here.  Works fine under Windows, and was working ok under Ubuntu 09.10.  Very slow since I upgraded to Ubuntu 10.04 (Windows still ok).

Using a lenovo T500 with "03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300"

Using "802.11n only", "802.11g only" or "802.11a only" in either 2.4Ghz or 5Ghz doesn't change anything.

Disabling security doesn't help either.  

I experience sometimes (very rarely) a sudden burst of speed, but it doesn't last.

Disabling + re-enabling WiFi with the hardware switch effectively brings speed up for some time.

---

### Post by JohnDoe365 on 2010-05-19
I gathered in some threads the information that disabling and re-enabling WiFi either by hardwar of software, as long a re-associate event happens, helps to bring back speed for some time.

I also experience that for some short time, once speed has droped, it suddenly rebursts but only for a very short time.

This behaviour is not hardware driver related which makes me think it is a WiFi subsystem of kernel issue.

Does anybody know how to raise awareness of the ubuntu / kernel team?

---

### Post by |Porsche on 2010-05-19
It seems like the issue has fixed itself. I will monitor it for a week. Are you all still having the issue?

---

### Post by thomasaaron on 2010-05-20
Did you run some uppates?

---

### Post by |Porsche on 2010-05-21
I keep my system up to date. Besides whats pushed down via apt I have not done anything special. Anything you want me to check?

---

### Post by lapinope on 2010-05-23
> **|Porsche said:**
> It seems like the issue has fixed itself. I will monitor it for a week. Are you all still having the issue?

Same thing here, internet speed seems to be normal again.  Maybe the system update did the job?  
[B]
Note[/B]:
I disabled IPV6 in order to help (see [this]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") and [this]("http://ubuntuforums.org/showthread.php?t=1472356&highlight=disable+ipv6#5") ) but it didn't really change anything.  I didn't tried to re-enable IPV6 yet though.

Thanks to all of you for your help :)

---

### Post by uwe lars on 2010-05-24
I'm very sorry. My system is nearly permanently up-to-date, too. Nevertheless, the problem persists. Restriction to 802.11b+g still necessary.

---

### Post by thomasaaron on 2010-05-24
uwe lars,

What system do you have, and what wifi card does it have?

---

### Post by uwe lars on 2010-05-29
Thomas,

I've a Lenovo SL510. lspci says:

05:00.0 Network controller: Intel Corporation WiFi Link 1000 Series

Best regards.

---

### Post by nDrewPJ on 2010-05-31
We all can subscribe to this bug report - it is affecting Intel and Broadcom wifi-cards for the moment:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)

---

### Post by thomasaaron on 2010-06-01
uwe lars,

This forum is for supporting System76 machines. Not that we mind helping you, though. We're happy too. I bring it up because we've never sold Intel 1000 cards. So, I don't really have any to test with.

That said, an update seems to have fixed the problem with our 5100 cards.

---

### Post by Loc@Scope on 2010-11-08
I was having the same problem with my portable  ASUS K70IJ-TY090V connecting to a Netgear router WNR3500L. I've tried to disable wep encryption : nothing change > slow connection. So I put again my parameter : WPA-PSK [TKIP] + WPA2-PSK [AES], and my router says to me that this kind of encryption allow only 54Mbps connection and to have the 300 mbps one I have to use : WPA2-PSK [AES] encryption...

So I do this and I have now a 300 Mbps connection ! YES

My wifi card is : 
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

And I use Ubuntu 10.04 amd64 with this kernel 2.6.32-25-generic.

I hope this can help other like this post help me.

PS : sorry for my english, I'm french :)

---

### Post by travlemon on 2011-11-28
Hello,

I know this thread is a little old, but I am having the same issue.  My laptop, with an Intel WiFi Link 5300, has a really slow connection under Linux.  Under XP, the connection flies, so I know it's not my device or router settings.  

On speed tests, I will reach about 20 Kb/s on uploads if I'm lucky, and about 1 Mb/s, on downloads, at the most.  In Windows, it reaches about 2 Mb/s on uploads and 6 Mb/s on downloads.  As far of the history of this problem, I had some speed issues for a long time, and I blamed my router without any investigation.  The speeds were just fast enough for me to not bother looking into it.

When I upgraded to Ubuntu 11.10, that's when things got significantly slow.  I have strong signal strength, but it still takes a sluggish 30 or so seconds to get to the router's setup page (if I'm lucky).

I have a desktop with the same version of Linux, and it has a Linksys wireless-g PCI card, and it does not have this issue.  It performs great on the speed tests, and the router config pages load pretty much instantly.


Does anybody any idea what I can do to fix this?  I have great signal strength, I eliminated the router config to be a problem, and in Windows it runs exceptionally fast.  

_2 final things:_ Here is my **iwconfig** output:
         ```
 IEEE 802.11abgn  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:CF:11:E6   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1080  Invalid misc:1641   Missed beacon:0
```

**And here's my awful speed report :(**
[IMG]http://www.dslreports.com/im/99758192/63189.png[/IMG]


Any help is MUCH appreciated!

---

### Post by isantop on 2011-11-30
We haven't had any reports of slow speeds with 5300's. Can you try running from a LiveCD to rule out a possible software problem? Also, was it a fresh install of 11.10, or did you upgrade?

---

### Post by travlemon on 2011-11-30
> **isantop said:**
> We haven't had any reports of slow speeds with 5300's. Can you try running from a LiveCD to rule out a possible software problem? Also, was it a fresh install of 11.10, or did you upgrade?

Thanks so much for responding!  Let me try to give you a quick summary of this problem's history, without rambling too much:

_Kubuntu 11.04_ - I noticed slow speeds, but they weren't slow enough for me to really investigate.  My router's config pages loaded slowly, but due to past issues with another Linksys router, I thought it was just the router. At this point, I don't suspect the wifi card as the problem.

_Kubuntu 11.10, upgraded from 11.04:_  This answers one of your questions.  This is when it become VERY slow.  Another coincidence was that my ISP was having issues in my area around the same time I upgraded.  So I naturally suspected that it was an ISP issue for quite some time.  When I used a couple other PC's in the house, I noticed no lag on the internet/network and became suspicious of my laptop.

_Linux Mint 12 (clean install and removed Kubuntu):_  Without investigating yet, I still wasn't sure where that delay came from, and was only just starting to look into it after noticing that Mint 12 also had the problem.  I believe Mint 12 is based on Ubuntu 11.10.

OKAY! Hope I'm not overloading on the info.  To answer your other question, I popped in a LiveUSB and ran speed tests.  It was so slow that it wouldn't even complete the test, and timed out.  I think I may have fixed the problem, but I'd still like to hear any advice you have.

I was going to download the latest Linux-based driver from intellinuxwireless.org, but I noticed the .ucode file was the same one packaged with Ubuntu/Mint 12.  I figured the result would be the same, so I simply moved any iwlwifi*.ucode files from the /lib/firmware folder to root's home (just as a holding place for them, rather than deleting them, of course). 

Then, I simply installed the Windows XP driver for the device with ndiswrapper and TADA, it works much better.  I'll show the newest speed test result, which is about the same as what I get when I'm in Windows.

I'd still prefer to hear any advice you may have, as this ndiswrapper version of the driver refuses to connect to my wireless network sometimes, and makes me jump through hoops to get it working again.  

Sorry for the rambling!  Anyway, thanks in advance for any advice, and below is my speed test result:

[IMG]http://www.dslreports.com/im/99796198/26742.png[/IMG]
This is pretty much what Windows clocked in at too, give or take

---

### Post by isantop on 2011-12-01
If you've got it working, then I think you should be okay. I can't think of anything to get it going much closer to your previous reports, apart from replacing the card.

---

### Post by travlemon on 2011-12-01
> **isantop said:**
> If you've got it working, then I think you should be okay. I can't think of anything to get it going much closer to your previous reports, apart from replacing the card.


I agree with you, I also think it's probably okay.  I noticed that making any changes to wireless settings, on the router (such as changing the channel) or in Linux, the card would start to hang up when connecting.  

But I have everything set the say I want it, and really shouldn't ever need to touch the settings ever again.  With that said, I think it's safe to say it's fixed.  Thanks for your help!

---

