---
title: "SSD: 2m hours of use = 228 years?"
date: 2009-07-17
forum: The Cafe
---

### Post by froggyswamp on 2009-07-17
Folks, how do I calculate it correctly? An SSD claims 2m hours of use which / 24 / 365 = 228 years of use to me, but it can't be true.

The SSD is here:
[http://www.markstechnologynews.com/2009/01/puresilicon-nitro-worlds-first-1tb-ssd.html](http://www.markstechnologynews.com/2009/01/puresilicon-nitro-worlds-first-1tb-ssd.html)

---

### Post by benj1 on 2009-07-17
could that be read only ? i thought the wear only occured in writing.

edit: [this]("http://www.storagesearch.com/ssdmyths-endurance.html") says 2million writes (lasting 51 years) maybe some body got confused

---

### Post by froggyswamp on 2009-07-17
Well, I guess you're right, "reads or writes" instead of "hours" makes much better sense.

---

### Post by tgalati4 on 2009-07-17
What's the warranty on these drives?

---

### Post by froggyswamp on 2009-07-17
The one I'm talking about is yet to be released this Autumn, as you can read from the URL from the 1st post.

---

### Post by Bart_D on 2009-07-17
> **froggyswamp said:**
> ...**how do I calculate it correctly**?...228 years of use to me, but it can't be true....

You can't calculate it correctly....it's too early in the life of SSDs(any SSD, not just the one you posted) to make such determinations.

It all depends on how much you use the drive.  Is it your only drive?  If not, what exactly have you installed on the SSD?  How often will you writing to the SSD?  Which operating system are you using?  Windows XP* could tear an SSD to shreds in less than 5 years due to a lack of TRIM support.  If you're using XP anyways, what processes have you turned off?  Have you partitioned the drive correctly?  Again, XP does NOT do it correctly.  Partitioning tools are available free but they need to used to set up the disk before installing the OS.  The same holds true for Linux..and again, it MUST be done before installation.  Has the user done this?  These are not like HDDs....they are NOT aligned correctly by default and doing this incorrectly or not doing it at all will reduce the life of a SDD, and this process is not clear cut either......there's still debate as to what is the best way to align.

Have you tweaked the operating system AFTER installing?  Tweaked for optimal performance that is.  Essentially, you need to write AS MUCH as possible to a 2nd drive..a HDD and minimize writes to the SDD.  You've got to tweak it correctly and monitor the drive's performance almost on a daily basis to track down any undesirable results.

There's so many things to consider.  Will the average user do ANY of the above?  Probably not.....they just hear that the SSD is supposed to be faster so they pop it in, install the OS and are on their way...bad!  Does the calculation of mean lifetime of the drive take ALL this into account?  It would have to be one complicated calculation if it did.

*Apparently Windows 7 WILL have some sort of TRIM support.  Don't know about Vista.

Oh and BTW, **Intel**'s 2nd gen drives are due for release late this year....**THOSE** WILL be the fastest SSDs BAR NONE!

---

### Post by hessiess on 2009-07-17
Personally I am still very sceptical about SSD's, they are a new and relativity untested technology.

HDD,s store there information as a magnetic field, meaning that data recovery in the event of a complete drive failure, is difficult but not imposable. Data recovery from damaged SSD's is still a area which has yet to mature, and is lickly to be more complicated than HDD recovery, especially in the case of a power serge damaging the internals of a chip.

---

### Post by jespdj on 2009-07-17
But HDDs are sensitive to shocks and movement, your HDD can crash if you move your laptop too violently when it's reading or writing data. HDDs also use a lot more power than SSDs. SSDs have no moving parts and therefore are not sensitive to movement and use less power. Most SSDs are also much faster than HDDs.

The performance of an SSD highly depends on the controller. There are only a handful of manufacturers that make controllers and a lot of manufacturers of SSDs use the same controllers.

SSDs have been around for a few years and are getting better, faster and cheaper, though they are still relatively expensive. Where I live (in the Netherlands) you can get a good 128 GB SSD for around € 300 and a good 256 GB SSD for around € 600.

For more info on how SSDs work, see for example: [http://www.anandtech.com/printarticle.aspx?i=3531](http://www.anandtech.com/printarticle.aspx?i=3531)

---

### Post by Bart_D on 2009-07-17
> **jespdj said:**
> But HDDs are sensitive to shocks and movement, your HDD can crash if you move your laptop too violently when it's reading or writing data. HDDs also use a lot more power than SSDs. SSDs have no moving parts and therefore are not sensitive to movement and use less power. Most SSDs are also much faster than HDDs....

SSDs will replace HDDs soon but, like **hessiess** said, they're not there yet.

---

### Post by toupeiro on 2009-07-17
I put FUD to the test when I built my last system and I run SSD for my OS.  dispicably fast, and only very, very few situations have occured where I felt a write penalty.  Setting  elevator=noop in my boot paramaters, and putting my system logs to a RAM disk helped 90% of that.
I have WoW on my SSD running in wine.  When I travel between continents, the new continent loads before the dots on the map even get there.  If you're doing a lot of writes, simply offload them to another disk.  When I copy this install to my 7K RPM hard drive, it does not perform this fast.

SSD is expensive per GB, but well worth the investment from a performance standpoint. Its still one of the cheapest investments you can make to give your rig a significant performance boost.

---

