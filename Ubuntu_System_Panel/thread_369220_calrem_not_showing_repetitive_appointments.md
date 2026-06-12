---
title: "calrem not showing repetitive appointments"
date: 2007-02-24
forum: Ubuntu System Panel
---

### Post by 4tro on 2007-02-24
I noticed some weird behaviour in my calrem using USP2 SVN repo

the appointments won't show repetitive appointments, it only shows the first appointment.

this is kinda annoying, cause i use the repetitive function to keep track of my  college timetable.

---

### Post by Malac on 2007-02-24
> **4tro said:**
> I noticed some weird behaviour in my calrem using USP2 SVN repo

the appointments won't show repetitive appointments, it only shows the first appointment.

this is kinda annoying, cause i use the repetitive function to keep track of my  college timetable.
I'll get on it first thing Monday 4tro. Although I am really busy this week.

---

### Post by 4tro on 2007-02-24
> **Malac said:**
> I'll get on it first thing Monday 4tro. Although I am really busy this week.

don't rush it ;-)
i can live with the gnome-panel calendar for the time being ^^

---

### Post by Malac on 2007-02-26
Okay 4tro new version uploaded to original post.
I think I've covered most eventualities but a few may have slipped through.
If you could let me know if this works, thanks.

---

### Post by 4tro on 2007-02-26
the repetitive appointments are showing nicely now...
but it seems it disregards the exceptions now, because today it gave me the day off && I had to be at school :P

---

### Post by Malac on 2007-02-26
> **4tro said:**
> the repetitive appointments are showing nicely now...
but it seems it disregards the exceptions now, because today it gave me the day off && I had to be at school :P
I never really use the evolution reminder functions so I am just putting in what I can think of as test data, exceptions I missed. :)
If you have nothing private in there and/or if you don't mind doing it could you send me a copy of your calendar.ics file as you seem to use most if not all of the options available. I'll use that as my test data instead.
You can e-mail me at the address on the [About] tab in Preferences/uspconfig.

---

### Post by 4tro on 2007-03-02
did you get my email?

---

### Post by Malac on 2007-03-02
> **4tro said:**
> did you get my email?
Yes I did 4tro, sorry I've not had any time this week to look at calrem at all. I'll hopefully get to it this weekend. :)

---

### Post by 4tro on 2007-03-03
yeah, i know the feeling... didn't do my homework this week though, so i updated to feisty.

I have to hand in a bunch of C exercises  on Monday. I'm looking forward to your post saying it is fixed (A)

---

### Post by Malac on 2007-03-10
Just to let you know I've not forgotten you. :)

It looks like I'm going to have to completely re-write the calrem plugin to get the features it needs. Inserting "fixes" into it was just making other things not work correctly and introduced other bugs and made the code pretty unreadable plus I'm sure execution speed was suffering. Which is why it is taking so long, coupled with the fact I'm busy at the moment with work.

I will let you know when It is done.

---

### Post by Malac on 2007-03-10
Okay 4tro, taken me four hours of solid re-write but I think I've got it now.
Can you try this one and see if all works as you would expect and the exclusions are working?

Thanks.

---

### Post by 4tro on 2007-03-11
i hate to tell you this...
The repetitive appointments do show up, but exceptions aren't handled :(
as you can see in the screenshot attached.

*edit*
after a complete reboot of usp, the problem stays, and it doesn't show my week off anymore, which can be recognized as being "vrij"

---

### Post by Malac on 2007-03-11
Aargh, back to the drawing board. :)
It's probably some anomaly with the evolution file again.

Can you just try a quick test for me and in calrem.py replace line 168:```
        pattern = "*.ics"
```with :```
        pattern = "calendar.ics"
```And see if that solves the problem. I think I may be scanning multiple files for no reason.

---

### Post by 4tro on 2007-03-12
replaced it but it doesn't solve it.
same behaviour

---

### Post by Malac on 2007-03-12
> **4tro said:**
> replaced it but it doesn't solve it.
same behaviour
Could you e-mail me your whole "calendar.ics" file as it is handling exceptions fine here. I will completely respect your privacy and delete it immediately the problem is solved.
I need to test it with yours as I can't seem to re-create the behaviour here.
Thanks.

---

### Post by Malac on 2007-03-13
Hi again 4tro,
:oops: Silly mistake on my part I coded for the recurring appointments and exclusions and forgot to set a case for just a single appointment on one day.
Here are the corrected files(Beta) :) still a little problem with VRIJ. Will work on that.

---

### Post by 4tro on 2007-03-14
what's wrong with the VRIJ, because as far as I can see it's working okay now 

many many thanks  =D>

---

### Post by Malac on 2007-03-14
> **4tro said:**
> what's wrong with the VRIJ, because as far as I can see it's working okay now 

many many thanks  =D>
It wasn't showing up the Bold Dates for that one. Here is one that does.

---

