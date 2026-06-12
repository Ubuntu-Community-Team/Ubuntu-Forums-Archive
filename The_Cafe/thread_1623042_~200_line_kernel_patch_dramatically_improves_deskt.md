---
title: "~200 line kernel patch dramatically improves desktop performance"
date: 2010-11-16
forum: The Cafe
---

### Post by undecim on 2010-11-16
The real article is down right now, but here's the bit from /.

> "There is a relatively miniscule patch to the Linux kernel scheduler being queued up for Linux 2.6.38 that is proving to have dramatic results for those multi-tasking on the desktop. Phoronix is reporting the ~200 line Linux kernel patch that does wonders with before and after videos demonstrating the much-improved responsiveness and interactivity of the Linux desktop. While compiling the Linux kernel with 64 parallel jobs, 1080p video playback was still smooth, windows could be moved fluidly, and there was not nearly as much of a slowdown compared to when this patch was applied. Linus Torvalds has shared his thoughts on this patch: So I think this is firmly one of those "real improvement" patches. Good job. Group scheduling goes from "useful for some specific server loads" to "that's a killer feature"."

[http://linux.slashdot.org/story/10/11/16/1330233/The-200-Line-Linux-Kernel-Patch-That-Does-Wonders](http://linux.slashdot.org/story/10/11/16/1330233/The-200-Line-Linux-Kernel-Patch-That-Does-Wonders)

---

### Post by Thelasko on 2010-11-16
[I managed to read it a few minutes ago.]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1")  I'm excited:P

It'll probably be years before we see this in Ubuntu though. :(

---

### Post by Verbeck on 2010-11-16
> **Thelasko said:**
> 
It'll probably be years before we see this in Ubuntu though. :(
wouldn't 11.04 be using the 2.6.38 kernel?

---

### Post by Thelasko on 2010-11-16
> **Verbeck said:**
> wouldn't t11.04 be using the 2.6.38 kernel?

I heard 2.6.37, but I'll have to check that...

Edit: [Found it!]("https://launchpad.net/ubuntu/+source/linux-meta/+publishinghistory")

So, we are looking at 11.10 for this update.

---

### Post by Helkaluin on 2010-11-16
Any one knows how this compares with the ck patches and the Brain****Scheduler?

---

### Post by Joeb454 on 2010-11-16
There's still a chance it will make it into 11.04 - how slim that chance is though, I couldn't say

Here's hoping :)

---

### Post by aeiah on 2010-11-16
if it really is such a dramatic improvement, then there'll be people rolling their own for 10.04 and 10.10 soon enough, with howtos and/or PPAs as well.

---

### Post by del_diablo on 2010-11-16
> **Helkaluin said:**
> Any one knows how this compares with the ck patches and the Brain****Scheduler?

I know it scales better than Brain****(which is +12 threads).
Beyond that, frankly I got no idea.

---

### Post by Thelasko on 2010-11-16
> **aeiah said:**
> if it really is such a dramatic improvement, then there'll be people rolling their own for 10.04 and 10.10 soon enough, with howtos and/or PPAs as well.

I'm hoping for a backport for 10.04, but I'm not holding my breath.

I have my reservations about using a PPA for a kernel.  Especially if it's a daily build.  That would be a nightmare.

---

### Post by partyk1d24 on 2010-11-16
Oops haha didn't realize what version of Linux Kernel you needed. I tried running the patch on my 10.10 install :-( hopefully I can still reboot, if not it is a good thing I set up my home on another partition. 

I thought it said something in the article about this being done on 10.10. So is there no way (at the current time) to do this with 10.10? If I tried running it do I need to worry about screwing up my existing kernel?

Sorry semi-newbie :-)

---

### Post by Thelasko on 2010-11-16
UPDATE: [It looks like this will be in 11.04 Natty Narwhal!]("https://wiki.ubuntu.com/KernelTeam/Specs/KernelNattyVersionAndFlavours")

> Natty Kernel Version

Likely 2.6.38 (final decision to be made right around Christmas) Advantage of 2.6.38 for linaro is an extra month to submit patches etc.

---

### Post by Thelasko on 2010-11-16
> **partyk1d24 said:**
> Oops haha didn't realize what version of Linux Kernel you needed. I tried running the patch on my 10.10 install :-( hopefully I can still reboot, if not it is a good thing I set up my home on another partition. 

I thought it said something in the article about this being done on 10.10. So is there no way (at the current time) to do this with 10.10? If I tried running it do I need to worry about screwing up my existing kernel?

Sorry semi-newbie :-)

Well, I don't know what you did, but it should be possible to run the patch on 10.10 if you know what you are doing.  However, you will have to compile the kernel from source.  It'll be a real pain.

If you did screw up your kernel, you can usually use an older one by selecting it in the Grub menu.

---

### Post by NightwishFan on 2010-11-16
This looks promising! Mainline has been improving rapidly for desktop performance lately.

---

### Post by MarcusW on 2010-11-16
Tried it. Works really well. :) Desktop responsive when building kernel with -j128, with a crappy C2D ULV processor.

EDIT:
For you who want to try it yourselves, but haven't compiled a kernel. Use "master kernel"s guide (just google it) and apply the patch before configuring. (patch -p1 < file) Good luck. :)

---

### Post by Spice Weasel on 2010-11-16
Phoronix has been slashdotted. :P It's realllllll slow.

Anywho, this is great! If only they could make the kernel a little smaller too...

---

### Post by Sporkman on 2010-11-16
Is this a Haiku killer? :D

---

### Post by czr114 on 2010-11-16
I just finished recompiling and testing, and this makes a world of difference, even over the Lucid preemptive. It's a shame I'll be stuck manually building kernels for a long while.

---

### Post by Npl on 2010-11-16
Wow, after years of flat out denying that there is even a problem, there really is a patch coming?
Hopefully the most important group that need to take the Linux desktop(s) serious but never did changed their stance - which would be the Linux devs.

Great news none the less.

---

### Post by V for Vincent on 2010-11-16
Beautiful. I'll try it out in a few months, once I've got some spare fiddling time...

---

### Post by Thelasko on 2010-11-16
> **czr114 said:**
> I just finished recompiling and testing, and this makes a world of difference, even over the Lucid preemptive. It's a shame I'll be stuck manually building kernels for a long while.

Perhaps a PPA is a better option.

---

### Post by Artemis3 on 2010-11-16
Or using mainline ppa when .38 is ready? Backports would be nice tho ^_^

---

### Post by psusi on 2010-11-16
As usual Phornoix and /. are hyping a non story.  This patch only affects people dumb enough to run make -j64 on the kernel, or some equally bone headed thing to flood their system with dozens of cpu hungry processes.

---

### Post by Thelasko on 2010-11-16
> **psusi said:**
> As usual Phornoix and /. are hyping a non story.  This patch only affects people dumb enough to run make -j64 on the kernel, or some equally bone headed thing to flood their system with dozens of cpu hungry processes.

Flash?

---

### Post by Decatf on 2010-11-16
But how many instances of flash are you gonna be running? Not saying this patch isn't important or anything but it's also important not to over hype it as something it isn't. e.g. "omg Linux is suppose to run super smooth now. really? lemme watch some bluray with my pentium pro now. wait wtf it can't handle it Linux succks!"

---

### Post by psusi on 2010-11-16
Yea, I don't think you are running 64 instances of flash either.

---

### Post by czr114 on 2010-11-16
It takes far fewer than 64 instances to get the load level up that high, especially when you have fewer cores than the testers. It takes only a few CPU-bound processes to bog down a single core system.

I tested it -j64, which isn't that common to most users, but nonetheless represents something a power user might do, in terms of load profile.

---

### Post by del_diablo on 2010-11-16
> **psusi said:**
> As usual Phornoix and /. are hyping a non story.  This patch only affects people dumb enough to run make -j64 on the kernel, or some equally bone headed thing to flood their system with dozens of cpu hungry processes.

It will affect game performance, or when you are updating system in the background on a more patch heavy system(Debian Sid, Archlinux, etc).
It also means that there will be no chokedowns on heavy file transfers <3
So its a big and important patch for the desktop!

---

### Post by HangukMiguk on 2010-11-16
Makes 11.04 a must upgrade for me.  Hoping for a fewer bugs so I can update sooner.

I'll probably fresh install though this time around.  Seems to work better for me than upgrades.

---

### Post by alexan on 2010-11-16
ppa? :confused:


where's the ppa? :confused: :confused:



I want the ppa for it!  :(

---

### Post by Thelasko on 2010-11-16
> **psusi said:**
> Yea, I don't think you are running 64 instances of flash either.

You said bone headed and CPU hungry in the same sentence and it was the first thing that came to mind.:lolflag:

---

### Post by NCLI on 2010-11-16
> **Thelasko said:**
> I heard 2.6.37, but I'll have to check that...

Edit: [Found it!]("https://launchpad.net/ubuntu/+source/linux-meta/+publishinghistory")

So, we are looking at 11.10 for this update.

That Natty currently uses the 2.6.37 kernel doesn't mean that will be the case when it's released ;)

---

### Post by psusi on 2010-11-16
> **czr114 said:**
> It takes far fewer than 64 instances to get the load level up that high, especially when you have fewer cores than the testers. It takes only a few CPU-bound processes to bog down a single core system.

I tested it -j64, which isn't that common to most users, but nonetheless represents something a power user might do, in terms of load profile.

A power user would know better than to fork 64 instances on a 4 core system.


> **del_diablo said:**
> It will affect game performance, or when you are updating system in the background on a more patch heavy system(Debian Sid, Archlinux, etc).
It also means that there will be no chokedowns on heavy file transfers <3
So its a big and important patch for the desktop!

This does not sound like it is the case.  It sounds like it just lowers the priority of a group of numerous ( more than the number of cores you have ) processes that are all trying to gobble up as much cpu as they can.  This is not going to be the case while you are playing a game and upgrading the system, both of which are single threaded and most people these days have 2 or more cores.

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> A power user would know better than to fork 64 instances on a 4 core system.
They test an extreme case, but this patch also improves load leveling with just one or two tasks running. I find that I can now do file transfers while updating the system, and stream a 1080P YouTube video with no issues on my dual-core system, whereas that used to be a very stuttery experience.

---

### Post by psusi on 2010-11-16
> **NCLI said:**
> They test an extreme case, but this patch also improves load leveling with just one or two tasks running. I find that I can now do file transfers while updating the system, and stream a 1080P YouTube video with no issues on my dual-core system, whereas that used to be a very stuttery experience.

No, it doesn't.  It groups processes together when determining their scheduling priority so that 64 tasks in a terminal compete with each other for time slices, and the one or two gui tasks are scheduled separately, rather than treating them as just one out of 66 tasks that all get an equal crack at the cpu.  Transferring files is not a cpu intensive task, so will not be affected by this patch.  I constantly have a bit torrent client running, and can run a single threaded make in the background while watching youtube on my dual core just fine without this patch.

---

### Post by czr114 on 2010-11-16
A power user is also going to be using more than a single threaded make on a dual core system. With fast disk access, they ought to be using somewhere 2:1 threads:cores. That can be said of any other application with a similar usage profile. The best solution would be to boost nice on something like a compilation, but in this example, the compilation is simply standing in for a resource intensive task.

Linux scheduling has, for years, favored server usage. There have been some very ugly arguments and politics, played even by Torvalds himself. It's nice to see some attention paid to the desktop.

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> No, it doesn't.  It groups processes together when determining their scheduling priority so that 64 tasks in a terminal compete with each other for time slices, and the one or two gui tasks are scheduled separately, rather than treating them as just one out of 66 tasks that all get an equal crack at the cpu.  Transferring files is not a cpu intensive task, so will not be affected by this patch.  I constantly have a bit torrent client running, and can run a single threaded make in the background while watching youtube on my dual core just fine without this patch.
It does for me, that's for sure. Have you tried the patch?

---

### Post by tadcan on 2010-11-16
> **Sporkman said:**
> Is this a Haiku killer? :D

I was about to give this a serious response. Then I saw the smiley. Yes, absolutely the Haiku dev team will finally see the error of their ways!

---

### Post by Thelasko on 2010-11-16
The [Phoronix article]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=2") is back up again.  I highly recommend watching the videos.

[Without the patch]("http://www.youtube.com/watch?v=uk70SeGA7pg&feature=player_embedded")

[With the patch]("http://www.youtube.com/watch?v=prxInRdaNfc&feature=player_embedded")

---

### Post by psusi on 2010-11-16
> **Thelasko said:**
> The [Phoronix article]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=2") is back up again.  I highly recommend watching the videos.

[Without the patch]("http://www.youtube.com/watch?v=uk70SeGA7pg&feature=player_embedded")

[With the patch]("http://www.youtube.com/watch?v=prxInRdaNfc&feature=player_embedded")

They look great, but again, who in their right mind ever runs make -j64?

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> They look great, but again, who in their right mind ever runs make -j64?
Well, enconding a video using a multi-core encoder should generate the same load, and many people do that. Or how about importing big photo or music collections?

---

### Post by handy on 2010-11-16
I use HandBrakeCLI to re-encode videos & it uses both cores of my C2Duo, at the highest rate it can, so they are usually running well over 90% each under these circumstances.

---

### Post by psusi on 2010-11-16
> **NCLI said:**
> Well, enconding a video using a multi-core encoder should generate the same load, and many people do that. Or how about importing big photo or music collections?

No, usually multithreaded encoders use one thread per core, not 64 on a system with far fewer cores than that.

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> No, usually multithreaded encoders use one thread per core, not 64 on a system with far fewer cores than that.
So what? My main point isn't to compare it to the test, the point is that this patch will help users who need to run intensive operations like these.

---

### Post by psusi on 2010-11-16
> **NCLI said:**
> So what? My main point isn't to compare it to the test, the point is that this patch will help users who need to run intensive operations like these.

Yes, but who in their right mind runs something as insane as make -j64?  Most people don't do silly things like that.  It's great that this patch makes that work load not cause desktop slowdown, but almost nobody ever runs that kind of ridiculous load.  Therefore, your average Ubuntu user will not know the difference, so it seems inappropriate to hail this as some sort of panacea as Phornoix is.

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> Yes, but who in their right mind runs something as insane as make -j64?  Most people don't do silly things like that.  It's great that this patch makes that work load not cause desktop slowdown, but almost nobody ever runs that kind of ridiculous load.  Therefore, your average Ubuntu user will not know the difference, so it seems inappropriate to hail this as some sort of panacea as Phornoix is.
The average user doesn't compile the kernel with 64 threads, we can both agree on that. However, the average user is likely to import media collections and encode videos, which this patch will make a much more pleasant experience, which is why it should be hailed as a "panacea."

---

### Post by psusi on 2010-11-16
> **NCLI said:**
> The average user doesn't compile the kernel with 64 threads, we can both agree on that. However, the average user is likely to import media collections and encode videos, which this patch will make a much more pleasant experience, which is why it should be hailed as a "panacea."

Given that those activities do not involve more than one or two threads, this patch will not make much difference.

---

### Post by NCLI on 2010-11-16
> **psusi said:**
> Given that those activities do not involve more than one or two threads, this patch will not make much difference.
It will if you'd like to browse the web while doing one of them, which I can assure you was a very unpleasant experience in Linux up until now.

---

### Post by handy on 2010-11-17
I've been talking to someone I know about this subject (actually he was the one that made me aware of it :)), & pointed him to the prime argument against it as seen in this thread. Here is his response:

[I]I searched for that thread, and upon reading it, I have decided the debate going on makes me angry in much the same way I got angry browsing UF in the past.

The debate in the thread is not even about the patch anymore, or its potential benefits, it is about threading and the test-case Linus provided where he builds his kernel with a "make -j64" command. This patch, from the reading I've done, isn't entirely about managing multi-threading, but multi-tasking as well. It's an addition to the scheduler, and thus helps control thread and process priority.

Ultimately, this patch will be a major benefit for "Desktop Linux", I think.[/I]
____________

I'll post what he thinks about it after he has tested it some more.

---

### Post by MarcusW on 2010-11-17
20-30 tabs in chrome, a video, msn, doing something in nautilus, maybe rendering something etc are A LOT of threads. I don't see why the -j64 wasn't an appropriate test? It shows Linux works a lot better under heavy loads now. If your experience has always been smooth, what kind of test did you expect to show that it's better now? :S

My computer locked down totally some times when rendering an image with multithreading and way too many photons. I expect that won't happen now, so I can enable multithreading again. :)

---

### Post by Hells_Dark on 2010-11-17
Best news for monthes :)

---

### Post by Shining Arcanine on 2010-11-17
> **NCLI said:**
> It will if you'd like to browse the web while doing one of them, which I can assure you was a very unpleasant experience in Linux up until now.

I thought NICE levels were for that.

---

### Post by Sporkman on 2010-11-17
> **tadcan said:**
> I was about to give this a serious response. Then I saw the smiley. Yes, absolutely the Haiku dev team will finally see the error of their ways!

It's just that one of the big arguments for Haiku on the desktop is its superiority in video playback over linux.

---

### Post by tadcan on 2010-11-17
Yes I've seen the demos and heard the complaints that because linux is put together from a collection of different programs in can never match the efficiency of haiku code base.

When I was using shotwell to do some colour tweaking my dual core 1.7GHz system struggled with nothing else running. So I'll give it a go again when am running the new kernel.

---

### Post by undecim on 2010-11-17
Guys, this does more than just help you run your desktop while running a make -j64. That was *just a test case.* Before you go and say that this patch isn't worth the lines of code actually *Try the patch out for yourself.* Specifically, on a low-end machine (it still makes a difference on newer machines, but it's not as noticable.

It makes the entire desktop much more responsive, even if you're not running something that intensive.

---

### Post by psusi on 2010-11-17
> **NCLI said:**
> It will if you'd like to browse the web while doing one of them, which I can assure you was a very unpleasant experience in Linux up until now.

No, it hasn't been an unpleasant experience, and this patch will have ZERO effect on that load.  It only affects loads where you have a terminal with many threads all trying to run, and another window.  If there is only one busy task in the terminal, and one gui task, this patch does not change how they are scheduled.

> **MarcusW said:**
> 20-30 tabs in chrome, a video, msn, doing something in nautilus, maybe rendering something etc are A LOT of threads. I don't see why the -j64 wasn't an appropriate test? It shows Linux works a lot better under heavy loads now. If your experience has always been smooth, what kind of test did you expect to show that it's better now? :S

The tabs are not all trying to run at the same time.  You have at most one active one that is busy rendering the page you just loaded up, or playing the video you are watching, and the rest are sleeping.  Not to mention that this patch groups tasks by tty, so it treats all of the chrome tasks the same as any other gui task.  It only firewalls off tasks being run in a terminal.

> **MarcusW said:**
> My computer locked down totally some times when rendering an image with multithreading and way too many photons. I expect that won't happen now, so I can enable multithreading again. :)

You don't seem to be using the word photons in a way that makes sense, so I think you misunderstand what it means.

---

### Post by psusi on 2010-11-17
> **undecim said:**
> Guys, this does more than just help you run your desktop while running a make -j64. That was *just a test case.* Before you go and say that this patch isn't worth the lines of code actually *Try the patch out for yourself.* Specifically, on a low-end machine (it still makes a difference on newer machines, but it's not as noticable.

It makes the entire desktop much more responsive, even if you're not running something that intensive.

Then you are suffering from a placebo effect.  The patch only alters the way a group of tasks being run in a terminal are scheduled, so if you aren't running a group of tasks in a terminal, then this patch is not affecting you.

---

### Post by Rave Gloves on 2010-11-17
Has anyone tried this on the netbook edition? How would i go about trying this out?

---

### Post by rmmst49 on 2010-11-17
psusi: not to belabor the point, but you seem to be very sure in your theoretical understanding of this patch while never having answered the question of if you'd actually tried the patch yourself.  unless the whole internet, the kernel people, and the people who have actually tested the patch for themselves are wrong, this patch seems poised to advance linux desktop responsiveness quite a bit, and that's sorely needed. Unless those phoronix videos are fakes, which they aren't, i want to try this patch NOW.

I would love to try this patch, but i'm really busy. someone with a little free time PLEASE BACKPORT THIS TO A PPA IF POSSIBLE, please allow me to get the benefits without having to do the work of downloading source, repatching, recompiling and reinstalling each new security release kernel manually. please please please.

---

### Post by Pogeymanz on 2010-11-17
I agree that this patch is a little over-hyped. Don't get me wrong, I'm excited about it too, but it isn't going to make Desktop Linux feel significantly better.

We need a better I/O scheduler for that. Con Kolivas's patches are amazing for Desktop responsiveness, especially because of the BFQ I/O scheduler, which fixes the horrible brokenness that somehow chokes any desktop system I've used when deleting/copying/saving a large file(s).

There should also be some built-in option to have the kernel prioritize executables from /usr/bin over other executables, so that our user apps are always more responsive than system processes.

I've thought about making some kind of hack that would just launch everything I do with a higher 'nice' level than default.

---

### Post by del_diablo on 2010-11-17
> **MarcusW said:**
> 20-30 tabs in chrome, a video, msn, doing something in nautilus, maybe rendering something etc are A LOT of threads. I don't see why the -j64 wasn't an appropriate test? It shows Linux works a lot better under heavy loads now. If your experience has always been smooth, what kind of test did you expect to show that it's better now? :S

Lets say you got 2 cores with 2 threads each, which makes that 4 threads total.
With brain**** you would have gotten the fastest compiling with -j4.
With the normal kernel you would have gotten the fastest compiling with -j5.
With that system, you more or less means that it will choke, but the compiling process will be fine.
Doing something like -j64 means that you CHOKE the entire system, without a single fail. I guess the critic is that running -j2 or -j3 would have done a good enough job on choking the system, which is the actual case. Just running -j5 would have been a good enough demonstration.
Well, I guess it is a really good way of "proving" that the desktop patch really does what it do: Improve the desktop expierience.
Without the patch the movie LAGGED like HECK, along with unsmooth glxgears in the background along with lagging browser.
With the patch suddenly nothing can choke down each other, and I think there is actual a speed improvement on the desktop as well.


rmmst49: [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa) I think, my googlefu is weak, but I hope i managed to hit the right one.

---

### Post by Decatf on 2010-11-17
People are not understanding the conditions under which this patch is useful for.

Rather than spewing more pointless he said she said garbage I'll just copy pasta this here.

> 
On Tue, Nov 16, 2010 at 12:21 PM, Kay Sievers wrote:

The only problem is that ***desktop*** users use ***desktop*** apps, 
which never have a controlling tty.  

This is a ***nerd*** config not helping any regular desktop user. You guys are 
optimizing the system for people who build kernels and watch movies at the 
same time, not for desktop users. Hooking into TTYs works for almost 
nobody sane out there. :)  

It's all fine, no comment on the patch, it's a nice hack. But please stop 
talking about the ***desktop*** here, it has almost nothing to do with 
it.  

Kay> 
On Tue, Nov 16, 2010 at 8:49 PM, **Linus Torvalds** wrote:

> The only problem is that *desktop* users use *desktop* apps, which
> never have a controlling tty.

Yes. And have you noticed people complaining about stuttering while
they run just their desktop app? No.

That's the thing. If you run a web browser and you use a flash player
to view youtube or whatever in it, and only use other interactive
desktop apps anyway, you won't see any problems _regardless_. It's not
like the other desktop app you have open (and is idle, because you're
not touching it) will matter.

Ask yourself who is complaining? _I_ have been complaining for years
about desktop latency. I usually do it in private to developers, but
trust me, I do it. Much of it has been about IO (the whole fsync
fiasco), but some of it has been about the scheduler.

Look at who were trying out Con's patches. They were compiling things
and running games at the same time. That's literally the kind of loads
that people were looking at. Partly because that's the kinds of loads
we haven't been good at. And it's the kind of load that this helps
with.

...
Clearly the majority of users seen in this thread are not running groups of CPU hungry tasks in a terminal like kernel compiling, with all the QQ going on about a PPA.

---

### Post by Pogeymanz on 2010-11-17
Linus -
> 
"Ask yourself who is complaining? _I_ have been complaining for years
about desktop latency. I usually do it in private to developers, but
trust me, I do it. Much of it has been about IO (the whole fsync
fiasco), but some of it has been about the scheduler."

Cool. At least they are talking about the IO stuff.

---

### Post by psusi on 2010-11-17
> **rmmst49 said:**
> unless the whole internet, the kernel people, and the people who have actually tested the patch for themselves are wrong, this patch seems poised to advance linux desktop responsiveness quite a bit, and that's sorely needed. Unless those phoronix videos are fakes, which they aren't, i want to try this patch NOW.

The only test I have seen so far involves make -j64.  I'm pointing out that is not a very real world test.

Thanks Decatf for the great quotes that support my point.

---

### Post by Decatf on 2010-11-17
The Phoronix videos aren't fake but they sure are doing a good job of giving people the wrong idea. I saw some article earlier today heralding this patch and Wayland as some sort of great equalizer that will bring Linux to par with Windows and OSX or something. Thanks a lot Phoronix hype machine...

---

### Post by MarcusW on 2010-11-17
> **psusi said:**
> 
The tabs are not all trying to run at the same time.  You have at most one active one that is busy rendering the page you just loaded up, or playing the video you are watching, and the rest are sleeping.  Not to mention that this patch groups tasks by tty, so it treats all of the chrome tasks the same as any other gui task.  It only firewalls off tasks being run in a terminal.


I often have a lot of chrome processes high up in "top", definitely a lot more than "at most one". ;) Although you're right, I've misunderstood which tasks it "shields" from. Luckily I do run a lot of heavy things in terminals, so it doesn't change much for me.

> 
You don't seem to be using the word photons in a way that makes sense, so I think you misunderstand what it means.

Photon as in photon mapping, meaning it uses up a lot of memory while rendering? :confused: And I do run that in a terminal, so the patch will help there. ;)

---

### Post by BigCityCat on 2010-11-17
I need this for when I have the appearance window and my file manager opened at the same time. I think but I'm not sure but there could possably be some lag there. How can I get the deb? lol

---

### Post by Protocol84 on 2010-11-18
> **czr114 said:**
> I just finished recompiling and testing, and this makes a world of difference, even over the Lucid preemptive. It's a shame I'll be stuck manually building kernels for a long while.  

Any chance I can get that patch file? I have found the original e-mail with the patch in it but I do not know where the file begins or ends.

**never mind I figured it out!!**

---

### Post by Helkaluin on 2010-11-18
This just in. 4 lines in bashrc will do this patch for you in userland.

[http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392)

---

### Post by Ric_NYC on 2010-11-18
Does it improve the speed of Flash videos too?

---

### Post by realzippy on 2010-11-18
> **Helkaluin said:**
> This just in. 4 lines in bashrc will do this patch for you in userland.

[http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392)

[I]Simply edit your own ~/.bashrc and add this to the end:
 
   if [ "$PS1" ] ; then  
           mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
           echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
   fi
 
 Then, as the superuser do this:

   ```
mount -t cgroup cgroup /sys/fs/cgroup/cpu -o cpu
mkdir -m 0777 /sys/fs/cgroup/cpu/user
```
 
 Done. Same effect. However: not crazy.[/I]

EDIT:

modified for ubuntu:
[http://pastebin.com/raw.php?i=sHRYRuAN](http://pastebin.com/raw.php?i=sHRYRuAN)

..does this work only in 2.6.38 ???

---

### Post by psusi on 2010-11-18
> **MarcusW said:**
> 
Photon as in photon mapping, meaning it uses up a lot of memory while rendering? :confused: And I do run that in a terminal, so the patch will help there. ;)

Unless it is a multithreaded app, it won't help.  Even if it is, it won't help nearly as much as it does with make -j64.

> **Helkaluin said:**
> This just in. 4 lines in bashrc will do this patch for you in userland.

[http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392)

Hah!  Perfect!

> **Ric_NYC said:**
> Does it improve the speed of Flash videos too?

No.  It stops videos from lagging and dropping frames if you are crazy enough to try watching them while also doing something as nuts as make -j64 in a terminal window.

---

### Post by FuturePilot on 2010-11-18
Now I'm confused. [http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html]("http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html")

So what is this patch? Good? Bad?

---

### Post by del_diablo on 2010-11-18
> **Ric_NYC said:**
> Does it improve the speed of Flash videos too?

Considering how shitty flash is threaded, it will should improve performance.

---

### Post by del_diablo on 2010-11-18
> **FuturePilot said:**
> Now I'm confused. [http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html]("http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html")

So what is this patch? Good? Bad?

Nah, the guy is just pissed over that the patch is several years late.
And the testing approach, which is just entirely stupid, along with the fact that adding more threads than the system can actually run adds in performance :(
And the guy is pissed over that there will be regressions, hard regressions.
The problem is basically that a combination of:
*The normal way of handeling priorities is by per thread or per load, the result is that when something happens, it can choke the system
*Adding more threads than your system in reality can support increases compile performance, render performance, game performance, etc
*Combine these 2 factors: It has been broken for ages, and nobody has fixed it
What brain**** did is more or less to fix the 2nd issue: If your CPU has 4 threads, you will get the maximum performance from 4 threads, not more than amount of cores. Along with a lot of jamble around other stuff, which essentially also made improvements.
Now, this patch working in tandem with BFS would be ****ing sweet.

---

### Post by realzippy on 2010-11-18
[http://lkml.org/lkml/2010/11/16/392](http://lkml.org/lkml/2010/11/16/392)

....does this work on 2.6.35-xx or does it need 2.6.38 ?

---

### Post by psusi on 2010-11-18
> **FuturePilot said:**
> Now I'm confused. [http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html]("http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html")

So what is this patch? Good? Bad?

Indifferent to slightly bad.

> **del_diablo said:**
> Considering how shitty flash is threaded, it will should improve performance.

Flash isn't multithreaded at all.

> **del_diablo said:**
> Nah, the guy is just pissed over that the patch is several years late.

No, he isn't, and you would know that if you bothered to read it.  He is saying that the patch actually made latency WORSE under normal workloads.

> **del_diablo said:**
> *Adding more threads than your system in reality can support increases compile performance, render performance, game performance, etc

No, it doesn't.  Using drastically more threads than you have cores to run on HURTS performance.

> **del_diablo said:**
> *Combine these 2 factors: It has been broken for ages, and nobody has fixed it
What brain**** did is more or less to fix the 2nd issue: If your CPU has 4 threads, you will get the maximum performance from 4 threads, not more than amount of cores.

Wrong again.  What the patch does is fix it so that the 64 threads in the terminal window are not all being scheduled with the same priority as the other gui windows you have running.

---

### Post by Ric_NYC on 2010-11-18
My question about Flash videos was based on this part of the article on Phoronix:


> It is truly a night and day difference. The 1080p Ogg video now played smoothly a majority of the time when still compiling the Linux kernel with 64 jobs.



Are Flash videos processed in a different way when compared to an Ogg video?

---

### Post by psusi on 2010-11-18
> **Ric_NYC said:**
> M
Are Flash videos processed in a different way when compared to an Ogg video?

For the purposes of this discussion: no.  If you are watching a flash video while running make -j64, this patch will help.  Or you can just not run make -j64, like any sane person would.

---

### Post by Decatf on 2010-11-18
I think people are still missing the a key point which was not mentioned by Phoronix.

That video posted by Phoronix uses a very high end system. That system  has no problem playing flash videos or any other type of video  at all. The lag was induced by applying _extremely_ heavy system load. This system load was run from a terminal.

The second video with the patch enabled shows the kernel preventing the heavy system load (the terminal processes) from hogging all the resources. This allowed the video process enough CPU power to play the video smoothly.

In other words this patch won't "improve the speed" of flash videos. What it will do is prevent flash videos from being slowed down due to terminal processes using CPU.

---

### Post by endotherm on 2010-11-18
> **FuturePilot said:**
> Now I'm confused. [http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html](http://ck-hack.blogspot.com/2010/11/create-task-groups-by-tty-comment.html)

So what is this patch? Good? Bad?

there has been a feud between Linus and Con for a couple years now, because Con's patches for realtime scheduling were not accepted into the kernel. google it if you want to check out the acrimony. Con's patch would have been benifecial for Desktop linux, but would not have helped the multi-user server side nearly so well.  

this patch also alters teh way threads are scheduled CPU time, but by doing it via TTY grouping of threads, the scheduler can optimize thread scheduling for a single user or many running on different TTYs. so it's good for desktop and big iron.

---

### Post by MarcusW on 2010-11-18
> **psusi said:**
> Unless it is a multithreaded app, it won't help.  Even if it is, it won't help nearly as much as it does with make -j64.


What I wrote:
My computer locked down totally some times when rendering an image with multithreading and way too many photons. I expect that won't happen now, so I can enable multithreading again.

---

### Post by Starks on 2010-11-18
> **Thelasko said:**
> I heard 2.6.37, but I'll have to check that...

Edit: [Found it!]("https://launchpad.net/ubuntu/+source/linux-meta/+publishinghistory")

So, we are looking at 11.10 for this update.

Ever since UDS-N, 2.6.38 is the target kernel for 11.04.

[https://lists.ubuntu.com/archives/ubuntu-x/2010-November/001000.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-November/001000.html)

---

### Post by psusi on 2010-11-18
> **MarcusW said:**
> What I wrote:
My computer locked down totally some times when rendering an image with multithreading and way too many photons. I expect that won't happen now, so I can enable multithreading again.

How many threads is the question?  If you are using 64 threads, then this patch will make a big difference.  Of course, you shouldn't be using that many threads, so if you are using a sane number, this patch won't make much difference, and you can get the same results just by running the program with nice.

---

### Post by handy on 2010-11-19
I did the following to run the cgroup stuff, courtesy of Vivek Goyal's post here:

[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)


> Addition to my .bashrc.

[b]if [ "$PS1" ] ; then
        mkdir -m 0700 -p /cgroup/cpu/$$
        echo 1 > /cgroup/cpu/$$/notify_on_release
        echo $$ > /cgroup/cpu/$$/tasks
fi
[/b]
I created one file */bin/rmcgroup* to clean up the cgroup.

[b]#!/bin/bash
rmdir /cgroup/cpu/$1[/b]

And did following to mount cgroup and setup empty group notification. 

I guess what he meant was to add the following to /etc/rc.local which is what I did & it seems to be working.

> 
[b]mount -t cgroup -o cpu none /cgroup/cpu
echo "/bin/rmcgroup" > /cgroup/cpu/release_agent[/b]

And it works fine. Upon ssh to my box, a cpu cgroup is automatically
created and upon exiting the shell, this group is automatically destroyed. 

I haven't played around enough to know if it is helping or not yet.

---

### Post by MarcusW on 2010-11-19
> **psusi said:**
> How many threads is the question?  If you are using 64 threads, then this patch will make a big difference.  Of course, you shouldn't be using that many threads, so if you are using a sane number, this patch won't make much difference, and you can get the same results just by running the program with nice.

I honestly don't know. Enabled multithreading with OpenMP and it does it automatically. Why would I want to control it manually with nice, when the kernel now does the same job for me automatically? ;)

Now what I'm wondering is where you get this magical number "64" from. Is it because the tests were done with -j64? How do you know heavy loads with fewer threads won't get similiar results? Do you have any experience in kernel hacking? Do you have a lot of knowledge about the linux kernel schedular? That the test was done with -j64 does not mean it ONLY does good when compiling exactly what he compiled at exactly 64 threads. 

My netbook gets "overloaded" att maybe ~8threads compiling, that's not a hard number to reach when compiling a couple of projects at the same time. I can't prove the patch will help, but it seems likely.

---

### Post by psusi on 2010-11-19
> **MarcusW said:**
> 
Now what I'm wondering is where you get this magical number "64" from. Is it because the tests were done with -j64?

Yes.

> **MarcusW said:**
> How do you know heavy loads with fewer threads won't get similiar results? Do you have any experience in kernel hacking?

Because I have experience kernel hacking, and understand how this patch modifies the scheduler behavior.  To put it in laymans terms, instead of running task 1, then 2, then 3... then 64, then your gui task, it runs task 1, your gui task, task 2, your gui task, task 3, etc.  You should be able to see why that would have such a remarkable effect when running make -j64, and not much with few threads.

> **MarcusW said:**
> My netbook gets "overloaded" att maybe ~8threads compiling, that's not a hard number to reach when compiling a couple of projects at the same time. I can't prove the patch will help, but it seems likely.

Yes, assuming you have less than 8 cores then 8 threads is enough to keep them all busy and compete for the cpu, so this patch will help, but not nearly as much as it does with 64.  If you have 4 cores though, you should be using 4 threads, not 8, and then this patch won't make hardly any difference.

---

### Post by NightwishFan on 2010-11-19
Would nicing the make -j64 to say 10 have the same end result (more responsive gui) as this patch? I am assuming a cgroup is a slightly different approach though.

---

### Post by MarcusW on 2010-11-19
> **psusi said:**
> Explanation.

Ok, thanks! Yeah, I guess this patch won't do any good for those using their OS like they're supposed to. That doesn't mean it won't do good for me though. :) One thing that always bothers me is when I've started overloading the system with some compiling, rendering etc, it's pretty much too late to do anything since the system won't respond my clicks and "Ctrl+C". Hopefully this will at least let me save the situation, even though a reboot isn't *that bad*.

---

### Post by psusi on 2010-11-19
> **NightwishFan said:**
> Would nicing the make -j64 to say 10 have the same end result (more responsive gui) as this patch?

Approximately.

---

### Post by del_diablo on 2010-11-19
> **NightwishFan said:**
> Would nicing the make -j64 to say 10 have the same end result (more responsive gui) as this patch? I am assuming a cgroup is a slightly different approach though.

Nice would just mean that it won't get thread priority, the effect and outcome is a lot different.
make -j64 is more or less on the default system asking: "Can I eat the system for a while?" and the schedule replies: "Sure".
With nice'd then the schedule replies: "Only if there is time".
With the patch or the modfied bashrc then the 64 threads won't be allowed to eat time when the GUI is suppose to be drawn, or other programs want to do something.

---

### Post by NightwishFan on 2010-11-19
Thanks, I wont worry about this much. If it is included then I can multi-task while compiling I guess. (More than now). I can probably test this easier with stress.

---

### Post by NightwishFan on 2010-11-19
If I run "stress -c 64" I can still use the GUI however it is slow, and playing a 1080p video is impossible. "nice stress -c 64" allows me to use the GUI quite nicely though the video still does not play. Finally "nice -n 20 stress -c 64" 1080p video playback is perfect, which makes me assume that anything on nice 20 is only runnable when nothing else wants to.

My cpu is a dual core intel at 2.22ghz, my kernel is custom compiled 2.6.32 with no preemption, tickless, and 1000hz.

---

### Post by sandyd on 2010-11-19
works awesome.
fglrx doesn't seem to work though, keeps on giving a ld error.
welcome improvement to performance since I use gentoo.
this patch + gallium = awesome performance btw ;)

---

### Post by Oxwivi on 2010-11-19
> **alexan said:**
> ppa? :confused:


Where's the ppa? :confused: :confused:



I want the ppa for it!  :(
+1

---

### Post by realzippy on 2010-11-19
> **Oxwivi said:**
> +1

No ppa,but as easy:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)

---

### Post by NCLI on 2010-11-19
**@psusi:** With all the recent details about how the patch works(Which I would have appreciated if you had provide from the beginning), I guess all I can say is that "It works for me(TM)"

It certainly seems to have improved my desktop performance with heavy tasks going on in the background, Now, whether that s my imagination or a real effect I do not know, since I haven't tested it in any scientifically acknowledgeable way, but it feels like a big difference to me.

I will await broad deployment(Natty) and see what the general reaction is.

---

### Post by Oxwivi on 2010-11-19
> **realzippy said:**
> No ppa,but as easy:

[http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html)
I'd prefer it be the same as one being patched. Linus did say it was tested the same way before being integrated into the kernel.

---

### Post by aktiwers on 2010-11-19
Where can I download this patch?? Been looking everywhere..  Either I am tired or blind..  I don't want the alternative solution, I want the patch :)

---

### Post by Protocol84 on 2010-11-19
> **aktiwers said:**
> Where can I download this patch?? Been looking everywhere..  Either I am tired or blind..  I don't want the alternative solution, I want the patch :)

**EDIT**
where I got it from
[http://marc.info/?l=linux-kernel&m=128978361700898&w=2](http://marc.info/?l=linux-kernel&m=128978361700898&w=2)
**EDIT**

Signed-off-by: Mike Galbraith <efault@gmx.de>

---
 Documentation/kernel-parameters.txt |    2 
 drivers/tty/tty_io.c                |    1 
 include/linux/sched.h               |   19 ++++
 init/Kconfig                        |   12 +++
 kernel/fork.c                       |    5 +
 kernel/sched.c                      |   25 ++++--
 kernel/sched_autogroup.c            |  140 ++++++++++++++++++++++++++++++++++++
 kernel/sched_autogroup.h            |   18 ++++
 kernel/sysctl.c                     |   11 ++
 9 files changed, 224 insertions(+), 9 deletions(-)

Index: linux-2.6/include/linux/sched.h
===================================================================
--- linux-2.6.orig/include/linux/sched.h
+++ linux-2.6/include/linux/sched.h
@@ -509,6 +509,8 @@ struct thread_group_cputimer {
     spinlock_t lock;
 };
 
+struct autogroup;
+
 /*
  * NOTE! "signal_struct" does not have it's own
  * locking, because a shared signal_struct always
@@ -576,6 +578,9 @@ struct signal_struct {
 
     struct tty_struct *tty; /* NULL if no tty */
 
+#ifdef CONFIG_SCHED_AUTOGROUP
+    struct autogroup *autogroup;
+#endif
     /*
      * Cumulative resource counters for dead threads in the group,
      * and for reaped dead child processes forked by this group.
@@ -1931,6 +1936,20 @@ int sched_rt_handler(struct ctl_table *t
 
 extern unsigned int sysctl_sched_compat_yield;
 
+#ifdef CONFIG_SCHED_AUTOGROUP
+extern unsigned int sysctl_sched_autogroup_enabled;
+
+extern void sched_autogroup_create_attach(struct task_struct *p);
+extern void sched_autogroup_detach(struct task_struct *p);
+extern void sched_autogroup_fork(struct signal_struct *sig);
+extern void sched_autogroup_exit(struct signal_struct *sig);
+#else
+static inline void sched_autogroup_create_attach(struct task_struct *p) { }
+static inline void sched_autogroup_detach(struct task_struct *p) { }
+static inline void sched_autogroup_fork(struct signal_struct *sig) { }
+static inline void sched_autogroup_exit(struct signal_struct *sig) { }
+#endif
+
 #ifdef CONFIG_RT_MUTEXES
 extern int rt_mutex_getprio(struct task_struct *p);
 extern void rt_mutex_setprio(struct task_struct *p, int prio);
Index: linux-2.6/kernel/sched.c
===================================================================
--- linux-2.6.orig/kernel/sched.c
+++ linux-2.6/kernel/sched.c
@@ -78,6 +78,7 @@
 
 #include "sched_cpupri.h"
 #include "workqueue_sched.h"
+#include "sched_autogroup.h"
 
 #define CREATE_TRACE_POINTS
 #include <trace/events/sched.h>
@@ -605,11 +606,14 @@ static inline int cpu_of(struct rq *rq)
  */
 static inline struct task_group *task_group(struct task_struct *p)
 {
+    struct task_group *tg;
     struct cgroup_subsys_state *css;
 
     css = task_subsys_state_check(p, cpu_cgroup_subsys_id,
             lockdep_is_held(&task_rq(p)->lock));
-    return container_of(css, struct task_group, css);
+    tg = container_of(css, struct task_group, css);
+
+    return autogroup_task_group(p, tg);
 }
 
 /* Change a task's cfs_rq and parent entity if it moves across CPUs/groups */
@@ -2006,6 +2010,7 @@ static void sched_irq_time_avg_update(st
 #include "sched_idletask.c"
 #include "sched_fair.c"
 #include "sched_rt.c"
+#include "sched_autogroup.c"
 #include "sched_stoptask.c"
 #ifdef CONFIG_SCHED_DEBUG
 # include "sched_debug.c"
@@ -7979,7 +7984,7 @@ void __init sched_init(void)
 #ifdef CONFIG_CGROUP_SCHED
     list_add(&init_task_group.list, &task_groups);
     INIT_LIST_HEAD(&init_task_group.children);
-
+    autogroup_init(&init_task);
 #endif /* CONFIG_CGROUP_SCHED */
 
 #if defined CONFIG_FAIR_GROUP_SCHED && defined CONFIG_SMP
@@ -8509,15 +8514,11 @@ void sched_destroy_group(struct task_gro
 /* change task's runqueue when it moves between groups.
  *    The caller of this function should have put the task in its new group
  *    by now. This function just updates tsk->se.cfs_rq and tsk->se.parent to
- *    reflect its new group.
+ *    reflect its new group.  Called with the runqueue lock held.
  */
-void sched_move_task(struct task_struct *tsk)
+void __sched_move_task(struct task_struct *tsk, struct rq *rq)
 {
     int on_rq, running;
-    unsigned long flags;
-    struct rq *rq;
-
-    rq = task_rq_lock(tsk, &flags);
 
     running = task_current(rq, tsk);
     on_rq = tsk->se.on_rq;
@@ -8538,7 +8539,15 @@ void sched_move_task(struct task_struct
         tsk->sched_class->set_curr_task(rq);
     if (on_rq)
         enqueue_task(rq, tsk, 0);
+}
 
+void sched_move_task(struct task_struct *tsk)
+{
+    struct rq *rq;
+    unsigned long flags;
+
+    rq = task_rq_lock(tsk, &flags);
+    __sched_move_task(tsk, rq);
     task_rq_unlock(rq, &flags);
 }
 #endif /* CONFIG_CGROUP_SCHED */
Index: linux-2.6/kernel/fork.c
===================================================================
--- linux-2.6.orig/kernel/fork.c
+++ linux-2.6/kernel/fork.c
@@ -174,8 +174,10 @@ static inline void free_signal_struct(st
 
 static inline void put_signal_struct(struct signal_struct *sig)
 {
-    if (atomic_dec_and_test(&sig->sigcnt))
+    if (atomic_dec_and_test(&sig->sigcnt)) {
+        sched_autogroup_exit(sig);
         free_signal_struct(sig);
+    }
 }
 
 void __put_task_struct(struct task_struct *tsk)
@@ -904,6 +906,7 @@ static int copy_signal(unsigned long clo
     posix_cpu_timers_init_group(sig);
 
     tty_audit_fork(sig);
+    sched_autogroup_fork(sig);
 
     sig->oom_adj = current->signal->oom_adj;
     sig->oom_score_adj = current->signal->oom_score_adj;
Index: linux-2.6/drivers/tty/tty_io.c
===================================================================
--- linux-2.6.orig/drivers/tty/tty_io.c
+++ linux-2.6/drivers/tty/tty_io.c
@@ -3160,6 +3160,7 @@ static void __proc_set_tty(struct task_s
     put_pid(tsk->signal->tty_old_pgrp);
     tsk->signal->tty = tty_kref_get(tty);
     tsk->signal->tty_old_pgrp = NULL;
+    sched_autogroup_create_attach(tsk);
 }
 
 static void proc_set_tty(struct task_struct *tsk, struct tty_struct *tty)
Index: linux-2.6/kernel/sched_autogroup.h
===================================================================
--- /dev/null
+++ linux-2.6/kernel/sched_autogroup.h
@@ -0,0 +1,18 @@
+#ifdef CONFIG_SCHED_AUTOGROUP
+
+static void __sched_move_task(struct task_struct *tsk, struct rq *rq);
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg);
+
+#else /* !CONFIG_SCHED_AUTOGROUP */
+
+static inline void autogroup_init(struct task_struct *init_task) {  }
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg)
+{
+    return tg;
+}
+
+#endif /* CONFIG_SCHED_AUTOGROUP */
Index: linux-2.6/kernel/sched_autogroup.c
===================================================================
--- /dev/null
+++ linux-2.6/kernel/sched_autogroup.c
@@ -0,0 +1,140 @@
+#ifdef CONFIG_SCHED_AUTOGROUP
+
+unsigned int __read_mostly sysctl_sched_autogroup_enabled = 1;
+
+struct autogroup {
+    struct kref        kref;
+    struct task_group    *tg;
+};
+
+static struct autogroup autogroup_default;
+
+static void autogroup_init(struct task_struct *init_task)
+{
+    autogroup_default.tg = &init_task_group;
+    kref_init(&autogroup_default.kref);
+    init_task->signal->autogroup = &autogroup_default;
+}
+
+static inline void autogroup_destroy(struct kref *kref)
+{
+    struct autogroup *ag = container_of(kref, struct autogroup, kref);
+    struct task_group *tg = ag->tg;
+
+    kfree(ag);
+    sched_destroy_group(tg);
+}
+
+static inline void autogroup_kref_put(struct autogroup *ag)
+{
+    kref_put(&ag->kref, autogroup_destroy);
+}
+
+static inline struct autogroup *autogroup_kref_get(struct autogroup *ag)
+{
+    kref_get(&ag->kref);
+    return ag;
+}
+
+static inline struct autogroup *autogroup_create(void)
+{
+    struct autogroup *ag = kmalloc(sizeof(*ag), GFP_KERNEL);
+
+    if (!ag)
+        goto out_fail;
+
+    ag->tg = sched_create_group(&init_task_group);
+    kref_init(&ag->kref);
+
+    if (!(IS_ERR(ag->tg)))
+        return ag;
+
+out_fail:
+    if (ag) {
+        kfree(ag);
+        WARN_ON(1);
+    } else
+        WARN_ON(1);
+
+    return autogroup_kref_get(&autogroup_default);
+}
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg)
+{
+    int enabled = ACCESS_ONCE(sysctl_sched_autogroup_enabled);
+
+    enabled &= (tg == &root_task_group);
+    enabled &= (p->sched_class == &fair_sched_class);
+    enabled &= (!(p->flags & PF_EXITING));
+
+    if (enabled)
+        return p->signal->autogroup->tg;
+
+    return tg;
+}
+
+static void
+autogroup_move_group(struct task_struct *p, struct autogroup *ag)
+{
+    struct autogroup *prev;
+    struct task_struct *t;
+    struct rq *rq;
+    unsigned long flags;
+
+    rq = task_rq_lock(p, &flags);
+    prev = p->signal->autogroup;
+    if (prev == ag) {
+        task_rq_unlock(rq, &flags);
+        return;
+    }
+
+    p->signal->autogroup = autogroup_kref_get(ag);
+    __sched_move_task(p, rq);
+    task_rq_unlock(rq, &flags);
+
+    rcu_read_lock();
+    list_for_each_entry_rcu(t, &p->thread_group, thread_group) {
+        sched_move_task(t);
+    }
+    rcu_read_unlock();
+
+    autogroup_kref_put(prev);
+}
+
+void sched_autogroup_create_attach(struct task_struct *p)
+{
+    struct autogroup *ag = autogroup_create();
+
+    autogroup_move_group(p, ag);
+    /* drop extra refrence added by autogroup_create() */
+    autogroup_kref_put(ag);
+}
+EXPORT_SYMBOL(sched_autogroup_create_attach);
+
+/* currently has no users */
+void sched_autogroup_detach(struct task_struct *p)
+{
+    autogroup_move_group(p, &autogroup_default);
+}
+EXPORT_SYMBOL(sched_autogroup_detach);
+
+void sched_autogroup_fork(struct signal_struct *sig)
+{
+    sig->autogroup = autogroup_kref_get(current->signal->autogroup);
+}
+
+void sched_autogroup_exit(struct signal_struct *sig)
+{
+    autogroup_kref_put(sig->autogroup);
+}
+
+static int __init setup_autogroup(char *str)
+{
+    sysctl_sched_autogroup_enabled = 0;
+
+    return 1;
+}
+
+__setup("noautogroup", setup_autogroup);
+#endif
Index: linux-2.6/kernel/sysctl.c
===================================================================
--- linux-2.6.orig/kernel/sysctl.c
+++ linux-2.6/kernel/sysctl.c
@@ -382,6 +382,17 @@ static struct ctl_table kern_table[] = {
         .mode        = 0644,
         .proc_handler    = proc_dointvec,
     },
+#ifdef CONFIG_SCHED_AUTOGROUP
+    {
+        .procname    = "sched_autogroup_enabled",
+        .data        = &sysctl_sched_autogroup_enabled,
+        .maxlen        = sizeof(unsigned int),
+        .mode        = 0644,
+        .proc_handler    = proc_dointvec,
+        .extra1        = &zero,
+        .extra2        = &one,
+    },
+#endif
 #ifdef CONFIG_PROVE_LOCKING
     {
         .procname    = "prove_locking",
Index: linux-2.6/init/Kconfig
===================================================================
--- linux-2.6.orig/init/Kconfig
+++ linux-2.6/init/Kconfig
@@ -728,6 +728,18 @@ config NET_NS
 
 endif # NAMESPACES
 
+config SCHED_AUTOGROUP
+    bool "Automatic process group scheduling"
+    select CGROUPS
+    select CGROUP_SCHED
+    select FAIR_GROUP_SCHED
+    help
+      This option optimizes the scheduler for common desktop workloads by
+      automatically creating and populating task groups.  This separation
+      of workloads isolates aggressive CPU burners (like build jobs) from
+      desktop applications.  Task group autogeneration is currently based
+      upon task tty association.
+
 config MM_OWNER
     bool
 
Index: linux-2.6/Documentation/kernel-parameters.txt
===================================================================
--- linux-2.6.orig/Documentation/kernel-parameters.txt
+++ linux-2.6/Documentation/kernel-parameters.txt
@@ -1622,6 +1622,8 @@ and is between 256 and 4096 characters.
     noapic        [SMP,APIC] Tells the kernel to not make use of any
             IOAPICs that may be present in the system.
 
+    noautogroup    Disable scheduler automatic task group creation.
+
     nobats        [PPC] Do not use BATs for mapping kernel lowmem
             on "Classic" PPC cores.

---

### Post by realzippy on 2010-11-19
You also get prepatched kernels from that "Altenative solution [link]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html")" you do not want...just in case you do not want to patch your kernel yourself... :

[I]Update 2: patched kernels (Warning: use these at your own risk!!!) for Ubuntu 10.10:

If you want to go even further and install a patched Kernel, you can download a "200 lines" patched Kernel (for 64bit only!) from HERE (thanks to accumulator @ Phoronix forums).

Also, WebUpd8 reader Scott Franke shared a Kernel he patched with bfs with which he says he gets better performance then with the "200 lines patch". Download:

    * 64bit: 1 and 2 (both .deb files required).
    * 32bit: 1 and 2 (both .deb files required).


Both of the above 2 Kernels are for Ubuntu 10.10 only! Use them at your own risk![/I]

---

### Post by aktiwers on 2010-11-19
Thanks a lot

How would I apply that patch? I saved it in my /usr/src as patch
Do I need to compile it or what to do before applying it?

I'm a noob at this, has never applied a patch like this before..

When I do:
```
 patch /usr/src/patch -p1 --dry-run
```
To test if everything is okay before going further, it simply hangs there forever..

---

### Post by handy on 2010-11-19
You don't have to change your kernel to get the same (actually this has been measured to be faster than the kernel patch) performance.

Adding a few lines at the end of your ~/.bashrc & making a tiny one line .sh file & adding two lines to your /etc/rc.local & you are good to go. Well I was, you may have to make a slight modification for Ubuntu.

[http://lkml.org/lkml/2010/11/16/413](http://lkml.org/lkml/2010/11/16/413)

Doing this in user-land is doing the same thing that the patch does. Only much easier (until the kernel carries the patch by default).

---

### Post by aktiwers on 2010-11-19
I read about that - I was just curios about trying to install the patch.

Either way I am on Debian, I might give it a go then. 

Still interested in how to install the patch though - just for the sake of learning.

---

### Post by KingYaba on 2010-11-19
I'll give this a try on my test machine.

---

### Post by realzippy on 2010-11-20
[COLOR="Red"]http://lkml.org/lkml/2010/11/16/413[/COLOR]

will **NOT** work on Ubuntu,unless you replace "/sys/fs" with "/dev" 

Here is an Ubuntu version:

[http://pastebin.com/raw.php?i=sHRYRuAN](http://pastebin.com/raw.php?i=sHRYRuAN)


credits to Ricardo Ferreira.

---

### Post by handy on 2010-11-20
> **realzippy said:**
> [COLOR="Red"]http://lkml.org/lkml/2010/11/16/413[/COLOR]

will **NOT** work on Ubuntu,unless you replace "/sys/fs" with "/dev" 

Here is an Ubuntu version:

[http://pastebin.com/raw.php?i=sHRYRuAN](http://pastebin.com/raw.php?i=sHRYRuAN)


credits to Ricardo Ferreira.

I'm sure that somewhere back there in the multiple times that I have tried to present this far easier & more efficient option (as opposed to the kernel stuff). That I have mentioned the need for a Ubuntu specific modification.

If Ricardo Ferreira is *the* one who posted it first for those who need it. I say good on him. :)

Wherever the good news comes from is fine by me. :D

Did I mention that I don't need it anyway? ;) (sorry bro' I'm only getting narky 'cause you seem to be? :confused: )

The bottom line as far as this patch is concerned be it kernel based or user-space oriented, is that a very small percentage of Linux distro users will notice any difference at all.

The dev's will & some others too, which is very cool.

---

### Post by realzippy on 2010-11-20
*"...sorry bro' I'm only getting narky 'cause you seem to be?"*

No,absolutely not narky.Why? The bold "NOT" only was because I wanted to
prevent *KingYaba* and other "testers" from running into errors.
Credits to "Ricardo Ferreira "... just a correct indication of source.
Sorry,did not intend bothering you.

---

### Post by Decatf on 2010-11-21
New version of the patch.

**[PATCH v4] sched: automated per session task groups [http://lkml.org/lkml/2010/11/20/91](http://lkml.org/lkml/2010/11/20/91)**

---

### Post by toupeiro on 2010-11-21
Fluid window movement with a kernel patch!  I love it!

... Can the X witch-hunt stop now? :P

*ducks*

---

### Post by Protocol84 on 2010-11-22
I have heard allot of talk about how the regular user will get no benefit from this patch (I used the shorter one that can be done in userspace). I can personally say that I have seen a good improvement in my computer with this patch.

The main instance that I saw improvement was when I was simply playing Vega Strike and browsing the Vega Strike Wiki. Before the patch browsing the web while playing was arduous at best, even scrolling was extremely sluggish. 

After the patch I now see almost no slowing down of firefox while I am playing the game.

Before the patch I could play 1080p video on youtube but any time my computer would think for anything else the video would stutter, now after the patch it never skips a frame.

I, personally, am very glad that I came across this patch and applied it to my system, and cannot wait to see what further revisions of it bring.

---

### Post by corkman on 2011-01-08
I am using an old intel dual core, the one without the hardware support for virtuailisation, and find myself running a virtualbox machine with hardy with the following running inside it: php-cgi, lighty webserver, mysql and built in support in php for sqlite3, imagick, curl and a few others essential librarries for web dev.  Eclipse is also open in my real machine, Chromium, Firefox, and LibreOffice Calc and I swith back and forth the whole time.

Some observations, using the desktop cube, things are much snappier, Eclipse is a lot less laggy when switching apps and redraws now almost instantly and my three year old laptop has now gained a whole new lease of life as it is now usable for daily working needs.

Total savings now as a result of a few lines of bash configuration is approx. 500 pounds sterling :)

So thank you to the people who found this patch, refined it and made it available!:popcorn:

---

### Post by MoebusNet on 2011-01-08
A question from those of us running antique/low spec machines: will this make any difference to the single-core users?

In my case I'm running a laptop with a Pentium M processor at 1.4 Ghz (state of the art circa 2002). How will this affect my performance?

---

### Post by corkman on 2011-01-08
> **MoebusNet said:**
> A question from those of us running antique/low spec machines: will this make any difference to the single-core users?

In my case I'm running a laptop with a Pentium M processor at 1.4 Ghz (state of the art circa 2002). How will this affect my performance?

Well I didnt use the kernel patch, just the bash configuration as detailed and that was a huge improvemet as I posted.  Try that as it is fairly easy to do and you will notice straight away if it works.  My compiz cube went from slow and unresponsive to weeeeeee..... :)
Not a scientific test, but then again it has worked for me, the usage case scenario I am most interested in ;-):popcorn:

---

### Post by psusi on 2011-01-08
> **corkman said:**
> 
Some observations, using the desktop cube, things are much snappier, Eclipse is a lot less laggy when switching apps and redraws now almost instantly and my three year old laptop has now gained a whole new lease of life as it is now usable for daily working needs.


You would get the same result by simply lowering the priority of your cpu hogging virtual machine, which is all this patch does.

> **MoebusNet said:**
> A question from those of us running antique/low spec machines: will this make any difference to the single-core users?


It has no impact on performance whatsoever.  What it does is make tasks more *responsive* than they otherwise would be when there are a bunch of tasks on another terminal trying to hog the cpu.

---

### Post by ki4jgt on 2011-01-08
I never got why backports existed. I tried to use backports and they never did what they were supposed to.

---

### Post by corkman on 2011-01-08
> **psusi said:**
> You would get the same result by simply lowering the priority of your cpu hogging virtual machine, which is all this patch does.



It has no impact on performance whatsoever.  What it does is make tasks more *responsive* than they otherwise would be when there are a bunch of tasks on another terminal trying to hog the cpu.

You maybe right, I am just a user of Ubuntu, not a systems programer, just a hobbyist with limited time and abilities and this works for me.  
But I do thank you for your observations about that if I reniced the process, however I would have spent ages renicing this, renicing the other, or I can just use an automated approach that works. i will try renicing now that I can compare before and after values of the processes I am interested in.

I go with what is easiest for me as a rule.:D

---

