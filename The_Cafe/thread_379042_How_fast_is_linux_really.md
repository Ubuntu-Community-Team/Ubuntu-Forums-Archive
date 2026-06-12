---
title: "How fast is linux really?"
date: 2007-03-08
forum: The Cafe
---

### Post by chaosgeisterchen on 2007-03-08
Good morning,

lately I ran into one of the many arguments pro/contra Linux, Windows XP and Mac OS X in the context of the news, that Apple has a rapidly growing market share and becomes more and more popular (Macs make up for 6.8% of the market).

One user, obviously biased towards Windows, brought up some interesting things about the free Kernels Linux and Darwin (which is more or less based on a FreeBSD one (Mach)). He explained, that Linux and Mac OS X are rather slow and unperformant, because of their inferior kernel architecture. I must say, that I have to second his sayings about desktop performance, if it comes to office work, image manipulation and so on. I run KDE on a rather performant machine (C2D E6300, 2048 DDR2-800), but it sometimes seems to slow down to zero, if I want to execute too many tasks simultaneously.

What are your thoughts about this topic? I would like to please you, only to give answers who lack a certain fanboy approach as they seldomly give objective advice.


Thanks for participating
regards

cg

P.S.: [A link concerning the performance of Linux and Darwin. Rather outdated (2.6.6).](http://www.anandtech.com/printarticle.aspx?i=2436)

---

### Post by aysiu on 2007-03-08
I can't imagine Windows or OS X being faster than my IceBuntu...

---

### Post by billdotson on 2007-03-08
I have noticed that Ubuntu can be pretty slow on my Core 2 Duo system which is odd.. when I go to the apps menu sometimes it takes 5 seconds to show the drop down menu.. and I am not running beryl..  any idea why the slowness in this and that my programs take 4-5 seconds to open?

---

### Post by sloggerkhan on 2007-03-08
I think system speed is really dependant on how users run and keep their machines.

Some people have windows boxes that have lag typing in word. My xp install performed similar to my GNOME before I deleted it. xfce and the other lightweight WMs are a little snapier.
But it really seems to vary from comp to comp from what I've seen.

The other thing... The first time I log in, stuff loads way slower than if I log out and log in again.

---

### Post by The Noble on 2007-03-08
Ubuntu is starting with quite a few services, so it may start a little slower than a _base_ XP on a comparable machine. Notice how XP gets slower? Thats because some actual programs are starting to run and are starting to bloat up XP. A fair comparison to XP would be Arch or Gentoo, as they are starting with as little as possible, and will tear any modern operating system a new one in terms of speed in boot and application performance.

---

### Post by DoctorMO on 2007-03-08
The Linux Kernel it's self competes against BSD, Solaris and HP-UX, windows only really competes with it's self; linux has to be good.

As far as architecture goes linux has an amazing structure for being able to handle any number of threads, processors, architectures, busses and device methods and do it very well. the memory management is second to none and I know vista takes advantage of some of the thread management ideas.

Since we don't have access to the windows kernel we don't really have any way to compare. but take it from me that a good kernel is one that when presented with crappy GUI programs that run a million threads and lock up can keep going and still remain usable. did you not read that bloke who used ubuntu for 30 days saying that even though his moview tool had loded 10 instances of the video converter program he could still use the computer and didn't have to restart?

Although saying that some people still have computers that crash, odd.

---

### Post by chaosgeisterchen on 2007-03-08
> **aysiu said:**
> I can't imagine Windows or OS X being faster than my IceBuntu...

Actually, it was said, that Linux is 20 to 30% faster than Darwin. But still slower than WXP. But one can't compare I assume, as Windows is built to offer a system necessarily base upon GUI. Linux goes another way and offers another layer with the X-Server. I assume that the X-Server is the main problem which has to be handled, though. It should be a lot faster.

Does anyone know about the current state of the XEGL approach?

---

### Post by Kateikyoushi on 2007-03-08
To know the limits of linux you have to go all the way and follow the gentoo 150% ricing howto.

I wonder how did he compare linux to windows kernel... hope not with the drop down menu speed test. ;)

---

### Post by chaosgeisterchen on 2007-03-08
> **Kateikyoushi said:**
> I wonder how did he compare linux to windows kernel... hope not with the drop down menu speed test. ;)

It emphasizes on empricism and I have to admit: I second it in some way, but not 100%.

---

### Post by watson540 on 2007-03-08
faster than a speeding bullet?
do i win something?

---

### Post by Jnifoo on 2007-03-08
Just two things, but we could find others, I'm sure...
- You shouldn't compare the actual Linux Systems with an OS that is not about 6 year old...
Compare MS Vista, MacOS X and Linux Ubuntu 6.x seems ok

- And in fact, what will you compare ? 
An OS that's running a full pack of applications installed since a year or two, or an OS out of the box, with minimal applications installed ?
An OS with just a few conventional applications for the web and the office, or  fully multi media system, or a fully eclectic configuration (web, office, photo, video, dev, etc.)

---

### Post by chaosgeisterchen on 2007-03-08
> **Jnifoo said:**
> - And in fact, what will you compare ? 
An OS that's running a full pack of applications installed since a year or two, or an OS out of the box, with minimal applications installed ?
An OS with just a few conventional applications for the web and the office, or  fully multi media system, or a fully eclectic configuration (web, office, photo, video, dev, etc.)

I want to compare a fully featured system, for sure.

---

### Post by mips on 2007-03-08
> **chaosgeisterchen said:**
> 
What are your thoughts about this topic? I would like to please you, only to give answers who lack a certain fanboy approach as they seldomly give objective advice.


Ubuntu and it's derivatives are slow, period. XP seems much faster to me. On the other hand if you use a different distro like say Gentoo, Sabayon, LFS etc you will find them blistering fast compared to ubuntu and XP. Even Sidux seem fast on my laptop seems very fast.

I suppose it has to do with how much shite is bundled into the distro etc. Bottom line, speed depends on what distro you use and from what I've heard there are some pretty fast ones out there.

---

### Post by chaosgeisterchen on 2007-03-08
> **mips said:**
> Ubuntu and it's derivatives are slow, period. XP seems much faster to me. On the other hand if you use a different distro like say Gentoo, Sabayon, LFS etc you will find them blistering fast compared to ubuntu and XP. Even Sidux seem fast on my laptop seems very fast.

I suppose it has to do with how much shite is bundled into the distro etc. Bottom line, speed depends on what distro you use and from what I've heard there are some pretty fast ones out there.

Where do you put ArchLinux, which I use at home?

---

### Post by yaztromo on 2007-03-08
Windows is built from the ground up to have a lightning fast GUI, it also has (XP and vista) intelligent application pre-fetching routines that speed up app launch time considerably over linux (try comparing the loading times of firefox and OO in windows to linux). So as a desktop machine, windows does feel a tad snappier to me.

From what I read and hear from other people is that the real bottle neck for linux lies in the Xserver, which was never really designed for the demands we place on it today.

Having said that I think the gap is closing. Running a KDE desktop now with compositing enabled gives very fast rendering speed to me, and app launch time (especially with QT apps) is getting rather fast.

What would make things feel really snappy is a preloader for firefox and OO :)

---

### Post by chaosgeisterchen on 2007-03-08
What about re-building Linux for adapting to the newly created desktop needs?

X shouldn't be a layer, more a part of the kernel.

---

### Post by Tomosaur on 2007-03-08
It depends on how you use your machine - what your hardware is like, etc etc etc. There's no single answer. For me, Ubuntu runs like a cheetah, but Windows (which I dual boot) is much, much slower.

---

### Post by chaosgeisterchen on 2007-03-08
> **Tomosaur said:**
> It depends on how you use your machine - what your hardware is like, etc etc etc. There's no single answer. For me, Ubuntu runs like a cheetah, but Windows (which I dual boot) is much, much slower.

Hard to compare on a machine that has never ever seen a version of windows in its entire lifetime.

---

### Post by racoq on 2007-03-08
> **chaosgeisterchen said:**
> Actually, it was said, that Linux is 20 to 30% faster than Darwin. But still slower than WXP. 

You have got to be kidding me. If you want to compare windows XP with any of ubuntu derivates, don't compare it with ubuntu with KDE, or even gnome (the more heavier DE), compare it for instance with Xubuntu (which is good looking and it is optimized for performance as windows XP). I have a pentium III 800 mhz with 512 MB RAM running Xubuntu, and it is faster than my brothers pc that is a Pentium IV 3 GHZ with 512 MB RAM on Windows XP.

Know why? Because the Windows XP, that my brother is using, it is all f****d up because of the many applications he installed . What i know is that i keep installing applications in Xbuntu, and it keeps begging me to install more, without killing performance.
And that is what linux architecture has of good, you can install applications and don kill the PCs performance, has Windows apparently does well.

---

### Post by RandomJoe on 2007-03-08
Comparing against a fresh XP install, maybe comparing OOo vs MS Office or just various Linux apps vs _Microsoft_ apps?  Sure, XP will almost surely be faster-feeling.  Microsoft made _sure_ to get the initial feel down, largely by preloading big chunks of key programs.

But start comparing the same apps on both platforms, and this difference starts to degrade.

And the _real_ test to me is, how do both systems compare after 6 months to a year of use?  While Windows is far better than it used to be, I still find it has a noticeable slowdown over time.  The more programs get installed/removed/reconfigured, the worse it gets.  Whereas my Linux installs don't show that same effect.

Not to mention the HUGE performance hit many Windows systems take right off the bat because they are running AV / Firewall software that hogs resources like nothing else...

Besides, I find I can run most Linu distros on far less capable hardware than XP.  Heck, that's how I have gotten most of my systems - people upgraded because the old system was "too slow".  I wipe and reinstall with Linux, it's doing fine.

---

### Post by blueturtl on 2007-03-08
My apologies, I seem to have completely abused the cause of the thread.

---

### Post by Somenoob on 2007-03-08
It's safe for me to say that Ubuntu was faster than Win XP on both my desktop machine and laptop.

---

### Post by mips on 2007-03-08
> **chaosgeisterchen said:**
> Where do you put ArchLinux, which I use at home?

I have not used arch but from what I gather it is one of the fast ones.

---

### Post by fuscia on 2007-03-08
i've only compared booting into openbox on my laptop with booting into xp on my neighbor's dell. they both have the same processor and memory. mine boots in 25 seconds and his in 28 seconds. i shutoff a bunch of stuff on startup on both our machines.

---

### Post by 3rdalbum on 2007-03-08
Linux feels much faster to me, and I'm running Gnome.

HOWEVER, I find that I use multitasking and multithreading much more than most other people. Linux has brilliant multitasking - it's almost superhuman in the way it prioritises intensive programs, yet gives the less intensive ones just enough processing power to work correctly. Windows XP's multitasking is a joke; it's only slightly better than what we had back in Mac OS 8!

If XP feels quicker to you though, remember that it's a 5 year-old operating system version. Your Ubuntu is likely to be the latest version. Try using a distro from 2002 and comparing speed.

---

### Post by JAPrufrock on 2007-03-08
> **RandomJoe said:**
> 

And the _real_ test to me is, how do both systems compare after 6 months to a year of use?  While Windows is far better than it used to be, I still find it has a noticeable slowdown over time.  The more programs get installed/removed/reconfigured, the worse it gets.  Whereas my Linux installs don't show that same effect.

Is XP slowdown caused by frequent program installation/removal, or by virus infection, spyware, malware, etc., or a combination of the two??  I often wondered why my XP slowed down so much over time.

Also, I agree with others in this thread that Ubuntu, and Linux in general, is much, much better at multi-tasking.  I don't use Windows much now, but I remember having to shut down programs if I wanted to burn a CD, or other resource demanding tasks.  With Ubuntu, I never think about what's running in the background.  For me, Ubuntu is much faster because I never have to re-boot.

---

### Post by yaztromo on 2007-03-08
> **RandomJoe said:**
> Comparing against a fresh XP install, maybe comparing OOo vs MS Office or just various Linux apps vs _Microsoft_ apps?  Sure, XP will almost surely be faster-feeling.  Microsoft made _sure_ to get the initial feel down, largely by preloading big chunks of key programs.

But start comparing the same apps on both platforms, and this difference starts to degrade.

And the _real_ test to me is, how do both systems compare after 6 months to a year of use?  While Windows is far better than it used to be, I still find it has a noticeable slowdown over time.  The more programs get installed/removed/reconfigured, the worse it gets.  Whereas my Linux installs don't show that same effect.

Windows also preloads large chunk of non-microsoft programs at boot. It uses system idle time to organise the next boot to do this. It also keeps (like linux does but better) large chunks of these programs in memory after they are terminated. Even after six months of Windows (I've got an XP install that goes back years and is still lightning fast) use I still find it much quicker to load software (like OO and firefox) than Linux does. Linux does just not have the intelligent prefetching capabilities of windows and it's a big contributary factor to why Linux is slower as a desktop machine.

I don't buy the idea that installing programs in Windows slows the whole thing down. It's never happened to me, and it's therefore no surprise that registry cleaners and uninstalling programs has no effect on system speed.

> c) Windows gets you high on speed by starting up fast, but it doesn't stay that way. Windows (yes even XP) has to be rebooted to regain the best performance. On Ubuntu I find that things will run just as peppy throughout the day no matter what I have used the system for earlier.

My work XP machine hasn't been rebooted in months. It's still just as fast as the day it was booted. Windows 98 suffered from these kind of problems, unfortunately their legacy has left a stigma which is unfounded in XP and Vista.

> HOWEVER, I find that I use multitasking and multithreading much more than most other people. Linux has brilliant multitasking - it's almost superhuman in the way it prioritises intensive programs, yet gives the less intensive ones just enough processing power to work correctly.

The other day I was uploading some files via FTP to my ubuntu machine. The whole desktop slowed to a crawl. Opening any app including just the menu took ages. I never get bad priority handling like this in XP.

---

### Post by racoq on 2007-03-10
> **yaztromo said:**
> Windows also preloads large chunk of non-microsoft programs at boot. It uses system idle time to organise the next boot to do this. It also keeps (like linux does but better) large chunks of these programs in memory after they are terminated. Even after six months of Windows (I've got an XP install that goes back years and is still lightning fast) use I still find it much quicker to load software (like OO and firefox) than Linux does. Linux does just not have the intelligent prefetching capabilities of windows and it's a big contributary factor to why Linux is slower as a desktop machine.

I don't buy the idea that installing programs in Windows slows the whole thing down. It's never happened to me, and it's therefore no surprise that registry cleaners and uninstalling programs has no effect on system speed.



My work XP machine hasn't been rebooted in months. It's still just as fast as the day it was booted. Windows 98 suffered from these kind of problems, unfortunately their legacy has left a stigma which is unfounded in XP and Vista.



The other day I was uploading some files via FTP to my ubuntu machine. The whole desktop slowed to a crawl. Opening any app including just the menu took ages. I never get bad priority handling like this in XP.


What is this, a club of support to Windows XP? Do some of you guys read your own posts before submitting?  We cant compare speed of both systems, dont you understand that? The systems are as fast as their users made them fast. Everybody knows linux is more "tweak friendly than Windows", so in that point u cant compare ubuntu with windows. As far as i can tell , from my experience, any default installation of ubuntu is faster than windows XP. So i dont get it were some people got those ideas that windows xp is faster than ubuntu. That is really not true.

---

### Post by WalmartSniperLX on 2007-03-10
Lets see. All I can say is that it depends on the distro. Some distros pack up a lot of software that may run slower than others. Distros like Gentoo that rely on you compiling everything for your architecture are blazing fast, and Gentoo in general is light weight. However get this:

I pinged my friend on MS windows XP with 800 byte packets on average of 300 m/s (actually I dont remember it was a little higher)

In linux I did the same with 800 byte packets, same exact test, and averaged 190 m/s (again dont remember the exact number but I know it was just within +/- 5 of 190)

The network performance for one is much better in Linux, unless I screwed something up but I very highly doubt that I did. :)


LOL but because of my ati x1600pro and ati's shitty linux support with their drivers, its always falling back on the cpu, which is VERY intense for my AMD Sempron64 3100+ :P

EDIT: But running fluxbox does make up for my ati driver problems. I seriously just gained 400 horsepower and 500 pounds of torque.... ok that was lame but you know what I mean.

---

### Post by Polygon on 2007-03-10
we cant really compared windows to linux as windows is closed source, we have no idea what goes on underneath the hood.

windows does boot up faster for me then ubuntu, but what ubuntu lacks in speed of boot up time, it excels in basically everything else.

---

### Post by aretei on 2007-03-10
How about simply reading this though they do not test OSX

[Vista vs XP vs Ubuntu]("http://www.viperlair.com/articles/editorials/vista/versus/")

---

### Post by SouthernGorilla on 2007-03-10
When I switched our antique HP (600MHz, 256k) from Windoze '95 (told ya it was an antique) to Edgy I noticed a huge difference in speed. This may have been largely due to just eliminating years of built-up junk holding back the OS, but it was still a heads-up comparison on the exact same hardware. Even after a few months of adding/removing/updating programs it's still faster than Windoze ever was. Of course, now I have a new computer, so I can't compare the two. And MS will never defile this beauty.

---

### Post by mysticrider92 on 2007-03-10
I have been running Ubuntu on my machine for a while and have always found it fairly quick. I recently put XP MCE on as a dual boot and it ran fast for a while, but after adding about five programs, it started getting slower and slower. You can't really compare certain thing about the two os's though, because after a fresh install, XP will be faster than Ubuntu, until you start adding programs and the registry gets all gunked up. Ubuntu almost never changes its proformance, unless you try to put say KDE on your Pentium 2, which will run XFCE happily. Vista vs. Ubuntu is no contest. Ubuntu will always win that one.

---

### Post by Ric95 on 2007-03-10
I've had a good chance to compare. For desktop menus and windows Ubuntu is only slightly faster than WinXP. But after the binary thrashing my family puts this machine through Ubuntu keeps going at a good speed, but WinXP slows and gets unstable. 
But I use Blender heavily and render times are a great benchmark! 
Here are time comparisons for a common benchmarking test: 
WinXP (32bit)   4:46
Ubuntu(32bit)  4:29
Ubuntu(64bit)  2:23
Gentoo(64bit)  1:44
Puppy linux is the ultimate for window and menu speed!, but I haven't tried Blender with that yet. 
I chose Ubuntu for ease of use. But I have had problems with upgrades!. Often the newer Kernel turns out to be less stable than an older kernel. But at least I get to choose that. :)

---

### Post by racoq on 2007-03-10
> **aretei said:**
> How about simply reading this though they do not test OSX

[Vista vs XP vs Ubuntu]("http://www.viperlair.com/articles/editorials/vista/versus/")

That test is relative and inconclusively
And i really don't care about boot up times. Ubuntu comes with pre-installed applications, try to test windows with all the similar apps that ubuntu comes. And that will be the real test. Even with the windows default installation, i dont find windows XP faster than ubuntu after the boot, and no one here did provide me with real and reliable results.

---

### Post by spockrock on 2007-03-10
if you guys are comparing the kernel then hands down linux is faster than windows and Darwin (Mac OS X)......much faster, and Mac OS X is actually the slowest, but is the snappiest, apps seem to load quicker on OSX then say windows and linux, linux seems slower at this......if thats what you guys are trying to get at.  This is of course to my understanding, that being said, my Ubuntu desktop is just as snappy as my Vista, XP and OS X ...... so I guess I am living the dream.... :\

Also I would like to know how they tested super pi because I have run super pi on the same machine, with XP/Vista and Ubuntu and the Linux kernel smokes Vista and XP, xp and vista run at realtime priority get about ~33 seconds, where as super pi linux does it in about ~27 seconds

---

### Post by billdotson on 2007-03-10
so why exactly do Windows OS seem to slow down over time?  I have heard that you can call it the Windows half-life.  Every few months or so you should reinstall and with each new release of Windows the half-life is longer so you have to reinstall not as often as the last version.

---

### Post by DoctorMO on 2007-03-11
> X shouldn't be a layer, more a part of the kernel.

No, No, No, No, No, No, No,..... PLEASE GOD NO!

The modularity of linux give it the flexibility to take over a lot of different machines from desktops, to wrist watches to super computers and servers no part of the kernel should be so specific!!

The X-Windows system is archaic and mostly due to the projects license and direction over the past few years.

When the windows system breaks in the GUI you have to restart the computer, when Xwindows breaks you just restart xwindows, which part of that is a bad idea? the development is also more directional; why do you think developing and fixing windows costs so much money and time, it's because it's not modular enough. even windows servers run a gui what a waste of clock cycles. why do you think windows doesn't do well on super computers? because it wastes cycles to a gui.

---

### Post by steveneddy on 2007-03-11
> **billdotson said:**
> I have noticed that Ubuntu can be pretty slow on my Core 2 Duo system which is odd.. when I go to the apps menu sometimes it takes 5 seconds to show the drop down menu.. and I am not running beryl..  any idea why the slowness in this and that my programs take 4-5 seconds to open?

I have a dual core machine and mine is so fast that I forgot that I still own an old PIII machine on the desktop that never gets turned on anymore.

I haven't had any problems yet, but I DID experience some slowness in the PIII machine running Dapper. Gimp was ver slow for me and I never got it fixed. 

But 5 seconds for a menu to open? that does sound excessive.

something you might try - install the system monitors in the top gnome bar and see what the processor does when the menu takes a long time to execute. I wonder if the processor is maxxed out and if it is, what process is running that makes it do that. 

I was having problems with XGL before I bought the dual core laptop. 

Sorry, rambling again..... -SE

---

### Post by steveneddy on 2007-03-11
> **billdotson said:**
> so why exactly do Windows OS seem to slow down over time?  I have heard that you can call it the Windows half-life.  Every few months or so you should reinstall and with each new release of Windows the half-life is longer so you have to reinstall not as often as the last version.

I think it's the way that windows allocates the actual hard drive space. It never really deletes and re-writes over anything, so there is a lot of HD searching towards the end and when that HD gets to the last 5%, then it's basically all over.

Not so with Linux.

Can anyone explain this better than I?

---

### Post by 3rdalbum on 2007-03-11
> **DoctorMO said:**
> No, No, No, No, No, No, No,..... PLEASE GOD NO!

The modularity of linux give it the flexibility to take over a lot of different machines from desktops, to wrist watches to super computers and servers no part of the kernel should be so specific!!

Okay then... if we're not making X part of the kernel, can we at least build Gnome into X? :-P

---

### Post by FyreBrand on 2007-03-11
> **chaosgeisterchen said:**
> What about re-building Linux for adapting to the newly created desktop needs?

X shouldn't be a layer, more a part of the kernel.Oh no.  The xserver can definitely stand some improvement but having it separate is what makes it so great.  If I do something and crash X in Linux I have to relogin my session and fire up applications again.  If I lockup the desktop in XP I have to restart and often hard start it.  That's bad and ntfs doesn't deal well with that.

In some functions XP is much faster.  Small application launching, booting (sometimes), and gui operations.  It's hard to quantify fast in a single instance test.  Overall efficiency needs to take into account other time consuming tasks because speed is relative, but efficiency is less so.  The hard drive must be defragmented regularly to keep file access smooth and disk thrashing to a minimum.  Security updates from your security suite must be updated regularly.  While not constant on tasks they still affect the overall efficiency of the system.

The biggest difference I can think of is services.   I have an Apache, MySQL, and PHP stack running almost all of the time in Kubuntu.  This is a development server so it doesn't see traffic but it's still a service running in the background.  I almost never feel the effect of this.  The service run pretty fast on my machine.  On the XP partition I have IIS installed with MySQL and PHP.  It's so very slow to respond and I can feel the resource load.  In comparison I just don't feel the development resource load in Kubuntu but definitely feel it in XP.

If I have a heavy resource application running in XP I'm locked into that operation.  The same isn't as true for me in Kubuntu.

If you want fast with eye candy try Sabayon 64 bit.  It's a hell of lot faster than K/Ubuntu.  I didn't think it was quite as stable or as well configured, but wow is it fast.

---

### Post by Mateo on 2007-03-11
for me it's much much faster.  in ubuntu once gnome-panel and the background ar loaded, the PC stops making noise and is done (sometimes it'll start making some noise a few minutes later; that's update-manager running).  In XP the computer continues to act business for another few minutes after the taskbar and everything is already loaded.  in this time the start button is either completely unresponsive or extremely slow.  I get a lot more general "busyness" in windows.  my computer is very rarely giving the blinking busy light in ubuntu.

---

### Post by kinkdxm on 2007-03-11
on a fresh install of xp it would boot up faster than a fresh install of ubuntu for me.
once I did all the updates for xp it would take mins to get from being off to the desktop.
with ubuntu after all the uptades it would take seconds.

---

### Post by ShareBuntu on 2007-03-11
After being a Windows XP user since the day it was released, by initial comparison Ubuntu felt somewhat slower. However, given that one has to defrag, install anti-virus, anti-spyware, bloated firewalls and perform mundane maintenance tasks to keep XP running smoothly the small speed bump encountered with X on Ubuntu really seems insignificant.

Also, comparison between Windows XP and Ubuntu performance after extended periods of running time tells a completely different tale. It is also important to look at how long Windows has been supported as a project at Redmond and the sheer amount of force behind it. Ubuntu is but an infant in the game with nothing near Microsoft's development capabilities, yet we are able to confidently compare the two operating systems - from not only a performance angle. That in itself says a lot about Ubuntu's success.

---

### Post by DoctorMO on 2007-03-11
> Ubuntu is but an infant in the game with nothing near Microsoft's development capabilities, yet we are able to confidently compare the two operating systems - from not only a performance angle. That in itself says a lot about Ubuntu's success.

I'm not sure thats true, not only can open source developers do the _right_ thing technically (instead of messing it up on purpose for some cooperate aim) but there are a lot more developers working more hours for open source projects than for Microsoft in all departments. although perhaps the number of developers in X windows is some what smaller than the number of developers in ole32.

I would also like to add that while X windows system is built to travel over a network, windows gui can't. so every gui request you make can be made over a network too, this is for things like x forwarding (I can load a gui tool from my home machine from work, or from a firends machine on the other side of the world as if it was running there but I see it here) and thin clients. I don't know how much of this functionality slows down Xwindows or how much can be made to go into it's own code that can be switched off for pure desktops in order to speed things up.

---

### Post by yaztromo on 2007-03-11
> **racoq said:**
> What is this, a club of support to Windows XP?

Why is that so wrong on this forum? Have I committed a cardinal sin? Am I not allowed to stick up for Windows if I think it really is faster than Ubuntu?

> 
Do some of you guys read your own posts before submitting?  We cant compare speed of both systems, dont you understand that? The systems are as fast as their users made them fast.

This is only true to a level.

> 
 Everybody knows linux is more "tweak friendly than Windows", so in that point u cant compare ubuntu with windows. As far as i can tell , from my experience, any default installation of ubuntu is faster than windows XP. So i dont get it were some people got those ideas that windows xp is faster than ubuntu. That is really not true.

No it's exactly the opposite.  I find Windows faster for nearly every desktop task, and I gave good technical reasons why this is so. All I see is people arguing for Ubuntu on this thread with very little substance in their posts because they are biased towards Linux.

And just because I think Windows is faster **on the desktop** hasn't prevented me from using Ubuntu. Speed isn't everything.

---

### Post by racoq on 2007-03-11
> **yaztromo said:**
> Why is that so wrong on this forum? Have I committed a cardinal sin? Am I not allowed to stick up for Windows if I think it really is faster than Ubuntu?



This is only true to a level.



No it's exactly the opposite.  I find Windows faster for nearly every desktop task, and I gave good technical reasons why this is so. All I see is people arguing for Ubuntu on this thread with very little substance in their posts because they are biased towards Linux.


This is only true to a level.



No it's exactly the opposite.  I find Windows faster for nearly every desktop task, and I gave good technical reasons why this is so. All I see is people arguing for Ubuntu on this thread with very little substance in their posts because they are biased towards Linux.

And just because I think Windows is faster **on the desktop** hasn't prevented me from using Ubuntu. Speed isn't everything.

You didn't gave me hard facts about it. So i will trust only in my experience. Which DE are u using KDE, even gnome?? Even with gnome (I dont use KDE so cant talk about it) when ubuntu boots up, it is faster in any equivalent applications. If u want to compare optimized DE with windows XP (which you said here is optimized), try using XFCE than post me your results. This will be a more fair test. People cant just say, "Windows XP is faster than Ubuntu", without testing all of the ubuntu family.

---

### Post by Mateo on 2007-03-11
> **'Ace[of]Bytes said:**
> Also, comparison between Windows XP and Ubuntu performance after extended periods of running time tells a completely different tale. It is also important to look at how long Windows has been supported as a project at Redmond and the sheer amount of force behind it. Ubuntu is but an infant in the game with nothing near Microsoft's development capabilities, yet we are able to confidently compare the two operating systems - from not only a performance angle. That in itself says a lot about Ubuntu's success.

That's not true, ubuntu wasn't developed from scratch.  Many of it's components have existed for a long time, longer than windows.

---

### Post by ShareBuntu on 2007-03-13
> **Mateo said:**
> That's not true, ubuntu wasn't developed from scratch.  Many of it's components have existed for a long time, longer than windows.
I agree with the fact that Ubuntu isn't entirely new but it's new to a different breed of consumer. The type of consumer Microsoft has been exposed to for years. In that sense Ubuntu is a first for Linux, which was the point I was trying to broadcast.

---

### Post by eitan_a on 2007-03-23
On my core duo notebook, Ubuntu is very snappy while running beryl and having many windows open.  I stopped using XP on here b.c. the popups were just unbearable and wouldn't allow me to do anything for 5 min after a bootup.  Ubuntu also loads very quickly compared to XP load time.

---

### Post by macogw on 2007-03-23
Mine's always very fast, even with Beryl going at all times.  I have a bootup time of around 20 seconds with Feisty, I think.  The kernels aren't inferior.  The way the kernels are made means that pretty much all the drivers are there so if you move the hard drive to another computer, it'll work just fine (something I love) whereas a Windows hard drive can't be moved between two very different models of computers.

One of my mom's favourite things about using Ubuntu is that her computer is a lot faster than it was when we had Windows.  It might be because you don't have to have a constant AV running.

---

