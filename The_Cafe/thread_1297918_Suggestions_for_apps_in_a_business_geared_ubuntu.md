---
title: "Suggestions for apps in a business geared ubuntu"
date: 2009-10-22
forum: The Cafe
---

### Post by pythonscript on 2009-10-22
I'm looking to make a custom ubuntu distro for a friend that's geared toward business/statistical work, and I'm wondering if anyone has any suggestions for good apps to include in it? I've used gnucash and R, but I'd like to know if anyone else has any suggestions. GUI's are great, so if someone knows of a great one for R, that's be helpful too. Thanks!

---

### Post by Paqman on 2009-10-22
If it's for a friend why don't you ask them what their business needs?

---

### Post by Sporkman on 2009-10-22
[SAS]("http://www.sas.com/"), which I think they offer Linux products.

---

### Post by Bölvaður on 2009-10-22
Spss ?

---

### Post by cariboo on 2009-10-22
An accounting program at least as good as Quickbooks or Simply Accounting.

---

### Post by Tibuda on 2009-10-22
[JGR]("http://jgr.markushelbig.org/JGR.html") and [R Commander]("http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/") are GUIs for R available as packages in CRAN. I don't use them, because I prefer to use scripting and command line.

---

### Post by pythonscript on 2009-10-22
> **Paqman said:**
> If it's for a friend why don't you ask them what their business needs?

She asked me for "general purpose business/stat software" in something that she could put on a few computers at work. She doesn't really know what specifics she's looking. Thanks to everyone for some of the suggestions!

> **cariboo907 said:**
> An accounting program at least as good as Quickbooks or Simply Accounting.

Any ideas on what this would be? In my experience, I've never found gnucash to be as powerful as Intuit's software.

---

### Post by Mateo on 2009-10-22
are you using gnome?  if so, gnumeric is a must.

---

### Post by pythonscript on 2009-10-22
What does gnumeric have over open office? I'm going to install open office by default, but if gnumeric has other features that Spreadsheet doesn't, I'll try to include that too.

---

### Post by Warpnow on 2009-10-22
> **pythonscript said:**
> What does gnumeric have over open office? I'm going to install open office by default, but if gnumeric has other features that Spreadsheet doesn't, I'll try to include that too.

It depends on the kind of stats they do...if its at an academic level (need to run regressions and such) neither will suffice. You'll need PSPP (most user friendly by far), R commander, or one of the other couple dozen stats softwares linux has.

---

### Post by pythonscript on 2009-10-22
All right, that's good information to have. Are all of the aforementioned packages (SAS, SPSS) either included in the repos like R, or free (as in beer)? Would their licenses restrict me from distributing them as part of a package I give to a group?

---

### Post by Sporkman on 2009-10-22
> **pythonscript said:**
> Are all of the aforementioned packages (SAS, SPSS) either included in the repos like R, or free (as in beer)?

No, SAS is not.

It is a leader in business analytics software, though, so an end user might need to buy & install it.

---

### Post by Warpnow on 2009-10-22
> **Sporkman said:**
> No, SAS is not.

It is a leader in business analytics software, though, so an end user might need to buy & install it.

If there's a linux version (only used the windows version) SAS is certainly not free. Its -very- expensive, I believe...like...don't think about it unless you're a big company or university.

---

### Post by pythonscript on 2009-10-22
I didn't think so; some of my students say they've used it, and that "it's great!" so it doesn't seem like the kind of software that would be released as free (beer or speech).

---

### Post by Sporkman on 2009-10-22
> **pythonscript said:**
> I didn't think so; some of my students say they've used it, and that "it's great!" so it doesn't seem like the kind of software that would be released as free (beer or speech).

I used to use it regularly when I was a transportation analyst - very powerful, good for analyzing huge data sets.

---

### Post by pythonscript on 2009-10-22
What about SPSS? Is that one free and distributable?

---

### Post by Warpnow on 2009-10-22
> **pythonscript said:**
> What about SPSS? Is that one free and distributable?

I believe its a GNU project, so, yeah, one assumes they'd use their own license. :D

---

### Post by pythonscript on 2009-10-22
I looked on the SPSS website, and I couldn't find any free downloads for Linux. Is their software really free (even free as in beer would be nice)?

---

### Post by Warpnow on 2009-10-22
> **pythonscript said:**
> I looked on the SPSS website, and I couldn't find any free downloads for Linux. Is their software really free (even free as in beer would be nice)?

Ah, no, misread your thread. SPSS is proprietary. PSPP is the gnu free alternative. I use PSPP for linear regression in my study of Economics. I like it. Extremely easy to use statistics application.

---

### Post by pythonscript on 2009-10-22
I just found PSPP, actually, and it sounds pretty good. I'm guessing there's no GUI with it, though, right?

---

### Post by Warpnow on 2009-10-23
> **pythonscript said:**
> I just found PSPP, actually, and it sounds pretty good. I'm guessing there's no GUI with it, though, right?

Its a GUI app. Pretty good GUI, too. Its in the repos, just apt-get install pspp.

Its very easy to use.

---

### Post by earthpigg on 2009-10-23
I'm just going to pop in and suggest this:

in *any* enviornment wherein multiple computers will be connected over a LAN, 'giver' is handy to have around.

no configuration needed.

the interface is much like an IM client, except instead of sending text it lets you send/recieve files without relying on any cloud or other layer of complexity.

---

### Post by mörgæs on 2009-11-04
#11: 

SAS is an expensive program for business purposes, but in some countries students can have it for free or for a small amount, if only used in study context.

---

### Post by pythonscript on 2009-11-04
> **mörgæs said:**
> #11: 

SAS is an expensive program for business purposes, but in some countries students can have it for free or for a small amount, if only used in study context.

I can get it for free through my university, but the license restricts me from distributing it with a live cd in a business environment, since the license is for "personal and educational use" only.

---

