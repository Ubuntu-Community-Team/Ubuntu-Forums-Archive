---
title: "Seeking Recommendations"
date: 2009-07-27
forum: System76 Support
---

### Post by HotShotDJ on 2009-07-27
Dear Friends --

I will (hopefully) be purchasing a new laptop within the next 30 to 60 days if all goes as planned financially over the next month.  I will likely purchase from System 76.

I've had my Dell E1505 for two years, and have been surprisingly satisfied with it -- it is what it is: a low end mass-produced laptop.  Also, I am a long-time Linux user, so there are no issues as far as switching to Ubuntu.  But I do have some questions about the current incarnation of the Pangolin Performance model --

[LIST=1]
[*]I plan on ordering it with either the P8700 or P8800 processor.  How many hours of running on battery can I expect?  Is there a higher capacity battery available? (I don't see anything other than the 6 cell standard battery offered)
[*]How would ordering it with a 7200 RPM HDD effect battery run time -- would the increased speed be worth the shorter run time?
[*]Whilst at home, I would like to plug in an external monitor and extend the desktop to the second monitor.  How well does this laptop's graphics card work for that type of configuration?  Similarly, how easy is it to plug into a television for OOo Impress/Powerpoint presentations?
[*]What is the partition scheme of the factory installed OS?  Is it a trivial task to reinstall from a standard Ubuntu Desktop install CD and add the System76 drivers?
[*]What is the typical time from ordering to being received by the customer.
[*]Is it REALLY as beautiful as the pictures suggest?
[/LIST]

---

### Post by marshmallow1304 on 2009-07-27
1. With the T9900, battery life is about 2-2.5 hours with no power-saving measures, but I haven't tested extensively.  I've heard rumours of a 9-cell, but nothing concrete.

2. Don't know, but the 500 GB @ 5400 RPM is quite fast.

3. Haven't tried that yet.

4. There is a separate home partition. (see screenshot)  The reinstallation process looks quite straightforward. See '[Restoring Your System]("http://knowledge76.com/index.php/Restoring_Your_System")'.

5. My Pangolin took 20 days from order to ship, but the Starling I ordered for my dad took 1 day from order to ship.  Of course, the Starling has no options other than external optical drive, so manufacturing wouldn't have taken as long.

6. YES.


Edit:  Huzzah for Thunderf00t.

---

### Post by 3Miro on 2009-07-28
> **HotShotDJ said:**
> 
[LIST=1]
[*]I plan on ordering it with either the P8700 or P8800 processor.  How many hours of running on battery can I expect?  Is there a higher capacity battery available? (I don't see anything other than the 6 cell standard battery offered)
[*]How would ordering it with a 7200 RPM HDD effect battery run time -- would the increased speed be worth the shorter run time?
[*]Whilst at home, I would like to plug in an external monitor and extend the desktop to the second monitor.  How well does this laptop's graphics card work for that type of configuration?  Similarly, how easy is it to plug into a television for OOo Impress/Powerpoint presentations?
[*]What is the partition scheme of the factory installed OS?  Is it a trivial task to reinstall from a standard Ubuntu Desktop install CD and add the System76 drivers?
[*]What is the typical time from ordering to being received by the customer.
[*]Is it REALLY as beautiful as the pictures suggest?
[/LIST]

1. I don't know.
2. I have a Pangolin with 4GB of RAM and unlike Windows, Linux excellent HD cashing abilities. Basically you get a HD with couple of gigs of cash, so there is no real slow down (I have 250 5400 and I am comparing it to the 7200 on my desktop, both computers run Linux)
3. Haven done monitors and TVs, but I did a projector. The Nvidia setting manager is as easy to use as any I have seen, no issues or whatsoever (unlike some of my friends with windows machines).
4. Partitioning is the default for Ubuntu, one small partition for / (it was big enough for me), swap and one larger one for /home. Reinstalling shouldn't be an issue, however, I never had to do that.
5. I got my laptop is little less than 2 weeks. I don't know if it is typical.
6. You get what you see. Beauty is in the eye of the beholder, but I very impressed by the looks of it.

The model is old, so some of the coloring is different, I found this video helpful:
[http://www.youtube.com/watch?v=nWBqgtJBOAA](http://www.youtube.com/watch?v=nWBqgtJBOAA)

---

### Post by gila_monster on 2009-07-28
> **HotShotDJ said:**
> [LIST=1]
[*]I plan on ordering it with either the P8700 or P8800 processor.  How many hours of running on battery can I expect?  Is there a higher capacity battery available? (I don't see anything other than the 6 cell standard battery offered)
[*]How would ordering it with a 7200 RPM HDD effect battery run time -- would the increased speed be worth the shorter run time?
[*]Whilst at home, I would like to plug in an external monitor and extend the desktop to the second monitor.  How well does this laptop's graphics card work for that type of configuration?  Similarly, how easy is it to plug into a television for OOo Impress/Powerpoint presentations?
[*]What is the partition scheme of the factory installed OS?  Is it a trivial task to reinstall from a standard Ubuntu Desktop install CD and add the System76 drivers?
[*]What is the typical time from ordering to being received by the customer.
[*]Is it REALLY as beautiful as the pictures suggest?
[/LIST]

I have a Pangolin panp4n (about a year old now). I haven't run the battery to the ground yet, but my estimate is that (under GNOME with compiz active and the wireless card on) I will get a about 2 hours 15 minutes with the battery. This would improve with desktop effects and the wireless off. I believe there is NOT a bigger battery for the Pangolin. (At least, I didn't find one during my original purchase research.)

Getting a faster hard drive will decrease battery life to some degree, all other things being equal. Whether this is worth it is a matter of personal opinion. I have the slower drive, and I've had no real issues. It's still pretty fast.

I've not tried an external monitor, sorry.

They ship with three partitions: swap (usually sized to match RAM), the root partition (/), and a separate partition for /home, which means you can reinstall the OS without nuking your data (if all goes well).

Time to order, as always, will vary depending on stock, orders in the queue, who's on vacation, the stock market, and a host of other things. Mine took about two weeks. Others have shipped the same day.

And yes, it's a good-looking machine.

---

### Post by thomasaaron on 2009-07-28
>    1. I plan on ordering it with either the P8700 or P8800 processor. How many hours of running on battery can I expect? Is there a higher capacity battery available? (I don't see anything other than the 6 cell standard battery offered)

TA: There is no larger battery available. I've seen one in some specs somewhere, but I don't think it was ever actually manufactured.

>    2. How would ordering it with a 7200 RPM HDD effect battery run time -- would the increased speed be worth the shorter run time?

TA: A 7200 RPM drive will use more power. However, it largely depends on how you are using the machine. If you are doing lot's of heavy, hard-drive intensive tasks, you probably will notice a significant increase in performance. If you are not, you may only notice a slightly faster boot time. It's not going to be much more of a drain on your battery than a 5400 RPM drive if you're not really pushing it.


>    3. Whilst at home, I would like to plug in an external monitor and extend the desktop to the second monitor. How well does this laptop's graphics card work for that type of configuration? Similarly, how easy is it to plug into a television for OOo Impress/Powerpoint presentations?

TA: External monitors and spanning desktops works fine. As for the TV, it depends on the type of inputs your TV provides. If your TV has HDMI input, you're in business. If not, you may have to be some sort of adapter.


>    4. What is the partition scheme of the factory installed OS? Is it a trivial task to reinstall from a standard Ubuntu Desktop install CD and add the System76 drivers?

15GB / (root)
SWAP = Installed RAM
Remainder = separate /home partition

>    5. What is the typical time from ordering to being received by the customer.

TA: Typically 7-9 days from order to shipping unless something goes on backorder.


>    6. Is it REALLY as beautiful as the pictures suggest?

TA: In my opinion, it's one of the top 3 prettiest computers we've ever produced.

---

### Post by bill516 on 2009-07-28
I have had my Pangolin for several months now and I am very well satisfied with it and with support from System 76.  I would make the purchase again.

Battery life is on the order of two hours and speakers are adequate for light duty.  They are not sufficient for serious music listening, but I do not know any laptop that could validly make such a claim.

Just one additional point concerning the System 76/Ubuntu installation.  On my machine, at least, the install (Ubuntu 8.10, which runs extremely well.) uses three primary partitions.  This is not a problem unless you want to do things that need to be loaded on primaries.  Your HD will read only 4 of those.

I believe I am right that Linux does not need a primary partition to boot.  I believe Windows and BSD, to name two, both do.

So if you are going to work your way toward a multiple-boot system you might have to do an Ubuntu reinstall and "liberate" one or two of those primary partitions.

As compared to Dell the tech support available here  puts Dell to shame, frankly.  It is no small reason why I would buy another System 76 product.

---

### Post by HotShotDJ on 2009-07-28
I'd like to thank everybody for their very helpful replies! Now I just need to cross my fingers and hope that the finances work out as planned.  I'm a little disappointed in the low battery run time -- I was hoping to see 3.5 to 4 hours.  But thats just a matter of making sure I have an AC adapter with me when I'm out and about.

I'm especially impressed that ThomasAaron took the time to post a reply.  With Dell, getting pre-sales information was like pulling teeth -- and now that my E1505 is out of warrantee, they won't speak to me at all.  I've been browsing the System76 threads, and have been impressed with the service being provided by ThomasAaron in this forum.  That, alone, is reason enough to make a purchase from System76.

My main reason for needing a new computer is because I am a non-traditional (read: old) graduate student.  Now that I'm beginning my thesis, my thesis committee requires everything be in *.docx format.  The university has kindly provided Windows XP, Office 2007, and SPSS 16 for Windows, all of which I run using VirtualBox (I will not "dual-boot" -- I want instant access to my real software, even when working in Windows).  But, my current laptop maxes out at 2G ram and the CPU has no hardware virtualization support.  Further, since I've put all this time into my M.A., I'll be continuing on to earn my Ph.D., so I need a computer that will meet my needs well into the future.  Once I enter Ph.D. candidacy, I'll have no money beyond my basic living expenses.

I've also considered the Serval Professional -- but I have to ask myself: do I really want to carry around 7.1 pounds around a college campus?  I feel old enough already! ;)  The smaller and lighter Gazelle would be nice if my eyes were 10 years younger.

Any further thoughts would be appreciated!

---

### Post by marshmallow1304 on 2009-07-28
> **HotShotDJ said:**
> my thesis committee requires everything be in *.docx format.

That's ridiculous.

[http://www.gnu.org/philosophy/no-word-attachments.html](http://www.gnu.org/philosophy/no-word-attachments.html)

---

### Post by jdb on 2009-07-29
> **marshmallow1304 said:**
> That's ridiculous.

[http://www.gnu.org/philosophy/no-word-attachments.html](http://www.gnu.org/philosophy/no-word-attachments.html)

Thesis comittees can be very anal about things like that.

jdb

---

### Post by HotShotDJ on 2009-07-29
> **marshmallow1304 said:**
> That's ridiculous.While tend to agree with the gnu philosophy, there are just certain comprises I have to make if I want certain individuals to serve on my thesis committee. Simply put, either I must comply with their requirements, or they will not sit on my committee.  The individual who is requiring *.docx formats also has expertise in my area of research that nobody else at my university has. In the end, I want the best committee possible, even if that means having to use software and file formats that go against my philosophical preferences.

Remember... once I have a few more letters after my name, I'll have the same academic freedom being exercised by my committee to require ODF documents from MY students.  So, the short-term compromise is worth it in the long run. :)

---

### Post by 3Miro on 2009-07-30
So what's wrong with .pdf?

Anyway, try Virtual Box, at least the VB is free (as in freedom).

---

### Post by HotShotDJ on 2009-07-30
> **3Miro said:**
> So what's wrong with .pdf?

Anyway, try Virtual Box, at least the VB is free (as in freedom).Nothings wrong with PDF... thats what I usually use.  But, I have to use what the committee wants for reasons I've already mentioned.  And... yes... I've been using VirtualBox for years.  Its the only way I would run Windows... nice and safe in its own little virtualized sandbox.

---

### Post by thomasaaron on 2009-07-30
HotShotDJ, I like to think of it this way:

When you dual-boot Windows, Windows exists alongside of Ubuntu.
When you use VirtualBox, Windows exists at the pleasure of Ubuntu.

I prefer the latter.

---

### Post by HotShotDJ on 2009-07-30
> **thomasaaron said:**
> HotShotDJ, I like to think of it this way:

When you dual-boot Windows, Windows exists alongside of Ubuntu.
When you use VirtualBox, Windows exists at the pleasure of Ubuntu.

I prefer the latter.LOL!  I very much like that way of thinking about it.  There's a good chance that you'll catch me stealing that line.

---

### Post by thomasaaron on 2009-07-30
That's cool. :popcorn:
Maybe you can tag it with a link to System76. :D

---

### Post by MarkID on 2009-07-31
Has anybody tried this?

[www.docx-converter.com]("http://www.docx-converter.com")

---

