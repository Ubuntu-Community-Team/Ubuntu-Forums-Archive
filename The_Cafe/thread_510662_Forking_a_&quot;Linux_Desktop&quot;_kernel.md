---
title: "Forking a &quot;Linux Desktop&quot; kernel"
date: 2007-07-26
forum: The Cafe
---

### Post by psyopper on 2007-07-26
I just [read this really interesting article ]("http://www.nuxified.org/article/fork_a_kernel_kill_an_os_and_revolutionize_the_desktop")that asks many of the questions I have been asking myself lately after attending the UbuntuLive conference.

The basic premise is that maybe there SHOULD be a Desktop Linux kernel. Here's a few snippets to look over to see if you think the article is interesting enough to read:

"**Linux kernel is too bloated**

It was made for servers because that's where its initial success was possible and where most of the money came. ... Developers are also developing on machines which are too powerful compared to the machines that ordinary desktop users are using,"

"**Lack of communication with desktop users**

Linux kernel developers are normatively disconnected from the rest of the users, most of which are desktop users, the kind making up 90% of all computer users. ... a lot of the time [the developers will] be oblivious to the needs of the ordinary desktop users."

"The point that CK makes is related to performance issues on hardware which is so powerful that it shouldn't have performance issues at all. Why do we still need a specially optimized Linux kernel just to properly enable music production? Shouldn't real time audio processing just work absolutely flawlessly on computers containing dual core CPUs? Even Windows XP doesn't have this requirement."

"One of the solutions being pondered is forking a Linux kernel into a kernel which would specifically be aimed at desktop users and their needs."

So what do you all think? I think there is DEFINITELY a need for a Linux Desktop kernel. Ubuntu could champion this easily and include it on the LiveCD's as a "checkbox" to select between the standard and Desktop kernel during installation.

---

### Post by igknighted on 2007-07-26
Are there enough programmers?  I would LOVE to help, but I lack the skills (as of now).  I think the real solution is to get a panel to oversee benchmarking on the kernel in ways meaningful to desktop users.  Have representatives from all the major desktop distros there and have them run some tests and put pressure on kernel developers in our favor.  We don't need to divide our strength, we need our voice to be heard.  We need a Union if you will, and not one of those POS greedy organizations that are America's unions now, but an actual group that will stand up and give us a voice.

---

### Post by init1 on 2007-07-26
> **psyopper said:**
> I just [read this really interesting article ]("http://www.nuxified.org/article/fork_a_kernel_kill_an_os_and_revolutionize_the_desktop")that asks many of the questions I have been asking myself lately after attending the UbuntuLive conference.

The basic premise is that maybe there SHOULD be a Desktop Linux kernel. Here's a few snippets to look over to see if you think the article is interesting enough to read:

"**Linux kernel is too bloated**

It was made for servers because that's where its initial success was possible and where most of the money came. ... Developers are also developing on machines which are too powerful compared to the machines that ordinary desktop users are using,"

"**Lack of communication with desktop users**

Linux kernel developers are normatively disconnected from the rest of the users, most of which are desktop users, the kind making up 90% of all computer users. ... a lot of the time [the developers will] be oblivious to the needs of the ordinary desktop users."

"The point that CK makes is related to performance issues on hardware which is so powerful that it shouldn't have performance issues at all. Why do we still need a specially optimized Linux kernel just to properly enable music production? Shouldn't real time audio processing just work absolutely flawlessly on computers containing dual core CPUs? Even Windows XP doesn't have this requirement."

"One of the solutions being pondered is forking a Linux kernel into a kernel which would specifically be aimed at desktop users and their needs."

So what do you all think? I think there is DEFINITELY a need for a Linux Desktop kernel. Ubuntu could champion this easily and include it on the LiveCD's as a "checkbox" to select between the standard and Desktop kernel during installation.

Desktop Kernel? Sounds like a kernel designed for GUI use. Wouldn't that eliminate native CLI use? That's a bad idea.

---

### Post by euler_fan on 2007-07-26
This might just be me, but I fail to see how bloat on a server is any better than bloat on a desktop.

I can see how developing on a machine where you don't feel the bloat can lead to an OS too heavy for the mainstream, but certainly there are any number of packages/processes in the kernel that could be improved by making them lighter/more efficient improving performance on both desktop and server alike.

IMHO, more power should not be an excuse for heavier software and efficiency should always be a top goal in software design at all levels, and for all environment.

It might never happen again in the desktop market, but still.

---

### Post by igknighted on 2007-07-26
> **init1 said:**
> Desktop Kernel? Sounds like a kernel designed for GUI use. Wouldn't that eliminate native CLI use? That's a bad idea.

Nonono, the issue is that the linux kernel comes optimized for servers.  Many of the changes deal with gaining an extra 0.1% on database benchmarks (as most kernel developers are paid by companies that make their money on servers... they want the best server OS possible).  Believe it or not, lots of these changes to help servers actually hurt desktop users.  The types of tasks the kernels do is different enough that something that speeds up database queries hurts responsiveness on the desktop.  Right now there is no voice to the kernel devs that this is happening.  How can an average desktop user say that since the recent kernel update tabs on firefox open slower (I took this example from the con article).

This has nothing to do with GUIs or programs installed, but rather how the kernel handles typical desktop tasks compared to typical server tasks.

---

### Post by starcraft.man on 2007-07-26
> **igknighted said:**
> Nonono, the issue is that the linux kernel comes optimized for servers.  Many of the changes deal with gaining an extra 0.1% on database benchmarks (as most kernel developers are paid by companies that make their money on servers... they want the best server OS possible).  Believe it or not, lots of these changes to help servers actually hurt desktop users.  The types of tasks the kernels do is different enough that something that speeds up database queries hurts responsiveness on the desktop.  Right now there is no voice to the kernel devs that this is happening.  How can an average desktop user say that since the recent kernel update tabs on firefox open slower (I took this example from the con article).

This has nothing to do with GUIs or programs installed, but rather how the kernel handles typical desktop tasks compared to typical server tasks.

Agreed (based on my limited knowledge of kernels over the years).

I dunno if forking is the end all solution, might cause too much trouble. We do need to bring more attention to the desktop in order to get overall performance and experience improved. We can't just rely on folks like ck's patches to do it for us. Maybe Shuttleworth should start an initiative based on this and talk with Linus about setting up some sort of streamlined way of getting Kernel problems to devs (average desktop users certainly don't want mailing lists... I think that's been established).

---

### Post by init1 on 2007-07-26
> **igknighted said:**
> Nonono, the issue is that the linux kernel comes optimized for servers.  Many of the changes deal with gaining an extra 0.1% on database benchmarks (as most kernel developers are paid by companies that make their money on servers... they want the best server OS possible).  Believe it or not, lots of these changes to help servers actually hurt desktop users.  The types of tasks the kernels do is different enough that something that speeds up database queries hurts responsiveness on the desktop.  Right now there is no voice to the kernel devs that this is happening.  How can an average desktop user say that since the recent kernel update tabs on firefox open slower (I took this example from the con article).

This has nothing to do with GUIs or programs installed, but rather how the kernel handles typical desktop tasks compared to typical server tasks.
OK, that's better. I didn't understand, but I do now.

---

### Post by PrimoTurbo on 2007-07-27
YES! The inherent problem of Linux is how slow it is on the desktop! I've been saying this all a long...

---

### Post by igknighted on 2007-07-27
> **PrimoTurbo said:**
> YES! The inherent problem of Linux is how slow it is on the desktop! I've been saying this all a long...

Honestly, I would be willing to bet that if there is ANY noticeable slowdown from XP it is a driver-related issue.  Most of the kernel related stuff is more "why isn't this blowing the bloated winXP out of the water" level things.  It's hard to say for sure though.  So much hardware is supported amazingly out of the box (WAY more than windows), but if it isn't the chances of finding good 3rd party drivers aren't good.  This could change due to an API change forthcoming in the 2.6.23 kernel, so hang in there.

---

### Post by runningwithscissors on 2007-07-27
Ah. Like always there is a lot of managerial 'we should do this'/'vision for the Linux desktop' nonsense.

I doubt anybody is going to hack on a "Desktop kernel" (whatever that is), though. 

A good, secure server OS makes for a good desktop OS too. I don't see why anyone would want to create a fork for desktop use.

---

### Post by hanzomon4 on 2007-07-27
Can't this be done at the distro/oem(if they get into the game) level with custom patchs to the main kernel?

---

### Post by runningwithscissors on 2007-07-27
> **hanzomon4 said:**
> Can't this be done at the distro/oem(if they get into the game) level with custom patchs to the main kernel?
Most distros supply a patched kernel.

---

### Post by vexorian on 2007-07-27
afaik ubuntustudio comes with  specific kernel changes for its tasks.

I think it would be rather nice if canonical could do some tweaks or even hire this guy. it is all FLOSS so we can do it... of course it needs resources.

Of course, I don't really buy much of the article since so far performance is not the main complaint I read about Linux on the desktop.

Edit: To put the post in context I initially thought the article in mention was this: [http://apcmag.com/6735/interview_con_kolivas](http://apcmag.com/6735/interview_con_kolivas)

---

### Post by PrimoTurbo on 2007-07-27
> **igknighted said:**
> Honestly, I would be willing to bet that if there is ANY noticeable slowdown from XP it is a driver-related issue.  Most of the kernel related stuff is more "why isn't this blowing the bloated winXP out of the water" level things.  It's hard to say for sure though.  So much hardware is supported amazingly out of the box (WAY more than windows), but if it isn't the chances of finding good 3rd party drivers aren't good.  This could change due to an API change forthcoming in the 2.6.23 kernel, so hang in there.

The problem is Linux not the hardware, why do people always blame everything but Linux. Any time there is clearly a problem, everyone who supports Linux says. No way it can't be the structure of Linux, it can't be the kernel! It's the damn hardware or your video drivers or whatever else. Clearly it's NOT...Why? Because higher end hardware does NOT have slow downs like the lower end Pentium 4's of the last generations. Because it has enough raw power to cope with the issues, while everyone stuck on medium end to low end hardware suffers with crappy performance.

I have never been able to mimic the smooth operation of Windows on Linux, I'm talking about general responsiveness of windows, resizing and scrolling. It's not even close on the same hardware, no matter what tweaks I have done, what desktop environment I have used or what drivers I have used.

---

### Post by PrimoTurbo on 2007-07-27
> **runningwithscissors said:**
> Ah. Like always there is a lot of managerial 'we should do this'/'vision for the Linux desktop' nonsense.

I doubt anybody is going to hack on a "Desktop kernel" (whatever that is), though. 

A good, secure server OS makes for a good desktop OS too. I don't see why anyone would want to create a fork for desktop use.

Clearly there is a fundamental problem, why **wouldn't someone** want to optimize Linux for desktop use?..

---

### Post by runningwithscissors on 2007-07-27
> **PrimoTurbo said:**
> Clearly there is a fundamental problem, why **wouldn't someone** want to optimize Linux for desktop use?..
I don't see this "fundamental problem". And I use 2.6.19 on a pentium 4 machine with the latest KDE.
Maybe you ran into some problems (which is unlucky), but Linux is perfectly fine for desktop use.

Of course, Con Kolivas worked on improving interactivity for desktops, so he'll always think it can be bettered, but for normal use I haven't run into any problems.

Besides, everybody here seems to have the idea that kernel devs all run CLI-only installations and aren't interested in making improvements for the desktop, which isn't the case at all.

---

### Post by PrimoTurbo on 2007-07-27
Perhaps you don't notice the difference. I have not seen any desktop use benchmarks of applications starting up and response but I am sure they would be a lot slower on Linux with a modern desktop environment compared to Windows.

But there is a fundamental problem when one of the key developers of the kernel quits and says there is, do you contribute to kernel hacking? If not they how do you deny the fact that there is a problem?...Just because you think your desktop environment runs fast enough?

---

### Post by runningwithscissors on 2007-07-27
> **PrimoTurbo said:**
> Perhaps you don't notice the difference. I have not seen any desktop use benchmarks of applications starting up and response but I am sure they would be a lot slower on Linux with a modern desktop environment compared to Windows.Except, I've used Windows on the same hardware and I don't notice a difference.

> **PrimoTurbo said:**
> But there is a fundamental problem when one of the key developers of the kernel quits and says there is, do you contribute to kernel hacking? If not they how do you deny the fact that there is a problem?...Just because you think your desktop environment runs fast enough?Con Kolivas quit over his work not being deemed good enough for the  mainline kernel. Yes, interactivity for desktop users can be improved (there is _always_ room for improvement), but as of _right now_ it is decent, and work is actually going on to make the OS more responsive for everybody.

Also, the bit about communication between desktop users and kernel developers. The LKML is open to everybody. I don't see why users can't communicate with kernel devs right now.

The "article" is FUD-ish.

---

### Post by PrimoTurbo on 2007-07-27
> **runningwithscissors said:**
> Except, I've used Windows on the same hardware and I don't notice a difference.

Con Kolivas quit over his work not being deemed good enough for the  mainline kernel. Yes, interactivity for desktop users can be improved (there is _always_ room for improvement), but as of _right now_ it is decent, and work is actually going on to make the OS more responsive for everybody.

Also, the bit about communication between desktop users and kernel developers. The LKML is open to everybody. I don't see why users can't communicate with kernel devs right now.

The "article" is FUD-ish.

No offense you have no clue what you are talking about. You are not a kernel developer and you have provided no benchmarks that prove that Linux desktop is on par to Windows in regards to speed, start up and general GUI responsiveness. I notice a clear difference on older hardware in respect to responsiveness of the desktop on all major desktop environments. (XFCE, KDE, GNOME) I have installed Linux (Ubuntu, Gentoo, Debian, Mandrake, Slackware, plus a dozen others) on nearly all computers at my works (over 55 computers) ranging from Pentium 3's 700MHZ to Pentium 4's 3GHz+. I notice the same problem across all of them, while less noticeable on 2GHz+ machines it's still very clear there are GUI problems across all of the machines. With video drivers installed correctly and 3d applications running fine.

Furthermore besides the fact that the kernel is not optimized for desktop use, there are inherent desktop and kernel communication problems. It's far slower rendering various windows because of the separate processes for each operation and the fact that the desktop environment runs completely separate from the kernel.

Why do people care so much that the kernel is optimized? It's already nearly different on every distribution.  Technically it's been forked hundreds of times.

---

### Post by runningwithscissors on 2007-07-27
> **PrimoTurbo said:**
> No offense you have no clue what you are talking about. You are not a kernel developer and you have provided no benchmarks that prove that Linux desktop is on par to Windows in regards to speed, start up and general GUI responsiveness. I notice a clear difference on older hardware in respect to responsiveness of the desktop on all major desktop environments. (XFCE, KDE, GNOME) I have installed Linux (Ubuntu, Gentoo, Debian, Mandrake, Slackware, plus a dozen others) on nearly all computers at my works (over 55 computers) ranging from Pentium 3's 700MHZ to Pentium 4's 3GHz+. I notice the same problem across all of them, while less noticeable on 2GHz+ machines it's still very clear there are GUI problems across all of the machines. With video drivers installed correctly and 3d applications running fine.Neither are you a kernel developer or have provided any benchmarks to support your claim.

> Furthermore besides the fact that the kernel is not optimized for desktop use, there are inherent desktop and kernel communication problems. It's far slower rendering various windows because of the separate processes for each operation and the fact that the desktop environment runs completely separate from the kernel.Uh... all OSes use seperate processes for operations. Furthermore, X isn't built into the kernel precisely due to the same reason that GNOME isn't built into the kernel. It doesn't belong there. And for good reason too. Nobody wants an X crash to bring down the whole OS.

> Why do people care so much that the kernel is optimized? It's already nearly different on every distribution.  Technically it's been forked hundreds of times.Precisely. Hence, the whole "desktop fork" deal is a non-issue.

---

### Post by Sunforge on 2007-07-27
Good grief. I read through the interview that sparked this thread and have to say, based on his comments that he had pretty valid grounds for ceasing his contributions. He'd had enough: he was devoting too much of his time to the Linux kernel and he felt that he was getting too little reward for it. Good for him and I wish him all the best learning Japanese.

His comments about the kernel community being unfriendly mirrors most people's view of IT the world over. The authority that you are given as a specialist in any role has to be balanced with the responsibility to use and share that knowledge with those who know less than you in a polite and responsible way.

Having said that the complaints voiced in the article aren't new: doctors, lawyers, accountants, in fact any specialist occupation has its fair share of people with a god complex. Linux and software development in general is no exception to this rule.
His other comments on hardware innovation being stifled by dominance of a single OS have some merit. The rise of Microsoft has meant that people the world over can exchange information speedily and efficiently but at a price: lack of choice. Linux has become the phenomenon it has partly in response to this lack of choice but as it grows it will suffer the same problems that Microsoft suffers from: you can’t be all things to all people and some hard choices will have to be made to ensure that it stays the phenomenon that it is.

---

### Post by salsafyren on 2007-07-27
Linux is definitely slower GUI wise than Windows.

I myself blame GTK mostly since QT feels much faster.

I think the GTK developers know that this is a problem, but it is a hard problem to solve.

Also, Firefox is much slower in Linux than Windows.

I would love for someone to post benchmarks on this, since a lot of people say it is a problem.

Just saying "It is not a problem for me, so we shouldn't do a thing about it" is really ignoring this issue.

Let's make Linux better, not put our head in the sand.

---

### Post by izanbardprince on 2007-07-27
A lot of the "bloat" can be left out before you compile the kernel, the performance issues are caused by the generic kernels that come with this distro or that one, because they have to compile in a TON of stuff that most people won't need.

The first thing that happens whenever I install Linux is I compile my own kernel specifically for the system it'll be running on, despite what people say, it does increase performance considerably.

---

### Post by igknighted on 2007-07-27
> **PrimoTurbo said:**
> The problem is Linux not the hardware, why do people always blame everything but Linux. Any time there is clearly a problem, everyone who supports Linux says. No way it can't be the structure of Linux, it can't be the kernel! It's the damn hardware or your video drivers or whatever else. Clearly it's NOT...Why? Because higher end hardware does NOT have slow downs like the lower end Pentium 4's of the last generations. Because it has enough raw power to cope with the issues, while everyone stuck on medium end to low end hardware suffers with crappy performance.

I have never been able to mimic the smooth operation of Windows on Linux, I'm talking about general responsiveness of windows, resizing and scrolling. It's not even close on the same hardware, no matter what tweaks I have done, what desktop environment I have used or what drivers I have used.

Dude, please read my post.  Never once did I say your hardware was bad, but rather that LINUX has poor driver support for it.  While there may be drivers for your decives, they are probably not as optimal as under XP.  So to recap, your hardware is fine, the linux kernel (driver features not included) is fine, but the drivers (the interface between the two) is your bottleneck.

My experience is this:  Linux always chops windows (not Windows (tm)) when moving.  Its a known issue, it doesn't matter your hardware.  I can't tell you if it is xorg or the kernel, it just happens.  Aside from that, the system (for me) is perfectly responsive.  I run linux on every level computer imaginable, I am typing this on a pIII 900 mhz e-pc at work for gods sake, so I'm not just running on high-end hardware.  The fact is, Windows (tm) is probably a bit faster fresh out fo the box.  But that doesn't last.  Windows will also move windows smoother.  Not sure why, it just happens.  But let an XP box be used for a few weeks, or just put it under a heavy load, and window drawing and responsiveness go out the window.  Linux on the other hand is consistant.  My menus come up at roughly the same speed under load and after months, and if one windows crashes or is busy it doesn't affect the rest.

So there are issues with both, I would like to be able to give you more help than that.  I really think that you just got unlucky and your hardware just doesn't have good linux support.  It's not too old at all, most machines I have are older and run fine (esp compared to XP on similar hw), so your case is surprising to me.

EDIT: Just a thought, have you tried the -ck patchset?  I wonder if Con's desktop-optimised kernel would help at all.

EDIT2: This isn't really a support thread, but if you post your specs in detail (or PM them to me) I'll see if there's anything else I can do to help

---

### Post by @trophy on 2007-07-27
> **runningwithscissors said:**
> I don't see why anyone would want to create a fork for desktop use.

So that their desktop will run faster/better without them having to tweak it for applications like playing/making music/videos, surfing the web, and games.

---

### Post by vexorian on 2007-07-27
> **salsafyren said:**
> Linux is definitely slower GUI wise than Windows.

I myself blame GTK mostly since QT feels much faster.

I think the GTK developers know that this is a problem, but it is a hard problem to solve.

Also, Firefox is much slower in Linux than Windows.

I would love for someone to post benchmarks on this, since a lot of people say it is a problem.

Just saying "It is not a problem for me, so we shouldn't do a thing about it" is really ignoring this issue.

Let's make Linux better, not put our head in the sand.
Wow experiences, they are fun and mixes, to me gtk is faster than windows XP, and firefox is a clear sign of speed up, it doesn't take 1 minute to load...



> No offense you have no clue what you are talking about. You are not a kernel developer and you have provided no benchmarks that prove that Linux desktop is on par to Windows in regards to speed

A benchmark is what you do when the speed difference is not noticeable to anyone. You seem to speak as if it was a fact that windows is faster than Linux, which to me seems to depend more on specific hardware and compatibility and drivers and it is a very mixed issue, in my computer Linux+Compiz-fusion is more responsive than windows XP (And I did spend a lot of time taking care of windows XP and I know there's no malware and I don't use any antivirus/spyware monitor / etc )

---

### Post by salsafyren on 2007-07-27
It is clear to me that we need some sort of benchmark to find the various bottlenecks in our system.

My experience is that GTK is slower than QT and Windows. Others say the opposite.

So where is the problem really?

It MUST be possible to quantify the problems, otherwise we are just wasting our time.

It would be nice with a desktop Linux optimization and benchmark project to pinpoint those issues.

---

### Post by Daishiman on 2007-07-27
This thread is so full of misinformation it's despairing, and I think the article makes the most useless and unnecessary proposals.

Let's go step by step. Con accuses the Linux kernel of being "too bloated". 
This is evidently not true. The kernel image takes up 2 megabytes plus drivers. All the subsystems and drivers are loaded on demand, so space-wise this is not an issue.
Algorithmically? There might be a source of slowness there. So which would be the kernel functions that might be performance bottlenecks?
-Drivers
-Disk scheduler
-Process scheduler
-Memory allocator

The disk scheduler is as optimized as it gets. It can be tweaked as desired for server or desktop workloads. My experience with that is that Linux disk performance is as good as it gets.
Process scheduler: Same thing. interactive processes work really, really well. Anyone who's used Gentoo doing background compiling with GCC knows that it's responsive. Certainly Con's argument is not pointed at that.
Memory allocator: Also as good as it gets, getting constant improvement, thankfully light years ahead than what Windows has to offer.
So on the kernel side the only thing we have are drivers, and we have the userspace applications.
The specific exampe of audio latency is due to two things: ALSA and kernelspace timers. I think it's a general opinion that ALSA sucks and needs a lot of work. As far as the high precision timers, they could probably be included in the stock Ubuntu kernel disregarding the performance loss if it's minimal. However that's a decision up to the distros and not the kernel devs themselves.

On app responsiveness, I'd say the fingers should be pointed at Xorg and the respective desktop toolkits. We all know that GNOME and KDE have far more features than, say, a standard XP desktop, but we pay for that in performance. Sure, you can have an XP or Vista desktop with as many features as KDE, but you'll be looking at an even SLOWER and less responsive kernel.

And then we have those huge mastodontic apps like Firefox, Evolution and Amarok that scream bloat. Again, app dev issue. The kernel has little to do with it. Firefox is slower on Linux because it's not the primary optimization target; Windows is. 

I think we can all eat some humble pie and admit that the kernel dev process is hardly user friendly. But from the interview it's also very clear that Con is not a computer scientist and there are a lot of things he does not understand as far a as algorithmic correctness goes that need to scale and be done right for everything, whether it's a desktop or a mainframe. I think we can look at the apps, the DE, and the graphics environment before looking at the kernel. Remember that Linux works very well in real-time environments and embedded; certainly when responsiveness is key Linux delivers. The challenge is striking a balance between that and throughput.

---

### Post by init1 on 2007-07-27
> **PrimoTurbo said:**
> YES! The inherent problem of Linux is how slow it is on the desktop! I've been saying this all a long...
Really? Because it works rather fast for me. Try a lighter WM. That should help. I'm not even using a WM right now. I'm in eLinks.

---

### Post by dca on 2007-07-27
Hmm, I've always looked at desktop linux as the by-product.  I'm actually impressed that we're at where we're at...  Linux is for a server.  It's darn good on a server.  SMP kernel, VM kernel, etc.  Is it possible that somebody is misinterpreting recompiling kernels for optimization on a particular platform with actually literally forking the kernel?  I dunno'.  Play nice, guys...

---

### Post by @trophy on 2007-07-27
> **dca said:**
> Hmm, I've always looked at desktop linux as the by-product.  I'm actually impressed that we're at where we're at...  Linux is for a server.  It's darn good on a server.  SMP kernel, VM kernel, etc.  Is it possible that somebody is misinterpreting recompiling kernels for optimization on a particular platform with actually literally forking the kernel?  I dunno'.  Play nice, guys...

What they're suggesting is forking the kernel so that desktop linux will no longer be a by-product.  And, other than the fact that forking is very expensive in terms of resources, manpower, and momentum, I agree.

---

### Post by psyopper on 2007-07-27
While I am certianly no programmer (I did build a JavaScript array once, about 8 years ago... and now that I use Linux I understand why it started with a 0) I do understand the science behind computer science. The work Con was doing was specifically aimed at process scheduling. 

Here's what I understand about process scheduling in a very high level view. There are essentially two types of tasks - foreground tasks and background tasks. Foreground tasks include things like the GUI, user input, display output and a host of other things that go into a "desktop experience". Background tasks include things like managing transactions on your MySQL database, managing your print queue, SAMBA, Apache and the like.

To give you a general idea what foreground and background tasks you are running on your computer, open up your System Monitor (System | Administration | System Monitor) and look at the Processes tab. The things listed with an icon are generally considered foreground tasks, the things listed without the icon are generally background processes.

Both foreground and background processes are required to run your desktop. There's no sense in sending data to your disk if there is no disk IO process running. And there's no sense in sending your favorite MP3 to Amarok if Amarok isn't running. 

Here's the deal though. On a desktop installation of Linux most users expect responsiveness out of their visible applications, GTK, Amarok, Gnome Panel, etc. Until recently the Linux kernel gave processor priority to background processes instead of foreground processes. For the most part the difference was never noticeable to the user, but under certian circumstances it DOES become noticeable to the user, particularly on average to older systems (and certianly not the Dual Quad Core Pentiums mentioned) because the processor can only do so many things per second. 

In the data-center (where the majority of the kernel devs focus their work) where the GUI is interacted with as little as once or twice a day, foreground tasks need little no no prioritization and process scheduling was optimized for background processes so that your Apache implementation can access your PostgreSQL database and return data to the user faster.

This is where Con came in. 

He was (probably still is) a desktop Linux user. He realized that the kernel was optimized against processes he used daily. His initial hacks were (almost exclusively) focused on forcing priority to userspace processes *when requested* by the user, otherwise priority was given to background processes. ( when click{clickedthings happen} else{otherthings happen} ) This worked reasonably well in most circumstances as a real data-center Linux install could include a GUI, but once configured could be run in CLI only which drastically reduced the number of foreground processes and let the processor be fed by the background; and a desktop Linux implementation whould produce a snappier system to the end user at the expense of things like disk IO.

His implementations were eventually nixed (pun semi-intended) by Linus in favor of a different sort of process optimization focused on fair process scheduling. This sort of scheduler works on a "round robin" basis giving no prioritization to either foreground or background tasks. Instead processes queue up and take a number and when their number comes up they get to send their request, just like your local DMV (except a s**tload faster)!

Why did Linus boot Con's ideas? Because the "fair process" scheduler was already implemented in the kernel by a different dev in one of the side branches. In fact it had been there for several months and had supposedly been undergoing ongoing regression testing by people custom compiling. There is some consternation about this process scheduler as it appears it includes a number of lines of code initially written by Con. This is why Con finally gave up, and when Linus et al implemented the "fair process" scheduler is about *when* Con gave up.

---

### Post by talkingwires on 2007-07-28
*deleted*

---

### Post by psyopper on 2007-07-28
So Linus apparently has something to say about this specific subject.

It's all on lmkl and [summed up quite nicely in this article]("http://kerneltrap.org/node/14008")

[I]From:	Linus Torvalds [email blocked]
Subject: Re: [ck] Re: Linus 2.6.23-rc1
Date:	Sat, 28 Jul 2007 10:12:32 -0700 (PDT)

People are suggesting that you'd have a separate "desktop kernel". That's 
insane. It also shows total ignorance of maintainership, and reality. And 
I bet most of the people there haven't tested _either_ scheduler, they 
just like making statements.[/I]

<snip>

[I]The fact is, I've _always_ considered the desktop to be the most important 
part. And I suspect that that actually is true for most kernel developers, 
because quite frankly, that's what 99% of them ends up using.

<snip>

So the whole argument about how kernel developers think that the desktop 
isn't important is totally made-up crap by Con, and then parrotted by 
osnews and other places.[/I]

<snip>

[I]The fact is, most kernel developers realize that Linux is used in 
different places, on different machines, and with different loads. You 
cannot make _everybody_ happy, but you can try to do as good a job as 
possible. And doing "as good a job as possible" very much includes not 
focusing on any particular load.[/I]

---

### Post by forrestcupp on 2007-07-28
> **psyopper said:**
> So Linus apparently has something to say about this specific subject.

It's all on lmkl and [summed up quite nicely in this article]("http://kerneltrap.org/node/14008")


Wow.  I thought this was a good idea until I read what Linus said.

Maybe the patched kernels we get from our distros are good enough.  I do wish you could get a good real-time kernel without having to build it yourself, though.

---

### Post by swoll1980 on 2007-07-28
I'd rather fork my friends wife :)

---

### Post by RAV TUX on 2007-07-28
> **forrestcupp said:**
> Wow.  I thought this was a good idea until I read what Linus said.



This topic in a nutshell:

>  "a person who can actually be bothered to follow up on problem reports is a *hell* of a lot more important than one who just argues with reporters"~Linus

---

