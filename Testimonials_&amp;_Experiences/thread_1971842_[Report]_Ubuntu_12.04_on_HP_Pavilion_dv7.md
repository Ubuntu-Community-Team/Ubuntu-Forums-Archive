---
title: "[Report] Ubuntu 12.04 on HP Pavilion dv7"
date: 2012-05-03
forum: Testimonials &amp; Experiences
---

### Post by Deltik on 2012-05-03
[CENTER][COLOR=Orange][SIZE=6]Ubuntu 12.04 Precise Pangolin[/SIZE]
[COLOR=Black][SIZE=1]on an[/SIZE]
[SIZE=5][COLOR=RoyalBlue]HP Pavilion dv7t-4100[/COLOR][/SIZE]
[/COLOR][/COLOR][SIZE=3]Compatibility Report[/SIZE]
[SIZE=2]by [Deltik]("http://www.deltik.org/")[/SIZE]


_**Previous Reviews**_
[Ubuntu 11.04 Natty Narwhal]("http://ubuntuforums.org/showthread.php?p=10850929") | [Ubuntu 11.10 Oneiric Ocelot]("http://ubuntuforums.org/showthread.php?p=11353243")[/CENTER]


_**In Short**_
Ubuntu 12.04 LTS has made an amazing comeback after the failure of Ubuntu 11.04 and the bigger catastrophe of Ubuntu 11.10.  I [COLOR="Green"]**highly recommend**[/COLOR] Ubuntu 12.04 LTS.


_**Recommendations (issued 29 April 2012)**_
Ubuntu 12.04 LTS is the way to go.  This is the best supported release of Ubuntu, especially for HP Pavilion dv7 laptops with AMD/ATI Radeon HD graphics cards.

If you are running Ubuntu 10.04 LTS Lucid Lynx, go ahead and attempt an upgrade directly to Ubuntu 12.04 LTS or reinstall Ubuntu 12.04 LTS.

If you are running Ubuntu 10.10 Maverick Meerkat or Ubuntu 11.04 Natty Narwhal, I suggest that you reinstall Ubuntu 12.04 LTS just in case the long upgrade path causes issues or is too time-consuming.  You may upgrade up the line, if you wish, but I've gotten reports of some problems.

If you are running Ubuntu 11.10 Oneiric Ocelot, please upgrade.  It'll be great. :) .  I've gotten a report that the upgrade may be successful if you do, even if you've got a bunch of custom PPAs.

**[COLOR="Red"]IMPORTANT NOTE:[/COLOR]** The AMD Catalyst™ Proprietary Display Driver is unfortunately horrible, and upgrading may cause graphics issues.  I detail the most optimal solution I could devise in the "Getting the Most Out of FGLRX" section below.


_**Pros of Ubuntu 12.04 LTS**_

[LIST]
[*]Fixed all performance and stability problems I was complaining about in [my last testimonial]("http://ubuntuforums.org/showthread.php?p=11353243")
[*]Finally, basic support for my synaptics touchpad!  I can right-mouse click and middle-mouse click.  Furthermore, Ubuntu once mentioned that Ubuntu 12.10 Quantal Quetzal may support this touchpad even better.
[*]Improved integration and functionality of Unity, especially the resistance to opening the dash
[*]Improved productivity thanks to HUD
[*]Power consumption seems to have decreased, thus increasing battery life.
[*]I got a report that GNOME 3 Shell now renders properly with FGLRX.
[*]Although window titlebars do not update on ATI graphics hardware with the "fglrx" driver, a solution to this problem should be delivered in [an update]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/770283").
[/LIST]

_**Cons**_

[LIST]
[*](*No new issues identified! :D* )
[/LIST]


_**Getting the Most Out of FGRLX**_
Graphics performs terribly on all (to my knowledge) Linux computers that have an ATI Radeon graphics cards.

The reason for terrible graphics performance is that ATI Radeon doesn't work well on Linux; AMD's Linux support is very poor even to this day.  There's no good solution to this problem, but there is something that you can do that may fix the low frame rate problem that you may be having.

**FGLRX** is the graphics driver provided by AMD and not the community.  You will experience improved performance, yet some new graphics problems may be introduced.  The Ubuntu community is powerless to help because the source code to the FGLRX driver is not open.

**Sync to VBlank** means that each screen update will have finished rendering before it is displayed.  This eliminates a "tearing" effect, or horizontal lines on an actively moving screen like in a video, but frame rate naturally decreases to allow the graphics card time to process the entire display first.

_Instructions for any general Linux system (recommended):_
[LIST=1]
[*]Download the latest AMD Catalyst™ Proprietary Linux x86 Display Driver from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").  The latest driver works the best, and although it has "x86" in the name, it works on 64-bit machines as well.
[*]Go to a terminal.  Know where you saved the [FONT="Courier New"]amd-driver-installer-XX-XX-x86.x86_64.run[/FONT] file.
[*]Run the command [FONT="Courier New"]cd /path/to/amd/driver[/FONT] , replacing "[FONT="Courier New"]/path/to/amd/driver[/FONT]" with the location you saved the driver installer to.
[*]Run the command [FONT="Courier New"]sh amd-driver-installer-*-x86.x86_64.run[/FONT] .
[*]Enter your password when the prompt for it pops up.
[*]Follow the default installation configuration.  If the installer refuses to install, it's probably because you have FGLRX already installed.  Follow the third bullet of the instructions in the "FGLRX troubleshooting after upgrading" section below and retry these instructions from step 4.
[/LIST]
_Instructions for Ubuntu 12.04 LTS (with Unity):_
[LIST=1]
[*]Search in the dash for "jockey".
[*]Open the first program in the results, which should be called "Additional Drivers".
[*]jockey will now search for the driver that you're missing.
[*]Activate the "ATI/AMD proprietary FGLRX graphics driver".  This may take a while.  [COLOR="Red"]DO NOT[/COLOR] activate the one with "(post-release updates)".
[*]If there's anything else in the list that you might want to activate, now is a convenient time to do so.
[*]Restart your computer.  Your graphics performance should have increased greatly, but be aware that FGLRX has many annoying problems.
[*]Go into Ubuntu Software Center and search for "CompizConfig Settings Manager".
[*]There should be one item in the list.  Install it.
[*]Search in the dash for "ccsm".
[*]Open the first program in the results, which should be called "CompizConfig Settings Manager".
[*]Select "OpenGL" from the "General" section.
[*]*Uncheck* "Sync to VBlank".  This might help increase frame rate even more, but if tearing issues (the screen feels like it's ripping) are bothering you, re-enable "Sync to VBlank".
[/LIST]
_Instructions for Kubuntu 12.04 LTS (with KDE):_
[LIST=1]
[*]Press [FONT="Courier New"][Alt]+[F2][/FONT].
[*]Type in "jockey-kde".
[*]Follow steps 2 through 6 in the instructions set above.
[*]Press [FONT="Courier New"][Alt]+[F2][/FONT] again.
[*]Type in "systemsettings".
[*]Open the first program in the results, which should be called "System Settings".
[*]Under "Workspace Appearance and Behavior", select "Desktop Effects".
[*]Select the "Advanced" tab.
[*]Under "OpenGL Options" *uncheck* "Use VSync".
[*]I keep "Use OpenGL2 Shaders" checked because from some basic testing, it looks like rendering performance is better with it.  I'm not sure what it is, though, and I haven't bothered to find out...
[/LIST]

Watch out, though!  I can't emphasize enough that FGLRX is filled with all sorts of problems.  I've learned to cope with them, and really, they're not that bad.

_FGLRX troubleshooting after upgrading:_
[LIST]
[*]If your cannot use your keyboard and mouse after booting, start Ubuntu in recovery mode and drop down to a terminal.  Uninstall FGLRX.
[*]If you want to uninstall FGLRX, and you had installed FGLRX from an Ubuntu repository, run the command [FONT="Courier New"]**sudo apt-get remove fglrx**[/FONT] .
[*]If you want to uninstall FGLRX, and you had installed FGLRX from AMD's binary package, run the command [FONT="Courier New"]**sudo /usr/share/ati/fglrx-uninstall.sh**[/FONT] .
[*]If you want to reinstall FGLRX, follow the applicable installation instructions above.
[/LIST]


_**Upgrade Your Computer**_
I thought I should include a bonus guide on how to make your computer even better because my laptop is no longer comparable to factory-shipped HP Pavilion laptops.  I upgraded its hardware recently.

_Buy a Solid-State Drive_
I bought a Crucial m4 256 GB (238.47 GiB) SSD for $285.  It was worth the money.  I used to criticize my computer for loading things so slowly for an [Intel Core i7-720QM]("http://ark.intel.com/products/43122/Intel-Core-i7-720QM-Processor-(6M-Cache-1_60-GHz)").  Boot up took about 50 seconds, logging in dragged on (especially in Ubuntu 11.10, which had the worst responsiveness of all Ubuntu releases so far).

After installing the SSD (don't worry; I still did testing of Ubuntu 12.04 LTS for this report using the original HDD) and installing Ubuntu on it, performance was lightning fast.  Boot takes no more than 12 seconds (from GRUB), and logging in to KDE takes mere seconds more.

I also got my hands on two other solid-state drives, both old ones from 2007: a Samsung (which had a poor reputation for SSDs back then) and an Intel.  I actually had these before purchasing my Crucial m4 256 GB SSD and before Ubuntu 12.04 LTS was released.

After reading my [last review]("http://ubuntuforums.org/showthread.php?p=11353243"), would you believe it if I said that Ubuntu 11.10 Oneiric Ocelot was *by far* the fastest release of Ubuntu I've ever used?  Most striking was how fast Ubuntu Software Center started up.  (Back in Ubuntu 11.10, Ubuntu Software Center took well over 30 seconds to become usable on a hard drive; Ubuntu 12.04 LTS's Ubuntu Software Center is now over six times faster to respond.)
In Ubuntu 11.10, Ubuntu Software Center was ready to go in 5 seconds!  Furthermore, the Intel SSD managed to score a 10-second boot time.

My most prominent benefit was using Pidgin's inefficient chat log searching.  It went through all 4,539 system logs, 72.79 MiB total, in 4.89 seconds.  On my HDD, this process took minutes.  During this time, I could not IM anybody because the entire Pidgin interface would be locked up.

Not only are solid-state drives super-fast, but they are also durable.  That Samsung SSD wasn't easy to grip, and I accidentally dropped it a lot, twice on the concrete outside.  It works fine.  This was the factor that convinced me to switch from HDD to SSD.  I've been through four HDD failures in the past, three of them happening in 2010 or later, under very different conditions.

If you value your battery life, an SSD will definitely help.  I didn't do a power consumption test, but [from AnandTech]("http://www.anandtech.com/show/4253/the-crucial-m4-micron-c400-ssd-review/11"), it looks like SSDs save a lot of power.  I've seen from other sources that power consumption by SSDs is a third of HDDs, and battery life may be extended from 30 minutes to more than an hour.

The only downside to SSDs is that they are extremely pricey.  Today, they're about $1/GB, whereas HDDs are down to $0.05/GB.
Me, I think that my $285 was well-spent.  No matter how much you overclock your CPU, you won't reach startup speeds of SSDs with an HDD.

[COLOR="Green"]Special SSD installation instructions on Ubuntu:[/COLOR] Enable automatic TRIM.  Follow [this guide here]("http://askubuntu.com/questions/18903/how-to-enable-trim").


_Clean the Ventilation_
I disassembled my laptop recently, and there was this... clog of dust jammed behind the exhaust.  I blasted it out, and the temperature of my laptop decreased a lot more than any software, even Ubuntu 12.04 LTS, could.  Instead of running between 200°F and 210°F, the thermometer is reading between 140°F and 150°F.


_Replace the ATI Radeon Graphics Card_
I haven't done this, but from all the problems FGLRX is giving, it seems reasonable that you should buy a graphics card from a brand that is *not* AMD/ATI.


_**Contradictions from Previous Reviews**_
Get this, I don't "like" Unity again.  In fact, GNOME 3 and Unity aren't working well enough for me to return to using.

I have chosen to run KDE on Ubuntu, or Kubuntu.  I made the difficult decision of switching to KDE 4.8 from GNOME 3.4.  Each have advantages and disadvantages, and in the end, I felt more comfortable with KDE than GNOME.  KDE offers advanced features that I'm surprised that GNOME doesn't have.  Also, Unity and GNOME have been giving me other graphics issues, but they are not present in KDE.


_**More Information**_
For more information from me or if you have information for me, just ask  me either through this forum topic or by my many methods of contact in  my Ubuntu Forums profile.

---

### Post by Perfect Storm on 2012-05-03
Very nice! :D
Hopefully you'll make a report of 12.10 when time comes.

---

### Post by Sxynerd on 2012-05-05
I wish I had the same results as you with my DV7-6135dx.  Mine has Beats Audio and I can't get the second sound card to work so I'm limited to the just the standard peaking crap speakers. :0/  It worked in 11.04.

---

