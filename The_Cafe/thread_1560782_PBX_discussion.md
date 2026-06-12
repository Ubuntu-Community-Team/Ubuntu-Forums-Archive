---
title: "PBX discussion"
date: 2010-08-25
forum: The Cafe
---

### Post by epsolon77 on 2010-08-25
I know there are a lot of us out here that have either had problems with a proprietary PBX, or use or want to create a PBX.  So lets discuss the pro's and con's to Asterisk, Yate, FreeSWITCH and any other topics and issues relating to phone systems and going open source.

---

### Post by epsolon77 on 2010-08-25
I personally have been playing around with Asterisk and have found the possibilities truly drool worthy.  The fact that I can tell the system to route however I need without complicated undertones our current PBX has makes it much more manageable for me.  Apparently you can also connect your PBX to Skype too, though I am not sure if video can pass through asterisk.  In any case the lack of licensing fee's are a big plus.  The estimate for adding something like 20 SIP trunks to our system topped 5 grand, and I can buy most of a new Asterisk system for that cost.  While I haven't done much testing with voice, I have gotten faxing up and running by adding a Hylafax system on to Asterisk, (using Asterisk as a call bridge between the FXS ports on our current PBX).  Voice quality through that seems good enough, but I haven't really tested the SIP phones.

---

### Post by TNT1 on 2010-08-25
> **epsolon77 said:**
> I personally have been playing around with Asterisk and have found the possibilities truly drool worthy.    Have a play around with [http://www.ebox-platform.com/](http://www.ebox-platform.com/) for drool worthy possibilities...

---

### Post by epsolon77 on 2010-08-25
Ebox does seem pretty cool.  It doesn't sound like a full featured PBX though.

---

### Post by TNT1 on 2010-08-25
> **epsolon77 said:**
> Ebox does seem pretty cool.  It doesn't sound like a full featured PBX though.  Dunno what constitutes a full featured PBX, but EBOX does a lot. VoIP server      Voicemail     Conference rooms     Calls through an external provider     Call transfers     Call parking     Music on hold     Queues     Logs   It also supports DID's, oh, and I've used it as a simple ATA in the past... Probably does more, but I am not very technical.

---

### Post by epsolon77 on 2010-08-25
TNT you are correct, it does actually have an install of asterisk.  They didn't say much about it, it seems buried in a screen shot somewhere.  That's pretty neat that you get an install of all that in one fell swoop!  What version of ebox are you using?

---

### Post by juancarlospaco on 2010-08-25
**[http://www.debpbx.org/](http://www.debpbx.org/)**

Dah most rule*-able* rules that rule the Rulez
and you will also learn spanish :D

---

### Post by lz1dsb on 2010-08-27
I've always wanted to start a softswitch (like Asterisk and the others, mentioned in this thread) at my brother's server. He has a phone line in his house and a nice internet connection. So I need to buy some FXS capable interface card for the server. So I would be able to initiate and receive calls from a SIP client in a VPN tunnel to the server. So far I haven't got the time to do this though...
But anyway, I didn't know that there're so many alternatives to Asterisk... So this threat was quite informative for me...

---

### Post by epsolon77 on 2010-08-27
lz1dsb, actually most of the options presented here have all been asterisk.  Ebox, elastix,and most others are just asterisk with other packages and a front end...  However Yate and FreeSwitch are two alternitives.  

Personally I've been playing with elastix and it is a very nice package.  It includes a ton of useful phone system based features.  Ebox is pretty cool too, but not focused twords phone functionality.  

For the cards, in order to receive an incoming call from the PSTN you need an FXO port.  To have a call ring to a standard analog phone you need an FXS port.  I highly recomend the Sangoma line of cards.  A 4 port card with 4 active FXO ports and hardware echo cancellation runs about 650, so it's not cheap.  The price on an FXS set should be similar.

---

### Post by sdowney717 on 2010-08-27
nothing to do with PBX I guess,  but I just signed up with sipgate for another free incoming line, outgoing is 1.9cent per minute.
people can call me and I configured my second line on the Linksys 2102 ATA to use a standard phone.
my other voip is voipvoip.com same rate but i pay 6$ per month for the phone number and this is cheaper so I might switch entirely.

Still looking for free incoming and outgoing using the standard phone with ATA but not finding it.

---

### Post by lz1dsb on 2010-09-03
> **epsolon77 said:**
> ...echo cancellation runs about 650, so it's not cheap.  The price on an FXS set should be similar.
650 for what currency we're talking about? Euros, Dollars, or else?
I'm just currious...

Cheers,
Boyan

---

### Post by epsolon77 on 2010-09-03
My bad.  I'm one of those Americans who forgets that there is a hell of a lot more to the English Language than America.  I'm talking USD (United States Dollars)

---

