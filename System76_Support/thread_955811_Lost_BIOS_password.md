---
title: "Lost BIOS password"
date: 2008-10-22
forum: System76 Support
---

### Post by tgoff on 2008-10-22
My Gazelle laptop (based on Compal FT01 body) was stolen from my house about 4 months ago, and I finally got it back from the police yesterday.  when I turned it on, I was asked for a BIOS password.  The guys who stole it were not the brightest lights on the tree (which thankfully ended up getting them caught), but to my surprise they managed to at least set up a BIOS password (Of course, there is the small possibility that I had been playing around with something and set this up and totally forgot in the ensuing 4 months).

I tried all of my usual passwords, a bunch of generic ones (hello, password, etc), and default BIOS passwords that I found online, all with no luck.  I finally cracked open all the access panels on the bottom of the laptop and found the CMOS battery marked 'batt2' next to the RAM slots.  It was hard to get to, but I managed to disconnect it.  after leaving it for a while with both the CMOS battery and the laptop batter disconnected, I was able to get a bit further.  However, now it is asking for a HDD1 password.  It seems that disconnecting the CMOS battery cleared the BIOS admin and user passwords, but even with admin access in the BIOS setup screen, I can't change the HDD1 password.

So... my questions are these:
-how do I clear the HDD1 password?  
-where is 'batt1' on my laptop?  are different parts of BIOS/CMOS dependant on different batteries?
-Does the HDD password maybe require a longer period of no power to clear than other BIOS settings?  if so, how long?  
-Would removing the hard drive allow me to get past the HDD password, and use a live CD?
-how can I flash a new BIOS?
-where can I get a diagram of the motherboard in my laptop?

The BIOS is a Phoenix/AWARD BIOS.  Any help would be much appreciated.  thanks.

---

### Post by thomasaaron on 2008-10-22
I believe you can reset your cmos to set everything back to its default settings.

It's not that hard, but I really don't like posting that sort of information on the forums, as it is model-dependent and potentially harmful to your machine if you make a gross error.

Please call me at support and I'll walk you through it.

---

### Post by thomasaaron on 2008-10-22
Just spoke to you on the phone, and then decided to research it a little more. I found this, but it doesn't look promising...

[http://www.daniweb.com/forums/thread14216.html](http://www.daniweb.com/forums/thread14216.html)

Here are some instructions on removing the hard drive password. It would be worth a try.
[http://www-307.ibm.com/pc/support/site.wss/YAST-3JXNTY.html](http://www-307.ibm.com/pc/support/site.wss/YAST-3JXNTY.html)

---

### Post by tgoff on 2008-10-23
Thanks Thomas for your suggestion.  However, it didnt work.  It seems from doing a bit more research that the password is actually stored on the hard drive.  any ideas on how to get past it?

---

### Post by lukjad on 2008-10-23
Well if it's on the hard drive, a live CD should be able to access it without being prompted. As long as it is not encripted, you can drag off any personal files and then reformat the HD. Is this an option for you?

---

### Post by tgoff on 2008-10-23
from what I have read ([http://www.heise.de/ct/english/05/08/172/](http://www.heise.de/ct/english/05/08/172/), [http://www.velocityreviews.com/forums/t307506-how-do-you-remove-an-ata-hard-disk-password.html](http://www.velocityreviews.com/forums/t307506-how-do-you-remove-an-ata-hard-disk-password.html) among others), the ATA hard drive password prevents any access to the hard drive, so using a live CD would not allow me to read the drive.  I have actually tried booting from a Kubuntu live CD, and it still goes to the password screen.  I could probably get it to boot from the live CD if I remove the hard drive, but then I have no hard drive, which isn't very useful.  I may try that anyway, just to prove that it will work.  maybe in the end, the only solution will be to get a new hard drive, but assuming the theives who had my laptop didnt erase all my data, I do have some stuff I'd like back on there.  Also, I really want to know why/how on earth this password got on there.  The guys who stole the laptop were local kids who I don't image are very tech savy.  If they were trying to pawn the laptop, why would they lock the drive instead of reformatting it?  I am both pissed off and incredibly curious.

---

### Post by jdb on 2008-10-23
> **lukjad007 said:**
> Well if it's on the hard drive, a live CD should be able to access it without being prompted. As long as it is not encripted, you can drag off any personal files and then reformat the HD. Is this an option for you?

Here's a good article on it:

[http://www.heise.de/ct/english/05/08/172/](http://www.heise.de/ct/english/05/08/172/)

I hadn't heard of this before, it's some pretty scary stuff.

jdb

---

### Post by MasterNetra on 2008-10-23
I heard you can take out the battery, leave it unplug for 24-48 hours (prehaps more i forget how long). And the bios should return to factory default. Idk if that works or not as i never tried it, but thats what I've heard. Because i believe you can do that with desktops but ya have to take out the watch battery from the motherboard.

---

### Post by jdb on 2008-10-23
> **MasterNetra said:**
> I heard you can take out the battery, leave it unplug for 24-48 hours (prehaps more i forget how long). And the bios should return to factory default. Idk if that works or not as i never tried it, but thats what I've heard. Because i believe you can do that with desktops but ya have to take out the watch battery from the motherboard.

That will reset most bios passwords (I've heard of some bios's that put them in non-volatile ram)  but it won't do any good at all for an HDD password.

jdb

---

### Post by thomasaaron on 2008-10-23
It's not the BIOS password that is the problem It's the hard disk password. The two are separate and ne'er the twain shall meet.

---

### Post by lukjad on 2008-10-24
I learnt something today.

---

### Post by sailor2001 on 2008-11-16
if you are dual-booted with windows, I use f12 at boot up yo get safe mode for windows (on an hp machine) and then into control panel/users...Have tried that with a Dell and it doesn't work.

---

