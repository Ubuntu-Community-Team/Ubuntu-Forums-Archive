---
title: "An Ubuntu Christmas"
date: 2008-12-29
forum: Testimonials &amp; Experiences
---

### Post by bp1509 on 2008-12-29
d

---

### Post by albinootje on 2008-12-29
> **bp1509 said:**
> 
 You can read the ongoings of this here:

[http://ubuntuforums.org/showthread.php?t=1023097](http://ubuntuforums.org/showthread.php?t=1023097)
-- cut --
This problem too, is still on-going.
(read more here: [http://ubuntuforums.org/newthread.php?do=newthread&f=103](http://ubuntuforums.org/newthread.php?do=newthread&f=103)) 


Concerning the first thread you mention, there are a lot more boot-loader managers than just grub.
Years ago when I was still using Lilo, I found Grub very difficult and weird, but I got used to it after some time.
There's also GUI software for Grub which might help.

Your second link to a thread seems unvalid, can you fix it ?

Concerning the fonts, do you have liberation- and/or msttcore fonts packages installed ? 
Those can be very useful for webbrowsing experience.

And great that your non-geek girlfriend managed to get you all this.
I wish I could make my mum give me proper presents :|

---

### Post by bp1509 on 2008-12-29
d

---

### Post by solwic on 2008-12-29
> **bp1509 said:**
> 
I just find it amazing Grub cannot handle SATA drives correctly.  

I have a 500GB SATA running right now, works perfectly.  No issues at all with it.  I suspect the SATA drive isn't the issue as much as the SATA card is.  

I also find it hard to believe that I'm the only person with Ubuntu to get a SATA drive to work, so I'm going to make an assumption here that GRUB can't handle *your* SATA drive (and as I said, most likely, the SATA card), not SATA drives in general.

> **bp1509 said:**
> 
One more day of this crap, and I'll be damned if i promote Linux on anything other than a server.  Sorry for all the venting, but this is just ludicrous.  At least 99.9% of the time when people come out to gripe about Linux they're complaining about DRMd files, devices with proprietary drivers.  I got 3 devices, all supposedly "supported" by linux that work about as well as hunks of junk.

Everybody has to vent once in a while.  I can't speak for the iRiver (never heard of it) but I have a 22" Acer LCD and a 500GB SATA drive that work beautifully with Ubuntu 8.10.

Just remember that while venting is fine, it's not very productive.  :P

Best of luck.

---

### Post by waspbr on 2008-12-29
hmmm, odd, I have a samsung 22" screen and I didn't feel like I have lost any space, it may take some getting used to, my max res is 1680x1050... 

Anyway, I am stuck with using a 12.1" screen from my lappy anyway since I have been moving a lot lately and had to leave my desktop behind. Makae sure you have your restricted extras package installed so you can use extra fonts. You may find that some themes may be more appropriate for a big screen than others, a search in gnomelook.org for themes and icon packages should help ya out (backgrounds also can make things look better).

Anyway, your girl is a keeper, it's rare to find a girl that will go so deep into the geek world for our sake. Make sure you take her out for a nice romantic dinner to let her know how much you appreciate it.

sorry I can't help ya with the SATA issue, I am still an IDE person. Though (can't believe I am going to suggest this) I have recently build a few fedora machines with SATA drives and I have had no issues at all. You might wanna give fedora 10 a try, if that doesn't work then the card really has issues. 

gl

---

### Post by creek23 on 2008-12-29
I thought this thread was something like "What you had this Christmas for you Ubuntu box?"

Now I know it's not it, I'd still give it a go :P

I bought 160GB external HDD and a router so I could have upgrade my Ubuntu box (the router is to share my DSL then download upgrades; then HDD is for having another partition to swap).

---

### Post by kspncr on 2008-12-29
> **waspbr said:**
> Anyway, your girl is a keeper, it's rare to find a girl that will go so deep into the geek world for our sake. Make sure you take her out for a nice romantic dinner to let her know how much you appreciate it.

Exactly what I was going to say. It sounds to me like you don't have a problem at all, just a couple computer issues. I don't have any suggestions or solutions but don't worry, I'm sure you'll get it all working soon enough.:)

---

### Post by bp1509 on 2008-12-29
d

---

### Post by solwic on 2008-12-29
Just thought of something.  My Mobo has a SATA plug on it, so this may be different than using a card...but at the last screen in the setup, before it starts installing files, there's a window with an "Advanced" button, for setting GRUB options.  

Even when the only drive hooked up in my SATA (but also when I tried to run a 80GB IDE drive with it), I have to go to advanced options and change (hd0) to /dev/sda.

In my case, that's the exact same drive...but GRUB doesn't like hd0 for some reason.

Good luck.  :)

---

### Post by solwic on 2008-12-29
> **bp1509 said:**
> Anytime I've had mixed discs, at least 1 SATA and 1 IDE, I've had tons of problems.  Grub, almost as a rule, needs to be manually editted or creates problems like I have now that I end up working around rather than fixing.

See my last post above, but yeah, I have to make one change to GRUB when I install Ubuntu.  And sorry, by the way, if I came across as snooty.  I spend a lot of time in the Testimonials and Experiences forum, and after a while you start to pick up the 'tude of the Linux fanboys.  :P

> **bp1509 said:**
> 
Venting here may not be productive, but it may serve as a warning to others of what hardware to stay away from, even if articles and reviews online elsewhere state "works with linux" when that's simply not the case.

You have a point.  I imagine my next PC purchase will be a laptop from Dell with Linux pre-installed.  Or some other laptop manufacturer that pre-loads Linux.  That way, you're almost (*almost*) guaranteed everything will work.  :P

Good luck with your issues...I'm sure there's a work around somewhere.  Just remember to use Google to search the forums...the forum search is a piece of sh*t.  :P

---

### Post by albinootje on 2008-12-29
> **jrock612 said:**
>  You have a point.  I imagine my next PC purchase will be a laptop from Dell with Linux pre-installed.  Or some other laptop manufacturer that pre-loads Linux.  That way, you're almost (*almost*) guaranteed everything will work.  :P 

:)

The mentioned "works with Linux" needs to be taken with grains of salt from time to time.

Ubuntu is a Linux distribution, but the Ubuntu team makes their own decisions, comes with certain Linux kernel patches.
Few days ago I was writing something on the Ext4 filesystem wiki, where it reads that Debian made a good choice concerning a certain library choice, whereas Ubuntu uses a different worse choice, while the reason why is unknown to the person writing that in the Ext4 wiki.

See for yourself :
[http://ext4.ext3.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu](http://ext4.ext3.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu)

Apart from that I've seen ATA and SATA mixing boot troubles in the past.
I thought that the usage of UUID would have resolved most of that.

---

### Post by bp1509 on 2008-12-29
d

---

### Post by stalkingwolf on 2008-12-30
about all I can say is you are not alone.  My sister bought her husband
a new flat screen for christmas and it wont work on the system they have.
And They are running XP. ( dont even go there Im so pissed at her right now
we hardly speak. and it has little to do with OS's).

I have a 250 Gb sata drive that is for storage that works fine with my 120Gb
ata drive.

---

