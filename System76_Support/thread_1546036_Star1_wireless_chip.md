---
title: "Star1 wireless chip"
date: 2010-08-04
forum: System76 Support
---

### Post by Vrekk on 2010-08-04
Hi, I was planning on upgrading the wireless in my house to wireless N because of its farther range and higher speeds, but I noticed that the wireless chip in the star1 does not support wireless N, (unless my sources are wrong, which is a possibility :o). Due to that and its , shaky at best, wireless drivers, I was wondering if it was possible to upgrade the internet chip in the star1. I would really rather not have to use a usb adapter if at all possible. 

Any help would be great.

---

### Post by jml on 2010-08-05
I own a first generation Starling as well.  There are not many user installable upgrade options on this netbook. There is only one small panel on this unit with no indication as to what lies beneath.  I suspect that you would have to at least partially disassemble the Starling to get access to the wireless card.  Hopefully one of the System 76 staff will chime in and answer your question more difinitively than I can.

Joe

---

### Post by isantop on 2010-08-05
That's about right. The Star1 is a pretty restrictive system as far as hardware goes. I'd stick with wireless G.

Most routers supporting wireless N support "Mixed Mode" where the fastest connection type available on a certain device is used. That way, you could upgrade the network to be more future proof, and get the benefit on other devices. Just make sure the router you get has this feature.

---

### Post by Vrekk on 2010-08-05
> **isantop said:**
> That's about right. The Star1 is a pretty restrictive system as far as hardware goes. I'd stick with wireless G.

Most routers supporting wireless N support "Mixed Mode" where the fastest connection type available on a certain device is used. That way, you could upgrade the network to be more future proof, and get the benefit on other devices. Just make sure the router you get has this feature.

I know that almost all N routers are backwards compatible with G, but the Star1 is the one that really needs the wireless N boost. It can't connect to my AC with wireless G from my desk, where i need it the most :|

> **jml said:**
> I own a first generation Starling as well.  There are not many user installable upgrade options on this netbook. There is only one small panel on this unit with no indication as to what lies beneath.  I suspect that you would have to at least partially disassemble the Starling to get access to the wireless card.  Hopefully one of the System 76 staff will chime in and answer your question more difinitively than I can.

Joe I took that part off the other day and it looks like a spot where you can add in a wireless (as in 3g) chip. I'm not sure though.

---

### Post by isantop on 2010-08-05
You might try Running restore again from the System76 Driver. Sometimes that clears this up, and there are definitely some fixes for Starling Wireless

---

### Post by Vrekk on 2010-08-05
> **isantop said:**
> You might try Running restore again from the System76 Driver. Sometimes that clears this up, and there are definitely some fixes for Starling Wireless
Even though this is the Ubuntu fourms, I don't use Ubuntu, and therefore don't use the driver. I have a hacked version of it to use with Arch so I'm running the same wireless driver that system76 has to offer. The linux support for the wireless card in the star1 (and maybe 2, not sure) has always been shakey, and System76 made it usable (you should use it before you apply the system76 driver :D), but I have given up on this card. Thats why I'm trying to see if I can replace/upgrade it without a usb.

I'm not scared to take a screw driver to my computer, but I just want to know if it can be done before I destroy my warranty with no reason

---

### Post by isantop on 2010-08-06
I believe it *can* be done, but it will violate the warranty, and it could be built in to the motherboard. At any rate, you'll practically have to tear the entire computer apart to get at it.

Also, as a quick reference: The old Starling is the Star1, the EduBook is Star2, and the new one is Star**3**. I know, it's weird. Same deal with the old, new and Ion Meerkats.

---

### Post by Vrekk on 2010-08-10
I figured it out, and for anybody else who may be wondering the same thing, the wireless card is removable (and should therefore be replaceable)  and is a pci express mini card.  Now just to buy a wireless N version and be rid of this card.

---

### Post by Vrekk on 2010-08-10
Sorry for double post, but I noticed other thing I need to ask system76 about the card. When I was putting it back together, I saw that there was only a cable for the "main" plug on the card, and not the aux? Why is this?

---

### Post by jml on 2010-08-10
Usually the two leads go to two separate antennas.  It's possible that the Starling only has one antenna.  Just a guess.

Joe

---

### Post by Vrekk on 2010-08-10
> **jml said:**
> Usually the two leads go to two separate antennas.  It's possible that the Starling only has one antenna.  Just a guess.

Joe

I noticed that, but the Starling has two, I found that there is another cable, but it is no where near long enough to reach the aux. Its wired to the spot under the panel under the netbook (the only thing that looks like its made to be upgraded), which makes me think all the more that that spot is meant for a 3g card.

EDIT: Well auctally I might just be able to throw another wlan card in there.

---

### Post by thomasaaron on 2010-08-11
Nope. You were right the first time. 3G card.

---

### Post by Vrekk on 2010-08-11
> **thomasaaron said:**
> Nope. You were right the first time. 3G card.

Sweet!  I moved the internal card to the slot that was ment for the 3G card (before I read your post), and was able to plug the attena made for the 3g card in the aux slot while I put the main in the main and I got a huge signal bost! I can use my netbook in my room again! Ya! Anyone who doesn't care about a warenty and has bad signal might what to try this (at their own risk of course)

---

### Post by Vrekk on 2010-08-21
Sorry for bringing up an old thread, but I wanted to tell anybody else who want to try this (at there own risk, this will break your warranty) that I was able to buy a Intel 5100 mini pci express card and have it work flawlessly. :D

For anybody else who wants to try this:
[http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html](http://www.vrekk.us/2010/08/taking-apart-system-76-star1.html)

---

### Post by t.schutter on 2010-08-26
Vrekk,

When you installed the Intel 5100 mini pci express card (which I am assuming is an Intel 512AN_MMWW2), did you get the signal boost from comment #13 from just hooking up just the one antenna (main)?

---

### Post by Vrekk on 2010-08-27
> **t.schutter said:**
> Vrekk,

When you installed the Intel 5100 mini pci express card (which I am assuming is an Intel 512AN_MMWW2), did you get the signal boost from comment #13 from just hooking up just the one antenna (main)?

With the RTL8187B chip I got a small to medium sized boost in strength by moving it to the 3g card slot and using both the normal wireless Anetta for the main and the one meant for 3g in the aux, but I do not recommend this unless you like trouble shooting hardware.  

With the Intel chip (yes it is an Intel 512AN_MMWW2), I got a fairly large signal boost (compared to the RTL chip) by installing it where the RTL chip originally was and only hooking in the main antenna. And that signal boost is before upgrading the router in my house to Wireless N.

---

