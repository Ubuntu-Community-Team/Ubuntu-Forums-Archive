---
title: "evil wireless router!!"
date: 2008-04-25
forum: The Cafe
---

### Post by nerdman978 on 2008-04-25
My dad finally cracked and decided I deserved a wireless network (internet in my room....YES!!!). Anyway, the router he bought was a  WRT54G router from Linksys. I hooked the router up to my DSL modem and then hooked up another ethernet cable to the desktop computer next to the modem. I then proceeded to install Linksys' lame easy install application (I was lazy)*. After running that I realized that the Linksys router no longer acted like an ethernet hub the way my Netgear hub used to. I couldn't connect to the internet! I could, however, connect to 192.168.1.1 and access the router's settings page. So what do I need to fix in order to access the internet via the wired AND wireless network (I hope to set up a home network with networked printers and hard drives :) ). First; however, I need the internet! I am writing to you on my old setup without the router so that I can use my friend google and Ubuntu Forums to solve this dilemma.

EDIT: I have Verizon DSL and a Westell 6100 Modem
 
*NOTE: This is a Windows (XP) question!

---

### Post by cardinals_fan on 2008-04-25
This should probably be moved to Other OS Talk -> Windows Discussion.

---

### Post by FuturePilot on 2008-04-25
Well what I would do is forget about the easy set up CD. It's probably easier doing it manually. That's what I did. I have a WRT54GS. I didn't even look at that CD, took me 5 minutes to set it up. I tell you what I did, but I have a cable modem so it might be a tiny bit different for you.

This is what I did. I unplugged my modem and waited a couple of minutes. Then I hooked the modem up to the router and plugged the modem back in and waited again for a couple minutes. Then I plugged in the router and waited a couple more minutes. Then I just ran a cable from the router to my main PC and I was online. The rest of my computers are wireless and all that was working too. 

If you do something like that you might want to make sure all the settings in the router are back to the defaults as well as the settings on your computer.

Then make sure you set up some good security.

---

### Post by Jareth on 2008-04-25
Very true. It sounds nuts but the order everything is switched on in is important sometimes.
I used to help people with this at work and it was a nightmare 90% of the time.
Like above says, first connect everything before powering up. Get your computer, connected through the cable to the router, sorted first before you do the wireless. Then the order of switching on should be (if memory serves):

router > modem > computer

Pay attention to the lights when switching on, each piece of hardware should tell you when its ready (you might get a light on the router complaining about not getting a signal until you switch the modem on.

If you're connecting through ethernet no software is required for the computer as the network card will sort everything out.

If all goes well you'll at least have a connected computer and you only have to worry about the wireless side.

---

### Post by nerdman978 on 2008-04-25
Ah. I realized from surfing the web that one of the roots of my problems lies in my modem's configuration (it actually acts as a router at default and I need to disable that), but I forget the user/password combo (it isn't admin/admin). Is there a way to manually reset the Westell 6100 to factory default settings?

---

### Post by FuturePilot on 2008-04-25
> **Jareth said:**
> Very true. It sounds nuts but the order everything is switched on in is important sometimes.
I used to help people with this at work and it was a nightmare 90% of the time.
Like above says, first connect everything before powering up. Get your computer, connected through the cable to the router, sorted first before you do the wireless. Then the order of switching on should be (if memory serves):

router > modem > computer

Pay attention to the lights when switching on, each piece of hardware should tell you when its ready (you might get a light on the router complaining about not getting a signal until you switch the modem on.

If you're connecting through ethernet no software is required for the computer as the network card will sort everything out.

If all goes well you'll at least have a connected computer and you only have to worry about the wireless side.
Very true about the order you turn everything on. I was just going to add that. ;) Everything needs to be connected and powered on in a certain order or else it might give you trouble.

---

### Post by blastus on 2008-04-25
> **nerdman978 said:**
> Ah. I realized from surfing the web that one of the roots of my problems lies in my modem's configuration (it actually acts as a router at default and I need to disable that), but I forget the user/password combo (it isn't admin/admin). Is there a way to manually reset the Westell 6100 to factory default settings?

If you can reset it, there would be a little hole on the back of the router that you can press with a toothpick or something like that and hold it down for several seconds.

The following may help you [Westell 6100 DSL Modem Installation Guide](http://www.lava.net/support/Westell_6100_DSL_Modem_Installation_Guide)

---

### Post by SuperSon!c on 2008-04-26
> **Jareth said:**
> Then the order of switching on should be (if memory serves):

router > modem > computer



actually, it's modem>router>computer if the devices are not powered.  if everything is up, power down the router first, then the modem, then modem>router>computer.  the computer is optional since you can run "ipconfig /release"  then "ipconfig /renew" from a command prompt to negotiate a new IP.

---

### Post by intense.ego on 2008-04-26
> **SuperSon!c said:**
> actually, it's modem>router>computer if the devices are not powered.  if everything is up, power down the router first, then the modem, then modem>router>computer.  the computer is optional since you can run "ipconfig /release"  then "ipconfig /renew" from a command prompt to negotiate a new IP.

I was going to say the same thing. What use is it powering up the router, if there is no modem giving you the internet in the first place.

---

### Post by Jareth on 2008-04-26
> **intense.ego said:**
> I was going to say the same thing. What use is it powering up the router, if there is no modem giving you the internet in the first place.

I agree with what you're saying, it sounded insane to me when I was being told but if it gives you jib doing it that way try it with the router first, as mad as it sounds.
Where I worked the customers were using cable modems and the company decided to make wireless available to them (big mistake). So they just sent out routers for them to attach to the modems. For months it was just no good and there was a groan anytime someone got one of these customers. Plus the fact no one was properly trained on the new kits. When they did select a group of us to take training the trainer showed us both ways (modem first, then router first) and it was always router first then modem. Can't explain the technical side of it, it just worked that way. I probably should add that the routers were netgear not linksys. But it might be the same.

Anyway, sorry to make a massive point on this, but I just wanted to explain my reasoning. I promise I'm not an insane saboteur!:lolflag:

---

### Post by malangaman on 2008-04-26
I had a similar problem and finally solved it by struggling through google and other such online sources.

---

