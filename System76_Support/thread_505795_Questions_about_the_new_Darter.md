---
title: "Questions about the *new* Darter"
date: 2007-07-20
forum: System76 Support
---

### Post by octathlon on 2007-07-20
Just a few questions before the final decision:

1.  Wireless 802.11 abg - is that Intel (or something else that uses an open source driver) -- in other words, it does not require ndiswrapper or a proprietary driver?

2.  Firewire is not listed in the specs, but on the picture I see a port that sorta looks like a firewire port, so  - is there a firewire port?

3.  A card reader is not listed in the specs (old Darter had one)  - just want to verify that there is not a card reader?

4. How much noise and heat does it create compared to the previous Darter or other laptops?

Thanks :)

---

### Post by tedrampart on 2007-07-22
5. whats that orange circle on the side of it too? 


(I think theres a card reader under the expresscard slot)

---

### Post by PsyWolf on 2007-07-22
I was wondering what barebones kit this laptop is based off of.  If we could find that, it would give us all the specs we need.

---

### Post by PsyWolf on 2007-07-22
I think I found it.  IT looks like it is based on [this barebones kit]("http://www.msicomputer.com/NB/product_spec.asp?model=MS-1221")

so to answer your questions.

yes to SD/MMC/MS/MS-Pro 4-in-1 Card Reader

and no to firewire.

but i could be wrong about the barebones.  It matches up pretty well though and they look the same.

---

### Post by tedrampart on 2007-07-22
right on, HDMI output.. thats pretty slick..

---

### Post by Ptero-4 on 2007-07-22
Woow. it's super kewl.

---

### Post by PsyWolf on 2007-07-22
get the word out about this laptop [Digg it here]("http://digg.com/linux_unix/New_Ubuntu_Linux_Laptop_System_76_darter_ultra_has_been_replaced")

---

### Post by octathlon on 2007-07-23
> **PsyWolf said:**
> I think I found it.  IT looks like it is based on [this barebones kit]("http://www.msicomputer.com/NB/product_spec.asp?model=MS-1221")

so to answer your questions.

yes to SD/MMC/MS/MS-Pro 4-in-1 Card Reader

and no to firewire.

but i could be wrong about the barebones.  It matches up pretty well though and they look the same.

Then I would need to amend the question to: Is the card reader working?  If you have the right barebones system, it also has a fingerprint reader, though I wouldn't expect that to work or care if it did.

With these specs, if this had had a 13" screen I would have immediately clicked "Buy" with no hesitation.  So on the way home today I stopped off and looked at a couple of 12.1" and a 13" notebook and ... well, with a 13.3" it's still pretty easy to see while keeping the notebook nice and small, but the 12"  screen is just enough smaller that it could be a problem (I'm in the bifocal stage of life)-- I don't think I would know for sure until I actually used it for a while.

---

### Post by palintheus on 2007-07-24
> **tedrampart said:**
> 5. whats that orange circle on the side of it too? 


(I think theres a card reader under the expresscard slot)


I looked at the manual from the MSI website and the orange circle is not labeled...

[link to the manual]("http://global.msi.com.tw/index.php?func=downloadfile&dno=5442&type=manual")

---

### Post by octathlon on 2007-07-25
Thanks for that link.  I wonder what that "multimedia" connector is; that's the one I thought looked like a firewire port.

It's been 4 days since asking, I wonder if anyone from System 76 will answer the questions.  After I ordered a Darter and got an email 2 days later telling me they had to cancel it because they were out of stock, they promised to email me when the new models were available and I still haven't heard anything from them.

---

### Post by palintheus on 2007-07-25
> **octathlon said:**
> Thanks for that link.  I wonder what that "multimedia" connector is; that's the one I thought looked like a firewire port.

It's been 4 days since asking, I wonder if anyone from System 76 will answer the questions.  After I ordered a Darter and got an email 2 days later telling me they had to cancel it because they were out of stock, they promised to email me when the new models were available and I still haven't heard anything from them.

Their site shows they are avail and I am placing an order for one today. I emailed the same question about the mystery port to [email]sales@system76.com[/email] and Tom replied and said he would contact MSI and post the answer in the forum.

---

### Post by thomasaaron on 2007-07-25
OK, folks.

The little mystery port is a socket for an optional antenna for a TV tuner.

---

### Post by palintheus on 2007-07-25
> **thomasaaron said:**
> OK, folks.

The little mystery port is a socket for an optional antenna for a TV tuner.

Is this built into the laptop or something that has to be installed? Next question, if it is built-in, is this something that can eventually be supported?

---

### Post by octathlon on 2007-07-25
These were the questions originally asked:

1. Wireless 802.11 abg - is that Intel (or something else that uses an open source driver) -- in other words, it does not require ndiswrapper or a proprietary driver?

2. Firewire is not listed in the specs, but on the picture I see a port that sorta looks like a firewire port, so - is there a firewire port? - **answered: no firewire**

3. A card reader is not listed in the specs (old Darter had one) - just want to verify that there is not a card reader? - **update: If there is a card reader as there appears to be, is it working?**

4. How much noise and heat does it create compared to the previous Darter or other laptops?

---

### Post by thomasaaron on 2007-07-26
> 1. Wireless 802.11 abg - is that Intel (or something else that uses an open source driver) -- in other words, it does not require ndiswrapper or a proprietary driver?

Uses IPW3945 wireless. Does not use ndiswrapper. Supported natively by Ubuntu.

> 2. Firewire is not listed in the specs, but on the picture I see a port that sorta looks like a firewire port, so - is there a firewire port? - answered: no firewire

No firewire.

> 3. A card reader is not listed in the specs (old Darter had one) - just want to verify that there is not a card reader? - update: If there is a card reader as there appears to be, is it working?

The card reader is not yet supported.

> 4. How much noise and heat does it create compared to the previous Darter or other laptops?

About the same. No appreciable difference that I can tell.

---

### Post by octathlon on 2007-07-26
Ok, thanks for the info!

---

### Post by palintheus on 2007-07-26
> **palintheus said:**
> Is this built into the laptop or something that has to be installed? Next question, if it is built-in, is this something that can eventually be supported?

bump

---

### Post by thomasaaron on 2007-07-27
Yes, it is built into the laptop.

We'd like to get it supported. But, honestly, we currently do no testing with TV tuner hardware, so it would probably be down the road a bit.

---

### Post by octathlon on 2007-07-27
Well, I think the 12" screen is just that much too small for me, and sadly I'd better pass on the Darter. :(  A 13.3" would have been ideal, but a 14" would probably be OK too.  Back to the wait and watch game, we'll see what all comes down the pike and also see how the Gazelle looks when it gets upgraded.  I think I read somewhere on here that would happen in September.  For you under-40's with good eyes, enjoy the Darter; it looks like a great deal. :)

---

### Post by jml on 2007-07-28
Don't give up on the Darter, Octathlon.  I'm 53 and I can read a 12 inch screen just fine.  Bifocals are wonderful!  ;)

Joe

---

### Post by zedmanauk on 2007-07-31
Does the HDMI port work under Ubuntu for video out?  It's not listed in the specs on the System76 website.  I'd like to connect my monitor via HDMI/DVI rather than VGA.

---

