---
title: "Is Desktop Linux finally being taken seriously?"
date: 2007-07-15
forum: The Cafe
---

### Post by phrostbyte on 2007-07-15
The University I go to is (with 30,000 students, 3,000-4,000 employees) actually considering Linux as an "upgrade" from Windows XP (what is currently being used). They are actually doing feasibility tests on this. About a year ago if you suggest desktop Linux to the same University they'd think you're making a funny.

---

### Post by lancest on 2007-07-15
Linux is hard to beat as an internet workstation for public use. (and more)  I hope your university gets the true Linux OS picture of security, stability and power. Because Vista is such an expensive and resource hog monster I predict more and more Universities will consider open source desktops in near future. LTSP or whatever.

---

### Post by smoker on 2007-07-15
> **phrostbyte said:**
> The University I go to is (with 30,000 students, 3,000-4,000 employees) actually considering Linux as an "upgrade" from Windows XP (what is currently being used). They are actually doing feasibility tests on this. About a year ago if you suggest desktop Linux to the same University they'd think you're making a funny.

where in the world are you? there may be other universities close by using linux they can have communications with, for reccommendations, etc.

---

### Post by az on 2007-07-15
> **phrostbyte said:**
> The University I go to is (with 30,000 students, 3,000-4,000 employees) actually considering Linux as an "upgrade" from Windows XP (what is currently being used). They are actually doing feasibility tests on this. About a year ago if you suggest desktop Linux to the same University they'd think you're making a funny.

Probably the best way to look at it is not as an all-or-nothing situation.  It probably doesn't make sense to migrate all 10000 (or whatever the number of workstations it is) to linux right now.  Perhaps for 1000 of them, it would be ideal to switch to Ubuntu, and for another 1000 would completely out of the question.  Perhaps for the remaining 8000, Ubuntu would work fine enough, but there is no real need to migrate immediately.

What needs to be done is ensure that those first 1000 migrate and it goes well.  If they can integrate easily with the other boxes on the network, they that is a success.  The next task is to work on the other 8000 over time.

I pulled these numbers out of the air - your mileage may vary.  

Good luck and it would be interesting to get updates on this.  Are you or can you get involved?

---

### Post by Matakoo on 2007-07-15
> **phrostbyte said:**
> The University I go to is (with 30,000 students, 3,000-4,000 employees) actually considering Linux as an &quot;upgrade&quot; from Windows XP (what is currently being used). They are actually doing feasibility tests on this. About a year ago if you suggest desktop Linux to the same University they'd think you're making a funny.

 I hope it goes well, but it is not necessarily a good choice. For general purpose workstations available to the students, it should work easily enough. I mean, computers where the only thing the students has access to is an office package, a web browser, and a homedirectory to save things in. A common enough setup, but there are pitfalls even there. For example, some electronic libraries require a browser plugin that, as far as I know, is only available for Internet Explorer. It's called ebrary, but on the plus-side the developers are hoping to get a Linux plugin released shortly.  And depending on the curriculum, there may be a need for software that isn't available for Linux natively. That was the case in some of my linguistic classes for example...okay, the software in question runs using wine but not as well as on XP. That may not always be possible to do, or worthwhile even if it is possible.  I don't want to be a harbinger of doom, but there are many reasons why a migration may not work out. And I would hazard a guess that not every workstation will be migrated. The university I'm enrolled in uses XP, MacOS and Linux on the desktops, and I don't think a mixed environment is uncommon. Then again, many universities are also using thin clients...  But I do think that Linux on the desktop is being taken more seriously now compared to say just a year or two back.

---

### Post by stmiller on 2007-07-15
Lots of Linux desktop support IT jobs in the Bay Area:

[http://sfbay.craigslist.org/search/jjj?query=desktop+support+linux](http://sfbay.craigslist.org/search/jjj?query=desktop+support+linux)

I think things are looking up.

---

### Post by markusf21 on 2007-07-15
Its not where it should and one day will be but its getting there. just look at dell

---

### Post by phrostbyte on 2007-07-15
> **Matakoo said:**
> I hope it goes well, but it is not necessarily a good choice. For general purpose workstations available to the students, it should work easily enough. I mean, computers where the only thing the students has access to is an office package, a web browser, and a homedirectory to save things in. A common enough setup, but there are pitfalls even there. For example, some electronic libraries require a browser plugin that, as far as I know, is only available for Internet Explorer. It's called ebrary, but on the plus-side the developers are hoping to get a Linux plugin released shortly.  And depending on the curriculum, there may be a need for software that isn't available for Linux natively. That was the case in some of my linguistic classes for example...okay, the software in question runs using wine but not as well as on XP. That may not always be possible to do, or worthwhile even if it is possible.  I don't want to be a harbinger of doom, but there are many reasons why a migration may not work out. And I would hazard a guess that not every workstation will be migrated. The university I'm enrolled in uses XP, MacOS and Linux on the desktops, and I don't think a mixed environment is uncommon. Then again, many universities are also using thin clients...  But I do think that Linux on the desktop is being taken more seriously now compared to say just a year or two back.

Well most of the computers default to Firefox anyways. The problem is as you said, some software which only runs on Windows. Surprisingly not that much that we need. Visual Studio 2005 ironically is needed for some CS classes, AutoCAD is needed for civil engineering. But you'd be surprised on how much specialized software runs natively on Linux. ProE which is used for mechanical engineering has a Linux port, as well as Matlab, a very important program in the school. Maya is on Linux, but Photoshop is not. Mostly the idea is to see how much software we can get running on Linux natively (or alternatives) and we are looking to virtualize the rest.

---

### Post by Matakoo on 2007-07-16
> **phrostbyte said:**
> Well most of the computers default to Firefox anyways. The problem is as you said, some software which only runs on Windows. Surprisingly not that much that we need. Visual Studio 2005 ironically is needed for some CS classes, AutoCAD is needed for civil engineering. But you'd be surprised on how much specialized software runs natively on Linux. ProE which is used for mechanical engineering has a Linux port, as well as Matlab, a very important program in the school. Maya is on Linux, but Photoshop is not. Mostly the idea is to see how much software we can get running on Linux natively (or alternatives) and we are looking to virtualize the rest. 

Yeah, there are many things that do run natively. And in many cases when that isn't the case, there are good alternatives. Reading my post again...it sounded rather negative. Far more than necessary really, since I do think that Linux is more than ready to tackle Microsoft on the desktop.  

For the situations when a windows-only program is required, I would set-up some sort of seamless remote desktop to an application server. 

I have to laugh at the Visual Studio requirement...admittedly, it's a good IDE (at least according to those I know who are more into application development than I am) but it's still just a development environment. It's kinda like telling people that MS Office is the only office suite in town if you want to produce good essays...without acknowledging that it's more important what you put in your code/essay than the tools used. 

That could be said about CAD-software too (as just one example), of course, but since those are more specialized I'm not surprised there are fewer options in that regard. Kinda odd that Autodesk hasn't made Autocad available but Maya is...since, IIRC, they are the makers of Maya as well.

---

