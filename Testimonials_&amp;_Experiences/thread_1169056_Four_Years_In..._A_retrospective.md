---
title: "Four Years In... A retrospective"
date: 2009-05-24
forum: Testimonials &amp; Experiences
---

### Post by ve4cib on 2009-05-24
The following is a rambling, somewhat disjointed account of my experiences using Ubuntu since the spring of 2005.  Yes, it is long.  Feel free not to read all of it.  Your browser contains a "back" button for your convenience...



My first introduction to Linux/Unix was back in second-year university, in the fall of 2004.  I was a computer science student back then (as opposed to a computer science graduate).  All of our assignments had to work on the university's Solaris machines.  Of course we were never actually sat down at a Solaris terminal; we had to SSH into the machines from the Windows labs and do all of our coding in Nano (or Vi, or Emacs -- we had oodles of choices!).

Naturally these early experiences weren't terribly pleasant.  I was comfortable enough with the command-line; when I was a kid we had a Kaypro II "portable" computer at home.  It had DOS and a BASIC compiler built into a ROM-chip, a two-tone (read: green and black) screen, no mouse, no HD, and two 5.25" floppy drives.  Commands like cd and dir were ingrained into my brain from a young age.  Of course remembering that I had to use "ls" instead of "dir" was a bit annoying for the first few weeks, but I got over it.

Anyway, as the assignments started getting more and more complicated, and my siblings were needing the family desktop at home for their assignments, I finally bit the bullet and bought myself a laptop.  My plan from the beginning was to put Solaris 10 on it, since that's what we had to use at school for the assignments at the time.

Solaris installed easily enough.  But having never, ever seen a GUI that wasn't Windows (3.1, 95, 98, or XP) I was utterly baffled.  The wireless card didn't work, and I had no idea how to fix it.  And it had that godawful eggplant-and-teal colour scheme going on.  It was possibly the worst computing experience I've ever had.

So after a day or two of essentially owning a large and expensive brick I started venting my frustrations to my friend and fellow CS student Heather.  She'd recently switched over to Linux and gave me one of her Ubuntu 5.04 discs.  I installed it at lunch and was up and running fairly quickly.

First impressions: the installation was pretty easy.  This was before the days of live-session installation, and the distro came with separate live and install discs back then, but it was fairly intuitive.  Pretty much the same as installing off the Alternate disc nowadays.

Then came the first boot.  It turned on.  This is a good sign.  I was welcomed with a brownish GDM screen, I entered my username and password, and hit enter.  So far so good.

After a few seconds of loading I was welcomed to the standard, unconfigured Gnome desktop of early 2005.  It was brown and orange, had an uninspiring background, but it was much, much nicer-looking than Solaris was.  You have no idea how good those brown tones look after your eyes have been subjected to a gui implemented entirely in Java!

I started playing around with the various settings, etc... Changed the screensaver to Helios, customized the application menu, edited the panel widgets, etc...  It was all pretty good.  I even got the wireless card working after quickly plugging it into a spare ethernet port in a lab and downloading the packages.  (Heather had to show me where to find the package manager, and gave me the quick, layman's version of what it did, but after that I was pretty well self-sufficient).

Then the problems started.  The sound didn't work.  At all.  Well, that's not entirely true.  Once in every 15-30 boots the sound would magically work for no obvious reason.  And being a complete newbie I didn't know how to check logs, and kernel modules were a complete mystery.  I was tempted several times to go back to Windows (where I knew the sound worked), but I was stubborn.  And having offline access to things like GCC, SWI-Prolog, Common Lisp, etc... was just too convenient for homework.  So I suffered without sound for several months.

Third-year started in the fall of 2005.  I'd spent an entire summer with Ubuntu, and had learned (what I considered at the time) to be a lot about it.  Sure, I still had no idea what a cron job was (and to be perfectly honest I'm still a little sketchy on the exact meaning of the term).  The assignments continued to get done on the laptop.  Then 5.10 came out.  Time to upgrade!

I backed everything up onto some CDs, and did a dist-upgrade through update-manager.  At some point during the upgrade (I started it right before going to bed) the computer froze.  I had to hold the power button to reboot it.  The machine was half-upgraded, and completely unusable.  I had to reinstall 5.04.  And then I just ignored the new version messages and stuck with my soundless comfort zone.

In February of 2006 I finally got around to upgrading.  A friend of mine had an extra 5.10 disc he tossed my way, stating that they fixed a lot of stuff, and the sound should work.

I did a clean-installation (my previous experience with upgrading making me wary).  5.10 was indeed a vast improvement.  I actually had sound!  And my HD space suddenly plummeted as I clogged it up with every CD I owned!  Naturally I didn't realize that Ubuntu doesn't come with mp3 support, so I ripped everything into this myserious "ogg" format.  I'd never heard of it before, but it seemed to play in Rhythmbox, so I was happy.  (And, being lazy and not wanting to re-rip or re-encode everything I actually went out and bought an mp3 player that supported OGG -- the Cowon iAudio X5 is a great little device!)

In June of that year the hyped-up 6.06 "Dapper Drake" LTS release came out.  Promising vast improvements to, well, everything, I did another fresh install.  This was about my 1 year anniversary of being a dedicated Linux user.  Bug reports were starting to make sense, and I could solve most basic and moderately-complex problems on my own.  Of course the number of these problems was going down with each new release.

Nothing of any great note happened over the next several months.  6.10 came out, but I chose to ignore that release, sticking with 6.06 instead.  Same with 7.04.

Due to heavy use my old laptop was starting to wear out.  It was a pretty cheap Toshiba to begin with, and being carried to and from school every day was taking its toll.  Three monitors and a new motherboard later I decided to retire "HAL-9000" as my school machine and bought myself a new HP laptop in the summer of 2007.  This was a 64-bit machine, the video card was an nVidia, not an ATI, and it had a Broadcom WiFi card.  Anyone with any experience with nVidia and/or Broadcom can probably see where I'm going with this...

When I got the new machine home I first decided to try out Windows Vista -- for half an hour.  That was as long as it took to burn the recovery DVDs in case I ever wanted to put Vista back on it.  Then I nuked Vista and put 7.04_amd64 on it.

Oh, the headaches.... 32-bit Dapper was working so well on my old machine.  Why must my new one be such a problem!?  I spent countless hours trying to get nVidia drivers installed and working, and the Broadcom drivers of the day were simply not very good.  I would randomly disconnect, I couldn't connect to WPA-protected networks, etc...  It was not a fun initial foray into the new release.  Fortunately most of it could be blamed on the hardware and drivers, not on the OS itself.

Fortunately being a fourth-year CS student I was comfortable writing shell scripts to automate tasks for me.  Somewhere I've still got a copy of the script I wrote that I had to run after every kernel upgrade to reinstall the beta nVidia drivers (the only ones that worked with the card I had).

Once the drivers were set up the system was a pleasure to use though.  7.04 was certainly well ahead of 6.06 in terms of features and capabilities.  Everything felt faster, cleaner, more intuitive.  Familiarity with the terminal was absolutely essential back in 5.04 and 5.10, and it was highly recommended for 6.06.  By 7.04 you could get away without ever seeing a terminal for all but the most complex of tasks (like installing beta nVidia drivers when X won't start).

Unfortunately it was about this time that the proprietary fglrx ATI drivers stopped supporting the card in my old laptop.  And to be quite honest, the open-source drivers for that card are simply not nearly as good.  The 3D accelleration is choppier, and any 3d app lags and/or gets very low framerates.  My old laptop could run compiz without feeling terribly slow.  So I had to turn off the desktop effects.  Eventually I switched that machine's default WM to Fluxbox.

(Changing from Gnome to Fluxbox was possibly the best decision I've ever made in my Linux-using history.  Gnome, while pretty, and easy-to-use for beginners, is a bit of a resource-hog.  Especially with desktop effects enabled.  Games like Urban Terror went from about 15fps under Gnome/Compiz to 60+fps simply by changing over to Fluxbox.  Login time is tiny with Fluxbox; hit "enter" after the password, wait about 5 seconds, and you're in.  It really is that fast.  I now use Fluxbox on both laptops.)

In November 2007 I upgraded to 7.10 with both machines.  I don't remember if I did a clean install or not, but whatever I did there were no major hiccoughs.  The usual Broadcom/nVidia troubles arose, but to my delight they weren't nearly as bad as before.  No more custom shell scripts to install beta drivers.  Yay!

In April 2008 I upgraded both machines again, this time to 8.04.  Both upgrades (not clean installs, but actual upgrades -- albeit with the CDs, not over the network) worked flawlessly.  A far cry from my experiences going from 5.04 to 5.10.  WPA/WPA2 support was still a bit sketchy with NetworkManager, but somewhere I heard about WICD, and I installed that instead.  Honestly, I don't see why Canonical is still pushing nm-applet; I find WICD to have more useful features, and is easier to use.

Since there'd been a steady improvement in every release since 6.04 I decided I'd try out 8.10 on my 64-bit machine (since the older laptop was essentially demoted to "file server" status it never got 8.10 installed on it).  Upgrading to 8.10 was a mistake.  I don't know what it was, but 8.10 simply broke everything on my laptop.  The wireless didn't work, the sound didn't work (I thought we fixed that problem back with 5.10!), and after a few days of trying to solve all the problems I simply reformatted and went back to 8.04.  And I would have stayed there had it not been for all the good press 9.04 had been getting.

Fearing disturbing my obviously-sensitive 64-bit machine again, I decided to do a fresh install of 9.04_i386 on my old laptop.  It's running it right now.  Thanks to the age of the hardware there's nothing in it that uses proprietary drivers anymore; this means that every piece of hardware -- including WiFi and the video card -- worked right after the install.  No messing with any extra packages.  I still replaced nm-applet with WICD.  But I'm actually using Gnome on that ancient device.  And it works!  It feels a bit sluggish at times (that's what a four-year-old CPU and 512MB or RAM will do), but 9.04 really is, in my experience, the best release that has ever been put on that machine.


So that's where things stand now.  I've tried almost every release since 5.04.  Three releases stand out in my mind as being particularly good:

6.06: First time the terminal wasn't absolutely essential, fixed so many bugs from earlier versions.  Makes 5.04 and 5.10 feel like Alpha and Beta testing releases for the real deal.  6.06 IMO is the first release that Ubuntu could claim as being "ready for prime time"

8.04: Like 6.06, 8.04 is just stable.  Almost everything works right out of the box (proprietary drivers aside -- but these are dead-easy to find, install, and maintain now, unlike 7.04).  Improvements to the UI, Compiz (for those eye-candy nuts), and stability improvements are about with this release.  Based on this track record I have very high expectations of the next LTS release.

9.04: The first release since 6.06 that feels fast and snappy on older hardware.  EXT4 is great, and after weeks of continuous use I have encountered absolutely zero stability issues.  If 6.06 could claim to be "ready for prime time" then 9.04 is definitely ready.

---

### Post by travis.cthall on 2009-05-24
[IMG]http://images.starcraftmazter.net/4chan/for_forums/cool_story_bro.jpg[/IMG]

---

### Post by moster on 2009-05-24
hehe, nice story to read in this sleepless night. Thanks for sharing your experience. :)

---

### Post by growled on 2009-05-25
Nice perspective on things. Thanks for the share.

---

### Post by tgalati4 on 2009-05-25
Chugging along since breezy badger.  I had similar experiences with different hardware, but still impressed.  Thanks for sharing.

---

