---
title: "Turn off hard drives?"
date: 2008-12-02
forum: Server Platforms
---

### Post by tstack77 on 2008-12-02
I have Intrepid server installed on a cf card with 2 sata HDs for my personal files (not raid). How do I set a HD spin-down time for the two sata disks?

Side: I also have webmin installed if there's an easier method going that route.

---

### Post by CrucifiedEgo on 2008-12-02
You probably don't want to do this.

Spinup/down lowers the useful life of your hard drive.  If you're going to be accessing them fairly often, it's a bad idea if you like your data intact.

OTOH, if you only access it once or twice a day, you could save some cash on your electric bill (if you're like me where power bills are sky high, that's important) it should work fine.  That said...

I have no clue how to do this.  I'll hit google and edit this post if i come up with anything.

---

### Post by MJN on 2008-12-02
With IDE drives this was always achieve using hdparm and the -S option.

For example, **sudo** **hdparm -S 120 /dev/hda** would set the spindown timer for hda to 10 minutes (see the hdparm man page for details on the rather quirky time definitions).

I don't know if this will work with SATA drives but it might be worth a try (setting the timeout to a very low value, say 10 seconds, is a good way to test it - of course in proper use this would be a little aggressive).

Mathew

---

### Post by Vegan on 2008-12-02
The avage 3-1/2 inch drive used 10W of power, so that is like 2 cets a month per disk, so its not much of a power saving.

:guitar:

---

### Post by mitchroberts on 2008-12-02
> **Vegan said:**
> The avage 3-1/2 inch drive used 10W of power, so that is like 2 cets a month per disk, so its not much of a power saving.

:guitar:

I do agree 2 cents is not much of a savings.

---

### Post by MJN on 2008-12-03
> **Vegan said:**
> The avage 3-1/2 inch drive used 10W of power, so that is like 2 cets a month per disk, so its not much of a power saving.
 
:guitar:Whilst I'm not disputing the benefits (or not) of whether it is worth spinning drives down (particularly given the performance issues and physical aspects such as thermal cycling) can you show me the calculation you used that equates 10W to costing 2c per month?
 
When I tapped the sum out I got a figure completely out of your ballpark:
 
(Convert W into kW): 10W/1000 = 0.01kW
(Calculate power usage over 1 month): 0.01kW x 24hrs x 30days = 7.2kWh per month
(Calculate cost @10 cents/kW): 7.2kWh x 10cents/month = **72 cents/month**
 
So whilst it's still not a great deal, it is 35 times more than you thought and hence worth questioning your premise.
 
Of course, it could be my figures/calculations that are wrong in which case feel free to point out the error of my ways! (I'm guessing it might be the electricity costs as I live in the UK hence had to make assumptions about what you guys in the US pay).
 
Again, I'm not disputing the practical benefit for a single machine/disk but am wondering where your figure came from as when you extrapolate over multiple devices the discrepencies between our figures become significant.
 
Mathew

---

### Post by Philio on 2008-12-03
> **MJN said:**
> **72 cents/month**

That's a bit cheaper than a new hard drive :)

Keep it on for 5 years solid @ $0.72/month and it's still cheaper than a new hard drive!

---

### Post by MJN on 2008-12-03
> **Philio said:**
> That's a bit cheaper than a new hard drive :)Indeed.
 
My point was merely that 72c != 2c by any stretch of the imagination!
 
Mathew

---

