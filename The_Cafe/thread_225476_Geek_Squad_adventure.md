---
title: "Geek Squad adventure"
date: 2006-07-29
forum: The Cafe
---

### Post by hizaguchi on 2006-07-29
My little brother has a computer that's about 6 years old and has finally submitted to a combination of spyware and Windows registry chaos.  Since it was in need of some more RAM and a reinstall, instead of calling me, for some reason my mom took it to the Geek Squad.  She paid $15 for RAM installation, not including the price of the memory itself!  On top of that, she paid (I can't imagine how much) to have them do the reinstallation.  It should have been a simple procedure.  Stick in some new memory and reinstall only Windows and Office.  No backups, no extra software, just a clean base installation.

I went over today to see the destruction the Geek Squad caused.  When you turn the box on, it says "keboard failure" and you can't do anything till you're in Windows (at which point USB starts working).  First though, the Windows bootloader thinks there are 2 copies of XP installed (there is only 1 partition on the computer's only drive), and you can't pick one because there's no keyboard so you have to wait for the 30 second timeout.  Once in Windows, alot of features (like showing a background image) are broken.

I set out to first fix the 2 copies of XP showing up at the boot screen.  I figured I'd just pop in the Windows disk and do a "fixmbr".  Wrong!  They disabled booting from CDs and floppies in the bios.  Guess what... I can't enable it because the keyboard doesn't work!  So I went to Walmart and picked up a non-USB keyboard for $10 and used it to correct the bios settings.  That didn't do much good though because the recovery console couldn't fix the boot record and I'm still not sure why USB doesn't work from the start.  But around this time the mouse stopped working.  I looked at the computer and found out that the USB expansion card had come unplugged because the Geeks left out the screws in all the pci cards (they just replaced the memory, remember?).

I think I'm just going to bring the computer home with me next time I visit and do a clean install myself.  I can't even imagine how the computer has this many problems comming fresh out of a "professional" installation, and I think just starting over will be easier than tracking down all the issues.  Plus I can give him some dual boot goodness while I'm at it. ;) 

Conclusion: Don't let the Geek Squad touch your computer.

---

### Post by Lord Illidan on 2006-07-29
Who are the geek squad anyway? Some teenagers who think that their A+ in computing gives them god status?

I've never had to call in a tech...well since I was 13 years old. And my pc is still healthy..

---

### Post by djsroknrol on 2006-07-29
The Geek Squad is part of Best Buy as I remember...my better half's brother's son works for a branch in the L.A. area...Can't say much about his line of work, but he did go thru intensive training for his job...I still think I can repair them faster and better myself..I have no use for that kind of service..

---

### Post by Iandefor on 2006-07-29
> **Lord Illidan said:**
> Who are the geek squad anyway? Some teenagers who think that their A+ in computing gives them god status?

I've never had to call in a tech...well since I was 13 years old. And my pc is still healthy.. It's a tech-support company that's part of Best Buy. Apparently, they'll also poke around in your computer, for a fee.

But I keep hearing about how crappy they are, so... I'll avoid their services where possible.

---

### Post by kop316 on 2006-07-29
I've seen the pricing for the Geek Squad, and believe me, you don't want to know how much they charged your mom for the reinstallation of XP.

---

### Post by K.Mandla on 2006-07-29
Thanks for the warning. I don't have a Geek Squad anywhere around here, but it seems I'm not missing much.

I have a similar story, except mine has a happier ending. A co-worker asked me to blank the drive of an ancient Presario 5304 his grandson uses to play games when he visits. The drive was cluttered with spyware and crud, of course.

I blanked it, then gave him a 10Gb 7200rpm drive as a system volume (and moved the old one to cache), an old PCI network card, six times the memory (from 64Mb to 384Mb) and a Sony CDRW.

It weighs about 10 pounds more, but I hear his grandson was thrilled. Best of all, I left a 2Gb blank space for the next time it gets funked up -- that's where Ubuntu will go. :D

---

### Post by jISh on 2006-07-29
A prime example of why, when you need these problems fixed, you learn to do it yourself, or have someone you know and trust do it.

---

### Post by G Morgan on 2006-07-29
The Windows bootloader can easily be altered just edit C:\boot.ini. It's a very un-windowsy textfile and mostly is self explainitory. At the very least altering the timeout is easy. you'll have to make it writable first though.

---

### Post by bobbybobington on 2006-07-29
Yeah from what I've heard they are overpriced and push uneccesarry products. As far as quality of service I suppose it varies from store to store, but DONT send your laptops to them because they just ship it to a repair center, where God only knows what they do to them there. Try going to a local computer repair place (check them out before of course)or just get the nearest computer geek to fix it (unless of course you can fix it)

---

### Post by erikpiper on 2006-07-29
Question: Why? Why couldn't ANYONE fix their own (Desktop) computer? I dont get it... I dont get it...


*Shivers*

---

### Post by Iandefor on 2006-07-29
> **erikpiper said:**
> Question: Why? Why couldn't ANYONE fix their own (Desktop) computer? I dont get it... I dont get it...


*Shivers* Some people have higher priorities is all. There's nothing wrong with stepping in and doing it for them for a fee, although Geek Squad is hardly a group to trust.

---

### Post by slimdog360 on 2006-07-29
why would anyone let their computer be touched by people who deliberatly look like this.
[IMG]http://blogs.vandamme.com/development/archives/FAIA_Geek_Squad-w.jpg[/IMG]

---

### Post by djsroknrol on 2006-07-29
Again, I have a family member employed by them, and I hope you don't think I'm trying to open a can of worms here...

I Think the principal idea is sound as they provide a service. Yes you're right, people have different priorities and some don't want to be bothered,but companies get bad raps from bad **employes**...The original post tells of a complete ignoramus..sombody with a vendetta..who knows..working on someone's computer...sometimes we're too quick to trash a "brand name" because of it...

---

### Post by Iandefor on 2006-07-29
> **slimdog360 said:**
> why would anyone let their computer be touched by people who deliberatly look like this.
[IMG]http://blogs.vandamme.com/development/archives/FAIA_Geek_Squad-w.jpg[/IMG] From [the blog from which you got that image]("http://blogs.vandamme.com/development/archives/2005/10/"):

[B]Best client costume - FAIA Geek Squad

[/B]'twas a joke. Plus, that was actually an in-house IT department:

> Some say our development team looks geeky but the IT department at [Florida Association of Insurance Agents]("http://www.faia.com/") has us beat!

---

### Post by aysiu on 2006-07-29
I've seen a wide variety of Best Buy employees over the years. Some are good. Some are very, very bad. Some are knowledgeable. some are totally clueless.

---

### Post by greggh on 2006-07-30
> **hizaguchi said:**
> On top of that, she paid (I can't imagine how much) to have them do the reinstallation.  It should have been a simple procedure.  Stick in some new memory and reinstall only Windows and Office.  No backups, no extra software, just a clean base installation.

$129 to install Windows
$59 to install Office

Their in-store prices are here [http://geeksquad.com/servicesandpricing/precinctsinbestbuy.php](http://geeksquad.com/servicesandpricing/precinctsinbestbuy.php)

They charge alot more for on-site repair though [http://geeksquad.com/servicesandpricing/homeinofficeservices.php](http://geeksquad.com/servicesandpricing/homeinofficeservices.php)

---

### Post by teet on 2006-07-30
> **greggh said:**
> $129 to install Windows
$59 to install Office

Their in-store prices are here [http://geeksquad.com/servicesandpricing/precinctsinbestbuy.php](http://geeksquad.com/servicesandpricing/precinctsinbestbuy.php)

They charge alot more for on-site repair though [http://geeksquad.com/servicesandpricing/homeinofficeservices.php](http://geeksquad.com/servicesandpricing/homeinofficeservices.php)

HOLY COW!

They are **[SIZE="2"]EXPENSIVE[/SIZE]**.  I've worked part time at a computer shop for the past couple summers.  I always felt kind of bad because I thought our prices were a bit steep sometimes.  We charge $68.50 for the first hours labor and $45 for every hour thereafter.  Also, an "hour" of labor is a rough estimate since you often click a few buttons and then walk away and do something else while a scan is running or whatever.  The average repair only takes 1 or 2 "hours" and I've only seen a few 3 or 4 "hour" repairs in my day.  On-site service has the same rate, but you start getting charged when the van pulls out of our lot.  Plus, you're going to get charged a lot more since the technician has to sit in front of your machine until it's done.  So a 3 hour onsite repair might be the equivalent of a 1 hour repair if you bring it into the shop.

I never realized Geek Squad was so expensive though...I don't guess we have to worry about losing business to them for a while!  Maybe we should raise our rates?

-teet

---

### Post by cantormath on 2006-07-30
> **hizaguchi said:**
> 

Conclusion: Don't let the Geek Squad touch your computer.

Many of my calls are due to those guys, I dont know how they justify charging for what they do.  I have actually seen them reinstall XP and all of the essentials on an IBM with the IBM access button, which if pushed will reinstall the system.  They didnt understand the little purple button.

They are not real geeks.

---

### Post by Rich3077 on 2006-07-30
I got a call from a freind at work who was in a panic because he took his computer in for a repair upgrade NOT AT BEST BUY AND NOT DONE BY THE GEEK SQUAD.. sorry for the caps, I am trying to make sure issues where not confused.
Anyway he had a new mobo installed and needless to say he could have bought a new computer for the price of the upgrade. The whole install was buggy and his system was crashing and eventually his PC died. He took the computer back as the upgrade was still under warrenty.
They came to find that the motherboard had failed and told him that his case was faulty and caused the mobo to fry and charged him for a new case. I was furious when I heard about this and asked for the phone number to the repair center.. my freind gave me the number and my father in law answered..until such time I was unaware that he did the upgrade himself. After a rather long argument with him he admitted that he didnt install the motherboard spacers. At this point I am steaming mad and called my freind and told him I would be willing to testify in small claims court but he said "As long as he learned his lesson something good has come of this"
Almost all computer repair/upgrade places are garbage.. so dont just blame the Geek Squad alone. The techs must do what their bosses tell them to do or follow company policy. This is bad news for everyone involved, not just the Tech and the coustomer.

Lesson learned... if you are not computer savy trust the 12 year old next door to do your upgrade before you take it to the shop. The 12 year old will probably do a better job and will appreciate the money much more.

---

### Post by Rich3077 on 2006-07-30
While I am busy ranting about family members I have thought of more to say.
I have a brother in law who got some kind of 4 year degree in computers in the 80's before the big I.T. rush. He is now the main systems administrater of a large hospital.. and doesnt know Jack.. or how to Google Jack. Its a shame really. He sometimes comes to me for advice. ( I process human waste for a living at a sewerage plant )

My other brother in law however is in the I.T. feild and knows Jack very well. 
He even knows hardware printer repair and is on call 24/7. Its nice to have at least one member of the family who is not a total scam. 

Peace
Rich

---

### Post by hizaguchi on 2006-07-30
> **G Morgan said:**
> The Windows bootloader can easily be altered just edit C:\boot.ini. It's a very un-windowsy textfile and mostly is self explainitory. At the very least altering the timeout is easy. you'll have to make it writable first though.
Ah, I knew there had to be a grub.lst somewhere. :)  Thanks.  Any ideas about the other problems, like no USB keyboard at boot up and not being able to set a background?  Those are blowing my mind, and a combination of that craziness and fear of what else they've managed to screw up still has wanting to just do a fresh install while he doesn't have anything else on the computer.  Of couse, I'm also the kind of person that cleans rooms in the house by moving everything out into the hall and then putting it all back the way I want it. :)

---

### Post by K.Mandla on 2006-07-30
> **Rich3077 said:**
> I process human waste for a living at a sewerage plant
Now that's an honest and worthy profession. Thank you sir, for the work you do.

---

