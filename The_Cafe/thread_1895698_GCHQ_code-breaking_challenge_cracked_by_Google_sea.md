---
title: "GCHQ code-breaking challenge cracked by Google search"
date: 2011-12-15
forum: The Cafe
---

### Post by t0p on 2011-12-15
GCHQ (the branch of Brit security services that concentrates on comms interception, code-breaking etc) set up a code-breaking competition as a way to recruit more spooks.  But, according to [*The Register*]("http://www.theregister.co.uk/2011/12/03/gchq_code_crack_compo_snafu/"), the competiton results page was not protected from search engines, so a simple Google **site:** command could lead to successful completion of the task.

*The Register* says that the canyoucrackit.co.uk website was set up in partnership with a recruitment agency and that GCHQ probably had no hand in the competition's development.  So that's okay then...

---

### Post by haqking on 2011-12-15
> **t0p said:**
> GCHQ (the branch of Brit security services that concentrates on comms interception, code-breaking etc) set up a code-breaking competition as a way to recruit more spooks.  But, according to [*The Register*]("http://www.theregister.co.uk/2011/12/03/gchq_code_crack_compo_snafu/"), the competiton results page was not protected from search engines, so a simple Google **site:** command could lead to successful completion of the task.

*The Register* says that the canyoucrackit.co.uk website was set up in partnership with a recruitment agency and that GCHQ probably had no hand in the competition's development.  So that's okay then...


the code was 
```
Pr0t3ct!on#cyber_security@12*12.2011+
```

which led to [www.canyoucrackit.co.uk/soyoudidit.asp](www.canyoucrackit.co.uk/soyoudidit.asp)

it was no big deal it was only a code to get to page where you could apply for a job.

It was only 25K a year to make tea for everyone.

Anyways i recently emailed GCHQ to inform them of a ton of metadata leakage from the website to which they responded saying they would resolve it imminently and thanking me for doing so.

The fact is they shouldnt be leaking anything especially from a external publicly accessible website...LOL

Glad i dont work for them

---

### Post by Paqman on 2011-12-15
> **haqking said:**
> 
The fact is they shouldnt be leaking anything especially from a external publicly accessible website...LOL


It's highly unlikely that the drones that maintain their public-facing website have any kind of access to any sensitive information. They might not even be on GCHQ premises or even employees.

Once again, xkcd has a ready-made cartoon for just this situation:
[IMG]http://imgs.xkcd.com/comics/cia.png[/IMG]

---

### Post by haqking on 2011-12-15
> **Paqman said:**
> **It's highly unlikely that the drones that maintain their public-facing website have any kind of access to any sensitive information. They might not even be on GCHQ premises or even employees.**

Once again, xkcd has a ready-made cartoon for just this situation:


You would be surprised, however they have dealt with it now.  Metadata is not about the public website, the metadata referred to the GCHQ network infrastructure

---

### Post by CharlesA on 2011-12-15
> **haqking said:**
> You would be surprised, however they have dealt with it now.  Metadata is not about the public website, the metadata referred to the GCHQ network infrastructure
That sounds like a bad thing to be leaking. :p

Glad they took care of it.

---

### Post by haqking on 2011-12-15
> **CharlesA said:**
> That sounds like a bad thing to be leaking. :p

Glad they took care of it.

Indeed, i mean this was not difficult or time consuming to harvest, it took 10 minutes with metagoofil.

The fact is for an organisation who mission statement is about privacy and sensitive information were missing Security 101 concepts, any sys-admin worth a salt knows to remove metadata from any publicly accessible data along with 100 other basic principles.

Anyway i emailed them, they responded back in an hour and 10 minutes after the response it was removed.

Highly amusing really, but was not particularly eye opening as it happens alot.

---

### Post by CharlesA on 2011-12-15
> **haqking said:**
> Indeed, i mean this was not difficult or time consuming to harvest, it took 10 minutes with metagoofil.

The fact is for an organisation who mission statement is about privacy and sensitive information were missing Security 101 concepts, any sys-admin worth a salt knows to remove metadata from any publicly accessible data along with 100 other basic principles.

Anyway i emailed them, they responded back in an hour and 10 minutes after the response it was removed.

Highly amusing really, but was not particularly eye opening as it happens alot.
Ah I see. At least they removed it in a timely manner, even if it is something that shouldn't be exposed in the first place.

---

