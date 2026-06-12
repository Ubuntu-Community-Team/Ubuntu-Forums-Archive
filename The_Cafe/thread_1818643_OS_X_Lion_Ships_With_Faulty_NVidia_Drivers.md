---
title: "OS X Lion Ships With Faulty NVidia Drivers"
date: 2011-08-05
forum: The Cafe
---

### Post by lucazade on 2011-08-05
TeaCurran writes with this mildly ranty objection to the most recent Mac OS X update; several friends who have made the leap on their MacBook Pros have various other complaints, too, including system slowdowns that resemble crashes (except that their pointers still work) and recurring black screens for some configurations (with or without the kernel panics TeaCurran mentions) — what's been your experience?

"Apple OS X Lion shipped with new NVidia video drivers that are causing anyone with a mid 2010 Macbook Pro to get a _kernel panic every 5-10 minutes. Apple knew about the issue before shipping lion, hasn't responded to the issue, and is censoring posts in their support forum that mention words like 'boycott' and 'petition.' _NVidia has responded that the drivers are the responsibility of Apple so they won't deal with the issue. How a major hardware manufacturer can ship such a faulty product without getting much press about it is completely beyond me."

[http://apple.slashdot.org/story/11/08/04/2118220/OS-X-Lion-Ships-With-Faulty-NVidia-Drivers](http://apple.slashdot.org/story/11/08/04/2118220/OS-X-Lion-Ships-With-Faulty-NVidia-Drivers)

---

### Post by lz1dsb on 2011-08-05
I've never had an Apple laptop nor I've ever wanted to have one. To me they've always been hugely over priced, but quite slick, I can't deny that. I think it's a shame for a company like Apple to deal with the problem in such way - not admitting and denying...

---

### Post by el_koraco on 2011-08-05
Once more the lesson is repeated - don't do system upgrades.

---

### Post by sffvba[e0rt on 2011-08-05
> **el_koraco said:**
> Once more the lesson is repeated - don't do system upgrades.

... but "Lion" is so shiny...

---

### Post by KiwiNZ on 2011-08-05
I have updated my iMac, MacBook Pro and my Mac Pro to Lion and have had no issues what so ever.

---

### Post by el_koraco on 2011-08-05
> **not found said:**
> ... but "Lion" is so shiny...

If I were using OSX, I'd download Lion, extract and burn the image file to a USB and a DVD, make a backup, try the new method just for kicks, and if it didn't work do a clean install. It's the same thing that happens with Ubuntu release upgrades, most of them go off without a hitch, but when they break, boy do they break.

---

### Post by kaldor on 2011-08-05
> **KiwiNZ said:**
> I have updated my iMac, MacBook Pro and my Mac Pro to Lion and have had no issues what so ever.

Worth the upgrade in your opinion? I didn't see anything I was interested in apart from some minor unimportant things.

---

### Post by unknownPoster on 2011-08-05
> **KiwiNZ said:**
> I have updated my iMac, MacBook Pro and my Mac Pro to Lion and have had no issues what so ever.

Same. And I bought my Macbook Pro in May/June of 2010. No problems at all.

Obviously, this issue isn't affecting everyone as that article seems to claim.

---

### Post by 3rdalbum on 2011-08-05
They don't have a billion combinations of hardware. How could this happen to Apple? I bet it only affects older Macs; ones that Apple doesn't really mind breaking.

---

### Post by kaldor on 2011-08-05
> **3rdalbum said:**
> They don't have a billion combinations of hardware. How could this happen to Apple? I bet it only affects older Macs; ones that Apple doesn't really mind breaking.

If you had read it without jumping to the I-hate-Apple knee jerk response, you'd see that it affects some 2010 MacBook Pro models.

---

### Post by zekopeko on 2011-08-05
This only affects only some customers of the mid 2010 Macbook Pros. The slashdot article is lying when it say it affects all mid 2010 Macbook Pros.

Look like another "I'm affected so it's a huge disaster!" rant.

---

### Post by conundrumx on 2011-08-05
I hadn't heard of anyone experiencing these problems until now.  I think what's most likely (and quite common on the internet) is that a few people started making noise, and it's just rolled down a hill of outrage snowballing despite the small number of people affected.

No company is going to be allow their customers to talk about boycotting them on their own website; a fix is undoubtedly in the works, and anyone who's experienced permanent damage or problems should be able to take the machine in to Apple without too much fuss.

---

### Post by kaldor on 2011-08-05
> **conundrumx said:**
> I hadn't heard of anyone experiencing these problems until now.  I think what's most likely (and quite common on the internet) is that a few people started making noise, and it's just rolled down a hill of outrage snowballing despite the small number of people affected.

No company is going to be allow their customers to talk about boycotting them on their own website; a fix is undoubtedly in the works, and anyone who's experienced permanent damage or problems should be able to take the machine in to Apple without too much fuss.

Apple also recommended backups as well. Not Apple's problem if people got screwed over for failing to follow advice.

Still, I'd much rather do a clean install.

---

### Post by zekopeko on 2011-08-05
> **kaldor said:**
> Apple also recommended backups as well. Not Apple's problem if people got screwed over for failing to follow advice.

Apple really made backing up and restoring a breeze. Other solutions are light years behind the ease-of-use and simplicity.

---

### Post by kaldor on 2011-08-05
> **zekopeko said:**
> Apple really made backing up and restoring a breeze. Other solutions are light years behind the ease-of-use and simplicity.

I'm lazy, so all I ever do is copy my entire ~/ to an external drive and copy it back when needed. Time machine is pretty awesome, though.

---

### Post by LMP900 on 2011-08-05
In case anyone is checking this thread and suffering from the issue; Ars Technica has updated their article with an apparent solution.

[http://arstechnica.com/apple/news/2011/08/buggy-nvidia-drivers-giving-2010-macbook-pro-owners-lion-upgrade-headaches.ars](http://arstechnica.com/apple/news/2011/08/buggy-nvidia-drivers-giving-2010-macbook-pro-owners-lion-upgrade-headaches.ars)

[QUOTE=Ars Technica] A commenter noted that Apple Care support technicians have offered another solution which appears to have permanently solved the problem on his machine. Navigate to ~/Library/Preferences/ByHost/, delete any files that contain "windowserver," and reboot the machine. The procedure may need to be repeated if you regularly connect to an external monitor once it is also connected.

Note that the user Library folder is hidden by default on Lion. You can get to it by holding down the Option key in the Finder's Go menu, use the Go To Folder command and paste in the full path, or use Terminal to make your ~/Library folder permanently visible.[/QUOTE]

---

### Post by stefangr1 on 2011-08-05
On my 2009 MBP battery life seems to have gone down by at least 20% since the upgrade to Lion. I also did have some major problems with the Time Machine that is provided by my Ubuntu Server (took several hours to solve, haven't had any problems since).

---

