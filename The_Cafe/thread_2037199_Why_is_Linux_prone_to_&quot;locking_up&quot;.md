---
title: "Why is Linux prone to &quot;locking up&quot;?"
date: 2012-08-03
forum: The Cafe
---

### Post by hoppipolla on 2012-08-03
Now, you may think this is a support query... and it sort of is but I honestly don't think this is MY problem as such, I think it is Linux's problem as a whole, or rather Linux-based OSs like Ubuntu.

Recently I've decided to give Lin another go (dunno who around here remembers me... hi! ^_^) but the problem is... it runs lovely but then as soon as something comes along that is heavy on the CPU it locks up all apps of the same type (GTK apps or QT apps depending on whether a GTK or QT app is active).

I believe this has always been an issue on Linux distros for me, even on different computers.

If other people don't have this then feel free to move this thread to support. I just think that it's something to do with Linux's library structure or something that is locking up access to certain libraries eg a GTK library which locks up other GTK apps.

It's a great shame whatever it is, as it greatly taints what is otherwise a great desktop experience.

I'm only using Lubuntu on this old-ish machine, so it really should be smooth. I'll try Win XP on here to see if it's smooth but I think Vista is smooth.

Anyway, cheers :)

Hoppi!

---

### Post by IWantFroyo on 2012-08-03
I don't have this problem, and never have on any Linux system.

---

### Post by cariboo on 2012-08-03
Are you sure it's the system locking, or is it a gui component? One way to tell is to try and access the system remotely from another computer via ssh

---

### Post by vexorian on 2012-08-03
This sounds to me as if you are not assigning enough Swap and your RAM is low. If not, the cause of lock ups tends to be a piece of hardware that is not supported too well.

"Something heavy" is kind of vague. And different computers does not really tell us about how different the computers are. In other words, we need specs and more details...

If you are looking for help, your title/place combination is probably not a good one.

In reality, there is seldom a 100% lock in Linux, unlike windows. There are safeguards, like pressing CTRL+ALT+F1 to open a terminal. You would have to know how to use the terminal, but from there you can try finding (e.g.: The top command) and killing (e.g.: The pkill command) the process that is causing the mess.

---

### Post by Lyfang on 2012-08-03
Switch  between Ctrl-Alt-F1 (CLI) & Ctrl-Alt-F7 (GUI) when it locks up, does it work? 

How stable your computer is, sometimes depends on the hardware. Have you tried the PC-BSD (based on FreeBSD) distribution? BSD has a reputation for great reliability. FreeBSD is an UNIX-like operating system without the AT&T UNIX source code. You can install [XFCE]("http://www.pbidir.com/bt/pbi/200/xfce") (is lightweight) on PC-BSD.

---

### Post by 3Miro on 2012-08-03
Currently I own 3 computers and I have two more at work. I am using mostly Ubuntu, but other distributions as well. None of those machines locks up.

Also, do you know that Google, YouTube as well as over 90% of the world's largest supercomputers all run Linux. Those don't crash either.

When people are experiencing problems with Ubuntu, it is usually due to a bad video driver. Are you using some really old ATI video card? 

Also, many machines come with non-standard BIOS and Windows needs special BIOS drivers to work well. When the manufacturer makes their own standard and doesn't work with other OS, then there is little one can do (other than don't buy computers that are broken by design).

If you ask for help with more details, we may or may not be able to help.

---

### Post by neu5eeCh on 2012-08-03
Hmmm... he makes a fairly trollish post, then disappears.

My Xubuntu install has been locking up, but it's because of Firefox and Chrome. They both greedily consume memory until the whole system is eventually brought to its knees. Both browsers are like benign memory viruses. I recently installed the FF addon "Memory Restart" and enabled "Purge Memory" in Chrome. Any number of Conky configurations have insane memory leaks. They start out at 1 megabyte and balloon to a quarter of a gig in a couple of hours. Conky, I suppose, can be forgiven; but why FF and Chrome are still so leaky is weird. The problem, however, doesn't seem to be limited to LInux.

---

### Post by vasa1 on 2012-08-03
> **VTPoet said:**
> Hmmm... he makes a fairly trollish post, then disappears.

My Xubuntu install has been locking up, but it's because of Firefox and Chrome. They both greedily consume memory until the whole system is eventually brought to its knees...
Can you associate the memory consumption with a particular type of web content?

---

### Post by drawkcab on 2012-08-03
This happens, understandably, on my atom systems where running a lighter dekstop environment really helps.  I run gnome shell on my atom 330 with 4gb and it is pretty sluggish.  XFCE on my atom n270 with 1gb runs really well, all the more so on something like Debian.

I look at gnu/linux, not as distributions per se but as being modular.  Ultimately it iss about choosing a base install, desktop environment and apps that scale to your system.  There are lots of choices out there especially if you have the skill to build up from a minimal installation.

---

### Post by hoppipolla on 2012-08-03
Perhaps "lock up" isn't the right term. Basically all of the GTK apps or Qt apps or whatever will stop responding. However, it's not happening now and I'm sitting here on Linux Mint XFCE (not technically Ubuntu I know, but still Linux).

Well, I guess this thread is largely satisfied in that I really wanted to ensure that it wasn't a universal issue related to the management of libraries in Linux-based OSs. I think Linux is wicked and didn't want to think any kind of flaw like this was universal.

Perhaps it's because I was running Lubuntu off of a pendrive? Maybe it'll be smoother now Mint is actually installed.

Normally I would have thought it was merely the pendrive issue in an instant, but because I remembered having this problem in the past, alarm bells started ringing!!

However, if you guys are all good then it must just be be, perhaps it will continue to run smoothly now that it's installed.

Oh and VTPoet that's very interesting about the memory restart add-on, etc. I think I'll grab that :)

Thanks all of you! ^_^

---

### Post by Primefalcon on 2012-08-04
USB are never up to par with an actual install

---

### Post by jwbrase on 2012-08-04
> **vexorian said:**
> This sounds to me as if you are not assigning enough Swap and your RAM is low.

That was my first thought too, and the likely problem is related to this, but adding swap wouldn't help, because executable code generally doesn't change in memory, so it doesn't generally get swapped (or need to be swapped). Instead, it's just thrown out when space is needed for something else, and grabbed from the original executable file or library when it's needed again. 

> **hoppipolla said:**
> Perhaps "lock up" isn't the right term. Basically all of the GTK apps or Qt apps or whatever will stop responding. However, it's not happening now and I'm sitting here on Linux Mint XFCE (not technically Ubuntu I know, but still Linux).

Well, I guess this thread is largely satisfied in that I really wanted to ensure that it wasn't a universal issue related to the management of libraries in Linux-based OSs. I think Linux is wicked and didn't want to think any kind of flaw like this was universal.

It's a universal issue (but not flaw, things would be much more annoying if it weren't there) in pretty much *all* modern operating systems, and shows up when you're on a system that doesn't have enough memory for everything it needs to run, or when a program or library uses a given bit of code for the first time since it was started up. The effects are seen most strongly when the program or library is being run off of a slow disk (such as a USB stick or a CD).

What's happening is that even when a program or library is running, its code is not always kept in memory, instead only being brought in as it's needed. Instead of delaying for a long time to read in the whole executable file or library when the program is first started, it reads in each bit as it's needed, resulting in lots of shorter delays instead of one big one. Furthermore, if the OS finds itself running out of memory, it will start unloading bits of programs and libraries that haven't been used in a while to make room for stuff that's being used right now (so if you've just started a QT app and have a lot of GTK apps minimized, and it needs room to load the QT library, it will unload part or all of the GTK library to make room for it). When the unloaded code is needed again, it must be read from disk again, which will cause some delay.

An example from my experience is Minecraft: it can use a significant amount of memory, often enough that other programs have to be pushed out to make room for it if it's been running for a while. While I'm playing it, the other programs I have open are generally just sitting in the background without being used, so I don't notice any slowdown while I'm playing. But once I exit Minecraft and go to another program (or if I alt-tab to another program while Minecraft is running) the other program will often take a while to respond because it has to be brought back in from disk. But once it's back in memory, it runs fine. Where I'd run into trouble is if I kept alt-tabbing back and forth between Minecraft and another memory-intensive program (such as my web browser), so that each one had to be re-loaded on a regular basis.

Fortunately, I don't have a lot of reason to do a lot of switching between Minecraft and other programs, and my computer has enough memory that nothing tends to be pushed out of memory unless I'm running Minecraft for long periods.

> 
Perhaps it's because I was running Lubuntu off of a pendrive? Maybe it'll be smoother now Mint is actually installed.

That could well be. Running a distro from CD or USB tends to be a bit slow, because of slow disk access, even when you have ample memory.

---

### Post by rjbl on 2012-08-04
> **hoppipolla said:**
> Perhaps "lock up" isn't the right term. Basically all of the GTK apps or Qt apps or whatever will stop responding. However, it's not happening now and I'm sitting here on Linux Mint XFCE (not technically Ubuntu I know, but still Linux).

Well, I guess this thread is largely satisfied in that I really wanted to ensure that it wasn't a universal issue related to the management of libraries in Linux-based OSs. I think Linux is wicked and didn't want to think any kind of flaw like this was universal.

Perhaps it's because I was running Lubuntu off of a pendrive? Maybe it'll be smoother now Mint is actually installed.

Normally I would have thought it was merely the pendrive issue in an instant, but because I remembered having this problem in the past, alarm bells started ringing!!

However, if you guys are all good then it must just be be, perhaps it will continue to run smoothly now that it's installed.

Oh and VTPoet that's very interesting about the memory restart add-on, etc. I think I'll grab that :)

Thanks all of you! ^_^

Personally I have never, ever, seen the sort of locking up you describe in any GNU/Linux distro; even when running very early RedHats from floppies (remember those?). I can't help wondering where you might be going wrong.

rjbl

---

### Post by Smilax on 2012-08-04
my conky 'locks up' every little while. 

try just a conky  clock, same problem, sits at the same time for ~10s.

everything else works good.

at work my fedora locks up all the time. i think its F14, so old.

---

### Post by forrestcupp on 2012-08-04
> **hoppipolla said:**
> Now, you may think this is a support query...

Wow! Haven't seen you around here in a long while, Hoppi. Hope you're doing well.

---

### Post by zer010 on 2012-08-04
I had a lot of issues with Lubuntu 12.04 locking up or having programs crash when I first installed it, about a week after release.  I then switched to F15 and had my share of issues with that, but that's kinda to be expected with  Fedora's "bleeding edge" nature.  After about a month, I switched back to L12.04 and have been quite happy with the experience...
Overall, I'm just a sucker for LXDE...:D

---

### Post by arclance on 2012-08-04
> **VTPoet said:**
> Any number of Conky configurations have insane memory leaks. They start out at 1 megabyte and balloon to a quarter of a gig in a couple of hours. Conky, I suppose, can be forgiven; but why FF and Chrome are still so leaky is weird. The problem, however, doesn't seem to be limited to LInux.
[All the ${top_X Y} variables in conky have a memory leak, are you using those?]("https://sourceforge.net/tracker/index.php?func=detail&aid=3543857&group_id=143975&atid=757308")
If I don't use them my conkys don't leak any memory.

---

### Post by nerdopolis on 2012-08-04
Up until recent kernels, there was problems with high IOWAIT on Linux, where if a process is performing a long operation a slow disk, like a copying an huge ISO to a flash drive, a whole bunch of other seemingly random processess, will slow down to a crawl as well, such as the window manager or desktop shell or web browser.
d 
I think the patches to fix or improve that where introduced as recent at about Kernel version 3.3 or 3.4, I'm not sure.

Seeing that you had your OS on a flash drive that sounds like what it could be... 

I used to have a full Linux OS on a flash drive, (in 2009) and I would get those hang issues.

---

### Post by Ubun2to on 2012-08-04
> **hoppipolla said:**
> Perhaps "lock up" isn't the right term. Basically all of the GTK apps or Qt apps or whatever will stop responding. However, it's not happening now and I'm sitting here on Linux Mint XFCE (not technically Ubuntu I know, but still Linux).

Well, I guess this thread is largely satisfied in that I really wanted to ensure that it wasn't a universal issue related to the management of libraries in Linux-based OSs. I think Linux is wicked and didn't want to think any kind of flaw like this was universal.

Perhaps it's because I was running Lubuntu off of a pendrive? Maybe it'll be smoother now Mint is actually installed.

Normally I would have thought it was merely the pendrive issue in an instant, but because I remembered having this problem in the past, alarm bells started ringing!!

However, if you guys are all good then it must just be be, perhaps it will continue to run smoothly now that it's installed.

Oh and VTPoet that's very interesting about the memory restart add-on, etc. I think I'll grab that :)

Thanks all of you! ^_^

I have no idea why, but this happens to me fairly often. It comes at random. On my System76 Lemur Ultra, I have 8 GB of RAM and an Intel SSD, and my swap partition is 8 GB.
I have to crash the system every time. Unhealty? Yes. But, will using any key combination for several minutes make it stop? No. Have I run into any errors? No (probably because I hear the Crucial brand SSDs are crap compared to the Intels).
I have no idea what could be causing it. It has happened with Chromium open, but I'm hesitant to jump to conclusions, as it can have only 1 tab open, and no other programs running. Everything locks up to the point that I can't even use CTRL + ALT + DEL, ALT + SYSRQ + K, or ALT + F2 to bring it down.
The fan gets loud about 3 second after it freezes, and it will stay like that if I don't do anything.
If it temporarily freezes, Compiz and Unity usually crash and restart. Sometimes, Unity restarts after I exit Terminal (and, no, I was not running Unity via Terminal, nor did I start Unity via Terminal-I can finish configuring a printer in Terminal, or ).

---

### Post by hoppipolla on 2012-08-04
Yeah perhaps it was just because it was from a pendrive. I haven't been having any problems since I stuck Linux Mint XFCE on here.

I would have gone for Xubuntu but I think the care and precision of Mint is pretty cool.

And hi forrestcupp! It's cool to be back yeah - I found it appropriate now I'm back on Linux!

I can't stay away! ahaha ^_^

---

### Post by Mikeb85 on 2012-08-05
> **hoppipolla said:**
> Yeah perhaps it was just because it was from a pendrive. I haven't been having any problems since I stuck Linux Mint XFCE on here.

I would have gone for Xubuntu but I think the care and precision of Mint is pretty cool.

And hi forrestcupp! It's cool to be back yeah - I found it appropriate now I'm back on Linux!

I can't stay away! ahaha ^_^

Pendrives and live CDs are always slow if you try to actually do anything...  Better to install in a VM, and of course native is best.

---

### Post by hoppipolla on 2012-08-05
> **Mikeb85 said:**
> Pendrives and live CDs are always slow if you try to actually do anything...  Better to install in a VM, and of course native is best.

V true :)

Everything seems to work better once I install!

---

### Post by neu5eeCh on 2012-08-05
> **vasa1 said:**
> Can you associate the memory consumption with a particular type of web content?

Not really. Flash content plus certain add-ons (such as I'm not willing to uninstall) may hasten memory consumption, but I haven't successfully googled any particular causes. They're all over the map. (GMail is a memory pig on Chrome.)

> **arclance said:**
> [All the ${top_X Y} variables in conky have a memory leak, are you using those?]("https://sourceforge.net/tracker/index.php?func=detail&aid=3543857&group_id=143975&atid=757308")
If I don't use them my conkys don't leak any memory.

Thanks! I hadn't realized this was the problem but I *have* learned to avoid certain conky configurations. I'm not skilled enough to edit any of the configurations, though.

---

### Post by Linuxratty on 2012-08-05
> **IWantFroyo said:**
> I don't have this problem, and never have on any Linux system.

It's happened to me three times in eight years.

---

### Post by kurt18947 on 2012-08-05
I can only recall one lock-up that <SysRq>+<alt>+<k> wouldn't unlock.  Mint 13 with Cinnamon running FireFox 13.  I had that happen a couple time though not recently.  12.04 w/ gnome shell has been very well behaved.

---

### Post by hoppipolla on 2012-08-05
> **kurt18947 said:**
> I can only recall one lock-up that <SysRq>+<alt>+<k> wouldn't unlock.  Mint 13 with Cinnamon running FireFox 13.  I had that happen a couple time though not recently.  12.04 w/ gnome shell has been very well behaved.

That's good :)

I've had not a single one since installing Mint 13 Xfce. I think it's a pendrive thing as far as I can tell :)

---

### Post by Uncle Spellbinder on 2012-08-06
> **IWantFroyo said:**
> I don't have this problem, and never have on any Linux system.
Ditto.

---

