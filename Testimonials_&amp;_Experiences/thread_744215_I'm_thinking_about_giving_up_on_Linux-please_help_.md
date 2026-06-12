---
title: "I'm thinking about giving up on Linux-please help change my mind."
date: 2008-04-03
forum: Testimonials &amp; Experiences
---

### Post by BoilingFrogs on 2008-04-03
First off I will say that I did enjoy a LOT of stuff about Ubuntu and was extremely impressed with some of the improvements that it has over a lot of other previous distros. I was a big fan of how fast it was too... every now and then I would close a program down just so I could open it again to see how fast it would load. Unfortunately that wasn't the whole experience I had with Ubuntu recently and now I'm starting to wonder if Linux is all its cracked up to be. I'm hoping I can be proven otherwise.

I have a Dell Dimension Intel duoCore @ 2.8 GHz, 1.5 Gigs of ram and an ATI 1650/ 256 mb that is about a year old. It came with Vista, but that OS is incompatible with most of my apps, my pocket pc and is a system hog. So I wiped the drive and installed XP, but first I had to change the ‘SATA Operation’ setting in the Bios so that it would work. I tried to set up a dual boot with Ubuntu 7.10, but Ubuntu couldn't install. It just made a mess of my hard drive and wrecked my XP installation. I posted a thread about the problem here: [http://ubuntuforums.org/showthread.php?t=742573]("http://ubuntuforums.org/showthread.php?t=742573")

Anyway, I ended up reinstalling xp and used Wubi 8.04 to install Ubuntu on top of xp. I had a lot of fun messing around with it, but spent most of my time trying to get windows apps to run on it, like Photoshop, etc. After being up all night, having set it up the way I liked it, I went to watch a video on you tube. I pushed play and the screen just went blank. A bunch of random text popped up on the screen and it left me essentially at a prompt outside of any os. I rebooted, but trying to boot Ubuntu just resulted in a bunch of error ridden text scrolling on the screen, like:

tty6 maind process ended, respawning
tty6 maind  (4616) terminated with status 255
respawning too fast,stopped
unable to execute "/sbin/getty" for tty1: Input/Output error
...

 It got so jumbled that it was typing layers of lines on top of other lines until finally it just stopped altogether. The os was just gone. I 'll admit I haven't got a clue what all that text meant or what caused the problem, but honestly how is that a stable system? While it was working it managed to lock up on me a few times too. You could say it was a hardware failure, but I've had massive hardware failures in the past with xp and I have never seen the os just spontaneously combust. There would be something left that was operable, something to work with. Maybe it could be blamed on the fact that it was a problem with the Wubi. The only reason I had to use the wubi, though, was because Ubuntu couldn't handle the generic hardware in my year old Dell that an old xp handled fine. That xp I installed it on is still running fine, btw. 

Now when I consider that most if not all of the apps that are used whether in graphic design, 3D, entertainment and business... aren't they all native to either mac or windows, while simultaneously not made for Linux? So you end up spending all this time trying to trick Linux into running these programs and almost always (if they work at all) end up significantly crippled. Plus the fact that Linux is in such a weird place, since it is on the bleeding edge of software it cant even keep up with itself and yet it still manages to always be lagging behind in the hardware department. With that and the additional hassles of scrolling through web pages looking for random lines of code just to get standard operations done and every page telling you a different way to go about it, all to have the thing lock up on you or just spontaneously corrupt itself and all of your files... I'm having a really hard time wondering why I want to have Linux. I mean, it's clearly not immune to locking up and with all the anti-spyware, firewalls and anti virus software available today, you would have to be an absolute moron to have a problem with viruses and malware on windows. Right now, all I can say is its really fast, really pretty and fun to use... but is that really enough to justify all the rest of its issues? If I want pretty, fun and useless I'll get a mac or hang out with a cheerleader. I realize that a lot of this is likely due to user error, but this still seems like a bit much. What am I missing here?

That being said... I'm typing this in Firefox, on Ubuntu 7.10 that I have installed with wubi on top of the same xp. (I still can't get it to just install directly onto the hard drive) I really do want this to work out, but it isn't looking good. Ive gone back and forth between Linux and Windows for a long time; I was really hoping this time Ubuntu would convince me to stick with it-any words of wisdom or insight into my problems?

---

### Post by BoilingFrogs on 2008-04-03
The silence from the Ubuntu community on this matter is disheartening. I realize it was a lengthy post, but is Linux really this indefensible?

---

### Post by kellemes on 2008-04-03
I think the best way to learn about GNU/Linux is to simply forget Windows for a period of time, let's say a month or so..  at the most go dual-boot.. I am actually a triple-booter ;-)
Just run Linux without Wubi and do things the Linux way, this instead of spending your time on trying to get Windows applications running that will at best 'function'.
Also I don't see why you'd install a Ubuntu Beta version (instead of the stable one) and expect it to be stable..

---

### Post by Therion on 2008-04-03
Well, I will tell you right off, I'm not here to "defend" Linux or Ubuntu in particular.  I did read your post and one thing in particular lept out at me which is pretty much summed up when you said...
> I had a lot of fun messing around with it, but spent most of my time trying to get windows apps to run on it, like Photoshop, etc.
Linux ain't Windows, yet you want it to run Windows applications it seems.  

Linux/Ubuntu, and I'm speaking solely for myself, is not about getting Windows apps to run without Windows.  It's about a new and different way of thinking and getting things done.  

In order to accomplish this new and different way of thinking, I had to first let go of the old way of thinking and accept that I was going to be in Learning Mode for some time to come.  I had to be willing to roll up my sleeves and commit to learning an entirely new operating system, complete with its own set of quirks and limitations.  In all honesty it sounds like you dipped your toe in the water, maybe splashed around a bit in the pool, but never wandered out of wading depth.

*<< interruption >>*

Further I note you installed Hardy Heron (v8.04) which is still in Beta.  > but honestly how is that a stable system? 
It's not, you installed a Beta.  Further, you installed it via Wubi an inherently unstable install to begin with (in my opinion) and what a combination THAT must be.  All in all, this hardly equates to an overall indictment of Ubuntu in my opinion.

Why don't you try one of the stable releases of Ubuntu, or an LTS version?  Give it a proper install (sans Wubi) and on its own partition before you decide to throw in the proverbial towel? 

All that being said, use what works for you.  Linux/Ubuntu is not for everyone, and maybe that means you.

---

### Post by bapoumba on 2008-04-03
Moved to "Ubuntu Testimonials & Experiences" as there is no direct support question.

---

### Post by ibuclaw on 2008-04-03
May I also point out that wubi is a virtual partition within your windows ntfs drive.

It's not as brilliant as installing linux on a secure **ext3** or **reiserfs** partition.
The Wubi installation of Ubuntu is more prone to errors if you are forced to hard reboot.

It is also not at quick, or as stable either.

If you want a shot as Wubi again.
Just uninstall Wubi from your windows programs folder, or whatever it is that you use.
Then wait two weeks for the official release of Hardy Heron, then try it again.

Else, another way would to back up anything precious and give XP a reinstall, you should be able to choose the way you want partitions to be laid out (or is that the OEM version...).
Anyway, if you create two spaces, one for Ubuntu, say 20GB and the rest from windows. After installing windows, you can use the 20GB partition you created as the space for Ubuntu, rather than "shrinking" XP. If that's where the problem was in the first place.

Regards
Iain

---

### Post by kellemes on 2008-04-03
> **Therion said:**
> Well, I will tell you right off, I'm not here to "defend" Linux or Ubuntu in particular.  I did read your post and one thing in particular lept out at me which is pretty much summed up when you said...

Linux ain't Windows, yet you want it to run Windows applications it seems.  

Linux/Ubuntu, and I'm speaking solely for myself, is not about getting Windows apps to run without Windows.  It's about a new and different way of thinking and getting things done.  

In order to accomplish this new and different way of thinking, I had to first let go of the old way of thinking and accept that I was going to be in Learning Mode for some time to come.  I had to be willing to roll up my sleeves and commit to learning an entirely new operating system, complete with its own set of quirks and limitations.  In all honesty it sounds like you dipped your toe in the water; splashed around a bit in the pool but never wandered out of wading depth.

That's hardly an indictment of Ubuntu in my opinion.

+1

And another thing..
A lot of people don't seem to realize Ubuntu may be GNU/Linux, but GNU/Linux ain't Ubuntu.
There are 350+ distributions out there.. I've heard a million of stories of people not being able to get 'n00b-friendly' Ubuntu running, but finding there OS in Gentoo, Arch or Slackware. And the list of 'n00b-friendly' distro's like PCLOS, Fedora, openSuSe, Mint, Mandriva, Zenwalk etc.. also is endless.

Like Therion wrote, you need to roll up your sleeves and expect to spend some time on this, and start with trying out different distributions.
[http://distrowatch.com/]("http://distrowatch.com/")

---

### Post by DK-420 on 2008-04-03
BoilingFrogs, I see that your plight with running Ubuntu has been very discouraging and somewhat not fun to you. I really sympathize with you, being as I am a very new user of Ubuntu myself. 

When I started, I was really into getting Photoshop running in Linux via Wine. I had some good attempts and some that were also very disastrous. I had a problem that when I initially installed either version 7, CS or CS2, the install would go great, then when I ran it a second time, the program would crash. I had found out that I needed the fonts that MS required, so I found where I could get them and installed. I haven't had and problems with it since. However since using it once or twice, I haven't touched it. I am now using Gimp which I find to be more to what I need, even though I am still learning the ropes. I also have Office 2003 running via Wine as well, and have not had any hiccups, even though I never use them any more. I am testing to see how things run so I can make the move to installing it on my desktop for my wife to use.

As Therion has mentioned; it is about getting your hands dirty and trying something entirely different.

I have a laptop that I run Ubuntu 7.10 on exclusively. It is also a Dell, but the Latitude D610 series. I have upgraded the RAM to 2gbs, and put in a 160gb hard drive. I also run different OSes on it via VirtualBox. I run WinXP, Win2000 as well as different distros, namely Fedora 8 and the Hardy Heron beta. Everything runs flawlessly.

I am not trying to tell you what to do, but I think you need to give Ubuntu another chance and take things a little more slowly. Don't try to get everything running at once, but take a while to get things running the way you need them to.

---

### Post by alexsabree on 2008-04-03
Learning linux **is** difficult. Now that I'm fairly good with it its 20 times as good as windows. Never crashes (unless you screw around with beta stuff)

Linux is.. amazing.. I have tons of my friends to convert over to linux and even though half of them have given up (I thought of uninstalling it at one time) the others are just captivated at what linux is capable of. After getting compiz-fusion working and getting a fairly decent computer to use compiz. It looks and performs amazingly. The only complaints that you can really put on linux is its learning curve, unique way of working, and its.. free'ness. In my opinion the only reason linux hasn't taken off like crazy is because people would rather download or copy a version of windows for free then get something that was free to begin with..

Please don't give up on linux, you only have to learn something once. Just like how you learned to use a windows OS.

---

### Post by cm.squared on 2008-04-03
To expand on what Therion said about linux not being windows, you shouldn't have to try to get windows applications running on linux to get the functionality of a certain application (wine can be quite the headache).  Linux has a whole host of programs that serve the same purpose as their windows equivalents.

You mentioned wanting to use Photoshop, but if your willing to depart from using that exact program the GIMP (Gnu Image Manipulation Program) is comparable in most respects.  It will take some getting used to, like migrating to linux in general, but in the end you shouldn't be much hampered.

For more linux equivalents to windows programs, see this page in the community documentation:
[https://help.ubuntu.com/community/WindowsApplicationsEquivalents]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents")

---

### Post by BoilingFrogs on 2008-04-03
Thanks for speakin up, I was beginning to think this was a dead end.I know i was a bit general in my post and I realize the enherant problems in installing version 8 a couple weeks early, but this is what wubi automatically downloaded, so i went with it. I suppose i didnt expect a pre-release to be dramaticly difffernt. So if that is the problem i can totally accept that as a major mistake on my part.

 It really isn't so much that particular run though, it was also the fact that i had already tried the 7.10 release, but I couldn't get it to install on its own partition. I tried several times to install the stable version directly on the hd, i was just forced into this position.

 Since its last crash i dug up the Wubi for 7.10 and ran with that version  up until an hour ago. I think I'm gonna run 8.04 again via wubi. Maybe i'm just a glutton but 8.04 was set up a little different and at least let me use the compiz fusion and 7.10 locked up a few times too... so i might as well have fun with it.

I realize this being one of my fists posts here and the fact that i mentioned this singular experience makes it appear that I just fiddled a bit and gave up, but in reality i have worked with linux off and on for a couple of years. Even this last run was literally 2 solid days with no sleep working on this. I didn't so much put my toe in the water and run back to the beach house... it was more like i cut a hole in the ice with a butter knife just so i could get in but it spit me right back out. I really do want something different than windows and i like a lot of stuff about Linux. Ubuntu in particular is really cool. This last time around just made me wonder if it was worth it. I tried to get it running and was going to force myself to stick with it, but i do need a few apps to run on it for the time being.

So its more than the inability to run industry standard applications that bother me. Its that in combination with all of the other factors. I wouldn't be so concerned with losing the programs if the OS itself would run better or be more reliable than windows... or at least install properly, which is really what i was hoping for. Believe me, the lack of the ability to run a few programs is pretty minor compared to the overall usability/crashing issue with the os itself. Again I'm the first to admit the likely fault is user error.

Maybe if i can just get it to install and run on its own partition, then it might run stable and i would LOVE that. I just saw the Dell sub-forum so maybe I'll pop in there. If anybody else as any guess as to what the problem is I'd appreciate it.

Thanks again

---

### Post by rune0077 on 2008-04-03
> **Therion said:**
> Well, I will tell you right off, I'm not here to "defend" Linux or Ubuntu in particular.  I did read your post and one thing in particular lept out at me which is pretty much summed up when you said...

Linux ain't Windows, yet you want it to run Windows applications it seems.  

Linux/Ubuntu, and I'm speaking solely for myself, is not about getting Windows apps to run without Windows.  It's about a new and different way of thinking and getting things done.  


I'm agreeing here as well. Windows and Ubuntu are two wholly different operating systems. There are a lot of professional, licensed software that is made for Windows and will not run on Ubuntu (and if it does run, it won't run as well as it does on Windows). Me, I don't need that software, so I have no windows-programs running in Ubuntu and am not planning to have. Other people may need these - maybe you need office, or Photoshop, or what not, and find the open source alternatives lacking for one reason or another, in which case, I hate to say, Windows really is what you need. 

If you tell me that you spend all your time with Ubuntu trying to get Windows apps to work, and then ask for my advice, I would have to say that it sounds like you would probably be better off with Windows. There's nothing wrong with that, though, different OS's have different strengths and weaknesses, so you need to find the one that does what you need. And if that turns out to be Windows, rather than Ubuntu, then of course you should use Windows. Hey, whatever turns you on, you know.

---

### Post by BoilingFrogs on 2008-04-03
> **cm.squared said:**
> 
You mentioned wanting to use Photoshop, but if your willing to depart from using that exact program the GIMP (Gnu Image Manipulation Program) is comparable in most respects.  It will take some getting used to, like migrating to linux in general, but in the end you shouldn't be much hampered.

For more linux equivalents to windows programs, see this page in the community documentation:
[https://help.ubuntu.com/community/WindowsApplicationsEquivalents]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents")

Thanks for the link, I'll check it out. i have used Gimp before on windows actually. It just kind of sucks after getting so used to Photoshop, spending all that time and money... its hard to give it up. I still haven't been able to get any of the CS versions to run with Ubuntu, just up to version 7 which ran fast as hell. Too bad they went and bloated up the later versions.

Are there any really good equivalents to Vegas though?

.......................

Plus i do photo repair work professionally... just got a call while right after i posted this last entry. One of the big reasons Id like to get Photoshop working. That and just one or two more apps and I'd be set. I'm thinking the VirtualBox is gonna be the way to go for me, cuz wine hasn't been my friend lately.... time will tell.

---

### Post by Therion on 2008-04-03
**@BoilingFrogs:** You know, I don't normally do this but I'm going to suggest you try downloading/installing Ultimate Edition (see my sig).  I remember both getting started with Linux, and 'buntu in particular, as well as all the problems and frustrations I encountered.

For me, finding Ultimate was a huge help; it was the first Linux distro I found that booted right up, installed without a single issue, and just flat out rocked my Linux world from the very get-go.  I don't know what the guy that builds Ultimate does to it (it's more than just additional software and a flashy theme, I assure you!) that makes it do what other distros didn't, but it did for me and it's what got me over the "hump".  

Yes, I know, it IS a big download (it's DVD only and about 1.6 gig if memory serves) but I suggest you give it a go.  Try the LiveDVD and see what you think.  If the LiveDVD is a go for you, do a full install, but please... Don't use Wubi...

Regards and good luck, whatever you decide!

---

### Post by steveneddy on 2008-04-03
> **Therion said:**
> Well, I will tell you right off, I'm not here to "defend" Linux or Ubuntu in particular.  I did read your post and one thing in particular lept out at me which is pretty much summed up when you said...

Linux ain't Windows, yet you want it to run Windows applications it seems.  

Linux/Ubuntu, and I'm speaking solely for myself, is not about getting Windows apps to run without Windows.  It's about a new and different way of thinking and getting things done.  

In order to accomplish this new and different way of thinking, I had to first let go of the old way of thinking and accept that I was going to be in Learning Mode for some time to come.  I had to be willing to roll up my sleeves and commit to learning an entirely new operating system, complete with its own set of quirks and limitations.  In all honesty it sounds like you dipped your toe in the water, maybe splashed around a bit in the pool, but never wandered out of wading depth.

*<< interruption >>*

Further I note you installed Hardy Heron (v8.04) which is still in Beta.  
It's not, you installed a Beta.  Further, you installed it via Wubi an inherently unstable install to begin with (in my opinion) and what a combination THAT must be.  All in all, this hardly equates to an overall indictment of Ubuntu in my opinion.

Why don't you try one of the stable releases of Ubuntu, or an LTS version?  Give it a proper install (sans Wubi) and on its own partition before you decide to throw in the proverbial towel? 

All that being said, use what works for you.  Linux/Ubuntu is not for everyone, and maybe that means you.

+1 here, also.

You sound like you are still in the Windows world.

Come into the light, young one. Come learn of the Force that is within your own PC.

Did you also think that your hardware may not be totally supported in Linux. Some of the newest stuff isn't fully supported yet, although it may be possible to get it running correctly after some "time".

Playing with Ubuntu inside of WUBI isn't using Ubuntu. Let go of your Windows strings and let yourself fly! Install Ubuntu without Windows and just use it, for a month or more, then come back to this thread and report back.

---

### Post by perhhk on 2008-04-03
There is really no use telling him to forget wubi when it won't install for him properly...

---

### Post by BoilingFrogs on 2008-04-03
> **Therion said:**
> **@BoilingFrogs:** You know, I don't normally do this but I'm going to suggest you try downloading/installing Ultimate Edition (see my sig).  I remember both getting started with Linux, and 'buntu in particular, as well as all the problems and frustrations I encountered.

For me, finding Ultimate was a huge help; it was the first Linux distro I found that booted right up, installed without a single issue, and just flat out rocked my Linux world from the very get-go.  I don't know what the guy that builds Ultimate does to it (it's more than just additional software and a flashy theme, I assure you!) that makes it do what other distros didn't, but it did for me and it's what got me over the "hump".  

Yes, I know, it IS a big download (it's DVD only and about 1.6 gig if memory serves) but I suggest you give it a go.  Try the LiveDVD and see what you think.  If the LiveDVD is a go for you, do a full install, but please... Don't use Wubi...

Regards and good luck, whatever you decide!


Thanks for the tip. I'm downloading it right now. 


Again though,just as a general response to most of the responses so far... let me emphasize that **_i want to install Ubuntu or any decent linux distro directly to the hard drive and leave windows behind. So far though Ive tried Ubuntu and an older mandrake, neither of which would write to my hard drive._** Thats the only reason I'm using wubi... that and because right now- just being in windows ticks me off. (I'll admit i didn't realize it would affect the operation of ubuntu that much though.. again live and learn.) So anyway, even if its crippled Im gonna hang out in Ubuntu, at least until i get something installed on its own. I'm open for hints.

---

### Post by ROWDY!!! on 2008-04-07
Exactly what hardware are you using, esp. HD type. What error message(s) was printed when it "wouldn't install"? You need to be specific if you've got a problem. Give as much information as a you can (but don't make things up).
I'm not sure if these'll work correctly inside Wubi but open a terminal and type in "lspci", post the output here, then type in "dmesg", this output is likely to be large, so save it to a text file then post it here to.
Jolly good luck!

---

### Post by wolfen69 on 2008-04-07
try something else. LinuxMint, Dreamlinux, Sabayon, PCLinuxOS, etc. those are all newb friendly and very good.

---

### Post by greyghost60 on 2008-04-07
I am a newbie, using Ubuntu from 7.04, currently on 7.10 and waiting for 8.04. But I have been around computing for some 30 years + when there was no such thing as windows! The nearest was GEM on IBM DOS. I am a part time IT manager with an medical firm and use Windows and Office at work because it is seen as the standard. I dread the move to VIsta but know it may come in 2-3 years unless I can persuade them to move to Linux. However enough rant. My advice buy a second hard drive install Ubuntu on that rather than re-partition your existing drive. Also as others much wiser than I have said use Linux progs rather than force Windows ones to run on an alien OS. But remember you will have to learn the methods that prog uses to achieve the results you want and not expect it to behave like the windows version. Lots of time with the help files I think.:smile
Currently I am using Linuxmint Lite on a laptop and the install when so well it asked me if I wanted to import my windows id into system and the 'My Documents' was there ready to go.
If I have one wish it would be OO Base reading and writing to access. 
Regards
Greyghost60 (the clue is in the number)

---

### Post by stchman on 2008-04-07
Another "Ubuntu ain't Windows" thread.

Ask these folks just how many Linux apps Windows runs?

If someone does not like Linux then don't use it.  Linux is different and does require one to think differently.

The key is that if you REALLY need certain Windows apps then stay with Windows.  I found that pretty much everything I did in Windows there was an app that did the same thing if not better.

The only reason I keep Windows around is for the occasional game I play.

---

### Post by wolfen69 on 2008-04-07
> The key is that if you REALLY need certain Windows apps then stay with Windows.dual boot!

---

### Post by wolfen69 on 2008-04-07
> **steveneddy said:**
> 

Come into the light, young one. Come learn of the Force that is within your own PC.



well said. :guitar:

---

### Post by stalkingwolf on 2008-04-08
You might try an alt. install.  Sometimes that works better.

If you absolutely have to have photoshop , you might take a look at
crossover linux.  I installed photoshop and 2000 office on on the trial version for my landlord and both worked fine.

---

