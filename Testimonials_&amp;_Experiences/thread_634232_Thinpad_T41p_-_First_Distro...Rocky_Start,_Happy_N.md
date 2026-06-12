---
title: "Thinpad T41p - First Distro...Rocky Start, Happy Now [~Long]"
date: 2007-12-07
forum: Testimonials &amp; Experiences
---

### Post by bmwman91 on 2007-12-07
Now, I am running Mint 4.0, but since it just seems to be Ubuntu 7.1 with GUI tweaks and changes to the initial software package, I am here.  I have also had more success troubleshooting things in these forums than on the smaller mint forums.

Anyway, this is a story of my first Linux experience, and can hopefully be used by anyone with the same laptop (see sig) who has issues.  If I do not cover something that you are having trouble with, feel free to post or PM me.  Maybe I ran into a similar one.

So, it all started with a co-worker telling me to try CentOS when I was bitching about how much I hate Windows due to some security issues I had.  A few weeks prior to this, a friend just got on Gentoo and tried to sell me on it.  As much as I love customization and minimal resource usage, I felt that Gentoo looked like it would hinder my productivity.  I am willing to trade some resource usage for ease of use and not having to wait for things to compile when there are perfectly good binaries out there.  CentOS...well, it looked a little hairy for a complete Linux n00b.  The last time I had to run things from a command prompt, it was in MSDOS lol (and I was reluctant to get on Win3.1 at the time).

So, after finding DistroWatch.com and reading various reviews, I decided to take the plunge with Linux Mint.  It appeared to be THE easiest distro for a total beginner, and it probably is.  I gave Mandriva 2008 a brief shot, but just did not get a good feeling from it.  Coming from Windows, I am used to nothing being free.  The "pay to upgrade" to the "full" Mandriva package just felt too much like Windows, and seems contrary to the Linux spirit.  Anyway, Mint feels a lot like Windows in the GUI aspect, so it makes the transition a little easier.  Doing things via the terminal is not a big deal, though I need to learn the UNIX commands since I was only familiar with DOS.

=======================================
The First Install - Almost went back to Windows
--------------------------------
So, I downloaded an ISO with the Mint 4.0 Live CD and it started right up.  Since the WinXP install was still quite fresh on my ThinkPad, I chose to delete its partition and make the computer 100% Linux.  The fact that I had reformatted & installed XP 2 weeks prior and managed to get some sort of unfixable MSN default homepage hack among other internet security suspicions gave me the desire to leave for good.  So, here I am in the Mint Live CD.  All of my hardware is detected and seems to run. So, I start the installer, format away the festering Windows rot, and am on my way.

Once I boot and login, I find that I cannot connect to wireless networks.  They all show up in a list, but there seems to be some problem actually getting on them.  I can plug in to my home LAN and have stuff work, so I do this and run MintUpdate to get the latest stable packages.

Restart...sweet, wireless now works.  I have a desktop WinXP box with all of my "real" documents/media/apps which I look for help on while practicing on my ThinkPad.  From searches, I found that the older version of the network manager had issues with WEP/WPA authentication.  An update fixed this and I was getting a 36Mbps connection which is what I typically get across the house from the router.  So, all is normal there, although it was a little frustrating at first having to hard-wire in.  It was OK; I knew that I was not in Kansas anymore and that I would have to be patient with my n00bishness.

Next up, I installed the "restricted" ATI drivers for the built-in FireGl T2-128 (M10) graphics chipset.  Alrighty, no issues.  Now my screensavers run smoothly.

Now, time to get this Compiz thing going since it sounds so cool.  It had issues, and I did a bunch of searching.  After installing the latest xserver-xgl package, it seems to work fine, although my frame rates in almost everything decreased.  After this, I installed Google Earth and it would freeze at startup.  After more Googling, I get it worked out with an "official" workaround.  However, it was TERRIBLY sluggish and barely usable.  I tinker with more settings....based upon forum posts and no real knowledge of Linux's workings (anyone want to give me a basic overview of the mechanics...I want to know it as well as I do Windows).

So, everything works now, but my sound quit.  The hardware is all recognized, drivers loaded, etc.  For some reason, nothing was coming out of the internal speakers or headphone jack.  One suspicion was that something was using the audio hardware so nothing else could.  A whole day of troubleshooting was of no help.  I strongly suspected Compiz as I saw that it caused a lot of issues with other people's systems.  No matter, NOTHING I did could make it work.  I was getting rather pissed and dark thoughts of putting Windows back started to creep in to my mind.  No sound, "stable" drivers mucking up my video performance, and a general fear of the unknown were taking their toll.

I booted from a Mandriva Live CD thinking maybe I would try that since it is considered noob-friendly.  Nah, I got the wrong vibe for aforementioned reasons.

On top of all this, when the screensaver ran and I came back to the computer, it would take 2-3 MINUTES for it to recover.  The GUI would slowly reappear and be completely frozen minus the mouse cursor.  Talk about aggravating!  I just had a "dirty" feeling by now...you know, the one where you install a bunch of packages that you do not really understand, none fix your issues, and you hand-edit configuration files based upon forum advice lol.


=======================================
The Second Install - So Far So Good - but XGL is a Big No-No (no Compiz for me :sadpanda)
--------------------------------
So, after all of this work, I pop the Mint Live CD back in and give a clean formatted install a shot.  This time I thought, "I will hand-pick each & every package update rather than doing them all like last time...maybe some audio update mucked things up."  So, first thing in I notice that the network manager suite was already the "new" one that worked fine with the wireless even before connecting to the updater...weird.  I thought I formatted the drive...well, I DID.  I have no idea why I got the "working" manager this time through.  Oh well, one less fire to fight!

First things first, I install the restricted ATI drivers.  Reboot...awesome, great frame rates and Google Earth does not hang, and is smooth as glass.  Next, I get in the update manager and inspect each listed update (filters out dangerous ones).  Nothing regarding Audio.  So, I just choose them all and go for it.  I will reboot and test my sound afterward.  If it stops working, I will have to do them a few at a time.  For the record, I have an Intel 82801DB-ICH4 audio card integrated in the chipset.  Just in case someone searches.....

Reboot...sound is still good.  So, goodness knows what I did the first time through, but I decided not to do anything funny.  Things WORK, and in about 1/4 the time it takes to do a clean install of Windows XP.

:guitar:

Now, I want to turn on Compiz just because it is fun to have.  Hrmmm...errors.  I get a message box saying something (cannot remember), search for it on Google, and find out that I need to install the latest xserver-xgl package.  I prefer the Synaptic package manager personally, over the terminal and Aptitude.  Maybe it is the Windows past, but I like having things laid out cleanly in a format that allows me to easily make mouse-choices.  I install XGL, and Compiz fires right up after a reboot.  Awesome.

I try to start Google Earth.  Hmmm, freezes at initialization just like in my first install.  I also notice that screensavers and glx_gears are running about half as fast.  Well, the hell with Compiz.  I want to free up system resources anyway, so I uninstall XGL and reboot.

BAM, Google Earth starts right up, although I swear it was a little choppier than before.  I may do a 3rd clean install since a couple other packages came with the xserver-xgl one and I did not remove them (nor can I remember what they were, there were 2 others).  Anyway, Compiz is dead, but I can live with that.  Some searching brought up that the current release of XGL has stability, compatibility, and performance issues in comparison to the "restricted" ATI drivers currently available.

So, that is it as far as "bugs."  XGL is not getting installed unless I find a serious need for it.  I have yet to install Wine, and I do not know if it needs XGL or if it can work with the ATI OpenGL support.

Here is a quick breakdown of my opinions.  On a scale of 0 to 10, with 5 being equal to Windows, 0 meaning the aspect is far superior in Windows, and 10 meaning Windows is inferior to this distro, here goes:

Ease of installation: 9
Installation time: 10
Hardware Support: 6*
GUI Ease of Use: 8
3D Performance: 5**
Other App Performance: 7
Software Suite: 9***
Community: 9#

* Honestly, the hardware drivers in Windows were better.  I do not blame Linux for this.  IBM intended the T41p to run Windows and made all their product-specific drivers for Windows.  I still score it higher since GETTING the drivers in Linux is a hell of a lot easier.

** First off, I do not really play games.  I may try to get Far Cry running just for the heck of it as a comparison, but that is it.  Anyway, I score it the same as Windows overall as OpenGL apps run the same on both OS's.  There is no DX support in Linux, which is fine since it is only needed in games anyway, but did have its uses.  I only really need 3D horsepower for MCAD projects, and they all use OpenGL anyway.  The only other "benchmark" I have is Google Earth, and it is as fast in Linux with the "restricted" ATI drivers.

*** How can I even compare here lol.  Windows has NOTHING free (minus bundled stuff, all of which is complete dogshit).  OpenOffice rocks, and all the other included stuff works very nicely.  Everything is free and has a good community for support.  I give it a 9 rather than a 10 because I miss WinAmp.  I loathe iTunes with a passion, and a lot of the media suites for Linux reek of attempts to emulate it.  XMMS was OK, but the media library cannot compare to WinAmp's.  I will give Amarok a chance, and am wary of Songbird (iTunes knock-off, blech!).

# The dynamic between the communities is very different.  While Google has the answer to all Windows problems, there really are not any great all-in-one sources like this.  The closed-source nature of Windows limits help to hobbyists and IT people.  While they are smart and helpful, an open-source community leaves a lot more room for expert advice.

I know, this was a long one.  Sorry about that.  I will post updates to my experience as they come in this thread.  Hopefully any other frustrated T41p users, or any who want to leave Windows will find this a little useful.  Also, my apologies for any and all spelling errors.  I did my best to catch the big ones, but I am sure there are a lot of them still.

---

### Post by bmwman91 on 2007-12-07
Oh, and the one other funny thing.

I cannot find a specific device driver for my ThinkPad's monitor.  It is running a "Plug 'N Play" generic driver with the correct resolution, but the only refresh rate i can specify is 50Hz.  I KNOW it can use 60hZ, and I would prefer that.  I read in a couple places that it actually IS running 60Hz, but displays 50Hz in the Screen settings manager.  Is there a terminal command that can give my my current display configs?  Thanks again.

---

### Post by wolfen69 on 2007-12-07
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bmwman91 on 2007-12-10
Thanks Wolfen!

UPDATE

=======================================
The Third Install - Damn you ATI!!!
--------------------------------

So, I was trying to hack the 8.42.3 ATI driver to work with my FireGL T2 (M10) card.  Why?  SOLELY to make Compiz work, and to continue learning about the nuts & bolts of Linux.  I followed this tutorial to the letter (minus the 64-bit part since I have a 32-bit proc):
[http://ubuntuforums.org/showthread.php?t=596671](http://ubuntuforums.org/showthread.php?t=596671)

Well, Compiz would start, but leave me with a completely white screen requiring a reboot.  GoogleEarth crashed the laptop, and most screensavers stopped working.  Soooo, after trying to roll things back with limited success, I opted for a clean install.  Since I still have a dirty Windows box in my room with the important media/documents, I did not have to hassle with backups on the laptop.  Once I get "good" at Linux I will cleanse the Win box.

So, after the nice 12 minute complete wipe & reinstall I am just running the proper ATI driver from the restricted packages manager.  Everything runs awesome (1950FPS from glxgears), and I can live without Compiz.  As much as it is cool, it is completely unnecessary for getting stuff done.

So, I guess I am either:
a) Waiting for ATI's next driver package which will have support for AiGLX on workstation cards, or
b) Going to have to try to hack some AIGLX driver again and test my luck.

I guess option C would be to leave well-enough alone...but where is the fun in that?!

So, does anyone think that ATI will ever actually provide support for their workstation cards again?  It blows my mind that they would drop them and only support the gamer-types who are always out buying the latest expensive card.  Burning bridges is a bad plan, and only reaffirms my belief in only buying nVidia cards when I have the option (if only laptops had PCIe slots lol).

---

### Post by wolfen69 on 2007-12-10
it wouldnt bother me a bit if ubuntu got rid of compiz. really, do people really NEED it to get work done? it seems people worry more about enabling eye candy than learning the OS. (this is not meant towards the OP) once you see the cube spinning a half dozen times, is it really important?

then again, bling is everything to kids these days. heaven forbid someone should actually do some work with their computer. that would take away precious seconds from bling time.(look at what my computer can do!)

im done.

---

### Post by bmwman91 on 2007-12-10
Haha, agreed there.  I want Compiz working mostly because doing so seems to be a good challenge.  On the other hand, I do not need it eating system resources, and I really should be working on migrating my Visual Studio 2005 skills to whatever the Linux equivalent is (I am told Python is...but so far it is just a console).  Considering that I am only eating about 170MB of my 1024MB of RAM without Compiz, I should just stay there.  Compared to the Windows usage of 350+ even after I disable garbage services and disable ALL window themes & effects, I have no reason to care.  Maybe that's another reason to be after Compiz...everything will feel less like Windows with it.  OK, that's a lame excuse.

BTW..
Any ideas on why I can only use a 50Hz screen refresh rate at the monitor's native resolution (1400x1050)?  Lower resolutions allow 60Hz.  in Windows, I could use 60Hz no problem (granted, I had drivers for my specific LCD panel there).  Apparently this is somewhat common, but nobody has a "fix."  Yarg.



Don't even get me started about the state of youth today either!  Get a haircut, a job, and some real self esteem!
(is a 23yr old allowed to bitch about kids?)

---

### Post by bmwman91 on 2007-12-13
More sweetness.....

I have No problems getting into the music/media/whatever folders I shared on the wireless network from my Wondows desktop.  Sweetness.....

Also, I am missing WinAmp less.  Amarok's media library is acceptable (though WinAmp's is really, truly, th ebest one I have used).  I got projectM up & running just fine and is a good surrogate for MilkDrop (well, it kinda IS MilkDrop).

[http://ubuntuforums.org/showthread.php?p=3076812](http://ubuntuforums.org/showthread.php?p=3076812)
My post has the procedure to get it working in Amarok (not XMMS).

Wheeeeeeee......

---

