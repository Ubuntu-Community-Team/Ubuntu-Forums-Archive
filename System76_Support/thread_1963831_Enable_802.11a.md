---
title: "Enable 802.11a?"
date: 2012-04-23
forum: System76 Support
---

### Post by Newbunto on 2012-04-23
I recently took delivery of a new system76 laptop. It has the Intel Centrino Advanced-N 6230 wireless module (802.11a/b/g/n Wi-Fi plus Bluetooth). It works fine connecting to an 802.11g access point. However I couldn't see how to enable 802.11a.

I don't know whether it is possible to use 802.11a and 802.11g simultaneously (is it?) but I probably don't need to do that. I would like to know how to switch between 802.11g and 802.11a however.

Ubuntu 11.10 (64 bit)

---

### Post by newbie-user on 2012-04-23
802.11a runs on a different frequency than G and B. So if you want to use 802.11a, you have to connect to an 802.11a enabled access point. You really don't find 802.11a around much anymore. You're more likely to see 802.11n using the 5GHz frequency.

---

### Post by Newbunto on 2012-04-23
I have 802.11a access points and 802.11g access points and no 802.11n access points.

---

### Post by newbie-user on 2012-04-23
So then you should be able to test the 802.11a functionality with the 11a access points.

---

### Post by Newbunto on 2012-04-24
It could be that 802.11a will just work and I don't have to do anything. Or it may be that I have to switch from 802.11g to 802.11a. I'm just looking for someone to provide hints as to which it is likely to be and, if the latter, what to do.

The complication is that the 802.11a access points are at a different physical location from where I am now. I would prefer to know in advance what I will have to do.

I take your point that if noone is using 802.11a anymore, I may have some difficulty getting an answer.

---

### Post by isantop on 2012-04-24
> **Newbunto said:**
> It could be that 802.11a will just work and I don't have to do anything. Or it may be that I have to switch from 802.11g to 802.11a. I'm just looking for someone to provide hints as to which it is likely to be and, if the latter, what to do.

The complication is that the 802.11a access points are at a different physical location from where I am now. I would prefer to know in advance what I will have to do.

I take your point that if noone is using 802.11a anymore, I may have some difficulty getting an answer.

You won't need to make any changes to connect to a .11a access point. All of that switching is determined by the Access Point.

---

### Post by ph4nt0m117 on 2012-04-24
As stated a billion times here, A is old and probably not even used anywhere in the US / Europe.  Though, if you really wanted to try and use A, I would recommend the madwifi driver.  There are so many different drivers for so many different cards available in all frequencies used ( A B G N ) that counting them all is ridiculous.

Although one question comes to mind, with A being so old, isn't the reach of an A card anymore so small that it's practically pointless?

---

### Post by derekcentrico on 2012-04-26
> **ph4nt0m117 said:**
> As stated a billion times here, A is old and probably not even used anywhere in the US / Europe.  Though, if you really wanted to try and use A, I would recommend the madwifi driver.  There are so many different drivers for so many different cards available in all frequencies used ( A B G N ) that counting them all is ridiculous.

Although one question comes to mind, with A being so old, isn't the reach of an A card anymore so small that it's practically pointless?

You're not up to speed.  802.11a is for the 5GHZ band that we all hear about on dual-band systems.

I would also like to know how to force Ubuntu to use 5GHZ versus 2.4GHZ as can be done on other OSes.

---

### Post by isantop on 2012-04-26
> **derekcentrico said:**
> You're not up to speed.  802.11a is for the 5GHZ band that we all hear about on dual-band systems.

I would also like to know how to force Ubuntu to use 5GHZ versus 2.4GHZ as can be done on other OSes.

I'm not sure if it's (easily) possible. I wouldn't recommend it if it was though; higher frequencies translate to higher power consumption and poorer wall penetration, plus not all routers are set to use 5 GHz. It's much better to leave it to auto-select the frequency to use.

---

### Post by derekcentrico on 2012-04-26
> **isantop said:**
> I'm not sure if it's (easily) possible. I wouldn't recommend it if it was though; higher frequencies translate to higher power consumption and poorer wall penetration, plus not all routers are set to use 5 GHz. It's much better to leave it to auto-select the frequency to use.

I was just pointing out that it is a new thing, again, rather than old technology.  It works great at least on Windows and Mac.

IF Ubuntu operates with it, neat.  But I haven't been so fortunate with WIFI.  More on that in another thread I assume (pending on results from 12.04 upgrade going on now)...

---

### Post by Newbunto on 2012-04-26
> **isantop said:**
> higher frequencies translate to higher power consumption and poorer wall penetration

For indoor use power consumption is less of an issue from the point of view of the battery going flat (since the laptop may be running off mains power anyway or could be if not).

(not directed at isantop specifically)
The main advantages of 802.11a over 802.11b/g are more channels, non-overlapping channels, less congestion and less interference with other devices. (I have a 2.4 GHz cordless phone that becomes completely dead with a 2.4 GHz WAP switched on.)

802.11n that is capable of running in either frequency band addresses those issues but not everybody has upgraded their WAPs.

802.11a is older than 802.11g but not inferior to it. The main advantage of 802.11g is compatibility with earlier 802.11b equipment.

> plus not all routers are set to use 5 GHz.

Agreed. If derekcentrico works out how to force Ubuntu to use 802.11a then he will definitely also want to work out how to undo that. (-:

> It's much better to leave it to auto-select the frequency to use.

Which raises the question as to how to tell what frequency got used.

If only for testing, it seems very sensible to me to be able to force 802.11a (and likewise to be able to force 802.11g).

---

### Post by chili555 on 2012-04-27
I have connected to an 802.11a access point in Ubuntu. It wasn't necessary to 'force' anything. It was only necessary to direct a connection to the specific AP, either through Network Manager or if NM is not installed, in iwconfig. It just works.

---

### Post by derekcentrico on 2012-04-27
I only agreed to wanting to know how to select 5GHZ in Ubuntu as there can be extreme interference on 2.4GHZ here at the flat from others.

I have a simultaneous dual-band router capable of both 2.4 and 5 at once.

I really don't care all that much, I just saw this thread and jumped in to see about a method.

Hell, I don't even have reliable WiFi on Ubuntu at this time so whatever there.  (more on that [http://ubuntuforums.org/showthread.php?p=11879073](http://ubuntuforums.org/showthread.php?p=11879073))

---

### Post by buddyd16 on 2012-04-27
derekcentrico: you do not select between the 5ghz and 2.4ghz in Ubuntu. Your dual band router should be broadcasting two separate wifi SSIDs for the 2.4ghz and 5hz bands respectively, ie you should see two different wifi acccess points for each band on the router.

Make sure have set up the router to broadcast both the 2.4 and 5ghz signals by default they only broadcast at 2.4ghz. This is done by connecting via wifi or hard line and logging into the router which should be outlined in your routers manual.

---

### Post by derekcentrico on 2012-04-27
> **buddyd16 said:**
> derekcentrico: you do not select between the 5ghz and 2.4ghz in Ubuntu. Your dual band router should be broadcasting two separate wifi SSIDs for the 2.4ghz and 5hz bands respectively, ie you should see two different wifi acccess points for each band on the router.

Make sure have set up the router to broadcast both the 2.4 and 5ghz signals by default they only broadcast at 2.4ghz. This is done by connecting via wifi or hard line and logging into the router which should be outlined in your routers manual.

No worries.  My router is fine.  I can select 5GHZ in settings on both Windows and Mac.  I was just wondering if it was so easy on Ubuntu.  I'm good to go, no problems from my end.  I was only participating to explain 802.11a is 5GHZ now and thought I'd ask for instructions on easy hopping if possible.  :P

My real issue is failure to access WiFi per the thread link above.  No help for me.  :confused:  Oh well!

---

### Post by Newbunto on 2012-04-29
> **chili555 said:**
> It was only necessary to direct a connection to the specific AP

As a later response notes, that doesn't work if the access point operates both 802.11a and 802.11g simultaneously (even if the client device does not).

---

