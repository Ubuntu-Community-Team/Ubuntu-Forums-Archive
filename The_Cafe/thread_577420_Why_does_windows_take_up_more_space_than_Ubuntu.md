---
title: "Why does windows take up more space than Ubuntu?"
date: 2007-10-16
forum: The Cafe
---

### Post by Ultra Magnus on 2007-10-16
Ok I have a random question - I have Ubuntu and Vista installed  on my laptop -  I have a separate / and /home partition and ubuntu has used up 3Gb of my / partition, Vista takes up 10Gb of its partition:

Why does Windows take up so much space - All I have on vista is McAffee Anti Virus (came with my computer) and Firefox and no Files or anything else. 

I've used up 40.6Gb of my /home partition So I haven't counted that in with the amount of space Ubuntu is taking up - I don't think an empty /home directory would take up too much though, atleast not 7GB to make up the difference

My Windows Pagefile.sys is 1.3Gb - I have about the same for my swap partition so why does Windows use 5.7Gb more than Ubuntu when I have loads of stuff installed on Ubuntu and there is almost nothing on Vista?

---

### Post by pmagill on 2007-10-16
This should clear some things up for you [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)


(irc.freenode.net #ubuntu) Paddy_EIRE

---

### Post by igknighted on 2007-10-16
I have always loved that article pmagill, but I fail to see the relevance here.

@ the OP: The simple fact is that Microsoft is not concerned with how much HD space its operating system takes up.  If you consider that you need a solid 1gb of ram, you are looking at this being installed on computers that were built recently.  And these days, extremely high capacity HD's are very cheap.  You could probably get half a terabyte for around $100 (I got a quarter terabyte external for $70... so not unthinkable I would imagine).  With prices like this, a couple gb's more used my the OS seems trivial, and hence minimizing the footprint is not a big deal to them.  Honestly, I would be more concerned about the RAM footprint.

EDIT: $90, half a terabyte: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073R](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073R)

---

### Post by cogadh on 2007-10-16
Simple answer: Windows has more bloat than Linux

---

### Post by igknighted on 2007-10-16
> **cogadh said:**
> Simple answer: Windows has more bloat than Linux

Thats not that _answer_, that is the observation.  The question was why.

---

### Post by Ultra Magnus on 2007-10-16
> **igknighted said:**
> I have always loved that article pmagill, but I fail to see the relevance here.

@ the OP: The simple fact is that Microsoft is not concerned with how much HD space its operating system takes up.  If you consider that you need a solid 1gb of ram, you are looking at this being installed on computers that were built recently.  And these days, extremely high capacity HD's are very cheap.  You could probably get half a terabyte for around $100 (I got a quarter terabyte external for $70... so not unthinkable I would imagine).  With prices like this, a couple gb's more used my the OS seems trivial, and hence minimizing the footprint is not a big deal to them.  Honestly, I would be more concerned about the RAM footprint.

EDIT: $90, half a terabyte: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073R](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136073R)

I know its kind of irrelvant because to run vista you need a new PC and new PC's will have large hard disks - (Although my brothers Vista Laptop only has 40Gb of hard disk space so thats a quarter taken up by the OS! - I have 120Gb but thats still 1/12 of my space, Ubuntu takes up 1/40th of my disk space - thats a massive difference)

But I was actually wondering why the big difference between two OS's with similar functionality? Is it something to do with that Linux uses shared libraries or something? - But then again I have very little installed on vista...

Anyway... that article was quite interesting - thanks for the link!

---

### Post by x0as on 2007-10-16
If I have to install windows I'll only install xp, default install is only 1.3gb.  I've managed to avoid installing vista so far, if it wants 10gb for a default install I certainty wont be installing it anywhere.

---

### Post by MellonCollie on 2007-10-16
Your pagefile will eat up 1GB-2GB. If hybernation's enabled, hiberfil.sys will be similar in size. System restore can take up a fair amount of space too.

I'm not sure how much space the drivers that come with Vista take up on a clean install, but on my system they're currently chewing up ~1GB.

I personally don't care if it uses 3GB, 7GB, or 12GB, providing it works and it works well (Which it does, for me :)).

---

### Post by igknighted on 2007-10-16
> **Ultra Magnus said:**
> I know its kind of irrelvant because to run vista you need a new PC and new PC's will have large hard disks - (Although my brothers Vista Laptop only has 40Gb of hard disk space so thats a quarter taken up by the OS! - I have 120Gb but thats still 1/12 of my space, Ubuntu takes up 1/40th of my disk space - thats a massive difference)

But I was actually wondering why the big difference between two OS's with similar functionality? Is it something to do with that Linux uses shared libraries or something? - But then again I have very little installed on vista...

Anyway... that article was quite interesting - thanks for the link!

I think a lot of it is sloppy code.  But while this can happen anywhere, in the linux world you see outrage when this happens, but Microsoft has no such voice (after all, no one actually sees the code...).  Also, try compiling the same source code with different compiler settings (-o3 vs. -o2 for example) and look at the size of the binary.  With HD space so cheap, MS might be adding a lot of HD space by compiling bigger binaries, adding some improvement elsewhere hopefully.

See this page for more on compiler optimizations: [http://www.nersc.gov/nusers/resources/software/ibm/opt_options/on.php](http://www.nersc.gov/nusers/resources/software/ibm/opt_options/on.php)

---

### Post by cogadh on 2007-10-16
> **igknighted said:**
> Thats not that _answer_, that is the observation.  The question was why.

Actually, it is an answer. The code for Windows is way more bloated than Linux. As ignighted just said, Windows is full of sloppy code. The Windows programmers only have to worry about making it work, not making it clean. The thousands of people who work on Linux are answerable to their peers for the state of the code and if someone writes something messy, someone else will likely clean it up. That doesn't really happen with Windows.

---

### Post by original_jamingrit on 2007-10-16
If you really need windows, wait untill windows xp service pack 3 comes out (you might be able to get a beta now).  Updating from service pack 2 will really bloat it up.  Plus, sp3 is supposed to have native ogg support, so maybe the majority of computer users will be able to smarten up and stop using mp3s.

All of the updates on my clean install of xp just doubles that size.  One could just reinstall it without autoupdates, and disable as many .dlls as possible.

It sounds like Vista is even worse.

---

### Post by cogadh on 2007-10-16
If never intend to uninstall the updates, you can also remove the leftover update files, which tend to pile up after a while.

---

### Post by hessiess on 2007-10-16
all windows programs are verry big compared to the linux equivalents eg, blender 11 meg, linux vertion. 3ds max 1 dvd, both programs have simaler functinlaty

---

### Post by igknighted on 2007-10-16
> **hessiess said:**
> all windows programs are verry big compared to the linux equivalents eg, blender 11 meg, linux vertion. 3ds max 1 dvd, both programs have simaler functinlaty

Could this be due to linux' use of shared libraries?  Every windows app keeps its libraries itself, while in linux you would download them once... could account for the difference in applications.  As far as the base OS install, I doubt this is the culprit however.

[QUOTE=cogadh]Actually, it is an answer. The code for Windows is way more bloated than Linux. As ignighted just said, Windows is full of sloppy code. The Windows programmers only have to worry about making it work, not making it clean. The thousands of people who work on Linux are answerable to their peers for the state of the code and if someone writes something messy, someone else will likely clean it up. That doesn't really happen with Windows.[/QUOTE]

I sorta just take windows programmers writing bloated, crappy code as the given that we were discussing.  I am more interested in whether the brass at redmond doesn't care, if they have reasons they want it that big (compiler optimizations so stuff runs better, selling more/larger HDs, whatever), or if the coders they have are just not capable of keeping the code manageable (be it due to a lack of overall skill or a lack of enough programmers)

---

### Post by funrider on 2007-10-16
dun get addict to winDOZE, it will kill u

---

### Post by cogadh on 2007-10-16
I really don't think it has anything to do with a lack of skill, I'm sure Microsoft's programmers are quite skilled. I think it has much more to do with the whole closed source mentality. With a big corporate product like Windows, the only oversight is internal and as long as the end product produces the desired results, who cares what it looks like on the inside, the only people who are going to see it work for MS. 

With Linux you have thousands of programmers worldwide looking at code that not only must produce the desired results, but must also be as simple as possible to understand for anyone who want to look at the code. To that end, Linux is constantly being cleaned up and optimized. In the end, the open source products will produce much cleaner, leaner code than the closed source product.

I speak of this out of my own experience in dealing with proprietary closed source software products that were developed by my former employer (not naming names, but it was nobody big). In addition to the software being completely bloated, the programmers themselves were embarrased by the state of the older parts of the code that no one had bothered to get back to and optimize. There was no driving force to do so, since the higher-ups just cared about whether it worked or not. It was the downside to the whole "if it ain't broke, don't fix it" mentality.

---

