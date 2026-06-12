---
title: "Why Isn't Linux Fully MultiProcessor Ready?"
date: 2010-02-10
forum: The Cafe
---

### Post by Ravernomina on 2010-02-10
As the Top Says Its something that bothered me for awhile. Why Linux Cannot Seem to thread a CPU task well. Take OS X for example. If i have 3 apps going my CPU on both cores stay the same, both doing the same amount of work as the other. On Linux One is going crazy and the other one isn't doing much. Why is this, Not trying to seem like a brat or anything, but i never understood that. I mean a Multi-cored CPU should have the kernel, drivers, libraries, and Extensions all multi-Core Ready. Some one Explain... Express your opinion.

---

### Post by Rhubarb on 2010-02-10
It really depends what workload you're giving it.
For instance, if you're doing a lot of heavy stuff in firefox, it'll only consume 1 core, because firefox is simply not coded (yet) to support multiple cores.

There are many many apps that'll only work on the 1 core, while there are only a few that support multiple cores.

Some multi-core supporting apps:
make - by default compiling only uses 1 core, but if you use the -j2 option it'll compile with 2 cores.
x264 - great codec for encoding videos, and supports 1 or many cores which you have to specify to get the performance boost.

Some apps just aren't well suited for multicore use.

Another thing that is noteworthy, is that apple has recently released [Grand Central Dispatch]("http://en.wikipedia.org/wiki/Grand_Central_Dispatch") as open source, so it's now possible to integrate this into Linux systems as well.

On a related note, Linux is used for many of the world's top super computers, where they have thousands of CPUs - but these systems run customised applications on a customised linux distro.

To sum up, if you run the same applications on your Mac as you do in Ubuntu, there really shouldn't be that much of a difference in CPU work loads.

---

### Post by Ravernomina on 2010-02-10
> **Rhubarb said:**
> It really depends what workload you're giving it.
For instance, if you're doing a lot of heavy stuff in firefox, it'll only consume 1 core, because firefox is simply not coded (yet) to support multiple cores.

There are many many apps that'll only work on the 1 core, while there are only a few that support multiple cores.

Some multi-core supporting apps:
make - by default compiling only uses 1 core, but if you use the -j2 option it'll compile with 2 cores.
x264 - great codec for encoding videos, and supports 1 or many cores which you have to specify to get the performance boost.

Some apps just aren't well suited for multicore use.

Another thing that is noteworthy, is that apple has recently released [Grand Central Dispatch]("http://en.wikipedia.org/wiki/Grand_Central_Dispatch") as open source, so it's now possible to integrate this into Linux systems as well.

On a related note, Linux is used for many of the world's top super computers, where they have thousands of CPUs - but these systems run customised applications on a customised linux distro.

To sum up, if you run the same applications on your Mac as you do in Ubuntu, there really shouldn't be that much of a difference in CPU work loads.

But there is... My OS X is Handling Apps better then Linux.... and thats saying something

---

### Post by 3rdalbum on 2010-02-10
> **Ravernomina said:**
> But there is... My OS X is Handling Apps better then Linux.... and thats saying something

Maybe the difference is that Mac OS X is running less efficiently than Linux, and so it's putting heavy load into three cores to perform the same work accomplished by one core on Linux.

Programs must be specifically written to split their work across multiple threads, and therefore across multiple cores. Either you can use these specially-written programs, or you can run multiple intensive programs at the same time.

Some programs use a hybrid approach - for instance, an MP3 encoder algorithm can only use one thread at a time, and some video encoder algorithms are the same. Some programs like SoundConverter and Blacklight will encode multiple files simultaneously, and each file's encoding job will automatically be assigned to a different core.

---

### Post by Ravernomina on 2010-02-10
> **3rdalbum said:**
> Maybe the difference is that Mac OS X is running less efficiently than Linux, and so it's putting heavy load into three cores to perform the same work accomplished by one core on Linux.

Programs must be specifically written to split their work across multiple threads, and therefore across multiple cores. Either you can use these specially-written programs, or you can run multiple intensive programs at the same time.

Some programs use a hybrid approach - for instance, an MP3 encoder algorithm can only use one thread at a time, and some video encoder algorithms are the same. Some programs like SoundConverter and Blacklight will encode multiple files simultaneously, and each file's encoding job will automatically be assigned to a different core.

Um not not really.... im running WOW, and flash and their both using my CPU at 25% each... on Linux It runs 100%

---

### Post by murderslastcrow on 2010-02-10
On the same computer?

---

### Post by Ravernomina on 2010-02-10
> **murderslastcrow said:**
> On the same computer?

Yes

---

### Post by Psumi on 2010-02-10
Is your processors by any chance lower than or equal to 2 GHz?

If so, then that's your problem. Flash takes up a CONSIDERABLE amount of CPU in linux (in comparison to Windows), and the recommended spec from adobe (not minimum) is 2 GHz for one core, doing nothing else but flash. (as well as 64 MB of Video Memory.)

---

### Post by szymon_g on 2010-02-10
> **Psumi said:**
> If so, then that's your problem. Flash takes up a CONSIDERABLE amount of CPU in linux (in comparison to Windows), and the recommended spec from adobe (not minimum) is 2 GHz for one core, doing nothing else but flash. (as well as 64 MB of Video Memory.)

lol. and people say that linux is better for older computers

but ad rem: linux is multiprocessor ready from it's beginning- but, saying that, i mean some usefull programs, like databases, webservers, mailservers etc- not a typical desktop applications

---

### Post by markp1989 on 2010-02-10
> **szymon_g said:**
> lol. and people say that linux is better for older computers


flash isnt the linux devs responsibility, adobe really need to pull there finger out and sort it out, its been bad as long as i remember

---

### Post by NightwishFan on 2010-02-10
I have always found Linux to behave exactly as expected on multicore processors. Is Linux "actually" less efficient or is it just reading like it.

---

### Post by Grenage on 2010-02-10
I'm slightly confused, why would it be less efficient for an application to use one core rather than two?  Surely it depends on what it's doing?

Also, considering you're running WOW on Linux, I presume you're running on wine; does that factor in?

---

### Post by koshatnik on 2010-02-10
Wow people put the stupid stick away for 5 minutes.

How are linux devs responsible for the apps written for the platform? If the app devs write processor heavy, RAM sucking apps, how is that linux's fault exactly? 

Linux is an afterthought for most commercial devs, so there will always be issues. Adobe is a prime example of this. You really think that if flash was open source it would run like that on linux?

---

### Post by cartman640 on 2010-02-10
Try compare with software that is available natively to both OS's, as has been pointed out flash is quite intensive under Linux, as is WOW through Wine (or which ever solution you're using) compared to the native MacOS version.

As for Linux being multi-cpu ready, it most certainly is, a good example I was reading about the other day is Weta Digital's render farm they used to render Avatar, it's 39,000 cores and runs on Ubuntu :D

---

### Post by benmoran on 2010-02-10
As others have already pointed out, Flash and Wow aren't indicative at all of the Linux Kernels ability to utilise cores. Flash because it's a mess, and Wow because it's running through Wine. I don't think Wine is really optimised for more than one core at this point.

---

### Post by Psumi on 2010-02-10
> **benmoran said:**
> As others have already pointed out, Flash and Wow aren't indicative at all of the Linux Kernels ability to utilise cores. Flash because it's a mess, and Wow because it's running through Wine. I don't think Wine is really optimised for more than one core at this point.

Also, there is no 64-bit wine (fully implemented, yet). It may seem like you're installing 64-bit wine when you use that apt-get command, but you're not.

---

### Post by ElSlunko on 2010-02-10
Flash & Wine are bad examples to use as a representation of what Linux can do. Bibble 5 rips my processors in the manner that satisfies me :D. Although Bibble isn't 64bit :\

[[img]http://www.ubuntu-pics.de/thumb/41935/desk_1_002_ZcayeQ.jpg[/img]](http://www.ubuntu-pics.de/bild/41935/desk_1_002_ZcayeQ.jpg)

---

### Post by MaxIBoy on 2010-02-10
> **Ravernomina said:**
> As the Top Says Its something that bothered me for awhile. Why Linux Cannot Seem to thread a CPU task well. Take OS X for example. If i have 3 apps going my CPU on both cores stay the same, both doing the same amount of work as the other. On Linux One is going crazy and the other one isn't doing much. Why is this, Not trying to seem like a brat or anything, but i never understood that. I mean a Multi-cored CPU should have the kernel, drivers, libraries, and Extensions all multi-Core Ready. Some one Explain... Express your opinion.
Rubbish. 

Linux is *too* multiprocessor-oriented. It tends to be optimized for servers and supercomputers with hundreds or thousands of CPUs, leading to problems like this:
[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]


If you want to optimize your kernel for desktop (as apposed to server) performance, you will want a "realtime" kernel. You can compile your own, or you can get one from somewhere. A pretty easy way for beginners to get one is to install the realtime kernel from Ubuntu Studio. Ubuntu Studio is compatible with Ubuntu, you can just add their repositories and then install the kernel from it without breaking anything.

If you feel like compiling a kernel, ou can also compile a kernel with the [BFS patch](http://ck.kolivas.org/patches/bfs/bfs-faq.txt), which can improve performance on desktop machines with 1-16 CPUs.

---

### Post by mickie.kext on 2010-02-10
> **Ravernomina said:**
> Um not not really.... im running WOW, and flash and their both using my CPU at 25% each... on Linux It runs 100%
I assume that you are running World of Warcraft in WINE so that is your problem. Wine is not multi-threaded.

PS, also flash is crap, Adobe hates linux.

---

### Post by MaxIBoy on 2010-02-10
> **mickie.kext said:**
> I assume that you are running World of Warcraft in WINE so that is your problem. Wine is not multi-threaded.

PS, also flash is crap, Adobe hates linux.
This.

You won't get good performance out of Windows software or cheesy token ports. End of story.

---

### Post by cb951303 on 2010-02-10
> **maxiboy said:**
> this.

You won't get good performance out of windows software or cheesy token ports. End of story.

+1

---

### Post by PhoHammer on 2010-02-10
> **Ravernomina said:**
> But there is... My OS X is Handling Apps better then Linux.... and thats saying something
I beg to differ. Running Chrome and Gimp, Ubuntu 9.04 vs Mac OS X 10.6.2 (on the same hardware), Linux is more responsive and completes tasks in Gimp faster. In my experience.

---

### Post by hessiess on 2010-02-10
It depends how the application was coded, almost all applications are single threaded, which means they cannot use more than one core. Rewriting programs, and even designing new ones to use multiple threads is non trivial.

---

### Post by The Real Dave on 2010-02-10
> **szymon_g said:**
> lol. and people say that linux is better for older computers


Try getting a fresh, usable, survivable, up to date Windows install on a PII with 64Mb of RAM. Linux rocks for older computers. You just gotta realise that its not going to be the same as in Windows. You wouldn't run Office 07 on something with 128MB RAM running W2K ;)

---

### Post by The Real Dave on 2010-02-10
> **ElSlunko said:**
> Flash & Wine are bad examples to use as a representation of what Linux can do. Bibble 5 rips my processors in the manner that satisfies me :D. Although Bibble isn't 64bit :\

</snip>]

Man, I want you computer....so bad :) But why in God's name have you 34Gb of swap? :o

---

### Post by Iksf on 2010-07-10
WoW and wine apps all run on one core under Linux. WoW will only use 2, more one and a half, on Mac or Windows anyway. I would love to see some way to resolve this but atm wine cant run programs as efficiantly as Windows

---

### Post by earthpigg on 2010-07-10
on Ubuntu 10.04, i7 quad, 6gb RAM, GTS250 1gb Video card, and only native software:

-world of goo causes one core to spike when started, then settles down to occasional single-core spikes

-defcon uses 90-100% of one core the entire time it is running

-osmos uses 90-100% of one core the entire time it is running

-urban terror uses 70-100% of one core the entire time it is running

These are four very well known Linux games. Any top ten list would include at least two or three of these.

They all run very well, but all the computing being only done on one CPU means my fans are forced to go batcrap crazy to keep that one CPU at or below 75°C. 

One possible haphazard solution would be to simply switch which single core is being used every 10 minutes or so.

This is with all games being run in windowed mode, using htop and lm-sensors to collect the data.

also worth noting: 
-World of Goo was created for Win/Wii/Mac then ported to Linux as an afterthought. 
-I think DEFCON was intended to have a Linux release from the start.
-Osmos, same as Goo, afterthought.
-Quake was created for Windows, then ported to Linux after being open sourced - Urban Terror was built on this foundation.

This doesn't tell us what the problem is, but it tells us what the problem isn't: it is ***not*** a WINE problem.

---

### Post by Redo on 2010-07-10
> **earthpigg said:**
> on Ubuntu 10.04, i7 quad, 6gb RAM, GTS250 1gb Video card, and only native software:

-world of goo causes one core to spike when started, then settles down to occasional single-core spikes

-defcon uses 90-100% of one core the entire time it is running

-osmos uses 90-100% of one core the entire time it is running

-urban terror uses 70-100% of one core the entire time it is running

These are four very well known Linux games. Any top ten list would include at least two or three of these.

They all run very well, but all the computing being only done on one CPU means my fans are forced to go batcrap crazy to keep that one CPU at or below 75°C. 

One possible haphazard solution would be to simply switch which single core is being used every 10 minutes or so.

This is with all games being run in windowed mode, using htop and lm-sensors to collect the data.

also worth noting: 
-World of Goo was created for Win/Wii/Mac then ported to Linux as an afterthought. 
-I think DEFCON was intended to have a Linux release from the start.
-Osmos, same as Goo, afterthought.
-Quake was created for Windows, then ported to Linux after being open sourced - Urban Terror was built on this foundation.

This doesn't tell us what the problem is, but it tells us what the problem isn't: it is ***not*** a WINE problem.


What's that have to do with linux multicore? None of those games are coded for multiple cores. Run an app in the background when you are running those games and it'll send the cpu load to the other core.

How on earth would an operating system be able to split up the processing of an application? That's the applications obligation, there would be nonstop critical errors if the OS tried to figure out how to send one processes' instructions to multiple cores.

---

### Post by Half-Left on 2010-07-10
I wish people would stop using top as an end all for system monitor stats. It's just not reliable.

If you compile using the proper flag it will use all your cores. I remember building KDE4 with make -j6 and all cores were being used 100%.

---

### Post by earthpigg on 2010-07-10
> **Redo said:**
> What's that have to do with linux multicore? None of those games are coded for multiple cores.

see:

> This doesn't tell us what the problem is, but it tells us what the problem isn't: it is not a WINE problem.

was in response to the earlier speculation that WINE stuff running in single core could have been unique to WINE.

> How on earth would an operating system be able to split up the processing of an application?

i don't know, im not a coder.

conjecture: 

software is created that features a virtual single core and "lies" to the target program. target program sends it's instructions to the apparent 'single core', and this software splits the load amongst several cores.

overall CPU cycle usage would be higher, but the entire load wouldn't be on one core.

presumably, the virtual single core software would be written from the ground up to efficiently utilize n cores.

yes/no?

---

### Post by MasterNetra on 2010-07-10
> **earthpigg said:**
> on Ubuntu 10.04, i7 quad, 6gb RAM, GTS250 1gb Video card, and only native software:

-world of goo causes one core to spike when started, then settles down to occasional single-core spikes

-defcon uses 90-100% of one core the entire time it is running

-osmos uses 90-100% of one core the entire time it is running

-urban terror uses 70-100% of one core the entire time it is running

These are four very well known Linux games. Any top ten list would include at least two or three of these.

They all run very well, but all the computing being only done on one CPU means my fans are forced to go batcrap crazy to keep that one CPU at or below 75°C. 

One possible haphazard solution would be to simply switch which single core is being used every 10 minutes or so.

This is with all games being run in windowed mode, using htop and lm-sensors to collect the data.

also worth noting: 
-World of Goo was created for Win/Wii/Mac then ported to Linux as an afterthought. 
-I think DEFCON was intended to have a Linux release from the start.
-Osmos, same as Goo, afterthought.
-Quake was created for Windows, then ported to Linux after being open sourced - Urban Terror was built on this foundation.

This doesn't tell us what the problem is, but it tells us what the problem isn't: it is ***not*** a WINE problem.

All that proves is there are other high cpu using/insufficent programs out there. It doesn't prove wine isn't the problem with running WoW in fact has absolutely nothing to do with the subject, those are different programs. Its been demostarted time after time that Linux itself has little to no issues with handling multiple cpus, the most likely problem is with the interaction between WoW and Wine.

---

### Post by sandyd on 2010-07-10
> **Rhubarb said:**
> It really depends what workload you're giving it.
For instance, if you're doing a lot of heavy stuff in firefox, it'll only consume 1 core, because firefox is simply not coded (yet) to support multiple cores.

There are many many apps that'll only work on the 1 core, while there are only a few that support multiple cores.

Some multi-core supporting apps:
make - by default compiling only uses 1 core, but if you use the -j2 option it'll compile with 2 cores.
x264 - great codec for encoding videos, and supports 1 or many cores which you have to specify to get the performance boost.

Some apps just aren't well suited for multicore use.

Another thing that is noteworthy, is that apple has recently released [Grand Central Dispatch]("http://en.wikipedia.org/wiki/Grand_Central_Dispatch") as open source, so it's now possible to integrate this into Linux systems as well.

On a related note, Linux is used for many of the world's top super computers, where they have thousands of CPUs - but these systems run customised applications on a customised linux distro.

To sum up, if you run the same applications on your Mac as you do in Ubuntu, there really shouldn't be that much of a difference in CPU work loads.
bein worked on while your talkin
[http://brainstorm.ubuntu.com/idea/24845/](http://brainstorm.ubuntu.com/idea/24845/)

---

### Post by earthpigg on 2010-07-10
> **MasterNetra said:**
> All that proves is there are other high cpu using/insufficent programs out there. It doesn't prove wine isn't the problem with running WoW in fact has absolutely nothing to do with the subject, those are different programs. Its been demostarted time after time that Linux itself has little to no issues with handling multiple cpus, the most likely problem is with the interaction between WoW and Wine.

It proves that games written for Linux not being designed to effectively use multiple cores is the norm, not the exception.

An open source solution specifically tailored to address this pattern wouldn't be the first time that open source coders solved a problem created by others.

now, if only i where a kernel hacker....


...maybe someday :P

---

### Post by stmiller on 2010-07-10
Here is Linux running on a 128 core machine:

[http://imgur.com/pl6XW.png](http://imgur.com/pl6XW.png)


:)

---

### Post by earthpigg on 2010-07-10
> **stmiller said:**
> Here is Linux running on a 128 core machine:

[http://imgur.com/pl6XW.png](http://imgur.com/pl6XW.png)

If I had that much processing power... ***I could play 127 typical Linux games at once!!*** :P

back to slightly less ridiculous comments: do you know what that computer is used for, or who owns it?

---

### Post by Redo on 2010-07-10
> **earthpigg said:**
> yes/no?

Well let me throw you an example. An operating system can only send a process the the CPU to be executed. If the program decides to split the operation over two cores, it has to figure out the fine details of how to do so.

Back to a basic example, let's say you have something like a calculator application. And you tell the calculator to do this calculation, "3 times 4 divided by 17, all to the 3rd power", or (3*4/17)^3

If the OS is to figure out how to split that up over multiple cores, it may decide to send 3/17 on core 1 and 4^3 on core 2, then multiply those two products together. Or it can do 3*4 on core 1, divided by 17^3 on core 2, all at once. They produce drastic differences in calculations. It's a sequential operation, and no OS could ever split that calculation up into two simultaneously parts and come up with the same result. It must be a sequential operation.

The OS doesnt have a CLUE how to split up the calculations, the program must tell the OS and CPU's how figure it out. There's no automatic algorithm to split this up that the OS can implement. And that's a basic calculator app, if a program is doing complex operations, it is simply impossible for the OS to figure out what should be sequential and what should be parallel.

---

### Post by MasterNetra on 2010-07-10
> **earthpigg said:**
> It proves that games written for Linux not being designed to effectively use multiple cores is the norm, not the exception.

An open source solution specifically tailored to address this pattern wouldn't be the first time that open source coders solved a problem created by others.

now, if only i where a kernel hacker....


...maybe someday :P

Aye theres that too, but it still had nothing to do with proving anything regarding wow + wine nor does it have anything really to do with Linux itself or the OS is not fully Multi-Processor ready.

---

### Post by Half-Left on 2010-07-10
> **stmiller said:**
> Here is Linux running on a 128 core machine:

[http://imgur.com/pl6XW.png](http://imgur.com/pl6XW.png)


:)

Well, it's a known fact that most of the world's top supercomputers run Linux, so the thread it quiet funny really. :p

---

