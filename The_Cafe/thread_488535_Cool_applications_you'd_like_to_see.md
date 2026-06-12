---
title: "Cool applications you'd like to see"
date: 2007-06-30
forum: The Cafe
---

### Post by BLTicklemonster on 2007-06-30
I would like to see:

If I decide to reboot from Ubuntu to XP (or any other os I have listed in grub), I'd like a GUI that I could use to decide which OS to boot to, set it, and click restart. This program would edit Grub for me, setting that OS as the default OS so that I would not have to stop Grub in the boot cycle, and choose which OS I want to boot to. Granted, if I then decide to restart from XP and go back to Ubuntu, I'd have to interrupt grub, but still, it would be nice. Especially if I had more than one version of Ubuntu, or Linux, I could run this program on each of them.

I'd also like to see a GUI for Samba or whatever networking that would ask me specific questions, such as when I share a directory, "what user name/ password do you wish to use", and "do you wish to use this for all directories, or just this particular one", and of course, the option "no username, no password" with the caveat "you do realize that this makes your network insecure" added, of course. THAT RIGHT THERE WOULD BE BANG UP AND INCREDIBLY USEFUL TO EVERYONE WHO USES UBUNTU.

I'd like to see something that would, upon a kernel upgrade, check your graphics, and determine whether or not you will be able to do a clean reboot without killing X, and warn you. At this point, you can upgrade your graphics, and run a test for compatibility to verify that X will not spaz out on your on reboot. ANOTHER THING THAT WOULD BE INCREDIBLY USEFUL TO EVERYONE. (why does this not exist in the first place? Heck, anything along this line would be an improvement.)

If not the latter request, then I'd like X to automatically resolve issues, and get you to a usable desktop without stranding you in no man's land. (when it would normally say X would not start, it automatically seeks NV if you use NVidia, or other solutions, until it gets a viable alternative to get the user to the desktop.) GET THE USER TO THE DESKTOP AT ALL COSTS. Then have a prompt come up explaining what happened, and PLACE A LINK on the desktop to the related .log file instead of briefly commenting that a log files is buried in your operating system where you'll never find it, but here's where it is, but you'll never find it on your own, just post at Ubuntu forums and whine like a girly noob)

NO NEW USER TO UBUNTU SHOULD EVER BE STRANDED. THIS WILL/DOES RUN NEW PEOPLE OFF FASTER THAN IF BILL GATES MADE XP FREE TO EVERYONE.

(probably already a thread started like this, no?)

---

### Post by tgm4883 on 2007-06-30
> **BLTicklemonster said:**
> I would like to see:

If I decide to reboot from Ubuntu to XP (or any other os I have listed in grub), I'd like a GUI that I could use to decide which OS to boot to, set it, and click restart. This program would edit Grub for me, setting that OS as the default OS so that I would not have to stop Grub in the boot cycle, and choose which OS I want to boot to. Granted, if I then decide to restart from XP and go back to Ubuntu, I'd have to interrupt grub, but still, it would be nice. Especially if I had more than one version of Ubuntu, or Linux, I could run this program on each of them.


Suse does this.  You can select restart to (list of Operating systems).  and it will reboot to that operating system.  When you reboot again, it will then start up your default OS (Like ubuntu).  We just have to implement that here.  

There is also a command that you can enter that will boot up a different OS

> 
If not the latter request, then I'd like X to automatically resolve issues, and get you to a usable desktop without stranding you in no man's land. (when it would normally say X would not start, it automatically seeks NV if you use NVidia, or other solutions, until it gets a viable alternative to get the user to the desktop.) GET THE USER TO THE DESKTOP AT ALL COSTS. Then have a prompt come up explaining what happened, and PLACE A LINK on the desktop to the related .log file instead of briefly commenting that a log files is buried in your operating system where you'll never find it, but here's where it is, but you'll never find it on your own, just post at Ubuntu forums and whine like a girly noob)


This should be in gutsy.  It's called bullet-proof-x
bullet-proof-x [https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x)
All blueprints for gutsy [https://blueprints.launchpad.net/ubuntu/gutsy/](https://blueprints.launchpad.net/ubuntu/gutsy/)

---

### Post by BLTicklemonster on 2007-06-30
!!! Please tell me more about suse doing this!

And that's great news about bullet proof X. Can they make it something that can be put in repositories for older versions of ubuntu? It sure would be nice to extend this functionality to older versions!

---

### Post by slimdog360 on 2007-06-30
im hungry

---

### Post by tgm4883 on 2007-06-30
> **BLTicklemonster said:**
> !!! Please tell me more about suse doing this!

And that's great news about bullet proof X. Can they make it something that can be put in repositories for older versions of ubuntu? It sure would be nice to extend this functionality to older versions!

I don't know how suse does it, maybe ill put it in a vm with windows and try and tear it apart.

I dont think that bullet proof x can be backported, although you could probably force it in.  It requires xorg 7.3 and I dont think they backport xorg do they?

---

### Post by BLTicklemonster on 2007-06-30
:) what I mean was, why can't Ubuntu do this? (lol I forgot suse is a linux distro)

---

### Post by SoulinEther on 2007-07-01
I'd like to see a nice GUI backup program akin to System Restore/Time Machine, making differential saves of all the files in the mounted partitions / drives of your choosing without having to "spaz out" and restart your computer into some alternate operating system to access all the stuff on the drive.

Plus, you should be able to select individual files and recover them on their own; when you replace the file of your choice and you later decide to restore your computer to an earlier date which can be earlier or later than the date of your already-replaced file, you can get the choice to skip that file.

Basically, I want to see a method to select which files are and which files aren't recovered.

And the user should have a method of determining where the backups are done. In the / partition? /home? /media/sda1? A network location? All should be possible. Even a temp save to the ram, for some testing purposes.

Perhaps creating another miniature partition on your hard drive containing all the essential files to keep your computer running while the drives are unmounted.

But hey. We can't all get what we want.

---

### Post by bikeboy on 2007-07-01
Re: Can bullet-proof X functionality be built into older versions of Ubuntu? Probably not, since I think it relies on newer Xorg versions that are only just being worked into Gutsy. It would most likely be a too big a change to get the new X server into older releases.

---

### Post by tgm4883 on 2007-07-01
> **bikeboy said:**
> Re: Can bullet-proof X functionality be built into older versions of Ubuntu? Probably not, since I think it relies on newer Xorg versions that are only just being worked into Gutsy. It would most likely be a too big a change to get the new X server into older releases.

See Above 

> I dont think that bullet proof x can be backported, although you could probably force it in. It requires xorg 7.3 and I dont think they backport xorg do they?

---

### Post by Tundro Walker on 2007-07-01
If you're willing to shell out a little dough, I think you could post a bounty for your program/gui request, and someone might take you up on it.  A lot of the gui's out there are really just front-ends that utilize the CLI functions already on your computer.  Someone should be able to whip up something, it's just that if you want it done now (and to your specifications), you might need to pay for it.  Or, hop over to Launchpad and bounce the ideas off them.  They usually start projects and prioritize them off peoples ideas.

---

### Post by bikeboy on 2007-07-01
Sorry tgm4883, don't know how I missed that part. I thought I read that post of yours :/

---

### Post by red_Marvin on 2007-07-01
BLTicklemonster, forgive me for plugging my own program, but it sounds like [this]("http://ubuntuforums.org/attachment.php?attachmentid=7566&d=1143245379") app (source included) does what you need. It was originally posted in [this]("http://ubuntuforums.org/showthread.php?t=149666&highlight=grub") thread.

---

### Post by BLTicklemonster on 2007-07-01
Plug away, Marvin!

I used an editor in Borlan a while back, and played around and made a few things, but grew bored with it, and to be honest with you, if I could figure out any of these *(okay, bear with me, I have no "learnin' ", I'm one of those people who tinker with stuff, so I have no idea what proper terminology is)* editors to work, and if I understood what all was going on with the program I was looking at, I'm sure I could make some do the things I ask for. 

...or at least find a sure fire way to crash linux, lol.

---

### Post by tgm4883 on 2007-07-01
Found this script while googling.  The guy uses KDE, but from the looks of it, it should work with gnome.  I don't have a dual boot system anymore otherwise I would test it.

Credit to [http://robotics.caltech.edu/~klk/linux.html](http://robotics.caltech.edu/~klk/linux.html)

---

### Post by tekoholix on 2007-09-12
> **BLTicklemonster said:**
> I would like to see:

If I decide to reboot from Ubuntu to XP (or any other os I have listed in grub), I'd like a GUI that I could use to decide which OS to boot to, set it, and click restart. This program would edit Grub for me, setting that OS as the default OS so that I would not have to stop Grub in the boot cycle, and choose which OS I want to boot to. Granted, if I then decide to restart from XP and go back to Ubuntu, I'd have to interrupt grub, but still, it would be nice. Especially if I had more than one version of Ubuntu, or Linux, I could run this program on each of them.

I'd also like to see a GUI for Samba or whatever networking that would ask me specific questions, such as when I share a directory, "what user name/ password do you wish to use", and "do you wish to use this for all directories, or just this particular one", and of course, the option "no username, no password" with the caveat "you do realize that this makes your network insecure" added, of course. THAT RIGHT THERE WOULD BE BANG UP AND INCREDIBLY USEFUL TO EVERYONE WHO USES UBUNTU.

I'd like to see something that would, upon a kernel upgrade, check your graphics, and determine whether or not you will be able to do a clean reboot without killing X, and warn you. At this point, you can upgrade your graphics, and run a test for compatibility to verify that X will not spaz out on your on reboot. ANOTHER THING THAT WOULD BE INCREDIBLY USEFUL TO EVERYONE. (why does this not exist in the first place? Heck, anything along this line would be an improvement.)

If not the latter request, then I'd like X to automatically resolve issues, and get you to a usable desktop without stranding you in no man's land. (when it would normally say X would not start, it automatically seeks NV if you use NVidia, or other solutions, until it gets a viable alternative to get the user to the desktop.) GET THE USER TO THE DESKTOP AT ALL COSTS. Then have a prompt come up explaining what happened, and PLACE A LINK on the desktop to the related .log file instead of briefly commenting that a log files is buried in your operating system where you'll never find it, but here's where it is, but you'll never find it on your own, just post at Ubuntu forums and whine like a girly noob)

NO NEW USER TO UBUNTU SHOULD EVER BE STRANDED. THIS WILL/DOES RUN NEW PEOPLE OFF FASTER THAN IF BILL GATES MADE XP FREE TO EVERYONE.

(probably already a thread started like this, no?)

You, sir, are an ID10T, and I can thoroughly explain why, even with my own admitted levels (though less than your own) of ID10CY:

First and Foremost: You're attempting to cater to users that have NO BUSINESS in front of a computer to begin with, let alone a linux-based sys (or any other that requires an educated user), unless YOU, as the one who introduced them to it, are FULLY WILLING to hold their hand thru the ENTIRE LEARNING CURVE, AND ALL THE MAINTENANCE AND UPDATES.

Second: Who, with a brain, dual-boots anymore? What with all the virtualization-ware available?  Where've ya' been?

Third: SAMBA GUI?  Are you kidding?  It's all GUI-fied on MY Feisty system...  Where've ya' been?

Fourth: FOSS video drivers DO WORK after a Kernel upgrade, so far as I've ever seen (in nearly 3 years of Linux-Exclusive use). On the other hand, NON-FREE Video drivers are NOT A SUPPORTED part of Ubuntu, and when you install them, YOU DO SO AT YOUR OWN RISK.  How dare you ask the developers of a FREE AND OPEN-SOURCE OS to PREVENT YOU OR SOME OTHER ID10T from doing damage to YOUR/THEIR OWN SYSTEM, due to actions that YOU TOOK ON YOUR OWN (such as installing closed-source s/w)?????

Coming from a COMPUTER-TECH, who works EVERY DAY with the very customers you are asking us to cater to, I say (and HOPE the community agrees) LET THEM GO BACK TO THE INSECURITIES AND INSTABILITY OF WINDOZE, if they don't like what they get with Linux, of if they don't have a promoting Tech, willing to HOLD THEIR HAND until they're educated enough to use GOOGLE AND UBUNTUFORUMS.ORG.

> NO NEW USER TO UBUNTU SHOULD EVER BE STRANDED. THIS WILL/DOES RUN NEW PEOPLE OFF FASTER THAN IF BILL GATES MADE XP FREE TO EVERYONE.
Then, don't abandon them...  'Nuff said...

---

### Post by tgm4883 on 2007-09-13
> **tekoholix said:**
> You, sir, are an ID10T, and I can thoroughly explain why, even with my own admitted levels (though less than your own) of ID10CY:

First and Foremost: You're attempting to cater to users that have NO BUSINESS in front of a computer to begin with, let alone a linux-based sys (or any other that requires an educated user), unless YOU, as the one who introduced them to it, are FULLY WILLING to hold their hand thru the ENTIRE LEARNING CURVE, AND ALL THE MAINTENANCE AND UPDATES.

Second: Who, with a brain, dual-boots anymore? What with all the virtualization-ware available?  Where've ya' been?

Third: SAMBA GUI?  Are you kidding?  It's all GUI-fied on MY Feisty system...  Where've ya' been?

Fourth: FOSS video drivers DO WORK after a Kernel upgrade, so far as I've ever seen (in nearly 3 years of Linux-Exclusive use). On the other hand, NON-FREE Video drivers are NOT A SUPPORTED part of Ubuntu, and when you install them, YOU DO SO AT YOUR OWN RISK.  How dare you ask the developers of a FREE AND OPEN-SOURCE OS to PREVENT YOU OR SOME OTHER ID10T from doing damage to YOUR/THEIR OWN SYSTEM, due to actions that YOU TOOK ON YOUR OWN (such as installing closed-source s/w)?????

Coming from a COMPUTER-TECH, who works EVERY DAY with the very customers you are asking us to cater to, I say (and HOPE the community agrees) LET THEM GO BACK TO THE INSECURITIES AND INSTABILITY OF WINDOZE, if they don't like what they get with Linux, of if they don't have a promoting Tech, willing to HOLD THEIR HAND until they're educated enough to use GOOGLE AND UBUNTUFORUMS.ORG.


Then, don't abandon them...  'Nuff said...

It's great that you brought back a month and a half old thread to post this, it really helps.  I really enjoyed it, it made me laugh.  

Is it wrong for someone to want features that are not essential to everyone?  I see a lot of features in Ubuntu that are not needed, but they are included anyway.  Do I rant and rave and scream at the developers?  No, I do not.   Lots of people still dual boot as virtualization technology is not where they need it to be for some things.

Pandering to the noobs is something that Ubuntu does well.  Did you forget that Ubuntu is linux for human beans?  Are this people somehow beneath that?  Or perhaps you thought you were [here]("http://forums.gentoo.org/")

And you want them to go back to Windows, what's up with that?  I almost never think people should run away from Linux back to Windows.  The exception to that is when some mis-informed idiot computer tech friend of theirs practically forces them to install linux.  You know the kind, the ones who always talk about how great Linux is, and it's free, and Windows sucks (and they probably spell it Windoze, Winbloze, and M$, MicroShaft, etc.  Which BTW, is pretty lame).  It's these individuals that force Linux down peoples throats that don't know any better.  You can tell which people have no business being here, they come here, and in the first 5 posts start saying how bad linux is and how not ready for the desktop it is and that they are going back to windows.  I don't blame them though.  I blame people like you who have some superiority complex and need to show other people how smart you are by running linux.  Same type of people who live and die about blu-ray vs HDDVD and Xbox 360 vs PS3. 

I guess what I really should be saying is thank you.  Thank you for only posting 5 times in almost 2 years.  Keeps me from having to read your posts in the support forums.

---

### Post by igknighted on 2007-09-13
> **tgm4883 said:**
> It's great that you brought back a month and a half old thread to post this, it really helps.  I really enjoyed it, it made me laugh.  

Is it wrong for someone to want features that are not essential to everyone?  I see a lot of features in Ubuntu that are not needed, but they are included anyway.  Do I rant and rave and scream at the developers?  No, I do not.   Lots of people still dual boot as virtualization technology is not where they need it to be for some things.

Pandering to the noobs is something that Ubuntu does well.  Did you forget that Ubuntu is linux for human beans?  Are this people somehow beneath that?  Or perhaps you thought you were [here]("http://forums.gentoo.org/")

And you want them to go back to Windows, what's up with that?  I almost never think people should run away from Linux back to Windows.  The exception to that is when some mis-informed idiot computer tech friend of theirs practically forces them to install linux.  You know the kind, the ones who always talk about how great Linux is, and it's free, and Windows sucks (and they probably spell it Windoze, Winbloze, and M$, MicroShaft, etc.  Which BTW, is pretty lame).  It's these individuals that force Linux down peoples throats that don't know any better.  You can tell which people have no business being here, they come here, and in the first 5 posts start saying how bad linux is and how not ready for the desktop it is and that they are going back to windows.  I don't blame them though.  I blame people like you who have some superiority complex and need to show other people how smart you are by running linux.  Same type of people who live and die about blu-ray vs HDDVD and Xbox 360 vs PS3. 

I guess what I really should be saying is thank you.  Thank you for only posting 5 times in almost 2 years.  Keeps me from having to read your posts in the support forums.

No need to insult Gentoo like that ;)

I don't see any reason why we couldn't port suse's reboot app.  Seems like a really good app to port as well.

@ teko: Where have you been man, the ONLY reason worth having windows at all is to run games, and you can't do that virtualized... so why are you so far behind d00d?

---

### Post by tgm4883 on 2007-09-13
> **igknighted said:**
> No need to insult Gentoo like that ;)

I don't see any reason why we couldn't port suse's reboot app.  Seems like a really good app to port as well.

@ teko: Where have you been man, the ONLY reason worth having windows at all is to run games, and you can't do that virtualized... so why are you so far behind d00d?

heh, I reread that part and it does kinda sound like im insulting gentoo.  What I meant by it was that Ubuntu tends to be easier to run than Gentoo, not that Gentoo is full of mean spirited people who just condemn noobs and shout and scream at one another.

---

### Post by igknighted on 2007-09-13
> **tgm4883 said:**
> heh, I reread that part and it does kinda sound like im insulting gentoo.  What I meant by it was that Ubuntu tends to be easier to run than Gentoo, not that Gentoo is full of mean spirited people who just condemn noobs and shout and scream at one another.

Oh i know, i was just joking around... it was a bit of a backhanded insult @ teko.

Honestly, Gentoo does (and partially deservedly... this coming from a big gentoo fan) have a 1337ist reputation.  But Teko sounds like a cross between Gentoo 1337ist and FSF zealot... so he must be a GNU/HURD user!

---

### Post by tgm4883 on 2007-09-13
> **igknighted said:**
> Oh i know, i was just joking around... it was a bit of a backhanded insult @ teko.

Honestly, Gentoo does (and partially deservedly... this coming from a big gentoo fan) have a 1337ist reputation.  But Teko sounds like a cross between Gentoo 1337ist and FSF zealot... so he must be a GNU/HURD user!

No, teko is too good for that.  He just boots the kernel and only has 1 and 0 on his keyboard

---

### Post by igknighted on 2007-09-13
> **tgm4883 said:**
> No, teko is too good for that.  He just boots the kernel and only has 1 and 0 on his keyboard

LOL!

---

### Post by tekoholix on 2007-09-13
> It's great that you brought back a month and a half old thread to post this, it really helps.My apologies to all.  Not to make excuses, but I wasn't exactly sober, I had a few other, unrelated frustrations working my nerves last night, and I inappropriately imposed them upon this community.  It's not too often that I embarrass myself, but when I do, I do it big...  Hadn't even had a clue how old the thread was...

> Pandering to the noobs is something that Ubuntu does well.  Did you forget that Ubuntu is linux for human beans?Agreed...  I've played with many different distro's, and of them all, this community has been, far and away, the most supportive.> Or perhaps you thought you were [here]("http://forums.gentoo.org/")  Had never tried Gentoo, so I was confused by your reference to it.  Guess I'm glad I hadn't...  

> And you want them to go back to Windows, what's up with that?  I almost never think people should run away from Linux back to Windows.  The exception to that is when some mis-informed idiot computer tech friend of theirs practically forces them to install linux.Again, agreed...  Very few of my customers have tried Linux, as yet.  Thus my ONLY reason for continuing to keep a windows VM, at all (to support them).  Of the ones that have, however, only one has gone back.  Guess I've just been lucky. 
> I guess what I really should be saying is thank you.  Thank you for only posting 5 times in almost 2 years.  Keeps me from having to read your posts in the support forums.Honestly, most of my interaction with the forums is in a purely learning mode.  I usually don't post unless I can contribute, somehow.  I can't blame ya' for not wanting to see more of me, after this one...

I love Ubuntu, and have since day one.  I hate seeing anybody going back to windows, but they do, and you're right.  Posts like this are as much to blame for that as anything...
> @ teko: Where have you been man, the ONLY reason worth having windows at all is to run games, and you can't do that virtualized... so why are you so far behind d00d?
Gaming has never been something I've engaged in, so I had not considered the need for dual-boot, for that purpose. Is gaming really that bad, via VM?  I hadn't realized...  I am, just recently, getting hooked on some of the many games freely available for Ubuntu, mostly for my kids' sake, but I haven't played any windows games, in years...

I never thought I'd drink and drive...  Hadn't considered the info-super-highway...

Apologies, all around...

Paul Harmor
Tekoholix.Computer.Services

---

### Post by igknighted on 2007-09-13
> **tekoholix said:**
> Gaming has never been something I've engaged in, so I had not considered the need for dual-boot, for that purpose. Is gaming really that bad, via VM?  I hadn't realized...  I am, just recently, getting hooked on some of the many games freely available for Ubuntu, mostly for my kids' sake, but I haven't played any windows games, in years...

I never thought I'd drink and drive...  Hadn't considered the info-super-highway...

Apologies, all around...

Paul Harmor
Tekoholix.Computer.Services

Apology accepted as far as I am concerned... we all make mistakes

FWIW, a virtual machine can emulate the processor, but is unable to properly emulate a 3d capable video card, so there is no 3d capabilities in VM.  There are a couple extremely experimental packages, but nothing ready yet.  You can play older games that don't require hardware acceleration just fine (Age of Empires 2 for example works great), but thats about it.

---

### Post by tgm4883 on 2007-09-13
> **tekoholix said:**
> 
I never thought I'd drink and drive...  Hadn't considered the info-super-highway...

Apologies, all around...

Paul Harmor
Tekoholix.Computer.Services

Accepted.  I withdrawl my comments about you.  We have all done dumb things while intoxicated.

---

### Post by luvdemheels on 2007-09-13
I really nice e-mail client similar to outlook would be great. That is one of the main things I need and don't have yet. Compatibilty with exchange would be an even better bonus.

(please no evolution references - too many problems I have seen)

---

