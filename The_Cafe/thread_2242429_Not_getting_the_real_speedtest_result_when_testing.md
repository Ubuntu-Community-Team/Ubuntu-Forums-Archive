---
title: "Not getting the real speedtest result when testing from phone"
date: 2014-09-01
forum: The Cafe
---

### Post by linuxyogi on 2014-09-01
Hi,

Since this is not related to Linux I am posting this here,

When I test my Internet speed from my PC which is connected to the router via Ethernet I get proper results but

when I run the test from my phone which is connected via Wi-Fi I always get 5.45 Mbps. This never changes.

My guess is its not even reaching transit its just testing the speed of my WLAN.

Am I correct and is this normal in case of Wi-Fi ?

---

### Post by pqwoerituytrueiwoq on 2014-09-01
What is the distance from the router/access point and the wireless type (b/g/n 150/n 300/n 450/ac)
wireless N is some complicated crap
are you sure you are not using your cell's services for Internet

---

### Post by linuxyogi on 2014-09-01
> **pqwoerituytrueiwoq said:**
> What is the distance from the router/access point and the wireless type (b/g/n 150/n 300/n 450/ac)
wireless N is some complicated crap
are you sure you are not using your cell's services for Internet

Actually this is my first wireless router after 8 years of Internet usage ! So I nothing about the terms you have mentioned (b/g/n).

This is [my router]("http://www.dlink.com/us/en/home-solutions/connect/routers/dir-600l-wireless-n-150-home-cloud-router"). 

The box says "Wireless N 150 Cloud Router" so it must be N. Distance is negligible coz I am using my phone in the same room where the router is.

 I have disabled 2G on my phone and even if it was enabled the max speed I get from 2G is 56kbps.

---

### Post by pqwoerituytrueiwoq on 2014-09-01
how fast is your Internet?, that is a very low end router, not one i would recommend to someone on a very low budget
on the low end i suggest a DIR-615 and replace the firmware with dd-wrt, i have had good luck with the 23720 build
do you know what the wireless chip in your phone is? the chipset would be useful or a wifi standard, may be able to find something with the model #
if you want a half decent budget router a TL-WR1043ND is a decent one (it can run at wireless N 450, not enabled by default), wireless N 300 tops out around 80Mb/s at close range (~5 meters), probably end with with ~30Mbps at ~15 meters

it is also possible there is a lot of interference making your wifi speed drop to crap, changing the channel to something other than 6 (common default channel) should help

That router should be able to do over 10Mbps easily, so unless your phone is from the age of flip phones i would guess the router is defective or just a piece of junk

---

### Post by linuxyogi on 2014-09-01
> **pqwoerituytrueiwoq said:**
> how fast is your Internet?
That router should be able to do over 10Mbps easily, so unless your phone is from the age of flip phones i would guess the router is defective or just a piece of junk

The package that I am paying for is only 512kbps but my ISP supports local peering and caching so when I download stuff using torrent I get speeds upto 10MB/s but thats on my PC of course which is connected via
Ethernet. 

There is a high probability that my phone is the limiting factor here. Not that its a very cheap phone as per our currency but the Nokia Asha series of phones have earned a very bad reputation here.


> **pqwoerituytrueiwoq said:**
> 
on the low end i suggest a DIR-615 and replace the firmware with dd-wrt, i have had good luck with the 23720 build


Actually router is not even a month old and I once tried to install dd-wrt on this router but it didn't work despite following instruction written on dd-wrt's website. After some searching I found that (from 2013) Dlink
has written the latest firmware of this router in such a way so that people cant install other firmwares. You try 
too hard and you brick the router.


> **pqwoerituytrueiwoq said:**
> 
do you know what the wireless chip in your phone is? the chipset would be useful or a wifi standard, may be able to find something with the model #


[These]("http://www.gsmarena.com/nokia_asha_501-5445.php") are the specs of my phone but I don't see info about the wireless chipset. Tried some other websites also.


> **pqwoerituytrueiwoq said:**
> 
if you want a half decent budget router a TL-WR1043ND is a decent one (it can run at wireless N 450, not enabled by default), wireless N 300 tops out around 80Mb/s at close range (~5 meters), probably end with with ~30Mbps at ~15 meters

it is also possible there is a lot of interference making your wifi speed drop to crap, changing the channel to something other than 6 (common default channel) should help

That router should be able to do over 10Mbps easily, so unless your phone is from the age of flip phones i would guess the router is defective or just a piece of junk

The fact is at the moment the only device that I connect in wireless mode is my phone which is piece of s***.
I use it to get sound alerts for emails and Facebook notifications. Thats it.

BTW, on Facebook I am a member of my broadband (unofficial) group and I see a lot of people complaining about this same issue. They say that their torrent speeds (with local peering support) never exceeds 5MB/s in  wireless mode. Not all of them are using my model so there must be some other factor which is common
here.

---

### Post by linuxyogi on 2014-09-01
[**[COLOR=#000000]@pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458")

Same problem [here]("http://mybroadband.co.za/vb/showthread.php/515728-5Mbps-transfer-speed-on-Wireless-N-network-Normal").

---

### Post by pqwoerituytrueiwoq on 2014-09-01
try wifi to your pc, i would try to download a large file (to the phone) buy running a web service on my desktop
also what is the write speed of your sd card in your phone
you can try running the [iperf]("https://iperf.fr/") benchmark software (available in the ubuntu software center)
[quote=linuxyogi]
[quote=pqwoerituytrueiwoq]do you know what the wireless chip in your phone is? the chipset would  be useful or a wifi standard, may be able to find something with the  model #[/quote]
Actually router is not even a month old and I once tried to install dd-wrt on this router but it didn't work despite following instruction written on dd-wrt's website. After some searching I found that (from 2013) Dlink
has written the latest firmware of this router in such a way so that people cant install other firmwares. You try
too hard and you brick the router.
[/quote]
i said a DIR-615 with ddwrt, you have a DIR-600L

---

