---
title: "GNOME is getting fatter. Thoughts about minimum hardware requirements."
date: 2015-06-25
forum: Ubuntu, Linux and OS Chat
---

### Post by jeff127 on 2015-06-25
I bought a new PC not long ago and I'm slightly irritated at the occasional slowness of GNOME in Fedora 21. It takes about five seconds to load Evolution or Firefox but when I reopen them it's much faster, it must be cached. I asked the computer shop for a processor that's "faster than a Sempron" and I thought I'd get better performance with a modern hard-disk, but that's not entirely true.

I might investigate if caching can be made more intelligent, or perhaps move to XFCE... but my point is that a new PC (even "above average") still doesn't always give instantaneous performance on everyday tasks. So if you're buying a new PC on the cheap I recommend getting a bigger CPU cache than what I've got. This CPU is quad-core with 4ghz clock speed and a small L-1 cache. I'm not disappointed by this because I don't like to spend much on consumer electronics, plus, it saves on my power bill! 

Stilll, I think the AMD Athlon would have been a better choice.

```

**I trimmed this output a little bit**
[root@computer]# lscpu
Architecture: x86_64
Byte Order: Little Endian
CPU(s): 4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2

Model name: **AMD A10-6800K APU** with Radeon(tm) HD Graphics
Stepping: 1
CPU MHz: 4100.000
CPU max MHz: 4100.0000
CPU min MHz:  2000.0000

L1d cache: **16K**
L1i cache: **64K**
L2 cache: 2048K
```

Have you bought a new PC and found it sluggish at times? Post your CPU specs so others can avoid them :)

---

### Post by kerry_s on 2015-06-25
try ubuntu-mate it's gnome on a diet, the way he was back in high school. lol

lol, your specs would run circles around mine. i'm using a simple hp mini-210-1010nr.

---

### Post by Bashing-om on 2015-06-25
jeff127; Hey !

Yours should run circles too around mine:
```

sysop@1404mini:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
bogomips        : 1999.99
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
bogomips        : 1999.99
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```
Running from a minimal install and xfce as the DE ; performing wonderfully well. No intention to do upgrade on this box.

[INDENT][INDENT]if it works
[INDENT][INDENT][INDENT]leave it alone
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by monkeybrain20122 on 2015-06-26
I don't think it has anything to do with gnome shell being "too fat". It is a myth that you need a super computer to run unity or gnome shell, the myth comes from people who either use very old hardware and think that 1G of ram is the norm or have a preference for the 'traditional desktop" and want to justify their aesthetics with a practical sounding argument .

 A new laptop (unless you have a netbook) typically comes with at least 4 G of ram and that is so plentiful that you won't see any difference between lxde and unity at two extremes resource wise since the relative difference is negligible when you have so much ram . If your new laptop is sluggish more likely it has to do with the graphic driver not playing nice with composting or something is not configured or running properly (memory leak e.g).

---

### Post by v3.xx on 2015-06-26
4 core and two threads per core.  IMO thats a fast machine.

> try ubuntu-mate it's gnome on a diet

I would agree with kerry_s, but I also notice some software will run slower than others, no matter how many core (I have 12).  Possibly its the way some software is built.

I do not run ubuntu gnome or unity, so no comment.

---

### Post by jeff127 on 2015-06-27
Hey guys guess what:

```
gsettings set org.gnome.desktop.interface enable-animations false
```

I thought you couldn't disable GNOME desktop compositing effects but I was wrong. I was looking at gnome-tweak-tool when I was supposed to be using gsettings. As MonkeyBrain says, it may be a graphics issue. I'm running an **AMD 'A' Series APU** and I don't have a driver, so if anything is using the graphics card it most likely isn't being handled efficiently. I'm happy now. That one command saved me. I think my hardware is overkill :)

Now I've got to figure-out a way of using 8GB of RAM :)

---

### Post by buzzingrobot on 2015-06-27
Disabling animations in Gnome does not disable compositing.

The "Instantaneous performance" the OP is looking for really does not exist.  When a program is launched, data is retrieved from the drives, then loaded into RAM and executed.  No matter how fast the drives, that will take some measurable, finite, amount of time. Faster hardware will speed that up, but it won't be instantaneous.

In addition, complex applications like Evolution and Firefox have many components that need to be loaded and that access the drives during normal use.  The easiest way to speed up access to them is to keep them open.

Standard Linux memory management caches data in RAM and makes it available for other programs and processes.  If that data is not re-allocated, then, it remains effectively cached. The more RAM that's installed, then, the greater this caching effect.

---

### Post by Bucky Ball on 2015-06-27
> **Bashing-om said:**
> 
Running from a minimal install and xfce as the DE ; performing wonderfully well. 


Same setup I've been using for about five years now that has been my experience on every machine I've ever installed that setup on, including my new HP Stream with a 32Gb eMMC chip instead of a hard drive and 2Gb of RAM. It flies. :)

---

### Post by wildmanne39 on 2015-06-28
I have not used it lately but preload can make the appications you use the most startup a lot faster.
> preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster
and that preload is a daemon that runs with root priviledges.
Thanks

---

### Post by Copper Bezel on 2015-06-28
I just finally upgraded from a 500 gig magnetic drive to a 120 gig SSD in my laptop. It's an Intel i3 with 4 gigs of RAM, and there was ... some of what I might consider sluggishness in Unity previously, but removing the bottleneck of the hard drive speed makes an absurd amount of difference. The responsiveness, the speed installing apps during setup ... it's just insane. Hybrid drives seem nice, but I don't think I'm going back to a pure magnetic drive on anything ever. The crazy thing is noticing just where I get the advantage - the Dash is *much* more responsive now, for instance. I don't miss just using Synapse anymore....

[quote=buzzingrobot]The "Instantaneous performance" the OP is looking for really does not exist. When a program is launched, data is retrieved from the drives, then loaded into RAM and executed. No matter how fast the drives, that will take some measurable, finite, amount of time. Faster hardware will speed that up, but it won't be instantaneous.[/quote]
That says nothing about instantaneousness on a human scale, though. You think of your hands as moving instantaneously on commands from your brain, but there's a delay there, too. If something takes 1/10 of a second or less, it's effectively instantaneous.

> In addition, complex applications like Evolution and Firefox have many components that need to be loaded and that access the drives during normal use. The easiest way to speed up access to them is to keep them open.
I personally look forward to the point at which applications are handled on all operating systems more as they are on recent releases of OSX, that whether or not they're in memory instead of suspended to disk depends on how you're interacting with them instead of whether you opt to close them or leave them open.

---

### Post by jeff127 on 2015-06-28
> **buzzingrobot said:**
> Disabling animations in Gnome does not disable compositing.


This is quickly turning into a support thread, but do PM me on how to disable unnecessary compositing features.

> **Wild Man said:**
> I have not used it lately but preload can make the appications you use the most startup a lot faster.


Preload's last update was 2013 according to Source Forge, I'll use buzzingrobot's suggestion and just keep stuff open. Easy enough to do plus I don't need to install anything.

> **Copper Bezel said:**
> I just finally upgraded from a 500 gig magnetic drive to a 120 gig SSD in my laptop. It's an Intel i3 with 4 gigs of RAM, and there was ... some of what I might consider sluggishness in Unity previously, but removing the bottleneck of the hard drive speed makes an absurd amount of difference. The responsiveness, the speed installing apps during setup ... it's just insane.


The new HD technology is indeed very good. It's a new era and I'm pleased to have a modern HD.


> **Copper Bezel said:**
> I personally look forward to the point at which applications are handled on all operating systems more as they are on recent releases of OSX, that whether or not they're in memory instead of suspended to disk depends on how you're interacting with them instead of whether you opt to close them or leave them open.

I predict this will be the new trend. When using Fedora or Windows 8 I find myself alt-tab'ing all the time. Fedora 21 GNOME doesn't have a list of open windows unless you create a new panel and add the "opened windows" feature. 8GB of RAM means you don't have to close an application.

---

### Post by Bucky Ball on 2015-06-28
> **jeff127 said:**
> This is quickly turning into a support thread, but do PM me on how to disable unnecessary compositing features.

Please do not. PM support is not encouraged here as it has no benefit for the forum community, which is what this forum is about. Also, a million or so heads are better than one. 95% of users and all staff do not provide PM support. Please keep it on the forums, not in the corridor. Thanks. 

If you want specific support, post a new thread with a descriptive title in the appropriate support area. Thanks.

---

### Post by buzzingrobot on 2015-06-28
> **jeff127 said:**
>  Fedora 21 GNOME doesn't have a list of open windows unless you create a new panel and add the "opened windows" feature. 8GB of RAM means you don't have to close an application.

In stock Gnome, the upper-left hot corner exposes a stack of the current workspaces with their windows depicted. Also, each open app places an icon in the Dash (the dock).  A single click on an icon there will move the focus to that application, regardless of which workspace it's located on.

I prefer scrolling between workspaces, so I add an extension that allows me to do that with the mouse wheel. I seldom find a reason to minimize a window or to have more than one application open in a single workspace.

---

### Post by Copper Bezel on 2015-06-28
Yeah, Gnome is actually pretty good for giving you an overhead view of all running windows. Unity follows more application-based switching, and you can see what applications are running at a glance, but it's actually easier to lose a window in a disused workspace somewhere and forget about it. 

Linux applications aren't fundamentally built to work the way Android and iOS and Windows Store and Apple-written OSX applications do, where leaving a window open doesn't necessarily mean its process is running and closing a window doesn't necessarily mean killing the process. I appreciate having Chrome hang out in my system tray when I happen to close the last window I'm working with, even though this means that it's simply *always* in memory regardless of my use, and I look forward to the point at which applications, windows, and processes can all be a bit more clever and operate a bit more independently of each other as they do on other platforms.

---

### Post by monkeybrain20122 on 2015-06-28
Well I dual boot Ubuntu 15.04 (unity) and Fedora 22 (gnome shell) on the same machine. The Fedora side always seems to be a bit slower (except for booting up) I think it has something to do with how gs handles compositing (mutter)

---

### Post by Copper Bezel on 2015-06-28
Again, that's configuration-specific. I've had machines that worked more smoothly with Gnome and machines that worked more smoothly with Unity. My current machine just *drags *in Gnome, and it's definitely an issue with the compositor on this video card (which is Intel and fully supported.)

---

### Post by buzzingrobot on 2015-06-28
> **Copper Bezel said:**
> 
Linux applications aren't fundamentally built to work the way Android and iOS and Windows Store and Apple-written OSX applications do, where leaving a window open doesn't necessarily mean its process is running and closing a window doesn't necessarily mean killing the process. I appreciate having Chrome hang out in my system tray when I happen to close the last window I'm working with, even though this means that it's simply *always* in memory regardless of my use, and I look forward to the point at which applications, windows, and processes can all be a bit more clever and operate a bit more independently of each other as they do on other platforms.

I'm not sure what you're getting at here.  Ending a process when a user closes a window is only a convention. Windows are just pixels. Whatever connection those pixels have with a process depends on how the developer decided to write that program.  Users buy into the metaphor so much that they think the window *is* the program.  So, the convention is to kill the process when the window is killed. It's a useful convention.

Users also often think 'minimizing' is something real, and not just a visual affect.

---

### Post by Copper Bezel on 2015-06-28
Have you, um, ever used Android? The way these environments are being structured now, idle processes can suspend to disk. The convention of users closing applications, at all, in itself, isn't the only way of doing things. It's an extra step of the kind that really ought to be the computer's job, not the user's. 

Separately, the strict link between windows and processes, inherited from emulating Windows conventions, also imposes some limitations and creates awkward workflows. An obvious example is LibreOffice - since it's my default handler for ODF and OOXML files, I don't open the application directly; I'm always either downloading a file or bringing it up in Nautilus or the Dash and opening it from there. If I close the last file open, the process quits. Opening another returns to the splash window and takes much longer than it would if the process were still running. But if I'm opening a sequence of documents one at a time to make small edits, it doesn't make sense to reload the application with each one - so I end up leaving the first document open, minimized, and then closing it when I'm done. Workarounds like that generally point to bad design, IMO. (Obviously, this isn't the case on OSX, where the link between the application and its document windows is properly broken.)

---

### Post by buzzingrobot on 2015-06-28
> **Copper Bezel said:**
> Have you, um, ever used Android? The way these environments are being structured now, idle processes can suspend to disk. The convention of users closing applications, at all, in itself, isn't the only way of doing things. It's an extra step of the kind that really ought to be the computer's job, not the user's. 

Android phone and Android tablet. Neither has a physical disk.  More often than not, I find it annoying that applications are left open by default. Clutters things. Android seems slow to close an app, a second or so before the window closes after tapping the close button, something I suspect may be deliberate.

> Separately, the strict link between windows and processes, inherited from emulating Windows conventions...


I assume it comes from Unix and its predecessors, which are a decade or so older than Windows. A GUI, typically X, used the process management capabilities that were already there.

I'm not sure of the value in breaking the link in a GUI application between the window it creates and the process itself, other than speeding up the next invocation of that app or leaving some background process active.

---

### Post by Copper Bezel on 2015-06-28
OSX does not follow the convention where windows represent processes - a running application is represented by an icon in the dock. Closing all of its windows will not exit the application. There's no direct metaphor with CLI applications, since users can interact with those in a variety of modes, and tying running applications to windows in the graphical environment is a Windows convention that Linux-based environments inherited. See "Start menu" and "taskbar." If there are prior Unix GUIs that used the convention as well ... good for them? I mean, bad, because it's a bad convention, but not really relevant, either.

As for lack of benefits ... other than the scenario I just explained? Well, I assume you've not used OSX, then. But yes, background processes and subsequent invocations are both very good reasons for separating that link. That's why some browsers like to live in the system tray and others warn you before they exit if they have downloads running in the background, etc. This is, again, a nonsense scenario: Why would closing the last page I happen to have open cancel all running downloads? 

And of course, it's not just what the system keeps running, but what it doesn't. What OSX does now is to allow idle processes (say, related to a minimized window you haven't touched in an hour that isn't playing audio or fetching data or something) to suspend to disk, effectively silently closing an application that you haven't invoked for a while. It is very similar to what Android does, and Windows Store applications emulate this convention as well.

Android doesn't "leave things open", and recent apps are listed in the order you've accessed them, so it's not really a matter of clutter. When you "close" an application, you're killing any background processes it's running and dropping its session data. It'd have to work differently in a desktop environment, though, where you want to be able to arrange your workspace a bit more granularly. Again, recent versions of OSX manage it. 

Android most certainly does have a "physical disk," precisely as much as my Ubuntu laptop does (given it runs from an SSD.) "Disk" does not mean "disc."

---

### Post by buzzingrobot on 2015-06-29
> **Copper Bezel said:**
> I assume you've not used OSX...

Used it extensively from its first roll out until about one year ago. I've owned about a dozen Macs.  They sat for years next to Linux machines.

(What an OS X, or any other OS, does with its icons is a design decision and does not have any necessary connection with the behavior of the actual software. The GUI is not part of the OS, it's a visual shell that accepts input from a user and displays output, just as character-based shells like bash and ksh. If OS X leaves icons in the dock to represent running processes, it could just as easily not leave those icons in the dock with no impact on the operating system.)

> Android most certainly does have a "physical disk," precisely as much as my Ubuntu laptop does (given it runs from an SSD.) "Disk" does not mean "disc."

Cell phones and tablets have storage media.  They do not have physical spinning disks. Android, as software, of course, is entirely non-corporeal.

I'm sorry, but what  describe seems to me a mix of semantics and metaphor, and, where something may actually exist, a distinction without a difference.

---

### Post by Copper Bezel on 2015-06-29
No, because we're talking about conventions that have direct impacts on the functionality of the software. Yes, OSX supports, in its dock, an icon with a menu and access to the menu bar and dialogue windows of an application when the application has no windows open. *Because that convention exists*, it is possible, reasonable, and expected for developers not to kill the application process when no windows are open. The more recent convention of applications suspending to disk means that the process itself is abstracted from its session data, so that a "running" application doesn't even necessarily mean a running process. This also permits that the system can request an application process to silently and gracefully quit when it is not needed in memory, and the applications that support said feature will do so. 

It is a bad convention that Linux-based desktops and applications all follow, strictly, to the letter, that an application is held open by its last remaining window, in most cases meaning that there effectively must be an open document, that its session data is dumped if the process quits, that the process cannot quit except by the user taking said action, and so on. It adds extra steps and messy workarounds to have all of these different constructions bundled together into one action. It's bad design. And if desktop Linuxes don't move on this, they will be the last platform to use this set of conventions, because OSX, iOS, and Android never did link applications to windows, and Windows is moving away from doing so, while suspending application sessions to disk when idle is universal on iOS and Android and for the "managed" applications from the Windows and Apple stores. 

The very idea of conventions is that they are a set of expectations and rules followed by the various members of a community for smooth interaction. The conventions followed on an operating system influence the conventions followed by its applications and so on. For instance, it is not accurate, technically speaking, to say that Ubuntu separates application and user data in a way that Windows does not; the system will not stop you from keeping application binaries in your user directory, and some applications do install this way. The only thing that keeps executables out in system folders is a convention of packaging. But this is considered a feature of Linux-based systems, because it's how things are done there. 

Comparably, Unity's dock does not support managing applications through the icon. The icon launches and manages running windows within that application, and stores static quicklists for sending commands through that application, like "open my pictures directory." It does not support dynamic menu input, as the Windows superbar and OSX dock do, or indicate running background processes and allow interaction with them, as the OSX dock does. These functions are instead taken up where absolutely necessary by indicator tray icons. It would be absurd for every running application to display an icon in the indicator tray, so most do not. Since there must be *some *GUI indication of the running application, most applications are written to exit and dump their data when they run out of windows. Since the user manages the quitting of running applications, the desktop environment does not monitor application processes or send any "when you're finished with that, maybe close out your process" signals as is done on all of these other platforms, so even if the applications supported such a thing, they'd never get the signal to do so. 

That set of conventions has a direct impact on workflow and ease of use. There are very good reasons that every other platform is moving away from them, and it will be a good thing when Linux-based-OS developers and application developers for those platforms are inexorably pressured into supporting the automation, integration, and persistence of state that come with the present proper way of doing things.

It is a matter of design, which is in fact the thing we are talking about, because we are talking about software, and software *is *&#8203;design. 

And *discs* spin. Disks store data. The convention is called "suspend to disk." The form of storage media is irrelevant.

---

### Post by buzzingrobot on 2015-06-29
You've lost me.  I still don't know what you're getting at. 

An operating system -- where processes live -- is one thing.  The shell a user interacts with to "talk" to that OS, whether that shell is Bash or Ksh or Powershell or KDE or Apple's GUI, etc., is a separate thing.  Decisions about when to relate actions taken in a shell to processes -- killing them, suspending them, launching them, etc., are up to that shell's designers. Designers typically adhere to convention because user's expect their habits to transfer and will frequently reject software that does not allow that, calling it "unintuitive". There's nothing magic, though, about putting little rectangles in something called a panel when a user clicks something on a window to make it behave in accord with the convention known as "minimizing". Whatever happens to the affected processes when a user clicks that minimize token is competely distinct from that GUI shell. 

Whatever the choice of spelling, there are no spinning platters in my phone or my tablet.

---

### Post by Copper Bezel on 2015-06-29
> Whatever happens to the affected processes when a user clicks that minimize token is competely distinct from that GUI shell.
Yes, I believe that you have sufficiently stated the obvious, and I do not believe anyone involved in this conversation is likely to fail to understand this. It does not somehow invalidate a discussion of design and behavior to say so. This is why I said this:

> I personally look forward to the point at which applications are handled on all operating systems more as they are on recent releases of OSX, that whether or not they're in memory instead of suspended to disk depends on how you're interacting with them instead of whether you opt to close them or leave them open.
In response to this:

> In addition, complex applications like Evolution and Firefox have many components that need to be loaded and that access the drives during normal use. The easiest way to speed up access to them is to keep them open.

We are talking about how applications are handled by the "shell" you referred to, which is a *component* of a graphical operating system, and how those applications expect to be managed. That is the thing that we are talking about. How applications behave and how they interact with users, and what actions in the graphical environment correspond to what actions relating to processes and memory management and so on. The thing that links the interface with the operations is indeed a set of conventions, and consistency with conventions within a target environment for an application is extremely important in software design.

When you suggest leaving an application open, you are suggesting that the user not close its last remaining window, because this is how Evolution and Firefox and every app on Ubuntu that does not generate an appindicator functions. I am saying that this behavior is an unfortunate necessity required by bad design, because every other graphical operating system on the planet is moving toward making this step unnecessary. This is accomplished the way changes in operating systems always are - by changing system code, conventions, and developer expectations simultaneously. 

That you opt to refer to a part of the operating system as "the operating system" and another as "the shell" is also an arbitrary convention, but it's an unhelpful and impractical one. I'm not sure how common that usage is within discussions of Linux-based OSes, but it would be nonsense in discussing anything else. The interface is an element of the program, regardless of how the two are connected. Linux-based OSes actually make this even more obvious than it is on other platforms, since some graphical apps will interact with the shell, too, as a part of their normal operation that's not immediately visible to the user. They're depending on bash being present as a part of their operating environment, treating it as an OS component.

> Whatever the choice of spelling, there are no spinning platters in my phone or my tablet.
Which are not required for disks. "Disk" and "disc" are distinct words with distinct meanings. The spelling is not arbitrary. There is no such thing as an "optical disk," for instance.

---

### Post by 9-rich on 2015-07-01
> **jeff127 said:**
> It takes about five seconds to load Evolution or Firefox

But once open they are pretty much instantaneous, and the only time I ever restart is following a reboot... 
You could set them to start on boot if you were so inclined.


It isn't Gnome in any case. I see similar behaviour for launching almost any browser on any OS on any platform, unless it's horribly under-specced.

---

### Post by Copper Bezel on 2015-07-01
Yeah, it's the desktop way of doing things, and first launch will always take the longest anyway, even on mobiles. Nothing Gnome or Ayatana can do about it, either, except insofar as Ubuntu can influence individual application developers. In the case of something like Firefox, that'd be pretty limited. 

I don't have much experience with Evolution - it's rare that I've used a local mail client, particularly now that the Gmail webapp can cache locally, and when I did, it was Thunderbird or Geary. I like Geary - very simple, straightforward interface.

---

