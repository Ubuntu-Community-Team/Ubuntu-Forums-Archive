---
title: "BOINC and CPU longevity"
date: 2009-12-05
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-12-05
Are the heatsinks that AMD provides enough to the CPU from overheating if I kept it running at or around 100% capacity for most of the day?

Also, will running it like this shorten the lifespan of my CPU or will I probably be looking to get a new computer before that would ever come into play?

---

### Post by soni1770 on 2009-12-05
laptop? desktop?

---

### Post by blueshiftoverwatch on 2009-12-05
> **soni1770 said:**
> laptop? desktop?
Desktop, specs are in my signature.

I guess I should have made it clear that I was running it on the computer that's in my sig.

---

### Post by Xbehave on 2009-12-05
Custome heatsinks/fans are often better, but generally if a CPU gets  too hot it will slow itself down instead of breaking

---

### Post by soni1770 on 2009-12-05
yea, i would not worry, but that's just me....

i've heard it's not so much constant running at a high temp but constant changes in temp that cause problems with solder joints etc..

but tv work great for years. so maybe not.

find out what the cutoff for your cpu is then see how far away from this  you are at 100%

running it at night when it's cold with the window open can knock a few degrees of, if you don't live on the ground floor;)

in the ternimal type 

sensors,

if you don't have them installed it will tell you how.

sensors should tell you current temp plus critical temp.

i run mine at 100% for 12hrs a night. no worrys yet

---

### Post by tom66 on 2009-12-05
Most heatsinks will more than support running the processor at full pelt for a long time. They should be designed to take away at least the TDP of the processor and a bit more. 

Running a CPU at 100% will reduce its life. However, it will be minimal - most CPUs are rated for 100,000hrs even under heavy load - that's about 11 years.

---

### Post by blueshiftoverwatch on 2009-12-05
> **Xbehave said:**
> Custome heatsinks/fans are often better, but generally if a CPU gets  too hot it will slow itself down instead of breaking
I was thinking of getting one anyway for overclocking purposes. Although I haven't done any research yet.

I've heard that Intel processors will slow down or stop if they overheat wheras AMD processors will burn up. Of course, the people who have told me this were Intel fanboys. Is there any truth to this?
> **soni1770 said:**
> 
in the ternimal type sensors,

if you don't have them installed it will tell you how.
I installed lm-sensors, ran sensors-detect, went through the wizard, scanned for everything, found some, told it to automatically add the lines into my /etc/modules file, checked the file myself, and restarted the computer. But when I type in 'sensors' it still says that there were no sensors found and tells me to run the 'sensors-detect' command again.
> **tom66 said:**
> Running a CPU at 100% will reduce its life. However, it will be minimal - most CPUs are rated for 100,000hrs even under heavy load - that's about 11 years.
Good to know.

---

