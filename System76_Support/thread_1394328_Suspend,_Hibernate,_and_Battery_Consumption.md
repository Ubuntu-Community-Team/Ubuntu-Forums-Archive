---
title: "Suspend, Hibernate, and Battery Consumption"
date: 2010-01-30
forum: System76 Support
---

### Post by cmnorton on 2010-01-30
I have a Gazelle Ultra running 9.10. I turn my computer on and off too much during the day, and would like to use Suspend or Hibernate. 

How much power do the Suspend and Hibernate functions consume?

Which is the best to use, if the unit is fully charged, but won't be recharged more than once a day?

In other words, are there some guidelines you can point me to on whether Suspend or Hibernate to use and how much power each state consumes?

Thanks.
cmn

---

### Post by perce on 2010-01-30
When a computer is hibernated it is shut off, so it consumes no power.

---

### Post by Derath on 2010-01-30
To expand on this a little, basically the computer saves the state of all applications and all to the hard drive and then shuts off, suspend (if I recall correctly) saves the state to memory and reduces power consumption to all other devices, and just keeps power running to the memory to continue the memory state.

If I am mistaken, please feel free to correct this, I'm running on assumptions and generic word-of-mouth on how exactly it works.

---

### Post by miniyak on 2010-02-01
Suspend is worth the small amount of battery capacity it shaves off imho

my panp5 could probably stay in suspend for a few days... come to think of it, its always in suspend and ive never really got a chance to test out  how much suspend drains over two ... lol

i think it drops to 70% over two days but i wouldn't quote that, and its going to be different(better) for the gazelle

---

### Post by PGScooter on 2010-02-01
my panp5 went from 100% to 87.4% in 8 hours on battery

---

### Post by cmnorton on 2010-02-02
> **PGScooter said:**
> my panp5 went from 100% to 87.4% in 8 hours on battery

Good. I can probably let it stew on batteries over at least a four-hour period. Thanks for all the answers to this.

---

### Post by miniyak on 2010-02-03
im probably a poor comparison to the average piece of hardware. I'm only using one Dimm of 2gb. Most folks I would assume have dished out for a second ram stick. Would explain differences in reported time... though now that i think of it more then 2-3 days in stand-by would probably be a stretch.

---

### Post by amasiar on 2010-02-05
How safe is Suspend on the hard drive? i.e. is it safe to suspend then jump on my bike and ride home? I imagine the hard drive is off so the vibrations won't damage it.

I've never actually drained the battery fully, but I've had my laptop for only few days.

---

### Post by jdb on 2010-02-05
> **amasiar said:**
> How safe is Suspend on the hard drive? i.e. is it safe to suspend then jump on my bike and ride home? I imagine the hard drive is off so the vibrations won't damage it.

I've never actually drained the battery fully, but I've had my laptop for only few days.

The disk spins down & docks in suspend.
Mechanically the disk is in the same condition as if the laptop where powered down.

jdb

---

### Post by amasiar on 2010-02-06
Seems like the hard drive is still spinning in suspend. Is that possible? I put my ear next to the hard drive bay and it sounds just like when its on. I think hibernate is the way to go if you are going to be moving the computer around

---

### Post by amasiar on 2010-02-06
except hibernate doesn't do anything except lock the screen :(

---

### Post by miniyak on 2010-02-07
if the internal hard drive is spinning, the computer is in in a state other then suspend.

When in suspend only the Ram is powered for the most part.

regardless if you expecting a extremely bumpy trip this could still harm a HDD even when its powered off and getting and SSD may be a consideration if the budget allows it.

Im just waiting till they come down in price..

---

### Post by viktor.pec on 2011-01-08
> **amasiar said:**
> Seems like the hard drive is still spinning in suspend. Is that possible? I put my ear next to the hard drive bay and it sounds just like when its on. I think hibernate is the way to go if you are going to be moving the computer around
There are 4 states in which computer may be. Found short info in ["Standby Explained (S1, S3)"]("http://blogs.msdn.com/b/omars/archive/2004/05/11/129553.aspx").
Your BIOS may be set to go to the state S1 on default when suspend is asked. Check with your BIOS and/or motherboard manual. (If it is still an issue, this is quite old post.)

---

