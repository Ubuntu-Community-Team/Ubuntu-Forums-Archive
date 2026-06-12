---
title: "The great zero challenge"
date: 2008-09-06
forum: The Cafe
---

### Post by Dr Small on 2008-09-06
> A challenge to confirm whether or not a professional data recovery firm or any individual(s) or organization(s) can recover data from a hard drive that has been overwritten with zeros once. We used the 32 year-old Unix dd command using /dev/zero as input to overwrite the drive. Three data recover companies were contacted. All three are listed on this page. Two companies declined to review the drive immediately upon hearing the phrase 'dd', the third declined to review the drive after we spoke to second level phone support and they asked if the dd command had actually completed (good question).

[http://16systems.com/zero/index.html](http://16systems.com/zero/index.html)

---

### Post by init1 on 2008-09-06
Yeah, I have wondered if it was necessary to use random data or if just 0's was enough.

---

### Post by happysmileman on 2008-09-06
Wow, $40 + a ($60?) crappy hard drive to do this, and you're only allowed disassemble it if you're an expert.

People aren't not doing it because it's hard (although I imagine it would be ridiculously difficult unless you happen to work for the NSA), they're not doing it because of it's ridiculous limitations on how you do it, paying postage both ways and very littel reward

---

### Post by Trail on 2008-09-08
Nice one.

---

### Post by LaRoza on 2008-09-08
> **happysmileman said:**
> Wow, $40 + a ($60?) crappy hard drive to do this, and you're only allowed disassemble it if you're an expert.

People aren't not doing it because it's hard (although I imagine it would be ridiculously difficult unless you happen to work for the NSA), they're not doing it because of it's ridiculous limitations on how you do it, paying postage both ways and very littel reward

Any security firm that could do it, would do it. 

They aren't doing it because they know it is "impossible".

---

### Post by smoker on 2008-09-08
> **LaRoza said:**
> Any security firm that could do it, would do it. 

They aren't doing it because they know it is "impossible".

this could save a bunch of companies a whole load of money. hard drive crushers aren't cheap, and the man hours used to remove every drive and crush it must be a fair amount of the budget.

---

### Post by LaRoza on 2008-09-08
> **smoker said:**
> this could save a bunch of companies a whole load of money. hard drive crushers aren't cheap, and the man hours used to remove every drive and crush it must be a fair amount of the budget.

If you ever had the option of playing with a hard drive, with the intention to make it unusable, you'd also know they are quite fun albeit, dangerous. Those platters are like dense little frisbees of death...

---

### Post by 3rdalbum on 2008-09-08
It's now $500 USD, not $40 USD as described in the screenshot :-)

The data can be recovered. Hard drive write heads are pretty precise, but there is a slight margin of error; small slivers of the hard drive will still have the original data where the second write pass has missed.

Researchers have also been able to read the exact magnetic charge that each bit of data has. If they know that the drive has been "zeroed" (overwritten with zeroes), then they can look at the minute differences in charge between each zero, to work out what the previous data was. The process is very slow, and measured in kilobytes per hour, but you'd be able to find the filenames.

Data recovery firms might not have this sort of technology on hand, but I'm sure they'd be able to contract it out if the level of payment was higher. And they might not even want to waste their time with the challenge since it's not actually real lost data.

---

