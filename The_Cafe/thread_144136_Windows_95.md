---
title: "Windows 95"
date: 2006-03-13
forum: The Cafe
---

### Post by IYY on 2006-03-13
A few days ago, I found an ancient computer running Windows 95. I decided to turn it on and remember the good old days. It was pretty much the same as I remembered, but with one main surprise: it was FAST. In every sense of the word.

It booted faster than any modern system (Linux or Windows), programs loaded instantly (even things like the browser, Office 95, file manager), worked quickly and smoothly... Just perfect. All this on a 100 MHz Pentium, with some 32 MB of RAM. A typical machine for the time. These days I see computers with almost 2000 MHz, 512 MB RAM (aren't these the minimum requirements for Vista?) running much slower! 

Here's my question: why can't modern window managers and programs be as fast and simple? Sure, we need to do a bit more these days, but not that much more. Sure, Win 95 crashed a lot, but isn't that due to the system underneath? As a desktop enviorment, it was quite perfect!

I do use Fluxbox and IceWM on some of my machines, but from time to time I do want to edit a document or browse the web, and that's when these huge modern programs that assume every machine is brand new kick in. Besides, Flux and Ice are just window managers, they can't do much.

Just an observation.

---

### Post by ssam on 2006-03-13
have a look round, there are plent of lighter applications. dillo is a very light webbrowser. abiword is faster than openoffice. have a look at the damn small linux default applciations.

dapper will have lots of speed ups over breezy, you could try that.

---

### Post by Teroedni on 2006-03-13
Here's my question: why can't modern window managers and programs be as fast and simple? Sure, we need to do a bit more these days, but not that much more. Sure, Win 95 crashed a lot, _but isn't that due to the system underneath?_
qoute


You mean that most Hardware around the globe was defective?
When it comes to effectiveness
What resolution dos it run on
how many colors;)

You know the Linux kernel by iitself only require 8mb;)

I think if you would run a customized linux system on that system you could atleast do as much as the Win95 could:), if not more:D

---

### Post by glug101 on 2006-03-13
Your computer CAN fly again:)  Check out DSL 
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

The acronym can stand for Damn Small Linux or Dimunitive Sized Linux (depending on company ;) ).  It's the best effort I've seen at what you are asking for.

On a larger scale.... Yes, I agree completely.  While there is a lot more capable with what we have currently on our desktops, it's not enough more to give the bloatware that we've been forced to accept.  The way I see it, computers have been getting faster at such a great pace, that not many people have cared that we are doing things a little faster with machines that are 1000x faster than what we used 10-15 years ago.  It's a serious problem for all OS's, and Linux is certainly not immune. (If you disagree, try running Open Office on a p-133, not happening too quick ;) )

However, there is hope!  The init-ng project will vastely improve the boot up process times, and there are other projects that are focused on digging out the bloat.  But unfortunately, due to negligence, it's a huge job.

---

### Post by IYY on 2006-03-13
> have a look round, there are plent of lighter applications. dillo is a very light webbrowser. abiword is faster than openoffice. have a look at the damn small linux default applciations.

dapper will have lots of speed ups over breezy, you could try that.

I use dillo whenever I can, but it isn't enough for everything. AbiWord loads faster than OO, but I don't really feel a speed diff when running. In fact, scrolling down is often even slower.

> You mean that most Hardware around the globe was defective?
When it comes to effectiveness
What resolution dos it run on
how many colors

No, I mean that the actual operating system was buggy, but not the window manager. Yes, it ran in less colours (same resolution, by the way), but I doubt  it's that important. 

> You know the Linux kernel by iitself only require 8mb

I think if you would run a customized linux system on that system you could atleast do as much as the Win95 could, if not more

I know that Linux itself is almost as light as the DOS system upon which 95 was built, but that's not my point. No user would want to customize their machine to that extent.

Projects like DSL and Ubuntu Lite are good, but aren't quite there in my opinion. 

Besides, what I'm getting at here is not the idea of a minimalist desktop for ancient hardware (though that'd be nice to have too), but a general speedup of all programs, configuration tools, window managers and desktop enviorments.

---

### Post by Teroedni on 2006-03-13
Besides, what I'm getting at here is not the idea of a minimalist desktop for ancient hardware (though that'd be nice to have too), but a general speedup of all programs, configuration tools, window managers and desktop enviorments.
----------------------qoute---------------------------


Yea i can understand what you mean:) 
BUt todays software also need to do more than yesterday. Programming is not simple , and to make it that efective would take too much time. And since most people have fast machines, the time will be better spent on functions and stuff.

Its all a question about Priorities.
Still LInux is going the right way and is getting better at this:)

---

### Post by Kerberos on 2006-03-13
I am fairly sure its due to the newer NT kernel (NT/2K/XP) using protected memory.  Basically each program is assigned an area of memory it can use, but on the 95 kernel (95/98/ME) if a program wants to write to an area of memory outside the boundaries of the current program, it can, which results in the much hated BSOD and a locked system.  On the NT kernel if a program tries to address an area of memory it doesn't have permission to the OS detects this and ends the process 'This program has performed an illegal operation and will be shut down' (but no BSOD - you generally need a bad device driver for that these days).  There is quite a bit of CPU and memory overhead involved though as everything has to be done with API calls rather than any direct memory/hardware access.  The end result is a system that cannot easily be taken out by a badly written program that overwrites a chunk of OS memory but generally has to do more work and use more memory to achieve it.

Well, that and the scadloads of eyecandy, sloppy code and unneccesary background processes that you get certainly don't help with speed too.

---

### Post by towsonu2003 on 2006-03-13
[QUOTE=Teroedni]Here's my question: why can't modern window managers and programs be as fast and simple? [/QUOTE]
I thought about two possible reasons: 
1. modern window managers are made for modern hardware. right now, a modern hardware profile seems to be pentium 4 + 512Mb RAM + 128MB video card. Everything is bloated accordingly. With such hardware, win xp will work fast and flawlessly. see next point for linux performance. 
2. drivers in linux... bc manufacturers are too stupid to write correct (bug-free) drivers for the hardware we use in linux, and bc open source driver writers can't get their hands onto specific-enough hardware specifications, we basically use the hardware below its optimum performance. so modern linux window managers look like they are slow, but they are fast when you got all the drivers correctly (especially video drivers)... 

From what I see with my experience in win xp (all drivers from manufacturers) and ubuntu 5.10 (no drivers from manufacturers), ubuntu is slower than win xp. win xp is slower than ubuntu if you don't get the manufacturer drivers and stay with win xp provided drivers. if i had the correctly written drivers, it looks to me like ubuntu would be faster. 

There are also distros that are put toghether for older hardware, so they can be used for getting better performance in systems where drivers are poorly written. there are also distros (gentoo as the primary and maybe the only?? one) that focuses on getting as much as you can from your system, by compiling everthing from source according to your unique system specifications (that you have to know obviously). 

One more thing, it seems that bleeding-edge distros (suse, fedora, ubuntu) have buggy software (and software in beta etc), so that may be having a bad effect. I expect (and will try sooner or later) distros like Debian that aim for stability above all will provide better performance. 

sorry for the rant.

---

### Post by glug101 on 2006-03-13
Rants are what the community chat area is for ;)

I agree with IYY's idea that modern software should be more efficient than it is.  And if I pick on linux more than others in that respect, it's because I know that my bi#ching might actually get something done about it;) (unlike with windows)  I will point out that OS 10.4 works unbelievably well for all basic tasks on my PowerMac G3 (circa 1999).  Of course, Apple has advantages that Linux developers can only dream of (limited amount of hardware to support, lot's of development money, and the Steve Jobs factor that demands perfection from EVERYTHING!), but I like to think of OS 10.4 as an example of Linux COULD be.  

I'd like to see an improvement along the lines of what was done with Nautilus between version 1.4 and 2.0.  That single piece of software went from unusable, to damn fantastic on my p133 laptop.  At the time, running that and the Enlightenment desktop, that computer looked way better than Windows, and ran much better too. (Windows 2000 would have been too much for my poor little harddrive and 48 meg o ram)

---

### Post by Virogenesis on 2006-03-13
[QUOTE=IYY]
Here's my question: why can't modern window managers and programs be as fast and simple? Sure, we need to do a bit more these days, but not that much more. Sure, Win 95 crashed a lot, but isn't that due to the system underneath? As a desktop enviorment, it was quite perfect!
[/QUOTE]
Heres my answer..... e17, its not out sure but its a interesting project

---

### Post by Jimmy_r on 2006-03-15
Hm, i said something similar a while ago: [http://www.ubuntuforums.org/showthread.php?t=113890](http://www.ubuntuforums.org/showthread.php?t=113890)

I timed my computers again, this time with a boot-tuned(mdmadm-raid, lvm,  evms and such disabled) 64-bit dapper drake.

The 200 MHz pentium MMX with 32MB ram took 40 secs from power on to fully started win 95.

The 1800MHz AMD Athlon64 with 1 Gig ram took 50 secs with Dapper, but
POST took 18 secs on the pentium and 5 secs on the Athlon, so we could say that

win 95 booted in 28 secs while ubuntu booted in 45 secs.
And Ubuntu took 16 secs to shut down, win 95 took 3 secs.

I am very curious to what is causing this, i mean, of course it is more advanced software now but it is also way more advanced hardware.

And i built a LFS system a while ago, i do not remember that it was much faster, even before i installed the xserver i belive it would have been defeated in boot time by win 95.

It just puzzles me. What in the world is taking the time? :-k 
Ok, i have bootcharts and such so I know what is taking the time, but still...

---

### Post by Kerberos on 2006-03-15
Ubuntu always took in excess of 5 minutes to boot on my x64 3400+ / 1gb laptop.  I dont reckon I should have to learn to hand tune my boot sequence (as people suggested) just to get it to boot in a reasonable amount of time.  Fast boot times = important in my opinion. :(

---

### Post by PatrickMay16 on 2006-03-15
I understand what the original poster means. It seems like things are getting more and more bloated every day. And the requirements go up with each new version of Windows. Compare 2000 to XP, and then XP to vista.

Here are the programs I use on slower machines:
xvt
dillo
icewm
ROX filer
XMMS
nano

For things like word processing, though, I have no idea what light alternatives would be. I think development teams for project like openoffice, GNOME, KDE, and such should focus on reducing memory and CPU usage, and overall increasing speed and performance. 

I recently tried Ubuntu Breezy on an OEM machine I bought in 2001. It was almost unusably slow on it! Woud!!! I couldn't believe it.

---

### Post by jdodson on 2006-03-15
OK, well first off, you are right, Windows 95 is hella fast.  But, seriously, you are really comparing apples to oranges.

Use Windows 95 for a month as your primary OS.  Seriously, do it.  I think you will find really soon why you don't use it anymore.  And its not because Microsoft doesnt support it, its because there is a reason you moved on and its not because you wanted to slow your computer down.

First off, Windows 95 allows things operating systems should not.  It does not provide "padding" for hardware access as OS's should.  Basically, instead of accessing a more fault tolerant API, you can access the hardware more directly.  This is great for speed, but bad when your hardware or driver code sucks.  I guess people could write better code, but they dont and blue screens of death happen often.

Windows 95 is not a true 32 bit OS.  Fat32 is not a true 32 bit filesystem.  Fat32 suffers from EXTREME limitations with file size and file number.  Plus, try formatting a large volume > 200G in Windows 95, it wont happen, you will not be able to use the whole drive.  Plus Windows 95/98 limit your ram size as well, check this out but last time I checked it was something lesser than a true 32 bit OS would allow.

Windows 95 lacks many niceties of a modern OS, for instance out of the box usb/firewire support.  You can get this as a download from Microsoft, but it did not come standard.

There are tons of other reasons why Windows 95 is not totally usuable anymore as a more moden desktop.  I could keep listing them, but I wont, I think you get the idea.

I could also point out that MANY apps dont run on 95 anymore and require 98, but most free software still runs ok.

There is also the the whole issue of programmer time.  Would you rather have, A) Blazing Fast Programs or B) Feature rich programs?  I am not saying that feature rich programs come at an expense in speed, but at times they do.  If you want free software program X delevered ASAP then a programmer should use a language that is quicker to develop in such as Python or C#, etc.  Programming in C will give much more speed, but whats more important?  I would argue programmer time and the ability for others to add on to the code in a language that has a lesser entry level to learn.

Feel free to use something like Damn Small Linux to achieve quick speed.  But you might notice why Gnome is quite a bit slower.  It is a feature rich Desktop, its not a peared down Window Manager.  I am not knocking Fluxbox here, I am just saying its built for speed not "just works" feature-rich-ality.

Plus, last time I checked Dillo did not support CSS.  Ummm, hmm well it is faster than hell, no arguement but CSS is pretty critical nowdays.

My Ubuntu setups use the Ext3 filesystem.  Fat32 might actually be a faster filesystem because Ext3 writes twice to ensure file integrity, but what would I rather have?  A faster filesystem that does not ensure file integrity?  Or a perhaps-slower filesystem that esures data integrity?  I would pick option two(assuming Ext3 is a bit slower, I am not saying it is, but it does write more times than Fat32).  Ext3 might even take up more space with an increased overhead than Fat32, I think that is acceptable to for ensured integrity.

Same goes for the Linux kernel vs. a Windows 95 kernel.  Seriously, the Linux kernel kicks Win 95's *** for features, stability, etc.  Would I trade that for a quicker 95-junk kernel?  Nope.  Perhaps one could go to a 2.4.X kernel, but I am not so sure they are much faster than 2.6.X anymore.

Gnome has been making many inroads to speed improvements, seen in dapper for an example.  I am not saying they cant make things faster, but I do understand why they are at times slower and it is acceptable to me that they are.  Not that they cant improve, but that to me, it is passable.  

Sometimes though, programmers use bad algorithms that are not well thought out.  As many developers add to a project the chance that bad algorithms are used is increased.  So I don't want people to think that speed improvements are outside the control of programming folk, they are at times.

Anyways, rock on.

---

### Post by Jimmy_r on 2006-03-16
Me thinks they should write everything in assembly... Imagine teh speed :p

No, but seriously. I hope that future versions of ubuntu will have some kind of smart installer:

Standard options:
I will install(based on hardware detection):
linux-amd64-k8 (Without bluetooth support, Without raid-support)
nvidia-glx
...
Go to "Expert menu" to change

Expert options:
Will you ever use bluetooth? No? Ok, then we wont install support for that...
Will you ever use raid? You dont know what it is? Then you probably dont have it. Still want to install support for it? Ok.
You have an amd athlon 64 system. The recommended kernel package is: linux-amd64-k8. You want to install that? Ok.
Installing kernel: Without bluetooth support, With raid-support

You have a Nvidia EN6600gt Graphics card. Recommended drivers are nv and nvidia-glx. Which one do you want to use? nvidia-glx? ok.
...

Then we would not need it to detect hardware at every single boot, and have fewer kernel modules to load.
Perhaps with a boot-option: detect_new_hardware which runs the detection-program again. Something like that would be nice.

---

### Post by leon-1 on 2006-03-16
When you load windows 95 you get the basest system possible, there are no advanced drivers for any of your computer components and they require to be loaded from disc (actually pretty much like any windows system), the hardware choices and architecture back then were considerably smaller and the drivers were both smaller and less complicated.

I loaded windows 95 onto a laptop about 2 months ago, the reason being is that the laptop did not have enough memory to support windows 98, it is for some friends youngsters to do thier homework on. I can honestly say that yes it was the fastest system that I had in the house. All in all the OS took up a little over 100mb with everything there, with the drivers loaded for the different components it was something along the lines of 113mb.

If your system has a hard drive searching through 113mb of OS to do something it is bound to find it faster than searching through 2.1Gb of information, add to that the size of the drivers that we have now (30mb and greater for soundcards and graphics cards ) and it won't take long to equal and surpass the complete size of the win95 OS. These drivers though provide much better support for a far greater and widespread amount of hardware and hardware manufacturers.

If you could tell someone the exact architecture of your machine down to the component part (I am not talking cards I am talking specific chip), then someone with the correct level of programming knowledge could provide you with drivers specific to your machine it would work like lightning. The chances are slim that it would ever happen.

As the greater amount of hardware is supported the larger the drivers get and to a degree they slow down a little. On each driver this means little, but when you put them all toghether it starts to add up, you will also notice slightly longer seek times for the hard drive as it has to find a needle in a haystack for specific items.

No things haven't slowed down, they have advanced to do more and support more unfortunately what we see is an apparent difference in speed because we do not get to see all the things going on in the background.

If architecture was standardised speed would be a result, however the chances of this are along the lines of me winning the national lottery rollover three times in a row whilst taking concorde for a spin over the Bermuda triangle;)

---

