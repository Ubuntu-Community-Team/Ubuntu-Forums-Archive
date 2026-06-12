---
title: "Asterisk PBX advice?"
date: 2012-04-28
forum: Server Platforms
---

### Post by wlraider70 on 2012-04-28
My church has a really old phone system with no voice mail. My goal is to look into the feasibility of setting up a PBX with VoIP internally and PSTN for external use.

So my question is simply tell me if my proposition below makes any sense and what I have missed. There are a lot of terms I don't recognize, so If used the wrong acronym let me know. 


1) Setup an asterisk server to route calls from phone to phone. I may use PBX in a Flash. [http://pbxinaflash.com/](http://pbxinaflash.com/) Does asterisk run on top of Ubuntu? 

2) The church has 2-4 PSTN phone lines, which requires a telephony PCI card in the server to utilize.
Can I use something like this, Linksys PAP2-NA VoIP Adapter. [http://www.voiplink.com/Linksys_PAP2_NA_p/linksys-pap2-na.htm](http://www.voiplink.com/Linksys_PAP2_NA_p/linksys-pap2-na.htm)

3) Setup some soft-phones as Proof of concept such as
[http://www.3cx.com/VOIP/voip-phone.html](http://www.3cx.com/VOIP/voip-phone.html)
Final step is deploying (cheap) SIP phones.


THANKS

---

### Post by rubylaser on 2012-04-29
PBX in a Flash works great.  I use it at home and at our Church.  We have 4 POTS lines and 5 SIP trunks.  In both cases, I used [Digium TDM11B]("http://www.digiumcards.com/digium_cards_combos.html") cards with (4) FXO modules to connect the POTS lines to the computer.  

Check out the [Nerdvittles site]("http://nerdvittles.com/"), they cover a bunch of very interesting PBX in a Flash ideas.  Also, their suggested phone is the [LG-NORTEL H.264 IP 1535 NTEX02BAE6 SIP VIDEO IP PHONE]("http://www.ebay.com/itm/LG-NORTEL-H-264-IP-1535-NTEX02BAE6-SIP-VIDEO-IP-PHONE-/330506306014?pt=LH_DefaultDomain_0&hash=item4cf3b601de#ht_2972wt_1141").

Ubuntu certainly supports installing Asterisk, I used to do this with Debian, but PBX in a Flash is so fast to setup, that's what I use now. That Linksys adapter won't work, that's for connecting old POTS telephones.  What you need is FXO ports to connect to the old POTS phone lines.

---

### Post by volkswagner on 2012-04-29
For running Asterisk with FreePBX you may want to have a look at [freedoh.net]("http://www.freedoh.net/freedoh.html").

There is a script for installing all the bits you need to get up and running, using Debian or Ubuntu.

The script author (Marcus Brown) recommends Debian.

I have just deployed the [Cisco SPA-303]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833150103") phones for $91 ea. which are an excellent mid-grade device for your IP phones.

---

### Post by wlraider70 on 2012-04-30
Is there a difference between POTS, plain old telephone system and PSTN. Are they analog? 

Also since I am using voip that is my connection to my office phones and the FXO port is the connection to the telephone company.

Thanks for the above help too.

edit: If I have about 8 phones in the office and the server is dedicated to PBX what kind of power should it have.

---

### Post by rubylaser on 2012-04-30
> **wlraider70 said:**
> Is there a difference between POTS, plain old telephone system and PSTN. Are they analog? 

Also since I am using voip that is my connection to my office phones and the FXO port is the connection to the telephone company.

Thanks for the above help too.

edit: If I have about 8 phones in the office and the server is dedicated to PBX what kind of power should it have.

**PSTN** = Public Switched Telephone Network which is owned and operated by the telephone company and delivers **POTS** = Plain Old Telephone Service to you home or business.  POTS connections are analog.

The FXO port would be to connect to the POTS line.

Here's a slightly old Asterisk [dimensioning guide]("http://www.voip-info.org/wiki/view/Asterisk+dimensioning"), but it will be good to get you pointed in the right direction.

---

### Post by johnnyvegas on 2012-04-30
These are nice phones -- Looks like E4 has them for 89.00 :guitar:

[http://www.8774e4voip.com/SearchResults.asp?Search=Cisco+SPA-303+&Search.x=0&Search.y=0](http://www.8774e4voip.com/SearchResults.asp?Search=Cisco+SPA-303+&Search.x=0&Search.y=0)

---

### Post by wlraider70 on 2012-05-01
Thanks for all the help, and for the befit of future users

I followed this guide [http://nerdvittles.com/?p=795](http://nerdvittles.com/?p=795) 
more info at [http://pbxinaflash.net/](http://pbxinaflash.net/)

I installed Centos, PIAF (Pbx in a flash) and incredible PBX3.0  As I understand it each one sits on top of the previous. 

It is extremely easy to configure, thought the install scripts had a few glitches. I have already made soft phone to soft phone calls and soft phone to cell phone via Google voice.

---

### Post by rubylaser on 2012-05-01
PBX in a Flash is great and so much easier than configuring this all by hand like I used to do in the past.  Glad you got it working.

---

