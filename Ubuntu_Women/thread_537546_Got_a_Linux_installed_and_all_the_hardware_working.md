---
title: "Got a Linux installed and all the hardware working"
date: 2007-08-29
forum: Ubuntu Women
---

### Post by Aishiko on 2007-08-29
Well as you know (if your in the IRC channel) I've been having a few issues with Ubuntu, mainly getting it to see and support my PCI bus, and by extention all my PCI cards.  So I put in a BugReport and included 20+ pages of information, some from the working (and very aonnying and unfriendly, in my opnion and past & current experince) RedHat EL4, until I some how figure out a way to make Ubuntu work on my desktop as well as it likes my laptop (same era computer).  Well the bug report is #135377 to anyone intrested.

In a few days I'll be getting a brand spanking new HDD, which I'll format ext3 and use as my new /home and then in a few months I'll get another and RAID 1 them (if I remember right that is mirroring, 0 is stripping and then 3 and 5 are used to combine several HDDs (all the same size) as one with a little bit lost to overhead, but I digress).

I'm hoping most of what i learn using RHEL4 will also apply to Ubuntu and then when Gusty comes out I hope it will support all my hardware and I'll try it once it gets released in Oct (I'm not going to use a development OS as my main OS, I many be crazy but I'm not insane!)\

I have a spare motherboard that I know all the compents are Ubuntu supported, however, I don't have a CPU for it and I don't know if the board is good or not, and with limited funds you don't want to gamble with what can be considered a substanital amount of your disposeable income.  I may be able to, but not right now.  Oh and the HDD? it's a gift from my family.

See you on the list and Irc!

---

### Post by bapoumba on 2007-08-29
Please post your experiences back :)

I'm not much into IRC, but follow the mailing-list, even if I'm not very vocal there.

---

### Post by elizabeth on 2007-08-29
> **Aishiko said:**
> Well the bug report is #135377 to anyone intrested.

Hooray for submitting a bug report! More of us should do it more often, and not just to get serious problems of our own fixed, but to improve Ubuntu itself :)

> (if I remember right that is mirroring, 0 is stripping and then 3 and 5 are used to combine several HDDs (all the same size) as one with a little bit lost to overhead, but I digress

Pretty much. [the RAID Wikipedia article]("http://en.wikipedia.org/wiki/RAID") is fantastic for further questions you might have, I consult it regularly. The most popular RAID arrays are 1 and 5, I use 5 at work and at home.

> I'm hoping most of what i learn using RHEL4 will also apply to Ubuntu 

I don't think you'll have a problem. My first Linux was Red Hat 7.2, and the transition from that to Debian wasn't too painful even back then (2002ish)

> See you on the list and Irc!

Yep! Nice to see you participating here on the forums too :)

---

### Post by Aishiko on 2007-08-29
I'll let you all know how it goes, It has been suggested that gusty might have better support for my hardware.  I figure if I had the problem then others must have too, but they might not have reported it but instead moved on to a different distro.

I have every intention of reporting more bugs as I find them, when it replaces redhat.  Speaking of Redhat, Elizabeth, I'm looking for a good multi-media player but every one I try to install doesn't come with all the dependancies, and I can't find the dependancies when I search the various repostories :(, if you can suggest one that has all the dependacies included in the rpm that would be wonderful.

Bapoumba, will do, I've not checked my email in a while been fighting with the OS!  But I'll do that tonight, and see what is going on :)

---

### Post by bapoumba on 2007-08-29
In the [Other OS Talk]("http://ubuntuforums.org/forumdisplay.php?f=147"), there is a [Fedora/Red Hat]("http://ubuntuforums.org/forumdisplay.php?f=162") section. You may want to browse there, and may be ask if not addressed already :)

---

### Post by Aishiko on 2007-08-29
I lost the post I was writing because firefox suddenly backed up but to recap I meantioned it onlyu because Elizabeth meantioned having used redhat in the past, and I have downloaded and used the tar.gz of zlib and xine, as my first attempt at actually compiling my own from scratch I was surprised it only took a handful of commands inthe terminal

------------------------------------------------------------------------------------------------------------
cd into the uncompressed directory
./configure
make
make check
make install
make clean
------------------------------------------------------------------------------------------------------------
and your done!  I just hope that it puts a link somewhere easy to get at.  If this fails I'll for sure check out that sub-forum.  On the upside if these work I can just use the same files to install on any Linux system.

---

### Post by elizabeth on 2007-08-30
For media players Xine is a great choice, but mplayer is my favorite :) It doesn't handle DVDs too well and it's command line based (except for the gmplayer bit, but that's not a very good GUI). I [wrote up this how-to]("http://www.princessleia.com/MPlayer.php") for compiling it on Debian, and it mostly works for Ubuntu - you just need to change the name of the package to "mplayer-compiled" or something when you build it so the Ubuntu package manager doesn't think it's the new "mplayer" in apt and get confused (that happened to me,  after a system upgrade my mplayer stopped acting like I had compiled it to, turns out a different version of mplayer had entered the repositories and blew away my own install, arg!)

---

### Post by Aishiko on 2007-08-31
ohh that stinks, I have Xine installed and the xine-ui but I can't figure out how to actually use it.

in Windoze I used media player classic, recently I foudn GOMplayer and I kinda liked that though I would have loved a player that combines features of both.  but I'm willing to try new things (otherwise I'd not be migrating to Linux!).

so I'll try mplayer.

thanks for the words of advice.

---

### Post by Aishiko on 2007-09-01
Ohhh I'm getting ready to try out the LiveCD of the Gusty Gibson,  and I'm hopeful that it will work with my chipsets.  I'll let you all know how it goes.  Don't be surprised to find this thread renamed something like  "GG works!"

:P

---

### Post by Aishiko on 2007-09-01
Yes that is an inside joke, 

but seriously I'm posting this from a gusty gibson LiveCD! it found ALL my hardware!  Now I have a hard choice and a question which I'll ask in the development forum.  If I use it as my main OS, until it's release in October (6weeks) if I can update it to the production version without much difficulty.  Plus using it as my main OS would let me really push it to it's limits.

So after a bit of looking at HDDs I'll decide which one I want to use.  I'm thinking of using a 40gig WD as my Ubuntu main with
/usr
/
/boot
/swap
/home will be a 500 gig harddrive
so what other /?* am I missing?

---

### Post by bapoumba on 2007-09-01
I'm running gutsy since Tribe2 ;)
If you install it, and run the upgrades on a regular basis, when gutsy is out, you'll be up-to-date. Now be aware that they are quite a few bugs (for ex, my main ethernet card is not recognized on boot, I have to bring the card up manually), and I'm running feisty on my main machine.
It's really up to you, but be prepared for bugs if you choose to install gutsy.

For partitioning, I usually leave /boot and /usr in /, with a separate /home and /swap. Once a gain, it's up to you. My / is 10Go on the gutsy laptop and 6Go on the feisty one (both lower specs hardware, 40Go and 10Go HD respectively). 40Go for the system is way more than needed ;)
I'd leave /home on your main drive (say 10Go for /, 1Go max for /swap and the rest for /home) and use the 500Go for storage (music, films and work files for ex). 

I read they were problems with certain drives (SATA IIRC, but not sure). Please search the forums with your drive specs, they are fixes and workarounds.

---

### Post by Aishiko on 2007-09-01
I'm prepared for bugs and unlike Windows I'll actually send (and have sent a bug report off the liveCD, something didn't load, or failed to load), error/bug reports. since Linux is more of a community project then a commerial monopoly.

What is /home used for?  I've been using it for all my data documents.  /swap I used 2 gigs (double my RAM amount), and I gave /boot a couple hunderd meg, you know what ever was left over after evenly giving 16 to a /home partain, 2 /swap, /10 /, at least in my redhat install which I'll leave on for the time being, you know just incase GG decides to break really badly.

When I'm done I'll have a 500WD, 164Hatachi, 80WD, for storage and a 40WD to boot off of.  Plus a CD burner and a DVD-Rom Drive.

Hugs Aishiko

---

### Post by elizabeth on 2007-09-02
> **Aishiko said:**
> What is /home used for?  I've been using it for all my data documents.  

The /home/user/ directory is for all your personal files. It also stores settings for your user, like if you're using gnome there will be something like a .gnome (the period before it is important and means it is "hidden" and often people shouldn't mess with it unless they're sure about what they want to change) directory in which all your gnome settings are stored.

> /swap I used 2 gigs (double my RAM amount), 

Although traditional wisdom dictates that you should use twice your RAM as swap, that is a bit out of date. I generally use that rule only up to creating 500M of swap, even on server class systems with 4G of RAM. Generally if you actually use more that 500M swap (doubtful if you have 1G RAM) you are probably leaning toward wearing out your hard drive with all the swapping and should just get more RAM.

> and I gave /boot a couple hunderd meg, you know what ever was left over after evenly giving 16 to a /home partain, 2 /swap, /10 /, at least in my redhat install which I'll leave on for the time being, you know just incase GG decides to break really badly.

bapoumba made a partitioning suggestion, at work we use a whole different one, and at home I just use /swap and / partitions. I keep an eye on disk usage in case I ever get close to filling up my drives, so the dreaded "fill up /var and your machine will go crazy" problem isn't one that is a problem for me. I figure being mindful of how much space you have is easier than making a bunch of partitions and then kicking yourself later because you devoted way too much to one or the other (of course you can resize Linux partitions, but that gets tedious when important data is involved).

> When I'm done I'll have a 500WD, 164Hatachi, 80WD, for storage and a 40WD to boot off of.  Plus a CD burner and a DVD-Rom Drive.

Sounds like a great setup :D

---

### Post by bapoumba on 2007-09-02
This is why I like to have /home on a separate partition. I usually dist-upgrade to the next release during the dev cycle. Then once the version is out, I run a clean install. With a separate /home (I do not format /home during the install) , all my settings are kept, desktop, themes, passwords, etc., all the adjustments I've done are there, no need to do them over again. But that's just me, and one way to go. (of course, I have backup, hmm, mostly up-to-date).

The most important is that you set up your computer the way that is convenient to you :)

---

### Post by Aishiko on 2007-09-02
I've decided to go with the following set up for the boot drive after reading your advice.
15Gig (15360MB) /
1gig (1024MB) /swap
21.5 gig (22583MB which was all that was left minus 1024MB free space just in case I need it for swap) /home
Now I don't expect to keep much on the /home partation but I suspect that 15gigs is over kill for Ubuntu in the / paration, and I can always shrink the /home if I decide to make anyother partations.  I have a stead fast rule I keep no user data or settings in the OS partation, if I can avoid it.

But right now it looks like I'll have to either go with just the CD-Burner or the DVD-drive as I get boot errors on boot up if they are both hooked up, but then I really want to replace the CD-burner with an LG DVD-Burner, I bought one for my mom about I'd say 18-24 months ago and it's been working wonderfully since then few if any issues.  Oh and I built her computer, it's a 1Ghz P3, just 128MB short of a gig of PC133 RAM, on a Arock Motherboard, a promise Controller card, and to top off the system a 30gig boot drive (WinXP Pro SP2), and 20gig Data drive.  Ohh it also needed a USB expantion card to give her some USB2 ports, but it's been rock solid as a machine.

Oh and I had internet issues crimping a new longer cord bypassing the hub I had been using ended that problem :)

---

### Post by Aishiko on 2007-09-02
This is my first post from Ubuntu on my home system not done from the GGibbon LiveCD!

Right now I'm formatting my 500 gig HDD (comes out to a total of 465.76) and adding programs and once it's all set up I'm going to go and check my email which I've neglated for a week or more........

If I'm not back in 3 days send an Apple or Cherry pie in after me!

---

### Post by bapoumba on 2007-09-04
> **Aishiko said:**
> This is my first post from Ubuntu on my home system not done from the GGibbon LiveCD!

Congratulations :)

---

### Post by Aishiko on 2007-09-04
Thank you :)

Right now I'm working on turning my Laptop into a dual boot (XP incase I ever need it again) and Ubuntu  I've got 13 gigs of free space that I can turn into Unpartaioned space and then reformat into ext3.  Right now I'm thinking of .5-1gig /swap, 3 gig /, and a 5 to 6 gig /home.  I mean the whole drive is only 30gigs.

ohh it's a Gateway Solo4200
1Ghz PIII
512 RAM
30GB toshiba HDD
8MB video card (yes eight megabytes!)
no onboard ethernet or modem
1USB port
8x CD burner
and it needs a new keyboard

I think I'll get a new one in time for the spring semester.

I wonder if there are any Quad-core Laptops........ :P

---

