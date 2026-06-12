---
title: "New User Comparing Speeds of Windows and Ubuntu"
date: 2006-08-22
forum: The Cafe
---

### Post by DougS on 2006-08-22
Firstly, all power and praise to the Ubuntu and Open Source software movement and excuse my simplistic attempts at evaluation.

My experiences with Linux distributions is as follows:
Trialled on PIII Celeron 400MHz, 192 MB RAM, 30GB Maxtor DiamondMax 8 PATA.

I tried different flavours of Linux, originally installed alone, then with a basic Win XP setup (no service packs) and my preferred Ubuntu solution (the philosophy is outstanding)

Whilst there are many excellent features of the software which makes it very attractive I found that it loads and runs far more slowly than Windows, despite my high expectations.

Summary:
Boot times:
Basic XP: 45s,
Xubuntu: 75s to login then 15s to desktop.
Kubuntu: 105s to login then 60s to desktop

Browser:
XP: IE: 5s
Xubuntu: Firefox: 13s
Kubuntu: Konqueror: 18s

Office:
XP: Wordpad: 3s
Xubuntu: AbiWord: 12s
Kubuntu: AbiWord: 25s, OpenOffice.org, Writer: 105s


The key finding is that, in the setup I tried, the systems seem to load and run MUCH more slowly. This was very unexpected and disappointing.

I await pricing of Windows Vista and bundled prices with, say Dell hardware to be able to compare this against, possibly a faster machine to compensate for my findings of a slower running Open Source solution.


Linux is almost there in terms of ease of installation, quality, hardware detection and simplicity but the speed issue will put anyone off?

Am I missing something (WITHOUT going into any highly arcane, technical solutions!)

---

### Post by frrobert on 2006-08-22
When you compared the two were you using the live Cd or did you install ubuntu on the hard drive?

---

### Post by MaximB on 2006-08-22
your CPU is slow - with only 400Mhz...
you are right about ubuntu's boot loading time
it is slower the winxp
but after you login - it is very fast , at least for me
you should upgrade your computer.
for now you better run xubuntu - as it is for a slower machines.

---

### Post by slibuntu on 2006-08-22
You must be joking, i'm running Ubuntu 6.06 on a Pentium M laptop, along with XP and Ubuntu is so much quicker,it takes about 30 secs to boot, XP takes a few minutes!

---

### Post by MaximB on 2006-08-22
> **frrobert said:**
> When you compared the two were you using the live Cd or did you install ubuntu on the hard drive?

good point
almost forgot about it
you can not compare the time using live cd
**install** xubuntu on your PC - then compare

---

### Post by DougS on 2006-08-22
> **frrobert said:**
> When you compared the two were you using the live Cd or did you install ubuntu on the hard drive?

Loaded to Hard drive for "fair" comparison.


Previous comments acknowledged and Xubuntu was my preference as it DOES run faster but still poor compared to Windows in my test?

I dislike having to keep upgrading hardware (on environmental grounds) and if a Linux distribution did the same job on a less powerful machine, that would be a MASSIVE advantage, it just seems that it doesn't?

Not criticising as I really WANTED it to work, I will probably be back later (getting near retirement so cost of computer use will become more important)

---

### Post by DougS on 2006-08-22
> **slibuntu said:**
> You must be joking, i'm running Ubuntu 6.06 on a Pentium M laptop, along with XP and Ubuntu is so much quicker,it takes about 30 secs to boot, XP takes a few minutes!


Firstly, don't know what Pentium M is in comparison to my test system. Ubuntu at 30s would be GREAT.

We seem to have a reversal of times almost?

As I say, I am searching for comparative info and ideas as I really want it to work!

---

### Post by magnoliablossom on 2006-08-22
Well my system is 1.6 ghz, 120 gig hard drive, 40 gig hard drive, and 256 meg ram....and my Ubuntu boots up wayyyyyyyy faster than my XP....Which it could be because I have so much crap I have to run with XP, like spyware detection, firewalls, and anti-virus...Which I run a firewall with Ubuntu too.

---

### Post by slibuntu on 2006-08-22
I think thats my reason aswell,all the services and stuff XP loads on startup slow it way way down

---

### Post by argie on 2006-08-22
Not sure, but I think gedit is more of an equivalent to wordpad than OO Writer.

Firefox does start slower. Perhaps try Firefox on both Windows and Ubuntu.
Or try Opera. I've heard Konqueror is not simply a web browser also.

In my experience, the Windows start up is quicker. Even on my 2.93GHz PIV, 256MB(if that makes a difference)

---

### Post by DougS on 2006-08-22
In that case I may yet try my 1.3 AMD Duron system as dual boot.

As has been said, if it's faster/safer for basic web browisng etc AND you get to learn about it as well, that has to be good.

It's just that the times are sooooo much worse for a test that I must have spent a few days on in total.... any other thoughts?

---

### Post by slibuntu on 2006-08-22
Maybe RAM does make a difference, cos i've a gig

---

### Post by MKR. on 2006-08-22
Some things do load a bit slowly, but it's a minor issue to me.

A few seconds more load time for more functionality? I'm willing to live with it. ](*,)

---

### Post by Lord Illidan on 2006-08-22
For bootup, you might want to try out initng, it reduces bootup speed by a real lot.. Had Ubuntu constantly beating Windows.

OpenOffice.org and Firefox are memory hogs. You will find that their performance is slow, yes.

You also have quite little RAM. Use Xubuntu, it is fast. Or else, ditch Ubuntu and try out Zenwalk Linux, it is another fast little distro([http://www.zenwalk.org](http://www.zenwalk.org))

Try using Abiword instead of Open Office and Opera or indeed, Epiphany instead of Firefox.

Also, keep in mind that for bootup, Ubuntu launches more things than Windows does. When you've filled up Windows with anti virii software, firewalls, msn messengers and the like, they get almost equal.

I am also wondering about dma.
Can you run : ```
sudo hdparm /dev/hd*
``` in a terminal, post the output here.

If you want a really, really fast OS, try Sylablle.

---

### Post by kircher on 2006-08-22
I've found windows xp boots much faster on my system than Ubuntu (P4 2.4GHz, 768MB ram), but running firewalls, AV etc on startup means that by the time windows is fully loaded, it's about the same as ubuntu. Also, check out this thread:- [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491). It shows how you can speed up the boot process quite a bit by disabling things you don't need. If you don't use raid, bluetooth etc, why load it at startup? I disabled some things using this tool, and it sped my boot up quite a bit. In general I find that my system runs faster in Ubuntu than it did in winXP, apart from initial boot times. Gnumeric and Abiword open 10x faster than word and excel. Open office is still rather slow though, but it's fairly fat. Firefox opens faster in Ubuntu than it did in XP. IE6 opens faster, but that's because of MS's nice secure idea of always having IE open even when it's closed. Same idea with windows media player.

---

### Post by Knowles on 2006-08-22
Isn't IE an intergrated part of the windows core? in which it would run faster no matter what?

---

### Post by aysiu on 2006-08-22
Ubuntu can be sluggish for whatever reason. The funny thing is that Ubuntu's live CD runs faster on my *work* computer than an installed version of XP does. But on my *home* computer, both the installed and live versions of Ubuntu run much more slowly than XP does (booting, running applications, etc.).

To make it even weirder, when I install and use *kde-core* instead of *kubuntu-desktop*, the launching of applications is a *lot* faster. For example, with *kde-core*, Firefox (a GTK app, mind you) takes three seconds to load. With *kubuntu-desktop* it takes ten seconds.

---

### Post by bensexson on 2006-08-22
I have found the WinXP appears to load faster but in reality it fools you by starting the GUI before it is really done.  I typically have to wait 2 mins before it is really ready to use.  On the other hand once Ubuntu is up it is ready to go.

---

### Post by HanZo on 2006-08-22
to add my experience to this topic, I ditched win xp from my compaq nx7000 laptop in favour of ubuntu because it was way faster. the problem is that windows takes ages to load  because of the antivirus, firewall and all the stuff that needs to start at boot time, on my machine the time I was waiting, from the point where the desktop wallpaper first appeared and the point where I could actually work with the os was at least double the time between pressing the button and the desktop loading.
in ubuntu when you see the desktop you can use it, it's a different feeling.
the next problem was that when I forgot to defragment the box for some time it would get even slower.
firefox also was soooo slow on xp, and much faster on ubuntu.
plus somtimes xp is very slow in maximizing minimized apps, photoshop sometimes took me a minute or two to be maximized and usable after I had it minimized for more than 10 seconds. things like this never happend to me in ubuntu. and yes... photoshop running in crossover office feels faster than it does in windows... not for all things.. just sometimes... but funny anyhow.

---

### Post by Maylar on 2006-08-22
If it were me, I would not be running Ubuntu 6.06 on that system. I would run something like [Damn Small Linux]("http://www.damnsmalllinux.org/")

---

### Post by Nick Garvey on 2006-08-22
> **bensexson said:**
> I have found the WinXP appears to load faster but in reality it fools you by starting the GUI before it is really done.  I typically have to wait 2 mins before it is really ready to use.  On the other hand once Ubuntu is up it is ready to go.

Yup, same thing with me, after it boots 10 other things are still going, so you can't really use the system yet, even if you can move the mouse.

---

### Post by b_martinez on 2006-08-22
Others have covered what happens with a fully internet secured XP, and I agree with them.
If you are still looking for suggestions on a distro, try Xubuntu. Or, if you want to look further afield, try Vector Linux. Very fast on my Gateway 433c [433MHz processor, 196MB RAM, 10G hard drive]. Every bit as fast as the installed Debian on that box.
 For a really far out of the area distro, try FreesBIE. Small, fast, lightweight live BSD distro, and it comes with an installer.Harder, and easier for a seasoned Linux user to get used to, steep learning curve for beginner/seasoned user and yet, a good system.
Just my 2 cents.
Bill

---

### Post by DougS on 2006-08-23
Trying to finalise this thread and thank all contributors for valuable thoughts.

1. More RAM always good!?

2. As potential migrator, valuing functionality, customisation and Terminal window possibilities the great need is to get up and running quickly AND have comparable responsiveness (when I retire, things may be different ;-)

3. initng sound useful and would be useful in setup instructions?

4. Other distros look appealing if they have user friendly install and apps of Ubuntu flavours.

5. Suggest AbiWord=Wordpad = Lightweight WP (maybe?)
OpeOffice=MSOffice = Heavyweight package(maybe?) agree too much for PII system?

6. Points about time to launch core parts of system, apps, security features etc. taken.

7. As I understand, DMA relieves load on processor and does massively affect hard disk load times so that may be a factor.
Test machine now consigned to loft as I have a new term and all the efort that implies coming up!

8. Zenwalk seems an even more lightweight and speedy distro to try but unsure if it installs and runs from live CD.

9. DSLinux looks like a fast, simple browser etc but unsure if it is "equivalent" in features to XP or Ubuntu - thinking again about potential migrators of course.

10. Have read indicated thread regarding "sticking to XP" again with useful info.


In summary, thanks for all comments, I am sure I'll be back when time allows. The community aspect is very important and powerful.
Regards
Doug

---

### Post by gThree on 2006-08-23
One other suggestion:

Try an Openbox session (or experiment with other *Box window managers).

---

### Post by HanZo on 2006-08-23
oh as it has been mentioned a couple of times, DSL is a nice little distro, have installed it on an old PII 300 Mhz machine and it runs very smoothly and impressively fast! installing it is not as straighfordward a process as with ubuntu but it's feasable for anybody who has basic experience with a)partitioning b)how linux works. the basic set of apps DSL installs is not so great but you can add apps through synaptic, and all the major apps are included.
you cannot compare it to ubuntu for a lot of things but it is a good solution for old hardware... as far as I can tell the best one (tried puppy and vector too... puppy was nice but would not install on my scsi disk and vector did not work at all...)

---

### Post by Mathiasdm on 2006-08-23
> **DougS said:**
> Loaded to Hard drive for "fair" comparison.


Previous comments acknowledged and Xubuntu was my preference as it DOES run faster but still poor compared to Windows in my test?

I dislike having to keep upgrading hardware (on environmental grounds) and if a Linux distribution did the same job on a less powerful machine, that would be a MASSIVE advantage, it just seems that it doesn't?

Not criticising as I really WANTED it to work, I will probably be back later (getting near retirement so cost of computer use will become more important)

Fair comparison? You should compare Firefox to Firefox, no to IE.
And compare OpenOffice to OpenOffice, and Abiword to Abiword.

---

### Post by mips on 2006-08-23
I find Kubuntu slower than XP even though Kubuntu is tweaked for speed...

---

### Post by Tomosaur on 2006-08-23
Hardly surprising, considering that the hardware requirements for Ubuntu are a higher than those of XP. I notice no discernible difference between boot up times on my machine, but loading to desktop is much, much faster on Ubuntu than one XP (which shows me my desktop, but doesn't let me do anything for a little while. Totally pointless).

---

### Post by Miguel on 2006-08-23
Hi guys,

I'm not really surprised by the faster bootup of XP. Although you should be able to get a modern linux distro to work OK. I'd personally try damn small or "damn small linux not" (DSL-N). Although the latter is still experimental, it features GTK2 and some "bigger" programs. Both can run from the CD. Also AFAIK you can install things via apt from the debian repositories. Whether this is a full replacement of WinXP or not is debatable.

Anyway, there are a couple of things you can make to improve your Ubuntu experience much. Are you happy with Xfce performance? If not, you can try fluxbox, openbox or IceWM. The next thing you could do was prelinking. There are a couple of threads on this forum explaining how to do it. Tuning hdparm also should help. And then, disabling unneeded services should  be a must.

---

### Post by mips on 2006-08-23
> **Miguel said:**
> 

Anyway, there are a couple of things you can make to improve your Ubuntu experience much. Are you happy with Xfce performance? If not, you can try fluxbox, openbox or IceWM. The next thing you could do was prelinking. There are a couple of threads on this forum explaining how to do it. Tuning hdparm also should help. And then, disabling unneeded services should  be a must.

got the whole prelink thing and whatever else improves speed. Also got fluxbox which seems fast. i dont boot into XP often but when i do it feels very fast compared to (k)ubuntu.

---

### Post by RAV TUX on 2006-08-23
> **DougS said:**
> Firstly, all power and praise to the Ubuntu and Open Source software movement and excuse my simplistic attempts at evaluation.

My experiences with Linux distributions is as follows:
Trialled on PIII Celeron 400MHz, 192 MB RAM, 30GB Maxtor DiamondMax 8 PATA.

I tried different flavours of Linux, originally installed alone, then with a basic Win XP setup (no service packs) and my preferred Ubuntu solution (the philosophy is outstanding)

Whilst there are many excellent features of the software which makes it very attractive I found that it loads and runs far more slowly than Windows, despite my high expectations.

Summary:
Boot times:
Basic XP: 45s,
Xubuntu: 75s to login then 15s to desktop.
Kubuntu: 105s to login then 60s to desktop

Browser:
XP: IE: 5s
Xubuntu: Firefox: 13s
Kubuntu: Konqueror: 18s

Office:
XP: Wordpad: 3s
Xubuntu: AbiWord: 12s
Kubuntu: AbiWord: 25s, OpenOffice.org, Writer: 105s


The key finding is that, in the setup I tried, the systems seem to load and run MUCH more slowly. This was very unexpected and disappointing.

I await pricing of Windows Vista and bundled prices with, say Dell hardware to be able to compare this against, possibly a faster machine to compensate for my findings of a slower running Open Source solution.


Linux is almost there in terms of ease of installation, quality, hardware detection and simplicity but the speed issue will put anyone off?

Am I missing something (WITHOUT going into any highly arcane, technical solutions!)

try installing Knoppix or Dreamlinux for faster OS's

also I know on my BIOS menu I can enable a fast boot for XP....does anyone here know if this can be utilized for Linux, or like RAID does Linux drivers have to be enabled?

---

### Post by K.Mandla on 2006-08-23
> **DougS said:**
> Am I missing something (WITHOUT going into any highly arcane, technical solutions!)
I can only offer a few suggestions.

First, I think it's safe to say that Ubuntu does, in fact load slower from start, and even Xubuntu is going to feel sluggish by comparison. I think your specs compound that problem, given that a lot of what Ubuntu loads is probably unnecessary for your hardware.

But I also think XP plays a little trick by showing the desktop before it's fully ready to roll. So I don't know when you clicked stop on your watch, but you might want to see if that adds any more time. (I know booting into XP on my brother's zv6000 laptop can take just as long as Ubuntu (and I think Ubuntu is probably quicker), if you count the fact that you can't really "do" anything until XP is finished loading.)

So that's one idea. It's probably also fair to mention that for as long as I've been using Ubuntu, I've been disappointed with Firefox's load times (not so much page access times, but load times). I even tried putting Firefox on a RAM disk, but something about it just makes it sluggish. Maybe that will be ironed out one day.

And in Ubuntu's defense -- or Xubuntu's, to be specific -- I think Wordpad is quite a bit lighter than Abiword. I could be wrong there, but I believe Abiword is probably a bit more complex than what you're comparing it to.

Aside from those points, I suppose it bears mentioning that there are ways around those load and boot times. Prelink and preload make a **huge** difference. File systems also come into play. And if you start with a server installation you can build [a very lightweight system]("https://help.ubuntu.com/community/Installation/LowMemorySystems") that will be much more responsive and load much faster. You can also tweak some network settings (like [disabling IPv6]("http://www.ubuntuforums.org/showthread.php?t=202838")) that might improve page access times. 

Last but not least, try a distro that's more attuned to those hardware specs. [DSL]("http://www.damnsmalllinux.org") is a good starting place, although it's probably intended for even earlier machines. Arch Linux is a fantastic speed improvement over Ubuntu, but you've gotta know your way around your hardware. Zenwalk is an improvement too, and Dreamlinux is great if you have the right equipment.

Either way, there are plenty of ways to help that box get its groove back ... without spending a bunch of dough.

Cheers!

---

### Post by grte on 2006-08-23
I've got to say, this test isn't entirely fair.  It highlights Windows strengths while completely ignoring Linux's.

See, yeah, Windows will load faster now.  Try the test again after six months of using it on a regular basis, as opposed to Ubuntu after six months of regular usage.

And that's what really matters, isn't it?  How often are you willing to reinstall Windows just to keep it fast?

---

### Post by nalmeth on 2006-08-23
I've always known and understood Windows booting faster than linux. Not many people will deny that, and most all the necessary points about getting to the usable desktop etc have been made.

My point is, I rarely ever turn off or reboot my machine. Startup time really means next to nothing for me. 

The ability of my system to handle multi-tasking, and load my applications does matter.

On my power system, firefox takes less than 5 seconds to load. On my slow systems, it will take longer, but for those systems exist swiftfox, epiphany, galeon, and at desperation, dillo. 

Windows and linux have come from different backgrounds, and have been developed differently.

So long as you believe Windows XP is the level to which every OS is measured, it will be long before you understand what linux is capable of.

All I mean to say is don't take those numbers to heart. Use the OS, find out what unique abilities it offers you, and decide if you find it useful.

Linux evolves everyday, and I find benchmarking to be increasingly useless.

---

### Post by forrestcupp on 2006-08-24
> **Mathiasdm said:**
> Fair comparison? You should compare Firefox to Firefox, no to IE.
And compare OpenOffice to OpenOffice, and Abiword to Abiword.

This is true, there are OpenOffice and Abiword versions for Windows.  It's not fair to compare them to Wordpad because Wordpad a pretty lightweight editor that comes free with Windows.  It's not meant to have a lot of features.

---

### Post by Miguel on 2006-08-24
> **yozef said:**
> 
also I know on my BIOS menu I can enable a fast boot for XP....does anyone here know if this can be utilized for Linux, or like RAID does Linux drivers have to be enabled?


Although I'm not 100% sure if you need RAID modules, I can tell you what BIOS fast boot does in my machines (a P4 2.8GHz w/ 512 Mb RAM and a Dell Inspiron 8600 laptop). It bypasses most bios checks (mem, IRQ and similar things) as long as the last boot (at least the BIOS part) was successful. So instead of checking all your system, it simply does a couple of quick and dirty tricks.

Anyway, most people here are not doing a fair comparison. Don't get me wrong, long app startup time is frustrating, and a long boot process is annoying to us laptop users. But when you start multitasking, especially with a couple of CPU intensive threads, you see the difference. When you need every bit of CPU power, being able to disable everything in your system that is not a CLI is a big plus. I'd bet linux (computing wise) flies with a dualcore and a SMP enabled kernel.

FInally, I also support K.Mandla's suggestions of lighter distros. Unless you want to do the work yourself, that is ;)

---

### Post by DougS on 2006-08-25
I continue to watch this thread with interest and again I accept the comments made regarding the limitations/inaccuracy of my simplistic test.

I have also tried some of the other distributions mentioned and they each have their own good characteristics.

I really WANT to understand the alternatives to Windows more and I think I'll go the dual boot route to have it "at my fingertips" so that it can be more fully understood and given a much fairer test over a longer term.

Again, thanks for all of the positive welcome from the community.

---

### Post by .t. on 2006-08-25
On my machine, Ubuntu has always booted faster than XP. However, which version of Ubuntu are we testing here? Dapper? Because you should wait till Edgy - the start-up time is much improved. If you really wanna see a fast Linux system, build a minimal Gentoo (ie few USE flags); however, at 400MHz I suspect that will take one hell of a long time.

---

### Post by ComplexNumber on 2006-08-25
>  Browser:
XP: IE: 5s
Xubuntu: Firefox: 13s
Kubuntu: Konqueror: 18sthe fast loading speed of IE is because it is built into the kernel, so its preloaded at boot time.

---

### Post by slimdog360 on 2006-08-25
comparing wordpad with abiword, try MSword to abiword. Also because IE is built into windows its always running which is why it starts quicker.
Beside if you want a faster distro you can always try something lik Zenwalk or Arch linux.

---

### Post by IYY on 2006-08-25
> Boot times:
Basic XP: 45s,
Xubuntu: 75s to login then 15s to desktop.
Kubuntu: 105s to login then 60s to desktop

I can believe that. Ubuntu does load slower than Windows.

> XP: IE: 5s
Xubuntu: Firefox: 13s
Kubuntu: Konqueror: 18s

5 seconds is not the time it takes for IE to start up, as it's already in the RAM when you boot up. 

> 
XP: Wordpad: 3s
Xubuntu: AbiWord: 12s
Kubuntu: AbiWord: 25s, OpenOffice.org, Writer: 105s

Wordpad is not an office program. It does not edit .doc files. If you want an rtf editors, there are some for Linux that will boot up in less than 3 seconds.

---

