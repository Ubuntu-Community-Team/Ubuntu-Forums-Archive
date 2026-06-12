---
title: "buying/building Cisco Lab for home"
date: 2008-03-15
forum: The Cafe
---

### Post by Mike'sHardLinux on 2008-03-15
I know there's a few IT pros on these forums. I wonder if any of you that either have or are pursuing CCNA or CCNP would mind giving some advice.

I want to build a Cisco lab. I have a bit of experience with IT, but am new to Cisco and WAN in general. I am taking 2 related classes: Network Technology and Service Integration (telecommunications, VoIP, etc..) and WAN Tech and Application ("Cisco class").

I have found [ciscokits.com]("http://www.ciscokits.com") and am considering buying a kit to make it easier on myself. Have any of you used them? I also posted a WTB ad on craigslist to see if there's anything available locally.

The only advice I've found online is generally just sales pitches..."We've put together these pieces because blah blah".  But what have you used? I am open to suggestions for vendors, specific models I should get or avoid, specific configurations for the equipment(Ie, minimum IOS version I should get), etc... Basically any advice you have...I'll listen. 

I know I'll need certain cables, WIC modules, etc... My budget is in the $1000+ range.

Thanks!

---

### Post by mrsteveman1 on 2008-03-15
I have a CCNA since last year

In school we worked on 2621xm routers, 2950 series switches, and some of the higher up stuff etc.

What is it you want to have around? There are 2 simulators that work quite well for most things, Boson makes one that can be used for a lot of the models (not the high end ones), and Cisco provides PacketTracer which is ok for what its supposed to do, some features are missing (isdn i think).

If you actually buy a device from Cisco you should get an account with them and access to the newest IOS versions for your device, so that shouldn't be a real problem. As long as whatever you buy supports the stuff you need to work on, the version isn't a real problem anyway because its not a production environment.

I do know you can pickup the 2600 routers and the 2950 switches pretty cheaply though i believe both are currently close to EOL if not already.

---

### Post by Mike'sHardLinux on 2008-03-15
Thanks for the reply, Steve!

I have the Cisco CCNA network simulator that came with the CCNA ICND book. I can't get it to install in Vista, although it does in XP, but it gave an error during install. I'll look into the Boson simulator.

I will use the simulators, but I still want to have the real thing at home. My teacher told me that the simulators cover a lot of the features, but there are some things they don't do that the real equipment does. I want to learn this equipment inside and out. Plus, I have to admit there's kind of a wow factor with having a rack of Cisco equipment that is kind of inspiring for a computer nerd like me.

At my school, we have the 2950 switches. I forgot the router model #, but they have compact flash slots on the front. My main concern is I want to get equipment I can use to learn so I can get CCNA, and possibly later, CCNP certified. I know the standards change, but I also  know there's no point in getting equipment that doesn't support features I need to learn. I believe the 1900 series switches are still usable, and the 2600 series routers are too. I assume anything newer than those should also do the job granted they have recent enough IOS that supports certain features.

I talked to the network guy at the school and he says they have a Cisco account and can get the IOS, but I don't expect him to get it for me.....illegal I think?

Thanks again! That's the kind of information I am looking for.

---

### Post by mrsteveman1 on 2008-03-16
the 2600 routers and 2950 switches are still fairly current (close to EOL though), but i believe the 1900 switches are EOL now and are a bit different from the others. 

Cisco bought their switching lines from a bunch of different companies, and some of them ran CatOS which was totally unrelated to the IOS software they use on routers, so there are some big differences in the older models. The newer switches seem to match IOS closer, and some of them no longer run CatOS at all.

Here's some more information on the differences [http://en.wikipedia.org/wiki/Catalyst_switch]("http://en.wikipedia.org/wiki/Catalyst_switch")

---

### Post by bdk on 2008-06-12
I started my CCNA studies with a CAT1924 and a SOHO91; both off of ebay and both pretty cheap at the time. Got my CCNA through study and using the BOSON simulator but now I've discovered Dynamips which is helping with my CCNP track. Had I known about Dynamips when I was studying for my CCNA, I would never of gotten the BOSON pack. Dynamips does everything short of switching and for that it would be worth buying two small ported 2950s or even cheaper 2900s. Dynamips will emulate a Frame Relay Switch, ATM Bridge and Switch and even tap into your existing ethX interfaces so you can route real traffic through the routers running in Dynamips. It will even do PIX emulation if you interested in the CCSP route.

Dynamips can be used to study all the routing fundamentals; everything layer 3 and up. You can also get GNS3 which will run dynamips for you in a nice GUI environment with drag, drop and plug capabilities.

GNS3 -> [http://www.gns3.net/](http://www.gns3.net/)
Dynamips -> [http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator](http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator)
Dynamips/GNS3 Support Forum -> [http://7200emu.hacki.at/](http://7200emu.hacki.at/)

You will need to supply your own IOS images though because it is the real thing and not just a Zork like text game as the BOSON software is.

Hope that helps!

*-bdk*

---

### Post by binary_dreamer on 2008-08-22
try this 
[http://www.blindhog.net/gns3-installation-tutorial-for-linux/](http://www.blindhog.net/gns3-installation-tutorial-for-linux/)

---

### Post by timcredible on 2008-08-22
i have my ccnp (which requires the ccna first) and wireless field engineer specialist cert.  i didn't buy any equipment (i work on cisco stuff for a living), but i did buy the books from cisco press for both the ccna test and ccnp tests, they were very good, and helped prepare you for knowing what topics you need to know, and they have flash cards.  the 2 classes you mentioned will not help with the ccna, it's mostly about ip addressing, routing, design, and switching (or at least it was in 2003 when i took the test).  i think that the books would actually help more than cisco gear.  but, if you want to buy cisco gear, go to cisco.com and check out the certifications area forum, there's plenty of people there that buy a lab setup, use it to study for their test, then sell the setup.

---

