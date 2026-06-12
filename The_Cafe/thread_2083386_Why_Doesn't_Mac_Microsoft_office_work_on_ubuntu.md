---
title: "Why Doesn't Mac Microsoft office work on ubuntu?"
date: 2012-11-12
forum: The Cafe
---

### Post by john1923 on 2012-11-12
Both OSX and Ubuntu are *NIX systems. Normally (in my limited experience) if a program works on one *NIX system, then it can be made to work on ubuntu. 

Is Microsoft making it difficult on purpose?

---

### Post by Grenage on 2012-11-12
Moving goalposts, and no single point of communication are undoubtedly just two of the reasons.  Throw in a comparatively tiny user base, and it's all rather reasonable.

---

### Post by Elfy on 2012-11-12
Not support.

*Thread moved to **The Community Cafe**.*

---

### Post by dannyboy79 on 2012-11-12
> **john1923 said:**
> Both OSX and Ubuntu are *NIX systems. Normally (in my limited experience) if a program works on one *NIX system, then it can be made to work on ubuntu. 

Is Microsoft making it difficult on purpose?
The same reason programs compiled to run on RedHat may not run in Ubuntu. It's just compatability issues of libraries and such.

Ubuntu is based on Debian, OS X to the best of my knowledge is based on a custom form of BSD.

---

### Post by mips on 2012-11-12
> **john1923 said:**
> Both OSX and Ubuntu are *NIX systems. Normally (in my limited experience) if a program works on one *NIX system, then it can be made to work on ubuntu. 

Is Microsoft making it difficult on purpose?

I suspect the issue is more related to the graphical window environment & APIs as OS X does not use X by default.

[http://en.wikipedia.org/wiki/Cocoa_(API](http://en.wikipedia.org/wiki/Cocoa_(API))

---

### Post by Lars Noodén on 2012-11-12
You can read more about Aqua and [Quartz](http://oreilly.com/pub/a/mac/2005/10/11/what-is-quartz.html) if you are interested, but one of the main reasons as already mentioned is that OS X apps are not X-based.  There is X available for OS X, so it is possible to run a great many Linux or BSD apps on OS X, but the reverse is not possible.

Then of course there is also the great history of hostility the MS has continually shown rivals, especially the FOSS community.  MS Office is one of the two cash cows that it depends on and that helps tie users to MS Windows, so it is not about to let that slip.  Though interestingly there are rumors of MS Office for Android.  So if Android is possible, then Ubuntu should also be possible.

---

### Post by MisterGaribaldi on 2012-11-12
@OP: There is no Mac OS X "compatibility layer" for Linux (or anything else) like there is Wine/Crossover Office for Mac OS X and Linux. Therefore, you cannot run Mac OS X compiled binaries anywhere else. In theory, one could run various scripts used in Mac OS X, but other than bash-type scripts, someone would have to implement AppleScript for Linux, and I seriously don't see that happening any time soon.

Microsoft could choose to write (port, really) Office to Linux. However, the post above about possibly a port for Android notwithstanding, I seriously doubt Microsoft will ever port Office to any other platform.

The only reason there's a Mac OS X version in the first place is because of a special, long-standing relationship that Microsoft has had with Apple for nigh unto 30+ years. If Microsoft and Apple hadn't had that, there would be no MS Office for anything *but* Windows.

---

### Post by Lars Noodén on 2012-11-12
It turns out that the rumor of Android was only around for a short while.  The post has since been updated with a retraction from higher up:

[http://www.zdnet.com/microsoft-office-coming-to-android-and-apple-devices-in-early-2013-7000005563/](http://www.zdnet.com/microsoft-office-coming-to-android-and-apple-devices-in-early-2013-7000005563/)

MS won't give up their lock on office formats easily, but I'm surprised they're not playing to a platform that has [75% marketshare](http://techcrunch.com/2012/11/02/idc-android-market-share-reached-75-worldwide-in-q3-2012/).  Traditionally they've only ever gained marketshare by leveraging their desktop monopoly but this cannot be done in the smartphone and tablet markets.  

Oh, well.  I find LibreOffice much better anyway and it is already ported to Linux.

---

### Post by mamamia88 on 2012-11-12
Simple answer because Microsoft doesn't want it too.

---

### Post by KiwiNZ on 2012-11-12
If MSFT could see a reasonable return of investment coming from porting Office to Linux they would do it, however given the Linux culture this is not achievable in the foreseeable future.

As for Android, currently MSFT is trying to establish their mobile OS in the market, vital to that would be the ability to view and update MS Office work therefore porting to Android at this point in the Win 8 Mobile lifecycle would be wrong . When or if Win8 mobile gets a reasonable market share a port to Android would be viable.

---

### Post by MisterGaribaldi on 2012-11-12
Microsoft has not given up on Windows Mobile (or whatever it is they're calling it these days) and there's no way they're going to dilute interest in it by making their crown jewels available for a competitor.

---

### Post by forrestcupp on 2012-11-12
I guess it has already been answered, but Mac OS X isn't anything at all like Linux. Not even the kernel is like Linux; it's BSD. You can't even run BSD apps in Linux. But like others have said, the BSD based kernel is only a very small layer of Mac OS X, and it's mainly all the other stuff that makes it incompatible.

On that subject, have you ever noticed that Android actually does use the Linux kernel, and you can't run Android apps in a Linux distribution? That's because everything on top of the kernel is completely different.

---

### Post by szymon_g on 2012-11-12
> **mamamia88 said:**
> Simple answer because Microsoft doesn't want it too.

simple answer- ********.
there is far too many differences between unices and unix-like operating systems to make it possible without major code rewriting and breaking a lot of things that already work.
and nobody would do that for such small user base.
and no, linux does not pose a danger for windows (on desktop)- MacOSX does. despite being years younger, it already has many time more users (not to mention about iOS, used only in products of one producer- Apple).

and to OP- ubuntu (and linux in general) isn't unix, its just a unix-like operating system. MacOSX is a proper unix.

> **forrestcupp said:**
> I guess it has already been answered, but Mac OS X isn't anything at all like Linux. Not even the kernel is like Linux; it's BSD.

no, it's not. quite a lot of *bsd userspace is used in Darwin (the open-source part of MacOSX), but not the kernel.

---

### Post by mamamia88 on 2012-11-12
> **szymon_g said:**
> simple answer- ********.
there is far too many differences between unices and unix-like operating systems to make it possible without major code rewriting and breaking a lot of things that already work.
and nobody would do that for such small user base.
and no, linux does not pose a danger for windows (on desktop)- MacOSX does. despite being years younger, it already has many time more users (not to mention about iOS, used only in products of one producer- Apple).

and to OP- ubuntu (and linux in general) isn't unix, its just a unix-like operating system. MacOSX is a proper unix.



no, it's not. quite a lot of *bsd userspace is used in Darwin (the open-source part of MacOSX), but not the kernel.
true because microsoft intended it to work on osx and wasn't thinking about a linux version at all.  Otherwise they would have developed a linux version

---

### Post by mike acker on 2012-11-12
> **john1923 said:**
> Both OSX and Ubuntu are *NIX systems. Normally (in my limited experience) if a program works on one *NIX system, then it can be made to work on ubuntu. 

Is Microsoft making it difficult on purpose?

why would you want it to?

On Ubuntu your basic package is:

[LIST]
[*]Browser: Firefox
[*]eMail and Calendar: Thunderbird
[*]write/spreadsheet/powerpoint: Libreoffice
[/LIST]
as soon as you go past this point you are into personal selections,-- music, photos, algebra(yeeech)


If the Office Policy calls for MSFT/Office it probably calls for Windows as well and you will have to submit a Statement of Need to get a personal preference app installed.


One should note that the MSFT/Office formats..... are now ISO standards.  Which means any base system -- MSFT, AAPL, Linux -- are all working wit the same format for office documents: .ODT, ,ODS, .eml, etc

---

### Post by mastablasta on 2012-11-13
> **mamamia88 said:**
> true because microsoft intended it to work on osx and wasn't thinking about a linux version at all. Otherwise they would have developed a linux version
 
 
the intended it to work because they had to to avoid some lawsuite they had with apple. as part of settlement they make office for MacOS, not sure what Apple did in return.

---

### Post by GeneralZod on 2012-11-13
See also:

[http://unix.stackexchange.com/questions/3322/what-makes-osx-programs-not-runnable-on-linux](http://unix.stackexchange.com/questions/3322/what-makes-osx-programs-not-runnable-on-linux)

---

### Post by speedwell68 on 2012-11-13
> **forrestcupp said:**
> I guess it has already been answered, but Mac OS X isn't anything at all like Linux. Not even the kernel is like Linux; it's BSD. You can't even run BSD apps in Linux. But like others have said, the BSD based kernel is only a very small layer of Mac OS X, and it's mainly all the other stuff that makes it incompatible.

On that subject, have you ever noticed that Android actually does use the Linux kernel, and you can't run Android apps in a Linux distribution? That's because everything on top of the kernel is completely different.

Bingo, Android/Linux is a completely different animal to GNU/Linux.

---

### Post by forrestcupp on 2012-11-14
> **szymon_g said:**
> 
no, it's not. quite a lot of *bsd userspace is used in Darwin (the open-source part of MacOSX), but not the kernel.

Interesting. I didn't realize that MacOS X uses the XNU kernel, and not the BSD kernel. For XNU, they just took the Mach kernel and incorporated parts of the BSD kernel into it. So that just goes to reinforce my point that MacOS is even less like Linux than I thought.

It's also worth noting that Linux is not a Unix clone, but that it was inspired by Minix. Linux is not even completely POSIX compliant.

---

### Post by mips on 2012-11-14
> **forrestcupp said:**
> 
It's also worth noting that Linux is not a Unix clone, but that it was inspired by Minix. Linux is not even completely POSIX compliant.

[http://en.wikipedia.org/wiki/POSIX#Mostly_POSIX-compliant](http://en.wikipedia.org/wiki/POSIX#Mostly_POSIX-compliant)

OS X is fully posix compliant. Linux & BSD not so much and I suspect linux to be less than BSD but at the same time I also suspect it's a certification thing where those with the money to certify trumps all.

Thing with compliance is you have to pay money for a compliance certificate and you have to do it for every single release you put out there so for open source stuff where money is tight it does not make a whole lot of sense to go down the compliance/certification road.

---

### Post by forrestcupp on 2012-11-14
> **mips said:**
> [http://en.wikipedia.org/wiki/POSIX#Mostly_POSIX-compliant](http://en.wikipedia.org/wiki/POSIX#Mostly_POSIX-compliant)

OS X is fully posix compliant. Linux & BSD not so much and I suspect linux to be less than BSD but at the same time I also suspect it's a certification thing where those with the money to certify trumps all.

Thing with compliance is you have to pay money for a compliance certificate and you have to do it for every single release you put out there so for open source stuff where money is tight it does not make a whole lot of sense to go down the compliance/certification road.
Linux goes by the Linux Standard Base instead. LSB is based mostly on POSIX standards, along with some other open standards, but it extends it.

---

### Post by mr john on 2012-11-14
Office is the number one reason why many companies wont ditch Windows for Linux.

Open Office made some inroads, but most workers prefer Office. Outlook is also by far the most popular email client used in big companies.  The Linux alternatives aren't on par with Outlook because they don't communicate well with Exchange Server which is already in use by most big companies.

I refused to move the desktops in the company I worked at for the last four years to Ubuntu, specifically for these reasons. Linux on the desktop isn't ready for big corporations, mainly because of the lack of Microsoft Office.

---

