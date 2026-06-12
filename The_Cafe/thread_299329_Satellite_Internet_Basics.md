---
title: "Satellite Internet Basics?"
date: 2006-11-14
forum: The Cafe
---

### Post by tonyr1988 on 2006-11-14
I've got a friend that's going to be getting satellite Internet soon (dropping dial-up), and asked me for help - they want to just know what to expect and would also like to setup wireless (going to get a laptop soon). Problem: I've done wireless networking and stuff before, but I've never seen a satellite Internet hookup - only dial-up and cable.

So....how does a satellite connection hookup? I've Google'd it, but most sites just explained how data was transferred from the satellite and back, but not about what happens when it gets to your house.

Thanks a lot

---

### Post by woedend on 2006-11-14
they are all now i believe 2 way and work similarly(ie, satellite to some kind of 'modem', then it will use ethernet or usb, most likely ethernet).  
i personally would strongly stay away from it.  everytime it gets too cloudy/rainy, kiss your internet goodbye.  And your lag time on average is horrible, so while speeds may be nice, responsiveness will NOT be.
not to scare you off though, let me know how he likes it.

---

### Post by tonyr1988 on 2006-11-14
Yeah, I've heard pretty negative things about it, but I think they're stuck in a "dial-up or satellite" situation (I was, too, until I moved a few months ago - whew).

I'm sure they'll get everything they need from the satellite company, I just wanted to make sure:

1) there wouldn't be any extra costs to worry about (modem, of course), and
2) it wouldn't change anything about wireless networking.

---

### Post by kuja on 2006-11-14
Satellite internet eh? 
Mine uses a satellite modem which connects to my router via ethernet. 

If it starts raining hard the connection is lost :( 
Response time blows (Lets say I ping google (a reasonably fast server)... ping time will be in the 1300ms range)
Download speed is decent, but if you have any intent to do much downloading, watch out for "Fair Access Policies" or similar. You often won't even be informed about said policies. *grumbles*
Upload speed leaves something to be desired.

---

### Post by BoyOfDestiny on 2006-11-14
> **kuja said:**
> Satellite internet eh? 
Mine uses a satellite modem which connects to my router via ethernet. 

If it starts raining hard the connection is lost :( 
Response time blows (Lets say I ping google (a reasonably fast server)... ping time will be in the 1300ms range)
Download speed is decent, but if you have any intent to do much downloading, watch out for "Fair Access Policies" or similar. You often won't even be informed about said policies. *grumbles*
Upload speed leaves something to be desired.

Ugh, same here. Anyway, currently using Hughesnet (and I hope to DSL will one day come to this area...) The positive thing I will say though, is that I activated the modem via firefox on ubuntu. No funky software required. Just activate, hook to your router, and enjoy the higher speed, ridiculous Fair Access Policy, and high latency, and unreliability in weather, not to mention a somewhat large monthly fee... 

Yes I'm bitter. I had cable but moved after uni... My top download speed was 3-4x, and the download upload cap 40gig/10gig a month... Also less than 1/2 the price... 

I know, dish is faster than dial up ( I can get around 130kB/s), and I've used 300baud modems back in the day... Just don't expect to be able to download an ubuntu.iso in one go. I had to resume several times with wget (which rocks) Since you'll get capped for 10-12hours to 5kb if you exceed a certain number of MEGABYTES in a few hour period...

---

### Post by mips on 2006-11-14
As long as it has an Ethernet port it will be easy to set up. it's like seting up to a normal adsl router etc. you just configure ip, netmask, gateway, broadcast addresses and thats it. Unless it requires one of those proprietory pieces of software. Best you get details on the Sat router & ISP to get a better overview.

Technology used is VSAT (Very small aperture terminal) and it is bi-directional.

Latency is VERY bad, thus it is not good for stuff like VoIP, Online Gaming etc.

If it rains or heavy cloud cover (this could be on either side of the sat connection) you loose your connection.

I played with it 2yrs ago and was not impressed to say the least. Something I would avoid at all cost if possible.

How far does he live from the nearest place that has cable/adsl ? How far does he live from you ? What you could consider is using long range wireless to get to the closest adsl/cable point. Basically use wireless as a extender technology. Requires two APs & high gain antennas.

---

### Post by dsimpson on 2007-01-19
True, latency is an issue, but I don't know where all the other complaints come from. If it is a choice between dialup and satellite, I had both and satellite is the choice for me. Weather is an issue sometimes, I live in the NW and rain, snow, clouds are often present, but besides having slow downloads during such times, I have only on 2 occasions lost internet service. My upload is 250-260k and download speeds are 1.5m, but you have to check the satellite companies and see what they provide. The biggest drawback is the cost. It is easy to set up, ethernet from the satellite modem to the router or computer and the installer will set up the connection to the internet and get you signed into your satellite webpage and email, then all you do is click on firefox or opera (your webbrowser of choice) and begin surfing.

---

### Post by MonkeyWrench32 on 2007-01-19
I've had satellite internet for years (DirecPC/DirecWay/HughesNet).  I'd only recommend it if you have no other options for broadband.  I absolutely hate the (un)Fair Access Policy.  My signal very rarely drops out (only in very bad weather).  Networking with standard hubs and routers (both wired and wireless) are very easy.

---

### Post by STREETURCHINE on 2007-01-19
> **woedend said:**
> they are all now i believe 2 way and work similarly(ie, satellite to some kind of 'modem', then it will use ethernet or usb, most likely ethernet).  
i personally would strongly stay away from it.  everytime it gets too cloudy/rainy, kiss your internet goodbye.  And your lag time on average is horrible, so while speeds may be nice, responsiveness will NOT be.
not to scare you off though, let me know how he likes it.

i use two way sat (in australia though)but the cloudy days are no problem my foxtel t.v cuts out but my internet connection is always fine,lag time is only a problem if you voice chat or phone through the internet,(we have voise here for voice over protocol)speeds are good ,so i think since we aussies are so far behind the rest of the world when it comes to the net..
 it should be fine in the US.of.A

we have just been through the worst storm for 50 years here and still had the net (220 ml in 48 hours )  :D

---

### Post by jago25_98 on 2009-05-31
Urchin, how much did it cost to get set up and the ongoing costs? Just out of interest (I'm in Europe)

I'd like 2 way data using a non directional antenna for use with a moving boat. What I don't understand is why the non directional connections are charged per mb, whereas parabolic antenna setups are available with monthly deals

---

### Post by XubuRoxMySox on 2009-05-31
We're using **[COLOR="Blue"]WildBlue[/COLOR]** at our house. The satellite modem connects to an ordinary wireless router by means of one ethernet cable. It's prob'ly no different from a cable modem or a DSL one.

But the (un)Fair Access Policy is really stupid. We share five computers in the house and we're home a lot (we home school), so we ordered the "maximum" package, which promises better speed as well as increased usage.

The speed beats dialup for sure! And it's nice not to have to take turns dialing in and tying up the phone lines. But one download of Ubuntu and **POW**. "FAP" warning, threatening to slow us down to dialup speed for 30 days if we exceed our allowable usage.

At least dialup was unlimited. So I use the dialup connection to download any big files overnight. But it's a pain in the butt.

---

### Post by mips on 2009-05-31
> **jago25_98 said:**
> Urchin, how much did it cost to get set up and the ongoing costs?...

That user has not been back to these forums since June 2007...

---

### Post by joel383 on 2009-06-29
> **dixiedancer said:**
> We're using **[COLOR=Blue]WildBlue[/COLOR]** at our house. The satellite modem connects to an ordinary wireless router by means of one ethernet cable. It's prob'ly no different from a cable modem or a DSL one.

But the (un)Fair Access Policy is really stupid. We share five computers in the house and we're home a lot (we home school), so we ordered the "maximum" package, which promises better speed as well as increased usage.

The speed beats dialup for sure! And it's nice not to have to take turns dialing in and tying up the phone lines. But one download of Ubuntu and **POW**. "FAP" warning, threatening to slow us down to dialup speed for 30 days if we exceed our allowable usage.

At least dialup was unlimited. So I use the dialup connection to download any big files overnight. But it's a pain in the butt.


i'm an installer for hughes-net, direct tv, and dish network, and soon wild blue

if you guys have any questions about it just ask... 

as for latency, it is always going to be there because of the round-trip to the satellite. but it should not be much more than about 1000ms, about one second. i'm sure those in the dial-up or satellite quandary will agree that the latency is negligible compared to the speed upgrade they are recieving.

hughes Fair Access Policy (FAP) resets every day, while  wildblue is a monthly limit.
hughes 1 wildblue 0

hughes has unlimited FAP between 1am-6am

granted this site is biased towards hughes, but it has quite a bit of info.
[http://www.directsatbroadband.com/hughes-net-vs-wild-blue.html](http://www.directsatbroadband.com/hughes-net-vs-wild-blue.html)

---

