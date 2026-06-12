---
title: "Arduino advice"
date: 2011-10-04
forum: The Cafe
---

### Post by F.G. on 2011-10-04
hi folkes,
i just finished a school project involving firmware programming for a ATMega128 microcontroller, saw someone referencing arduino in another thread. and now i'm dead set on getting my self an arduino starter kit.

so i'm wondering if anyone can advise me whether i should go for the Uno, Mega or Duemilanove arduino boards (and what the difference is). also any other advice on starter kits and starting out in this area. 

my previous project was focussed on RFID, so that's probably an area i'll return to.

thanks.

---

### Post by compubob on 2011-10-04
I have an arduino uno and ultra sitting infront of me.. 
the uno I have has a 328 chip and the amount of I/O available is much less than a mega.. I would really only use the uno if I was designing something that I was eventually gong to run on it's own circuit board by removing the chip and creating my own board.. the Mega does not have a removable chip, but has a lot more outputs and inputs.
so it all depends on your project.
you can find more info at [www.arduino.cc](www.arduino.cc)

---

### Post by F.G. on 2011-10-04
hmm, thanks for your reply compubob, i don't have a particular project in mind, just to explore the possibilities of arduino in general.  
at some point i would be interested in building a rfid skimming / eavesdropping device, as hf rfid is an area i know quite well and it would be a natural follow on from my previous academic focus. this is, however, by no means my only aim.

what i'm thinking about getting is this:
[http://www.earthshineelectronics.com/arduino-compatible-products/91-basic-arduino-uno-starter-kit.html](http://www.earthshineelectronics.com/arduino-compatible-products/91-basic-arduino-uno-starter-kit.html)
as it seems like good value and comes with instructions (for a gentle start). 

so, it sounds like the Uno is quite limited then? I suppose as I don't have any specific purpose in mind maybe this doesn't really matter.
also i haven't managed to find the arduino Ultra you mentioned?

---

### Post by compubob on 2011-10-04
> **F.G. said:**
> hmm, thanks for your reply compubob, i don't have a particular project in mind, just to explore the possibilities of arduino in general.  
at some point i would be interested in building a rfid skimming / eavesdropping device, as hf rfid is an area i know quite well and it would be a natural follow on from my previous academic focus. this is, however, by no means my only aim.

what i'm thinking about getting is this:
[http://www.earthshineelectronics.com/arduino-compatible-products/91-basic-arduino-uno-starter-kit.html](http://www.earthshineelectronics.com/arduino-compatible-products/91-basic-arduino-uno-starter-kit.html)
as it seems like good value and comes with instructions (for a gentle start). 

so, it sounds like the Uno is quite limited then? I suppose as I don't have any specific purpose in mind maybe this doesn't really matter.
also i haven't managed to find the arduino Ultra you mentioned?
sorry, I meant to type Mega, not Ultra.. I had people talking to me when I was typing that.
Look for a kit that comes with a LCD screen, I got my first one off ebay for $30 and it came with a pile of LED's, Resistors, a Breadboard, 2 Line LCD Display, Potentiometers and at least 100 jumper wires.
Also a good source for arduino stuff is [http://shop.moderndevice.com/](http://shop.moderndevice.com/)
I picked up a RBBB Kit, some spare 328 chips and some sensors just a few weeks ago from them.

---

### Post by ssam on 2011-10-05
go for the standard uno if you just want play. if you decide on a specific project that needs something different (mega for more IO, or maybe a nano save space) then get that then.

if you want to save money there are a few cheaper clones. but it may require you to tweak some config files in the IDE to get it working.

its also worth noting that there is a ARM based arduino in the works [http://arduino.cc/blog/2011/09/17/arduino-launches-new-products-in-maker-faire/](http://arduino.cc/blog/2011/09/17/arduino-launches-new-products-in-maker-faire/) still I would say get started with an uno, and then see if you need something different.

---

### Post by F.G. on 2011-10-05
thanks for both your replies, there are a bunch of cheap Duemilanove starter kits on ebay with lcd's. these are the version with the ATMega 328, which seems to be more or less the same as the Uno. so i might get one of these. otherwise for not much more (£31GBP) i could get the Uno or the Mega(ATMega 1280 version), with lcd and bits.
i think i;m just going to have to take the plunge.

also, i thought that the atmega1280 was a variation of the atmega128 (which i;m familiar with)and therefore a smaller chip than the atmega328?

anyway thanks for all you help, if i don't get some particular advice in the immediate future i think i'm just going to buy one (probably the Uno with the LCD).

---

### Post by F.G. on 2011-10-05
done!

so, after much procrastination and trying to tally up component part I went with the Duemilanove starter kit with two potentiometers, an LCD, 30 leds and only 10 resistors (and other bits, £26GBP from ebay).
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=270656049300#ht_2989wt_1149](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=270656049300#ht_2989wt_1149)

I know its an older board design, but i figure for my purposes it probably doesn't matter (and they seem to be pretty much the same). soon it will be winging its way here from Hong Kong.

any advice on what to do when it arrives? is more than welcome. (by that i mean i'm not just flatly refusing to google, but am open to suggestion).

---

### Post by Tux Aubrey on 2011-10-14
Hi FG

I hope your Arduino arrived safely.

You could check out a few of my favorite Arduino sites bookmarked here: [My Electronics and Arduino Bookmarks]("https://www.google.com/bookmarks/l#!threadID=GSXOK6iehThA%2FBDSA-gwoQ4fmkkJQm")
I would especially recommend [http://tronixstuff.wordpress.com/](http://tronixstuff.wordpress.com/) and adafruit.com for tutorials.

Like you, I have some ebay Arduinos (as well as some from more official sources).  I have had good service from the ebay clones but I have heard of bad experiences too.  The quality of the builds from different vendors does vary quite a lot.

By the way, both Twitter and Google+ have quite a number of Arduino users posting.

---

### Post by F.G. on 2011-10-14
Hi Tux Aubrey,
thanks for your post. some of those links I've come across before but most of them are completely new to me (even with fairly extensive googleing). 

irritatingly my kit has yet to arrive, the seller had a high number of good feedback comments, so hopefully all will be well it arrives (and all the components will work).

thanks again for all the links.
f.g.

---

