---
title: "To those of you who tells skeptical win users 'JUST install Ubuntu'"
date: 2009-10-25
forum: Testimonials &amp; Experiences
---

### Post by angry_norwegian on 2009-10-25
When telling Linux users that I haven't installed Linux because of userfriendliness issues, the last couple of years I've heard 'but you can just install Ubuntu. It just works' and similar messages.

So I've tried it a couple of times, and installed it first on my gf's laptop, and had many problems with it.
I tried again on my desktop, and encountered many problems there as well. Experienced Linux users seem baffled by this, as by their standards Ubuntu is a walk in the park.

Therefore I have written down a few of the problems I've had on the latest install of 9.04.

Before you read it, this is not me bashing Linux, telling you Windows is better, blaming someone else for my ignorance or anything like that. I'm not seeking advice on solving the different problems I list here, I'll do that later if I can't fix it myself.

**[COLOR=Red]What I want with this post is to tell Linux proponents to NOT oversell Ubuntu to experienced windows-users.[/COLOR]** Don't say "you can JUST install ubuntu". Rather say something like: > "Remember that as an experienced Windows user, you are used to knowing solutions to a lot of problems. This may not be the case in Ubuntu. At first it may be frustrating to start at square one, but as with everything else, there is a learning curve. If you're a little patient, you'll find Ubuntu as user-friendly and configurable than Windows, if not more'.The following describes the process of installing Ubuntu, getting sound in system and movies and making flash movies work:

---

***Problems with ubuntu***:

Had to install 3 or 4 times before the OS loaded after reboot. Checked in BIOS every time that the correct hard disk was set as boot device.

3 plug-ins for SWF listed by Firefox, but none were actually found.
No Java in browser -> googling 'ubuntu Java Firefox'. Reading lots of suggestions that didn't help. trying a solution. Didn't work. Trying something else. Nothing worked.

Updating solved the above 2.

No sound on HDMI. Googling 'no sound hdmi ati ubuntu' and similar. Reading 10-15 web pages on the subject, trying several 'solutions' to no avail. Finally downloaded the proprietary driver via synaptic -> envyFD or something, which solved the sound problem.

A couple of reboots.

New problem: Resolution has changed from display native 1280x768 to a fuzzy 1920x1200. Display option in system->preferences does not respond, but hogs 100% CPU. Rebooting a couple of times doesn't help. Googling 'change resolution ubuntu ati driver', 'change resolution ubuntu terminal FDLRX' etc. Finding the commmand xrandr -s 1280x768, which solved it until next reboot. Now I have to open terminal after every reboot and enter that command. Settling with this as a solution.

New problem: Tearing when playing a movie in Ubuntu's standard player. Same problem in Mplayer.

ALso, no sound in Mplayer. The settings in mplayer doesn't have an HDMI option. Googling 'mplayer hdmi no sound'. Trying a solution involving editing the mplayer config file. Navigating to it in GUI, editing it, to discover i can't save it. Googling the error message. Editing it via terminal and sudo. This doesn't help, and now there is no sounds whatsoever in Ubuntu.

I revert to the backed up mplayer settings file. Back to square one, with system sounds, but no sound in mplayer. Giving up for now.

After updating the system, I can install swfdec in Firefox. However, flash movies in youtube plays without sound, and at 0.1 fps. Trying to remove the plugin swfdec in firefox tools->manage content plug-ins. Right clicking doesn't bring up any context menu, and pressing Delete on my keyboard does nothing. Googling 'remove firefox plug-in ubuntu'. Oh, surprise, surprise, I have to use terminal. The ubuntu forum answer tells me to cd to .mplayer\plugins, but I don't know where that is. I give up, and just try to install Adobes plugin without removing the old one. I get an error message telling me it's already installed, but that's not true.

Etc. I'll spend a couple more days trying to get everything right, probably having more problems like the above. Remember, I'm not complaining, I just want experienced Linux users to stop telling people they can 'just install ubuntu'. That's overselling it, and that's not a good strategy for gaining market shares. Rather, if people aren't prepared for the fact that Linux will take some work getting used to, but they are told it will be effortless, they are more likely to give up and go back to MS.

---

### Post by sblunix on 2009-10-25
Those are all easily solvable solutions, and if you would've posted that in the forum you would've gotten the problem fixed in about 5 minutes, on your first boot of ubuntu, you always install all the updates and use the necessary proprietary drivers, that's not any different from windows, so you can't act like this is User-unfriendliness... For your flash/java problems, once again a quick post in the forums would inform you that all you have to do is install java on your computer and install flash player on your computer, which the community would help you do, the same goes for windows, you still have to install java and flash if you want to use each, so this isn't an unfriendliness issue, for your resolution problem, theres a configuration file on your computer which you can set to use your preferred resolution, once again, the community would help you through this. For your sound error, in case you haven't noticed, you're not the only one with that problem, if you looked at the forum, EVERY DAY there are at least 10 posts discussion how to easily fix your sound driver, and for your swfdec issue, This is because swfdec is open source and experimental, you should've just asked the community to tell you how to install Adobe Flash.

Before you say that "ask the community" is too much work or something of that sort, new Windows users face the same problems, and much more, and they have to spend a long time using google to find out how to fix it, while one post on the forums and 5 minutes on Ubuntu will quickly fix all your problems. I'm sorry that you don't understand that the Ubuntu Community is there to explain to you how Ubuntu is different from Windows, but it is, and in many ways, superior. All your problems have been faced and fixed by windows users, and that can just as easily be done on Ubuntu, just in a different (simpler usually) way.

---

### Post by Mark Phelps on 2009-10-25
Ok, you really DO have a valid issue ... but ...

Traditionally, folks have come to Linux interested in experimenting with a different OS and willing to learn new skills to tune it and customize it.  But with the disaster that was Vista, we got LOTS of folks coming here looking for a free version of MS Windows (could tell by the number of folks demaning to know how to install Wine to run all their Windows programs) -- and most, if not all of them, were unwilling to learn anything.  Many demanded that we NOT reply with any of that "Linux jargon" (meaning, command line instructions).

Ubuntu has always been, and to a large degree will remain, a solution for the "do-it-yourself" crowd.  And while some things, like installation and upgrading, and now, application installation, have been made easier over the years, Ubuntu never has been, and most probably, never will be a free version of MS Windows -- for the "I just want to point-and-click and not learn anything about computing" crowd.

You'd be amazed at the number of folks coming here (mostly from MS Windows) who did something destructive to their machines, complaining about lack of "warnings" -- and when we tell them the warnings were clearly displayed, reply, "Yeah, but I never read those things!"

Which is why, I steadfastly advise EVERYONE to use the LiveCD approach first -- before installing ANY Linux distro.  Anything that does not work with the LiveCD, and is not easily fixed by downloading a package and installing it, poses potential disaster after installation.

And finally, as an ardent supporter of Linux and Ubuntu, I have to say that I am NOT interested in increasing "market share".  We're not in the business of making money from our products -- which is what increasing market share is really all about.  We're in the business of offering people an OS alternative to Microsoft and Apple -- an alternative that presumes the customer is willing to learn some new skills.

With the recent announcement of Windows 7, and (as I have experienced personally) the really enormouse strides in performance and productivity that 7 has made over the initial release of Vista, I expect that we will start seeing a large number of "Going back to MS ..." kinds of posts.

Personally, my position has always been, and always will be, use WHAT WORKS BEST FOR YOU.  So, if that means that OUR community here goes back to being hobbyists, that might make Canonical unhappy, but not me.

---

### Post by Topsiho on 2009-10-25
Angry_norwegian has done a lot to solve his/her problems with Ubuntu, installing and after install. Some people have these problems, as I also found out once, installing Ubuntu on my daughters computer, next to Vista (one has to do the repartitioning in Vista, as Vista appears to check the partition sizes on boot, and does not boot when it finds them altered by another application such as GParted).
The good thing is: [s]he has learned a lot doing so.

When I used Windows (long tome ago) I ran in all sorts of problems all the time (being sort of an inquisitive super user allways), and if I was lucky I could read how to solve them in magazines, this luck did not happen often. Solutions were in most cases very mysterious, and really dangerous, involving editing the register. Google (and before that Altavista) did not yet exist, or were not as usable as Google is now.

[Have you ever re-installed a version of Windows? That is a nightmare. After the install trillions of updates, and having to find and install the drivers of most anything, even mouse and keyboard, and so on. Hoping they are still there somewher on the internet.]

Google now is a very good friend, and using forums as this one, specially for Ubuntu, can be great. Not always, I'am afraid, but quite often someone answers your question quite usefully.

However: this very forum has one great disadvantage: it is too popular. If you ask a question in a very short time it is not on page 1 anymore, but it soon disappears to page 2, 3 and so on. So you have to "bump" your question to get it in a visible place, if no one responds soon enough...

Topsiho

---

### Post by KayakJim on 2009-10-25
If you really want a Linux install that works automatically with sound, video, and other working things, try [Linux Mint]("http://www.linuxmint.com/") instead.

While Ubuntu is a great general distribution, for an actually fully functional desktop Mint is the way to go.

---

### Post by howefield on 2009-10-25
> **angry_norwegian said:**
> Ijust want experienced Linux users to stop telling people they can 'just install ubuntu'. That's overselling it, and that's not a good strategy for gaining market shares. Rather, if people aren't prepared for the fact that Linux will take some work getting used to, but they are told it will be effortless, they are more likely to give up and go back to MS.

Please don't underestimate the smidgeon of responsibility the recipient has to look after themselves and do the required research, before choosing to accept any such "advice" :)

---

### Post by running_rabbit07 on 2009-10-25
Linux Mint **IS** Ubuntu with a green theme and ubuntu-restricted-extras installed.

---

### Post by KayakJim on 2009-10-25
> **running_rabbit07 said:**
> Linux Mint IS Ubuntu with a green theme and ubuntu-restricted-extras installed.

I know. My statements were in regard to the OP's system fully working "out-of-the-box" as it seems they wanted instead of having to install a few extra packages after initial installation.

---

### Post by jc0811 on 2009-10-25
> **KayakJim said:**
> If you really want a Linux install that works automatically with sound, video, and other working things, try [Linux Mint]("http://www.linuxmint.com/") instead.

While Ubuntu is a great general distribution, for an actually fully functional desktop Mint is the way to go.

I have tried Linux Mint myself but if feels like a distribution that has permanent training wheels and those training wheels will never come off. 

I found a better distribution. Just go to 

[http://distrowatch.com/table.php?distribution=superos](http://distrowatch.com/table.php?distribution=superos)

this guy just took the regular Ubuntu distribution and remade it with all the necessary codecs, flash, java etc. out of the box. Check it out.

---

### Post by running_rabbit07 on 2009-10-25
I find it easier just for do a search and find one of the many tutorials for setting up a newly installed system. With about five commands, I can set up a functionally happy, user friendly system. Provided that the machine that the installation is on, is compatable with Ubuntu/Linux.

---

### Post by bruno9779 on 2009-10-25
When I switched to Ubuntu 4 years ago, I just installed.

M$ itself convinced me to with Vista.

Not everything worked out of the box, but there has not been an issue that I could not resolve here on the forums.

On my rig Ubuntu just works. Win-dose just doesn't.

---

### Post by solwic on 2009-10-25
> **bruno9779 said:**
> When I switched to Ubuntu 4 years ago, I just installed.

M$ itself convinced me to with Vista.

Not everything worked out of the box, but there has not been an issue that I could not resolve here on the forums.

On my rig Ubuntu just works. Win-dose just doesn't.

You know, a lot of people gripe about Ubuntu not working OOTB.  But, seriously, I think it ought to be required for a person to install their own OS.  You learn a lot about how a computer works, about how your OS works, and you gain some general knowledge and experience in the process.  

If Ubuntu started working OOTB, I'd probably switch to Debian or Zenwalk or some other distro that doesn't.  I *like* understanding how my system works, and I *like* tinkering with it.  

I also think that there should be one class in every college, one that is required, where students are given a severely broken computer (software-wise, not hardware...but maybe both is a better idea) and their only objective is to fix it.  No books, no lectures...just Google and a borked system.

I think you'd learn so much more doing that than you would studying chapters and taking tests.  Of course, maybe I'm partial to that because that's how I learned....

Anyway....

---

### Post by steveneddy on 2009-10-26
Hey - it's another "I installed the latest unstable version of Ubuntu and can't figure it out! This sucks!" post by a user with ONE POST! and this is it!

To the OP (original poster) : 

Please read the forums and if you are actually confused, post a help thread. I believe your issues are easily solvable, and if you are still confused or lost, post in your help thread that you are confused or lost. None of us started with Ubuntu super powers. We all started where you are right now. I still post help threads. We all do. But please, post a help thread in the proper section and I guarantee you will get all the help you need/want.

My opinion follows, and is worth totally nothing:

In my experience, those that say they are "experienced Windows users" aren't actually very experienced computer users at all.

I mean, in my eyes, an **experienced** user is one who is familiar with partitioning a hard drive, installing various operating systems and having most of the skills that a basic A+ person would have.

You may indeed have those "skills", but you need to realize that most of the knowledge that you acquired in the Windows world is worthless in Ubuntuland.

1. Try a more stable version of Ubuntu, like 8.10.

2. Post a help thread

3. Check you hardware for compatibility. Laptops are hard to get any OS running, especially Windows, unless the hardware is well supported.

4. Look at [www.system76.com]("http://www.system76.com")

5. Look at the links in my sig.

6. Keep trying. Never give up, never surrender!

---

### Post by steveneddy on 2009-10-26
> **irun said:**
> you know, a lot of people gripe about ubuntu not working ootb.  But, seriously, i think it ought to be required for a person to install their own os.  You learn a lot about how a computer works, about how your os works, and you gain some general knowledge and experience in the process.  


Anyway....

+1

---

### Post by running_rabbit07 on 2009-10-26
> **steveneddy said:**
> Hey - it's another "I installed the latest unstable version of Ubuntu and can't figure it out! This sucks!" post by a user with ONE POST! and this is it!

To the OP (original poster) : 

Please read the forums and if you are actually confused, post a help thread. I believe your issues are easily solvable, and if you are still confused or lost, post in your help thread that you are confused or lost. None of us started with Ubuntu super powers. We all started where you are right now. I still post help threads. We all do. But please, post a help thread in the proper section and I guarantee you will get all the help you need/want.

My opinion follows, and is worth totally nothing:

In my experience, those that say they are "experienced Windows users" aren't actually very experienced computer users at all.

I mean, in my eyes, an **experienced** user is one who is familiar with partitioning a hard drive, installing various operating systems and having most of the skills that a basic A+ person would have.

You may indeed have those "skills", but you need to realize that most of the knowledge that you acquired in the Windows world is worthless in Ubuntuland.

1. Try a more stable version of Ubuntu, like 8.10.

2. Post a help thread

3. Check you hardware for compatibility. Laptops are hard to get any OS running, especially Windows, unless the hardware is well supported.

4. Look at [www.system76.com]("http://www.system76.com")

5. Look at the links in my sig.

6. Keep trying. Never give up, never surrender!

He doesn't want help, we wants it already done for him. People don't realize that if Ubuntu packaged everything in the ISO to make each system install correctly, it would fill at least a few DVDs.

I seriously doubt the OP will ever post again. He is just flame baiting.

---

### Post by Tamlynmac on 2009-10-26
> running_rabbit07
He doesn't want help, we wants it already done for him. People don't realize that if Ubuntu packaged everything in the ISO to make each system install correctly, it would fill at least a few DVDs.

I seriously doubt the OP will ever post again. He is just flame baiting. 	

Ya think????

If they actually wanted help, why would they post in the T&E and not the Help Sections? As we all know, the T&E is not a help section and I doubt anyone would use it as such. :rolleyes:

---

### Post by SirBismuth on 2009-10-26
I do apologise in advance, as I am probably troll-feeding here.

When I first prepared to install Ubuntu, I went into it expecting things to NOT just work, having come from OSes like FreeBSD.  Well, I was pleasantly suprised when 90% percent of things did indeed just work OOTB when I first intalled Ubuntu.

When things didn't work, I found these forums, and/or used Google.  Then, after a bit of research, things that didn't just work, now just worked! :)

I think that the mindset that you approach Ubuntu, or any distro, with, makes a huge difference.

B

---

### Post by mdsmedia on 2009-10-26
> **SirBismuth said:**
> I do apologise in advance, as I am probably troll-feeding here.

When I first prepared to install Ubuntu, I went into it expecting things to NOT just work, having come from OSes like FreeBSD.  Well, I was pleasantly suprised when 90% percent of things did indeed just work OOTB when I first intalled Ubuntu.

When things didn't work, I found these forums, and/or used Google.  Then, after a bit of research, things that didn't just work, now just worked! :)

I think that the mindset that you approach Ubuntu, or any distro, with, makes a huge difference.

B
I don't remember whether I expected it to work or not. I burned a LiveCD. I was impressed. I found a HowTo on dual-booting. It worked. Ubuntu became my main OS.

I came into Linux with an open mind. Some things that only work in Windows, only work in Windows. I decide whether they are a priority. If not, I leave them alone. I live with the limitations that may be found in Linux. I look for workarounds. I don't want to boot into Windows, so if I don't need to or don't want to, I don't.

I accept that some things are not as easy to do in Linux. If they're important enough, I try to get them to work in Linux. if they're essential, I boot into Windows until I find a solution in Linux.

I'm still a Linux newb, so I accept MY limitations, but I don't expect more of Linux than what I can get out of it.

I recently spoke to a friend who I would consider a Windows newb who likes to download and try things. I reinstalled Windows for him a few months ago. I needed Ubuntu during the installation, to backup files for him, and to restore them. I've mentioned Ubuntu/Linux to him, but I've never pushed him to install it. I've laughed at some of the problems he experiences. This time I've almost persuaded him to try Linux. To dual-boot. I've explained what I think are the weaknesses for a Windows user. I've explained what I think are the strengths. I left it up to him. I don't think Ubuntu "just works" but it does so at least as well as Windows, if not better.

---

### Post by 3rdalbum on 2009-10-26
A lot of us do say "You can use Ubuntu - it's different to Windows and you will need to relearn some things, but ultimately it's just as easy to use".

From the perspective of someone who has used Ubuntu for a few years, many of your problems are genuinely easy to solve, but I guess it's easy to forget that new users aren't familiar with things and will try to solve problems differently to someone who is familiar with all the tools.

---

### Post by armandh on 2009-10-26
95% of my Ubuntu installs have been slam dunks.(2'6" Xs)

about 1% will never work right 
and it is no use beating one's self over the head about it.

the more esoteric the hardware the more likely the problem.

my DDS-32 printer with a win 2K beta driver is not supported by Vista but I got it to work over the net under Ubuntu. 
(factory support is on a par with Studebaker)

here are a few Ive encountered

had to remount the HDD in a 5" bay adapter so the primary IDE line would service it and the optical. [no boot elsewhere except the floppy]

Intel mini ATX board with celleron and SiS chipset-video
9.10 works @ 800x600 or less. higher rez has sparkly lines
xp ok with SiS driver

cd/dvd drives worn out or bad enough OOTB.

nearly dead bios batteries

suspected lightning damage, 2 PCI slots don't work, on another the on board lan was intermittent, solved by turning off and using add on.

the list, if everyone adds theirs, is endless.
hardware and driver issues aside,
Ubuntu is still as easy as Linux gets!

---

