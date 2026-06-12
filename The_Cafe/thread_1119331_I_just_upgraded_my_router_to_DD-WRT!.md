---
title: "I just upgraded my router to DD-WRT!"
date: 2009-04-07
forum: The Cafe
---

### Post by smartboyathome on 2009-04-07
I have a Linksys WRT54G router which I thought was dead (due to it not broadcasting a wireless signal), and had bought a WRT54G2 as a replacement for months ago. Today, I decided to see if flashing the firmware with DD-WRT would make it work again, since someone suggested that corrupt firmware might be the problem. Lo and behold, it works! Even better, bandwidth monitoring so I don't have to worry about going over [s]Comcrap's[/s] Comcast's limit. I have officially retired my WRT54G2 for now, since the WRT54G works better, and actually gives me better signal strength! :D

---

### Post by Giant Speck on 2009-04-07
EDIT:  Feh.

---

### Post by MikeTheC on 2009-04-07
DD-WRT firmware is substantially better than any of the manufacturers' commerical-product firmware, in my experience.

If you look through there, you will notice (among other things) the ability to increase or decrease the signal strength from the router, and you'll also find your router's report on how strong your computer's WiFi signal is from the *router's* perspective.

I've got a Buffalo WHR-HP-G54 that I put the firmware on, and frankly I couldn't be happier.

---

### Post by FuturePilot on 2009-04-07
> **MikeTheC said:**
> DD-WRT firmware is substantially better than any of the manufacturers' commerical-product firmware, in my experience.

If you look through there, you will notice (among other things) the ability to increase or decrease the signal strength from the router, and you'll also find your router's report on how strong your computer's WiFi signal is from the *router's* perspective.

I've got a Buffalo WHR-HP-G54 that I put the firmware on, and frankly I couldn't be happier.

+1. The stock Linksys stuff is terrible. It doesn't give you many options or control over it. I put DD-WRT on my WRT54GSv7 and I love it.

---

### Post by Stupendoussteve on 2009-04-07
Congrats :)

I have been using the WRT54G with hacked firmware since a little after it was introduced, and even bought a second one in order to extend my one network connection around the house so I can use ethernet in my office. They are powerful little boxes.

If you like DD-WRT you might enjoy [Tomato]("http://www.polarcloud.com/firmware"), it is a bit easier to configure and use, and offers a bit more interactivity in its interface (live updating traffic graphs, for example).

---

### Post by jpeddicord on 2009-04-07
> **Stupendoussteve said:**
> Congrats :)

I have been using the WRT54G with hacked firmware since a little after it was introduced, and even bought a second one in order to extend my one network connection around the house so I can use ethernet in my office. They are powerful little boxes.

If you like DD-WRT you might enjoy [Tomato]("http://www.polarcloud.com/firmware"), it is a bit easier to configure and use, and offers a bit more interactivity in its interface (live updating traffic graphs, for example).

+1. I'm quite a Tomato fanboy myself.

---

### Post by smartboyathome on 2009-04-07
> **Stupendoussteve said:**
> Congrats :)

I have been using the WRT54G with hacked firmware since a little after it was introduced, and even bought a second one in order to extend my one network connection around the house so I can use ethernet in my office. They are powerful little boxes.

If you like DD-WRT you might enjoy [Tomato]("http://www.polarcloud.com/firmware"), it is a bit easier to configure and use, and offers a bit more interactivity in its interface (live updating traffic graphs, for example).

Eh, I'm not going to mess with anything on it. It is working great with DD-WRT, so why change it? ;)

Also, I can't find where the wireless signal strength config is with the v24-sp1 release. Anyone know where to find it? :)

---

### Post by MikeTheC on 2009-04-07
> **smartboyathome said:**
> Eh, I'm not going to mess with anything on it. It is working great with DD-WRT, so why change it? ;)

Also, I can't find where the wireless signal strength config is with the v24-sp1 release. Anyone know where to find it? :)

Yeah, hang on a sec...

EDIT: Wireless -> Advanced Settings -> TX Power

---

### Post by smartboyathome on 2009-04-07
> **MikeTheC said:**
> Yeah, hang on a sec...

EDIT: Wireless -> Advanced Settings -> TX Power

Thanks! It is set at 70 by default, I tried raising it to 140 but that didn't seem to do much for the range. :(

---

### Post by gletob on 2009-04-08
> **smartboyathome said:**
> Thanks! It is set at 70 by default, I tried raising it to 140 but that didn't seem to do much for the range. :(

I think someone told me a while ago putting up the power just makes the AP visible farther away but the range of the adapter limits the ranges

I had a old belkin with DD-WRT but it died (Damn puppy killed the toaster and my laptop AC adapter too)

---

### Post by LookTJ on 2009-04-08
> **smartboyathome said:**
> Thanks! It is set at 70 by default, I tried raising it to 140 but that didn't seem to do much for the range. :(Whoa! Be careful!!

84mW should  be fine

otherwise, look at [http://dd-wrt.com/wiki/index.php/Index:FAQ#How_high_should_I_set_the_transmit_power_on_my_router.3F](http://dd-wrt.com/wiki/index.php/Index:FAQ#How_high_should_I_set_the_transmit_power_on_my_router.3F)

---

### Post by MaxIBoy on 2009-04-08
I've always wanted the ability to SSH into my router from school and send a reboot-over-LAN signal to my server in case it crashes. Not that I've ever needed that feature, mind you-- It would simply give me some peace of mind. It's on my list of things to do.


Still, setting up a dynDNS server on a router must not be easy...

*Google*

Nevermind, it'll be a piece of cake.


Heh, I wonder if my router'll run Doom.

---

### Post by zmjjmz on 2009-04-08
Gotta love DD-WRT. I have it on my WRT54GS, and it's never been better.

---

### Post by kevdog on 2009-04-08
I'll be the first to say it?  What took you so long??  dd-wrt/tomato/prior versions such as Seaveas/etc have been around for such a long time!!! To not upgrade your compatible router is just plain ludicrous.  

Lastly, if you are interested, follow the developments between ddwrt and tomato.  A lot of the developers have left the ddwrt project due to internal fighting of the vision of where ddwrt is going.  There are rumors it wants to become a for-profit venture closing some of the source.  Tomato at this time seems to have no such vision.  Disapproving developers jumped shipped.  

I use ddwrt because it seems more fully featured currently, however it will be interesting how the projects continue to evolve with time!

---

### Post by FuturePilot on 2009-04-08
> **kevdog said:**
>  

Lastly, if you are interested, follow the developments between ddwrt and tomato.  A lot of the developers have left the ddwrt project due to internal fighting of the vision of where ddwrt is going.  There are rumors it wants to become a for-profit venture closing some of the source.  Tomato at this time seems to have no such vision.  Disapproving developers jumped shipped.  

I've done some researching on those rumors and as far as I can tell none of them are true.

---

### Post by kevdog on 2009-04-08
FuturePilot

I hate spreading rumors, however I did run across a site a ways back were a bunch of the current/former coders for ddwrt were commenting.  There seemed to be a large riff.  Again however it was difficult to make sense of the contexts of there arguments since nothing was spelled out in black and white.  If I run across the link I'll post it. 

I'm not tying to bash either project.  They are both excellent.  I'm just as curious as the next guy however the direction each project will head in the future.  I use ddwrt on a regular basis, however can attest its not a completely bug free product.  I guess every work in project is never completely bug free, but its interesting on the problems you find on the ddwrt forums.  Id actually recommend new users not to peruse the ddwrt forums because you may get the impression that the software is experimental and unstable (which it definitely is not!) based on all the comments made in the forums.  

Hmm, I guess similar attitudes would be had about Ubuntu if you read the forums as well!!! Interesting how the whole concept of a support forum can change overall opinion quickly.

[http://www.bitsum.com/about-ddwrt.htm](http://www.bitsum.com/about-ddwrt.htm)

---

### Post by jpeddicord on 2009-04-08
> **Taylor said:**
> Whoa! Be careful!!

84mW should  be fine

otherwise, look at [http://dd-wrt.com/wiki/index.php/Index:FAQ#How_high_should_I_set_the_transmit_power_on_my_router.3F](http://dd-wrt.com/wiki/index.php/Index:FAQ#How_high_should_I_set_the_transmit_power_on_my_router.3F)

Whoa, yeah, anything above that and you risk your router melting down. I usually don't turn mine up past 70 (default was 54), otherwise I begin to hear a high-pitch noise. Creepy.

---

### Post by kevdog on 2009-04-08
Ive run mine at 200mW for months at a time and nothing has happened.  I eventually reset it because I found no difference in the signal strength range.  I found actually changing the channel to either 1 or 12 made the biggest difference and along with application of the aluminum foil signal director antaneas.

---

### Post by Haiyadragon on 2009-04-08
I ran dd-wrt for a while, but every once in a while the webserver would crash and I had to ssh in and reboot the thing. Also, the web interface seems very slow and cluttered.

I now run Tomato and it's much faster, easier to use and hasn't crashed on me yet.

---

### Post by smartboyathome on 2009-04-08
> **kevdog said:**
> I'll be the first to say it?  What took you so long??  dd-wrt/tomato/prior versions such as Seaveas/etc have been around for such a long time!!! To not upgrade your compatible router is just plain ludicrous.

What took me so long? Worrying I would brick the router like I break other electronic devices. Once I got another router, I was free to play around with this broken one all I wanted, as there was no worrying if I broke it.


> **kevdog said:**
> I use ddwrt because it seems more fully featured currently, however it will be interesting how the projects continue to evolve with time!

Ditto. If only someone had a demo dummy Tomato interface up, for people like me who just want to check it out. ;)

---

### Post by Thelasko on 2009-04-08
> **smartboyathome said:**
> What took me so long? Worrying I would brick the router like I break other electronic devices. Once I got another router, I was free to play around with this broken one all I wanted, as there was no worrying if I broke it.

Yeah, that's one of my main reasons for not doing this.  The wife-to-be would kill me if I broke the internet.

Plus I have one of the new WRT54G routers that apparently doesn't work DD-WRT.  It's been frustrating me lately as every once and a while I can't access the http interface.  I went to reset it, and accidentally *reset* it back to factory defaults.  That was a pain to fix.

---

### Post by John.Michael.Kane on 2009-04-08
> **smartboyathome said:**
> Ditto. If only someone had a demo dummy Tomato interface up, for people like me who just want to check it out. ;)

This site [Virtual Tomato GUI]("http://lampiweb.com/tomato/status-index.htm") should give you an impression of the Tomato Firmware.

---

### Post by smartboyathome on 2009-04-08
> **Thelasko said:**
> Yeah, that's one of my main reasons for not doing this.  The wife-to-be would kill me if I broke the internet.

Plus I have one of the new WRT54G routers that apparently doesn't work DD-WRT.  It's been frustrating me lately as every once and a while I can't access the http interface.  I went to reset it, and accidentally *reset* it back to factory defaults.  That was a pain to fix.

You have the WRT54G2, then. It has recently been able to be used with DD-WRT (not anything else, but once you get DD-WRT on there, you can flash it with <insert firmware here>). See [these instructions]("http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G2") on how to install it. I still am not daring to touch *my* WRT54G2 with DD-WRT, though, as it is more complicated and I don't want to brick that one.


By the way, thanks for the link to the Virtual Tomato GUI. After trying it out, I figure that I am going to just stick with DD-WRT. ;)

---

### Post by FuturePilot on 2009-04-08
> **smartboyathome said:**
> What took me so long? Worrying I would brick the router like I break other electronic devices. Once I got another router, I was free to play around with this broken one all I wanted, as there was no worrying if I broke it.


Bah, I like to live on the edge. I only have 1 router and a couple of months ago I just decided to do it and held my breath. :p

But seriously I can understand that. I've had my router for a over a year and I just recently put dd-wrt on it. I didn't do it sooner because it was working fine and it was under warranty so that pretty much would have voided the warranty. But since it no longer is I said what the heck. Now it works even better. :D

---

### Post by kamitsukai on 2009-04-08
I've been looking at getting a router to put tomato on but I think I might go for that new Fon router thats coming out at the end of april =]

---

### Post by Helios1276 on 2009-04-08
DD-WRT turned my rubbish WRT160N into a use-able router! However, XBL seems to still hang though that could be a number of things.

---

### Post by cardinals_fan on 2009-04-08
I have one of those too, and I also thought mine was dead.  However, I just ripped mine open, so I don't think it will be used anytime soon.

---

### Post by MikeTheC on 2009-04-08
> **Thelasko said:**
> Plus I have one of the new WRT54G routers that apparently doesn't work DD-WRT.

Yeah, not much you can do about that. However, you can still buy the WRTG4GL, which will work flawlessly with DD-WRT. Several months ago a friend bought one and we set it up with DD-WRT. He was very happy with it.

Also, if you have enough RAM on your router (say, at least 4MB) you can pick from one of the two slightly specialized versions of the full firmware and have either a VPN server or a VOIP server native and built into the router.

---

### Post by smartboyathome on 2009-04-15
Now I'm starting to wish I had never upgraded my router. Every few days, it stop working, and I have to restart it. To top it all off, I can't run Tomato on it, apparently the devs of Tomato just hate WRT54Gv6, and so they didn't even bother trying. Looks like I will ahve to switch back to the old router soon, which is bad since I won't have all the features I [s]want[/s] need. :(

---

### Post by pwnst*r on 2009-04-15
I have a WRT150N which is my main router on DDWRT and a WRT54GL running DDWRT as a bridge.  The WRT54GL is installed behind my plasma and is used for my xbox 360 and ps3.  lol @ microsoft's $99 wireless adapter.

---

### Post by jpeddicord on 2009-04-15
> **smartboyathome said:**
> Now I'm starting to wish I had never upgraded my router. Every few days, it stop working, and I have to restart it. To top it all off, I can't run Tomato on it, apparently the devs of Tomato just hate WRT54Gv6, and so they didn't even bother trying. Looks like I will ahve to switch back to the old router soon, which is bad since I won't have all the features I [s]want[/s] need. :(

The problem is that the v5/6/7 models have only half of the onboard NVRAM and RAM to use. Tomato *is* lightweight, but it does need the full RAM that the L or <v4 models provide. The same applies to DD-WRT: while you can run the "micro" edition, it might not perform as well as you would expect when using a non-crippled router.

---

### Post by smartboyathome on 2009-04-15
> **jacobmp92 said:**
> The problem is that the v5/6/7 models have only half of the onboard NVRAM and RAM to use. Tomato *is* lightweight, but it does need the full RAM that the L or <v4 models provide. The same applies to DD-WRT: while you can run the "micro" edition, it might not perform as well as you would expect when using a non-crippled router.

That is sad. I guess I am left with using the crippled router? Or using the new one with the default firmware.

---

### Post by jpeddicord on 2009-04-15
I was stuck in the same situation last year. Finally went out and bought a WRT54GL for around $30 (some Buffalo routers will do as well). They're relatively cheap nowadays; if it is really important to you it might be something worth considering.

---

### Post by Thelasko on 2009-04-16
> **jacobmp92 said:**
> I was stuck in the same situation last year. Finally went out and bought a WRT54GL for around $30

That's a good deal.  I think my crippled WRT54G was $40 and the GL was $60 last I checked.  Where did you get it?

---

### Post by jpeddicord on 2009-04-16
I think Amazon had a promo for them at one point. Just checked Newegg, and yeah, it was $60 retail. Only thing I can say is keep looking. :p

---

