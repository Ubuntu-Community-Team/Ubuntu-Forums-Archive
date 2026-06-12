---
title: "Making your own lan: 568A vs 568A"
date: 2011-11-01
forum: The Cafe
---

### Post by Dry Lips on 2011-11-01
Hi boys and girls!
 

 I've gotten hold of quite a bit of CAT6 cable, and I'll be making my own lan for the first time. 
This is how the setup is going to be:
  
 **Wireless router** -&#8211;> cable --&#8211;> **Switch** &#8211;-> cable (x2) ---> **computer 1 & 2**.  
 
So I just thought I'd ask some of you who have done this before how the setup is done. 

 **a )** Would I have to make a ***crossover cable*** between the *wireless router* and the *switch*? (568A/568B)
 
**b)** Between the *switch* and the *computers* I make a couple of ***straight-through cables***? (568B/568B)
 
Thanks in advance!
Dry Lips :)

---

### Post by mips on 2011-11-01
Pick one standard and stick to it! Either way is good.

Coming from a Telco environment everything was 568A terminated. I see the US National Communication Systems Federal Telecommunications Recommendations do not recognize T568B termination either.

If your switch/router has gigabit ethernet ports then you don't need a x-over cable as auto-mdix will be implemented in the silicone. You also don't need a x-over cable if one of the devices has a mdix switch. If you have none of the above you will require a x-over cable.

[http://joncamfield.com/oss/schooltools/Reference/EthernetCabling.htm](http://joncamfield.com/oss/schooltools/Reference/EthernetCabling.htm)

---

### Post by CharlesA on 2011-11-01
I run gigabit switches on my network so I don't have to worry about the crossover cable problem. Auto-MDIX = win.

Stick with one standard and run with it.

---

### Post by Dry Lips on 2011-11-01
Thanks for replying guys!

The switch is 1 gigabit, but the lan ports on the router is only 10/100M...
However, according to the manual there's "[I]Auto MDI / MDI-X function for 
all wired Ethernet ports[/I]". Does that mean I can use straight-through cables
even though the router hasn't got gigabit ports?

---

### Post by haqking on 2011-11-01
out of interest, why not put computers 1 and 2 straight to the router ?

or does it have limited ethernet ports ?

most home routers these days are already a switch

---

### Post by CharlesA on 2011-11-01
> **haqking said:**
> out of interest, why not put computers 1 and 2 straight to the router ?

or does it have limited ethernet ports ?

most home routers these days are already a switch
The router is 10/100 and they want gigabit speeds. I do the same at home since I can't be bothered getting a better router.

---

### Post by haqking on 2011-11-01
> **CharlesA said:**
> The router is 10/100 and they want gigabit speeds. I do the same at home since I can't be bothered getting a better router.

ha just seen that now, in his second post ;-)

cheers

---

### Post by Dry Lips on 2011-11-01
> **haqking said:**
> out of interest, why not put computers 1 and 2 straight to the router ?

or does it have limited ethernet ports ?

Because computers 1 & 2 are located in office #2 at the other end of our house... ;)
Though I could probably also plug computer 1 into the router, and share the network
connection from computer 1 --> 2...

---

### Post by Dry Lips on 2011-11-01
Okay, thanks guys! Since both the router as well as the switch supports [I]auto MDI-x,
[/I]I'll go make some nice straight  **568A **cables [B]... Cheers!
[/B]

---

