---
title: "Let's boot with Upstart (GDM ready in 15s)"
date: 2008-03-17
forum: The Cafe
---

### Post by jdong on 2008-03-17
I got bored and rewrite my entire system to boot up with Upstart. Yes, I rewrote all jobs, essentially wrapping them to call init scripts individually and tweaking the dependencies correctly.


**Short Statistics:**
Time spent hacking: 5+ hours. Ran into a lot of snags getting udev and filesystem mount ordered correctly, and each time I failed at that it meant needing a livecd!


The Victim: Me. Err, oh you meant the computer: Macbook Core 2 Duo 2.16, 2GB RAM, running Hardy.

Enjoyment: Infinite. This kind of nerdy thing keeps me going.

**Stopwatch/Visual statistics**:
I'll get to bootchart in a moment, but bootchart doesn't tell the whole story -- what bootchart calls a bootup time and what the user sees as the bootup time are two entirely different things. These boot times are from a stopwatch from GRUB to login chime:

Native Upstart: **18s**

SysV Upstart: 30s

**Bootchart Stats:**

Native Upstart: (**22s**) [http://jdong.mit.edu/~jdong/macbook/bootchart-upstart.png](http://jdong.mit.edu/~jdong/macbook/bootchart-upstart.png)

SysV Upstart: (27s) [http://jdong.mit.edu/~jdong/macbook/bootchart-sysv.png](http://jdong.mit.edu/~jdong/macbook/bootchart-sysv.png)


**Observations:**

(1) Note how slow my laptop hard drive is. Around 12MB/s is its peak read speeds. If I tried this with a powerful desktop hard drive, the 10 second long "readahead-list" could be shaved to 5 seconds or less.

(2) **Ignore the first 17s of both bootup charts for the time being**: Time spent probing modules and slurping readahead cannot be optimized by parallelized startup and are more or less hardware and kernel limitations on bootup speed. Focus on what's after the big blue trapezoid @ 15s: The actual time it took to set up dbus, hal, avahi, GDM, anacron, sysklog, and other system services. It took **5 seconds** to do all of that on Upstart while SysV took **over 10s**. That's effectively doubling the speed at which services are coming up. In addition, notice how Upstart was more consistently able to break the one-core barrier of CPU usage.


**The event.d:**
For educational purposes, here's how I wrote my upstart events: [http://jdong.mit.edu/~jdong/event.d.tar.gz](http://jdong.mit.edu/~jdong/event.d.tar.gz)

You're welcome to play with it all you want, but **DO IT ON AN EXPERIMENTAL BOX**. It's extremely easy for one typo or logic error to result in an unbootable system.


**EDIT**

As a proof-of-concept, I "defragged" (rewrote rapidly) all the files readahead identified as being used at bootup, and got peak IO to around 15MB/s and upstart boot time to **19s by bootchart**

EDIT 2: Youtube video of bootup: (note how rough around the edges it is :D)
[http://www.youtube.com/watch?v=cY8MWwbESy4](http://www.youtube.com/watch?v=cY8MWwbESy4)

Bootchart for this bootup: [http://jdong.mit.edu/~jdong/macbook/hardy-upstart-defragged.png](http://jdong.mit.edu/~jdong/macbook/hardy-upstart-defragged.png)

EDIT 3: After some requests I am posting some dependency diagrams of my boot:
[http://jdong.mit.edu/~jdong/macbook/depchart/upstart-dep.png](http://jdong.mit.edu/~jdong/macbook/depchart/upstart-dep.png)

For comparison, SysV: [http://jdong.mit.edu/~jdong/macbook/depchart/sysv-dep.png](http://jdong.mit.edu/~jdong/macbook/depchart/sysv-dep.png)

For the most part it fans out massively parallel quite well, which is encouraging news. Now, to optimize the longest chain length....

You can generate this diagram on your own system by grabbing [http://jdong.mit.edu/~jdong/macbook/depchart/depchart.py](http://jdong.mit.edu/~jdong/macbook/depchart/depchart.py) and [http://jdong.mit.edu/~jdong/macbook/depchart/depchart-sysv.py](http://jdong.mit.edu/~jdong/macbook/depchart/depchart-sysv.py)

They don't come with manuals; figure it out :D

---

### Post by phrostbyte on 2008-03-17
Wow, if these speed boosts are correct, that is friggen amazing. This needs to be added to Intrepid so badly. I mean like it should be one of the major focuses to get a stable event based bootup up.

---

### Post by Penguin Power on 2008-03-17
John, you need a hobby. One that involves interaction with other humans.

---

### Post by DoktorSeven on 2008-03-17
Honestly, I never was interested in this sort of thing.  For Windows, maybe, where reboots are common and frequent, shaving time off of booting is important, but I almost never reboot Linux, and if I did, I really don't mind a few extra seconds.

I guess it's one of those "why not" things, because if it can be faster, you might as well make it faster, but I've just never been too interested. 

:)  Nice results, though.

---

### Post by jdong on 2008-03-17
I added a youtube of the upstart bootup process so one can get a feel for what kind of bootup time it is. It definitely feels noticeably faster than stock Hardy boot.

Note that all services that are a part of the regular bootup sequence are started up (and a few more for this laptop to set up wireless and power saving and webcam), I **did not perform any trickery** involving trimming/stripping down services!

---

### Post by bruce89 on 2008-03-17
> **Penguin Power said:**
> John, you need a hobby. One that involves interaction with other humans.

I'm screwed then.

> **DoktorSeven said:**
> Honestly, I never was interested in this sort of thing.  For Windows, maybe, where reboots are common and frequent, shaving time off of booting is important, but I almost never reboot Linux, and if I did, I really don't mind a few extra seconds.


I've never understood this practice, it's wasteful of electricity.

---

### Post by RAV TUX on 2008-03-17
> **jdong said:**
> I got bored and rewrite my entire system to boot up with Upstart. Yes, I rewrote all jobs, essentially wrapping them to call init scripts individually and tweaking the dependencies correctly.


**Short Statistics:**
Time spent hacking: 5+ hours. Ran into a lot of snags getting udev and filesystem mount ordered correctly, and each time I failed at that it meant needing a livecd!


The Victim: Me. Err, oh you meant the computer: Macbook Core 2 Duo 2.16, 2GB RAM, running Hardy.

Enjoyment: Infinite. This kind of nerdy thing keeps me going.

**Stopwatch/Visual statistics**:
I'll get to bootchart in a moment, but bootchart doesn't tell the whole story -- what bootchart calls a bootup time and what the user sees as the bootup time are two entirely different things. These boot times are from a stopwatch from GRUB to login chime:

Native Upstart: **18s**

SysV Upstart: 30s

**Bootchart Stats:**

Native Upstart: (**22s**) [http://jdong.mit.edu/~jdong/macbook/bootchart-upstart.png]("http://jdong.mit.edu/%7Ejdong/macbook/bootchart-upstart.png")

SysV Upstart: (27s) [http://jdong.mit.edu/~jdong/macbook/bootchart-sysv.png]("http://jdong.mit.edu/%7Ejdong/macbook/bootchart-sysv.png")


**Observations:**

(1) Note how slow my laptop hard drive is. Around 12MB/s is its peak read speeds. If I tried this with a powerful desktop hard drive, the 10 second long "readahead-list" could be shaved to 5 seconds or less.

(2) **Ignore the first 17s of both bootup charts for the time being**: Time spent probing modules and slurping readahead cannot be optimized by parallelized startup and are more or less hardware and kernel limitations on bootup speed. Focus on what's after the big blue trapezoid @ 15s: The actual time it took to set up dbus, hal, avahi, GDM, anacron, sysklog, and other system services. It took **5 seconds** to do all of that on Upstart while SysV took **over 10s**. That's effectively doubling the speed at which services are coming up. In addition, notice how Upstart was more consistently able to break the one-core barrier of CPU usage.


**The event.d:**
For educational purposes, here's how I wrote my upstart events: [http://jdong.mit.edu/~jdong/event.d.tar.gz]("http://jdong.mit.edu/%7Ejdong/event.d.tar.gz")

You're welcome to play with it all you want, but **DO IT ON AN EXPERIMENTAL BOX**. It's extremely easy for one typo or logic error to result in an unbootable system.


**EDIT**

As a proof-of-concept, I "defragged" (rewrote rapidly) all the files readahead identified as being used at bootup, and got peak IO to around 15MB/s and upstart boot time to **19s by bootchart**

EDIT 2: Youtube video of bootup: (note how rough around the edges it is :D)
[http://www.youtube.com/watch?v=cY8MWwbESy4](http://www.youtube.com/watch?v=cY8MWwbESy4)

Awesome work John!

---

### Post by jdong on 2008-03-17
I should also add, there's still plenty of room for improvement:

(1) The dependencies were originally tweaked to get the keyboard up and working ASAP because I ran into a lot of *cough* issues recovering from failed bootups during testing phase. Holding up bootup until udev is triggered is probably costing at least a second or two.

(2) Readahead takes nearly 10secs by itself. I'm SURE I can trim that down a bit.

(3) I'm still calling init scripts from upstart. In other words, rather than upstart telling sysvinit to "start up everything in runlevel2 in order" as by default, I am having upstart control the starting of each job individually, and the way I've set up how one job relates to another means that over 10 jobs can boot in parallel at a time. However, If I further switch to a fully upstart based solution,  I can bypass starting a shell and sourcing all those init files.

---

### Post by macogw on 2008-03-17
> **DoktorSeven said:**
> Honestly, I never was interested in this sort of thing.  For Windows, maybe, where reboots are common and frequent, shaving time off of booting is important, but I almost never reboot Linux, and if I did, I really don't mind a few extra seconds.

laptops.

---

### Post by RAV TUX on 2008-03-17
> **macogw said:**
> laptops.
Exactly.

---

### Post by jdong on 2008-03-17
Intelligent service management is more about speed -- it's about getting the ordering right too.

There's a few servers that I manage that do a LOT of stuff and their bootup usually takes 5 to 10 minutes (even something like a home NAT gateway can take 2 or 3 minutes to boot up). Being able to shave that down to 1 or 2 minutes (which is entirely possible with the help of Upstart parallelizing services) can be a big deal if you unexpectedly have to boot it up, like after a power outage.

In addition, Upstart makes writing jobs a lot easier than SysV init. Rather than guessing a bootup order number, you get to simply specify what services your service depends on, and Upstart will automatically find the optimal order to start everything up.

---

### Post by Arkenzor on 2008-03-17
[QUOTE="macogw"]laptops[/QUOTE]

Only thing that matters with my laptop is hibernate/restore time, I only reboot for real at most once a month.

---

### Post by jdong on 2008-03-17
I added some Graphviz generated dependency diagrams comparing SysV to Upstart boot. It should be immediately obvious why Upstart is preferrable.

---

### Post by yatt on 2008-03-17
This news brings a smile to my face. I shut my desktop down at least once a day, and my laptop several times a day.

---

### Post by jdong on 2008-03-19
Would there be any interest (both "victims" (testers/users) and developers/hackers) to form a Launchpad group or project to put out an Upstart modified version of Hardy?

I'd be more than happy to contribute towards hacking something like that, and I have a feeling I'm not the only one interested in concurrent bootup technology. It will likely be orthogonal to the Intrepid upstart effort, as Upstart 0.5 for Intrepid has a different syntax rulefile than Hardy, but I think for Hardy we can make a community Upstart modification as a just-for-fun thing.

---

### Post by notwen on 2008-03-19
The improvement time is pretty impressive.  Be sure to keep us up-to-date if you do start a project.  I'd gladly try this on one of my tinker boxes.  =]

---

### Post by smbm on 2008-03-19
> **jdong said:**
> Would there be any interest (both "victims" (testers/users) and developers/hackers) to form a Launchpad group or project to put out an Upstart modified version of Hardy?

I'd be more than happy to contribute towards hacking something like that, and I have a feeling I'm not the only one interested in concurrent bootup technology. It will likely be orthogonal to the Intrepid upstart effort, as Upstart 0.5 for Intrepid has a different syntax rulefile than Hardy, but I think for Hardy we can make a community Upstart modification as a just-for-fun thing.

I'm in. How can I help?

---

### Post by jdong on 2008-03-19
> **smbm said:**
> I'm in. How can I help?

Well here's a quick rough braindump:


Big Picture:
Get a LiveCD of an Upstart-based Hardy rolled so testers can hop in more easily than unpacking event.d tarballs.

I think Hardy has "solidified" enough that changes from now to its release will likely not affect us at the bootup level, so work can begin relatively soon.

First-Level TODOs:

(1) Finish implementing all bootup jobs. So far I've only done about 90% of the rcS/rc2 scripts, basically only the ones that are absolutely crucial to a proper bootup. Finishing these should be trivial.

(2) Remove ugly hacks. On my local event.d's recently I've been trying some very greedy hacks to pump up boottime, including modifying write cache behavior. This hasn't helped too much (1-2s improvement at most) towards a faster bootup but really are quite ugly/unprofessional. Let's remove this.

(3) Find some maintainable way of remastering a LiveCD with this event.d. So far I'm considering just a  script that empties out and replaces event.d on the livefs. A package would be more elegant, but I'm not sure what benefits that'll actually provide if any.

(4) Bzr branches of everything. I'm already in the process of making bzr branches of my bootup scripts; I just want to make sure there's no blatantly obvious errors or sensitive info before pushing it onto Launchpad.

Second-Level TODOs:

(1) Set up some Wiki pages
(2) Document basic init->upstart conversion process (should be trivial)
(3) After rough images work, probably a bit of PR such as ubuntu-devel-discuss
(4) Address how new init scripts are handled. Currently, we are ignorant of their presence. We should either detect+notify users of unhandled init scripts or automatically convert them to Upstart jobs.
(5) Address undoing these hacks
(6) Address migrating an existing system to Upstart
(7) Address debugging and logging of failures. Currently, logging leaves a lot to be desired.

---

### Post by jdong on 2008-03-19
Oh yeah, first matter of business: **A NAME**! In IRC earlier I joked about naming the project "UpHard" and all our scripts and products along that "theme" but for obvious reasons I'd probably get in a lot of trouble for doing that :D


I was thinking we'd call our distro UpHack and our team the UpHackers, but other names are welcome. I'd like the name to bluntly tell potential users how insanely risky all this is (that is, rewriting the bootup mechanism) and that it's entirely unsupported and for fun.

---

### Post by smbm on 2008-03-19
> **jdong said:**
> Well here's a quick rough braindump:


Big Picture:
Get a LiveCD of an Upstart-based Hardy rolled so testers can hop in more easily than unpacking event.d tarballs.

I think Hardy has "solidified" enough that changes from now to its release will likely not affect us at the bootup level, so work can begin relatively soon.

First-Level TODOs:

(1) Finish implementing all bootup jobs. So far I've only done about 90% of the rcS/rc2 scripts, basically only the ones that are absolutely crucial to a proper bootup. Finishing these should be trivial.

(2) Remove ugly hacks. On my local event.d's recently I've been trying some very greedy hacks to pump up boottime, including modifying write cache behavior. This hasn't helped too much (1-2s improvement at most) towards a faster bootup but really are quite ugly/unprofessional. Let's remove this.

(3) Find some maintainable way of remastering a LiveCD with this event.d. So far I'm considering just a  script that empties out and replaces event.d on the livefs. A package would be more elegant, but I'm not sure what benefits that'll actually provide if any.

(4) Bzr branches of everything. I'm already in the process of making bzr branches of my bootup scripts; I just want to make sure there's no blatantly obvious errors or sensitive info before pushing it onto Launchpad.

Second-Level TODOs:

(1) Set up some Wiki pages
(2) Document basic init->upstart conversion process (should be trivial)
(3) After rough images work, probably a bit of PR such as ubuntu-devel-discuss
(4) Address how new init scripts are handled. Currently, we are ignorant of their presence. We should either detect+notify users of unhandled init scripts or automatically convert them to Upstart jobs.
(5) Address undoing these hacks
(6) Address migrating an existing system to Upstart
(7) Address debugging and logging of failures. Currently, logging leaves a lot to be desired.

Golly.

A fair bit of that sounded like sorcery/black magic to me!

Is you're setup pretty standard? Could I just import all your scripts and give it a blast. Is that advisable.

I may need some help implementing some of this stuff. As I've no idea at all about it. I'm keen to learn though.

As soon as you've sorted the name (I'll put my thinking hat on) and we can meet in IRC (for help) I'll get cracking.

---

### Post by jdong on 2008-03-19
> **smbm said:**
> Golly.

A fair bit of that sounded like sorcery/black magic to me!



Sorry I didn't mean to direct all that at you :D I was just trying to make everyone who is interested aware of some of the things we'd have to do.

I've registered UpHack in Launchpad: [https://edge.launchpad.net/uphack](https://edge.launchpad.net/uphack) and pushed up two bzr branches, including my event.d.

> 
Is you're setup pretty standard? Could I just import all your scripts and give it a blast. Is that advisable.


That's exactly how I plan on spinning the first LiveCD. The most obvious problem I can see is that Readahead needs to be disabled when booting off the LiveCD; I think I'll have the readahead script grep for the bootup arguments indicative of a LiveCD and abort if found.

Before I spin a livecd, I'd like to reimplement all my event.d files in reference to a very standard (i.e. freshly installed Hardy) system.


> 

I may need some help implementing some of this stuff. As I've no idea at all about it. I'm keen to learn though.


Sure. I don't expect anyone to understand what I'm saying right now until I set up some rudimentary documentation on a wiki page. Not only is Upstart very sparsely documented, a lot of these scripts are the creation of myself with zero documentation whatsoever.

I'm a bit busy these few days, but expect sometime over the weekend to get another big push of data.

---

### Post by bobbocanfly on 2008-03-19
Would definately give this a test on a spare partition, might even be able to help out in some way. That boot speed is brilliant.

---

### Post by smbm on 2008-03-19
> **jdong said:**
> Sorry I didn't mean to direct all that at you :D I was just trying to make everyone who is interested aware of some of the things we'd have to do.

I've registered UpHack in Launchpad: [https://edge.launchpad.net/uphack](https://edge.launchpad.net/uphack) and pushed up two bzr branches, including my event.d.



That's exactly how I plan on spinning the first LiveCD. The most obvious problem I can see is that Readahead needs to be disabled when booting off the LiveCD; I think I'll have the readahead script grep for the bootup arguments indicative of a LiveCD and abort if found.

Before I spin a livecd, I'd like to reimplement all my event.d files in reference to a very standard (i.e. freshly installed Hardy) system.




Sure. I don't expect anyone to understand what I'm saying right now until I set up some rudimentary documentation on a wiki page. Not only is Upstart very sparsely documented, a lot of these scripts are the creation of myself with zero documentation whatsoever.

I'm a bit busy these few days, but expect sometime over the weekend to get another big push of data.

Cool.

I'll keep an eye on the Launchpad page.

---

### Post by mech7 on 2008-03-19
hmm with me the booting is fast... its the logging in and actually loading the desktop thats soooo slow :p

---

### Post by jdong on 2008-03-19
> **mech7 said:**
> hmm with me the booting is fast... its the logging in and actually loading the desktop thats soooo slow :p

I'm working on a way to "fix" that too :) but it's unrelated

---

### Post by bash on 2008-03-19
Wow really neat work. Things like that really awake the geek in me. I'm really curious about this and always found boot up to be something you could definitly tweak out a couple of seconds. Now I don't know anything about hacking my way around the whole startup process. But I quite like to learn (by doing ;) ) it. Except the next 3 weeks I'm packed with big uni papers. Guess no fun for me.

What comes to mind though is that you basically have to modify every process that is started during booting. Now you got that setup for your system and the idea of a LiveCD is great as well. But wouldn't you run intro troubles if the user would start the install others programms that get started at boottime. For example I have got a mysql server running on my desktop box because I also use it as a MythTV setup. Wouldn't these programs "just come" with the "old way" of booting. Or can upstart be setup more generally so that it doesn't matter in the end what services/demons your start during boottime? (This is me asking, not knowing the whole bootup system particularly good)

---

### Post by jdong on 2008-03-19
> **bash said:**
> . But wouldn't you run intro troubles if the user would start the install others programms that get started at boottime. For example I have got a mysql server running on my desktop box because I also use it as a MythTV setup. Wouldn't these programs "just come" with the "old way" of booting. Or upstart be setup more generally so that it doesn't matter in the end what services/demons your start during boottime? (This is me asking, not knowing the whole bootup system particularly good)

That was what I meant about #4 on the 2nd level TODO. Currently, you're right, that job would be ignored. We need to either:

(1) Look in rc2.d for scripts we don't know about, and notify the user with information on what he can do to get Upstart to recognize them.

(2) #1, but automatically convert it to an Upstart job

(3) At the end of Upstart boot, execute all SysV jobs that aren't Upstart Jobs sequentially.



I need to think this through more, as each of those options is appealing in its own way.

---

### Post by macogw on 2008-03-20
> **jdong said:**
> That was what I meant about #4 on the 2nd level TODO. Currently, you're right, that job would be ignored. We need to either:

(1) Look in rc2.d for scripts we don't know about, and notify the user with information on what he can do to get Upstart to recognize them.

(2) #1, but automatically convert it to an Upstart job

(3) At the end of Upstart boot, execute all SysV jobs that aren't Upstart Jobs sequentially.



I need to think this through more, as each of those options is appealing in its own way.

I like #3.  The other two...automagic generation of config files...sound a bit scary.

I'm totally up for playing with this though.  I should take a dpkg dump first though, so I can do a set-selections and reinstall my packages if reinstalling Ubuntu becomes necessary

---

### Post by igknighted on 2008-03-20
Why not a combination of all three?  Give the user a setting to be notified of how to change it (#1) or to have it automagically converted (#2).  Then in the meantime #3 could be a default behavior (which I suppose should also be able to be turned off) that would boot the scripts that haven't been added yet.

---

### Post by Meson on 2008-03-20
Is it possible to just implement this as rc3,4,or 5?  It should make it easier to test on the same exact system rather than installs on seperate partitons (which have different radial distances along the disk - dunno if that is negligable or not).

---

### Post by jdong on 2008-03-20
> **Meson said:**
> Is it possible to just implement this as rc3,4,or 5?  It should make it easier to test on the same exact system rather than installs on seperate partitons (which have different radial distances along the disk - dunno if that is negligable or not).

Then you do not get the benefit of Upstart during rcS.

---

### Post by jdong on 2008-03-21
[http://bazaar.launchpad.net/~uphackers/uphack/uphack-tools/files](http://bazaar.launchpad.net/~uphackers/uphack/uphack-tools/files)

Muahaha, phase 2 of world domination:

I've begun work on an automatic sysv to upstart conversion script.

So far, it's able to find all rcS and rc2 jobs and dump them into event.d jobs

Now, I just need to go thru and "quirk" the jobs that have special dependencies (i.e. most of the initial bootup stuff, and hal->dbus->gdm stack) and we've got an automatic upstart converter.


**WARNING**: Right now using this tool will likely result in an unbootable system. It writes event.d to the current directory and refuses to overwrite existing event.d directories so you can preview what it'd do, but I purposely did not allow it to apply those changes to the system. Do not run it as root for security reasons.

---

### Post by Buffalo Soldier on 2008-04-02
jdong,

How's your world domination plan? Any updates for your fans here?

---

### Post by tjwallace on 2008-07-01
Any progress?

---

### Post by david_lynch on 2008-08-19
> **bruce89 said:**
> 
I've never understood this practice, it's wasteful of electricity.
If you want to save electricity you can sleep or suspend. I keep my linux servers on 24/7 though, since some jobs never end.

---

### Post by ShirishAg75 on 2008-10-27
Any updates on the same jdong?

---

### Post by gaspard.leon on 2008-10-27
Hi,

I'm also hoping/waiting to hear of jdong's progress on this front (if any)

Also exciting: has anyone read this article regarding 5 second linux boot: [http://lwn.net/Articles/299483/](http://lwn.net/Articles/299483/)

it would be interesting to redo some of the optimizations they achieved (with ubuntu instead of fedora..) even 10 to 20 seconds would be a huge improvement over the usual 60 to 150 second boots a lot of us are seeing.

personally on my old AthlonXP machine, I could never suspend (even with Windows) but I forgo AGP support in favor of using suspend because it's so sweet "booting" in several seconds.

Under hardy 8.04.1 using nvidia drive, I added" "Option" "NvAGP" "0" and now I can suspend!!

anyway good luck all

---

### Post by bluk on 2008-11-12
i installed upstart 0.5

following patch is needed to make it (upstart 0.5) work WITHOUT INITRAMDISK

add it before *setsid ();* in init/main.c
```

        /* Mount /proc
         * hack needed when not running initramfs
         */
        system ("mount /proc");

```
compile with *debian/rules binary* and install the packages written to ..

BEFORE REBOOTING with the new upstart 0.5:
/etc/init.jobs.d => /etc/event.d (new location for upstart jobs)
[LIST]
[*]sudo mkdir /etc/init
[*]sudo ln -s /etc/event.d /etc/init/jobs.d
[/LIST]

i slightly changed jdong's script to reflect new syntax and introduce adapted dependencies (note that i commented out many services that i do not run (no code line has been deleted, only commented out))
- see attachment upconv.py -

then i ran
*./upconv.py /etc/rc2.d/*
and copied anything from *jobs.d/* to */etc/init/jobs.d/*

and applied some manual tweaks:
comment out cups #start on .. (i seldomly need printing)
*rm /etc/init/jobs.d/{loadcpufreq,console_screen_kbd_sh,readahead,rc2,rcS}*
(loadcpufreq removed because it's statically compiled into my kernel, readahead because my X301's flash-drive doesn't need it and console_screen_kbd_sh because it's superseded by setupcon and not used anyway)
also remove rc2 and rcS as i now have native upstart boot i don't want these to be loaded anymore (some services don't like being started twice either)

so this is my *ls /etc/init/jobs.d*
```

acpid               cups                   mountall_sh       rc6                sysklogd
atd                 dbus                   mountdevsubfs_sh  rc-default         system_tools_backends
avahi_daemon        gdm                    mountkernfs_sh    rc_local           tty1
bluetooth           hal                    mountoverflowtmp  rcS-sulogin        tty2
bootmisc_sh         hostname_sh            mtab_sh           readahead_desktop  tty3
checkfs_sh          hwclockfirst_sh        networking        resolvconf         udev
checkroot_sh        hwclock_sh             NetworkManager    rmnologin          udev_finish
console_setup       keyboard_setup         policykit         screen_cleanup     urandom
control-alt-delete  klogd                  procps            ssh                x11_common
cpufrequtils        loopback               rc0               stop_readahead
cron                mountall_bootclean_sh  rc1               sulogin

```

the dependency graph is included as attachment. to generate one yourself use jdong's script with
```
./depchart.py /etc/init/jobs.d/ > depchart-upstart-new.graph && dot -Tpng -o upstart-new.png depchart-upstart-new.graph && eog upstart-new.png
```

**NOTE:**
If you ever run into an unbootable system add *init=/bin/bash* to the kernel command line in GRUB and when booted into bash run */etc/init.d/rcS*
you'll be able to start fixing from there..

enjoy fast booting and thanks for the initial effort! :)

---

### Post by Sam Lars on 2009-03-06
Thanks for all of the info, bluk.
I finally got a build to work in [my PPA]("https://launchpad.net/~nattgew/+archive/ppa") for Upstart 0.5.1
I may try installing it sometime, but I don't really trust it yet.  Could anyone tell me if that package should be good?  I'm not too experienced with packaging, and this is kind of an important thing to play around with.
Also, question:
You say the patch is needed for "WITHOUT INITRAMDISK"
Is this something specific to your setup that you don't use initramdisk or is this for Ubuntu in general?  In other words, should I make that change when I build the package myself?

---

### Post by dragos240 on 2009-03-06
this should be used in jaunty

---

### Post by CJ Master on 2009-03-07
> **dragos240 said:**
> this should be used in jaunty

I believe it is.

---

### Post by dragos240 on 2009-03-08
now that sounds interesting....

---

### Post by linuxisevolution on 2009-03-08
Intrepid boots in 10 seconds by default on my family system, and me with Better specs running hardy is slower!

Family system: AMD 5000+ 2.6ghz X2 2gb 800mhz ram 500gb hdd ( 250+250gb).
Boot time: 10 seconds

My system: Intel E4500 3ghz 4gb 735mhz ram 320gb hdd (250gb + 80gb)
Boot time: 45 seconds :(

---

### Post by Sam Lars on 2009-03-08
So I tried this out and had no luck with either the original post or the one with the new version, though I didn't try installing the new version.
It kept stopping after saying Starting NFS common... and had a bunch of file system check errors.  It looked like it was running through things more than once and erroring out.
I ended up messing up my boot process a bit, but at least I got it working again.

I upgraded to Jaunty, and found it to be faster on boot.  I didn't install bootchart, it's a testing installation.
Its /etc/event.d looks the same as Intrepid's, so it's not using Upstart like it's mentioned here.

---

### Post by Starks on 2009-03-09
So... Is there anyway to test upstart 0.5 through the relative safety of a PPA or idiot-proof walkthrough?

---

### Post by Sam Lars on 2009-03-09
What bluk posted is pretty good.
Keep in mind that when messing with something like this, safe is definitely not a word to describe it.
Ubuntu splits the Upstart package up into other packages that provide the rc scripts for upstart to run and the contents of the /etc/event.d (or /etc/init/jobs.d) that Upstart uses.  I was able to package Upstart 0.5, but its contents conflicted with the other packages Ubuntu has for it.  I'm not sure how to proceed, getting a package to build at all was a first for me. :)
If you're really interested, you can go ahead and try it.  I think I finally figured out where my problems were coming from and what was going on.
If you run into something, start a thread in a support forum... I kind of forgot this is in the Community Cafe.

---

### Post by Starks on 2009-03-09
I only ask because the latest upstart bzr had temporarily hosed my system.

---

### Post by ghindo on 2009-07-12
Now that Karmic is running Upstart 0.6, I wonder how we'll see the boot process change and improve...

---

### Post by MacUntu on 2009-07-12
Would be nice if one of you could upload this depchart.py script - jdong's site seems to be gone.

Files are there: [http://bazaar.launchpad.net/~uphackers/uphack/uphack-tools/files](http://bazaar.launchpad.net/~uphackers/uphack/uphack-tools/files)

Should have read the thread more carefully. ;)

---

### Post by mtecknology on 2010-04-27
[https://code.edge.launchpad.net/uphack](https://code.edge.launchpad.net/uphack)

---

### Post by madjr on 2010-04-27
> **mtecknology said:**
> [https://code.edge.launchpad.net/uphack](https://code.edge.launchpad.net/uphack)

why isnt this implemented in lucid?

this is the same hack right?

---

### Post by mtecknology on 2010-04-27
> **madjr said:**
> why isnt this implemented in lucid?

this is the same hack right?

This is just what I saw of jdong. What came after this was a very lengthy discussion on IRC that amounted to this...

The move to upstart is a very hard one and involves some very tricky stuff. Apparently upstart is also the reason that plymouth exists. I guess there's a lot of magic involved in upstart now which pretty much means things are a whole lot more complicated than they were.

I'm interested in working on moving things from sysv to upstart but from the sounds of it, this is a VERY tricky task and may not be completed in time for Maverick.

I guess this is more random now. I just wanted to mention what we talked about in brevity.

---

### Post by jdong on 2010-04-28
> **madjr said:**
> why isnt this implemented in lucid?

this is the same hack right?

For the record, this **has** been properly implemented in Lucid by Scott James Remnant (Keybuk) and friends.

This thread is old and its information is only worth historical nostalgia at this point. (maybe some tools are still somewhat useful)

---

