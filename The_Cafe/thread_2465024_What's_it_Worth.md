---
title: "What's it Worth?"
date: 2021-07-19
forum: The Cafe
---

### Post by Shibblet on 2021-07-19
My current fiasco within the Linux world has resulted in some eye opening experiences.

If you want to see a majority of the issues, I will post the links here.  

[https://ubuntuforums.org/showthread.php?t=2463888]("https://ubuntuforums.org/showthread.php?t=2463888")
[https://ubuntuforums.org/showthread.php?t=2464288]("https://ubuntuforums.org/showthread.php?t=2464288")
[https://ubuntuforums.org/showthread.php?t=2464112]("https://ubuntuforums.org/showthread.php?t=2464112")
[https://ubuntuforums.org/showthread.php?t=2463954]("https://ubuntuforums.org/showthread.php?t=2463954")

However... Let me explain.  No, that'd take too long... Let me sum-up:
> Basically H.264 Hardware Decoding on (is a 780ti legacy at this point?) Nvidia Video Cards is not supported within Chromium Based Browsers... for the most part (as the links will explain.)

Now, I had asked for some help testing (control) on this with a friend who uses Windows 10, and has the same Nvidia Graphics Card as I do.

Everything seemed to work in Windows 10, with a few minor tweaks.  Whereas in Linux, we were able to get a small portion of things to work with some major tweaks.

YouTube was the first issue.  In Windows 10, all my friend had to do was download the "h264ify" extension from the Chrome Web Store, and his YouTube started using the Hardware Decoder to playback video.  This actually left him a bit confused.  "Why do I need this extension to get Hardware Decoding for YouTube?" he asked.  "Same reason I do for Kubuntu Linux..."  I did explain it to him, but I won't go into that detail here.  Regardless, no such filter was needed for Google Stadia, or any other Cloud based Gaming Service that we tried on Windows 10 (XCloud / Nvidia GeForce Now).  Hardware Acceleration just worked in all of the Chromium based browsers we tried.  i.e. Edge/Chrome/Brave

In Kubuntu (20.04 / 21.04) however, it took quite a bit of configuring and setup, along with a lot of trial and error just to get YouTube to use Hardware Decoding.  And even after that was established, none of the browsers used Hardware Decoding with Stadia/XCloud/GeForce Now.

Don't get me wrong, the services worked, but were limited to 720p, due to the inability to decode the incoming stream "fast enough."

This all led to a philosophical discussion between my friend and I about the nature of Linux, and why I would go through all of that just to not get the result that I wanted.  Why would I bother, when Windows 10 just does it all by default?

He made a good strong argument about the nature of software and usage in general.  How games from Steam and GoG worked better with Windows.  How Linux users cannot "really" use XBox-Game-Pass for PC, unless they use XCloud, which, in turn, doesn't quite work.  His argument is fundamentally that Windows is easier, more functional with hardware, has "better" software, and increased compatibility.

Now, I know that these arguments aren't necessarily hard-truths, but they are understandable from his standpoint.

**[SIZE=3]Why would anyone use an OS that doesn't play my games, use my hardware, or have my software?[/SIZE]**

My only response to him was:

**[SIZE=3]"I agree that Windows can make things 'easier' from that point of view.  But at what cost?  What is your 'ease of use' and 'functionality' actually worth?"[/SIZE]**

The discussion then quickly turned into EULA's and Data Collection...  But eventually came back around to the "cost of the agreement."

I'd like to hear other ideas on this matter.  I know it may seem like an age-old discussion, but it tends to keep coming up in the Linux world.  So, I'll ask:

**[SIZE=3]Why do you use Linux?  What is it's worth to you?  Why not use a commercial OS for it's "easier" options?[/SIZE]**

---

### Post by TheFu on 2021-07-19
A few thoughts ... 

[LIST]
[*]Linux (at the shell), behaves like an OS should.
[*]It can be automated easily to accomplish most things.
[*]Privacy.  Read page 29 of the Windows EULA.
[*]No forced, paid, upgrades.
[*]Hardware support.  My old printers and scanners with 32-bit drivers on WinXP are working great on Linux, but never worked since MS-Vista on Windows.
[*]Easier to patch than Windows, by far.  For all the 3rd party programs installed, those are integrated via PPAs into the normal APT package system. Windows completely fails on this.
[*]Security. 99% of the time, we learn about Linux security issues a week or 3 months after our systems were already patched.  
[*]No forced patches on MSFT decision.  No forced online account to run an OS.
[*]Linux runs great on a mid-performance computer from 2009.
[*]Total uptime and total availability for the system.
[/LIST]

We are all different and have different priorities in life. Some people prefer to use Commodore 64 computers. That's fine, provided they do what they want, with minimal security risks. The same goes for Windows.  If you are a parent, get your kids a Linux PC.  That will teach them things that most kids never learn about computers and it doesn't prevent them from learning OSX or Android or MS-Windows too.  They will learn that whatever MSFT is selling isn't required or mandatory.  They will learn problem solving ... without being forced to learn it for a class, but the skill will still be theirs.  And if they don't decide to become a computer nerd, then they will spend more time outside, doing physical activities, likely not wasting hours daily behind a screen.  Win-win!

---

### Post by Shibblet on 2021-07-19
One question regarding your list:
> **TheFu said:**
> 
[LIST]
[*]Privacy.  Read page 29 of the Windows EULA.
[/LIST]

Can you specify the paragraph and subsection?  I found it online, and it's not divided into pages.


And one comment:
> **TheFu said:**
> 
[LIST]
[*]No forced, paid, upgrades.
[/LIST]

As a matter of fact, one of the changes to make Chromium based browsers decode H.264 in Hardware for YouTube, requires a patched, but older version of libvdpau1.  I have to mark it as "locked" in Muon, so that it doesn't get upgraded.

---

### Post by poorguy on 2021-07-19
> **Shibblet said:**
> My current fiasco within the Linux world has resulted in some eye opening experiences.
**[SIZE=3]Why would anyone use an OS that doesn't play my games, use my hardware, or have my software?[/SIZE]**

My only response to him was:

**[SIZE=3]"I agree that Windows can make things 'easier' from that point of view.  But at what cost?  What is your 'ease of use' and 'functionality' actually worth?"[/SIZE]**

I'm not a hard core gamer however I do play some games.
I'm into X plane Fight Simulator and spent a great deal of money on X plane Flight Simulator that would install and run on Linux however what a big disappointment and a PITA just to install and set it up and then to start it so I could finally fly. 

Screw it Linux don't game easy unless you have a Steam account which I don't and ain't gonna get,

Same X Plane Flight Simulator in Windows click on an icon everything loads and I'm ready to fly after a matter of a few seconds.

Windows still supports my old outdated graphics cards does Linux hell no Linux doesn't.
 OK the older graphics driver appears in the repository however it won't run even though it appears to install has something to do with missing dependencies and lack of the newer kernel supporting the older graphics driver.

A plus for Windows OS.
Games are developed for Windows not Linux.


> **Shibblet said:**
> 
The discussion then quickly turned into EULA's and Data Collection...  But eventually came back around to the "cost of the agreement."

I use Windows 10 and just don't worry about data collection or the politics on how Microsoft runs their business or Microsoft's business ethics or lack of business ethics I just don't care.

Whether I use Windows or Linux my personal information is going to be available because my bank and my doctor's office and my credit card companies all use Windows so guess what that means.


> **Shibblet said:**
> 
I'd like to hear other ideas on this matter.  I know it may seem like an age-old discussion, but it tends to keep coming up in the Linux world.  So, I'll ask:

[B][SIZE=3]Why do you use Linux?  What is it's worth to you?  Why not use a commercial OS for it's "easier" options?
[/SIZE][/B]
I don't have an answer for why I use Linux because I use Linux and Windows and both OSs work.

I use Linux because it's free to use.
I use Windows because it's free to use.

Both OSs have advantages over the other depending on individual user needs.

For gaming Windows rules and always has and always will imo.

To be fair Linux offers Flight Gear Flight Simulator and it appears to be awesome however in my case it's a no go since Linux no longer supports my graphics cards for whatever reason.

For basic computer use I use Linux. Ubuntu 20.04.2 because it supports Wayland real well and PCLinuxOS because it installs and runs without problems OOTB on every old desktop computer I use.

Life is good. :D

---

### Post by GhX6GZMB on 2021-07-19
+1 to @TheFu.

I could add:
* no planned obsolescence, making older HW useless
* no automatic bundling of 3rd-rate, lousy applications as default (horoscopes etc.)
* installation takes 30...50 minutes, not a full day
* upgrades take 5..10 minutes, not half a day
* ...

I could go on. I've switched completely to (x)ubuntu on three of my laptops and use them all the time.
I also have a Dell Inspiron 15 with Win10 that needs 6 minutes for booting. I never use it except for M$ specific tasks.

---

### Post by monkeybrain20122 on 2021-07-19
I think gamers make a lot of noises, but most computer users are not hard core gamers. Sooo...As for videos, Linux video players are very capable of hardware decoding.  Both Firefox and chromium based browsers have mpv addons which work for most video sites and use full hardware decoding (ff2mpv for Firefox, play-with-mpv for Chrome and co, on my Nvidia machine they do hardware decoding for many vp9 video streams too like Youtube's) On Chromium based browsers, vdpau-va-driver plays h264 streams with hardware decoding for Nvidia cards through vaapi, there is a [fork]("https://github.com/xtknight/vdpau-va-driver-vp9") to get Chromium based browsers to decode vp9, but at the moment it just doesn't play vp9.

So really as a non gamer the kind of issues you brought up aren't really a big deal.

BTW I may be wrong (as I am not a gamer) but I think Mac is not great for gaming either, but then no one would hold that against Apple.

---

### Post by Skaperen on 2021-07-19
Linux is open-source and rebuildable.  too often i've had commercial software with source included, but no way to rebuild it and run it so i know what i am actually running in binary.  my mainframe days still influence how i do things.  i don't even trust Android unless i could run what i build.

but i can't review it all, alone.  that's why i also want it to have a community.  paying for it is not the issue.  if i had to pay $1000 to use Linux with buildable source that can be shared with a world-wide community, i would have paid long ago.  if that happened to Windows, today, i would not go for it.  if it had happened long ago, i might have.  i'm now just too stuck on Linux.  too much of my code and knowledge base depends on Linux.

---

### Post by poorguy on 2021-07-19
> **Shibblet said:**
> 

**[SIZE=3]Why would anyone use an OS that doesn't play my games, use my hardware, or have my software?[/SIZE]**



> **monkeybrain20122 said:**
> I think gamers make a lot of noises,  


**"gamers make a lot of noises". :-({|= :lol:**

---

### Post by Frogs Hair on 2021-07-19
The topic has been discussed at length in other threads as stated and this thread is degrading rapidly. Closed !

---

