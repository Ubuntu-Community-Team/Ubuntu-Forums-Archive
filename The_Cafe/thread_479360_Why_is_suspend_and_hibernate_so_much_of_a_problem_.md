---
title: "Why is suspend and hibernate so much of a problem in linux?"
date: 2007-06-20
forum: The Cafe
---

### Post by mthakur2006 on 2007-06-20
Hi,
Why is suspend and hibernate so much of a problem in linux? is it because of the drivers or something else? on my fiesty, the clean install can suspend and restore succesfully but after installing the updates, it can't.
Why is it so much of a pain?
thanks.

---

### Post by Roger Gundberg on 2007-06-20
A long time ago (under windows) I realized there may be a conflict of some sort  with the BIOS. So I went into the BIOS and set all power management to 'disable'  and  handed all power management  off to the software.  This worked for me  maybe it  will work for you?

---

### Post by king0lag on 2007-06-20
Same problem here, at first it would give me a friendly little "doh" but now it doesn't work at all, doesn't give me any reason just pops back on :(

---

### Post by blah blah blah on 2007-06-20
It's a kernel thing.

---

### Post by PriceChild on 2007-06-20
If you use binary drivers, e.g. nvidia or fglrx (ati/radeon/nv/i810 etc. are ok) then you can forget resume.

Basically the binaryness means linux developers don't know how to reinitialise the card and so your resume fails.

Use purely open source drivers and you "should" be ok.

---

### Post by mthakur2006 on 2007-06-20
> **PriceChild said:**
> If you use binary drivers, e.g. nvidia or fglrx (ati/radeon/nv/i810 etc. are ok) then you can forget resume.

Basically the binaryness means linux developers don't know how to reinitialise the card and so your resume fails.

Use purely open source drivers and you "should" be ok.

i have opensource intel drivers, a conexant driver but it used to resume before when i had the conexant driver.
the only thing i think would have caused it would be this power management thread: [http://ubuntuforums.org/showthread.php?t=419772&highlight=ipw2200+power+save](http://ubuntuforums.org/showthread.php?t=419772&highlight=ipw2200+power+save) :confused:

---

### Post by prizrak on 2007-06-20
The answer to your question is the following:
Every manufacturer implements their ACPI in their own way that is somewhat different from others. Because of that it may work well on one machine and not on another. Perhaps there was a bug fix that enabled suspend/resume on ASUS machines but that broke it on Lenovo. It's kind of tricky with such crappy standardization.

---

### Post by strabes on 2007-06-20
If you have an ati card follow the guide in the link in my sig

---

### Post by mthakur2006 on 2007-06-20
cool, but i have an intel card, the desktop has ati and it works fine, no need for ddrivers or anything

---

### Post by Polygon on 2007-06-21
> **PriceChild said:**
> If you use binary drivers, e.g. nvidia or fglrx (ati/radeon/nv/i810 etc. are ok) then you can forget resume.

Basically the binaryness means linux developers don't know how to reinitialise the card and so your resume fails.

Use purely open source drivers and you "should" be ok.

wrong.

i use a ati card (ati radeon 9800 128mb) and i use the binary fglrx, and both suspend and hibernate work perfectly for me, except for a outstanding bug where alsa screws up and i get no sound when i come out of hibernate/suspend

but other then that it works perfectly.

---

### Post by DoctorMO on 2007-06-21
I wouldn't mind but in the recent US anti trust case, papers show that Microsoft diddled the ACPI specs with each hardware vendor in order to prevent other os makers using ACPI. a very interesting read since it was the text between members of Microsoft and various hardware partners. you can see most of that stuff on Groklaw.

---

### Post by prizrak on 2007-06-21
> **Polygon said:**
> wrong.

i use a ati card (ati radeon 9800 128mb) and i use the binary fglrx, and both suspend and hibernate work perfectly for me, except for a outstanding bug where alsa screws up and i get no sound when i come out of hibernate/suspend

but other then that it works perfectly.

Yeah on Dapper my nVidia laptop would suspend/resume w/o an issue. The new nVidia driver breaks it tho.

---

### Post by king0lag on 2007-06-24
> **king0lag said:**
> Same problem here, at first it would give me a friendly little "doh" but now it doesn't work at all, doesn't give me any reason just pops back on :(

I have to take this back, I traced my problem to a faulty AC Adapter for my laptop. Hibernate now works perfectly again! :)

Final Solution: If hibernate is failing, ask your cats if they chewed your wires.

---

### Post by macogw on 2007-06-25
> **DoctorMO said:**
> I wouldn't mind but in the recent US anti trust case, papers show that Microsoft diddled the ACPI specs with each hardware vendor in order to prevent other os makers using ACPI. a very interesting read since it was the text between members of Microsoft and various hardware partners. you can see most of that stuff on Groklaw.

As usual, MS breaks standards.  What else is new?  They still, with all the thousands of programmers and millions of dollars they have, can't make a web browser follow standards. Of course they're trying to kill interoperability at every turn.  It's the only thing they have left to keep people buying their crap.

---

### Post by sedd on 2007-06-26
> **PriceChild said:**
> If you use binary drivers, e.g. nvidia or fglrx (ati/radeon/nv/i810 etc. are ok) then you can forget resume.

Basically the binaryness means linux developers don't know how to reinitialise the card and so your resume fails.

Use purely open source drivers and you "should" be ok.

> **Polygon said:**
> wrong.

i use a ati card (ati radeon 9800 128mb) and i use the binary fglrx, and both suspend and hibernate work perfectly for me, except for a outstanding bug where alsa screws up and i get no sound when i come out of hibernate/suspend

but other then that it works perfectly.

Try this one: suspend/resume works for me with proprietary nvidia drivers, but NOT with opensource nv drivers. Its way more complicated than simplistic "opensource = good, proprietary = bad" FUD.

---

### Post by juxtaposed on 2007-06-26
> They still, with all the thousands of programmers and millions of dollars they have, can't make a web browser follow standards.

But since Internet Explorer is the standard (as it is the most used), doesn't it therefore automatically follow standards (if you are the standards, then you follow them...).

---

