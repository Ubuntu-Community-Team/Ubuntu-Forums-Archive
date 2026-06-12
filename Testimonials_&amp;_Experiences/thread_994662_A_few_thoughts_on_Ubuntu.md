---
title: "A few thoughts on Ubuntu"
date: 2008-11-27
forum: Testimonials &amp; Experiences
---

### Post by Iendicis on 2008-11-27
How long has it been? I really can't believe it's only been a year and a half since I booted into Slax (the last of the 5.x series). I guess it's time for a look back.

At the time I had a crappy old Pentium III I was expected to do my work and gaming on. I was bored and looked around for free games, and noticed a little something called "KDE" on the list. I clicked.

Roughly twenty four hours later I emerged with a booting LiveCD KDE desktop. Thanks to Slax, of course.

In hindsight, I took the long way around. My video card was a GeForce 2 MX that could barely load Quake II properly. This made driver battling quite a journey, and of course, x.org was not as nice as it is today. I quickly learned the wonders of dpkg-reconfigure xserver-xorg. I still get a shiver down my spine when I use that command in setting up Debian Etch installations.

Once I mastered Slax - which is built on Slackware but has a very different software management process and was somewhat an odd place to start - I wanted to go and see what else Linux would offer. Thanks to the wonders of Distrowatch, I found a few options.

One was PCLinuxOS, and the other was Ubuntu. I sprang for the former first, having seen and learned KDE already. I played the PCLinuxOS for a while in LiveCD, but I never really installed it. I still hung to Windows when I needed to get work done.

After I was done with PCLinuxOS, I went to Ubuntu 7.04, which at the time was the talk of the town. I fired it up, and promptly fell madly in love.

I would have installed Ubuntu at that moment when disaster struck. My BIOS was corrupted, and would not boot off of hard drives. For about four months I used Puppy Linux and DSLinux. Using those two helped me learn more about Linux and how it works. My bad luck was actually a good learning experience for me, because I was forced into using Linux programs.

Eventually I figured out what was wrong with the computer (I took the BIOS battery out, what a brilliant scheme!), but I had become much more learned on computers, to the point that I knew what kind of junk I was dealing with. 

A Pentium III? GeForce 2? What kind of madness is this?! You can't run anything on that!

An emotional reenactment, yes. But no less true or emotional.

So I eventually got a better computer from a family member who doesn't mind technology charity every once in a while, and I immediately scraped Windows off the virus-infected hard drive like a plague. I then installed Ubuntu 8.04, which was fresh out of the oven at the time. I've been using it and Debian Etch ever since.

Now, my thoughts on Ubuntu specifically:

Pros:
-IT'S FREE!
-It's much better at OpenGL than Windows. On the exact same machine, Nexuiz ran at 7 FPS with everything turned off. Under Linux, Nexuiz ran 45 FPS with relatime lighting, full textures, and bloom on, plus a few other options that I forget.
-It's easily personalized. I've done some Ubuntu zealotry work in my neck of the woods, and my desktop is very much different than my friend's. There's a charm to that.
-apt-get is civilization's one true wonder.
-Ubuntu 8.10 worked so well "out of the box" that I was able to convert more than a few people to switch. The wireless internet that even Windows XP and Vista have issues with in my house was tackled and secured by Ubuntu 8.10.
-Wubi is quite nice. It's nice to use on laptops that people don't want me partitioning like crazy (which I am prone to do).

Cons:

-Ubuntu has been unequivocally sluggish on nearly every computer I've used. It's not really, really bad (not Vista bad) but it's to the point that I refuse to install on anything less than a gig of RAM. I have to admit, I haven't tried tweaking it much; that's my next Linuxland step. If Ubuntu had the performance of Debian, by goodness, I'd marry the closest Ubuntu disc I had. (In my researches, Debian takes up about 80-100 MB RAM while idle. Ubuntu uses 150-200 MB RAM while idle, which is about what Windows XP gets when I've really flushed it out. Linux Mint hits the 250 MB RAM range. An unmaintained Windows XP installation around here gets up to 300 MB RAM while idle.).
-Ubuntu has an old version of Fluxbox in it's repos. I know why it's old; I didn't say I had to be logical in my rantings. :P I'm learning how to compile by source, but that has been largely unsuccessful.
-Debian can run more of my games, and better. Neverwinter Nights ran perfectly on Debian 4.0. In Ubuntu and Debian 5.0, it doesn't. I don't know why. But it puzzles me as to why it breaks so easily. The Pulseaudio stuff as well has caused loss of sound in  games only a handful of times, but it's enough. Wine is also more stable in Debian, for some reason.

I have a feeling that all of my Con arguments are solvable, and that's what I do as a hobby. It's amazingly fun, and boy do I thank whoever made that KDE link that I clicked on a year and a half ago. It's been a great ride.

for those who want to take a peek, I wrote a guide for many of my friends to read about how to get started up in Ubuntu. It's viewable [here]("http://docs.google.com/Doc?id=dcqpqgxb_176d69df9j").

---

### Post by wolfen69 on 2008-11-27
> **Iendicis said:**
> 

-Ubuntu has been unequivocally sluggish on nearly every computer I've used. It's not really, really bad (not Vista bad) but it's to the point that I refuse to install on anything less than a gig of RAM.

how many computers have you tried it on? i've installed it on over 30 computers now and have not noticed any real sluggishness. as far as needing a gig of ram, my next door neighbor has 384ram and Ibex runs great.

btw, what is your everyday OS?

---

### Post by Iendicis on 2008-11-27
> **wolfen69 said:**
> how many computers have you tried it on? i've installed it on over 30 computers now and have not noticed any real sluggishness. as far as needing a gig of ram, my next door neighbor has 384ram and Ibex runs great.

btw, what is your everyday OS?

Probably ten or fifteen. But I'm spoiled; I used DSL for four months. Now that's fast. :P Like I said, it's solvable. My newest install is fairly stable. It's more the fault of old hardware or my laziness in not turning off unneeded services. It's definitely not as fast as Debian, though.

As for the everyday OS, I use Ubuntu the most. I use Windows XP on the main laptop because the other user would freak if I replaced it with anything. If I had the choice I'd go fully Ubuntu.

---

### Post by fletchoid on 2008-11-27
How to make Ubuntu GNU/Linux more user friendly, and therefore more widely adopted.

After almost 20 years of tolerating Micro$ofts arrogance and greed, I decided to try Ubuntu GNU/Linux.  So far, I like what I see, and over the past few months, have moved over 90% of my computing over to Linux.  However, one thing sort of sticks in my craw.  Many of the things that an ordinary user wants to do are cloaked in mysterious geek code.  A google search on how to do some straight forward manipulations yields a multitude of differing command lines, and descriptions that seem to assume that you have been hacking computers since you achieved puberty.  If Ubuntu wants to appeal to the masses, it needs to have more GUI interfaces to do some of the common manipulations that a typical user might want to do.

For example:  You have an older hard drive with your Linux OS on it, and it is getting decrepit.  You decide you had better clone the dying drive on to a new drive before the darn thing fails and you are screwed.   You do a google search and you get a bunch of garbledegook:  “sudo dd if=/dev/sda1 of=/dev/sdb1 gnsnert –r gnoolde flrubble geek nibble drrdd dfdflk df sd  etc etc.”
Now, I do appreciate the power of the command line, but to be honest, the average computer user just starts to hear “arglebarglemorblewhoosh” and decides to stick with Windoze.  

Are there no gnerds out there that can write an easy to use script for these sorts of things??

Example:

“Determine the identity of the drives on your computer”
When you hit enter, the script reads your drives and gives you info as to what they are called.
“Which drive do you want to clone?”
you enter the number of the drive you want to clone…. You could even have an “Are you sure?”
“Which drive do you want to put the clone on?”
You enter the destination drive.
The script reiterates what you are asking you to do and makes sure you are sure.
“proceed?”
Y/N
Badaboom, badabing, the damn computer does the hard work.
“Do you want to increase the partition to include the whole drive?”
Y/N
If yes, then the computer does what you ask.
If No, you are asked what size to make the OS partition.

This sort of stuff is why Windblows is so popular amongst those who really don’t give a crap how their computer works, they just want to get on with their day.

While I admit that I am willing to spend a Saturday morning dicking around with my computer, using the Linux terminal to do what I want, there are a hundred others who think I am nuts, and a loser, and would NEVER attempt typing arcane commands into a Linux terminal to do what they want to do.  They would just buy a Windoze program that does it for them.  So, if Ubuntu REALLY wants to become a widely adopted OS, a lot of the simple, straight forward activities need to be placed into a pretty GUI and made simple.  Otherwise, only us gnerds will attempt these things.  Or maybe that is the whole point.  Gnerds WANT to be the misunderstood elite, isolated in their dimly lit computer rooms,  spending their weekends optimizing their OS, running benchmark programs, and… hey wait, that’s me…. Damn….. Are there nerd women on Lavalife?……

---

### Post by eldragon on 2008-11-27
i agree, ubuntu has been quite sluggish...

ive converted my laptop to arch, this very same laptop i thought was slugish compared to my desktop...(which i dont actually use much).

my desktop, still running ubuntu..right now, feels really slow. i dont know whats really wrong with it, maybe its because ive dragged it all the way from 6.06 to 8.04 (im skipping 8.10 there) from upgrade to upgrade. but im not sure.

tbh, im so damn happy with arch right now im hoping my desktop crashes so that i get forced to install arch there too :D im just THAT lazy :D

---

### Post by Iendicis on 2008-11-27
@fletchoid: Some things are a little under-gui-ified, I agree. But I wouldn't want a million little gui apps clogging up my installation, either. That's a plus for me actually. If a relative has an Ubuntu issue, I can just give them so terminal text to plug in and get it done.

I also appreciate that while you have to use the terminal, the same functionality in Windows costs money. Or a higher "level" of Vista. I'd take the terminal over spending money any day. Besides, how many normal computer users do you know actually know well enough to do anything the typical GUI app can't do? I think you're overestimating the typical user.

For the power user, though, the command line is essential. For example, people on the Ubuntu forums. ;) I find it very useful when I know how to use it.

But I am forced to disagree with your general thesis; the command line is not essential for the average user. I have family members who have never touched it, even after using Linux for a year.

@eldreagon: I looked at Arch Linux, but decided to continue learning Ubuntu. Once I'm ready to move up, I'll move into Arch or Gentoo. Probably Arch. But I'm still a newb in this game.

I actually messed with my Ubuntu install today and got rid of some of that sluggishness. It takes some effort, though. The biggest change in performance was getting rid of Pulseaudio, which gave me sound back for Nexuiz and UT99. Not too bad for a day's work.

---

### Post by hyper_ch on 2008-11-28
> **fletchoid said:**
> For example:  You have an older hard drive with your Linux OS on it, and it is getting decrepit.  You decide you had better clone the dying drive on to a new drive before the darn thing fails and you are screwed.   You do a google search and you get a bunch of garbledegook:  “sudo dd if=/dev/sda1 of=/dev/sdb1 gnsnert –r gnoolde flrubble geek nibble drrdd dfdflk df sd  etc etc.”
Now, I do appreciate the power of the command line, but to be honest, the average computer user just starts to hear “arglebarglemorblewhoosh” and decides to stick with Windoze.  

An average user would never dream of cloning their drive because they wouldn't even suspect anything to be wrong ;)

---

### Post by 3rdalbum on 2008-11-28
> **fletchoid said:**
> 

For example:  You have an older hard drive with your Linux OS on it, and it is getting decrepit.  You decide you had better clone the dying drive on to a new drive before the darn thing fails and you are screwed.   You do a google search and you get a bunch of garbledegook:  “sudo dd if=/dev/sda1 of=/dev/sdb1 gnsnert –r gnoolde flrubble geek nibble drrdd dfdflk df sd  etc etc.”

Are there no gnerds out there that can write an easy to use script for these sorts of things??

Yeah, I can. I considered writing a general-purpose "dd" frontend once. But for the drive cloning, I'm sure there is already a GUI out there. If you need something and can't find anything, I'll be happy to knock out a quick Pythoncard program for you if you send me a PM.

---

### Post by armandh on 2008-11-28
8.10 runs fine on the P-III 
I am using a 933mhz with 1 meg of ram as a media server
hooked via a 128mb video card and HDMI to a 42" flat screen.
plays dvds and .avi fine

---

### Post by jmcgovern on 2008-11-28
As someone who's done a little bit of work in hardware repair and technical service before, I'm going to agree that the 'average user' is going to be completely oblivious to the fact that his HDD might be dying untill it actually dies or this fact is pointed out to him by someone who's above average.  At that point, they're going to do one of two things.

1. take the whole thing to a repair store somewhere, where the computer will probably be declared 'too old, not worth saving' and an attempt will be made to sell them a new machine. (This is most likely)

2. If they're told there's an alternative, they'll go grab a spindle of blank CD's to burn off all their important documents and files.  Then they'll take the machine to tech-savvy relative to replace the drive and reinstall the OS and programs.

Granted, I've not had years and years of experience, but in my experience the 'average user' knows little more than how to send and receive an email, surf the web (unsafely), and type up and print out a word processing document.  I think most of us here forget what an 'average user' is because an 'average user' wouldn't go near these forums, and doesn't even know Linux exists.

The biggest problem I see with Linux in general (and let me make clear I LOVE linux and dread every time I have to boot into or use Windows for some reason.) is ussues that are honestly most likely not under the control of the distro developers.  Namely, sound, wireless, and video issues.  Untill the manufacturers of these components get on board and start making Linux drivers for their products and stop forcing us to use kludges like faking out the driver into thinking its in Windows (see ndiswrapper) or using proprietary drivers that were almost an afterthought by the manufacturer and may or may not work, Linux will have a very hard time getting any more mainstream.

---

### Post by fletchoid on 2008-11-28
> **3rdalbum said:**
> Yeah, I can. I considered writing a general-purpose "dd" frontend once. But for the drive cloning, I'm sure there is already a GUI out there. If you need something and can't find anything, I'll be happy to knock out a quick Pythoncard program for you if you send me a PM.

Thanks for the offer, however, I think you missed my point.  I was using the cloning of a drive as an example of a procedure that could be made very simple for the average (and maybe slightly above average) computer user.  I enjoy mucking around in my OS, but so far I have been only able to convert 2 other people to Linux, because the average user is intimidated by the learning curve.  What good is a cult if you can't make converts, and get them to wear new running shoes, and drink the koolaid?

As for gumming up the system with a lot of GUI crap.  You could have the basic install, and then have add on utilities to do these sorts of things.  Oh, wait! that's exactly how the OS is installed.... a basic install, and then you add programs here and there as you need them.  But or course you have to give them indecipherable names that sound like an autistic Swede made them up, and occasionally require arcane commands to get them working properly.

Sometimes I suspect that many Linux users are a bit elitist, and want to keep the club closed.  All we need is a secret handshake.

If we are to ever bring down the evil empire, er I mean reduce the influence of Micro$oft, the switch to and use of Linux needs to appear to be much simpler.  Just look at the success of the Mac ads.  The stuffy uptight PC guy, with his complicated, insecure OS is gently mocked by the laid back, unflappable cool guy.  Of course, this is a load of crap, but the ad campaign is working.  The sale of Macs is up.  Okay, they had a lot of help from Vista, but I think you get my point.  Now, they are advertising the Mac Genius, that will do all the hard work of transferring everything for you.  So simple. So easy. And people are buying into it.

Of course, if Linux ever becomes too popular, and becomes too easy to use, I will no longer be able to get free meals and beer for fixing a friend or neigbours computer.  Hmmmm, maybe we should just keep it a little mysterious.

---

### Post by banana jama on 2008-11-29
Nice review. I didn't have the same problems as you did with ubuntu though. Mines isn't slughish since it has four gigs of ram and unlike you my wifi did't work straight out of the box. I came to the world of linux not by choice but out of necessity. I'm a college student who's ms laptop crash and recovery drive was broke who also had an english paper due the next day. I ve been reading about ubuntu for a while but was always to afraid to make the switch but, I'm glad I did. I'm now 100% linux. And haven't used ms in over 2 weeks. I must admit linux wasn't the easiest thing to set up. Why wifi and graphic card did work but with the help of the forum I was able to set it up. This is one of the main reasons I belive ubuntu is better than microsoft because there is a strong community around the os. Ubuntu will probably never be very popular and that's ok because I actually works in our favor. With so few people using ubuntu and other distros linux users don't have to worry about about viruses and other malware. The devolpment of the linux kernal and oses like ubuntu that uses them is probably the best thing that has happen in software because it gives people a choice to choose something different than jobs and gates.

---

