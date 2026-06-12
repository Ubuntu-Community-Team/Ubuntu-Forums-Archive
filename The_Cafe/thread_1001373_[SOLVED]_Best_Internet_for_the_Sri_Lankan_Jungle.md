---
title: "[SOLVED] Best Internet for the Sri Lankan Jungle"
date: 2008-12-03
forum: The Cafe
---

### Post by C.S.Cameron on 2008-12-03
Hi:
I'm seeking advise on finding an internet provider.
My place is in the jungle a couple of kilometers inland from Hikkaduwa.
The house has electricity, (intermittent), but I do not think cable internet is an option.
I often need to send and receive files of several megs.
Speed and low cost are priorities.
Any help will be greatly appreacieted
Cork

---

### Post by Bibek on 2008-12-03
> **C.S.Cameron said:**
> Hi:
I'm seeking advise on finding an internet provider.
My place is in the jungle a couple of kilometers inland from Hikkaduwa.
The house has electricity, (intermittent), but I do not think cable internet is an option.
I often need to send and receive files of several megs.
Speed and low cost are priorities.
Any help will be greatly appreacieted
Cork

If your place has a phone line, then you could look into ADSL. I think Adsl2+ can get you up to 8mbps. Normal ADSl would give you around 2mbps. For ADSL, you need a normal telephone line.

---

### Post by Grant A. on 2008-12-03
Satellite Internet?

---

### Post by mips on 2008-12-04
Has the place got a phone line? If it does or you can get one see if you can get ADSL.

Other options are 3G HSDPA if their is signal coverage. Sattelite would work.

---

### Post by billgoldberg on 2008-12-04
> **Bibek said:**
> If your place has a phone line, then you could look into ADSL. I think Adsl2+ can get you up to 8mbps. Normal ADSl would give you around 2mbps. For ADSL, you need a normal telephone line.

Yes, but ADSL speeds can slow down dramatically if you aren't close to a central.

So you could get a 8mbps package but only get around 100kb/s.

I would most likely go for satellite Internet.

I have heard the ping is a lot higher with satellite Internet, so gaming online won't be an option, but it should be fast.

edit: and ADSL 2 should get at least 20mbps (I have 12mbps). Normal ADSL can also be faster than 2mbps, I used to have 4.6mbps on normal ADSL.

---

### Post by mips on 2008-12-04
> **billgoldberg said:**
> 
I have heard the ping is a lot higher with satellite Internet, so gaming online won't be an option, but it should be fast.


Correct, besides normal pings you can add 0.5seconds for sattelite links. Not good for gaming, video or VoIP but everything else should be good.

---

### Post by C.S.Cameron on 2008-12-07
Unfortunately there are no phone lines where I am.
Found that Sri Lanka Telecom sells a fixed wireless phone with built in modem.
The phone connects to a computer through a USB cable and is said to be good for 56 kbs.
I bought one, It only comes with Windows software which installs from some sort of virtual CD inside the phone.
When I plug in the USB cable, windows goes through its found new hardware thing, installs the USB ok but freezes when it gets to the CD ROM.
Spent hours talking o the SLT tech's without success.
Trying to install in Ubuntu looks promising. Nothing freezes when I plug in the USB cable and the software runs under Wine. Unfortunately It is difficult to research how to get dial up working in Ubuntu until I get connected.

Just after buying this phone I found out about Dialog.
They sell a wireless service that is also good for anywhere on the island.
They have plans with speeds up to 2 Mbs and best of all, they are listed under Mobile Broadband in Network Connections.

Will give them a try on Monday, Hopefully I can then mark this thread as solved.

---

### Post by mips on 2008-12-08
> **C.S.Cameron said:**
> 
Found that Sri Lanka Telecom sells a fixed wireless phone with built in modem.
The phone connects to a computer through a USB cable and is said to be good for 56 kbs.
I bought one, It only comes with Windows software which installs from some sort of virtual CD inside the phone.


Can you tell me the make & model of the phone and possibly post a picture. There is a similair service over here (mostly Indian company) and I know some people have it working on linux.

Have you enquired about cellular EDGE, 3G & HSDPA?

---

### Post by PmDematagoda on 2008-12-08
SLT sucks with Linux, and will only support Windows, which means that you need to think about everything before buying something from them, remember that. And keep away from the USB ADSL modem, it usually will not work with Linux. About CDMA(which is probably what you have), I am not sure if using the software via WINE would be that useful, but I haven't really used it so I can't really say.

About other providers. Mobitel(which belongs to SLT) has a plan for 3G/HSDPA connections, with a max speed of about 14 Mbps(from what I vaguely remember), but you better check the modem that Mobitel provides with it to ensure compatibility, they used to give Huawei modems that do have a pretty good reputation for working with Linux, but not so sure about what they are selling now. Dialog is good as well, but I don't know a lot about them. Hutch and Tigo also aren't really known to me.

Good luck getting a proper wireless connection here.:)

---

### Post by C.S.Cameron on 2008-12-08
The SLT phone is CDMA and has a Huawei modem, 
Had a couple service guys over yesterday for about 2 hours, could not even get it working in Windows.
The laptop is Asus based and has a built in modem which could be part of the problem.
Planning to head to Galle this morning to give Dialog a try.
Mobitel is next on the list if that does not work.

---

### Post by C.S.Cameron on 2008-12-09
Well, if you can read this I am connected.
Currently using the SIM card from my cell phone, account should be activated tomorrow.
Went with Dialog, got a Huawei USB modem. work good in Galle, OK in Hikkaduwa, not sure about the jungle yet. Depends if it is inside the G3 area. In Hikkaduwa I am getting 7.2 Mbps.

So far I have only tried it with XP.
Now my challenge is to get it working with Ubuntu.
I have not used a dial up service in the last decade and never with Linux.
Right now I got to go get the flat fixed on my bicycle.

Please, where do I start and what do I do next?

---

### Post by mips on 2008-12-09
> **C.S.Cameron said:**
> 
Please, where do I start and what do I do next?

for linux ubuntus network manager thingy might just pick it up automatically (v8.10) alternatively look into the Vodaphone mobile connect client for linux. Althought it says vodafone you can use it on any network.

---

### Post by C.S.Cameron on 2008-12-10
In Windows the modem runs Vodaphone Mobile Connect Lite, Where do I download this for Ubuntu?

---

### Post by mips on 2008-12-11
[https://forge.betavine.net/frs/?group_id=12&release_id=200](https://forge.betavine.net/frs/?group_id=12&release_id=200)

But first check if you cant get it working in network manager or whatever it is called as I know it supports connections of this type. See:
[https://bugs.launchpad.net/ubuntu/+bug/164369](https://bugs.launchpad.net/ubuntu/+bug/164369)
[http://public.warp.es/vmc](http://public.warp.es/vmc)  This is included in Network Manager.

---

### Post by C.S.Cameron on 2008-12-12
After getting connected and working in windows I downloaded Vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb.
Before installing this I tried NetworkManager Applet using Dialog GSM (Post-Paid) and it worked right off.
Thanks for all the help.

---

