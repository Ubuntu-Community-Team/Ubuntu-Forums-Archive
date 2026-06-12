---
title: "Sadly, back to XP."
date: 2007-05-23
forum: Testimonials &amp; Experiences
---

### Post by gnomic on 2007-05-23
I built my new machine to run Ubuntu. ASUS P5NSLI, E6800 duo core, 2G RAM, 1TB Disk, an Nvidia 7300 LE PCI video card. And I went to install 7.04.

Kernal corrupt? WTF? Works on my other machine. OK - boot 6.10 and install, upgrade, and ta-da, working machine. Very easy and quick - less trouble that installing XP in fact. :D

But low video res (1Kx768 at 50hz?). I can't live with that.:o

And that's where the whole story goes bad. I get dumped to the command line, spend hours looking for the answer - fine several - and eventually give up after investing a week trying to get the video card to work.

I've been doing this for a few years. I've gone through AppleDOS, CP/M, System III and IV Unix, every version of MSDOS and Windows, all versions of OS/2, and most other OSs on the market. I've been a sysadmin, a programmer, and know my way around an operating system. Understand - I can fix this. I'm not intimidated by all the cryptic error messages. I'm just frustrated that I have to spend all this time on such a simple problem.

In future releases, I hope you spend some time fixing the fault isolation and recovery process. I really dont care as a user about all the nits. I just want it to work. (Yea, I coulda bought a Mac. But I believed in you). Fixing the support forums will help as well. There is a flood of info on the net and finding the right solution is damn near impossible for anyone but an expert who is intimately familiar with the versions and histories to figure it all out.  

I was yours to lose and you lost me. No one is more sad about this than I am.:(

---

### Post by jrusso2 on 2007-05-23
I don't understand, did the Nvidia drivers not provide better resolution?  Or could you not get them to install?

---

### Post by juxtaposed on 2007-05-23
That's unfortunate - sorry you had problems.

Have fun with windows and consider giving Linux a try when you think the problems might be solved (Ubuntu development, especially between the versions, is very visible).

---

### Post by discmaster on 2007-05-23
I understand gnomic, I truly do. I don't have the same issues as you have, but I am finding this to be a major problem...
> Fixing the support forums will help as well. There is a flood of info on the net and finding the right solution is damn near impossible for anyone but an expert who is intimately familiar with the versions and histories to figure it all out

AMEN BROTHER!!!

---

### Post by nubutu on 2007-05-23
>I built my new machine to run Ubuntu. ASUS P5NSLI, E6800 duo core, 2G RAM, 1TB Disk, an Nvidia 7300 LE PCI video card. And I went to install 7.04.

You shouldn't, it's not a stable release. For somebody with no experience it seems more sensible to go for the most tested ones.

>Kernal corrupt? WTF? Works on my other machine. OK - boot 6.10 and install, upgrade, and ta-da, working machine. Very easy and quick - less trouble that installing XP in fact.

Interesting.

>But low video res (1Kx768 at 50hz?). I can't live with that.

Me neither, if I've got better resolutions available.

>And that's where the whole story goes bad. I get dumped to the command line, spend hours looking for the answer - fine several - and eventually give up after investing a week trying to get the video card to work.

Obviously it wasn't enough or you looked in the wrong places.

>I've been doing this for a few years. I've gone through AppleDOS, CP/M, System III and IV Unix, every version of MSDOS and Windows, all versions of OS/2, and most other OSs on the market. I've been a sysadmin, a programmer, and know my way around an operating system. Understand - I can fix this. I'm not intimidated by all the cryptic error messages. I'm just frustrated that I have to spend all this time on such a simple problem.

With that experience you should be able to fix it in no time. There are kids in this forum who do it without any effort.

>In future releases, I hope you spend some time fixing the fault isolation and recovery process.

Who are you talking to? Most of us don't fix anything, we're not developers.

> I really dont care as a user about all the nits. I just want it to work. 

Use Windows, it just works--although how it's a different discussion--and Ubuntu JUST works, by the way.

>[...] I believed in you).

Again, who are you talking to? And this is not a church, for God's sake.

> Fixing the support forums will help as well.

Many things can be said about Ubuntu and its community, but certainly one of those is not the lack of support they offer. Maybe you should see the root of your problems somewhere else--I suggest in you, for instance.

>There is a flood of info on the net and finding the right solution is damn near impossible for anyone but an expert who is intimately familiar with the versions and histories to figure it all out.

I thought you were a computing expert. It's true, the signal/noise ratio on the net is somewhat poor, but we've got google and the likes, don't we?

>I was yours to lose and you lost me. No one is more sad about this than I am.

Don't make me cry, you're certainly more sad than I am, specially when I see that this is your only post in the forums. Have you actually looked for help or you're just trolling around? 

Just in case you are not playing funny, let me tell you that you should reconsider why you want to use Ubuntu. If you just want to do pretty simple things with you computer and you are NOT ready to spend some time learning how to do them, I advice you to stick to Windows; you will save yourself some bad moments like this one.

---

### Post by gnomic on 2007-05-23
> **jrusso2 said:**
> I don't understand, did the Nvidia drivers not provide better resolution?  Or could you not get them to install?

They installed, but didn't solve the problem. When I disabled them (planning to try another video card), it blew the config fine in the /etc/X11/ directory. Since I couldn't get 7.04 to boot from the CD or the DVD (both say that the kernel is corrupt, but boot and run on another machine), I booted with 6.10 - but couldn't figure out how to fix it (my *nix days were 15 years ago). I tried a few things I found here but none of them worked.

The real problem is that once the xserve config file was blown, there didn't seem to be any way to gracefully recover. Which left me editing using vi (I detest vi - had to program in C with it for a year). None of the solutions worked and I didn't have access to post on these forums.

I plan on checking in to future releases. Its SO close to being usable that I hate giving up. I'm not bashing Ubuntu or Linux and I'm not whining (well, a little). I just want the Ubuntu gods to know that even power users like me (there is a reason I built this monster and it isn't games) are having problems making the leap. I hope that I've offered some constructive criticisms. Dropping to the command line and expecting the user to debug a seemingly complex graphics problem is a bit much to expect of newbies - even power user newbies.

If I could stand the itsy-bitsy desktop, I think that it would have run fine. Installing apps and upgrading was WAY better than earlier versions and I liked the default apps just fine.

---

### Post by konungursvia on 2007-05-23
Just download Ubuntu 6.06 and burn it to a disk, and install that one. It will go on your new hardware easily, and you can easily use "envy" to instlal the nvidia driver. 7.04 will be flaky for  a few months yet, on some hardware. 6.06 is not, it's the most stable and reliable.

---

### Post by psyke83 on 2007-05-23
> **nubutu said:**
> >You shouldn't, it's not a stable release. For somebody with no experience it seems more sensible to go for the most tested ones.

There's no need to dish out that kind of advice - Feisty is not an unstable release. The only disadvantage of Feisty is that it isn't a LTS (Long Term Support) release; Dapper is. If the original poster was building a server and wanted to use Ubuntu, Dapper would be ideal. For everything else, Feisty is the logical choice.

The originator of this thread obviously had issues and if they want to wipe their hands clean of Ubuntu, it's their own prerogative; all we can do is offer advice when it's asked and wish them well when they leave.

No offense intended to anyone, of course - I just felt that I should add the comment about Feisty.

---

### Post by gnomic on 2007-05-23
> **nubutu said:**
> 
Don't make me cry, you're certainly more sad than I am, specially when I see that this is your only post in the forums. Have you actually looked for help or you're just trolling around?

Just in case you are not playing funny, let me tell you that you should reconsider why you want to use Ubuntu. If you just want to do pretty simple things with you computer and you are NOT ready to spend some time learning how to do them, I advice you to stick to Windows; you will save yourself some bad moments like this one.

**Hey - no need to get insulting here.** I planned to switch to avoid Vista and because I heard that Ubuntu  was ready for prime time. I've been waiting years for this. I had high hopes.

I'm willing to spend time to learn new things, but 12 hours to fix a simple video problem? Yes, you probably could have fixed it in minutes. But I spent hours looking through the posts here and searching the Internet. The problem was I got back TOO much info. It took a while to figure out the good from the bad. And in the end, it didn't solve the problem. And if its a problem for me, its a problem for the adoption of Ubuntu is all that I'm saying.

A GRUB option to "Restart with default video driver" might be a good solution to the problem. NEVER leave a user at the command prompt after an error.

I considered going back to 6.10 but it seems like I'd be in the same boat (although the 6.10 CD does recognize the correct video resolution...) if something went wrong. Well, I've got 1/2 a TB ready to try it out. Maybe next week.

---

### Post by YukonGuy on 2007-05-23
Sadly Feisty Fawn appears to have more problems than Edgy Eft did. I started running Ubuntu with Breezy Badger and had not problems with that version of Ubuntu either.  I too run an nVidia card, albeit a legacy one now but, I don't understand why this problem wasn't tested or worked on prior to the release of Feisty Fawn.  I too spent hours looking through posts here on the Ubuntu Forums.  Why should I have to do that in order to get my computer and operating system to work properly?

Feisty Fawn should just work. It does not appear to just work for a lot of owners of nVidia graphics cards!  As much as the fix or fixes are relatively easy for someone with significant computer experience to work around and/or fix it's not so easy for people that just want a solid, easy to install operating system without having to troubleshoot an installation upon first use. 

I don't care if the problem lies with nVidia or Ubuntu Development Team.  The problem is Feisty Fawn is feisty.  This is not a good thing!

Regards,

YukonGuy

---

### Post by nubutu on 2007-05-23
It technically may not be an "unstable" release--would anyone install such a thing?--but it definitely is not a rock solid one. There are threads in this forum where people can be found having all sort of problems with Feisty, and regarding it as the worst Ubuntu release ever. I can't judge that for I only tasted the last three, although my personal experience is that this is the only one who made me struggle to do some very basic things.

No offences, don't worry.

---

### Post by nubutu on 2007-05-23
>Hey - no need to get insulting here. I planned to switch to avoid Vista and because I heard that Ubuntu was >ready for prime time. I've been waiting years for this. I had high hopes.
>I'm willing to spend time to learn new things, but 12 hours to fix a simple video problem? Yes, you probably >could have fixed it in minutes. But I spent hours looking through the posts here and searching the Internet. The >problem was I got back TOO much info. It took a while to figure out the good from the bad. And in the end, it >didn't solve the problem. And if its a problem for me, its a problem for the adoption of Ubuntu is all that I'm >saying.
>A GRUB option to "Restart with default video driver" might be a good solution to the problem. NEVER leave a >user at the command prompt after an error.
>I considered going back to 6.10 but it seems like I'd be in the same boat (although the 6.10 CD does recognize >the correct video resolution...) if something went wrong. Well, I've got 1/2 a TB ready to try it out. Maybe next >week.

Sorry about that. I'm sure you'll find your way if you stay a bit more with Ubuntu. The first step will be to ask a proper question about your problem, I bet you get a good answer pretty quickly. (Before even doing so you can search the forum to check whether somebody had the same problem than you have, I bet that's the case for I had it at the very beggining too).

---

### Post by userundefine on 2007-05-23
Should've made a backup of xorg.conf, not that you'd have known to do that since it was nvidia tweaking it.  Perhaps it should be automated to make a backup of the file before installing new drivers and configuring it in case something like that happens.

You don't even need the nvidia drivers to get your desired resolution.  Just a text editor.  This really isn't a problem to go back to XP about.  A quick ? in the forums would've had this sorted before you even thought about making this kind of post.

---

### Post by gnomic on 2007-05-23
Can anyone point me to an easy, reliable source for this question? 
[B]
I bought a new Nvidia (PNY) GeForce 8500 GT, but can't seem to find it on the list of officially supported video cards. I understand that the 8XXXX series has a unified architecture, so in theory it should work. Where is the best place to find the answer?[/B]

I can still use my old 7300, but I thought that it might be the problem at first. Now that I have this newer, faster card (that uses LESS energy than the old one), I'd like to use it if I can. 

Which makes me realize a great feature request - a preinstall routine on the CD that will enumerate the system hardware and give you a compatibility report.

---

### Post by gnomic on 2007-05-23
Yeah - for some reason I didn't get the email to let me post here. That took a couple of days to sort out. By then the frustration level was up. No ones fault - its just what happened.

---

### Post by gnomic on 2007-05-23
> **userundefine said:**
> Should've made a backup of xorg.conf, not that you'd have known to do that since it was nvidia tweaking it.  Perhaps it should be automated to make a backup of the file before installing new drivers and configuring it in case something like that happens.

You don't even need the nvidia drivers to get your desired resolution.  Just a text editor.  This really isn't a problem to go back to XP about.  A quick ? in the forums would've had this sorted before you even thought about making this kind of post.

I did make a backup and edit it manually according to the instructions. It didn't solve the problem. I tried to post questions, but didn't get the authorizing email. By the time I did, I was readlining frustration. 

I think I will try the Edgy release.

---

### Post by Lucifiel on 2007-05-24
Errr... I'd suggest that you try Dapper instead.

Edgy is a little troublesome for many.

---

### Post by gnomic on 2007-05-28
The 6.10 release appears to be working much better for me. I'm still working through all the issues of finding out what apps work best for me and learning how they work under linux, but so far, so good. Let the porting begin. 

Thanks for the encouragement.

---

### Post by DFreeze on 2007-05-29
> **gnomic said:**
> [B]
...NEVER leave a user at the command prompt after an error.
[/B]

Just letting you know the devs are hearing you (well, the users that share your opinion, anyway). This [spec]("https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x") is all about gracefully handling X getting hosed. It's just around the corner, the next version, Gutsy Gibbon, should at least not dump you in CLI when there's a problem with the video settings. 

I can't help you with your setup, because I don't have hardware anywhere near yours (wish I did, though). My nVidia didn't work (GeForce 4 series) at first, and I had a hard time finding the right solution in all the page hits, just like you. My problem was solved unchecking the dual monitor support in nvidia-settings. It seems that my driver gives users with two screens some nifty features that get in the way when you only have one monitor. 

But then again, I'm sure your problem is of a different nature. Good luck with your switch. You'll feel at home soon enough!

---

### Post by GerryB on 2007-05-29
> **gnomic said:**
> I built my new machine to run Ubuntu. ASUS P5NSLI, E6800 duo core, 2G RAM, 1TB Disk, an Nvidia 7300 LE PCI video card. And I went to install 7.04.

Kernal corrupt? WTF? Works on my other machine. OK - boot 6.10 and install, upgrade, and ta-da, working machine. Very easy and quick - less trouble that installing XP in fact. :D

But low video res (1Kx768 at 50hz?). I can't live with that.:o

And that's where the whole story goes bad. I get dumped to the command line, spend hours looking for the answer - fine several - and eventually give up after investing a week trying to get the video card to work.

I've been doing this for a few years. I've gone through AppleDOS, CP/M, System III and IV Unix, every version of MSDOS and Windows, all versions of OS/2, and most other OSs on the market. I've been a sysadmin, a programmer, and know my way around an operating system. Understand - I can fix this. I'm not intimidated by all the cryptic error messages. I'm just frustrated that I have to spend all this time on such a simple problem.

In future releases, I hope you spend some time fixing the fault isolation and recovery process. I really dont care as a user about all the nits. I just want it to work. (Yea, I coulda bought a Mac. But I believed in you). Fixing the support forums will help as well. There is a flood of info on the net and finding the right solution is damn near impossible for anyone but an expert who is intimately familiar with the versions and histories to figure it all out.  

I was yours to lose and you lost me. No one is more sad about this than I am.:(

I think you're right in complaining a bit. Ubuntu has come a long way and it seems that at the very least someone in the development team should come back to you with a reply like this: "We're waiting for the code" or "We're working on it" or "Some work is being done on this and we will get back to you". Which manufacturer would not want to sell their equipment even for 5% of the market? Do manufacturers not support Mac OS? There has to be more communication between the development team and all manufacturers.  Something else that bothers me. How is it that previous versions support a particular kind of  equipment and not a later one? Why do some distros have the code for a particular equipment and not others? Is there not a way to make things more efficient? Gnomic, you might be ahead of the curve, but you deserver recognition from Ubuntu. All in the interest of moving forward!

---

### Post by Docter on 2007-05-29
The problems you're having aren't really to do with linux, per se, Ubuntu in the grand scheme of things is just one distro in a galaxy of others. It is built on an Open Source policy which is how it is installed by default. This is clearly at odds with your needs. You might try Slackware or Zenwalk to see if that suits you better, which I think it will as you have suggested that you lack the inclination to set this stuff up. 

Seeing as you're a computer expert you shouldn't miss the fantastic support forums that ubuntu spawns and you'll find it's ready to go. I'm just saying: Why is it a black and white choice between Windows or Ubuntu?

---

### Post by poetmayhem43 on 2007-05-29
I've just installed the same graphics card and too was annoyed at being bounced back to the CLI.  

The following guide got it up and running for me ([http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)), but the one thing that it neglected to mention was that I had to install the driver first or print out the page and do it from the CLI.  
I chose the former, installed the NVIDIA drivers, then rebooted (it bounced me to the CLI with the X error as my ATI card was no longer recognised, I turned off PC, put in the new card.  Turned on and victory!  (More tweaking is probably needed, but haven't yet managed to pull my partner away from sliding a penguin down a slope :p).  

If you haven't already try the guide above and see if it helps.

---

