---
title: "Hardy is BY FAR the worst Ubuntu version yet.  LOCKUP WARNING!!!"
date: 2008-04-26
forum: Testimonials &amp; Experiences
---

### Post by Jim March on 2008-04-26
Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

A bug has been issued to the kernel team, priority high, marked "triaged":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

Today I did a fresh install from the release CD, standard 32bit, Intel945 video, Atheros WiFi, all standard parts on an Acer laptop that handled Feisty and Gutsy like a champ.  No overheating.  1.5gigs RAM, swap stats show zero use so it's not corrupted swap.

I don't think the devs are going to be able to fix this one easily.  There's just NO feedback or debugging info possible.  When Fedora 9 releases I may be forced to abandon ship.

This really sucks.

---

### Post by HunterThomson on 2008-04-26
Why move to Fedora? Why not just use Gusty which worked so well? That is what I did.:KS

---

### Post by qball on 2008-04-26
I fixed the issue myself by installing a 2.6.23 kernel. (installed myself).

---

### Post by Jim March on 2008-04-26
qball: do you mean "compiled it yourself"?  I'm considering doing that with .25 :).

But there's a bigger issue and this addresses Hunter: first, something has gone tragically wrong with how Hardy error-traps.  Linux is flat-out NOT supposed to do this.

Second, I install and support desktop Linux setups for clients, on average a new one every month or so.  I have to be concerned about them, going into the future.  Ubuntu has taken a huge steaming dump on it's user base.  Hardy should have been delayed a month or more.  I don't know that it's right for me to chain them to something that's gone visibly diseased.

---

### Post by FredB on 2008-04-26
2.6.24-12 version is obsolete. Hardy version for release is 2.6.24-16.

I'm using an acer laptop (5520eg) and my hardy 64bits works perfectly. Bad luck, maybe.

---

### Post by adityakavoor on 2008-04-26
> Hardy is BY FAR the worst Ubuntu version yet

I agree:mad:

---

### Post by Jim March on 2008-04-26
> 2.6.24-12 version is obsolete. Hardy version for release is 2.6.24-16.


**Tell me something I don't know.** The bug is still open against -16 and is crashing machines in unchanged fashion across the entire Hardy alpha, beta AND release cycles.  Which is why I posted to that thread that a brand new production-Hardy install was breaking in the same fashion.

In desperation I've installed an am running the Hardy realtime (-rt) kernel from the repos. Dunno if that'll help.  It might, as whatever is going on is "load related" and -rt alters the load handling process.

If this breaks I'm compiling 2.6.25.

> I'm using an acer laptop (5520eg) and my hardy 64bits works perfectly. Bad luck, maybe. 

Having a system with a fundamentally broken error handler is bad luck for all of us.  We do NOT know the cause, only that this is happening.  YOU have no idea what tiny tweak will bring this hell down around your ears.

---

### Post by fdimmling on 2008-04-26
> **adityakavoor said:**
> I agree:mad:

Me not. 

Installed Hardy on an Acer 4652 LMi with 1GB RAM and Intel 940 Graphics. Works quite well except for ugly Chinese characters which is due to a font substitution problem. 

Friedrich

---

### Post by sirdilznik on 2008-04-26
I had problems with the 2.6.24 kernels too.  Manually compiled and installed 2.6.25 and everything is A-OK!

---

### Post by Jim March on 2008-04-26
What I figured.  OK.  I'm going to stick with .24-rt for a bit, see if that makes a diff.  For my own purposes I have no problem compiling .25 but I have to be concerned about customer systems and I'd rather not go custom-kernel there.

---

### Post by vexorian on 2008-04-26
huh trollish title.

How many people have experienced this in the retail version anyway?, 3, five?  of all those who installed hardy since it was released...

---

### Post by schtufbox on 2008-04-26
I'm using 2.6.24-16-rt kernel, hardy is working fine for me :) Apart from one slight bug, but it's not a hardy issue I don't think, more a metacity one :0

---

### Post by siulca on 2008-04-26
I agree that this release is to premature for a final release.

With previous versions I had to fix a few things but at least the internet was working out of the box. This time the network stopped working so it's too painful o try and fix anything without the internet. So I'm downloading 7.10 for a fresh install. 

I suggested somewhere else it would be a good idea to give each release a rough maturity rating so that we don't waste time and put off potential Ubuntu users with failed installs/upgrades.

---

### Post by xjgnsdof on 2008-04-26
I'm going to have to disagree with you. The Linksys WUSB54Gv4 wireless adapter on my desktop, the Broadcom (yes, Broadcom!) wireless card on one of my laptops, and my NVIDIA 8800GTS 512 graphics card are working "out of the box." In Gutsy and Feisty, I had to install all of those things manually. For the noob, Hardy has better default apps (especially Firefox), and (is it just me?) faster performance than it predecessors. On a side note, sound recorder now works for me because of the inclusion of Pulse audio.

So it locks up...blame it on the drivers, not the OS. It's the price we pay for having either bleeding edge tech or antiquated tech. From what I can surmise from the posts I read in these forums, most people find Hardy a vast improvement; and I guess that those people have mid-range rigs.

---

### Post by FredB on 2008-04-26
> **Jim March said:**
> **Tell me something I don't know.** The bug is still open against -16 and is crashing machines in unchanged fashion across the entire Hardy alpha, beta AND release cycles.  Which is why I posted to that thread that a brand new production-Hardy install was breaking in the same fashion.

Did I say something contrary to this ? Are you deaf ? I have NO strange behaviour like the one you're talking about.

> 
In desperation I've installed an am running the Hardy realtime (-rt) kernel from the repos. Dunno if that'll help.  It might, as whatever is going on is "load related" and -rt alters the load handling process.
Good luck.

> If this breaks I'm compiling 2.6.25.Good luck again.

> Having a system with a fundamentally broken error handler is bad luck for all of us.  We do NOT know the cause, only that this is happening.  YOU have no idea what tiny tweak will bring this hell down around your ears.

If I don't face it, am I guilty ? Don't "child me". I am a grown up, and being happy with gutsy. Maybe it is an hardware problem. Who knows ?

---

### Post by Jim March on 2008-04-26
> huh trollish title.

How many people have experienced this in the retail version anyway?, 3, five? of all those who installed hardy since it was released...

It's not hardware, I went back to Gutsy briefly to confirm that.

Sigh.  Look, even a driver issue should cause a total lockup like this.  People with this lockup issue seem to be curing it with kernel swaps...so far in my case -rt is looking OK, not confirmed yet, others are saying compile .23 or .25.  OK.

As to how many are affected: on the Hardy development forum (now closed down), the biggest discussion on these lockups ran 11 pages if I recall right.  So I'm hardly the only one.  And since the symptoms were *exactly* the same from late alpha through all betas and now into production, looks to me like it kicked in during the 2.6.24 kernel compile and never left.  In this forum right now some guy posted a "kernel panic" thread (with zero answers) that's an exact match to this issue.

FredB: As to me talking down to you, you're the one that told me that the latest kernel is -16 when I had posted that I'd just installed a fresh production build.  Trust me, I noted the kernel rev.

---

### Post by malangaman on 2008-04-26
I want you all to know that I am learning a great deal reading this thread. The child jabs are are,funny coming from brainy computer geeks. I am happy with Gutsy and will not upgrade until your problem is solved. Please report back your progress.

---

### Post by Jim March on 2008-04-26
The real lessons are here:

[https://bugs.launchpad.net/bugs/204996](https://bugs.launchpad.net/bugs/204996)

In my case, hours of serious pounding have proved to me that the -rt (realtime) kernel straight out of the Hardy repos fixed my issues 100%, with about the only downside looking like maybe a 10% (tops) chop in video performance.  At least one person reported a failure though.

It looks like we've got multiple causes of these lockups.  Which takes us back to my point: error checking is haywire somewhere.

---

### Post by El Lance-O on 2008-04-26
I too am disappointed with this release. I was hoping it to be the best release so far, but it's TERRIBLE.

All of my folder thumbnails in my music folder (I use album art as icons) are smaller and look TERRIBLE. All my launchers on my desktop which before didn't have titles, simply icons, now are all .desktop files which I can't change.

When I boot, my CPU goes CRAZY, freezing everything up for a good couple minutes before settling down. I can't even open the main menu when this happens.

Flash is worse than ever, eating more CPU than before.

Everything is just SLOW SLOW SLOW!

I really regret ever upgrading, but I already had a hardy libc6 on Gutsy to get the Wii Whiteboard app to work, so I kind of HAD to upgrade or else deal with the subsequent problems.

My wifi LED on my Dell Inspiron 1505n won't turn on now, and I've read in a thread on this problem that this is caused by the ipw3945 driver that from what I have gathered, sucks.

My biggest concerns is the CPU usage from random processes that I don't recognize or don't have names at all. What is this nonsense?!

I really hope everything works out fine, but in the meantime I have an external in the mail, so I will be backing everything up and doing a fresh hardy install.

If that doesn't work, I will go back to Gutsy I guess, no matter how much I would HATE to do that.

COME ON DEVELOPERS, WHAT HAPPENED?!

---

### Post by bbmak on 2008-04-27
I agree, i would downgrade my to 7.10

---

### Post by thejinx0r on 2008-04-27
I found the RC more useable than the final release... :S

---

### Post by Palu on 2008-04-27
My "household" (a college community involving about 10 users) has now upgraded and everyone with the wireless card Intel Proset Wireless 3945 have now lost ability to connect to the internet. None of us are very technical. I mean, I'm a recently graduated technical developer, but I'm pretty recently from Windows too. :( That's a major card for Dells and Asus, so it's a big issue.

---

### Post by yessriram on 2008-04-27
Have the same problem too. Freezes real hard. Absolutely no reaction to any key combinations. Time of freezing is as unpredictable. 

I did an upgrade from 7.10 initially, realised there were issues; did a fresh install. The problem re-surfaced. 

My machine- Gateway solo 1450. All the previous versions have worked like a charm. Been on this since 2005.

Waiting to hear the problems resolved...

---

### Post by wobster on 2008-04-27
Oh well. The only upgrade that ever worked seamlessly here was feisty->gutsy. And gutsy was rock-solid in the end.

Sadly, this release is a complete mess indeed.

---

### Post by Jim March on 2008-04-27
I'm still on the -rt repository kernel and it has indeed solved all my problems.  However, it's not a cure for everybody.  Sigh.  That in turn means there may be multiple causes of the freeze-ups.

---

### Post by bobnutfield on 2008-04-27
I have had Hardy installed from Beta since about mid-march on a new laptop purchase.  I have followed the updates religiously and I believe Hardy is now about 90% stable.  But, I am still getting the occassional lock-up, as Jim March describes.  Firefox is still so full of bugs (3 beta 5) it's like a nest of cock-roaches.

I am one of the luckier ones here who seems to have been reasonably successful in getting Hardy to a near-stable state.  But there are dozens and dozens of horror stories on this forum, both for new installs and upgrades.  I have been using Ubuntu since 2006 and have never seen a distro released with so many problems still inherent in the release build.  What amazes me is that whenever there is a thread started about Hardy being worse than previous releases, some people post as though we are crazy and Hardy MUST be perfect because it is working well on THEIR machine.  There are too many people posting terrific problems here for it to isolated to just a few.  Jim March seems to be a reasonably knowledgable user who also seems to have nothing against Ubuntu as a distro.  His is NOT the only knowledgable opinion that Hardy is just not ready.

I am going to stick with Hardy because I have no mission-critical work being done on my laptop, but if I did, I could not afford to stay with it.  And, like Jim March, I am concerned that as Hardy and it's problems spread throughout the new-user community, Ubuntu's reputation as THE distro of choice for new linux converts is definately in jeopardy.

Bob

---

### Post by Jim March on 2008-04-27
I just want to add that they'll probably get it sorted, almost certainly via a kernel update.

I'm also doing my best to help - so far as I know I'm the first to try the -rt kernel as a fix and while it's not helping everyone, some besides myself are reporting success.

Meanwhile I'm going to take a second crack at compiling 2.6.25 later today.

---

### Post by Redrazor39 on 2008-04-27
If I had learned how to code soon enough, I would've jumped on the boat and helped. I need a working system though and can't risk such a buggy release.

This is just pitiful.

---

### Post by Jim March on 2008-04-27
Well NOW it'll get fixed!!!  A reviewer over at ITWire ran into the random lockups problem:

[http://www.itwire.com/content/view/17863/1103/1/3/](http://www.itwire.com/content/view/17863/1103/1/3/)

Guess we're not imagining things, eh?

---

### Post by factotum218 on 2008-04-27
> **adityakavoor said:**
> I agree:mad:

As do I. The highest priority bug seems to be that Windows is number one according to Ubuntu. If thats all they want is a market share then I might be going back to Slackware or FreeBSD. I have given Ubuntu a chance off and on for the last three years with nothing but problems. With Slackware, and FreeBSD and dare I say debian (I know, ubuntu loves debian blah blah blah, thats all total bs) I have not had one problem since my first install back in '01.
And, not to mention this gem I came across while trying to  address the issues I had:
[https://wiki.ubuntu.com/PainlessUpgrade](https://wiki.ubuntu.com/PainlessUpgrade)
A complete reinstall to upgrade a supposed desktop for the masses distro? I am ashamed to be affiliated with Ubuntu as a user of GNU/Linux.

---

### Post by immerohnegott on 2008-04-27
I upgraded my laptop (Dell Latitude C400 -1.2ghz PIII M, 512M RAM GMA830) to Hardy and am now experiencing the oh-so-fun arbitrary lockups as well. No trouble at all out of Edgy/Feisty/Gutsy on this thing, upsetting to run into errors like this on a vanilla setup.

---

### Post by iaculallad on 2008-04-27
So far so good, Hardy's running very well with my system from the first time I installed its LTS release :guitar:

---

### Post by josel777 on 2008-04-27
By far the worst release ever! I am going  back to Gutsy. I am not sure why anyone would release something so unstable.

---

### Post by MattDTownsend on 2008-04-27
I second the problems. Random locking on my linux box. Old Compaq Armada seems okay, but I'd kinda rather be on my dualcore.

I'm trying to compile the .25 kernel -- but I've had trouble making it far enough before a lockup. The RT kernel did not work with my SATA drive.

By far the worst experience with an ubuntu upgrade, and it's insulting. I've been going through this nonsense with linux distros for 10 years -- and this is what is killing linux on the desktop every time people start talking about one distro or another rising up. Once it gets popular enough, the devs start devoting more and more time to making it "pretty" and "easy" -- i.e., a video player than can now browse the YouTube, or whatever they did -- and, oops, it seems to lock up on lots of machines. Minor inconvenience.

I went through this with Redhat (pre-Fedora), Mandrake, SuSe, and a few others. The only system that never really let me down was FreeBSD, which I'll be going to if this isn't resolved soon.

George is gettin' upset!

---

### Post by jerrylamos on 2008-04-27
I've got vmlinuz-2.6.24-16-generic release levels running on two different computers, two installs of Ubuntu, one of Xubuntu, and one of Kubuntu (multi boot obviously).  No linux lockups yet.  Occasional Firefox 3.0b5 lockups and Open Office write crashes.  Both Reload O.K.

Other than that, more things I do work than in any previous level of Ubuntu going back to Dapper Beta.  I don't do games.  I do plenty of internet videos, ABC news, AOL music videos, You Tube, BBC News videos, ... digital pictures, Open Office, email, forums, ... 

Earlier than the release level, example release candidate was pretty good, the beta's and alpha's were marginal and various parts broken as might be expected.

Jerry

---

### Post by jtbalt on 2008-04-27
I've been looking around the forums and searching to see what I can find, but nothing that has yet to yield a solution.  Under Gutsy I had to jump through hoops to manually install the driver for my Linksys WMP54G v4.1 wireless network card (RT61 drivers).  

When I installed Hardy I was amazed to see that the drivers appeared to be installed and working...but...I started getting random lockups which required a press of the power button to restart - nothing would respond, except the lights on the keyboard would flash when it locked up.

With the computer plugged into network via CAT5 I get NO lockups whatsoever.  But when unplugged and the wireless card is used the lockups return immediately.  

I haven't messed around with trying different drivers or a different kernel - Does anyone have any ideas which would be better to try first?

Thanks,
John

---

### Post by Jim March on 2008-04-27
Switching to the -rt kernel is easy - you just pull the kernel modules ending with "-rt" out of Synaptic, edit your grub menu and reboot.  Lots easier than a kernel compile and you can quickly back out if needed.

That really did sort my machine out, and the type of lockups you describe were exactly like mine.

---

### Post by MattDTownsend on 2008-04-27
> **jtbalt said:**
> 
With the computer plugged into network via CAT5 I get NO lockups whatsoever.  But when unplugged and the wireless card is used the lockups return immediately.  


Interesting. I pulled my wlan card (usb wireless g) to try AGAIN to compile a new kernel after the last freeze. Perhaps it's a problem .24 has with wlan? I'm using ndiswrapper.

---

### Post by MattDTownsend on 2008-04-27
> **Jim March said:**
> Switching to the -rt kernel is easy - you just pull the kernel modules ending with "-rt" out of Synaptic, edit your grub menu and reboot.  Lots easier than a kernel compile and you can quickly back out if needed.

That really did sort my machine out, and the type of lockups you describe were exactly like mine.

I'd hardly say that's easy for beginners. When I tried an RT install, it kept freaking over my SATA drive. What do you mean by pulling out the modules ending with -rt? Do you mean mismatching kernel to modules?

And you can always back out of a kernel compile.

---

### Post by riven0 on 2008-04-28
Very strange that so many people are having problems. This has been the smoothest installation for me so far, but I've only had Hardy installed for about 2 days now. How long did it take you guys to start noticing lock-ups?

---

### Post by Niniel on 2008-04-28
Lol, this thread is funny.
Not in the sense that I'm trying to belittle people's problems. But seriously, "worst ever"?
How much are you willing to bet that there are threads like this after every single release?
I have to say, from my limited experience, the upgrade has gone very well. I kind of expected a total crash and burn after I read some Gutsy upgrade stories after that come out, but I haven't run into any problems yet but one (icon themes broken).
And yes, the system does feel a little faster.

---

### Post by Invader Amoto on 2008-04-28
This is by far the worst ubuntu version yet...for some. Most people seem to have it working perfectly. I haven't been so lucky though. I don't feel like explaining my problems again so i'll just link to the thread i started about my (strange) problems.
[http://ubuntuforums.org/showthread.php?p=4818011]("http://ubuntuforums.org/showthread.php?p=4818011")

---

### Post by nudnik on 2008-04-28
After several years of Ubuntu this release has caused me to flee to FreeBSD on my main machine (Intel DG33BU MB  with a Core 2 Duo CPU). I'm sad to say the freezes rendered my desktop virtually useless. Debian remains on my antique back-up unit. I may consider returning once the kernel has been updated, assuming that sorts things out.  

The mascot holds true...see below.

---

### Post by Jim March on 2008-04-28
In part, the title was to get people's attention.  However, Linux in general is NOT supposed to hard-lock like this while giving no clue as to what blew up.  That's not acceptable.  It means error-checking is wonky, and it's going to be a cast-iron bi+ch to fix because hey, guess what, no error messages/logs AT ALL.

My Acer lappy running the -rt kernel has a SATA drive.  So at a minimum that CAN work.

Matt and others, **here's how to add the -rt kernel**.  Note that the GRUB instructions are set up to allow you to test-jump to different kernels on boot which I think is a good place to be while we sort this out.

---

Assuming you have a working Internet connection:

1) Under the "System" menu find "Administration", go into "Synaptic". This is a more advanced version of the "Add/Remove Programs" tool.

2) In Synaptic hit the "search" button, change "look in" to "name" and under the keyword to search for type "linux" (no quotes). Hit "Search".

3) It's now showing you everything you can add to your system that has the word "linux" in it's title. Make this window bigger and stretch the"package" column wider (look for the vertical line just left of "installed version", drag it to the right).

4) Scroll down until you spot each of the following:

linux-headers-2.6.24-16-rt
linux-headers-rt
linux-image-2.6.24-16-rt
linux-image-rt
linux-restricted-modules-2.6.24-16-rt
linux-restricted-modules-rt

For each one, hit their checkbox and mark them as "to be installed". Hit the "apply" button when done.  It'll download and install the stuff.

DO NOT reboot yet!

5) Pull up the "terminal" under "Applications>Accessories". Copy and past this next line in exactly as written - use the mouse's right-click in the terminal to do the "paste" as "CTRL-V" won't work in the terminal window:

sudo gedit /boot/grub/menu.lst

6) You're now editing a file in a simple "notepad" type program. Look for the line that says "timeout" and raise the number of seconds. I recommend 20.

7) Find the word "hiddenmenu" sitting on it's own line and put a hash ("#") in front of it to turn "hiddenmenu" off.  Save this edited file.

8) Do a normal shutdown or restart.

When you come back up, a menu will pop up showing all of your kernel flavors available. Pick the one that ends in -rt (realtime) and hit enter to start with that kernel. Run it for a while, see if this helps.

Explanation:

The "realtime" kernel alters the way multiple tasks are scheduled ("prioritized") between each other. It will run fractionally slower for most apps but any app that requests it can be bumped way up in priority. This is for situations where the computer has to be doing something on schedule, tied to other needs such as on an assembly line or something, and can give a critical task it's whole attention.

Something about it's scheduling difference has fixed the lockups on my system and some others.

When regular kernel updates come along, I'll check and see if those fix the lockups and report back to this thread.

---

### Post by zedcar on 2008-04-28
> **Niniel said:**
> 
I have to say, from my limited experience, the upgrade has gone very well. I kind of expected a total crash and burn after I read some Gutsy upgrade stories after that come out, but I haven't run into any problems yet but one (icon themes broken).
And yes, the system does feel a little faster.

Well I'm glad it went well for you, but I'm really worried by this thread - the stats say it all. So far only 20% of 8.04 installers say it was a good experience. 30% say it was really bad, and the rest say it caused problems they were able to solve. It might be too soon to say this is the worst ever, but numbers don't lie. 

I'm sure the team is working on this freezing issue and I wish them well. (It seems to me that wifi is a common denominator.)

---

### Post by hiddensphinx on 2008-04-28
> Hardy is BY FAR the worst Ubuntu version yet

I agree too. So many problems getting ATI X200 gpu on a Compaq V2000 to load. It freezes after loading. Recovery version of Linux via GRUB not helping at all.

I used Ultimate Boot CD for Win XP to fix my master boot record by using the reconvery console option. Then I used the Linux Rescue CD 2006 to remove the partitions where Ubuntu was located.

Fiesty Fawn/Gutsy Gibbon were awesome but Hardy Tardy is something I am staying away from.

---

### Post by Jammin80503 on 2008-04-28
If Hardy isn't working on your machine, just chill and wait a few months. Some users are experiencing lockups - You cant deny that. However, those that do should just revert to gutsy and wait. All the work I've done with hardy has gone great.

---

### Post by gtdaqua on 2008-04-28
> **Niniel said:**
> Lol, this thread is funny.
Not in the sense that I'm trying to belittle people's problems. But seriously, "worst ever"?
How much are you willing to bet that there are threads like this after every single release?
I have to say, from my limited experience, the upgrade has gone very well. I kind of expected a total crash and burn after I read some Gutsy upgrade stories after that come out, but I haven't run into any problems yet but one (icon themes broken).
And yes, the system does feel a little faster.

I agree. When Gutsy was released, there were similar talks. But I should say Hardy is good for me. And yes, the server is quite faster now - especially web apps. The response time I get is considerably better than that of Gutsy's. 

Whatever it is, Ubuntu masters should look at what is causing the kernel panics & other issues and should provide workarounds. This is more important than saying that 'these kind of threads happen after new releases....'

---

### Post by Jim March on 2008-04-28
After two days of heavy pounding, the -rt kernel finally locked up on me.

It did so differently than before - with this latest I still had mouse movement.  Seems there's more than one failure mode going on...dammit.

---

### Post by Buffalo Soldier on 2008-04-28
My overall experience with Hardy
- 1 laptop  since Alpha 6
- 1 home desktop since Alpha 6
- 3 office desktop since RC

All 5 machine has been far more stable than Gutsy. So I'm really surprised with the lock-ups mentioned here.

Maybe I should try a fresh install using the latest realease CD. Will update here once I try that out.

---

### Post by sloggerkhan on 2008-04-28
Hmmm. Not sure if it's a fluke error, but I installed Hardy on spare partition. All seemed okay. Then, suddenly everything on the machine died completely, all gui, everything, and you couldn't even log into a terminal because every terminal screen was too bust printing something along the lines of killing process <various names> out of memory
where a lot of the same names kept getting repeated with incrementing PIDs.... really bizzarre. I know my RAM works, passes memtest, have 2 gigs of it....
Just bizzarre. I gotta get stuff done, so I haven't gone back to check it out, though.

Can't say it's the worse release yet, though.

---

### Post by Jim March on 2008-04-28
[COLOR="Red"][SIZE="5"]Could whoever has made 2.6.25 work PLEASE post a URL to the instructions you used?  There are a bunch of different Ubuntu kernel build instructions and so far two haven't worked with Hardy and 2.6.25.[/SIZE][/COLOR]

Thanks.

---

### Post by gunbladeiv on 2008-04-28
instead of mentioning the hardy problem, why not just sit back and relax, use your stable version of ubuntu until the problem fix?
i dunno why you keep saying hardy is the worst release ever, cuz i've been installing/upgrading hardy on 10 of different pc and laptops with no problem.  Maybe it need a little fix, but it's not the worst ever.  I think you guys need to learn how to fix instead of complaining.

---

### Post by timbosity on 2008-04-28
Agreed. Have Hardy working perfectly on desktop (Ubuntu). It even fixed some of the problems I had previously with weird dependencies. still have a few issues with Xubuntu hardy on my laptop, most notably with firefox, but thats not really directly related to hardy... One thing though, where did xmms go? i want it back

---

### Post by Swagman on 2008-04-28
Yeah I've been getting hard freezes too.
According to the missus, Two this morning alone (I work nights so late out of bed).

She did say that it seems to happen about 5 mins after the screen saver kicks in.

I've also notice on booting the system (NOT after crash) that the hard drive pages like its trying to compete with windows !!

Makes using The fox kinda sticky.

---

### Post by MattDTownsend on 2008-04-28
> **Jim March said:**
> After two days of heavy pounding, the -rt kernel finally locked up on me.

It did so differently than before - with this latest I still had mouse movement.  Seems there's more than one failure mode going on...dammit.

Sorry to hear that, Jim.

I installed the -rt kernel with apt-get, and it seemed to install all of that crap with it. I'm pretty sure that kernel just dislikes my SATA controller, which happens. I haven't given a serious shot at compiling .25 yet -- it seems that some things have changed since last I compiled a kernel. Ubuntu makes you stupid. Which doesn't help these situations.

To those of you who wonder why people are upset: Anyone who has been around on Linux for a while has been through this before. After major failures on Redhat and Mandrake -- after distribution upgrades on machines where the distros previously worked -- I fled to FreeBSD. This was some time ago. Then I came back to Linux and had this happen several times -- again with SuSE and a few others.

So, to me at least, this feels like old news. I'll give a few days for a new kernel to be released in the repos. If after two or three days they can't solve a major problem on many people's systems (that's been talked about, apparently, for some while), I'll be headed back to a BSD system, most likely.

I've recommended Ubuntu to a lot of people because it "isn't supposed to do this." I had faith that Ubuntu would avoid the fate of previous systems, but this is now in question, in my mind. I really didn't want to leave to another distribution, again -- and if a number of old timers now abandon Ubuntu (if it takes too long to fix this) and newcomers can't even boot the CD, Linux on the desktop will be delayed again, just like it was every time the lead distro went to crap. Which is bad news for us all.

It may not be freezing on your system -- it seems fine on my old laptop. But that doesn't mean it's okay. This should not have been released into stable, period.

---

### Post by Kaparen on 2008-04-28
Yeah, got the same problem. I use 'blank screen' as my screensaver and it made Ubuntu 8.04 freeze. I took the easy way and turned off my screensaver completely and I haven't had a problem since. I think I will giver Kernel 2.6.25 a shot later tonight. 

I've got to say though that apart from that bug this is the best release yet for me, everything works right out of the box and I think that the debian/ubuntu folks are doing a really good job.

---

### Post by El Lance-O on 2008-04-28
I had problems of the such using Gutsy, where the screen would lock up, but mouse movement was still smooth and responsive. Restarting X with [ctrl]-[alt]-[backspace] did nothing, and at times holding [ctrl]-[alt]-[prntscn] and typing R-E-I-S-U-B (as noted in the ubuntuguide for Feisty/Gutsy) did nothing as well.

If I caught it quick enough, I could restart X and it would be fine. So there obviously have been problems like that, it's just catching us off guard because it's a new release.

I think it is a little harsh to say it's the worst, but there are definitely problems that need attention to by someone that has the technical ability to remedy.

Hopefully it all works out?

---

### Post by carney1979 on 2008-04-28
> **sirdilznik said:**
> I had problems with the 2.6.24 kernels too.  Manually compiled and installed 2.6.25 and everything is A-OK!

Been awhile since I "rolled" my own kernel.

I would like to compile it with the same options, no more or less than the standard Hardy kernel.

Anyone have a quick howto on how to do this?

David

---

### Post by GTengineer on 2008-04-28
> **carney1979 said:**
> Been awhile since I "rolled" my own kernel.

I would like to compile it with the same options, no more or less than the standard Hardy kernel.

Anyone have a quick howto on how to do this?

David

I am also interested in this. I am using 2.6.24 and I am having a LOT of problems right now. My computer locks up HARD! the LED's for numpad, caps, etc, blink but there is absolutely no response from the machine. I am also experiencing all these random restarts or logs me off unexpectedly. 

I am at wits ends with Ubuntu right now. I am a Linux noob and use this machine purely for work so I cannot have this instability and down time ... I took on Ubuntu because supposedly it just "works" but it is not ... 

BTW I upgraded to Hardy because it had some better software but mainly because Gutsy had problems with my GPU (8800GT) after I upgraded from a 7600GT.

---

### Post by htrdfrk on 2008-04-28
If I may put in my two cents;

I have been following Ubuntu since Edgy and I have to be honest, I was not impressed.  Nothing seemed to ever work for me, most importantly the wireless wouldn't work for love nor money, but I stuck with it determined to learn and get it to work.  Hell even the worst version of Linux ever made is better than the best windows version.  After upgrading from Edgy to Fiesty, everything began running so much better.  Wireless was good, streamlined well, just didn't have some of the features I was hoping it would have.  Then gutsy came out, I ignored it....not sure why, just had no interest in upgrading at the time.  Finally the new and improved Hardy came to our door steps in the form of Beta.  Of course I threw the Beta version in my machine as I was so excited about it I couldn't wait till the final release.  Much to my surprise, it went so flawlessly that I didn't have to adjust or configure anything.  Absolute beauty if you ask me.  I have used the Beta version since it first came out, without a problem.  The distro release finally came available last week and of course I didn't redownload the final release, just updateded the Beta.  Everything still seems to work perfectly, but strangely I have noticed that all the sudden it seems to hang a lot.  It doesn't fully lockup, just hangs for a few seconds to maybe 30 seconds at the most then catches back up with itself.  I'm not sure if this is relevant to the lock ups others are experiencing, but since it didn't happen before the update I am assuming it has to do with something that was in the updates on the day the final was released.  And if my memory serves me correctly, I believe there was an update to the kernal on the last update.

I may just be rambling about nothing, but I thought I would at least throw that out there.

Hope everyone gets it working, as I personally think this is miles above the other releases, when it works at least.

---

### Post by martrn on 2008-04-28
> **GTengineer said:**
> I am also interested in this. I am using 2.6.24 and I am having a LOT of problems right now. My computer locks up HARD! the LED's for numpad, caps, etc, blink but there is absolutely no response from the machine. I am also experiencing all these random restarts or logs me off unexpectedly. 

I am at wits ends with Ubuntu right now. I am a Linux noob and use this machine purely for work so I cannot have this instability and down time ... I took on Ubuntu because supposedly it just "works" but it is not ... 

BTW I upgraded to Hardy because it had some better software but mainly because Gutsy had problems with my GPU (8800GT) after I upgraded from a 7600GT.

If you are interested in compiling or 'rolling your own kernel' then you can follow this guide here :-- [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835")  I do not know the setting used to compile the linux-generic kernel, but this guide if followed through give you an ubuntu base kernel to build.

I have my own custom kernel, and it works well and no problems with the linux-generic kernel also apart for a few odd processors.  The lockups you are talking about hit randomly a few people.

---

### Post by nudnik on 2008-04-28
> **Jim March said:**
> After two days of heavy pounding, the -rt kernel finally locked up on me.

It did so differently than before - with this latest I still had mouse movement.  Seems there's more than one failure mode going on...dammit.

This is why I fear the Heron for time being. I'm betting a thorough kernel revision is necessary.

Holds breath until dev team produces a fix. Won't clean my room either. :twisted:

---

### Post by GTengineer on 2008-04-28
> **martrn said:**
> If you are interested in compiling or 'rolling your own kernel' then you can follow this guide here :-- [http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835")  I do not know the setting used to compile the linux-generic kernel, but this guide if followed through give you an ubuntu base kernel to build.

I have my own custom kernel, and it works well and no problems with the linux-generic kernel also apart for a few odd processors.  The lockups you are talking about hit randomly a few people.

Thanks I will read into this tonight.

---

### Post by ile on 2008-04-28
Hello.

1st of all: Ive made a clean hardy install and ive had no problems but my 3945 wireless not working.

I know this is a final release, but wont expect a free-of-bugs version till one or two month after the release.

I think WE are the final beta testers. Be serious: no one (person or enterprise) will establish a work-web or workstation on a just released OS. People have the "bad" habit of hating to lose their time.

I think its our "duty" (this is the work-all-together community, remember?)to install it at home (keep ur 7.10 on another partition), to test it and get it a ready-to-go OS so to be able to spread a good distro (both for newbies and enterprises. Do not forget enterprises since they pay all of this).

Or u can buy a Mac. Ill stay here for now.

---

### Post by yyyc186 on 2008-04-28
>>>>Hell even the worst version of Linux ever made is better than the best windows version. 

After trying to upgrade to Hardenned Heron, I must take dramatic exception to the above statement.  I've hated MS for decades, probably longer than many of you have been alive, but 8.04 is inexcusable.

---

### Post by GTengineer on 2008-04-28
> **ile said:**
> Hello.

1st of all: Ive made a clean hardy install and ive had no problems but my 3945 wireless not working.

I know this is a final release, but wont expect a free-of-bugs version till one or two month after the release.

I think WE are the final beta testers. Be serious: no one (person or enterprise) will establish a work-web or workstation on a just released OS. People have the "bad" habit of hating to lose their time.

I think its our "duty" (this is the work-all-together community, remember?)to install it at home (keep ur 7.10 on another partition), to test it and get it a ready-to-go OS so to be able to spread a good distro (both for newbies and enterprises. Do not forget enterprises since they pay all of this).

Or u can buy a Mac. Ill stay here for now.

I have been beta testing Hardy for a long time and always put up with the crashes, glitches, etc, during that time because I knew it was *beta*. I am not a software developer, I did all I could by at least reporting bugs, etc while beta was out. However you would expect that a an official release this sort of major problem would be ironed out. And no you cannot always "keep your 7.10" partition, as I said it had problems recognizing my 8800GT when I had to reinstall it (7.10) after redoing all my disk partitions for better disk management.

---

### Post by yyyc186 on 2008-04-28
[QUOTE=ile;4823900]Hello.

1st of all: Ive made a clean hardy install and ive had no problems but my 3945 wireless not working.

I know this is a final release, but wont expect a free-of-bugs version till one or two month after the release.

I think WE are the final beta testers. Be serious: no one (person or enterprise) will establish a work-web or workstation on a just released OS. People have the "bad" habit of hating to lose their time.

Clean installation seems to be the ONLY way this release was ever tested.

Give what I've seen with 8.04 so far, I won't expect the level of stability we had with Gutsy to appear for another 60-84 months.

Conversion to MAC is like the best option at this point.

---

### Post by martyssweb07 on 2008-04-28
I've experienced a few lockups myself, but honestly, I attribute them all to firefox 3.  Which I must say is incredibly buggy. 

Granted this is speculative, But, I'm thinking if I threw out firefox 3 and replaced with 2, I doubt, I'd have nearly as many problems.

Just a thought.

---

### Post by GTengineer on 2008-04-28
> **htrdfrk said:**
> Hell even the worst version of Linux ever made is better than the best windows version.

Don't take this the wrong way but this is utter BS. Vista x64 on my machine is making Ubuntu look like pure "junk" to put it mildly.

---

### Post by Rohen on 2008-04-28
My System also Locks up, unexpectedly.  It's a real drag since I NEED to get some work done but it's practically impossible to do so in a timely manner.

Not only is it Firefox, but also Evolution, Add/Remove Programs, and even OpenOffice.

The only thing that seems to work correctly is WoW :P

I will uninstall Firefox and re-install to see if that helps but if ANYONE has found a fix for this PLEASE LET US KNOW!!!!!!!!!!!!!

I need to turn in a project next week and need this working ASAP :(  THX

:( :( :(

---

### Post by GTengineer on 2008-04-28
> **Rohen said:**
> My System also Locks up, unexpectedly.  It's a real drag since I NEED to get some work done but it's practically impossible to do so in a timely manner.

Not only is it Firefox, but also Evolution, Add/Remove Programs, and even OpenOffice.

The only thing that seems to work correctly is WoW :P

I will uninstall Firefox and re-install to see if that helps but if ANYONE has found a fix for this PLEASE LET US KNOW!!!!!!!!!!!!!

I need to turn in a project next week and need this working ASAP :(  THX

:( :( :(

Please report back if you find Firefox to be indeed the culprit of the lock ups. I cannot seem to find a reason for mine since it crashes very randomly.

---

### Post by analoog on 2008-04-28
my firefox crashes when loading flash elements.

My main problem with hardy is that GNOME is restarting without a warning.
It suddenly switches to laptop mode and restarts.
can't find any clue in the logs.

---

### Post by GTengineer on 2008-04-28
> **analoog said:**
> My main problem with hardy is that GNOME is restarting without a warning.
It suddenly switches to laptop mode and restarts.
can't find any clue in the logs.

Same here, thanks for confirming I am not the only one with this problem (although sorry you have it too).

---

### Post by 00arthuryu on 2008-04-28
heya
i have 2 computers, one desktop and one laptop after upgrading from Feisty and Gutsy respectively. Both computers crash without warning and at completely random times.
On my laptop everything just seems to just freeze
On my desktop however, it seems to not be able to read the Hard disk, as if the the application is open when it happens, it is still interactive and you can still move it around, but no commands can be put into terminal etc. as it cannot read the HDD for the command 'sudo shutdown -r now' or 'sudo reboot'

---

### Post by JAGGEDSPHERE on 2008-04-28
Sadly I think I have to agree.
I installed HH yesterday and have had 3 lockups thus far.
This is pretty unacceptable for me right now. I have just started in my first semester of university.(CS degree)
I am so frustrated! CTRL+ALT+Backspace does nothing.
I noticed that the system froze sometime after I plugged my USB thumb drive in...
If nothing comes out soon I will go back to Gutsy or try another distro.

Edit: I should also note that the mouse works smoothly during a lockup.

---

### Post by agim on 2008-04-28
Why do some long-time ubuntu people write this crap? I understand when someone new comes on and just wants to argue, or when someone has legitmate comments, but to just use flame bait language to start a post is just plain stupid. For people who have used Ubuntu for a long period of time to just come out and say that the entire OS is crap is just senseless, especially around a new release. We want people to come into the community. 

To the people who have been here since Feisty or even longer who are making these kinds of remarks: you know that problems with ubuntu are often limited to a single machine, rarely a whole class of machines, and NEVER to every machine. So why make such stupid remarks? Stick with Gusty, move to Arch, whatever. Just don't come onto the forum and make idiotic remarks that scare newcomers away.

If any newcomer is reading this... I am not a computer programmer, I had little or no knowledge of linux 8 months ago. Hardy is my third Ubuntu release, and each one has been better than the last. If you have any questions or problems, most of us are pretty helpful, and I am sure 95% of you will be happy you made the switch to Ubuntu.

---

### Post by wpshooter on 2008-04-28
> **00arthuryu said:**
> heya
i have 2 computers, one desktop and one laptop after upgrading from Feisty and Gutsy respectively. Both computers crash without warning and at completely random times.
On my laptop everything just seems to just freeze
On my desktop however, it seems to not be able to read the Hard disk, as if the the application is open when it happens, it is still interactive and you can still move it around, but no commands can be put into terminal etc. as it cannot read the HDD for the command 'sudo shutdown -r now' or 'sudo reboot'

If you (speaking collectively) are one of those persons that believes that an O/S (be it M/S Windows, Linux, or any other O/S) can be "upgraded" from one version to another with NO problems, **then you probably still believe in the tooth fairy**.

You are likely enough to run into all kinds of problem even if you attempt to install the new version from scratch on a cleanly WIPED hard drive.

I am not saying that you can NEVER upgrade without any problems but that IMO the chances are very much tilted against you.

But as to Hardy, I have not, so far, been able to get it to install and run correctly even when installing it from scratch.

Good luck to us all.

---

### Post by Ken Jannot on 2008-04-28
I experienced the random lock-ups with 7.10--which is why I upgraded to 8.04 as soon as I could. Now I have problems that make my previous lockups pale in comparison. Visuals are all skrewy--display is stuck on 640x480. Sound doesn't work. And several utilities don't ever start up. I'm newish to Ubuntu, having started with 7.10, and I have to agree that it's experiences like this that let me know why Linux is still relegated to a minor chunk of the pc world.

---

### Post by Speedy328 on 2008-04-28
> **gunbladeiv said:**
>  I think you guys need to learn how to fix instead of complaining.

So you are saying that we shouldn't be concerned about significant problems/issues about this distro that appears to be affecting a large number of users (myself included)? New users to Ubuntu don't want (or be expected) to waste time dealing with wireless problems, video problems, video freezes. This is not the way to 'sell' Ubuntu to the masses as an alternative to Windows.

My upgrade from 7.10 to 8.04 on my Dell D600 laptop went fine during the beta phases. In fact, the upgrade was the most painless one I had experienced so far. However, that changed when I upgraded to RC. I began to note a problem during bootup and with my wireless card (a Cisco Aironet 350) not responding. I have so far been unable to remedy that problem and have actually ended up with an audio problem that I didn't have before.

I'm glad that there are others who have had no problems with the upgrade and there are those who have been able to deal with the problems. But don't tell me I don't have the right to complain about issues with the release, especially if I am unable to remedy the problems after several attempts.

---

### Post by agim on 2008-04-28
And I think its possible that the people making all the noise are people like you. Most of us have done well with 8.04. It has been the smoothest OS I have used. Better than Feisty, Gutsy, PCLOS or puppy. You are painting with too large a brush.

---

### Post by FredB on 2008-04-28
You will only read people who have problems, so about 5% of upgraders.

Let them cry, they will soon understand there is no advantage at all make other people angry.

I am using Hardy since beta, and IT WORKS ! Just do a clean install with your home backuped.

And around 50% of the trouble will be dead.

---

### Post by B3n3v3nt3 on 2008-04-28
Until now it is indeed by far, the worst ubuntu version I've tried, I can't even install it. I get the initramfs + busybox problem ([http://ubuntuforums.org/showthread.php?t=765195]("http://ubuntuforums.org/showthread.php?t=765195"))
I've tried all those stuff and nothing :(

---

### Post by timbosity on 2008-04-28
OK,

my extra two cents here. I have laptop running xubuntu since december and then my work desktop in february on ubuntu. (my first go at ubuntu and linux). The laptop is old and w had a few quirky things to sort before I was happy; upgrading it to hardy was seamless except for firefox troubles, easily fixed with reverting to FF2; Dell desktop on ubuntu: Seamless and not a worry whatsoever and its been on 3 days with not a glitch... 

good work guys, Hardy is a sweet distro!!!

---

### Post by eragon100 on 2008-04-28
It's working great for me, best release yet FOR ME :)

But this amount of users complaining about problems in the new version almost sounds like windows millenium/vista, and is (obviously) not good :mad:

---

### Post by FredB on 2008-04-28
Sigh. I will stop my subscription to this post which now stinks.

Cannot bare same old whining. Just do a clean install, avoid flash plugin nonfree and 50 to 75% of your problems will be dead.

Be smart, stop on complaining, ACT !

---

### Post by GTengineer on 2008-04-28
> **FredB said:**
> Sigh. I will stop my subscription to this post which now stinks.

Cannot bare same old whining. Just do a clean install, avoid flash plugin nonfree and 50 to 75% of your problems will be dead.

Be smart, stop on complaining, ACT !

Can you people get it through your heads that it is not an "upgrade" only problem? I have made about 2 clean installs of Hardy, the beta and the new RTL. Comprende?

The Linux fanboyism or elitism is getting almost as bad as Apple's .... Instead of trying to help, its easier to criticize those having troubles and sweep it under the rug. Anyway unsubscribe away! :roll:

---

### Post by paulyballs on 2008-04-28
> **GTengineer said:**
> Can you people get it through your heads that it is not an "upgrade" only problem? I have made about 2 clean installs of Hardy, the beta and the new RTL. Comprende?

The Linux fanboyism or elitism is getting almost as bad as Apple's .... Instead of trying to help, its easier to criticize those having troubles and sweep it under the rug. Anyway unsubscribe away! :roll:
I am also experiencing the same problems with a clean install.

---

### Post by erginemr on 2008-04-28
With no intention to bash Hardy, I am also one of those unhappy users upgrading to it, and then, trying to do a clean install. Each time, this way or the other, the system crashed on me.

Luckily had my Gutsy system backup just before the upgrade. So, I will go back to Gutsy and wait for a few months for the Hardy cake to bake.

---

### Post by zedcar on 2008-04-28
> **FredB said:**
> You will only read people who have problems, so about 5% of upgraders.

Let them cry, they will soon understand there is no advantage at all make other people angry.

I am using Hardy since beta, and IT WORKS ! Just do a clean install with your home backuped.

And around 50% of the trouble will be dead.

Let's be careful with stats... the survey on this forum says it all: [http://ubuntuforums.org/showthread.php?t=764847](http://ubuntuforums.org/showthread.php?t=764847)

Currently only 21% of both fresh installers AND upgraders say it is a flawless process; i.e 79% have had trouble. That's way too high to be acceptable. Even if you try to argue that more people complain than praise, it's still impossible to justify your statement that only 5% have trouble. We should not argue whether this is a problem (it is!) - we should be trying to post constructive comments that help the developers solve the problem.

---

### Post by FattyCNS on 2008-04-28
> **zedcar said:**
> Let's be careful with stats... the survey on this forum says it all: [http://ubuntuforums.org/showthread.php?t=764847](http://ubuntuforums.org/showthread.php?t=764847)

Currently only 21% of both fresh installers AND upgraders say it is a flawless process; i.e 79% have had trouble. 


Let's also be careful on reading too much into those statistics. People who are having trouble with the upgrade are far more likely to be browsing the forums and come across that thread.

---

### Post by agim on 2008-04-28
COMIC BOOK GUY
Last night's Itchy & Scratchy was, without a doubt, the worst episode ever! Rest assured that I was on the Internet within minutes, registering my disgust throughout the world.

BART
Hey, I know it wasn't great, but what right do you have to complain?

COMIC BOOK GUY
As a loyal viewer, I feel they owe me.

BART
What? They're giving you thousands of hours of entertainment for free. What could they possibly owe you? I mean, If anything, you owe them.

COMIC BOOK GUY
(pause) Worst episode ever.

---

### Post by analoog on 2008-04-28
> **GTengineer said:**
> Same here, thanks for confirming I am not the only one with this problem (although sorry you have it too).
Should I report this problem on [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) ??
Or is it already reported? If not how should I report it? I have no experience in posting bugreports@launchpad.

---

### Post by bdoe on 2008-04-28
Wow...  Ugly, ugly thread! :shock:

I guess I should consider myself one of the lucky ones. I downloaded Hardy right as soon as it was released. In fact, I had to pull it down via torrent because all of the Ubuntu download mirrors were being clobbered silly!  So, anyway, I burned it to CD, rebooted, started the install, and prayed.

The Linux gods must've been smiling on me, because this install went absolutely without a hitch!  My wireless card was recognized right off the bat and, as soon as I entered in my WPA key, I was off and running. Installed the restricted mode drivers for my nVidia GPU, and went to work on customizing. My laptop has been running within Hardy since Thursday night.

Was it flawless?  No. It didn't take me long to figure out that sudo was broken. Thankfully gksudo still worked, and I was able to edit my hosts file, and sudo worked again.  I also ditched Network Manager and installed WICD after having to enter my WPA key one time too many. The only other problem I had was with network shares permissions going all screwy-lewy, but that turned out to be an issue with my file server (running Feisty). And there are a couple of Compiz windows effects that aren't working properly (minimize animation, window dropshadows).

I honestly have to say that this has been the best, easiest Ubuntu install I have ever experienced!  I realize I'm still a relative newbie, having lost my Linux virginity to Feisty, but - sheesh!  If only my Windows installs were this easy!

Worst version yet?  Not in the least bit! Gusty has that dubious honor for me. Feisty was good, but it seemed basic, in a Windows 95-ish sort of way; that, and setting up a wireless network was a royal pain in the ***. Gutsy was horrible. It refused to play nice with my laptop at all, throwing bootup errors about my CPU-PCI bridge, complained about there being "too much work" for IRQ4 (my IRda port, which wasn't even being used), kept losing wireless connectivity every time my card did an AP scan, and just ultimately crashed and burned into a fiery mess within a week.  So far, I have to say, Hardy has be hooked on Linux at last!

Now, Firefox 3 Beta 5...  Adding that to the distro was a mistake. I find myself yearning for Internet Exploder with every second I'm using this thing!  I may just ditch it and use Firefox 2 instead, and wait for FF3 final.

---

### Post by bingobingo on 2008-04-28
Can not say I am a fan of this upgrade so far, need to go back to 7.10. Though the upgrade went smoothly and everything works from what I can tell, 8.04 is hogging major cpu cycles, mostly 100% loaded all the time (even with no 'apps' running), making for a very slow computer. Can not say what is causing it, but something is certainly not right. And i noticed a huge amount of forking going on, no where near what was happening in 7.10.

Nec PowerMate Eco (awesome earthfriendly computer)
Transmeta Crusoe TMTM5800 (wish it was Efficeon)
Freq. 895.967 MHz
Ram 360 Mb
IDE Fujitsu 20g Hd
Intel Wireless mini-pci

---

### Post by zdude on 2008-04-28
I think this release sucks about as bad as the gutsy release. Gutsy would at least work but I fought hangs up/freezes forever. Finally, running the 169.04 nvidia driver fixed it. Now with hardy, sudo didn't work and gksudo only worked on the second try. After awhile gksudo even quit. There would be loads of gksudo processes but none visible. Finally the shutdown/restart button quit working and the only way to shutdown was pulling the power. I restored my gutsy backup, which now works (sans suspend/hiberate) and all is well again. I'll sit on the sidelines for awhile or maybe try another distro.
I think Fiesty was the best release ever and I've been using ubuntu since hoary.

---

### Post by Stik on 2008-04-28
I haven't had many issues with hardy. I had been using slackware for the
last 7 years and finally got tired of the time it took to keep it upto date.
Don't get me wrong, I still to this day feel it is the best distro I've
used, but I felt It was time to move on to something a little bit less time
consuming to maintain. Other than than pulse audio being nowhere near ready
for default and the inclusion of the firefox beta I have had no issues at
all with hardy. I started using it just before it went beta and kept
kept up on upgrades. I have been mildly suprised at how well my desktop
works. Keep up the good work guys..

---

### Post by MattDTownsend on 2008-04-28
I successfully built the .25 kernel, and we'll see if that solves my locking. So far, so good. I had to built ndiswrapper for it, as well -- so fair warning to anyone who tries. Make sure you've got that source, if you need it.

Anyone have luck building NVidia drivers for this kernel? (Yes, if you use an nvidia card, you will need these, too. Or you will need to switch the driver listing in /etc/X11/xorg.conf from "nvidia" to "nv.") There seems to be some issues, and I've tried manual and automatic patching with no luck.

The nv driver is okay, but video saturations are all wrong.

We'll see how long I want to go on like this. If there's no resolution, i.e., a new kernel, available by the weekend, I will most likely ditch to another distro or BSD. Assuming, of course, this kernel build I've done solves it as people suggests. Hardy Heron makes a mockery of the LTS structure. One would expect a lot of time into development of the LTS version to weed out these sorts of problems. Otherwise, why even bother distinguishing this as the safer, more stable option? What a joke.

---

### Post by bikeboy on 2008-04-28
> **MattDTownsend said:**
> One would expect a lot of time into development of the LTS version to weed out these sorts of problems. Otherwise, why even bother distinguishing this as the safer, more stable option? What a joke.

What makes you assume it didn't? Did you contribute?

And for the millionth time, LTS does not means "l33t most stablest distro release everz!!!". It means exactly what it says. It will receive bug fixes and security updates for twice as long as the other releases, allowing those who need stability (of the platform & OS) to stick with it and benefit as it settles down the be more stable and reliable than our other already stable releases.

---

### Post by MattDTownsend on 2008-04-28
What LTS means and what people expect of it are clearly two different things. I know there are many people who have worked hard on Ubuntu, and I've tried to do my part by spreading the good news of Ubuntu over the last few years.

But there is clearly a problem with Hardy Heron. Maybe a big one, for some people. Right now, I have a dual-core paperweight. Ubuntu may be shooting itself in the head with this one. I've seen very popular distributions get ditched for other options when they go down this road. And while I've seen smug responses to real problems before, it's never involved a distro that has undergone apotheosis like Ubuntu. The "Well, it may be rendering some people's systems unusable, but it's still pretty cool" response is not acceptable. Especially when these systems functioned with every previous release.

So, yes, I am upset. But I'm not trying to attack any developers. I'm just saying that I've been around the block, and that for a stable release, this is bad news bears.

And since my compiled .25 kernel failed to stop the freezing, I'm going to have to shoot for another distribution or for BSD. But I've been on most of them, at this point, so it's no biggie. I like Ubuntu, but I can only wait for a few more days. What's really bothers me is that I feel I no longer have an option to suggest to Linux newcommers...since, $1,500 paperweight. Even if this is fixed, soon, I don't know what to think about that. I couldn't recommend Ubuntu now.

---

### Post by Zach_the_Lizard on 2008-04-28
As a new user of Ubuntu, and someone who has limited knowledge of Linux in general (but I am fairly technical and will learn soon), Ubuntu 8 was excellent for me and an upgrade over the previous version. I didn't have to compile this or that, or go into a terminal and wget the nvidia drivers because the screen is all screwed up. Nor did I have to fool around with getting my Broadcom wireless drivers working.

All I had to do was use the install cd, connect an ethernet cable to download the non-free drivers and then I could be untethered.

Ubuntu is years ahead of Vista, and I, a long time Windows user have made the change. All I miss is a few games. I also am missing the massive harddrive corruptio n that screwed over my Vista installation, and Vista's lack of ability to install without messing with the BIOS. This is the first time I can say Linux installed more flawlessly than Windows. Progress has been made. It's far better than when I tried using Fedora.

For me, Ubuntu 8 is the best Linux has to offer. But then again, I've only used Fedora and Ubuntu. 

As a side note, I really loved the live cd install as you play around idea. It's great being able to browse the web with Firefox while the OS is installing.

---

### Post by tenmoi on 2008-04-28
Hardy Heron is the BEST distro ever because I know when exactly it will crash and WHY. I am lucky here 'cos I can easily reproduce the crash.
Under mild load it will NOT lock up. Tell it to copy a big file (in my case 3 or 4 Gigabite)and it locks up. Tell it to compile kernel 2.6.25 and it locks up half way through the compilation. Tell it to download 100 M files and play an avi file with VLC and it locks up. TARDY Heron is in fact so tardy that it cannot do heavy work. 

Back to Windows and wait for some months for this to be straightened out.

---

### Post by Junk_head on 2008-04-28
A whole lotta hate brewing here...

Im having lock-ups too but you know what are you gonna do? I'll wait for the updates, I think it might have to do with dual booting on my side, i installed hardy with vista on the side. This occurred issue with gutsy too, i did a clean install with just a gutsy only hdd and problems gone. I also used a hardy RC .iso, when i should have just waited for the official release. But it seems these lock-ups are occurring with the official release aswell. So dunno what im gonna do.

---

### Post by FredB on 2008-04-29
Deleted post.

---

### Post by Guilden_NL on 2008-04-29
Forget the lack of driver support, the lockups (yes I have them non-stop) what bothers me is the inability to blacklist drivers or better yet, do a Microsoft style install and tell the OS to ignore: "A, B or Wireless" (as many of us have had the poor result with HH).

That will allow Linux to make a dent in the desktop. HH has made a huge backward leap and may have killed any forward momentum that GG had going.

---

### Post by Guilden_NL on 2008-04-29
> **MattDTownsend said:**
> I like Ubuntu, but I can only wait for a few more days. What's really bothers me is that I feel I no longer have an option to suggest to Linux newcommers...since, $1,500 paperweight. Even if this is fixed, soon, I don't know what to think about that. I couldn't recommend Ubuntu now.

BINGO!  I agree, no bashing here for the fun of it, but I've been smacked hard for making negative comments.  I've decided to move to SUSE and pull my entire home network to it, and not ever mention Ubuntu in my 150,000 + employer where I am an enterprise architect.

Too many Canonical people with fragile personalities lurking about with hard deadlines tattoo'd on their foreheads.

---

### Post by FredB on 2008-04-29
What is your hardware ? Even Windows doesn't support all existing hardware on Earth.

I have kinda special hardware on my laptop - including the horrible atheros 5007eg wifi hardware - and it works flawlessly.

Can't understand, that's all.

But I think if we go back 6 months ago, we could see the same "complaining and whining", replacing Hardy by Gusty and Gutsy by Feisty.

So, what's new after all ?

---

### Post by Polygon on 2008-04-29
so roll back to gutsy until it gets fixed

you are forgetting that not everyone has these problems, jsut because a small percentage of the population are getting these lockups doesnt mean the entire release is bad. For me hardy is working perfectly, and i love it.

Maybe for the next version you should try the alphas and betas and report bugs so they get fixed BEFORE the final product gets released, so its better for everyone

---

### Post by SomeGuyDude on 2008-04-29
I have an extremely infrequent lockup.

The thing is, my opinion on this kind of thing is quite different than with Windows. While on Windows I accepted periodic lockups because it worked for the most part and I had no idea how to use Linux, with Ubuntu I overlook the lockups because I've noticed that has the updates roll in, they become more and more uncommon. Give it a week and they'll be gone.

---

### Post by FredB on 2008-04-29
> **Guilden_NL said:**
> BINGO!  I agree, no bashing here for the fun of it, but I've been smacked hard for making negative comments.  I've decided to move to SUSE and pull my entire home network to it, and not ever mention Ubuntu in my 150,000 + employer where I am an enterprise architect.

Too many Canonical people with fragile personalities lurking about with hard deadlines tattoo'd on their foreheads.

You're free to go with SuSE, which is slow and fat.

If you don't talk your 150 000 employees about ubuntu, they will heard of it another way.

There is about 100 distros right now. If you don't like one, go for another, and stop breaking nerves of other people with your posts.

---

### Post by Guilden_NL on 2008-04-29
> **FredB said:**
> What is your hardware ? Even Windows doesn't support all existing hardware on Earth.

I have kinda special hardware on my laptop - including the horrible atheros 5007eg wifi hardware - and it works flawlessly.

Can't understand, that's all.

But I think if we go back 6 months ago, we could see the same "complaining and whining", replacing Hardy by Gusty and Gutsy by Feisty.

So, what's new after all ?
Fred, 
I have a Broadcom 43xx wireless card in a desktop too far away to plug into an ethernet connection.

Do I know about Broadcom and Ubuntu issues?  Yes I do sir!

I too have been running Hardy since early Beta with no problems, and it actually caused me to load Ubuntu on a system that it wouldn't load on due to a known chipset issue with my SATA drives.  No problem, it was well documented and I lived with it until someone provided a notice that HH Beta fixed the bug - VOILA! It worked and I was happy.

However, this Broadcom wireless card was reported and prematurely closed.  Nothing anyone could say could convince anyone to reopen the bug report.

OK. But HH was released as LTS into an environment where there are tens if not hundreds of thousands of these cards, and there is NO way to black list the driver, therefore no way to upgrade, or do a clean install.

I am a Linux supporter, but the competition is Microsoft.  Their install scripts almost always (but not perfectly) allow you to skip a known driver problem on install.  Ubuntu must match or better that with its install scripts if it wishes to increase market share.  At this point, expert users are throwing up their hands and mumbling about the install of HH.

I am all ears if you have an idea how to blacklist a driver on a clean install of HH on a wiped drive.  I've tried it with a wiped drive with a clean install of Gutsy and a blacklist statement, then an upgrade.  

Any thoughts on how else to beat this install routine?

---

### Post by Guilden_NL on 2008-04-29
> **Polygon said:**
> so roll back to gutsy until it gets fixed
Maybe for the next version you should try the alphas and betas and report bugs so they get fixed BEFORE the final product gets released, so its better for everyone

Polygon,
I did that.  And reported the Broadcom issue and it was prematurely closed.

But here's the much bigger issue: why can't we blacklist through a GUI (think Windows users) or even a terminal, when we know that there is a problem? You can do this in Windows, we need to make sure that Ubuntu has the same.  It's not that difficult if the install set up allows addition to the install script.

Believe me, I am not bashing Ubuntu as a Noobie - I am very upset that a known problem was prematurely closed and nobody seems to care.  The number of Broadcom problems with Ubuntu is well known and numerous (do a search and see).

Your thought process is dead on, but I did that and still see a big hole in the LTS release.

But I sincerely mean this, thanks for keeping your response on topic, on target and not bashing me for having stated problems.  I do appreciate your post.

---

### Post by MONODA on 2008-04-29
> So it locks up...blame it on the drivers, not the OS
no it's not the drivers, it's the fact that so much beta and alpha software has been included by default in hardy (and other ubuntu releases) with no warning (compiz fusion). Anyway, I am also having problems with hardy, random lockups and it did not install the driver for my wireless; neither were a problem in gutsy. also ff3 and nautilus hang for several minutes randomly. everything is much slower and less stable. I was really disappointed with this release but it doesnt feel right to complain since I am getting this for free so I switched to OpenSuSE :).

---

### Post by samjh on 2008-04-29
While I understand the pent-up frustrations of those whose Hardy installations are not working properly, I do wonder whether it's worth scaring new users away by posting those complaints in this very prominent forum.

Fact is, the vast majority of users are satisfied with Hardy ([Hardy Heron Satisfaction Survey](http://ubuntuforums.org/showthread.php?t=766982)).  It's a fairly good result for the Ubuntu team.

Most users can install Hardy and work with it just fine, so this sort of mass-complaining seem to be hysterical rather than rational.

If you have problems, report it on Launchpad.  Or else discuss it on more appropriate forums: [Testimonials and Experiences](http://ubuntuforums.org/forumdisplay.php?f=103) and [General Help](http://ubuntuforums.org/forumdisplay.php?f=331).  Keep in mind also that some problems cannot be solved by Ubuntu developers or MOTUs, and require fixes upstream.

---

### Post by jeluranni on 2008-04-29
Glad to hear I'm not the only one who feels this way. The release candidate was solid. About a week before the final release it started having problems. CPU usage started spiking and I personally feel Firefox beta three is way too buggy to be the default browser. What use is the system monitor if it can't identify the process that is taking up all the CPU's time?

---

### Post by Quillz on 2008-04-29
So since system lockups are happening to you and a minority of users, it suddenly makes Hardy Heron the worst version of Ubuntu ever? I doubt that. Personally, I had many, many issues with 6.06, but I wasn't out complaining, saying "blah blah blah this version sucks blah blah blah."

That said, I did experience lockups with 6.06 and 7.04, but never with 6.10 or 7.10. Odd.

---

### Post by rockface on 2008-04-29
My main system always has Ubuntu installed by default, Gutsy at this moment in time. But it is unusual for me to install (even an LTS release) inside the first four to six weeks of release. I've installed Hardy beta, rc and final on my other machines and it just does not seem quite right. Memory and cpu spikes, applications that work once then fail to initialise the next occasion you use them. Inconsistant and erratic behaviour that cannot be reproduced because they happen at random.

Will these problems be sorted out, almost certainly. But don't dismiss others that are, and continue to have issues with Hardy. Ubuntu is quickly becoming as bad as Mac and Windows fanboism in its respective users. This needs to be stamped out or Ubuntu as a community is going nowhere, fast!

---

### Post by Quillz on 2008-04-29
> **rockface said:**
> My main system always has Ubuntu installed by default, Gutsy at this moment in time. But it is unusual for me to install (even an LTS release) inside the first four to six weeks of release. I've installed Hardy beta, rc and final on my other machines and it just does not seem quite right. Memory and cpu spikes, applications that work once then fail to initialise the next occasion you use them. Inconsistant and erratic behaviour that cannot be reproduced because they happen at random.

Will these problems be sorted out, almost certainly. But don't dismiss others that are, and continue to have issues with Hardy. Ubuntu is quickly becoming as bad as Mac and Windows fanboism in its respective users. This needs to be stamped out or Ubuntu as a community is going nowhere, fast!
I agree there are far too many Linux/Ubuntu fanboys, but as Ubuntu becomes more and more popular, the user base grows with it. So it's only natural that there will be an ever increasing number of fans and fanboys.

Anyway, I did have a few minor issues with 8.04, mainly relating to Firefox. But they were quickly fixed.

---

### Post by Saint Angeles on 2008-04-29
this weekend i installed hardy on the 8th computer i've tried it on.

i've installed it a pentium III, 3 pentium 4s (totally different kinds though), an old athlon, a dual core... and a couple i didn't even care to find out.

i've never had a single problem (other than having to use ndiswrapper on my sister's computer)

please think about your thread titles before trying to start a flame war. just because you have had bad luck does not make hardy a bad OS.

report your bugs and thats it. i saw nowhere that you are supposed to report a bug then complain your butt off on ubuntuforums.

PS red hat, mandrake, gentoo, debian, winXP... are all the worst OSes by your standards because i've had problems with those.

---

### Post by FredB on 2008-04-29
OK with you. But the problem is like another people said : *hysterical* posts. 

If people don't like this version, why the h*** do they install it ? Don't they have the opportunity to grab live cd and see if it works before installing it ?

Anyway, integrism is bad, as you said too.

---

### Post by Quillz on 2008-04-29
> **FredB said:**
> OK with you. But the problem is like another people said : *hysterical* posts. 

If people don't like this version, why the h*** do they install it ? Don't they have the opportunity to grab live cd and see if it works before installing it ?

Anyway, integrism is bad, as you said too.
You're right, you'd think more people would try the live CD first. Although, I do recall the live CD of 6.10 being a little different from the actual install. Not just that things were slower, but some apps didn't work at all on the live CD but worked fine on the install. Not sure if this has been fixed or not.

---

### Post by swoll1980 on 2008-04-29
I have had no problems with Hardy, and find it quite enjoyable to use. As for a lot of people having these problems I think that is exaggerated (considering how large the Ubuntu user base is) if 60,000 people had the problem it would be about 1% of the total user base that hardly seems like a lot. Someone commented that because there was 11 pages dedicated to a thread on this that it must be affecting a large number
of people. What is that like 20 people? when the number of affected people reaches 1%
Then I think the Ubuntu devs can be concerned.

---

### Post by agim on 2008-04-29
couldn't agree more

---

### Post by Saint Angeles on 2008-04-29
> **MONODA said:**
> no it's not the drivers, it's the fact that so much beta and alpha software has been included by default in hardy (and other ubuntu releases) with no warning (compiz fusion). Anyway, I am also having problems with hardy, random lockups and it did not install the driver for my wireless; neither were a problem in gutsy. also ff3 and nautilus hang for several minutes randomly. everything is much slower and less stable. I was really disappointed with this release but it doesnt feel right to complain since I am getting this for free so I switched to OpenSuSE :).
no warning? is this a joke cuz i can't tell.

do you remember gutsy? it had compiz with no warning too. i guess the warning is in the release notes, and the wiki, and the forums...

lemme show you a trick... you ready?

```
metacity --replace
```

as for the firefox thing... i noticed that beta4 seemed better than beta 5. i reduced my "swappiness" and now its lightning speed again.

google "reduce swappiness in ubuntu" for details... its default at 60, i lowered mine to 10

i don't exactly know why that helped but it totally did.

now we need less of these "problem blanket threads"... if you have a wireless driver issue, goto the correct forum and recieve help. ive found that there's rarely an issue on any version of linux that can't be fixed.

---

### Post by hellmet on 2008-04-29
I've always been with the idea of a one or one-half year release cycle. It gives so much time to develop the OS, and fix bugs before releasing it. And people can actually settle with the current version before jumping and upgrading to the next version in search of cutting-edge features.

Canonical.. you listening?

---

### Post by Quillz on 2008-04-29
> **hellmet said:**
> I've always been with the idea of a one or one-half year release cycle. It gives so much time to develop the OS, and fix bugs before releasing it. And people can actually settle with the current version before jumping and upgrading to the next version in search of cutting-edge features.

Canonical.. you listening?
I don't see what difference that release model would make. It's not like you're being forced to upgrade to 8.04. If you're comfortable with 7.10 and it works great for you, there's no point to upgrade. People always seem to think a new software version means they must upgrade, and it's just not true. Unless you're running a really old version that's no longer supported, there's no reason to blindly upgrade.

---

### Post by mybunche on 2008-04-29
Even though I am still using 6.10 on this PC because I am too lazy to save my configs, I have tried 8.04 and it works fine for me. The only issue I have is with Firefox3b5 not displaying some webpages correctly. 

I wonder what the cause is if people are having problems because clearly there are no problems for many others. Maybe a combination of:
-problems with CD image eg downloading, burning, disc, etc
-hardware compatibilty
-kernal and Gnome problems
-maybe be better if it was a 2 CD install instead of everything crammed on one CD. More room to maneuver if things need to be added.

---

### Post by Nunu on 2008-04-29
I like the fact that its a bit "buggy", Gives me a reason to try and fix it. not only do i learn more about Linux, I also learn the code.

---

### Post by hellmet on 2008-04-29
People upgrade in expectation that the new release will bring features that'll make their Linux life better.. 
Say you were using XP, and Vista came out. Wouldn't you want to try it and see what new features it had? How this new OS would make your life easier, and how it would enhance your productivity.
If Canonical had a 1 year cycle, there would be no release for people to upgrade to every 6 months, and that'd bring more stability to each release too.
I'm not able to explain it well in words, but that is my idea.

---

### Post by paul.prinsloo on 2008-04-29
Sorry  have to disagree..I had lockups with every version till now..for the first time I have now run for a full day without any problems whatcoever!!

Compiz-real used to eat up my machine, mouse used to lock-up, machine used to cometo a grinding halt if I leave it alone for a while...not any more!

thanks Ubuntu

---

### Post by FredB on 2008-04-29
> **hellmet said:**
> People upgrade in expectation that the new release will bring features that'll make their Linux life better.. 
Say you were using XP, and Vista came out. Wouldn't you want to try it and see what new features it had? How this new OS would make your life easier, and how it would enhance your productivity.
If Canonical had a 1 year cycle, there would be no release for people to upgrade to every 6 months, and that'd bring more stability to each release too.
I'm not able to explain it well in words, but that is my idea.

Well, I think a 6 month release is better because :

1) Computer is evoluting fast.
2) Some software can have 2 major releases the same year, think of Gnome for example.

Nobody threatens you and force you to upgrade to the latest version available, after all.

---

### Post by sstusick on 2008-04-29
I too, have had several lockups and Hardy Heron's only been installed a few days. It also hangs randomly for a few seconds, but I thought this might have been attributed to Compiz. 

Network manager seems to be buggy -- my wifi signal keeps jumping from 70%-89% and I am in the same room as the router. Normally the signal should be 94-96%, at least that's what it was on Gutsy. The signal also doesn't seem to change much (according to Network manager) when I am in the Living room, which is about 30 feet away. 

Other than the lockups, and a quivering Network manager, I like Hardy and hope the kinks can be worked out.  

Just a note that this is the first version of Ubuntu that has actually locked up my laptop, and I've been using Ubuntu since last year (Feisty). The lockups on SuSE is what caused me to leave that distro. 

If I experience another lockup, I will probably wipe the partition and go back to Gutsy.

---

### Post by regomodo on 2008-04-29
well, apart from hardy setting up Grub so badly wrong, it has been perfect. Gutsy was a whole mess for my pc that i actually gave up on Ubuntu because of it.

---

### Post by gn2 on 2008-04-29
I haven't had any problems on my C2D desktop PC with Ubuntu 8.04 or on my PIII laptop with Xubuntu 8.04 other than to replace FF3 which I didn't like.
I've been using 8.04 since it was an RC.

For my laptop 8.04 is a major step forward, 7.10 did not work at all well but the problem which was specific to older hardware has been fixed.

---

### Post by FredB on 2008-04-29
Well, you don't like firefox 3, and you'll have to use it next year, as firefox 2 support will be plugged out in december if firefox 3.0 is released next june.

Besides this, don't say too loud you don't have problems with Hardy... You will make angry some persons here :p

---

### Post by bikeboy on 2008-04-29
> **sstusick said:**
> I too, have had several lockups and Hardy Heron's only been installed a few days. It also hangs randomly for a few seconds, but I thought this might have been attributed to Compiz. 

Network manager seems to be buggy -- my wifi signal keeps jumping from 70%-89% and I am in the same room as the router. Normally the signal should be 94-96%, at least that's what it was on Gutsy. The signal also doesn't seem to change much (according to Network manager) when I am in the Living room, which is about 30 feet away. 

Other than the lockups, and a quivering Network manager, I like Hardy and hope the kinks can be worked out.  

Just a note that this is the first version of Ubuntu that has actually locked up my laptop, and I've been using Ubuntu since last year (Feisty). The lockups on SuSE is what caused me to leave that distro. 

If I experience another lockup, I will probably wipe the partition and go back to Gutsy.

I was having lockups during the beta phase due to my wireless (rt61). Ubuntu backported a driver, I installed it and I haven't had a problem since. Moral of the story, as above, seeking help for individual issues is more constructive than than complaining.

---

### Post by gn2 on 2008-04-29
> **FredB said:**
> Well, you don't like firefox 3, and you'll have to use it next year, as firefox 2 support will be plugged out in december if firefox 3.0 is released next june.


Very true. I'm hoping that the things I don't like in FF3 will all be fixed by the time it's out of Beta.
If they're not maybe I'll just try a different browser(s) 
That's the joy of Linux, having so many good options.

---

### Post by samjh on 2008-04-29
> **hellmet said:**
> I've always been with the idea of a one or one-half year release cycle. It gives so much time to develop the OS, and fix bugs before releasing it. And people can actually settle with the current version before jumping and upgrading to the next version in search of cutting-edge features.

Canonical.. you listening?You ought to take a look at some of the reasons why Mark Shuttleworth and the original Ubuntu developers chose the 6-month release cycle.

A 1.5 year release cycle is too slow.  You're almost approaching Debian's slowness.  Fedora releases once every 6 months or so; Opensuse releases between 6 to 10 months; even the enterprise-oriented Red Hat Linux releases every 6 months.  Any release cycle longer than 12 months is just too slow, especially for an OS targeting the consumer PC market.

The problem is not the length of the release cycles, but the number of new features that are being crammed into each release.  Sure, Ubuntu looks very innovative that way, but it hurts stability.  Although my current Ubuntu system is working very well, there are some minor issues, and some of my past installations had show-stoppers which were eventually fixed but very inconvenient nonetheless.

What we DON'T need, are over-the-top threads like this one.  It doesn't take much to realise that the majority of Hardy users are getting on just fine.  This sort of scaremongering and denouncements only hurt Ubuntu's development, while doing nothing to fix the actual problems behind the complaints.

---

### Post by kinematic on 2008-04-29
> **wpshooter said:**
> If you (speaking collectively) are one of those persons that believes that an O/S (be it M/S Windows, Linux, or any other O/S) can be "upgraded" from one version to another with NO problems, **then you probably still believe in the tooth fairy**.

Bet you never tried Debian testing or unstable. I've been running and upgrading testing for about 2 yrs now and there are people on the Debian forum who've been doing the same thing far longer so your statement is simply not true.

---

### Post by samjh on 2008-04-29
> **kinematic said:**
> Bet you never tried Debian testing or unstable. I've been running and upgrading testing for about 2 yrs now and there are people on the Debian forum who've been doing the same thing far longer so your statement is simply not true.

I ran a hybrid Debian 4.0/Lenny system for about 3 months.  Ran into several problems with broken packages and one X breakage.  It was reasonably stable, but not as stable as then-current Ubuntu 7.10.

Debian Etch by itself was very stable though.  But I don't have the patience to wait 2+ years for stable releases.  Debian Backports do a pretty good job, but again, the main system is just too obsolete for my liking.

---

### Post by hellmet on 2008-04-29
> 
You ought to take a look at some of the reasons why Mark Shuttleworth and the original Ubuntu developers chose the 6-month release cycle.

A 1.5 year release cycle is too slow. You're almost approaching Debian's slowness. Fedora releases once every 6 months or so; Opensuse releases between 6 to 10 months; even the enterprise-oriented Red Hat Linux releases every 6 months. Any release cycle longer than 12 months is just too slow, especially for an OS targeting the consumer PC market.

The problem is not the length of the release cycles, but the number of new features that are being crammed into each release. Sure, Ubuntu looks very innovative that way, but it hurts stability. Although my current Ubuntu system is working very well, there are some minor issues, and some of my past installations had show-stoppers which were eventually fixed but very inconvenient nonetheless.

What we DON'T need, are over-the-top threads like this one. It doesn't take much to realise that the majority of Hardy users are getting on just fine. This sort of scaremongering and denouncements only hurt Ubuntu's development, while doing nothing to fix the actual problems behind the complaints. 		  		  		  		 		 			 				__________________

Well put samjh. 
Anyways.. the developers always know the best. Btw, I was wondering if a slower cycle would help decrease or would it increase the cost of production of ubuntu. That is salaries to employees, support staff, free cd distribution etc. 
I got 10 cds during Breezy time, and now I was allotted only one cd. I'd have liked atleast 2 cds, one i386, one 64bit. Alas

---

### Post by FredB on 2008-04-29
> **gn2 said:**
> Very true. I'm hoping that the things I don't like in FF3 will all be fixed by the time it's out of Beta.

Such as ? ;)

> If they're not maybe I'll just try a different browser(s) 
That's the joy of Linux, having so many good options.

Indeed. I'm using homemade pre-release candidate version of Firefox. And they work ;)

---

### Post by samjh on 2008-04-29
> **hellmet said:**
> Well put samjh. 
Anyways.. the developers always know the best. Btw, I was wondering if a slower cycle would help decrease or would it increase the cost of production of ubuntu. That is salaries to employees, support staff, free cd distribution etc. 
I got 10 cds during Breezy time, and now I was allotted only one cd. I'd have liked atleast 2 cds, one i386, one 64bit. Alas

I thought about your post again, and think that a 12-month release cycle has merit, but on one condition...

A strong and regularly-updated backports repository.

The current Ubuntu backports repos are extremely limited.  We should be looking at something like the Debian backports repos which have a lot of popular packages.

If Ubuntu adopts a 12-month release cycle, then the backports repo for each stable release should be up-to-date with the latest versions of the most popular packages, especially OpenOffice, Firefox, Thunderbird, Mono and Java, and perhaps even Gnome/KDE/Xfce, etc. etc.

---

### Post by hellmet on 2008-04-29
I don't really understand the concept of backports.. So can't really reply to your post.

---

### Post by gn2 on 2008-04-29
> **FredB said:**
> Such as ? ;)

Don't like the way FF3 handles bookmarks, specifically there are three folders in the Bookmarks sidebar that I cannot delete and it seems bookmarks have to go in one of these three folders that I want to delete. :(

Don't like having what is basically a hack to run Add-ons, the Add-ons will no doubt be updated in time but some are still not compatible just now, even with the nightly tester tools add-on.

Beta software is fine for those who want to run it, but it's not for me.
My own opinion is that having a beta web browser as default for an LTS release is just plain wrong.
Nice to have FF2 as an option in the meantime though :)

---

### Post by K.Mandla on 2008-04-29
Moved to Testimonials and Experiences.

---

### Post by FredB on 2008-04-29
> **gn2 said:**
> Don't like the way FF3 handles bookmarks, specifically there are three folders in the Bookmarks sidebar that I cannot delete and it seems bookmarks have to go in one of these three folders that I want to delete. :(

Which folders ? 

> Don't like having what is basically a hack to run Add-ons, the Add-ons will no doubt be updated in time but some are still not compatible just now, even with the nightly tester tools add-on.


Erh... Looks like extensions coders are waiting for RC to adapt their code.

> Beta software is fine for those who want to run it, but it's not for me.
My own opinion is that having a beta web browser as default for an LTS release is just plain wrong.

Let me free to think you're not right. In about 6 weeks, Firefox 3 will be at least in RC1 or even RC2 milestone. And they will be provided for Ubuntu Hardy.

> Nice to have FF2 as an option in the meantime though :)

Besides the "big problem" related to urlclassifier file, the only big problem is flash plugin nonfree...

---

### Post by SupaSonic on 2008-04-29
+1 for lockups. Have no idea what's causing them, but I suspect FF3. very sad that there's no way of debugging the problem.

EDIT: I had them in gutsy as well

---

### Post by gn2 on 2008-04-29
> **FredB said:**
> Which folders ?

The three default ones which are part of the FF3 Bookmark system.

As for FF3 being beta, 8.04 could have been released with FF2 as default and changed to FF3 once FF3 was the finished article.

---

### Post by ssuuddoo on 2008-04-29
by me, everything is ok.
I WARN you, do not WARN others and do not PANIC.

shame.

bugs are everywhere, but we should put them adequate weight.
and when your installation freezes, it does not mean that the 
WORLD should beware of installing Hardy, because the world is not
you.

PS: when hardy is so hard 2 U, install gutsy again. no problem.

oo

---

### Post by MattDTownsend on 2008-04-29
All of this has happened before. All of this will happen again.

I've seen this many times. I've been using Linux in one form or the other on the desktop for 10 years now. All you have to go on is my word and the word of others who have paperweights now sitting on their desk: something isn't quite right with Hardy. And this is a wrong turn.

Are some of us irate? Sure. But if an irritable userbase were the key to killing a distribution, Linux as a whole would have been dead a long time ago. Of far more danger to Ubuntu is just what I'm seeing here -- those of you who respond to our problems with a testament of how good Ubuntu is, or how we should downgrade to Gutsy, or whatever -- that's not helping. For several pages of this thread, a number of people tried to find a solution to this lockup problem, or a workaround -- and so far, none has worked for me. And it seems that way for a few. I have a relatively normal system with plain-jane hardware -- nothing fancy, nothing very incompatible. I built it that way. Every previous release of Ubuntu ran fine. Now, I upgrade, and I can't even get an error report when it locks up.

The one thing Linux must do is NOT lock up randomly. That's it. When it does that, it's failed in doing what it's meant to do. And if you really think the best way to help us is to tell us to watch what post title we use or to tell us to not to "scare" off newbies who, after the next release, may also have a paperweight sitting on their desk -- well, don't expect a very large userbase in, say, two years.

All of this has happened before. All of this will happen again.

---

### Post by bilal.17 on 2008-04-29
the same thing happens to me... but very occasionally so i'm not sure if its the same problem. But it sounds like it has the same symptoms with just the mouse working and everything else frozen. Very strange to be quite honest.

---

### Post by hal_bg on 2008-04-29
[QUOTE=Jim March;4798322]Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.


I agree!!! My Dell C400 is freezing once an hour. No debug info at all... But I hope it will be fixed.

---

### Post by ed-koala on 2008-04-29
It's sad to see so many folks having problems.  I myself have a AMD 64 processor and have been running Hardy for 2 months.  Yes, it had some issues in beta, not the least of which was programs shuitting down unexpectedly.  But, it got fixed.

I'm experiencing no problems whatsoever with my made-from-scratch mutt PC.  Everything works smoothly, even FF 3.  Granted I don't have a wireless network (which has always caused issues in every release), but this version is a delight for some users like myself.

I trust the dev's will fix the lockup issue, eventually.  I recommend using Gutsy until then.  No sense giving up on Ubuntu just yet!!

---

### Post by bigbrovar on 2008-04-29
me too i have been experiencing lockups with my ubuntu .. seem my problem was caused when i use firefox .. or opera .. so i stoped both and i now use epiphany seamoney flock and the system has been quite stable since..

---

### Post by bigbrovar on 2008-04-29
this thing is now driving me nuts ... i have had two lockups between the now and my last post which was like an hour ago .. i think i have had inuf and am downgrading to gutsy as we speak... i just cant take it anymore .. i have a 2gb,2.0gzh core 2 duo,nvidia geforce 8400gt hardly a system low on hardware and definitely not one that should crash at any slight click of a program any program... it gets worse by the day ..i tot it was caused by just FF3 but even opera,epiphany,ff2 have all caused my system to lockup... yeah i loved how improved,polished and fast hardy heron is .. but damn! the crashes just dont make sense.. not when i just wiped out vista from my system thinking that Ubuntu would give me the stability i need...gutsy gave me that.. and to some extent even the beta version of hardy was seamless.. just dont know what went wrong.. all i know is that ths system locks up like hell.. Gutsy here i come

---

### Post by ukripper on 2008-04-29
I have not updated my grub with hardy kernel as yet after the upgrade, I am still using 2.4.22(gutsy kernel) for hardy and everything is just expected. Using firefox 2 instead of ff3 beta5.  

I will probably move to hardy kernel soon though.

---

### Post by Frank Black on 2008-04-29
Installed Heron on my sons computer last weekend. We did have Dapper on it. Heron seems sluggish, slow, kind of a bloated feeling. Like eating lots of refried beans as compared to Dapper. Not completely locking up to the point of reboot but too many of the "grey out" screens which I believe I read is an indication of app/process not responding. Had used a Belkin wireless card with Dapper with no problems. No such luck in Heron so I put in a Linksys, (or D-Link I can't remember) and network works fine now. Internet side anyway. I haven't tried computer file sharing yet.(counting this one I have three computers on the network sharing DSL from a wireless router). I figure the developers will get things straightend out in due time. When I encounter problems and get frustrated I try to remember that Ubuntu is FREE and Windoze costs several hundred dollars for the OS not counting MS Office.

---

### Post by karellen on 2008-04-29
I've said it before and I'll say it again: there is absolutely no excuse for something that worked in a previous version of Ubuntu and in Hardy it doesn't. no "OEM fault for not releasing drivers for Linux", no "obscure bugs not reported in time", nothing. the past is the evidence

---

### Post by kaylus on 2008-04-29
> **MattDTownsend said:**
> All you have to go on is my word and the word of others who have paperweights now sitting on their desk

Oh give me a freaking break. Can we be any more melodramatic? There is nobody right now with a computer that has become so worthless that it can't be used for more than a paperweight.

If the OS isn't taking on your system, downgrade until stability is achieved. Trying to spread fear into people by saying your computer is so facked up that it can't be used at all is disingenous. Stop lying.

> I have a relatively normal system with plain-jane hardware -- nothing fancy, nothing very incompatible. I built it that way. Every previous release of Ubuntu ran fine. Now, I upgrade, and I can't even get an error report when it locks up.

For you. What is with people believing the entire world revolves around their anecdotal experiences? Previous versions of Ubuntu screwed up on me all the time. I used to complain about Webcam access crashing the system without a message. I couldn't install 7.04 and never could find a reason why. Hardy has been running on my machine just fine, installed wonderfully, picked up all my hardware. I'm ecstatic.

> The one thing Linux must do is NOT lock up randomly. That's it. When it does that, it's failed in doing what it's meant to do.[QUOTE]

Not lock up randomly? I'm sorry, but my OS has a higher purpose than that, but I get your point.

[QUOTE]may also have a paperweight sitting on their desk -- well, don't expect a very large userbase in, say, two years.

No new user will have a paperweight on their desk. Even an idiot knows that if they try something new, and it doesn't work, continue with what you were doing until you find a something new that does work. People aren't saying "Oh, your bad experience scares newbies". They are saying "Your blatant misrepresentation scares newbies".

1. The entire world is not having a problem. A subset of users are having an issue.
2. Your anecdotal experiences with previous releases don't pertain to everyone elses experiences.
3. Installing Hardy Heron will not destroy your computer and turn it into only a paperweight.

I mean, seriously.. what are you expecting to accomplish by posting illogical statements and griping about the userbase? I'm sure that the problems are being worked on right now, if you don't have a workaround or the workarounds don't work for you -- SORRY! Downgrade. You _do_ have that choice don't you?

---

### Post by karellen on 2008-04-29
hm..about this > 1. The entire world is not having a problem. A subset of users are having an issue.
the entire world is not using Linux, not mentioning Ubuntu. a subset of users are using it ;)
so yes, every single experience - be it good or bad - matters and it shouldn't be treated as anecdotal

---

### Post by karellen on 2008-04-29
about this...
> 1. The entire world is not having a problem. A subset of users are having an issue.
the entire world is not using Linux. a subset of users are using it ;)
so yes, every single experience - be it good or bad - matters and it shouldn't be labeled as anecdotal

---

### Post by karellen on 2008-04-29
silly me, my first double post...

---

### Post by vinsenjunior on 2008-04-29
I installed Hardy and had quite some problems. Well...it's hard(y). I believe this is a kernel issue. A little dissapointed, but I don't think I will stop using Ubuntu. Of all distros I tried, so far Ubuntu is the one for me.  

Right now I already downgraded to Gutsy and all is good (the only itch is that -i'm not using the latest/coolest Ubuntu- thing :p)

I will keep using Gutsy until there is an official stable kernel release. I'm sure the Ubuntu team is busy as hell right now, so I'll cheer for them :popcorn:

Ubuntu rocks! :guitar:

---

### Post by MangasColoradas on 2008-04-29
> Linux kernel 2.6.24-12 lockup

But Hardy is 2.6.24-16?

---

### Post by beamo on 2008-04-29
I'd have to say, from my experience so far, that Hardy is great. The only drawback is firefox 3.0 which doesn't allow all the extensions I normally use. It wasn't a big deal to completely remove it and go back to firefox-2.

The other problem, and this has been a problem with every release, is the suspend function. It only works once per reboot. Kind of annoying.

I first tried Ubuntu with Hoary Hedgehog and it wasn't very usable. I switched over full time with 6.06 and have been delighted to see the huge strides since then. 

Great job to all who work on this.

---

### Post by rmfought on 2008-04-29
I just experienced my first hard freeze on my behemoth desktop.  The mouse still moves, but the desktop is completely unresponsive.  I can't decide whether to be happy or dismayed that others are experiencing the same issue.  I have installed Hardy Heron on three machines, an Acer Ferrari 4000 laptop, a fairly recent home-built desktop (the one that froze), and a 4-5 years old homebuilt desktop.  Aside from the beta of Firefox 3 and it being seemingly more difficult to setup Samba and NFS shares, I was pleased with Hardy until this happened.  I never had any sort of issue like this with Fiesty or Gutsy.  It especially ticks me off since the lock-up occurred while I was working and I probably have lost some work.

My specs:
Asus M2N32 Mobo
AMD X2 5200
2 GB Corsair RAM
ATI X1950XTX
SB X-Fi
250/500 GB SATA drives

Nothing special installed except the ATI restricted driver.  Was running OpenOffice Writer, Meld, a terminal and a file browser at the time.

Time to file a report ...

UPDATE
Well, it just happened on my Acer laptop as well, right as I was trying to send an important e-mail, which now I am sure is lost.  So 2 out of 3 of my machines have frozen solid.  This is not good.

---

### Post by bilal.17 on 2008-04-29
I now had a first freeze on my desktop, previously it only occured on my laptop. Hopefully it was just a one  time thing and wont happen again, but this issue needs to be resolved and probably will be. Just give the devs some time.

---

### Post by Delever on 2008-04-29
I thought it won't happen for me, but it did yesterday three times. After uninstalling everything possible evolution-related (avoiding to remove ubuntu-desktop), and turning Compiz BACK ON, problem seems to be gone (knock knock)

---

### Post by zdude on 2008-04-29
I had posted earlier about having bad problems with Hardy, well I tried a clean install with a newly burnt image and all seems to be working ok at this point, outside of me rebuilding my desktop and apps I had installed (oh, joy!). Hardy actually recognized my wireless (rt73) which is cool. I used to use serialmonkeys version. Also the audio card is recognized, that used to be loaded from the backports. I haven't really worked it hard yet but all seems to be pretty good. The suspend option still is broken on my machine and it used to work perfectly under Feisty but I guess that's progress. So for now I am eating my words from earlier. Looks like a pretty good job done by the developers.:guitar:

---

### Post by wolfen69 on 2008-04-29
> **Jim March said:**
> What I figured.  OK.  I'm going to stick with .24-rt for a bit, see if that makes a diff.  For my own purposes I have no problem compiling .25 but I have to be concerned about customer systems and I'd rather not go custom-kernel there.

i dont think it's going to be a problem on every single computer. relax.

as far as these "hardy sucks" threads go,(not this one) people need to get a grip and rephrase things: "hardy sucks for **me**" "it wont work on **my** computer". then again, these people probably complain about everything in their life.

---

### Post by geco on 2008-04-29
I'm another unhappy Hardy "former"-user... after a totally fresh install (with hard drive partitioning) from the alternate-CD Hardy started to freeze whenever I logged in GNOME. Only the mouse pointer moved, but neither the keyboard or the touchpad buttons responded. I discovered that it was the open source ati driver who gave problems (no freezes with the standard vesa driver). but I was so upset that I decided to install Debian testing. I'll stay with Debian untill I'll have good news from Hardy, then I'll decide what to do.

---

### Post by lfaraone on 2008-04-29
I have upgraded an entire lab of computers (26) that are pounded on every day by students, and have had no issues whatsoever.

YMMV.

---

### Post by Delever on 2008-04-29
It DOES happen.

Get over it :)

---

### Post by nick2000 on 2008-04-29
I have upgraded 3 7.10 PCs to 8.04. All 3 went bad in a different way.

* One cannot detect the video card type for some reason. It was fine under 7.10, now I can only get it to work by using failsafe gnome session...
* Another one cannot use the Nvidia restricted drivers while that worked just fine under 7.10. SO... no google-earth
* The last one and most problematic hard-freeze regularly. I used to have some lockups twice a month under 7.10 where the mouse would move but no keys or clicks got through, but this one is a hard-freeze (reset button time) pretty much every 2 hours or less. How do I downgrade back to 7.10 easily?

---

### Post by Bungo Pony on 2008-04-29
I'm a happy upgrader! It's stable as a rock without any glitches. But I installed UbuntuStudio... doesn't that use a special lowlatency kernel?

---

### Post by tact on 2008-04-30
> **karellen said:**
> I've said it before and I'll say it again: there is absolutely no excuse for something that worked in a previous version of Ubuntu and in Hardy it doesn't.

Please remind yourself that part of progress means sometimes knocking down structures and rebuilding.

Part of that progress in ubuntu has been the replacing of entire subsystems (like the sound server - pulse audio) and so it is MORE than possible (and to me - acceptable as part of progress) that for some people, unlucky people, the new may not work on their hardware where the older version did.

You say absolutely no excuse for something that worked in a previous release to not work in Hardy.  

I say - no excuse needed.  

Face it.  

There is a LOT in Hardy that is new.  Not just talking about new tweaks or incremental feature adds in applications or systems.  I am talking about entirely NEW entire subsystems.

For me, and my hardware, no problem.  Everything works faster, better, and many things (like suspend resume that never worked before) are working now.

For other people, on their hardware - perhaps a different story.   Sad but there WILL be some unlucky people who were able to run Feisty/Gutsy but find that Hardy will not run on their hardware.

And I do NOT see that as anything but PROGRESS.  Sad some were unlucky.  But for the majority its just fine.  Given time perhaps even the (introduced) issues for that unlucky lot will also be worked out.

I will say this now for the first time here - there is NO EXCUSE for you to to demand that EVERYTHING that worked (on you hardware) in past versions must ALWAYS work in future versions.  

There will ALWAYS be the possibility that a BETTER new ubuntu component will not work for some people who had no problem with the OLDER component.

Thats progress.  Breaking eggs to make omelettes

Cheers.

---

### Post by MONODA on 2008-04-30
Please remind yourself that part of progress means sometimes knocking down structures and rebuilding.
 
 Part of that progress in ubuntu has been the replacing of entire subsystems (like the sound server - pulse audio) and so it is MORE than possible (and to me - acceptable as part of progress) that for some people, unlucky people, the new may not work on their hardware where the older version did.
 
 You say absolutely no excuse for something that worked in a previous release to not work in Hardy. 
 
 I say - no excuse needed. 
 
 Face it. 
 
 There is a LOT in Hardy that is new. Not just talking about new tweaks or incremental feature adds in applications or systems. I am talking about entirely NEW entire subsystems.
 
 For me, and my hardware, no problem. Everything works faster, better, and many things (like suspend resume that never worked before) are working now.
 
 For other people, on their hardware - perhaps a different story. Sad but there WILL be some unlucky people who were able to run Feisty/Gutsy but find that Hardy will not run on their hardware.
 
 And I do NOT see that as anything but PROGRESS. Sad some were unlucky. But for the majority its just fine. Given time perhaps even the (introduced) issues for that unlucky lot will also be worked out.
 
 I will say this now for the first time here - there is NO EXCUSE for you to to demand that EVERYTHING that worked (on you hardware) in past versions must ALWAYS work in future versions. 
 
 There will ALWAYS be the possibility that a BETTER new ubuntu component will not work for some people who had no problem with the OLDER component.
 
 Thats progress. Breaking eggs to make omelettes
 
 Cheers.> 
yes you are right, but this only applies in some cases and not in software development since it can be easily avoided. Instead of only having 6 months to include bug fixes and such, the ubuntu team has to kind of rush. If ubuntu was a rolling release distribution then time could be taken to make sure that the features implemented are rock solid. Also, ubuntu includes a lot of alpha a beta software. for example, compiz fusion is still alpha and causes many lockups and other problems. another example is ff3, it is the default browser but is unstable and a cpu hog, epiphany should have been the default broswer with ff3 and ff2 in the repos. Another reason why features are rushed is because if a new version of software is released (eg ff3) but is still not stable, then it has to be included in the repos since it cannot support the older version and have no support for the new. This would be avoided if ubuntu was rolling release.

ARCH FTW XD

---

### Post by tact on 2008-04-30
> **MONODA said:**
> Cheers.yes you are right, but this only applies in some cases and not in software development since it can be easily avoided.
[...]
If ubuntu was a rolling release distribution then time could be taken to make sure that the features implemented are rock solid.


It really comes down to this:
Hardy IS "rock solid"....   on my system.  That includes compiz, ff3 and other stuff you speak of as unstable.  I find them rock solid.

Whats that you say?  That is only my subjective assessment?  Only my subjective experience?

You are right.  There are others who find that (on their systems) Hardy is not rock solid.  So my experience is just my experience.

Here is the rub - for those who have problems their experience is also purely their subjective experience.

Hardy is solid (for some)
Hardy is not solid (for some)

So who is right?  How can the devs be criticised for not making sure Hardy is rock solid?  It is rock solid many would say.

So where is the problem?   It is "...on my hardware" hardy is either rock solid of not rock solid.

As I pointed out in my post..  huge chunks of serious subsystems were replaced in the change from Gutsy to Hardy.   

You MUST expect that some hardware that previously worked with feisty/gutsy may not work with the new bits in hardy.   And... conversely there may well be (definitely is, my experience) some hardware that previously never worked with feisty/gutsy that will work under hardy.

Its NOT a function of the devs working harder to ensure the development is rock solid (it IS rock solid to many...remember).

It is a function that with DIFFERENT software components employed there will be a shift in the hardware that is (or is now not) supported.

---

### Post by MONODA on 2008-04-30
It does not make sense to sacrafice compatibility with many PCs which worked perfectly before to implement features that aren't needed immediately. If time was taken to properly make major changes then these problems would not exist. This fast implement of half baked features will be the death of ubuntu for sure.

---

### Post by park8b156 on 2008-04-30
Works fine for my Acer Aspire 5100 laptop.  Just can't get total function from gnome art manager or emerald but compiz and awn work??????

---

### Post by Mr.Andersson on 2008-04-30
I've been running Hardy since beta 3 and now the stable release, with only one problem. When switching user in the upper panel, X just hangs.

Otherwise, it works perfectly good!

---

### Post by tact on 2008-04-30
> **MONODA said:**
> It does not make sense to sacrafice compatibility with many PCs which worked perfectly before to implement features that aren't needed immediately. If time was taken to properly make major changes then these problems would not exist. This fast implement of half baked features will be the death of ubuntu for sure.

I strongly disagree on two counts:
1.  go for it ubuntu..  be cutting edge.. make the leaps of faith into new/better technologies, and do it as WELL as you do making it as GOOD as you do for those with supported hardware - because after all the minority who find that compatibility with their hardware is sacrificed can still use what did work for them - Gutsy et al

For the happy rest of us - enjoy the ride, its exciting and we have a dynamic and pack leading QUALITY distro.

2.  "if time were taken to properly make changes" - hardware issues are hardware issues.  No amount of time can make incompatible hardware compatible.  Some amount of time may improve the situation in borderline cases.  

As I mentioned - Give it time and maybe some of the incompatibilities or problems some people have with hardy may be solved or workarounds sorted.

In the meantime, people with hardware that worked well with feisty/gutsy but not with hardy need not scream from atop soapboxes that hardy is the worst release and the devs got it all wrong and we should have slower release cycles etc.

Hardy IS rock solid...  (For so many people on their hardware).   I wish those screaming "hardy is the worst/unstable..." would wake up and realise this truth.  Perhaps then they will realise how silly they look and change behaviour.

True - Hardy is not rock solid (For a minority of people on their hardware).  Let them report bugs, work with devs to solve them and stop deceiving themselves and others by taking to soapboxes screaming "Hardy is the worst...."


One more time:
Hardy IS rock solid - ON MY HARDWARE.  Myself, and people with like experiences, are NOT uber-defensive "hardy boy bullies" just trying to silence any nay-sayers.  So do not ignore our experience/comments.  

Its a fact... for a huge number of people hardy is a case of "good, better, best".  Rock solid stable... ON THEIR SYSTEMS.

In THAT light..  with THAT knowledge...  those who are pissed that hardy does not work well ON THEIR SYSTEMS (and if I were in that group I'd be pissed too)...  if they want to scream something and have half a brain - they wont be screaming that "hardy is the worst...unstable release and here is why (devs, release schedules. etc)."

...because that is patently not correct.

If I were part of that group who are having problems that were not present in feisty/gutsy, yes I'd be pissed too, but I'd be embarrassed to go around saying "hardy is unstable".   I'd be saying "ON MY SYSTEM..." and doing whatever I can to assist.  And if there is no resolution - fall back to Gutsy.


:)   Cheers

---

### Post by MONODA on 2008-04-30
> because after all the minority who find that compatibility with their hardware is sacrificed can still use what did work for them - Gutsy et al yes but then they cannot get upgrades to packages anyway, people experiencing problems should not be left out in the cold(eg. in feisty, pidgin is still gaim)
>  hardware issues are hardware issues
but these are not hardware issues, these issues are caused by alpha and beta software (compiz is alpha and ff3 is beta, both of which are very important to the OS. Including compiz as the default wm was a terrible idea. I am sure that these are not the only ones)
> If I were part of that group who are having problems that were not present in feisty/gutsy, yes I'd be pissed too, but I'd be embarrassed to go around saying "hardy is unstable". I'd be saying "ON MY SYSTEM..." and doing whatever I can to assist. And if there is no resolution - fall back to Gutsy.
but it is unstable. the hardware does not matter, its the halfbaked software that is included by default that is what makes it unstable. (alpha & beta software included in a OS = OS is unstable)
NOTE: I do not agree with the OP that hardy is the worst release ever etc. but I am just saying that ubuntu needs to revaluate the update cycle/method and needs to check to make sure that they do not brake many things (including features will always brake things) when implementing features.
P.S. maybe I am wrong and like stability too much, I guess Debian is for me then ;)

---

### Post by mudenza on 2008-04-30
I should have stayed with 7.10, now instead I've got my harddrive clawing away at a snail's pace as everything has just been given extra weight. I've got 700+ Ram, and I've never have experienced such slowdown before with Ubuntu. I'm keeping my hat on, thanks.

---

### Post by tact on 2008-04-30
> **MONODA said:**
> yes but then they cannot get upgrades to packages anyway, people experiencing problems should not be left out in the cold(eg. in feisty, pidgin is still gaim)


Isnt pidgin unstable?  Gaim more mature and stable?  *tongue in cheek*

Look up the termination of support dates for feisty and gutsy.  You may be pleased.   Updates will come for a while yet.

> **MONODA said:**
> 
but these are not hardware issues,


Says you?  Are you totally ignoring me and all I say and all others say about hardy working well, stable, rock solid, on their hardware?  (on their what?  Hardware).

> **MONODA said:**
>  these issues are caused by alpha and beta software (compiz is alpha and ff3 is beta, both of which are very important to the OS. Including compiz as the default wm was a terrible idea. I am sure that these are not the only ones)


Says who?  Your experience, ignoring people like me who find even with these alpha/beta software releases included - hardy is stable?

All the above software are totally rock solid stable on my system under hardy.  I could write REAMS about how I heavily I use my laptop and how crucial it is to be stable and available to me for about 12hrs a day...  and how I dared to install the hardy beta on it and how it was totally stable for me right thru to release and on to this date.

I do carry with me the assumption that there is a chance that some core part of hardy may be replaced in Irate Ibis leaving me stranded, unable to use Irascribable Ibis, if that new core part is will not play well with my hardware (which - if you have not heard me still... is amazingly stable with hardy).

> **MONODA said:**
> 
but it is unstable. 

No its not.

We could go all day.  But lets not.  

I hope you can finally one day realise that there are many many people like me who find hardy and all the systems and software with it - STABLE.  Rock Solid.  :)  

Its
TRUE
We
Do EXIST

> **MONODA said:**
> the hardware does not matter, 


Says you?  I say hardware does matter and that its more than conceivable that people who found gutsy stable will find hardy unstable - on their hardware..  their what?  Hardware.

> **MONODA said:**
> its the halfbaked software that is included by default that is what makes it unstable. (alpha & beta software included in a OS = OS is unstable)


Again - sorry if this is sounding monotonous..  that even with all the alpha/beta applications included...  I, and many like me, find that hardy is....
stable
rock solid
good better best...

When will you accept that i am not bluffing you here... and I am not a facist hardy bully boy trying to silence anyone, or carrying any other agenda that may give you cause to speed read over what I (we) are saying when we(I) say we find ...hardy ...is... stable.  Best release yet.

> **MONODA said:**
> 
NOTE: I do not agree with the OP that hardy is the worst release ever etc. but I am just saying that ubuntu needs to revaluate the update cycle/method and needs to check to make sure that they do not brake many things (including features will always brake things) when implementing features.
P.S. maybe I am wrong and like stability too much, I guess Debian is for me then ;)

Debian is for you?  hehehe fine but isn't that akin to my suggestion that those with problems with hardy stay with feisty/gutsy?  :)

Yep...  I am acknowledge that in your writing you are adressing things from a slightly different angle.  A much saner angle than the OP.  Nonetheless I disagree with you.  :)

I do see your point.  And to a degree I do agree with you.  I absolutely agree with the principle that care should be taken to not release versions with showstoppers.

If EVERYONE was having the same problems as the OP. Or even a majority of people....  then I would be saying "this sucks, hardy is a bomb and the devs are careless to release such rubbish"

But that is NOT the case here.  Not at all.  

I believe that those who have those recurring whole system random lockups that they cannot trace back to any single point (like ff3, gvfs, compiz,  pulse etc) like the OP and a few others are experiencing - are facing this:
- hardy has problems on "their hardware".
- that they can run feisty/gutsy with no problems means nothing because hardy is a very different creature with whole masses of critical subsystems replaced with new software totally unlike what was packaged with feisty/gutsy ergo...
- the assertion that "feisty/gutsy runs well on my hardware but hardy doesn't so the problem is hardy not my hardware" - is not at all sane or logical.
-  what is sane/logical is that their hardware ran feisty/gutsy well.  It does not run different software (hardy) well.  Therefore there are things in their hardware that is not well tolerated by the new inclusions in hardy.  Hardware problem.
-  they have (sadly) found themselves in the "not completely supported hardware" set with hardy.  Whereas with a different beast, feisty/gutsy, they were in the happy "supported hardware" set.

(of course I am not saying that hardy is perfect and that there are no bugs at all.  just that there are no showstoppers that justify the way the OP is carrying on or justifying any assertion that "hardy is inherently unstable".   It may be unstable on certain... hardware.  It is CERTAINLY stable on what i perceive to be a vast majority of ...hardware)

---

### Post by SupaSonic on 2008-04-30
It's just weird that Ubuntu LTS(!) would ship with Firefox Beta and pulseaudio. I mean cutting edge is fine for feisty, for gutsy, but I'd think the devs would be a bit more on the conservative side with Hardy. As it stands, I'm glad for everyone who's having no issues with the new release, I just feel really upset that I'm not one of them.

---

### Post by MONODA on 2008-04-30
> hehehe fine but isn't that akin to my suggestion that those with problems with hardy stay with feisty/gutsy?
there are huge differences between debian and previous versions of ubuntu.

> Isnt pidgin unstable? Gaim more mature and stable? *tongue in cheek*

 Look up the termination of support dates for feisty and gutsy. You may be pleased. Updates will come for a while yet.
no pidgin is more stable, GAIM is beta, not 1.0 yet and pidgin is not beta. updates to packages will come yes but upgrades will no (eg. OO.o in gutsy will not upgrade to 2.4.)

Hardy can be called unstable b/c almost on 1/4 systems it will not work properly. an upgrade should add support for more hardware and keep support for previously supported hardware. the fact that the word hardware is in the phrase, "It works well on my hardware" does not mean that problems others are having are hardware related, especially when the hardware was previously supported. Hardy is filled with pre-final software and is incompatible with previously compatible hardware meaning that it is unstable and should still be considered beta.

EDIT: I am not trying to convince anyone that gutsy is better and hardy sucks, use what you like. I just wanted to clear that up

---

### Post by MONODA on 2008-04-30
just curious, what do ubuntu devs think of hardy?

---

### Post by Delever on 2008-04-30
I believe they are hunting it down. After all, lockup bug is one of the worst bugs ever (and please, smarties, don't deny it exists). Damn, I would dive deep to review every bit of possible code, because I *want* ubuntu to be stable on *every* system. That is the goal.

---

### Post by NotTheMessiah on 2008-04-30
I am experiencing regular lock ups on two different machines(lappy centrino,and desktopAMD64).I was running feisty on my laptop previosly and it was rock solid. Gutsy on my desktop and it was definitely locking up. But Hardy is locking up like it's going out of fashion.

---

### Post by enchantedsky on 2008-04-30
> **Jim March said:**
> Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

A bug has been issued to the kernel team, priority high, marked "triaged":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

Today I did a fresh install from the release CD, standard 32bit, Intel945 video, Atheros WiFi, all standard parts on an Acer laptop that handled Feisty and Gutsy like a champ.  No overheating.  1.5gigs RAM, swap stats show zero use so it's not corrupted swap.

I don't think the devs are going to be able to fix this one easily.  There's just NO feedback or debugging info possible.  When Fedora 9 releases I may be forced to abandon ship.

This really sucks.

My experience is the exact OPPOSITE. Hardy Heron has actually solved many of my lockup problems.

I have had so many CPU lockups with Ubuntu 7.10 Gutsy Gibbon 64-bit, and doing a fresh install with 8.04 has actually solved many of my problems. I have a Dell C521 with a AMD X2 processor

To each, their own. But do not generalize and speak for other people saying Hardy Heron sucks ---- when you are only speaking about your own experiences (and a minority of other people!)

---

### Post by NotTheMessiah on 2008-04-30
> **enchantedsky said:**
> (and a minority of other people!)

Yeah...it kind of sucks when you belong to a 'minority of other people'.
I guess we are not that important...as long as the majority of people do not experience lockups.

---

### Post by kaylus on 2008-04-30
> I believe they are hunting it down. After all, lockup bug is one of the worst bugs ever (and please, smarties, don't deny it exists). Damn, I would dive deep to review every bit of possible code, because I *want* ubuntu to be stable on *every* system. That is the goal.

That, besides the jab in the center, was one of the more intelligent responses I've seen in this thread. To the previous that told me not to use the word "Anecdotal", I have this to say:

It is anecdotal, the people are talking about their personal experiences that we cannot verify. Even the positive experiences are anecdotal, it's not a cutdown. **Think: If this bug was so prevalent, it would have been noticed alot earlier and affected more people in the slew of pre-releases.** If you read the bug descriptions prior to 04-16-08 there were only a couple people who reported it out of all who tested the releases.

Read some of the accounts "Hardy is unstable, it doesn't work on 1/4 the machines". To give a different account: After starting with the RC and finding it extremely stable for me, I've had it installed on a large amount of machines Dell laptops, IBM Laptops, Dell Desktops, HP Desktops and custom builds. I also have three server releases running stable with an uptime since the release of Hardy. 

Saying 1/4 the machines that run Hardy is not scientifically verifiable, yes there is a problem with Hardy. It is being worked on. All we have now are anecdotal accounts where people are trying to get their point across in messages and using extremisms to do so "All my computers are paperweights now!" -- give me a break.

I want Ubuntu to be stable for everyone as the above poster said, but I also agree with another previous poster: Ubuntu Hardy Heron is rock solid on every installation I am using it on. I've got it loaded on more machines then the amount of people who've posted negative in this thread. 

It doesn't discount your problems, but I'm letting you know that because you have problems it doesn't discount the many many many of us who are not having issues, so extreme examples (like telling people if they install it their computers will be paperweights) are uncalled for.

I hope we get this bug zapped fast! I want all of you guys to enjoy this release as much as I have.

Kaylus

---

### Post by tact on 2008-04-30
> **SupaSonic said:**
> It's just weird that Ubuntu LTS(!) would ship with Firefox Beta and pulseaudio. I mean cutting edge is fine for feisty, for gutsy, but I'd think the devs would be a bit more on the conservative side with Hardy. As it stands, I'm glad for everyone who's having no issues with the new release, I just feel really upset that I'm not one of them.

Totally agree with you being "really upset" that you are not one of those who has no issues with Hardy and find it (including ff beta and pulseaudio) to be stable.

I do feel for those with hardy problems.  And I do support the "feel upset it doesn't work better than gutsy for me" feelings that those with hardy issues may feel.  I admitted 2 or 3 times in past posts in this thread that if I were amongst the number of people who are having issues with hardy I'd certainly be upset. :)

But... knowing that there are a LOT of people out there who do not have problems with hardy, even ecstatically proclaiming it truly is the best release yet...  I'd be thinking very hard before proclaiming as the OP has that hardy is the worst... and its unstable.  (period).  THAT kind of person gets no sympathy from me at all and no interest to assist even if I could.

---

### Post by uweklosa on 2008-04-30
Hi

I think Hardy is a really good release. I have installed it on three different notebooks, three different desktops and two servers. All systems are stable and run faster then with gutsy. The hardware recognition has improved much. The two systems with AMD CPUs have no lockups anymore. The only problem I have are crashes of firefox with flash. It's annoying but it's not worth being angry about it.

I'm really happy with the Hardy release.

Uwe

---

### Post by ubuntu-freak on 2008-04-30
Hard-lock crashes are always graphics device driver related. If you installed the driver using the RDM, disable it and try Envy instead. 
 
Nathan

---

### Post by tact on 2008-04-30
> **NotTheMessiah said:**
> Yeah...it kind of sucks when you belong to a 'minority of other people'.
I guess we are not that important...as long as the majority of people do not experience lockups.

"You can't please everyone" 

There has always been two pools... 
- the big one full of happy campers who have hardware that is supported for some time.
- the substantially smaller pool where the unhappy campers with hardware that is less easily supported wade and wallow

Whilst the big pool gets bigger and the small pool gets smaller we all know that the small pool will never go away completely.  "You can't please everyone"

We all have that primal expectation that the flow of people will always only be from the small pool to the bigger pool and that these migrants will have smiles on their faces.  Their hardware now supported after all this time.

What we dont expect, and get pretty steamed about, is if there is some shift in the landscape such that the boundary line between the big and small pools gets shifted and some of the previously happy big pool campers end up in the small pool though they themselves didn't move, the line was shifted without their approval or agreement.  

Hardy has changed the landscape in a lot of big ways.  Whole new sound system, policy kit, gvfs, CFS, and so much more.

As such one has to expect that there may well be a number of people who previously had no issues (with feisty/gutsy) who find themselves having issues now with all the new stuff in hardy.  Unfortunate as that may be it can happen.

When I first installed hardy beta on my laptop I was a little nervous wondering if all the new stuff in hardy would work as well on my hardware as the older feisty/gutsy.   i.e. I specifically wondered things like "...ALSA worked fine, would pulseaudio work better or cause me grief!?"

Happily, for me on my hardware... pulseaudio, for example, works brilliantly.  Goodbye ALSA.

Had I found myself getting lots of unexplained and random lockups that seemingly defy logging and evade all attempts to isolate - I'd be pissed but be thinking... well I cannot run these new systems - on my hardware.

I'd not be on a soapbox screaming that hardy is the worst release yet ignoring the many with opposite findings.

Cheers.

---

### Post by bigbrovar on 2008-04-30
Yet another Lockup :confused:  .. i dont know i am sooo exhausted.. no OS should act like this .. I finally Give up for the first time since using Ubuntu i would be Downgrading  :( .. really hope the issue is fixed though so that i can come back soonest ..

---

### Post by plun on 2008-04-30
> **bigbrovar said:**
> Yet another Lockup :confused:  .. i dont know i am sooo exhausted.. no OS should act like this .. I finally Give up for the first time since using Ubuntu i would be Downgrading  :( .. really hope the issue is fixed though so that i can come back soonest ..

Well, this is known issues and can you please test if it is Firefox.

[https://bugs.launchpad.net/firefox/+bug/215728](https://bugs.launchpad.net/firefox/+bug/215728)

> Workaround was successful (disabling phishing/attack detection, closing Firefox, deleting ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite , opening Firefox).


Ubuntus team leader for Mozilla was more interested in Epiphany....:(

---

### Post by bigbrovar on 2008-04-30
> Well, this is known issues and can you please test if it is Firefox.

[https://bugs.launchpad.net/firefox/+bug/215728](https://bugs.launchpad.net/firefox/+bug/215728)

Quote:
Workaround was successful (disabling phishing/attack detection, closing Firefox, deleting ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite , opening Firefox). 
Thanks but i dont think its just about Firefox.. i have tried FF2 ,opera,epipahny,.. but its all the same .. although i must admit the chances are higher when am on FF3 and opera ... i finally gaveup when i experienced it again when while i was using seamonkey.. the lockup thing could have sumtin to do with wireless .. oh i dont know .. but am back to god ol solid as ever gutsy .. hopefully the bug will be fix then I WILL BE BACK

---

### Post by NotTheMessiah on 2008-04-30
> **tact said:**
> "You can't please everyone" 

There has always been two pools... 
- the big one full of happy campers who have hardware that is supported for some time.
- the substantially smaller pool where the unhappy campers with hardware that is less easily supported wade and wallow


That same logic can be used when we talk about(trash) Microsoft products."Can't please everyone"

 I thank you that you miraculously diagnosed my problems as hardware related for both laptop and desktop. I never said anything about worst/best operating system but i think that it is necessary to report problems such as these. We are not going to turn into mac users which used to be very silent and pretended there were no problems with mac products. I refuse to do that. And if the OP want's to declare Hardy the worst OS ever, he is entitled to do so and it will only be his personal opinion just like the people that declare Vista the best OS ever.

---

### Post by kaylus on 2008-04-30
> **NotTheMessiah said:**
> That same logic can be used when we talk about(trash) Microsoft products."Can't please everyone"

 I thank you that you miraculously diagnosed my problems as hardware related for both laptop and desktop.

So what are you saying? That the software is only broke on random computers? I'm sorry to tell you this, sir, but if software is poorly written so that it is buggy then it will be buggy irregardless -- If problems are occuring on only a small sampling of machines then it likely is not a software problem.

Remember back to helpdesk 101. If everyone else is successful in getting the software to run then it is likely either:

1) You need to reboot.
2) You have configured the software wrong, try again
3) You need to clear your cache.
4) You have a hardware problem

Since you probably didn't configure the software at all (esp. in the case of a fresh load) the answer is most likely #4.


> We are not going to turn into mac users which used to be very silent and pretended there were no problems with mac products. I refuse to do that.

You probably weren't part of the same Mac community I was part of during the System 7 days. Quite vocal as I recall. If you are referring to before THAT time, then I'd have to say most users on most OS's were about the same Vocal in those days. But we were too busy arguing about the true meaning of multi-tasking vs. multi-processing.

> that declare Vista the best OS ever.

Not to stray too far from topic, but I always found uber-elitism unfounded. Every tool has it's Job. Did you know that our Oracle Application servers with an enterprise java application run faster and with more stability on Windows Servers than Solaris or Linux? Ouch. You don't ignore that with elitism, but notice and try to correct.

Of course, Oracle has always been chincy in my opinion. And it might fall into rule #2 of the helpdesk software above. We might just not know how to configure it to potential - hur hur.

Kaylus

---

### Post by Saint Angeles on 2008-04-30
> **NotTheMessiah said:**
> Yeah...it kind of sucks when you belong to a 'minority of other people'.
I guess we are not that important...as long as the majority of people do not experience lockups.
naw, you're just as important.

but not important enough to change everything about hardy. file a bug report and it will help the devs fix the problems.

hardy will continue to be updated as these bugs get fixed. does anybody here remember how absolutely horrific winXP was when it first came out? thats why when you do a fresh install, you need about a hundred updates from windows update. (and it takes a hell of a long time and a dozen restarts).

---

### Post by Geekkit on 2008-05-01
Thanks Jim for posting this. I'll avoid Hardy for a few months until they (the devs) fumigate. Last show stopping kernel lockup I had problems with was 6.10 where my mobile phone connection (via USB) would lock the kernel up 100% of the time.

---

### Post by tact on 2008-05-01
> **NotTheMessiah said:**
> That same logic can be used when we talk about(trash) Microsoft products."Can't please everyone"


Agreed.  It works/applies to trash as much as quality products.  

> **NotTheMessiah said:**
> 
 I thank you that you miraculously diagnosed my problems as hardware related for both laptop and desktop. 


You are more than welcome.  Best of luck.

> **NotTheMessiah said:**
> 
I never said anything about worst/best operating system 


Agreed.  I was referring to the OP and the those who DO say so when I made any comment in that regards.  Sorry if that wasn't clear and you though I was accusing you of such behaviour.

> **NotTheMessiah said:**
> 
but i think that it is necessary to report problems such as these. We are not going to turn into mac users which used to be very silent and pretended there were no problems with mac products. I refuse to do that. 

I have never asked people to be silent and not report matters.  I have the highest praise for those who are not silent and report matters.  I encourage this highly.

I have the utmost disrespect for those who disregard that hardy is rock solid stable for very many people, yet still persist to post in multiple threads declarations and "warnings" that "hardy is the worst...  hardy IS unstable".   <----- notice the period.

"hardy is the worst".   Not a true statement.  A lie if one knows that a vast majority find hardy stable and the best release yet.

"hardy is unstable".   Not a true statement.  A lie if one knows that a vast majority find hardy stable and the best release yet.

"Hardy is unstable on my system - I get random lockups".  This may well be a true and sincere statement.  No misleading.  No lie.

See the difference?  THIS difference is all I am pointing to in all my posts on the matter.  Its an important difference.

When you KNOW that there are a majority of users who are finding hardy is rock solid stable... how can one say "hardy is unstable".  <---note the period.

At best one can say "hardy is unstable [no period] on my system..." perhaps adding "...don't know why, cannot find the cause.. tried all these things... logged reports..  "   etc.


> **NotTheMessiah said:**
> 
And if the OP want's to declare Hardy the worst OS ever, he is entitled to do so and it will only be his personal opinion just like the people that declare Vista the best OS ever.

At last we disagree.   I think the OP has no right to air such trash and consider it a misuse of these forums, and a misuse his ability to communicate.  Spreading deliberate mis-information is a no-no in the world i live in.

And make no mistake - writing " Hardy is BY FAR the worst Ubuntu version yet. LOCKUP WARNING!!!" whilst KNOWING that this is not the case for a vast majority of hardy users - IS spreading mis-information.

Notice the effect of it on geekkit from his post (below)
> **Geekkit said:**
> 
Thanks Jim for posting this. I'll avoid Hardy for a few months until they (the devs) fumigate. Last show stopping kernel lockup I had problems with was 6.10 where my mobile phone connection (via USB) would lock the kernel up 100% of the time.


Its a bit sad isn't it?  When someone (OP) acts irresponsibly with their comments, exaggerates wildly, and causes someone who has never tried, and thus can never know whether his hardware will run hardy well or not, to turn their backs on what may be the best ubuntu experience they have ever had - Hardy. (as testified to by the many of the majority who find hardy to be the best release ever).

Not to mention the effect unseen it has on silent readers who perhaps have been thinking of trying ubuntu and after reading this thread title decide to give it a miss totally.

---

### Post by tact on 2008-05-01
> **kaylus said:**
> So what are you saying? That the software is only broke on random computers? I'm sorry to tell you this, sir, but if software is poorly written so that it is buggy then it will be buggy irregardless -- If problems are occuring on only a small sampling of machines then it likely is not a software problem.


Well said, kaylus.  

Let me add too that when problems occur on a small sampling of machines the fix may not be a "bug fix" at all.  (emphasis on the work "may" please)  There may be not be a software "bug" as such causing all those lockups on certain machines.

There also may be no problem with the hardware per se.  (It works under feisty/gutsy).   

So if its not a software bug as such AND there is nothing wrong with the hardware as such...then whats the problem?  

You all know the answer.  Think it over.  hehehe.

Cheers.

(clue:  "Hardware issue/problem" does not equal "broken hardware")

---

### Post by tact on 2008-05-01
> **Geekkit said:**
> Thanks Jim for posting this. I'll avoid Hardy for a few months until they (the devs) fumigate. Last show stopping kernel lockup I had problems with was 6.10 where my mobile phone connection (via USB) would lock the kernel up 100% of the time.

Take the time to dl, burn and boot from a liveCD of hardy if you are afraid that the problems jim march highlights may affect your PC.

jim's experience is NOT universal by ANY means.

Cheers

---

### Post by Tom Mann on 2008-05-01
Hmmm... I've installed Hardy on 4 different PC's - none have had this problem. I had a problem in the Beta stages with lockups however. I managed to get around it with an apt-get update from the command line in single user mode, but as of it's final release I've had no problems whatsoever.

---

### Post by boot_sectorz on 2008-05-01
I think people are missing the point here. We know some computers are working way fine with Hardy. But some of us have this freezing problem. Gusty didn't have it. Fedora, Suse didn't freeze on me. Actually this is my first freeze on Linux ever. I installed Hardy 5 days ago. I have had 8 random freezes. All fails and you have to cold-boot the machine in order to do anything. I have not figured out what is the problem as it occurs randomly and even when you have absolutely nothing running, 30secs into a boot and it freezes rock-solid! Some suspect graphics drivers, wifi etc but none of that match what I have.

Dell D630
Intel 965i Graphics
Intel Wireless Card
Centrino Duo

---

### Post by nomeat on 2008-05-01
Just want to confirm that I have lockups after the screen saver has been on for a few minutes.
This comes with such consistant regularity that I believe any efforts to resolve the lock ups should start with how the screen saver interacts with the system.

I am using Ubuntu Studio 8.04 that comes with the -rt kernel (and a very cool look and creative applications. Just need to add the office and email programmes of your choice.)

I also find that most other applications run much smoother than former distros ( and I use a lot of unusual apps).

I hope disabling the screen saver resolves the problem for now.

Kubuntu with KDE4 uses the generic kernel and I deleted it due to too many failures including total lockup everytime I logged out or try to shut down.
Always powering off at the power point or holding the power button for 6 seconds was one of the reasons why I switched from Windows to Linux.
This is the first time I have had to do this in the 2.5 years since I made the change.

---

### Post by madad2005 on 2008-05-01
Don't know if this has been mentioned already, but my taskbars lock-up when I click on the clock/date on the top right task bar after a fresh install. I can still work if there are windows active on the main screen, but the task bars are frozen. I assume someone else has already picked it up.

I do like Ubuntu 8.04. You have to expect some bugs to be present, especially if the software is free.

---

### Post by scrop79 on 2008-05-01
> **madad2005 said:**
> Don't know if this has been mentioned already, but my taskbars lock-up when I click on the clock/date on the top right task bar after a fresh install. I can still work if there are windows active on the main screen, but the task bars are frozen. I assume someone else has already picked it up.

I do like Ubuntu 8.04. You have to expect some bugs to be present, especially if the software is free.

Yes, i did get same problem many times. When i click on the clock, task bar freeze. Everything else still working. Someone please let me know how to fix this. Thanks in advance

---

### Post by NotTheMessiah on 2008-05-01
> **madad2005 said:**
> Don't know if this has been mentioned already, but my taskbars lock-up when I click on the clock/date on the top right task bar after a fresh install. I can still work if there are windows active on the main screen, but the task bars are frozen. I assume someone else has already picked it up.


Yep that happens to me on the laptop. And when you restart x(ctrl-alt-backspace) a couple of times the menu/panels disappear and it finally throws this error message:

[http://img388.imageshack.us/img388/4179/crashtf4.png](http://img388.imageshack.us/img388/4179/crashtf4.png)

And then you have to restart fully.

---

### Post by nomeat on 2008-05-01
> **scrop79 said:**
> Yes, i did get same problem many times. When i click on the clock, task bar freeze. Everything else still working. Someone please let me know how to fix this. Thanks in advance

This works for me:
Open a new panel at the bottom and add a new clock there.
I could remove the top clock with a right mouseclick.
I like it better that way anyhow.
I have all the launchers at the bottom so the top panel only shows what applications are open.

---

### Post by NotTheMessiah on 2008-05-01
> **boot_sectorz said:**
>  Gusty didn't have it. Fedora, Some suspect graphics drivers, wifi etc but none of that match what I have.

Dell D630
Intel 965i Graphics
Intel Wireless Card
Centrino Duo

Gutsy was freezing on me as well...similar story with Hardy. I suspected firefox but then it froze when a screen saver was running just like one person experienced but with Hardy this time. 

It's not the wireless since i don't have wireless on my desktop. And i have an Amd 64 socket754. It definitely might be the n driver but we can only guess

---

### Post by SniperSlap on 2008-05-01
Every time I log in, I get a message talking about an error for an unsupported or not installed package.

Playing sound through totem causes my computer to hang.  No ctrl-alt-backspace, only a reboot.

Any time I move from WiFi to Wired connections, I have to log out and back in to use gnome vfs ssh mounts.

Any time I open files on a gnome vfs ssh mount, a new mount is created.

What is going on with this release?  Why did it go ahead if it wasn't ready?!  Another problem I'm noticing now is that the Ubuntu teams are conspicuously quiet on this matter.
I really hope they don't end up turning out to be like any other company or project on this.  Speak up and acknowledge the problems.

Many other people who have upgraded are noticing odd problems here & there.  The system just isn't "hardy".  If updates are released to address issues, I hope they update the install disc images...

---

### Post by zetetic on 2008-05-01
> **Jim March said:**
> Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

A bug has been issued to the kernel team, priority high, marked "triaged":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

Today I did a fresh install from the release CD, standard 32bit, Intel945 video, Atheros WiFi, all standard parts on an Acer laptop that handled Feisty and Gutsy like a champ.  No overheating.  1.5gigs RAM, swap stats show zero use so it's not corrupted swap.

I don't think the devs are going to be able to fix this one easily.  There's just NO feedback or debugging info possible.  When Fedora 9 releases I may be forced to abandon ship.

This really sucks.

You should be using Debian. No problems at all.

---

### Post by zdude on 2008-05-01
Damn! I tried Hardy, did a clean install (2 time) and all was working - until I found the networking download speed was horrible. Tried the serialmonkey driver - same story. This was downloading via any program. Weird thing is my wireless when downloading @ < 100Kb/s would kill the speed for all the users on my wireless net. I switched back to 7.10 and I am back to > 5000Kb/s downloads and other users can't even tell. Weird! The best I could do is retrace it to the kernel but it was causing weird pauses and dropped packets and others on my wireless were complaining so I had to rollback. My router showed it was really busy and there was no data flowing.
Outside of that - I was starting to like Hardy but I have a need for speed:)

---

### Post by Geekkit on 2008-05-01
> **tact said:**
> Notice the effect of it on geekkit from his post (below)


Its a bit sad isn't it?  When someone (OP) acts irresponsibly with their comments, exaggerates wildly, and causes someone who has never tried, and thus can never know whether his hardware will run hardy well or not, to turn their backs on what may be the best ubuntu experience they have ever had - Hardy. (as testified to by the many of the majority who find hardy to be the best release ever).

Not to mention the effect unseen it has on silent readers who perhaps have been thinking of trying ubuntu and after reading this thread title decide to give it a miss totally.

You're suggesting that John "exaggerated wildly" and I have "never tried"? Did you even read any of the bug reports from the bug forum that John linked to? There were literally dozens of people having lockups and reporting their logs, changing/turning off hardware, downloading, compiling, and updating kernels in an attempt to isolate the problem.

Really, go read the links to the bug listings before firing off any more posts. It may help you save any last shred of credibility that you have left.

---

### Post by keylime on 2008-05-01
Only problem I have currently, between three machines that have it, is that the 64-bit O/S won't run Flash well with a bridge website. That's it. Otherwise, it's smokin'.

---

### Post by HunterA3 on 2008-05-01
I've been using Ubuntu for about 4 releases now, can't remember the rev level, and I can't recall having the number of issues I've experienced so far with 8.04
 
Everything ran slower, ATI drivers failed to load, compiz didn't worked because of the video drivers, wireless network did't work, it broke several of the programs I had running in Gusty, and despite installing the drivers for my printer, it still would not recognize them to complete the setup so I could print. 

On a positive note, I didn't have the random lock ups that many others are describing and the programs that did install properly ran fine--one of the benefits of using an older laptop I guess.

Because it was impacting productivity, I had to go back to 7.10. I guess I'll wait for the wrinkles to be ironed out before I try again. I assumed since this was the next LTS release that the bugs would have been squished before the release date. Not that I'm faulting anyone who worked on the development of this release. It just caught me off guard since I'm use to it just working.

---

### Post by Saint Angeles on 2008-05-01
> **Geekkit said:**
> You're suggesting that John "exaggerated wildly" and I have "never tried"? Did you even read any of the bug reports from the bug forum that John linked to? There were literally dozens of people having lockups and reporting their logs, changing/turning off hardware, downloading, compiling, and updating kernels in an attempt to isolate the problem.

Really, go read the links to the bug listings before firing off any more posts. It may help you save any last shred of credibility that you have left.

haha... dozens of people (out of the thousands upon thousands that have downloaded hardy and installed it) and all of a sudden hardy is the worst ubuntu ever!

thats called exaggeration.

---

### Post by oyvinst on 2008-05-01
This thread (and its topic) is [COLOR="Red"][SIZE="2"]sc[/SIZE][SIZE="3"]R[/SIZE][SIZE="5"]E[SIZE="6"]A[/SIZE]M[/SIZE][SIZE="3"]IN[/SIZE][SIZE="2"]g[/SIZE][/COLOR] too loudly. I've installed Hardy-H on three different machines with quite different hardware, two new laptops and an older desktop, using restricted drivers on two of them. Hardy has given me very little problems. Sure, there are a few quirks and things that needed fixing, but all in all a great experience. Never had any lockups on any of them, and I guess I should be happy about that. But my point is, don't automatically assume that most others will have to face the same problem and therefore advise them to avoid Ubuntu. That's simply not the case. Hardy is the most feature-rich Ubuntu to date, and with that comes complexity. I'm sure the kernel-devs/maintainers are working hard at fixing the most pressing issues that have surfaced after the release. And it doesn't cost you a penny, nickel, dime or whatever.

---

### Post by revelationman on 2008-05-01
Well I am experiencing constant lock ups so it is an issue
I have to hard reboot always I am very disappointed with this and please do not say i should of check the hardware read the past comments others are having the same issue's. 
I think the Dev team miss the boat on a few issues with this they should waited longer to get all the bugs out
Do not get me wrong I like Ubuntu very much but if they want to take a serious shot at the big boys stuff like this should not happen 
I was going to put this on my friends laptop and I do not think I should bother. I do not want the headache of someone saying you put this crap on my laptop and now it freezes. 
Oh not all of us are brave enough to compile a kernel so get bloody real 

Cheers  

:mad::mad::mad::mad::mad::mad:

---

### Post by LorisMaria on 2008-05-01
Even though the title might be too harsh and alarmist, the problem exists, as we can tell by the amount of people on this thread that have reported the same experience.

It's happening to me as well, on my Gateway laptop. It runned smoothly at the beginning, now I'm getting lockups everytime powersaving tries to kick in. I tried changing all configs, but to no avail. There is nothing else wrong, so I don't know what to try and fix.

I'm too newbie to go around messing with kernels and realtime, so I'm hoping they'll release a fix for it soon. Just today, I've hard restarted the computer around eight times. I moved from Windows because this was unnaceptable, but one can only hope that the smart people developing this will find out what's happening :)

It's sad I cannot help more than just by whining about it here.

---

### Post by Holonet on 2008-05-01
I have to agree with revelationman here.  I actually don't have any glaring problems with hardy so far.  Firefox 3 is running faster, nothing seems to have slowed down on my machine...  I would take ubuntu over most other OSes (especially Windows), any day of the week, but the fact does remain that with issues like this, minor, but annoying ones which pop up consistently, it cannot expect to gain ground with the commercial systems.

Facts are facts, and I would bet that 90% of computer users make any newbie in here seem like a hacker 50 feet underground with their own robotic pizza dispenser.  This isn't because they're all stupid, but many have learned to accept the bulky powerless interface of Windows in payment of simplicity.  In every release, there are still issues which the Windows user can say "that never happens to me" to.  Surely, companies like Microsoft deliberately make things difficult whenever they can.  There is no blame to throw around so much, but if this community is to grow beyond those who are willing to sit for more than 5 minutes to figure something out, Ubuntu will have to overcome these problems.

---

### Post by bigbrovar on 2008-05-01
> **Saint Angeles said:**
> haha... dozens of people (out of the thousands upon thousands that have downloaded hardy and installed it) and all of a sudden hardy is the worst ubuntu ever!

thats called exaggeration.
u have to put things in perspective i great number of pple have reported lockup with their system running hardy.. even though there never had such a problem in gutsy.. the fact that it might look like a small number of pple doesnt matter .. not everybody with the problem have reported it in Ubuntu forum.. but the problem exist.. i myself has terrible lockups when i upgraded to hardy and yeah i did a clean install .. it was just sooo bad that i had to downgrade to gusty something that i have never done since using Ubuntu.. and i can say that i have not experienced one lockup since .. yeah the title of the thread might be a bit extreme but i guess it was written  in the heat of frustration .. i myself wrote crapppy things about ubuntu at the height of my frustration.. (although i quickly edited my post when i calmed down :) ) .. anyway i know the devs are working on it and things would soon be straightened out soonest .. but for now i wont recommend it to a new user

---

### Post by tact on 2008-05-01
> **bigbrovar said:**
> .. anyway i know the devs are working on it and things would soon be straightened out soonest .. but for now i wont recommend it to a new user

Why is that?  Because you think a new user may have the experience of the minority rather than the majority?

Isn't a more reasonable approach the same approach any new user to ubuntu should take - burn a live CD...  run off the liveCD for a day or two and see whether hardy runs fine... "on his hardware".

(btw no one is saying the experience of the minority is unimportant - what I am saying is that its not valid to brand hardy (period) as the worst ubuntu yet, or even say hardy (period) is unstable - because there is a huge userbase out there who find hardy to be the best release yet and rock solid stable)

Cheers.

---

### Post by mrojas73 on 2008-05-01
> **adityakavoor said:**
> I agree:mad:

I do not,  running on my Dell XPS 1530 and Desktop with 0 issues.

---

### Post by minibeardeath on 2008-05-01
i am a brand new user (i lterally switched from xp on sun apr. 27), and i am having a blast w/ hardy heron. this is my first full time linux experience ever, and the only problems that i have had have been the driver issues associated w/ any switch. i have had one lock up, but that generated an error repoet and everything.i built my system myself about 6 months ago, and hardy heron is far greater than xp could have ever dreamed of being

---

### Post by tact on 2008-05-01
> **Geekkit said:**
> You're suggesting that John "exaggerated wildly" and I have "never tried"? 


Absolutely to both points!   

1.  jim march, the OP, has exaggerated wildly saying (thread title) "Hardy is BY FAR the worst Ubuntu version yet. LOCKUP WARNING!!!"

The reason I say this is that no one can deny that there is a far greater number of people who have no issues with hardy, and find it the best release ever as well as rock solid.

This does not deny that a problem exists, for SOME people.  And this does not amount to silencing anyone who has a problem with hardy.

2.  In your post you thank jim march for the "warning" and will "stay away" from hardy.  

A plain understanding of your words "stay away" from hardy indicates you have not ever tried hardy and will "stay" in that place.

Have you tried hardy?  You don't have to.  I am not insisting.  Just observing.  Are you not trying hardy because of this thread by jim march? (your post clearly indicates this is the case).

Ergo - you are not trying hardy based on the wildly exaggerated posts of jim march in this thread.   

Cheers.

> **Geekkit said:**
> 
Did you even read any of the bug reports from the bug forum that John linked to? There were literally dozens of people having lockups and reporting their logs, changing/turning off hardware, downloading, compiling, and updating kernels in an attempt to isolate the problem.

Really, go read the links to the bug listings before firing off any more posts. It may help you save any last shred of credibility that you have left.

Oh yes.  I have read the bug reports jim march links to.  Avidly and with interest so I can understand the problem in case I need to assist someone struggling with the problem.

I even exchanged posts with jim march in the hardy beta development threads before hardy was released.  He was being alarmist back then too but I wanted to understand how the problem presents itself and what people tried to fix it.  I remember posts advising Jim to not be so alarmist and try to assist devs by logging problems on launchpad.  He did so eventually but apparently has not ceased to be alarmist.

Thank you for your inputs.  I think my credibility stands fine.

---

### Post by simon_w on 2008-05-01
+1 for "No problems whatsoever" - in my experience (so far, at least) this is the best ubuntu release I've ever used, and represents a significant improvement over Gutsy even, for me.  Many things which I had to scour forums to get working in Gutsy worked out-of-the-box with Hardy, and performance (again, so far) has been excellent.

Very happy indeed.

---

### Post by xscottx3 on 2008-05-01
I am happy with Hardy so far. Though there were was one episode where it logged me out for no apparent reason. Now and then the entire desktop, applications and all will freeze up for a few seconds. Hopefully I can sort it out.

---

### Post by NotTheMessiah on 2008-05-02
> **xscottx3 said:**
>  Now and then the entire desktop, applications and all will freeze up for a few seconds.

Welcome to the growing minority:) Let's hope that our problems will be solved soon.

---

### Post by Saint Angeles on 2008-05-02
> **NotTheMessiah said:**
> Welcome to the growing minority:) Let's hope that our problems will be solved soon.
just give it some time. its important that people are vocal about their problems with hardy so that the devs can get to the bottom of things and fix them. but every OS ever released has had problems. we are lucky enough to be using an OS with an outstanding community of developers and newbies alike. i'm sorry about your hardy issues but be realistic.

have you ever seen a version of windows released that was absolutely perfect with not a single bug? at least with Ubuntu, there are constant updates (not like windows updates that come out every couple months).

also, people are a lot willing to help people when they keep their cool and are respectful.

"you catch more flies with honey than vinegar"

---

### Post by RickAstley on 2008-05-02
Most of the problems with Hardy Heron can be attributed to Robb Carr... he really let us all down.

---

### Post by nomeat on 2008-05-02
[SIZE="5"]**I just want to report that since I disabled the screen saver, I have had no lockups any more.**[/SIZE]

I use the -rt kernel not the -generic version.

Short "lockups" (5-30secs) are normal in my experience with Linux. I have had that a lot with Open SuSE too. This depends on what processes are running in the background and I wouldn't straight away assume a bug in the OS.

I would urge everybody with these problems to add the system monitor applet in their panel.

---

### Post by NotTheMessiah on 2008-05-02
> **Saint Angeles said:**
> just give it some time. its important that people are vocal about their problems with hardy so that the devs can get to the bottom of things and fix them. but every OS ever released has had problems. we are lucky enough to be using an OS with an outstanding community of developers and newbies alike. i'm sorry about your hardy issues but be realistic.

have you ever seen a version of windows released that was absolutely perfect with not a single bug? at least with Ubuntu, there are constant updates (not like windows updates that come out every couple months).

also, people are a lot willing to help people when they keep their cool and are respectful.


I completely agree with everything up there.As a recovering Windows user i have an extremely high tolerance for pain. My frustration is not of the "i am going back to[insert operating system]" type but rather of the "I can't use my Ubuntu properly because it freezes on occasions" type. 

Cheers

---

### Post by antonym on 2008-05-02
personally, I don't think the 'lockups' problem is one single problem, nor do I think that it's caused by any one version of ubuntu.

I started using ubuntu with Feisty Fawn, and then upgraded that installation to Gutsy some weeks after it came out. Not long afterwards, I began getting freezing issues -- randomly, not connected to processor or memory usage, no mouse or keyboard or alt-sysrq function. 
Gutsy kept freezing, anywhere from minutes to hours after I started the computer up -- sometimes before I even logged in. Nothing I tried helped at all, so I shifted back to Windows 2000 for a few months, hoping Hardy would fix the issues.

Upgrading that same installation, first to the Hardy beta, then to the full release... did nothing. Still freezing. What's worse, the startup process spawned worrisome fsck and kernel errors, and my screen resolution couldn't be coaxed above 640x480.

Early this morning I installed Hardy, with only minor hiccups. The fresh installation is running fine -- I've been on it all day, with no freezes whatsoever thus far (though I haven't dared turn on the restricted drivers yet). I'm really quite happy about it.

My theory, therefore, is that in SOME (many?) cases, freezes and weird screwups are caused by some flaw in the upgrading system.


Everyone, just chill out. It's frustrating, I know. I've been incredibly frustrated too. But I'm not jumping around wailing about Gutsy or Hardy being the worst versions ever, or blaming the devs. There are problems somewhere, and they will be fixed.
If this clean install seems to work for me, I will spend the time to copy over all of my files and programs and settings and custom themes. Despite all my problems, I greatly prefer Ubuntu over every other OS I've tried, even the W2K that I spent so many years on (which is the best thing M$ ever put out, btw). 
Thanks to the devs for their hard work in making this a great release, and I sincerely hope the many assorted freezing issues are worked out as fast as possible.

---

### Post by Delever on 2008-05-02
OK, since many who had lockups post here, lets see if there is some trend. I saw one post to mention socket 754 amd64 processor; that's the one I have.

Let me guess: nForce3 motherboard probably too? That's the one nVidia named as 'legacy', just to avoid releasing driver updates for it. Apparently hardware is buggy as hell. I had to use some half-baked drivers to get audio working on Vista.

So, my setup is this: K8N-E Deluxe motherboard with nVidia nForce3 250Gb. I saw in launchpad that there was no specific trend, but does anyone who experienced lockups also have this hardware?

---

### Post by Slade Winstone on 2008-05-02
Hi,

I've been having horrible lock up problems with Ubuntu, as have MANY, MANY others (try searching the message boards) since early Gutsy (maybe even late Feisty).  

In my case lock-ups seem to be (maybe) related to laptop ACPI.  With a boot kernel switch of "noacpi" or "acpi=off", my lock-ups all but disappear.  I believe after much googling that, at least in my case, this may be related to kernel development and very poor bios ACPI implementation.

For those using laptops and having lockup problems, try switching off ACPI, and hope desperately that future kernel development might see an end to this problem :(

Slade.

ps. still love Linux and Ubuntu and never going back to Windows! :)

---

### Post by xelink on 2008-05-02
no lockups thus far everything seems rock solid and any complaints are minor and far outweighed by the improvements(nvidia drivers in synaptic which is nice, more automated install, system basically "just worked" no real config needed)
and I'm running with a 70% overclock on CPU and motherboard and 2 sticks of RAM, and a 35% OC on the other set

---

### Post by Delever on 2008-05-02
Browsing through incoming updates (for 8.04.1, they are visible with PROPOSED section enabled), i found that many address hangs in various different places, like:

compiz-fusion-plugins-main Version 0.7.4-0ubuntu5:

* fix another possible hang during animation

evolution-data-server-common (this was probably my problem):

* fix double free in the contacts backend, the issue could be causing the clock applet hang that several users are having (lp: #204775)

lshw:

* Add 10-cap-detection.dpatch: fixes hang when reading capabilities of some PCI devices (LP: #202460)

So bug fixes are coming. Who doubted that?

---

### Post by miksuh on 2008-05-02
First I want to say that i'm sorry that so many of you have those lock up problems etc. I hope those problems will be solved rather sooner than later.

Secondly, yes I'm long time Debian user. I have been using Debian on desktop and server since 1998. But I'm not here because I would try to turn you away from Ubuntu or try to convert you to Debian users. It's your choice which distro you use. You are free to choose.

But to be honest I'm not surprised, not at all. I was expecting something like these problems. That hype around next "stable" Ubuntu LTS-version did not really convince me. Maybe I have been using linux way too long to be fooled like that. I would like to remind you about one thing which many of you ubuntu users tend to forget.

All Ubuntu releases are based on development version of Debian, Debian unstable aka Sid. Debian unstabble is development version which is not even meant to be used on production systems, not on desktops and ot on servers. There IS lots of bugs in Debian unstable and if you are using it you should be ready for the problems. 

This graph tells more than million words:
[http://bugs.debian.org/release-critical/](http://bugs.debian.org/release-critical/)

The red line is shows the number of release critical bugs (RC bugs) in Debian unstable, green line shows number of RC-bugs in Debian testing (currently Lenny) and Blue line shows number of RC bugs which have been found from Debian stable (currently Etch) after the release of stable. Etch was released when green line was close to zero. RC- bug is a bug which is severe enough to stop Debian from releasing. Next Debian release will be made when that green line is again close to zero, not before that. Next release is still scheduled to be before end of this year.

As you can see number of RC bugs in Debian unstable is much much higher now than anytime in recent years. And Ubuntu Hardy Heron is based on that same codebase. So am I surprised that there is stability problems with Hardy? No i'm not. 

There seems to be lots of confusion about what Ubuntu LTS means. No LTS does not mean that release is more stable than other ubuntu releases. And no it does not mean that development cycle was longer than with other releases. It means just what it says LTS = long time support. Ubuntu project supports LTS version longer than other releases, that's it.

Mark Shuttleworth sayd awhile ago, that he would like to see all major Linux distro releases be syncrhonized. I can see why, because it's not good to release ubuntu when Debian unstable is in it's most buggy state in years. But it's not going to happen. Debian will not, change it's release cycle to Ubuntu style. Debian is released when it's ready, not before that. Stability is wery important for the Debian. Debain is huge project and it take stime to test everything well. So ubuntu has a big problem.

I think Ubuntu project is trying to do something which is not possible. They are trying to create Debian sized user friendly distro with latest software and short release cycle, and still keep it in somehow usable state. And that's not possible. In my personaly opinion it's pure impossibility to create stable release in 6 months like ubuntu does. Debian is currently aiming for 18 month release cycle, that's much more realistic than 6 months. Eg. it took 21 months to release Debian Etch which was released 13 months ago.

I think that sooner or later ubuntu developers realize that they have to make release cycle longer. Debian continues to grow. In Debian lenny (testing) there is more than 3000 packages more than 
in current stable. This means lot more work. Evey releas is bigger than previous. Ubuntu project can't handle that kind of growth if they want to keep that 6 month release cycle. I nothing changes you will see more worse problems in the future too.

As I said, I'm not trying to convert anyone. but if you have problems with Ubuntu then try Debian. If you can use Ubuntu then you can use Debian too. Debian Etch is wery easy to use.

---

### Post by karellen on 2008-05-02
interesting post miksuh, you really put things in the right perspective :)

---

### Post by Seventh Reign on 2008-05-02
I think some people need better computers .. Its been a week and I have not experienced a single lockup or crash.  Solid like Granite .. Beautiful like Marble.

---

### Post by jaknap on 2008-05-02
One more problem with Skype. When I connect to Skype it gives me error of P2P connect failed. Please suggest me, what to do. and my Skype is behind proxy server. Can Any one.. :)

---

### Post by mozetti on 2008-05-02
> **jaknap said:**
> One more problem with Skype. When I connect to Skype it gives me error of P2P connect failed. Please suggest me, what to do. and my Skype is behind proxy server. Can Any one.. :)

You're not going to get help for that in this thread. Either find a thread that's already discussing your problem and ask for help there, or start a new thread (only one!) detailing your problem.

---

### Post by Mighty_Joe on 2008-05-02
> **Delever said:**
> 
So, my setup is this: K8N-E Deluxe motherboard with nVidia nForce3 250Gb. I saw in launchpad that there was no specific trend, but does anyone who experienced lockups also have this hardware?

Nope. I get lockups within 10 minutes of booting and have unrelated hardware:
Gigabyte 7ZXE Mobo (VIA chipset)
AMD Athlon XP 2000+
ATI Radeon 8500

---

### Post by zerix01 on 2008-05-02
Running Kubuntu 8.10 AMD64 with KDE 4.0.3

System runs noticeably faster than with 7.10 and no lock ups and all hardware works out of the box. My system is heavily overclocked and stressed all the time with Folding@home. Hardy is the first Ubuntu that I didn't need to hack the xorg.conf file to get my screen to correctly display 1440x900. Gusty, even after installing the Nvidia drivers, would display nothing once X started if I didn't disable the splash screen, this is no longer the case.

The only problem I had so far was upgrading from Gusty to Hardy ended in disaster. I'm pretty sure this was due to me having the Nvidia drivers installed through Envy which I remembered after the fact says to uninstall it before upgrading. I don't know if there are outstanding issues with upgrading from one to the other so a clean install couldn't hurt to try out for those of you that went the upgrade path.

Also I think my speed difference is from CFS introduced in 2.6.23. I wonder if that is conflicting with some configs. I know some more features were added in .24 so possibly they were they start of this mess. I know CFS effects how much CPU time each process gets, I'm not sure if it effects how they are executed or not which may cause such issues. Has anyone tried another distro with these kernels and experienced the same problem?

My Hardware:
Athlon X2 3600 AM2
EVGA (Foxconn) Nvidia 590SLI
Nvidia 8800GTS 320MB
Audigy Platinum PCI sound card
3x500GB SATA RAID5 using mdadm

---

### Post by AnneFtl on 2008-05-02
Hi, **Brand new user** , installed HH last night.
 I had a total lockup while playing with making new folders that point to info on another HD.
 The lockup required a power off to get out of it.
 Today, I came here looking for answers and found I am not the only one having freeze problems....  HOWEVER

I also find a number of people are compiling a different version of something and then all seems to work ok.. 
 
**MY QUESTION..... **
What are you compiling, where do you get it, and when its done how do you exchange it for whatever it is that is bad?

I do not want to try and learn another OS while having to worry if a system freeze is OS related or STUPID OPERATOR related.

---

### Post by Delever on 2008-05-02
> **AnneFtl said:**
> 
What are you compiling, where do you get it, and when its done how do you exchange it for whatever it is that is bad?


If you are new, i suggest NOT to do that.

Sadly, it seems that the best thing for now is to wait for updates. There already are new proposed (under testing) updates coming which MAY fix lockup problems for some. Proposed updates can be enabled (System->Administration->Software Sources), but again, as I understand, they can be canceled (correct me if I am wrong), and then you are on your own.

---

### Post by lazyart on 2008-05-02
I would suggest downloading gusty (7.10) and using it for a month or so until things setting down, then upgrading.

---

### Post by antonym on 2008-05-02
> **Delever said:**
> OK, since many who had lockups post here, lets see if there is some trend. I saw one post to mention socket 754 amd64 processor; that's the one I have.

Let me guess: nForce3 motherboard probably too? That's the one nVidia named as 'legacy', just to avoid releasing driver updates for it. Apparently hardware is buggy as hell. I had to use some half-baked drivers to get audio working on Vista.

So, my setup is this: K8N-E Deluxe motherboard with nVidia nForce3 250Gb. I saw in launchpad that there was no specific trend, but does anyone who experienced lockups also have this hardware?


It does seem that some people's problems are related to nvidia hardware. I have an ABIT KN8 Ultra (socket 939, and I believe nForce4), with a 7300GT video card.
In the bugs I was following on launchpad, some people were helped by installing the newest nVidia drivers from the company's website -- this was generally for people with a 7300/7400 card (instructions at help.ubuntu.com/community/NvidiaManual). 
While it seemed like this is the fix that would apply to me, it didn't help my case one bit. However, doing a clean install (rather than one upgraded from gutsy) seems to have gotten rid of the freezing -- or at least thus far.
For other people with freezing, there are a handful of different solutions for a problem that seems to present the same in most cases... just keep trying different things.

---

### Post by aimpau on 2008-05-02
I've been with this problem ever since it arrive in Gutsy. I had a full week of no lock up in HH **until** I auto mounted my 2nd HDD.


Try to answer the ff:
**TREND PLOTTER**
Do you have:

1. TWO HDD (linux and XP)?
2. Your CD/DVD drive is a slave of the non-linux HDD?
3. Chipset video?
4. Jumperless Overclocking (AMD)?


To all those having lockups, please try the ff:

1. Figure out what the ID number of process "cupsd" and "cron". KILL THEM
2. Disable automount of XP hard drive.

Please get back to me regarding the results.

---

### Post by aimpau on 2008-05-02
Also, please post your dmesg.

---

### Post by gentooruwest on 2008-05-02
First off, would those of you that are lucky enough to have specific hardware that doesn't show this problem please stop telling those of us that have hardware which doesn't work with this kernel that it's our fault and that we're a minority?  We don't need better computers :)  Mine was just built.  

I'd just like to add my name to the list of people who are quiet please with the feature rich and smooth release of Hardy ... however I'm also one of the ones facing the lock-ups.  This problem is clearly with the smp code of the kernel that hardy released with.  Nothing against hardy ... if anything the blame should be placed on all those responsible for beta testing and doing QA on this kernel.  I myself am going to wait it out until the dev's release a fixed kernel.  I actually like hardy that much.

---

### Post by The_Boot on 2008-05-02
Is this just an Ubuntu problem or is it in all Ubuntu derivatives? I've been using Xubuntu Hardy since it was pre-beta and haven't had it crash once. I'm using it at home on a Toshiba laptop and a 3.2GHz dual core P4 w/ 2GB DDR. I've also installed it on over 15 other computers ranging from a 500MHz Celeron with 64mb SDRAM to a 2.4GHz P4 with 512mb RAM and all different hardware setups. It may be a Gnome problem, not a kernel bug if it's just in Ubuntu. 

That's just my 2 cents.

---

### Post by AnotherFineMess on 2008-05-02
I had the same annoying glitches of high iowaits (constant Hard Disk use) causing the system to become unresponsive when i upgraded to Hardy. I tried unistalling the Tracker Deamon, Fuse Server, disable Effects etc. but nothing seemed to actually make things better. I tried compiling the new kernel (2.6.25) though it did not work 100% ok. In the end  i downloaded the kernel deb binaries from the Kernel archives for my AMD64 processor at [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/") which gave a breath of fresh air to my system. No more constant Hard Disk use...

[COLOR="Red"]Download from the link above your system specific architecture. You should uninstall your Graphics Card Drivers before rebooting and reinstall them after booting with your new kernel using the restricted drivers manager or with EnvyNG
[/COLOR]

Note that the correct files for the AMD64 architecture which i used for my system are:
[linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb")
[linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb")

When these 2 deb's are installed reboot and your new kernel will load as default from the grub menu

---

### Post by spaceboy909 on 2008-05-02
Hardy has hosed my resources pretty bad.  My system is now stuttering and stalling all over the place, compared to Gutsy, and compared to Windows XP..............well, unfortunately, XP wins the resource game hands down on my box.  Firefox might use 15% cpu in XP for a given set of pages, and in Ubuntu, for the same pages, it can range between 30-60%.  In some cases it takes 90-100%, and that's just unbelievable.

I'm trying to make the switch to Linux, but there are so many hang ups and issues, and the "easy guides" are typically 10-20 page hacker manuals.

I suppose when I get my new system, some of these problems won't matter anymore, but if Ubuntu can't knock out some of the more annoying issues, I'll have to try other distros that are more stable and resource friendly.

---

### Post by SonicJMC on 2008-05-02
I had a nice fast gutsy system, also was nice and fast in Feisty.
Now, Hardy... Can't use compiz, system is barely usable. Ugh, I feel like I'm back in Windows.
Sadly, my Windows XP install now outperforms my Ubuntu install by a long shot. That's sad.

---

### Post by Geekkit on 2008-05-02
miksuh:

Thanks for the very informative post and especially for the link containing facts not feelings. It really helps point out what many are finding out and why. Personally, I will be waiting at least three months before even attempting Hardy. I too have had a problem with this "thou shalt release a new version every six months". It's unrealistic. I'd much rather wait until it's fully baked before using it.

---

### Post by enchantedsky on 2008-05-02
All you Hardy Heron critics amaze me, because I feel Hardy is the best Ubuntu release so far. Everything works on my Dell, except hibernation/suspect mode, but that's easily forgivable when I know there aren't any good motherboard drivers in Linux for my Dell.

What you guys really need to do is NOT upgrade; you need to do a CLEAN INSTALL of Ubuntu Hardy Heron. I experienced numerous problems when I upgraded from Ubuntu 7.10. Report back to this thread, or post a new thread if things are different (e.g., fewer problems than before).

Remember, it's too easy to blame Ubuntu when things aren't working. But try to be more specific, like perhaps it is Gnome's fault, the newer Linux kernel or X-Org's fault (Hardy is using newer versions of these programs). What solved many of my Gutsy Gibbon problems is probably the newer Linux kernel being installed by default in Hardy.

---

### Post by NotTheMessiah on 2008-05-02
> **Delever said:**
> OK, since many who had lockups post here, lets see if there is some trend. I saw one post to mention socket 754 amd64 processor; that's the one I have.

Let me guess: nForce3 motherboard probably too? That's the one nVidia named as 'legacy', just to avoid releasing driver updates for it. Apparently hardware is buggy as hell. I had to use some half-baked drivers to get audio working on Vista.


I've got a DFI LanPArty UT nf3 250GB,geforce 6600GT, clawhammer 3700+,one SATA HDisk and a DVD BUT i also have hardy on my laptop centrino 1.73ghz, geforce 6200 Go.

I've experienced lockups on both. On the laptop i got the calendar locking up bug(requiring restart) and the evolution server hitting 100% CPU usage and then obviously FF stalls(need to kill it) and the wireless seems to be stalling as well.

On the desktop i don't have the calendar issue but i've had complete freezes(requiring cold shutdowns) - i had ff opened,a pdf file and was working on some documents(word document etc)....and the evolution-server bug as well.

---

### Post by NotTheMessiah on 2008-05-02
> **enchantedsky said:**
> 
 you need to do a CLEAN INSTALL of Ubuntu Hardy Heron.

Both of my installs were clean and NOT upgrades.

> **enchantedsky said:**
>  Everything works on my Dell, except hibernation/suspect mode, but that's easily forgivable when I know there aren't any good motherboard drivers in Linux for my Dell.

So not quite everything...hibernation/suspend works on my laptop...every second time or so :)

---

### Post by revelationman on 2008-05-03
My experience with has not been great the 5 day lock ups were very annoying for me coupled the video and hard drive issues.
It would be hard to say the worst version of Ubuntu but there has been lots of negative feedback on Hardy. 
I am not a developer or programmer I cannot imagine how hard it must be to create an OS. I feel Hardy should of been held back for another few months, keep in beta till most of the bugs have been ironed out.
I believe Hardy can be a great system  but not now, I have went back to Windows XP it is stable hey it took Microsoft 6 years to make it stable. 
What I found very strange was to included Firefox 3 in beta they should of stuck with the stable version that to me was a very silly thing to include.
What I love about Hardy and miss is all the software that it come with,and the time clock with the weather and time zones.
I will keep on looking at the forum to see if any improvements have been made and maybe I might go back and try Hardy again.
In closing I still feel very positive on the direction that Ubuntu is going and I always will support it. 

:guitar:

---

### Post by FredB on 2008-05-03
27 pages of people complaining about hardy being the worse sh*t they've ever seen ?

Wow... It amazes me how people are complaining without looking to some of the roots of their problem.

1) Hardy is not gutsy. Xorg is Hardy was built to do autodetection. Just use hardware drivers from the "Driver manager" tool.

2) Do clean install

3) Think about overclocking or other hardware tweaking.

Anyway, I'm using Hardy since it was beta, and NO PROBLEM for me. Maybe because I know how to give my hardware respect ?

---

### Post by revelationman on 2008-05-03
> **FredB said:**
> 27 pages of people complaining about hardy being the worse sh*t they've ever seen ?

Wow... It amazes me how people are complaining without looking to some of the roots of their problem.

1) Hardy is not gutsy. Xorg is Hardy was built to do autodetection. Just use hardware drivers from the "Driver manager" tool.

2) Do clean install

3) Think about overclocking or other hardware tweaking.

Anyway, I'm using Hardy since it was beta, and NO PROBLEM for me. Maybe because I know how to give my hardware respect ?

Hardware respect what do you do salute it sorry to be sarcastic but I have done clean installs and I do run Ubuntu on my Compaq Deskpro that is fine. 

There is still some hardware that has some issues. 

I like Ubuntu and Hardy but no matter what I have tried it still locked up on me. 

I have submitted bug reports and I constantly look for any solutions. But really I cannot continue to hard boot this laptop it is not good on the hard drive.

So I just wait and see what happens maybe a update who knows.

:guitar:

---

### Post by yimmmy on 2008-05-03
<b>WOW </b>  i can Not belive this , i just recently upgraded my ubuntu gusty gibbon desktop to hardy <snip> and it is by far the bigest failure i have ever to see , i cant belive what this has done to me why has ubuntu let me down , my install went fine ... until the reboot . right after the loading splash screen my screen turns black and hangs dosent let me go to terminal dosent let me "three finger salute " it ,nuthing. 
right now i was in the process of throwing in the live cd And what do you know .. its taking 4 hours to just load the i/o buffers ...
i had 40 GIGS of personal pictures i just uploaded to this box 
and what has hardy done to me :"(

---

### Post by MONODA on 2008-05-03
> <b>WOW </b> i can Not belive this , i just recently upgraded my ubuntu gusty gibbon desktop to hardy <snip> and it is by far the bigest failure i have ever to see , i cant belive what this has done to me why has ubuntu let me down , my install went fine ... until the reboot . right after the loading splash screen my screen turns black and hangs dosent let me go to terminal dosent let me "three finger salute " it ,nuthing.
right now i was in the process of throwing in the live cd And what do you know .. its taking 4 hours to just load the i/o buffers ...
i had 40 GIGS of personal pictures i just uploaded to this box
and what has hardy done to me :"(
you can recover your files using [system ruscue cd]("http://www.sysresccd.org/Main_Page"). Print out the quick start guide and keep both that and the cd handy in case of system failure. You should never upgrade in ubuntu and dont even think about upgrading without backing up first. If you dont have the patience to try and make it work, switch distros, try opensuse or mandriva.

---

### Post by yimmmy on 2008-05-03
> **MONODA said:**
> you can recover your files using [system ruscue cd]("http://www.sysresccd.org/Main_Page"). Print out the quick start guide and keep both that and the cd handy in case of system failure. You should never upgrade in ubuntu and dont even think about upgrading without backing up first. If you dont have the patience to try and make it work, switch distros, try opensuse or mandriva.

yes i finaly got into the rescue disk But, for some reason i dont have permission to veiw or copy my photos , ive never delt with this before could some one reply the cmd or what ever it is for your permissions?

---

### Post by MONODA on 2008-05-03
> yes i finaly got into the rescue disk But, for some reason i dont have permission to veiw or copy my photos , ive never delt with this before could some one reply the cmd or what ever it is for your permissions?
you should open a nautilus window as root:
alt+F2 and type in "gksu nautilus" without the quotations. It will ask for your password, type it in and press enter. you will be presented with the root user's nautilus window. You can now do whatever you want in this window, be careful.

nautilus: the file manager for GNOME, like windows explorer
root user: the administrator user.

---

### Post by yimmmy on 2008-05-03
when you press alt-f2 it opens the application launcher , i can open a folder threw that but it dosent ask for a pass. on the live cd

---

### Post by MONODA on 2008-05-03
did you try copying the files at least?
PS. start a new thread, dont hi jack this one.

---

### Post by yimmmy on 2008-05-03
sorry , a new thread is a good idea just got a little carried away there. 
yes i did by the way

---

### Post by roderick on 2008-05-03
> **El Lance-O said:**
> I had problems of the such using Gutsy, where the screen would lock up, but mouse movement was still smooth and responsive. Restarting X with [ctrl]-[alt]-[backspace] did nothing, and at times holding [ctrl]-[alt]-[prntscn] and typing R-E-I-S-U-B (as noted in the ubuntuguide for Feisty/Gutsy) did nothing as well.

If I caught it quick enough, I could restart X and it would be fine. So there obviously have been problems like that, it's just catching us off guard because it's a new release.

I think it is a little harsh to say it's the worst, but there are definitely problems that need attention to by someone that has the technical ability to remedy.

Hopefully it all works out?

It's

ALT+SysRq+RSEIUB

No CTRL and the order is EXTREMELY Important and you must wait a few seconds between each to ensure that the system has time to kill processes. I posted a blog about this. See here: 

[http://roderick-greening.blogspot.com/2008/04/how-to-recover-from-system-crashes-or.html](http://roderick-greening.blogspot.com/2008/04/how-to-recover-from-system-crashes-or.html)

---

### Post by Ripfox on 2008-05-03
forget it...ugh

---

### Post by roderick on 2008-05-03
Hey all,

I have 2 complete systems running Kubuntu perfectly fine. Both were upgraded from Gutsy with no issues.

Both laptops are Acer, one with the Intel 855 and the other 950 chipset. Both have Intel GME video cards.

I use KDE and not Gnome.

I do not have the screensaver enabled, but OpenGL has been the root of past lock-ups I have seen on a friends system under Gutsy (using some 3D screensavers and Amarok visualizations) with an older ATI card. I traced the bug at the time back to the Mesa 3D graphics driver used by OpenGL.

Based on this (and reading earlier posts) I believe the lock-ups are probably video driver related. Check if disabling the screensaver solves your problems. Also, try disabling Compiz and running the native window manager (metacity/kwin). If either of these correct your problems, then the issue is video related, and can possibly be fixed if you report it as a bug in Launchpad.

In fact, I truly hope that all the people here who have experienced issues are reporting bugs in Launchpad. The only way for the devs to fix a problem is via the end user reporting the bug (or possible bug) via the correct methods. Posts like this, without associated bug reports, really serve no good intentions at all.

I have 2 systems with no issues. I also have friends who have no issues, and their hardware varies a lot (5 more systems). On these systems, no screensaver is enabled and Compiz is not enabled.

---

### Post by hodenkat on 2008-05-03
Here's my thoughs.

I have two identical laptops,one with 7.10, and the other upgraded to 8.04.
I took a big chance upgrading because the laptop had WinXP and was doing a dual boot just fine.

The one with 7.10 didn't need any tweaking at all. The one with 8.04 needed a minor amount of tweaking to get compiz to work but that's about it!
In hindsight I would not have upgraded because I didn't *need* to.
I haven't seen any benefit in the upgrade over 7.10 at all.

I would say to anyone who hasn't upgraded yet...**wait!**
Maybe it's just me but I don't see anything about 8.04 that makes it better than 7.10. It doesn't boot faster, it doesn't have any new features that make a big difference...it's the same to me. If anything it's not as friendly towards some video cards, but if you search around you can fix most issues with a few terminal commands.

In short, if it broke, don't fix it. :popcorn:

---

### Post by ORi0N on 2008-05-03
Well... I haven't installed 8.04 on new hardware yet, but on a Toshiba Satellite Pro 4600 laptop it works just fine... Only the new themes for gnome are a bit heavy for this machine, but with mist it works just fine... There's only an issue with the IrDA interface, but that was always a problem...

Are you sure there's not anything wrong with your hardware?

---

### Post by NotTheMessiah on 2008-05-03
> **revelationman said:**
> 
What I found very strange was to included Firefox 3 in beta they should of stuck with the stable version that to me was a very silly thing to include.


They have deemed it stable. I've been using it since it came out -b5- on my XP partition and it has been fast and rock solid ...not one hiccup.

---

### Post by NotTheMessiah on 2008-05-03
> **FredB said:**
> 
Maybe because I know how to give my hardware respect ?

Good for you mate :lolflag: well done

---

### Post by Geekkit on 2008-05-03
> **FredB said:**
> 27 pages of people complaining about hardy being the worse sh*t they've ever seen ?

That and clueless people insisting how everyone's hardware works with Hardy.

---

### Post by azimuth on 2008-05-03
> **Geekkit said:**
> That and clueless people insisting how everyone's hardware works with Hardy.

You must have found some threads I missed. It would be as wrong to claim that Hardy works with everyone's hardware as it is to claim that Hardy is completely broken just from one's own limited experience. 

Hardy does work on the three computers, so far, that I am running it on. If you want to know if it will work for you, you are going to have to try it. I sure wouldn't rely on the wildly varying accounts I've seen on here to prevent me from a chance to make up my own mind.

---

### Post by Geekkit on 2008-05-03
> **azimuth said:**
> You must have found some threads I missed. It would be as wrong to claim that Hardy works with everyone's hardware as it is to claim that Hardy is completely broken just from one's own limited experience. 

Hardy does work on the three computers, so far, that I am running it on. If you want to know if it will work for you, you are going to have to try it. I sure wouldn't rely on the wildly varying accounts I've seen on here to prevent me from a chance to make up my own mind.

Although I haven't installed it on my own two computers (I'm still using Gutsy), I've attempted to help two people I know well trouble-shoot Hardy on their systems only to watch the same thing everyone is complaining of in this thread: kernel freezes.

Kernel freezes/lockups are difficult to diagnose and trouble-shoot and it doesn't help when people like FredB come along and suggest that the reason why an install didn't work is because of the user not giving the hardware respect. The two people I know did clean installs, did not attempt to fiddle with settings (they left defaults), and realized quickly that asking questions will result in being flamed like so many have in this thread who are complaining and showing frustration with this problem.

To be honest, I'm not sure what is worse: the kernel lockups or the Linux fanatics that insist users aren't respecting of their hardware. In either case the result is the same: someone who quickly takes the opinion that Windows really is better than Linux.

As for me, I will do what I always do which is wait a few months for the dust to settle and for bugs to be patched and then make the transition. If at that time it doesn't fly, I try a different distro. I've learned in the last 15 years that it doesn't matter what software you use, you have to let it settle before committing - regardless of whether it's FOSS or commercial software.

---

### Post by azimuth on 2008-05-03
FredB's opinions are as valid as anyone's. I am inclined to believe him when he says he wouldn't be having the success he is, if he was overclocking or pushing and pulling all the software switchs that we are ALL tempted to play with after a new install. It would be as incorrect to assume everybody is creating their own problems as it would be to assume that nobody is.

---

### Post by sstusick on 2008-05-03
> **yimmmy said:**
> [...]i just recently upgraded my ubuntu gusty gibbon desktop to hardy <snip>[...]:lolflag:

---

### Post by diaz028 on 2008-05-03
Works fine here, actually works better than last two dists. Gutsy and Feisty... for me anyways. I find things to work so much smoother and less crap to do to get stuff working.

-D

---

### Post by diaz028 on 2008-05-03
> **diaz028 said:**
> Works fine here, actually works better than last two dists. Gutsy and Feisty... for me anyways. I find things to work so much smoother and less crap to do to get stuff working.

-D

BTW, I'm running a Q6600 @ 3.0Ghz and no issues here. Installed EVE Online and was resuming my game within 1 hour of fresh install. The upgrade from gutsy to me is seamless. I can say that I've had a lot less hiccups with hardy than I've had with both previous dists.

-D

---

### Post by mikeg113 on 2008-05-04
> **karellen said:**
> I've said it before and I'll say it again: there is absolutely no excuse for something that worked in a previous version of Ubuntu and in Hardy it doesn't. no "OEM fault for not releasing drivers for Linux", no "obscure bugs not reported in time", nothing. the past is the evidence

 I completely agree. I did a clean install on my laptop and no wireless, 3d or access to network shares. I worked on it for a week trying to correct the problems. Very frustrating.
 I have given up and reinstalled Gutsy on my laptop. I wouldn't say Hardy is a failure of Vista proportions but it's not as good as Edgy, Feisty or Gutsy in my experience.

---

### Post by MasterNetra on 2008-05-04
Why not try Kubuntu? :p What i find ironic is that i initially fresh installed Ubuntu (Hardy) but switched to Kubuntu (Hardy) (Installed Kde + Kubuntu Components and removed Gnome + Ubuntu. Save for the Kernal... I didn't dare touch that >.>) and ironically enough Kubuntu runs better and faster... 

fyi anyone know the components off hand that seperate a Kubuntu and a Kubuntu 64bit?

---

### Post by gwenn on 2008-05-04
Intel(R)Core(TM)2 CPU 4300 @1.80G
Invidia GeForce 7300 SE/7200 GS
ASUS P5K
ubuntu hardy.Everything works fine.

---

### Post by s0ylent green is pe0ple on 2008-05-04
yeh works fine for me too...
i did have some problems with 7.10 but its all good now out of the last bunch of distros i have tried (not just ubuntu ) 8.04 has worked best...

hardware: asus p5-e, c2d e8200, 4GB ocz pc2-6400, seagate 7200.11 1TB, seagate 7200.10 160GB, samsung hd501lj 500GB, antec 900, pny nvidia 7600gt, zalman cnp9500led, samsung syncmaster 2232bw

---

### Post by h4mx0r on 2008-05-04
I noticed during beta that a lot of things weren't being well tested (seemed like they were working on things backwards). But there were a lot of new features and bonus content on the cds to make things more efficient. Overall I think things are going good and should expect a few quick fix updates and revisions in next release.

---

### Post by s0ylent green is pe0ple on 2008-05-04
actually now i think about it i had some problems installing, i had to hit "retry" for some parts but once it was installed it has worked fine, i've not had any of the sound problems i had with 7.10 but to be fair i'm using a different sound card now, so thats something

---

### Post by nowshining on 2008-05-04
when i used the 2.6.24 kernels everything worked for me just dandy (on Gutsy) except for POSE apps taking up a lot of CPU and I think I found a way to re-gain Control :P incase of course it happens again or something I did in sysctl helped, anyway I compile & install my own custom kernels anyway. :)

right now i'm running 2.6.25.1

You guys do know that Ubuntu patches the kernel to bits with it's own crud.

---

### Post by imT on 2008-05-04
:lolflag: in october with Intrepid Ibex we'll gonna hear the same things, that hardy was better, "i better stick with hardy cus is LTS" and many, many other comments like this.

---

### Post by nowshining on 2008-05-04
lol IImT

ubuntu is LTS but Kubuntu is not, unless they changed it from last I heard.

---

### Post by dtrask on 2008-05-04
System 76 Darter Ultra 2
running Hardy 64 bit

runs fine...if not faster...only issue is the power meter/management, but that was an issue in Gutsy too.:guitar:

---

### Post by Mantorp on 2008-05-04
> **imT said:**
> :lolflag: in october with Intrepid Ibex we'll gonna hear the same things, that hardy was better, "i better stick with hardy cus is LTS" and many, many other comments like this.

fully agree with you! For now this release is cool, but I exspect some updates very soon.

---

### Post by s0ylent green is pe0ple on 2008-05-04
> **imT said:**
> :lolflag: in october with Intrepid Ibex we'll gonna hear the same things, that hardy was better, "i better stick with hardy cus is LTS" and many, many other comments like this.

yeh its true, its the same thing every time lol

---

### Post by roderick on 2008-05-04
> **nowshining said:**
> lol IImT

ubuntu is LTS but Kubuntu is not, unless they changed it from last I heard.

It is indeed LTS, but only the flavor with KDE 3.5.9. There is an alternate with KDE 4.0, which is not LTS.

---

### Post by DMK62 on 2008-05-04
The KDE 3.5.9 version of Kubuntu is not a LTS release. It is only supported for 18 months. It would not make sense to provide support for 3 years for a kde 3.x based release when KDE will have moved fully over to 4.x well before those 3 years.

Dale

---

### Post by roderick on 2008-05-04
> **DMK62 said:**
> The KDE 3.5.9 version of Kubuntu is not a LTS release. It is only supported for 18 months. It would not make sense to provide support for 3 years for a kde 3.x based release when KDE will have moved fully over to 4.x well before those 3 years.

Dale

I stand corrected. :)

---

### Post by DMK62 on 2008-05-04
Well hopefully a stable and full featured version of kde 4 will be out before those 3 years are up lol. I did try running it alongside 3 but it still needed a lot of work. I will be installing the kde 3.5.9 version of 8.04 next week and seeing that a couple of the previous versions of Kubuntu required me to become very familiar with kde I don't foresee any major hassles.

On a lighter note...  Would linux be any fun without bugs in it ? Without those bugs would you have made yourself learn how to use the terminal ? I have learned more about linux during those moments of crisis than during regular use lol.

Dale

---

### Post by VanCardboardbox on 2008-05-05
For me it was 7.10 that locked up relentlessly.

I installed 7.10 on a Dell Latitude D620 laptop as a dual boot with XPpro in order to check out Ubuntu. The OS was not at all stable on that machine. Suffered many lock-ups (which appeared to be related to an ATI video card/driver issue) and I could not for the life of me get wireless networking to function despite the wealth of info in the forums. 

Wiped clean and installed 8.04 and what a difference! No lock-ups, ATI driver is working great, and wireless worked from the first try. Sound, printing, and USB all work correctly. It even recognizes my camera and audio players. I was so impressed that I installed 8.04 on my main desktop box (Intel Dual 2.GHz, 2GB RAM, Nvidia GeForce 7100) and likewise is running smoothly. Count me among those who are finding Hardy to be solid.

---

### Post by revelationman on 2008-05-05
Sadly if you were to review all the posts here and online you will find Hardy to be a major disappointment.

I have given up on hardy on my laptop due to the constant freezing, i tried everything look at everything, then there was the hard drive issue. I am now back to Windows XP and everything is fine.

Not giving up I installed Hardy on my Compaq Deskpro C733 512 ram 64 Meg Nvida Video Card, it ran well with 7.10 no issues so I did a clean install of Hardy.

Well what happens it goes grey then slow then reboots lol  and this is with a NVIDA card Maxtor hardrive come on .

There is some of you that have had no issues I find that very hard to believe to be honest. I know some of you here think that Ubuntu and Linux is unfalable but this is load of crap. 

I will stick to my guns on this I feel that Hardy was forced out to early by the higher ups at Ubuntu. Hardy in my mind needed more development and testing. 

On the plus side I do like Ubuntu very much and I am not giving  up on it.

I think the next release in October I believe will correct these issue's well I hope.

So is Hardy the worst Ubuntu the answer is yes but I feel there is potential for Hardy to be the best Linux distro but there is loads of work to be done. 

:guitar:

---

### Post by Magnes on 2008-05-05
I had problems with rt61 on newly upgraded to 8.04 Ubuntu, but they are gone now after updating kernel and stuff to version -17.

---

### Post by Synkboy on 2008-05-05
> **adityakavoor said:**
> I agree:mad:

I upgraded from a perfectly working AMD 64 version of Gutsy(which was working perfectly), and now none of the extensions I had for Firefox are working, and I cannot get flv to play(Youtube etc), how I wish I could just rollback to the previous version:(

---

### Post by SneakyWho_am_i on 2008-05-05
I had my biggest problems in Gutsy. I've drifted back and forth between Linux and Windows for a long time. I'd always been far better with Windows (and DOS!!) than I had been with Linux. Red Hat, Xandros (or Redmond Linux, whatever), Knoppix, Mandrake (which I bought. In a box. With printed manuals!), briefly even Mandriva..!

I liked Windows 200 best of Windows's, too :)

My lockups were all experienced on either a 32 bit AMD Athlon XP 3000+ or a 2.8Ghz Celeron.

Mandriva crashed CONSTANTLY, I couldn't work it out. I tried every combination of hardware and software I had access to, and couldn't get it to do its thing.
Got a new machine with Windows preinstalled, and stuck with that for .... I can't remember, sic months? IT had these random lockups too, in Windows! Well, eventually they settled down :)
But I got frustrated with:
- restarting my computer on updates... A text file with a copyright notice in it is updated - which hasn't been accessed even once since install - and for some reason I need to restart the computer to complete the update process. And it NAGS (by the way, you can fix that in the management console)...
- windows stealing focus
- maxed out cpu use
- Having to choose between Xampp and IIS
- Firefox runs slowly
- IE runs REALLY SLOWLY (who the heck uses IE anyway? most people must be living under rocks :()
- Blender runs slowly
- Merc.... no, all my favourite apps... slowly. Armagetron under explorer 57 frames per second. Under X, never below 150, sometimes as high as 800, you better believe it (maybe some frames go to /dev/null? I mean, I don't think my screen can even update that fast...)

So I was despairing and going to give up on Ubuntu [Gutsy] when it started crashing and burning like Windows had.

**my memory was stuffed**
Root of my problems all along.
I'd done the first few memory tests in memtest86 and they'd been fine. I thought that that was enough. I was wrong. If I just take care of that, I'm fine. RAM, RAM, RAM.
It was my undoing on so many days.
My RAM surely can't be faulty? I bought it in a store, a reputable one! New, in box! It was the fastest RAM in the store!?
Well yes. The ram is the problem.
(install badram!)

since i've realised this, hardy has been a beautiful dream. i think that if i go back and install a fresh copy of hardy in 3 months time, it will be perfect and practically unbreakable. the guy who said you should hesitate to upgrade was absolutely right.
I hunger for all the bleeding edge stuff. I don't need it, some would call me foolish. Slightly older releases are **probably** a lot more stable....
....
.... but for me, once I fix the problems with my hardware, Hardy is a thousand times more dependable than Windows.

Why does Wiindows carry so much bloat? Turns out that much of it is for:
- compatability (with old releases of Windows)
- to try to work with dodgy or unknown hardware
- to prevent or work around user error

ironically the things that make it more stable can sometimes make it less stable, and a lot less pleasant to use.
I haven't read the original post in this thread, and I've completely ignored almost every page, but if you're reading my post and still awake, here it is in a nutshell:
- windows is probably going to treat you every bit as bad as linux if you're having trouble (unless your system is definitely in pristine condition and you are a veteran Windows user)
- BE EXTREMELY PARANOID ABOUT THE HEALTH OF EVERY PIECE OF HARDWARE YOU OWN, whenever your computer starts playing up. Investigating will seem like a huge waste of time and effort, but trust me, if you find something, it will TOTALLY pay off.

my two cents
PS all of a sudden i can't read the buttons, which one submits? i'm looking at white text on an almost white background...

---

### Post by Delever on 2008-05-05
How many people  fount their lockups fixed after recent few updates?

---

### Post by roderick on 2008-05-05
> **Synkboy said:**
> I upgraded from a perfectly working AMD 64 version of Gutsy(which was working perfectly), and now none of the extensions I had for Firefox are working, and I cannot get flv to play(Youtube etc), how I wish I could just rollback to the previous version:(

Install firefox-2 which should trigger uninstalling firefox-3 and you should be back in business.

firefox-3 still has some work, and perhaps it was a bit ambitious to force firefox-3 on users at this time.

---

### Post by The_Boot on 2008-05-05
I've yet to have a problem with Xubuntu, are people having problems with just Ubuntu, or all Ubuntu derivatives? I've tried it on a full range of hardware configurations.

---

### Post by s0ylent green is pe0ple on 2008-05-05
> **Delever said:**
> How many people  fount their lockups fixed after recent few updates?

zero so far....
(not tempting fate i hope :lolflag: )

---

### Post by joeschmit123 on 2008-05-05
Daily lockups on both Server and Desktop version.

Linux is better, because ....  ????

Which version of Ubuntu is most stable?  
I know  all the bells and whistles don't work in Linux so I don't even expect it.  I just want some stable.

---

### Post by wyth on 2008-05-05
I didn't want to wade through 32 pages to find out if someone just asked this simple question, because after the first few pages, it was clear it hadn't yet been raised:

If this is a kernel issue, why are people blaming Hardy?

As I understand it, some of these kernel lock-up issues aren't specific to any particular distro.  

I've not had a single lock-up in over a month on 8.04 (since beta).  I've been using the generic kernel.

Are people distinguishing between the kernel and Ubuntu itself?

---

### Post by Geekkit on 2008-05-05
> **wyth said:**
> Are people distinguishing between the kernel and Ubuntu itself?

Don't have to: [http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

### Post by roderick on 2008-05-05
From what I am reading, the lockups appear to be related to graphics.

I would first suggest people disable compiz, and see if the problem resolves itself.

As a second test, I see people seem to meantion Firefox 3 and possibly in combination with Flash. Any of the mozilla based browsers use xulrunner, I believe, and there was a recent update for that. It could be related (from what I have read on the bug reports). So, get the updates and try Firefox again. If problems persist, try other browsers (e.g. downgrade to FF2 or use konqueror, opera, etc).

Finally, some people have reported issues with GL screensavers. Try disabling the screensaver or choosing one of the non opengl ones and see if it resolves.

I also do not remember seeing any specific reports with Intel graphics (though could be wrong). There are apparently some ATI regressions which have popped up.

So, to sum up, it seems the issues are display related. To verify the entire system is not locked up, you can try some tricks and see if it is truly the display.

For example, does CTRL+ALT+BACKSPACE work? Can you CTRL+ALT+F1 to the first TTY? If so, then it's graphics related (most likely).

In any case, reporting the symptoms and what appears to cause the problem should be posted to Lanchpad to help diagnose the problem.

My system here is 100% working, though I do not have a screensaver enabled, and I have compiz disabled. I have an Intel 945GM. I can successfully play 3D games without lockup, both native (Neverwinter Nights) and via wine (Dungeon Siege II).

---

### Post by siretfel on 2008-05-05
I was about to post a question asking why is my notebook running like an old, rusted, steam train now that i have Hardy, when i found this thread.
Seriously with or without compiz, with or without firefox 3, i have a major problem with hardy!
My notebook is slow, 'heavy',it takes time to open applications, no question about watching videos,I cant listen to internet radio when i'm browsing cause rythmbox stucks for no reason.
With Gutsy everything worked like clock!With compiz enabled, full graphical effets,i mean i literaly pushed my notebook to the limit with Gutsy and it was AMAZING.
Hardy...naaah
I'm going back to Gutsy till something better comes on.
Hope everything goes ok with hardy.Till then i'll 'rip'out Gutsys' guts hehe.

---

### Post by roderick on 2008-05-05
> **siretfel said:**
> I was about to post a question asking why is my notebook running like an old, rusted, steam train now that i have Hardy, when i found this thread.

Sounds like either Direct Rendering is not working, or you have a possible driver issue (hard drive possibly).

Can you check and see if Direct Rendering is working (glxinfo and look for Direct Rendering: Yes). If it is not, everything will appear slow, as rendering is done in software then.

---

### Post by Ekeluo on 2008-05-05
I seriously don't think the lock ups has anything to with (on my laptop) it actually crashes least when I'm surfing. It does lock up regularly once an opengl program opens (esp. elisa), all others in the middle of a compiz animation. I think mine has to do with libgl mesa dri or something along that line of thinking. I'll wait to see what is done.

---

### Post by siretfel on 2008-05-05
> **roderick said:**
> Sounds like either Direct Rendering is not working, or you have a possible driver issue (hard drive possibly).

Can you check and see if Direct Rendering is working (glxinfo and look for Direct Rendering: Yes). If it is not, everything will appear slow, as rendering is done in software then.

Damn!You're right!Check this:
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

How do I change this?

(thanks for the advice)

---

### Post by darrenn on 2008-05-05
I have the same laptop as Jim March and I have had ONE hardlockup. Hardy is working perfectly for me. I think his problem might be hardware related. Because I am not having any of the problems he is having.

---

### Post by NotTheMessiah on 2008-05-05
Well like clock work :) there are updates now for Evolution and probably the bug that I've mentioned a couple of times.

---

### Post by d_fiant_1 on 2008-05-05
I find hardy the most stable of the 3 Ubuntu versions I have used. I did a clean install...everything installed without a drama, unlike 7.10 and 7.04.

Compiz, AWN, Conky, Amarok, Kaffeine, VLC ATI Catalyst all run flawlessly.

It has been 10 days 21 hours and 1 minute since my last restart...the last 2 versions of Ubuntu needed a cold restart at least every 4th day if it made it that far.

I'm more than impressed with 8.04

---

### Post by VMC on 2008-05-05
> **d_fiant_1 said:**
> I find hardy the most stable of the 3 Ubuntu versions I have used. I did a clean install...everything installed without a drama, unlike 7.10 and 7.04.

Compiz, AWN, Conky, Amarok, Kaffeine, VLC ATI Catalyst all run flawlessly.

It has been 10 days 21 hours and 1 minute since my last restart...the last 2 versions of Ubuntu needed a cold restart at least every 4th day if it made it that far.

I'm more than impressed with 8.04

I couldn't agree more! I haven't tried ubuntu since 7.04. It has been a couple of years anyway. This new "Harty" release I tried thinking that in no time it will come all crashing down. To my surprise it has worked flawless! I mean I have no trouble whatsoever. 

Guess I'm lucky.:)

---

### Post by roderick on 2008-05-05
> **siretfel said:**
> Damn!You're right!Check this:
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

How do I change this?

(thanks for the advice)

Well, depending on what driver, video card, etc... PM me and I'll try and help. Otherwise, start a new thread and post your problem indicating your video card, output of glxinfo, /etc/X11/xorg.conf, etc.

---

### Post by metasolaris on 2008-05-06
> **VMC said:**
> I couldn't agree more! I haven't tried ubuntu since 7.04. It has been a couple of years anyway. This new "Harty" release I tried thinking that in no time it will come all crashing down. To my surprise it has worked flawless! I mean I have no trouble whatsoever. 

Guess I'm lucky.:)

I have a dual core amd64 and Hardy is 100%. Now, Firefox 3 is another matter,,,

---

### Post by joeschmit123 on 2008-05-06
Although many people are referring to the workstation, well, I do have a workstation that lockup constantly but that is a less of an issue for me.
My problem is the server.  I built a barebone server then added MailScanner, postfix, spamassassin, clamav, webmin.  I'll let the thing run for a while and then suddenly it won't respond to port 25 connection.  Need to reboot to get it back.  
Where can I get a previous version?  OR a stable version?

---

### Post by buntunub on 2008-05-06
> **joeschmit123 said:**
> Although many people are referring to the workstation, well, I do have a workstation that lockup constantly but that is a less of an issue for me.
My problem is the server.  I built a barebone server then added MailScanner, postfix, spamassassin, clamav, webmin.  I'll let the thing run for a while and then suddenly it won't respond to port 25 connection.  Need to reboot to get it back.  
Where can I get a previous version?  OR a stable version?

Perhaps you need to check your firewall settings? Hardy comes with a new firewall (ufw, I think), which is command line only.

Hardy comes with ALOT of underlying changes. These are changes in GNOME as well (2.22). These changes are all about security, networking, and virtualization support. This, of course, means that things work a bit differently than they did in Gutsy, and some things work completely different. Try to get an understanding of this, and your experience with Hardy will drastically improve, as has mine.

---

### Post by meho_r on 2008-05-06
Ah, I didn't have problems with Hardy till recent update (Evolution and more stuff, I don't remember what it was, but it had about 40 MB). Now I have lockups about 20 min. or half an hour after boot (seems random). Anybody have similar issue AFTER last update?

---

### Post by sports fan Matt on 2008-05-06
Ive read all these pages and im sorry, but this isnt ones personal whining station.  If you have problems, thats cool, but only in the last few pages, have I seen help.  There is a VERY simple solution which is to use Gutsy.  VERY SIMPLE! 

Just because hardy isnt stable for you, doesnt mean it MUST be used. And im sorry, but to quote the original post, "the worst ubuntu version yet", im sorry..ALL VERSIONS OF WINDOWS are much worse then ANY versions of Ubuntu! :) 

Now im going back to my day and not going to worry about these threads --Have a great day all! :)

---

### Post by karellen on 2008-05-06
> **joeschmit123 said:**
> Although many people are referring to the workstation, well, I do have a workstation that lockup constantly but that is a less of an issue for me.
My problem is the server.  I built a barebone server then added MailScanner, postfix, spamassassin, clamav, webmin.  I'll let the thing run for a while and then suddenly it won't respond to port 25 connection.  Need to reboot to get it back.  
Where can I get a previous version?  OR a stable version?

maybe for a server you should consider other distros - centos or debian stable - not too bleeding edge and more reliable

---

### Post by williswasabi on 2008-05-06
Kinda got bored reading through the 34 (!) pages of this thread, so maybe it's been covered. :)

This is not only the worst version of Ubuntu, it's the worst version of *Linux* I've used since kernel 0.97g or thereabouts in 1993-94. Linux used to freeze solid back then if you let it run overnight sometimes. Linux doesn't freeze. In the 14 years I've been using Linux, it hasn't happened since--until now. It freezes so hard the Caps-lock key won't change the light status. 

Worked great in a VMWare Fusion guest upgrade from Gutsy. My Via C3 home server freezes randomly in the boot process after upgrade. The C3 can't even get all the way through the 8.04 Live CD boot with all PCI cards pulled and even the hard drives disconnected. Hard freezes like this made me suspect hardware. Gutsy however is working just fine on it after a reinstall, as it always has.

Hardy just isn't all the way cooked. You figure a release labeled as LTS would be well-tested. Seriously, take a month or two next time like with 6.06 LTS. For the first time I'm glad I don't use Ubuntu on servers at work...

---

### Post by Gatemaze on 2008-05-06
> **williswasabi said:**
> 
Hardy just isn't all the way cooked. You figure a release labeled as LTS would be well-tested. Seriously, take a month or two next time like with 6.06 LTS. For the first time I'm glad I don't use Ubuntu on servers at work...

Yes sadly I have to agree on this. I also had the impression that an LTS version would be reliable and well tested as the time between the last (drake) and this (heron) would allow to focus on a reliable LTS version. The issue is that I was looking forward to heron as I am still running drake because I decided that it is easier to upgrade from LTS to LTS. Waiting two years would not really make a difference a couple more months for me. Considering that there are only two more months of support of the drake, I really hope the issue is fixed by then.

---

### Post by Rohen on 2008-05-06
Well.....  Unfortunatley I am re-installing Ubuntu Hardy Heron on my PC.  I have checked the Hash and and CD for errors and there are ZERO, NONE, Zilch...  If I come accross the lockups again then it is definitely a Hardware Problem.

Also, to elaborate on the subject... my CPU usage went crazy every once in a while as well!  So bad was it that I couldn't start any programs.

I am writing this from my sister's Labtop (Windows) :(

CROSSING MY FINGERS!!!

---

### Post by NotTheMessiah on 2008-05-06
> **Rohen said:**
> 
Also, to elaborate on the subject... my CPU usage went crazy every once in a while as well!  So bad was it that I couldn't start any programs.

I am writing this from my sister's Labtop (Windows) :(

CROSSING MY FINGERS!!!

That's the Evolution bug..... 100% cpu usage and then some. try the new updates..they seem to be working for me......for now

---

### Post by Babstar on 2008-05-06
**[B]Compiz is the culprit for me.**[/B]
Long story short.  Kubuntu 7.10 upgraded to 8.04. Upgrade nil problems, system ran nicely zero lockups or problems.
 After making my way through to page 33 of this thread I decided to find out if compiz is the causing problems as others speculate.  I install compiz and can now replicate the lockups others are seeing.  After opening and searching a 730 page pdf in acroread the display locked hard, mouse was still usable. I ssh'ed  in from another system, top showed compiz.real using about 90% cpu. I could not kill the process, a reboot & remove compiz and everything back to normal.
To all those who have the lockups, please download the kubuntu 8.04 live CD and try it  (compiz is not enabled) and see if fixes the lockups, report results.

Please please please do not bash Ubuntu.    Ubuntu is a community based project, it is free, it does not "owe' you.  Ubuntu can, and should have to face constructive criticism, but the title of this thread, and some posts along the way are plain nasty. Help by providing some basic diagnostic information, rather than bashing.

---

### Post by Rohen on 2008-05-06
All right so I've re-installed Hardy and so far (been up for 2 hours) I've had ZERO lock ups.

I'm using my Nvidia and with the graphics turned up and so far nothing.  If this good news is still good news by tomorrow then it must mean a:

1. Bad Installation from the beginning
2. Bad Upgrade to Heron
3. Both

Just my thoughts

:popcorn:

---

### Post by Ian Clark on 2008-05-06
> **fdimmling said:**
> Installed Hardy on an Acer 4652 LMi with 1GB RAM and Intel 940 Graphics. Works quite well except for ugly Chinese characters which is due to a font substitution problem. 
I had the weird Chinese issue, too but only in AbiWord.  Overall Chinese input and display have improved a lot.  On 7.10 I had mixed character display problems, whereas now all Chinese displays as one font in FF.  Also, the AbiWord issue can be resolved by going here: [http://abisource.com/wiki/Install_on_Ubuntu](http://abisource.com/wiki/Install_on_Ubuntu)

I have a machine that was put together by Chinese in 2004.  Lots of RAM and an intel 4 processor.  Hardy works great.  7.10 didn't have a good ATI driver and couldn't enable effects.  Hardy can enable effects now, and FF3 just rocks.

---

### Post by Cris(c) on 2008-05-06
Hi there...I'm a very new in this world of linux...I started with ubuntu gutsy and had a very pleaseant experience. However, when I updated to the kernel 2.6-24-16 my problems began. First, booting with this kernel is 24-16 is a random process: sometimes it does, but most of the times I get the following messages at the very beginning of the booting:

[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 12. 

Then, after 5-10 sec I get a message saying that he CPU#1 got stacked for more than 11 sec...from there nothing more. With the 2.6.24-17 is even worse: when I am able to boot I get no audio and no wireless! So far I've been using the 2.6.22-14 kernel (which works fine except that the headphone jack doesn't stop the speakers). 

I've tried all what I've found in different threads and nothing's worked so far. And also it seems and not the only one experience this problem ([http://ubuntuforums.org/showthread.php?t=768684](http://ubuntuforums.org/showthread.php?t=768684))...does anyone know how to work this out?

---

### Post by siretfel on 2008-05-07
Hi all,

I have to reconsider about hardy heron.
After some searching and after I destroyed some settings in my graph card i did a clean reinstallation of hardy last night.
The problem i had at first was extremely slow performance in my system.This was due to wrong drivers i used for my ati 9100 radeon graph card. After searching i found that i had to use the open source driver i found this guide to use compiz:
[http://ubuntuforums.org/showthread.php?t=764633&highlight=SKIP_CHECKS%3Dyes](http://ubuntuforums.org/showthread.php?t=764633&highlight=SKIP_CHECKS%3Dyes)

It worked excelently for me and not only hardy is performing like a bad *** in my laptop but it is working much more faster than Windows XP which i have as dual boot.

Now, i had also some problems with firefox 3.Since i browse alot, i needed my extentions.So i uninstalled it and installed firefox 2.
The problem was that i couldn't install add-ons.So after searching the forums i found that if i delete .mozilla folder in my user folder (.mozilla is hidden so you have to press ctrl+h to  show hidden files) and restart firefox everything works like a charm)
Another problem was java in firefox which i couldn't make it work.but, after searching again i found the solution.

finally...i followed this excelent guide
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
to make firefox streaming video like a charm!

So far after a few hours everything works e x a c t l y as i like to work: Fast,clean,easy,virus-free,spyware-free,and best of all.....TOTALLY FREE hahaha!

That's all folks!

---

### Post by hyper_ch on 2008-05-07
> **siretfel said:**
> Now, i had also some problems with firefox 3.Since i browse alot, i needed my extentions.So i uninstalled it and installed firefox 2.

The problem is that most extensions will run on FF 3 but that the internal version only goes to 2.x.

You can install the nightly tester tool ( [https://addons.mozilla.org/de/firefox/addon/1391](https://addons.mozilla.org/de/firefox/addon/1391) ) and it will make most addons running on FF3.

---

### Post by siretfel on 2008-05-07
> **hyper_ch said:**
> The problem is that most extensions will run on FF 3 but that the internal version only goes to 2.x.

You can install the nightly tester tool ( [https://addons.mozilla.org/de/firefox/addon/1391](https://addons.mozilla.org/de/firefox/addon/1391) ) and it will make most addons running on FF3.

Thanks for your suggestion!I didn't know that there was such a tool.I'll give it a try.

---

### Post by hyper_ch on 2008-05-07
didn't know so either until about a week ago someone suggested it in another thread ;)

---

### Post by buntunub on 2008-05-07
> **Babstar said:**
> [B][B]
Please please please do not bash Ubuntu.    Ubuntu is a community based project, it is free, it does not "owe' you.  Ubuntu can, and should have to face constructive criticism, but the title of this thread, and some posts along the way are plain nasty. Help by providing some basic diagnostic information, rather than bashing.

Gotta agree with this. I had ungodly horrid issues with Gutsy, all of which were downright irritating to have to deal with as a Linux newby. We (the average 'Buntu users) like to think that when Canonical does a release, that it will be trouble free, just like Vista was on its release day... :lolflag:

Well, the Open Source/Linux world just does not do things the same way folks. This is something one must come to terms with if you are going to continue to use Linux in general. You can pay for professional support from Canonical if your needs dictate, or you can seek Community support for your problems here or on IRC, but to do that, you must first be respectful, and be prepared to provide detailed data on your issue, so that people can actually try to help!

---

### Post by Caesum on 2008-05-07
Well, I've tried gutsy and now Heron. Both suffer total lockups. I can leave the machine on for hours and its fine but other times it'll lock up a few times within a couple of hours. Two things seem to bring this on rapidly - cpu intensive programs like factoring numbers and firefox. I can sometimes have a cpu intensive program running all night and its fine, or even two instances since this is a quad core cpu. Other times it will crash after a few hours. But often when i've got something intensive running it will crash after five minutes of using firefox. When I say total lockup the mouse stops working and the keyboard responds to nothing - even caps and num lock won't turn on/off. 

I read someone suggested disabling cupsd and cron which I tried but this had no affect. I've run the memory test all night and it showed up nothing as well. Looking through logs there are no entries prior to the lockups.

The machine is new, with gutsy the first os on it, which was wiped and reinstalled once because of the problems. I'm running 64-bit ubuntu and the only non-standard driver currently installed is the nvidia 169.12 driver for a GT8800 graphics card because the ubuntu drivers only work in low resolution with low refresh rates that give me migraines (even though the ubuntu loading screen seems to be in a higher res?)

After lockup I've checked CPU temps and they're 39 degrees which is well within expected.

So..... I'm totally stuck now.

---

### Post by buntunub on 2008-05-07
> **Caesum said:**
> Well, I've tried gutsy and now Heron. Both suffer total lockups. I can leave the machine on for hours and its fine but other times it'll lock up a few times within a couple of hours. Two things seem to bring this on rapidly - cpu intensive programs like factoring numbers and firefox. I can sometimes have a cpu intensive program running all night and its fine, or even two instances since this is a quad core cpu. Other times it will crash after a few hours. But often when i've got something intensive running it will crash after five minutes of using firefox. When I say total lockup the mouse stops working and the keyboard responds to nothing - even caps and num lock won't turn on/off. 

I read someone suggested disabling cupsd and cron which I tried but this had no affect. I've run the memory test all night and it showed up nothing as well. Looking through logs there are no entries prior to the lockups.

The machine is new, with gutsy the first os on it, which was wiped and reinstalled once because of the problems. I'm running 64-bit ubuntu and the only non-standard driver currently installed is the nvidia 169.12 driver for a GT8800 graphics card because the ubuntu drivers only work in low resolution with low refresh rates that give me migraines (even though the ubuntu loading screen seems to be in a higher res?)

After lockup I've checked CPU temps and they're 39 degrees which is well within expected.

So..... I'm totally stuck now.

1. The Ubuntu stock 169.12 Nvidia driver works just fine. Try changing your resolutions from within the nvidia-settings utility (Admin>nvidia settings), or, [PHP]$sudo nvidia-settings &[/PHP]

Changing settings this way, then save xorg.conf when your done. The GNOME Resolution app will reflect the changes when your done. As far as the lockups, the best way to find out whats going on under the hood when this happens is, [PHP]$cat /var/log/messages | less[/PHP]

Sift through that immediately after reboots on lockups and see if you can find error messages, or things that point to something going amiss. Your running a quad core and what?.. SLI'd 8800's? There could very well be a hardware issue going on here, and that would be my first guess, as Hardy tends to run pretty solid on my rig which is almost identical (6 days uptime with zero, nada, zilch, lockups).

---

### Post by Caesum on 2008-05-07
Well, looked through all the logs and there is just nothing before the crashes like this:

```

May  7 16:58:44 darkstar -- MARK --
May  7 17:18:44 darkstar -- MARK --
May  7 17:36:03 darkstar syslogd 1.5.0#1ubuntu1: restart.

```

the crash above happened at 17:35 or so.... nothing in the log for the previous 18 minutes.

The only lines which look strange when booting are:

```

May  7 17:36:03 darkstar kernel: [   27.224945] pnpacpi: exceeded the max number of mem resources: 12
May  7 17:36:03 darkstar kernel: [   27.225043] pnp: PnP ACPI: found 15 devices
May  7 17:36:03 darkstar kernel: [   27.225045] ACPI: ACPI bus type pnp unregistered
May  7 17:36:03 darkstar kernel: [   27.225213] PCI: Using ACPI for IRQ routing
May  7 17:36:03 darkstar kernel: [   27.225214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

...
May  7 17:36:03 darkstar kernel: [   31.460188] Driver 'sd' needs updating - please use bus_type methods
...
May  7 17:36:03 darkstar kernel: [   31.460345]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

```

Oh, and it's just one 8800, maybe two one day.....

---

### Post by bdoe on 2008-05-07
Well, so far I've been running Hardy on my laptop, and the only notable problem I've had with it is with hibernation. When I tried hibernating, the system complained about there not being enough swap space, and then hung. One of these times I'll get around to resizing my partitions, but for now, I'm still pretty content with how things are working.

I use Thunderbird instead of Evolution for my e-mail, and I've downgraded FF3 to FF2 due to incompatibilities with FF3 and my online college.

Perhaps posting my hardware might help pinpoint hardware problems others are having, so here goes:

Basic:
HP Pavilion dv9830us laptop
Intel Centrino (core2duo) at 1.83GHz
4GB PC2-5400 DDR2 memory
300GB hard drive
nVidea GeForce 8600M GS (512MB), using restricted drivers
Intel Pro/Wireless 4965AGN
Realtek HD audio

lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Hope that helps some people out there.

---

### Post by heartburnkid on 2008-05-07
This is exactly why I live by the "Early adopter" rule -- namely, don't be one.

Wait 2 months to install any major software release, and 6 months for any hardware.  By then, they've worked out the kinks.

Of course, I broke this rule for Ubuntu, but Hardy's worked out fine for me so far (with the exception of Compiz occasionally deciding it doesn't want to draw window borders, but that seems to have cleared up with the last round of patches).  Guess I'm just lucky.

---

### Post by buntunub on 2008-05-07
> **Caesum said:**
> Well, looked through all the logs and there is just nothing before the crashes like this:

```

May  7 16:58:44 darkstar -- MARK --
May  7 17:18:44 darkstar -- MARK --
May  7 17:36:03 darkstar syslogd 1.5.0#1ubuntu1: restart.

```

the crash above happened at 17:35 or so.... nothing in the log for the previous 18 minutes.

The only lines which look strange when booting are:

```

May  7 17:36:03 darkstar kernel: [   27.224945] pnpacpi: exceeded the max number of mem resources: 12
May  7 17:36:03 darkstar kernel: [   27.225043] pnp: PnP ACPI: found 15 devices
May  7 17:36:03 darkstar kernel: [   27.225045] ACPI: ACPI bus type pnp unregistered
May  7 17:36:03 darkstar kernel: [   27.225213] PCI: Using ACPI for IRQ routing
May  7 17:36:03 darkstar kernel: [   27.225214] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

...
May  7 17:36:03 darkstar kernel: [   31.460188] Driver 'sd' needs updating - please use bus_type methods
...
May  7 17:36:03 darkstar kernel: [   31.460345]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

```

Oh, and it's just one 8800, maybe two one day.....


Try booting with -noapic-nolapic and see if that helps.

---

### Post by nick09 on 2008-05-07
Bah Hardy is working like a madman on my parent's PC(fresh install).

I really don't have many problems.

---

### Post by squidmaster on 2008-05-07
Oh man.... I've been an avid ubuntu user for nearly 3 years now and have NEVER been this disappointed in a relase until Hardy.
By far, agreeably, the WORST release to date.
Slower than vista on 256mb ram and more lock ups and random errors than windows ME.

---

### Post by Rohen on 2008-05-07
> **GTengineer said:**
> Please report back if you find Firefox to be indeed the culprit of the lock ups. I cannot seem to find a reason for mine since it crashes very randomly.

All right so what I did is that I re-installed Hardy completely.  I checked the Hash for errors and then the CD for errors and there are ZERO.

I am now a happy Ubuntu user once again.  HOWEVER, right when I installed Java I ran into one small lock up that lasted for a second.  Then later on I had another one that lasted a second as well.

My Comp has locked up 4-5 times so far (it's been a day) and it's only been for a second each.  So... the bright side is that I'm not experiencing those ugly lock ups for 10-20 secs anymore.  So what's causing this?

I can safely say that it had something to do with a bad upgrade, and it has to do with Java.

My suggestion: Uninstall Java... see if that helps somewhat.
My second suggestion: Re-install Ubuntu.

---

### Post by VMC on 2008-05-07
I keep hearing complaints regarding not just ubuntu, but Linux in general as not working correctly or this distro's bad or that one, when in fact I don't hear anyone complaining and saying instead, this computer, this laptop doesn't work with Linux!

Most all computers were built for Windows, period! It's a wonder and a great effort to the devs that Linux works as good as it does given the upstream battle. 

Instead of complaining to the OS, start complaining to the hardware manufacturers.
Vista has proven my theory on that one.

Ubuntu isn't at fault or Linux in general, Toshiba, HP, Gateway, etc, have some if not most responsibility. The hardware manufacturers are getting off easy on this one!

---

### Post by Astrolabe on 2008-05-07
Hmm - I have installed Hardy on to four machines I am running on a home network (albeit 2 of them running Hardy Mythbuntu: back and front end) and while I too am being plagued by lockups, it is only on one machine. The others run perfectly.

As with others who have posted here, there is nothing in the logs to indicate what might be going wrong on this one machine. Can anyone suggest where else I might look or if there is a way to increase the level of logging? (obviously temporarily as I don't want to blow the disk with massive log files).

For what it is worth, I think the team have done a brilliant job with this release and perhaps we need to remind ourselves that it isn't commercial software.

---

### Post by NotTheMessiah on 2008-05-07
I am happy to report that after two batches of updates i haven't experienced any lockups on both the lappy and desktop.Very happy now:) ecstatic actually

ooppss just realized that my openoffice icons are gone(known issue with oo)
but i don't care :)

---

### Post by erginemr on 2008-05-08
In my third attempt to install Hardy, I also had two or three hard lock-ups, and I believed the lock-ups were originated by Compiz vs. video card. 

But for me too, it started to work like a clock after the last wave of updates, which presumably addressed important parts of the Gnome infrastructure. So, I suggest everyone having lock-up problems to update and test run their system for a while.

---

### Post by Geekkit on 2008-05-08
My update (although probably should be another post) ...

Installed it on a relatively new system (P4, 3 GHz, 1 GB RAM onboard Intel vid card), and it seemed to run without a glitches in the 45 minutes I was running. Did install Java, big scary closed source CODECs, no breaky, breaky. (Yes, I did break my own rule of not adopting early but I have a client that needs a server and I needed to see if I should go with 7.10 or 8.04).

Also talked with another fellow who installed on a laptop who has not had problems. So from my end I've seen two laptop problems, one laptop success and one desktop success.

Disappointments for me:
1.) They apparently have removed the Nautilus undo/redo feature (and the quick blurb about it in the "what's new" section on the main site). I was really looking forward to this which would have made Nautilus much more usable (be forgiving of users). This was a 5/10 thumbs down.
2.) Ubuntu 8.04 now uses up over two times the amount of memory that Ubuntu 7.10 uses. 8.04 even without tracker and Compiz sits at a hefty 400 MB. When I run 7.10 (without tracker and Compiz), I sit at a lean 130 - 170 MB RAM. To me that's a major disappointment since two of my old home systems only have 512 MB RAM. I know, I know, GET MORE RAM right? That's not the point. One of the reasons that pulled me over to Ubuntu was how lean it ran: it was a major selling point for me because I wanted to maximize the life of my hardware a year or so more. For my old systems I'll continue to use 7.10 but for my office system (which is newer), I'll give 8.04 a go. This was a 8/10 thumbs down.
3.) At system shutdown I see shutdown info: I don't want to see this at shutdown. If I want that information, I'll check the logs thank you. 3/10 thumbs down.
4.) How many releases are we going to see with no default document templates or a quick UI approach to adding them? I'm talking about the right click -> create new document. How about a OO presentation? OO document? OO spreadsheet? GIMP image? XHTML document? C/C++ file? Python file? I can add it but this should be there ... in the very least the OO documents. 4/10 thumbs down.


Likes:
1.) I did notice a significant speed different with 8.04 and FF 3. For me it was very much noticeable. I noticed that when I opened PDF files, ODT files, MP3s, assorted videos, and did compiling, the system seemed much more peppy. FF 3 was a world of difference faster than FF 2 although I'm not sure I like their URL field at the top with the rich text: makes it hard to focus on the URL itself. Both of these 8/10 thumbs up.
2.) I liked the temperature attached to the system clock. 6/10 thumbs up (now I can remove the plugin from FF)
3.) I checked the kernel logs on my office computer and saw no funny business. This is a good sign. 8/10 thumbs up.
4.) A bit torrent client that isn't a piece of crud! Finally! 8/10 thumbs up.
5.) FF 3. Having said that I probably shouldn't ... I used it for a few of minutes only. Still ... 9/10 yay!

Overall I'm going to have to stick with 7.10 at home (my wife needs Windows XP for accounting S/W so she gets the newer computer :/ ) because of 8.04 being similar Vista in the respect it's becoming memory hog (2x the amount from one release to another? What's next? 1 GB for 8.10?). Office system can stay with 8.04 as long as it keeps me productive with no crashes. For me I'm willing to live without the weather/temperature, fancy Python apps, Compiz, and hoo-has as long as I can remain productive ... like how 7.10 has allowed me to be for the better part of this year.

---

### Post by spiner on 2008-05-08
Pentium D 3.4 GHz, 1 GB RAM, NVIDIA Geforce 7300 GT: at the moment Ubuntu 8.04 is the most stable distro I was able to install on this machine.
Just some freezes before upgrading to NVIDIA-provided graphic drivers.

Completely satisfied up to now.

Rgs.

/Spiner

---

### Post by km6xz on 2008-05-08
As a new user I was very concerned with this thread but my ACER TravelMate 4230 laptop has worked perfectly since I installed H.H. 8.04 last week. I  installed Ubuntu on a fresh hard drive that I can swap out with the original that has Vista Ultimate OS on it. All the hardware except the built-in camera works, in fact the sound card works better than under Vista. FireFox runs noticeably faster.
As a first time user, I can say this has been as simple as pleasurable....not problems at all.

Now if I can learn how to run a few web dev applications on Ubuntu, I can dump MS Vista.  
Stan

---

### Post by hyper_ch on 2008-05-08
km:

what webdev apps?

---

### Post by Delever on 2008-05-08
> **NotTheMessiah said:**
> 
ooppss just realized that my openoffice icons are gone(known issue with oo)
but i don't care :)

Select Human theme in open office preferences.

---

### Post by kolslorr on 2008-05-08
MY harddisk is going to wastebin as i have to hard reboot with 8.04 EVERYDAY.

WAKE UP UBUNTU TEAM!

---

### Post by hyper_ch on 2008-05-08
> **kolslorr said:**
> MY harddisk is going to wastebin as i have to hard reboot with 8.04 EVERYDAY.

WAKE UP UBUNTU TEAM!

See, that helps the devs not at all as you don't give any information...

---

### Post by sharkbite1414 on 2008-05-08
Hey, has anyone tried check their disk for errors? 
My Ubuntu 8.04 64-bit edition work fine execpt I can't use desktop effects (see link below for full explenation)
 [http://ubuntuforums.org/showthread.php?t=782506](http://ubuntuforums.org/showthread.php?t=782506)

---

### Post by dlmoak on 2008-05-08
I'm a new user - just started with Gutsy about 6 weeks ago.  I built a new computer and installed Hardy on it when the computer arrived (about two weeks ago).  So far I have had no problems other than getting my scanner to work.  All my other hardware was recognized and the system works well and very fast.  Firefox has timed out for 15 seconds or so twice.

---

### Post by lespaul_rentals on 2008-05-08
And thus ends my recommendations of Ubuntu to people interested in Linux.

I love Fiesty Fawn and to this day still use it on occassion.  It's stable, it has some great features, and is a great distro.  But Gutsy annoyed the heck out of me, and now Hardy is a failure.

What is going wrong here?  Why is the Ubuntu development team using hasty patches and horrible code?  Why is the primary web browser Firefox 3, a beta version?  I know that a lot of Ubuntu users are Firefox fanboys and will do anything to kiss the feet of that (IMO) weak browser, but come on.

If you look at a distro like Slackware, you think stability.  Why is it so stable?  It's because it uses rock-solid, secure versions of software.  The Slackware team isn't going to throw in beta software in hopes of arousing fanboys.  As far as I know, Slackware 12 still uses the old version of Apache in its default install.  Slackware also has fantastic hardware support, and it keeps getting better and better instead of fluctuating like Ubuntu.

And heck, look at Debian.  Debian is stable and secure because the Debian team is far more strict about what code they use.  They don't just slap in some code that just happened to work.

Come on, guys.  Theo de Raadt is exactly correct when he attacks Linux for its sloppy way of development.  *They have the same rapid development cycle [as Microsoft], which leads to crap.*

---

### Post by roderick on 2008-05-08
Obviously, the Firefox 2 vs 3 is problematic for most. For me, it has not been an issue as I use konqueror (kubuntu).

If you are unhappy with Firefox 3 try either downgrading to version 2 temporarily (until FF 3 is not beta) or use the native WM browser.

Other issues people have are likely compiz related. I believe it was a bit too early to make compiz enabled by default. I suggest people try disabling compiz and see if that rectifies their issues.

Other than that, the rest is rock solid for a vast majority of users. The minority who have problems with drivers and hardware, while unfortunate, is a simple reality. Not all hardware is available for developers to test all configurations. With all the bug reports coming in though, you can expect these things will resolve themselves over time.

I really enjoy the majority of changes in Gutsy and now Hardy. I have only had minor issues, all during the alpha/beta testing.

---

### Post by heartburnkid on 2008-05-08
You know, there's a whole lot of overreaction in this thread.  Stuff along the lines of "OMG Ubuntu sux now!" or "I'm never recommending Ubuntu again!"  Let me ask you something -- and I mean ALL of you:

When was the last time you used Version X.0 of a software product -- ANY product, open-source or proprietary -- and it worked flawlessly on launch day?

Because honestly?  I don't think I ever have.  Because, in the diverse world of computing, it's damn near impossible to do.  The folks at Canonical, or *anywhere* for that matter, simply can't test their products against every single combination of hardware out there.  They can do their best in the beta period, but once something goes into wide release, new bugs and problems will be found, and old bugs and problems that were thought minor will be compounded.  It's simply the nature of the beast.

The way I see it, you guys have a couple of choices.  If you want to play on the bleeding edge, you can deal with the issues that come with the territory, and when you encounter said issues, submit clear and concise bug reports to the good folks at Canonical who gave us this marvelous thing *for free*.  Heck, it's open source; if you've got the skills, make a fix and send it to them!  On the other hand, if you'd rather not deal with the problems inherent in being an early adopter, *then don't be an early adopter*.  Go back to 7.10, or whatever you were using before, and give them 2-3 months to work the kinks out.  Either way, all this hysterical yammering gets us absolutely nowhere.

---

### Post by bigwrestlerguy on 2008-05-08
[FONT="Comic Sans MS"]This is my first experience using Ubuntu on my own machine. I had a bit of time on school computer labs using 7.10, and I liked it so much I had to put it on the home compy. However, 8.04 has been crashing worse than XP has ever done. I think I might have to install the 7.10 to give it a fair shot... But I'm actually tempted to put vista back on...  [/FONT]

---

### Post by strikeback03 on 2008-05-08
I didn't read this whole thread, but for me every version of Ubuntu I have used (since 6.10) has required new kernel switches to run stably on my desktop.  I'm guessing it's related to my motherboard (Foxconn P965) being not so mainstream.  I too had random freezes which left no log and required a hard reboot.  I finally got 7.10 dead stable (with all_generic_ide, noapic, nolapic, irqpoll, and ht=on), so I'm on the fence whether to go to 8.04 or not.  I'd like ESPN video to work (does in 8.04, not 7.10), but it has to be stable and I need FLV support, so if I can't get that for 64bit I won't bother upgrading yet.  I had to update my BIOS just to get the LiveCD to boot.

OTOH, my T43 laptop has worked perfectly and immediately with each version, as have the computers at work I have installed on, including a DFI P965 board.  My point is that I'm not sure what they change, but unless they happen to be using pretty much exactly your hardware, bugs can and do slip through.

---

### Post by km6xz on 2008-05-09
> **hyper_ch said:**
> km:

what webdev apps?
Hi hyper_ch
I currently use Dreamweaver CS3 and CodeCharge Studio 4.0 to develop my web sites using php and MySql.
The most important application for me is CodeCharge Studio and if there was some way to run it on Ubuntu I would be set. 

I just like the look and feel, the community and the philosophy of this whole project.  I should spend some time needed to learn te OS as much a I know the Windows/Dos side but having such an easy transition with 8.04 it is an option and not an absolute requirement. I plan on switching my entire office over from 4 different flavors of Windows(2000, XP Vista and 2003), I have 14 desktops and a server and all the needs of the office could be handled from what I have seen by Open Office.  Getting legal copies of Windows here in Russia is a very pricy investment so they were not all upgraded at the same time..what a headache in keeping everyone talking to each other...

Stan
St Petersburg Russia/San Francisco

---

### Post by randomnick on 2008-05-09
> You know, there's a whole lot of overreaction in this thread. Stuff along the lines of "OMG Ubuntu sux now!

[http://www.ubuntusucks.com]("http://www.ubuntusucks.com")
:):):)

Look who the domain belongs to, lol. (It's NOT ME. I enjoy a good flaming of what I consider a half baked (thats being generous imo) release, but I wouldn't go *that* far)
Looks like they thought of everything. Perfect redirection though.

---

### Post by hyper_ch on 2008-05-09
> **km6xz said:**
> Hi hyper_ch
I currently use Dreamweaver CS3 and CodeCharge Studio 4.0 to develop my web sites using php and MySql.
The most important application for me is CodeCharge Studio and if there was some way to run it on Ubuntu I would be set.
For php / mysql I just prefer a good text editor ;)  and what do you like much about dreamweaver? Have a look at Kompozer there... an alternative for CodeCharge could be Zend Studio... but there are other tools also... for ajax I heard that aptana is quite good - but haven't tried it myself.

> **km6xz said:**
> I plan on switching my entire office over from 4 different flavors of Windows(2000, XP Vista and 2003), I have 14 desktops and a server and all the needs of the office could be handled from what I have seen by Open Office.
Most stuff can be directly converted to OOo. The only thing is if you use MS Access... that might be challenging...

---

### Post by jtuchscherer on 2008-05-09
> **lespaul_rentals said:**
> 

If you look at a distro like Slackware, you think stability.  Why is it so stable?  It's because it uses rock-solid, secure versions of software.  The Slackware team isn't going to throw in beta software in hopes of arousing fanboys.  As far as I know, Slackware 12 still uses the old version of Apache in its default install.  Slackware also has fantastic hardware support, and it keeps getting better and better instead of fluctuating like Ubuntu.

And heck, look at Debian.  Debian is stable and secure because the Debian team is far more strict about what code they use.  They don't just slap in some code that just happened to work.


I absolutely agree with you. Debian stable means stability. If I build a server, stability is what I aim for. So that is good. But Debian stable also means outdated software for my desktop pc. I cannot just sudo aptitude evolution to get the bleeding email client of my choice. I will need to use a version that is over a year old and does not have the features I need.
In the end it all boils to the old Linux tag line: Freedom as in free speech: You are free to choose what you want to use. Looking for stability - go Debian or Slackware or RHEL or whatever. Looking for the bleeding edge: Try Ubuntu 8.10.

I don't want Ubuntu to be another Debian stable with a 18 month release cycle. If I'd want that I would use Debian stable. I think their release strategy is great and it is why I choose Ubuntu.

You say, you will not recommend Ubuntu anymore. That is totally fine with me. I won't tell you what to recommend and what not. But let me tell you, I will continue to recommend Ubuntu to my friends who look for the newest stuff out there. I probably will add a little disclaimer and the advice to check the live cd first. 

My last point is that bashing a distro like it happens in this thread is pretty poor behavior. There are a lot of people dedicating their free time (I know, there are even more who get paid for it) to develop something we can use and in some cases enjoy for free. If it doesn't work, well, it doesn't work. You then have two choices: 
1. Contribute with filing bug reports or submit patches. 
2. Move on and use another distro or revert to an older version. 

Just bashing never helped anybody. Stay constructive and always appreciate what you get for free.

So long...

---

### Post by sebastjanp on 2008-05-09
> **jtuchscherer said:**
> I absolutely agree with you. Debian stable means stability. If I build a server, stability is what I aim for. So that is good. But Debian stable also means outdated software for my desktop pc. I cannot just sudo aptitude evolution to get the bleeding email client of my choice. I will need to use a version that is over a year old and does not have the features I need.
In the end it all boils to the old Linux tag line: Freedom as in free speech: You are free to choose what you want to use. Looking for stability - go Debian or Slackware or RHEL or whatever. Looking for the bleeding edge: Try Ubuntu 8.10.

I don't want Ubuntu to be another Debian stable with a 18 month release cycle. If I'd want that I would use Debian stable. I think their release strategy is great and it is why I choose Ubuntu.

You say, you will not recommend Ubuntu anymore. That is totally fine with me. I won't tell you what to recommend and what not. But let me tell you, I will continue to recommend Ubuntu to my friends who look for the newest stuff out there. I probably will add a little disclaimer and the advice to check the live cd first. 

My last point is that bashing a distro like it happens in this thread is pretty poor behavior. There are a lot of people dedicating their free time (I know, there are even more who get paid for it) to develop something we can use and in some cases enjoy for free. If it doesn't work, well, it doesn't work. You then have two choices: 
1. Contribute with filing bug reports or submit patches. 
2. Move on and use another distro or revert to an older version. 

Just bashing never helped anybody. Stay constructive and always appreciate what you get for free.

So long...

God Damned you're right here. I tottaly agree. If you want stability search somewhere else if you like bleeding edge dont cry about stability issues but try to help fix them.

---

### Post by 23meg on 2008-05-09
> **randomnick said:**
> 
Looks like they thought of everything. Perfect redirection though.

No, it's a very opportunistic, silly attack from someone who has no idea what they're dealing with. It's plain stupid. Anyone who thinks the sum of *bug reports* **on its own** is indicative of the overall quality of a free software OS has no idea what they're talking about. This includes you, since you've put forward the same naive non-argument before. And besides, to people who have put countless volunteer hours into triaging or fixing the bugs in that database, it's a straight insult. 

Have you ever participated in a volunteer effort to improve something that matters to you in your life? I'm asking because I feel compelled to insult you for doing so.

---

### Post by Gatemaze on 2008-05-09
> **heartburnkid said:**
> 
When was the last time you used Version X.0 of a software product -- ANY product, open-source or proprietary -- and it worked flawlessly on launch day?


Never, but mate there is a difference between trying to resolve a couple of issues and a difference than having a system that will lockup whenever... If you are using your system to watch some movies and listen to some music then obviously it does not really hurts you when your system will lockup.... but for some others that are doing work you can imagine the consequences...

---

### Post by Gatemaze on 2008-05-09
> **sebastjanp said:**
> God Damned you're right here. I tottaly agree. If you want stability search somewhere else if you like bleeding edge dont cry about stability issues but try to help fix them.

Sorry guys but I disagree with you on this.... LTS versions should offer the stability... Personally I decided to be upgrading on LTS versions only, which hopefully are more stable and save me from upgrading every 6 months... Maybe that's why there might have been a bigger fuzz for heron because it is a LTS release... I am confident on the kernel team who is trying its best to resolve the issues...

---

### Post by hyper_ch on 2008-05-09
> **Gatemaze said:**
> Sorry guys but I disagree with you on this.... LTS versions should offer the stability... Personally I decided to be upgrading on LTS versions only, which hopefully are more stable and save me from upgrading every 6 months... Maybe that's why there might have been a bigger fuzz for heron because it is a LTS release... I am confident on the kernel team who is trying its best to resolve the issues...

It is more stable than Windows ever was (for me)

---

### Post by Sealbhach on 2008-05-09
I never used Linux before.

I found Hardy 8.04 very stable, did everything I asked it to. Found all the hardware.

Much better than Vista, which is the dark side of my dual-boot.


.

---

### Post by AldenIsZen on 2008-05-09
Sorry to hear the trouble. This makes my "gripe" that I can't get write properties for Google calendar in Evolution to work as promised, pale in comparison. However, stuff happens.

 I am glad that I can get Hardy to work on an old computer that would always lockup on a black screen (after the Gnome splash, even keyboard/mouse)  on the live CD or after installing with the alternate CD on Feisty AND Gutsy! I can finally remote login to my faster computer and have decent response, and my girlfriend can use the fast one. I'm even going to setup Windows in a virtual machine, possibly with local Windows XP install. Which means no more arguing. :guitar: 

 I do understand your frustration.. but give it some time. As someone mentioned before, someone somewhere will have an issue with any brand new software. And when your fix comes, remember that someone was dedicated to fix it. Could take 2 seconds, could take 15 hours, but someone will get to it with their likely volunteer time. :popcorn:

 I guess what I am trying to say, people will look down on your sensationalism. Not to mention you insult all those that worked hard on this. I feel most people, such as myself, have had a better experience, which sharply contradicts your claim that this is "BY FAR the worst Ubuntu version ever!" Maybe for you, and as such, say THAT! But you made it sound like if we all install it and the sky will fall.. .. .:confused:

 As far as error handling.. I know little about these matters, however logic tells me if their is a total lockup, it is probably driver related and if a bad enough lockup, there wont be time to throw errors... it's frozen and locked up!](*,)

---

### Post by geezerone on 2008-05-09
Yes, I suppose that the releases of Ubuntu have been fairly stable so when a little less unstable a release happens everyone expects more. I am glad this is free and a good alternative to MS products and believe like others, that a solution will be found to make most happy! :)

---

### Post by buntunub on 2008-05-09
I just experienced my first set of lockups and X server crashes last night. I was unable to ssh in to that system when it happened. The ctrl+alt+SysRq+RSIUB keystroke combo did the trick however, and popped me back to shell. Then, I did -

[PHP]$cat /var/log/messages | more[/PHP]

Sifting down to the end of that revealed the culprit. Lots of errors about nvclock. This was a new app I had installed to change the fan speeds on my 8800, which I needed to do because the GPU was starting to run hot on some games I play. It is beta software - go figure. Immediately following those errors were messages about kernel dumps and resynch. At that point I was unable to restart X, so I did a -

[PHP]$sudo shutdown -r now[/PHP]

It rebooted gracefully and restarted, taking a very, very long time to do so. I hit alt+f2 at the bootsplash to watch the messages as it booted up. This revealed that it was taking so long to boot up because it was rejournalling the filesystem. When it was done with that, it booted up normally, and all has been ducky since. Oh, I also sudo rm'd that nvclock app which caused the issues.

Now, why did I just explain what happened, and what I did to debug and fix it? In hopes that those of you running in to issues can maybe learn from that and figure out what is going on with YOUR systems, and then either fix them, or post the appropriate logs to bugzilla so a dev can debug the faulty code. This is how its done - how the system works, and it works extremely well. Keep in mind too that most the devs I know do NOT read forum posts - ever! They dont because of threads exactly like this one. They do however, read the bugzilla threads quite carefully, because that is where real debugging and problem fixes occur when there is faulty code. So, long story short, 1) try to debug and fix the issue yourself - learn how to do this! 2) Eliminate the possibility that the issue was caused by you or your hardware. 3) Report the BUG to bugzilla with supporting logs and details so that your issue can be reproduced on the dev test machines. 4) Closely follow the bug that you posted and provide feedback support to the dev assigned to work your case.

---

### Post by porksome on 2008-05-09
Having used linux (ubuntu as main distro) exclusively for the last two years and even successfully converted wife and kids to linux, Hardy is a disappointment for me.
 
- Unable to boot LiveCD or install in anything other than safe graphics mode
- Xorg refuses to recognise my Radeon 9600 mobility M10 (open source will not install and the problems I've had trying to get Fglrx working on Hardy have driven me to dispair- stuck with VESA)
- The system randomly locks up after 2 or three minutes use unless an external mouse is attached, which delays the lockup for several minutes longer.
- Haven't been able to test much past the installation process as it hard locks within minutes of login.
- Have desparetly searched forums for solutions to the many problems I have but alas nobody seems to be able to offer solutions. Hardy either works for you or it doesn't it seems.
 
Hardy is unusable on my machine for now. Don't let us down Devs, sort the chaos out as we know you can.
 
For now I will revert to Gutsy and look at other distro options until Hardy is sorted.
 
:-(

---

### Post by Caesum on 2008-05-09
> **buntunub said:**
> Try booting with -noapic-nolapic and see if that helps.

Just tried that, lasted for five minutes before total lockup, which is a lot less than usual!

---

### Post by linuxlizard on 2008-05-09
I disagree with you guys claiming that ubuntu is bleeding edge, therefore it's ok that it's not stable. 

Ubuntu has *never* been hyped as being bleeding edge. Quite the opposite- it's supposed to be (and historically has been) very stable, easy to set up and usable by beginners, while offering apps that are recently released but tested enough to be fairly stable.

In fact, I've defended the fact that releases (like gutsy) didn't include the latest and greatest versions of software right here on this very board in the past, because the ubuntu philosophy has always been a balance of up to date software and stability. Or at least it was until Hardy had so many flaws and now you guys are trying to defend it by saying it's suddenly a bleeding edge distro.

It's always been a distro with the (rightful) claim that it is useful by regular human beings. And that's why a lot of advanced linux users choose not to use it. They want the bleeding edge. If you don't believe what I just said about many advanced users avoiding it for this reason, google around and look at message boards other than this one.

If you want bleeding edge, you might try something like fedora core, which has always been a distro proud to claim that, and has always been a distro that accepted stability hiccups as a result.

If ubuntu is shifting away from this and truely has become a bleeding edge distro, then it's a *HUGE* mistake IMO. There are a few other distros that can take up the slack for beginners (pclinuxos, freespire, and suse all come to mind), but no one has done a well rounded distro for beginners to advanced alike, with as strong a community as Ubuntu. 

It's also a mistake because right now we've got loads of unhappy vista users trying ubuntu. It's absolutely a shame to give them something as unstable as vista as their first linux experience. The instability along with the confusion of a new operating system and the complexity of troubleshooting on linux is going to send them right back to vista where they started, when we could have made a lot of new linux converts...

---

### Post by scouser73 on 2008-05-09
Hardy Heron is the best version of Ubuntu so far, perhaps it's some other part of your system rather than the O/S

Usually a clean installation should resolve the issues you have, failing that you could go back to Gutsy Gibbon.

---

### Post by azimuth on 2008-05-09
> **Gatemaze said:**
>  Personally I decided to be upgrading on LTS versions only, which hopefully are more stable and save me from upgrading every 6 months... 

I see one fault in your upgrade strategy. Just because a new version comes out every 6 months, doesn't mean you need to upgrade to it. All versions are supported for 18 months and LTS desktop is supported for 3 years. Server LTS versions are supported for 5 years. By leaving a version that is working for you before it has reached the end of it's support cycle, indicates that you are more interested in "bleeding edge" than stability. If you are expecting to avoid the bugs, you may need to rethink your strategy. You need to determine if the temptation of a shiny new distro is going to be worth the work you will need to put into it as an early adopter. Feisty has another 6 months of support and Gutsy another year. It may be more advantageous for "you" to continue the stability that you know, than to sample the deep end of the pool.

---

### Post by buntunub on 2008-05-09
The funny thing about this is that 99% of every post I see on this thread about lockups/random freezes, I have seen (from mostly the same people) on every dist-upgrade since dapper! Makes it extremely difficult to take seriously. Kinda like the boy who cried wolf kinda thing. Not saying that some of the posters here don't have issues - i'm sure they really do, and really need help, but there are some who just post for the sake of stirring up the flames.

Caesum - see my post immediately above your last. That is really the only answer. You must try to nail down what specifically is the cause of your crashes, and then research ways to fix it. Its what we all have to do in the end. It could be, and seems to me to be, that your going to have to experiment with different boot flag options, OR you really do have perhaps a motherboard issue. Since your setup and mine are about the same, it does not make sense that I have zero problems with Hardy, and you do on a fresh x64 install on both rigs (yours and mine). It more than likely means that your hardware is either faulty or setup in some way that is drastically different, causing the kernel to dump. Another option would be to regress kernels back to something like 2.6.22, or switch back to Gutsy until July when it is rumored that Ubuntu 8.04.1 comes out.

---

### Post by heartburnkid on 2008-05-09
> **linuxlizard said:**
> I disagree with you guys claiming that ubuntu is bleeding edge, therefore it's ok that it's not stable. 

Ubuntu has *never* been hyped as being bleeding edge. Quite the opposite- it's supposed to be (and historically has been) very stable, easy to set up and usable by beginners, while offering apps that are recently released but tested enough to be fairly stable.

If that's directed to what I said about "living on the bleeding edge", then you misunderstand me.  I am not saying that Ubuntu is a particularly bleeding-edge version of Linux; what I'm saying is that when you're an early adopter of ANY product, Ubuntu or otherwise, you are on the bleeding edge, to some degree or another.  I have not seen any software released ever that didn't have issues on some people's hardware configurations.  Coming up through the Windows world, even the lauded Windows XP had stability issues when it was first released.  And Service Pack 2 for XP actually managed to nuke several people's hard drives when it first came out.

If you install on launch day, you will have issues.  Simple as that.  They might be minor ones; they might be major ones; they might even break your computer.  There is no getting around this; given the complexity of the computer market these days, it's flat-out impossible to make any software work absolutely perfectly on every single configuration before release.  That's the simple facts of the digital life; how you act on them is up to you.

---

### Post by lespaul_rentals on 2008-05-09
> **heartburnkid said:**
> If that's directed to what I said about "living on the bleeding edge", then you misunderstand me.  I am not saying that Ubuntu is a particularly bleeding-edge version of Linux; what I'm saying is that when you're an early adopter of ANY product, Ubuntu or otherwise, you are on the bleeding edge, to some degree or another.  I have not seen any software released ever that didn't have issues on some people's hardware configurations.  Coming up through the Windows world, even the lauded Windows XP had stability issues when it was first released.  And Service Pack 2 for XP actually managed to nuke several people's hard drives when it first came out.

If you install on launch day, you will have issues.  Simple as that.  They might be minor ones; they might be major ones; they might even break your computer.  There is no getting around this; given the complexity of the computer market these days, it's flat-out impossible to make any software work absolutely perfectly on every single configuration before release.  That's the simple facts of the digital life; how you act on them is up to you.

Fair enough, there are bound to be some issues.  What has happened with Hardy is unacceptable.  Not even Gutsy had all these issues at release.

And linuxlizard is exactly correct in his post.  Ubuntu is unstable, and whenever someone complains they get the "bleeding edge" reply.  Well, Firefox 3 Beta as the default browser is a bit too bleeding edge for me.  I'm sorry, but that right there was a huge mistake.  That alone is enough ammunition to flame the distro.

---

### Post by heartburnkid on 2008-05-09
> **lespaul_rentals said:**
> And linuxlizard is exactly correct in his post.  Ubuntu is unstable, and whenever someone complains they get the "bleeding edge" reply.  Well, Firefox 3 Beta as the default browser is a bit too bleeding edge for me.  I'm sorry, but that right there was a huge mistake.  That alone is enough ammunition to flame the distro.

Frankly, it was either this or ship with Firefox 2 in their LTS release.  The LTS is going to be supported for 3-5 years.  Firefox 2 will be obsolete in 1 year's time.  Do the math, and you see that going with FF3 was really their only option, short of switching the default browser to Epiphany or the like.

---

### Post by jtuchscherer on 2008-05-09
> **linuxlizard said:**
>  Or at least it was until Hardy had so many flaws and now you guys are trying to defend it by saying it's suddenly a bleeding edge distro.



Not suddenly. It's always been. Just don't get confused because once a version is released you don't get all updates for each package. You normally only get the security updates. At the point of release each version so far has been very bleeding edge.

[QUOTE=lespaul_rentals] That alone is enough ammunition to flame the distro.

[/QUOTE]

Then go on and flame, but you won't change anything. It's a waste of your time and everybody's who is reading it. Switch distro. Go back to Gutsy. Install FF2 on your Hardy. But don't never ever flame.

---

### Post by randomnick on 2008-05-09
I find the reason that everyone keeps giving for the inclusion of FF3 asinine. 
> Frankly, it was either this or ship with Firefox 2 in their LTS release. The LTS is going to be supported for 3-5 years. Firefox 2 will be obsolete in 1 year's time. Do the math, and you see that going with FF3 was really their only option, short of switching the default browser to Epiphany or the like.

This is the common argument for its inclusion regurgitated by the zealots.
So FireFox 2 will be obsolete in a years time, so what? It is better to ship with a beta buggy browser than a stable one?

I have "done the math" and it does not equate. 
Why not just release FF3 as an update when it has reached an acceptable level of stability? Surely that would make more sense than its inclusion which is causing system lockups across a broad spectrum of different hardware configs.

> But don't never ever flame. 
... 
This particular gem would make a nice signature.

---

### Post by zhanglini on 2008-05-09
I installed Hardy 10 times in 10 days.  Sometimes it is because of my mistake, sometimes it just froze and gave me this GDM whatever error.
I have some applications that can't do in Linux, and Wine has been useless --- nothing ever worked there.
Thanks to Wubi!!!  I decided to install Hardy as an application in XP.  It has been a week without problem.  This is where Hardy belongs, as an applcation.  No dual boot, definitely no Hardy-only computer for me.

---

### Post by heartburnkid on 2008-05-09
> **randomnick said:**
> I find the reason that everyone keeps giving for the inclusion of FF3 asinine. 


This is the common argument for its inclusion regurgitated by the zealots.
So FireFox 2 will be obsolete in a years time, so what? It is better to ship with a beta buggy browser than a stable one?

I have "done the math" and it does not equate. 
Why not just release FF3 as an update when it has reached an acceptable level of stability? Surely that would make more sense than its inclusion which is causing system lockups across a broad spectrum of different hardware configs.

1: As I understand it, Canonical doesn't do major version upgrades of included programs within one version of Ubuntu.  Ironically, this is usually cited as a stability concern.

2: Are the freeze-ups really tied to Firefox?  So far, there's been little technical info posted on the issue, and plenty of whining and posturing, so I really don't know.

> 
... 
This particular gem would make a nice signature.

Indeed it would.  Perhaps you should follow it instead of deriding people as zealots for trying to have an intelligent discussion.

---

### Post by NotTheMessiah on 2008-05-09
> **lespaul_rentals said:**
> 
Come on, guys.  Theo de Raadt is exactly correct when he attacks Linux for its sloppy way of development.  *They have the same rapid development cycle [as Microsoft], which leads to crap.*

Rapid????What was rapid about vista? They had plenty of time to make that thing work...and it's still considered a flop

---

### Post by 23meg on 2008-05-10
> **randomnick]
This is the common argument for its inclusion regurgitated by the zealots.
So FireFox 2 will be obsolete in a years time, so what? It is better to ship with a beta buggy browser than a stable one?

I have "done the math" and it does not equate.[/quote]

1) FF2 will not just be obsolete soon said:**
> happened in Dapper[/URL]. You wouldn't want it happening again. 

2) [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
 
3) Many extensions that people will have on their FF2 installations wouldn't work, updating the localizations and themes would cause lots of problems, and there would have been lots of unforeseen issues when migrating profiles. 

[QUOTE=randomnick]Why not just release FF3 as an update when it has reached an acceptable level of stability? Surely that would make more sense than its inclusion which is causing system lockups across a broad spectrum of different hardware configs.

FF3 **is** at an acceptable level of stability. If you cared enough to look beyond the "Beta" label (which is just what it is: a label) and actually looked into the FF3 release schedule and upstream status and bug reports, you'd know that FF3 has been past feature freeze for weeks, and by the time it was released as part of Hardy, Mozilla had deemed it RC quality except for a few superficial glitches, and stated that any improvements from that point would be fixes for minor issues. Beta 5 was out on April 2nd, and Hardy on April 24th, which means that the version of FF3 that shipped in Hardy received 22 days worth of stability and polish work on top of the last beta release. In other words, it was pretty much final. The only serious issue with it that cropped up afterwards was the CPU spike issue, and it's fixed in Hardy now. 

As for system lockups, there's no evidence that FF3 is causing system lockups. I have not even seen a single bug report about this, let alone evidence. It's probably a non-existent issue that you're making up as part of your silly attacks.

---

### Post by mohtasham1983 on 2008-05-10
I had many problems playing videos in hardy. I found out that compiz was making those problems. Disabled compiz, and everything was working fine. After some I had trouble with playing youtube videos and playing music at the same time. That is, uninstalled hardy and installed gentoo. It took me  a long time to compile all programs that I wanted, but for some reason it start locking my keyboard and mouse. Gave gentoo another try and compile everything again, but had problem with blocking packages.

I gave up, and tried to install kubuntu 8.04 this time. So far everything is fine, except that in kde4 I can't figure out how to add a show desktop button to the task manager. If KDE 4 had the system monitor applet available in gnome, it would be really awesome.

---

### Post by padeco on 2008-05-10
hi there,

i've installed hardy 8.04. no issues at all during installation. great look and quite fast.

however, when running add/remove program or synaptic, things go wrong. i starts to download upgrades etc... normally, then without any apparent reason the download speed slows down and the whole system freezes / locks! there is no response whatsoever.

i thought it first it was related with ff3, nop. if anyone has any idea, pls send us some help.no other issues so far with hardy 8.04

regards,
padeco

---

### Post by hyper_ch on 2008-05-10
> **23meg said:**
> 3) Many extensions that people will have on their FF2 installations wouldn't work
The nightly builder tools addon makes almost everything work.

---

### Post by 23meg on 2008-05-10
> **hyper_ch said:**
> The nightly builder tools addon makes almost everything work.

It's called Nightly Tester Tools for a reason, right? It's for nightly testers, not non-technical casual users. Things that don't work usually don't work for a reason; forcing them to work with hacks isn't a solution.

---

### Post by erginemr on 2008-05-10
Here is a candidate for the origin of hard freezes:
[http://forum.compiz-fusion.org/showthread.php?t=8065](http://forum.compiz-fusion.org/showthread.php?t=8065)

---

### Post by squidmaster on 2008-05-10
double post. see below.

---

### Post by squidmaster on 2008-05-10
Reverted to Firefox 2
lockups and reboots went down by 1/2
still have tons of problems with Flash.

I believe it has something to do with rendering on some chipsets?
For instance, my intel chipset mobo has no problem with FF3 and flash, though FF3 will freeze sometimes it did the same thing on my XP and vista installs. But now we go to my nVidia chipset board (both of them) and I have constant lock ups.
Just what I have been able to decuce though.
Computer that is 100% intel, CPU, GPU, Chipset, has no problem at all, so that means most of you Dell boys and Laptop boys will have very little problems, but when it comes to something (maybe even VIA, I need to test that) nVidia, the lockups happen.

I am looking into if it still does it without Compiz but I don't want to lose my eye candy! haha

As well it looks like if you turn off "animations" is ccsm it doesn't seem to lock up nearly as much.

---

### Post by Arthur Archnix on 2008-05-10
If the point of this thread is to make all the developers and Ubuntu people who are happy with their systems cry, then congratulations: Mission Accomplished.

=D>

---

### Post by AlexMono94 on 2008-05-10
I would say the exact opposite, I would say it is the best release so far! :) I haven't experienced any lockups as of yet but maybe I'm just lucky. It's a shame it locks up for some people. :(

---

### Post by squidmaster on 2008-05-10
I'll say it ONE MORE TIME.
It may be kinda lame but
DISABLE ANIMATIONS IN COMPIZ (CCSM)
I have not had a single lock up since I did such.

---

### Post by dahlheim on 2008-05-10
> **squidmaster said:**
> I'll say it ONE MORE TIME.
It may be kinda lame but
DISABLE ANIMATIONS IN COMPIZ (CCSM)
I have not had a single lock up since I did such.

jesus, people, get over yourselves.  some of us really aren't that stupid.  i started locking up in gutsy, presumably after some update which i did not keep track of, and i don't use compiz, and before that everything was working just fine for quite a long time, and NO it's not faulty hardware.

computer science is not an exact science.

---

### Post by lespaul_rentals on 2008-05-10
> **randomnick said:**
> I find the reason that everyone keeps giving for the inclusion of FF3 asinine. 

This is the common argument for its inclusion regurgitated by the zealots.
So FireFox 2 will be obsolete in a years time, so what? It is better to ship with a beta buggy browser than a stable one?

I have "done the math" and it does not equate. 
Why not just release FF3 as an update when it has reached an acceptable level of stability? Surely that would make more sense than its inclusion which is causing system lockups across a broad spectrum of different hardware configs.

Exactly.  Firefox 3 should definitely be sent out to everyone as an APT update, but not a moment before its stable release.  Who cares if Firefox 2 will be obsolete in a year's time?  That a year away!  Now Hardy users are stuck with a beta browser for a year.

---

### Post by Dark Horse on 2008-05-10
I hope somebody finds a solution soon I have 2 Computers Running hardy 
One a Gigabyte MB With an AMD 2K Processor and Nvidia 6100 on board Video  with 3.5 GB of Memory has never locked up yet. This computer Is an XFX MB With an Nvidia Ge Force 7150 on board Graphics card with an Intel Duo core processor, and 2GB of memory. At this point I seriously considering going back to gutsy for this Box. Except for the random freezes Hardy looks like a big Improvement For this system needs stable more than new. I thought LTS was supposed to be stable.
P.S.  I am running Ubuntu Studio it comes with the rt Kernel to start.I would do a wipe and re install if I thought it would help.
   Mark :confused::)

---

### Post by padeco on 2008-05-10
> **padeco said:**
> hi there,

i've installed hardy 8.04. no issues at all during installation. great look and quite fast.

however, when running add/remove program or synaptic, things go wrong. i starts to download upgrades etc... normally, then without any apparent reason the download speed slows down and the whole system freezes / locks! there is no response whatsoever.

i thought it first it was related with ff3, nop. if anyone has any idea, pls send us some help.no other issues so far with hardy 8.04

regards,
padeco

well, it seems that once i switched net connection from wireless to ethernet cable there has been no further freeze/lockup. any one has any idea or similar issues.?.

regards,
padeco

---

### Post by 23meg on 2008-05-11
> **lespaul_rentals said:**
> Exactly.  Firefox 3 should definitely be sent out to everyone as an APT update, but not a moment before its stable release.

See my last post for why that can't be done.

> **lespaul_rentals said:**
> Who cares if Firefox 2 will be obsolete in a year's time?  That a year away!  Now Hardy users are stuck with a beta browser for a year.

They won't be "stuck", since an alternative (FF2) is presented to them, FF3 as it was shipped is way past "beta quality" despite the beta label, and I don't see where you get the "a year" figure from: FF3 is to go final in June.

---

### Post by erginemr on 2008-05-11
Good news! A new patch/update for Compiz has been released that can be installed via Update Manager. According to release notes, it addresses some hanging problems when that occur Compiz animations plugin is enabled. :D

---

### Post by mooscape on 2008-05-11
I tried installing Hardy via upgrade from Gutsy (which worked well, Gutsy that is). My computer has since been suffering from TOTAL lockups (everything stops working, only hard shutdown possible). Another problem is that the system won´t startup or shutdown properly. The graphic at startup/shutdown  goes wonky and the system locks. I tried a clean install and suffered from the same problem. I have tried switching to the real time (RT) kernel and can at least type this message without a crash. This is getting quite scary. I am leaving Gutsy on my production machines for now.

hp compaq nx9110 (ATI graphic card :-(

---

### Post by Jageye on 2008-05-11
Any news on this particular problem, I'm getting the same hard lockups, came from a rock solid gusty. Fresh install.Hope the devs get this sorted out, i dont really want to have to reinstall gusty.

---

### Post by geco on 2008-05-12
> **geco said:**
> I'm another unhappy Hardy "former"-user... after a totally fresh install (with hard drive partitioning) from the alternate-CD Hardy started to freeze whenever I logged in GNOME. Only the mouse pointer moved, but neither the keyboard or the touchpad buttons responded. I discovered that it was the open source ati driver who gave problems (no freezes with the standard vesa driver). but I was so upset that I decided to install Debian testing. I'll stay with Debian until I'll have good news from Hardy, then I'll decide what to do.

Hello everybody, I didn't follow the whole thread, but this is just to do an update of my current situation.
Even Debian (testing) decided to not to work after un upgrade, well... it's testing so I knew it could happen... so I came back to Gutsy and restored my backup files... maybe these issues are due to something that doesn't depend on Ubuntu team... is  my laptop (ACER TravelMate 3200 series) too old??? I wonder about that!
Anyway I wasn't able to identify the origin of the lockups... maybe the ATI Radeon videro card, maybe the wireless card... I have no idea!

That's all,
byebye

---

### Post by cjpetrie on 2008-05-12
Ubuntu 8.04 2.6.24.16 won't boot after upgrade on my Actius MM20 PC.
The screen goes black and the disk light comes on solid. For hours.

Kernel 2.6.22.14 does boot however. I don't see a .25 option.

Can anyone let me know how to get to the latest version that works please?

---

### Post by RiTarDid on 2008-05-12
I was also considering rolling back my kernel, but discovered that my problem with hardy resided in filesystem/formatting errors (ext3 for me)....panel menus and gparted (among other apps)caused lockups when i tried to get to the bottom of my troubles manually.
after maybe 10 formats and re-installs and literally hundreds of lockups; the boot sequence stopped to check the filesystem consistency (finally!); made some corrections to the HDD and I haven't had a lockup or any other problem for three days now...

Hardy i386 on second partition of SATA disc
Athlon64 3000+ @ 2.02Ghz
2GB RAM @ 200Mhz
Asus (nVidia) 7600GS AGP

hope i could help, good luck all!

---

### Post by lespaul_rentals on 2008-05-12
> **23meg said:**
> They won't be "stuck", since an alternative (FF2) is presented to them, FF3 as it was shipped is way past "beta quality" despite the beta label, and I don't see where you get the "a year" figure from: FF3 is to go final in June.

If it's "way past beta quality" then why is it causing system crashes?

---

### Post by buntunub on 2008-05-12
> **lespaul_rentals said:**
> If it's "way past beta quality" then why is it causing system crashes?

I see you have a fixation with FF3 beta. Let me assure you that the lockups you speak of are NOT the norm. For most folks meaning 95% of the Buntu using world), Hardy is the best thing since sliced bread, and runs 100% error free. This issue is solely YOUR issue, and perhaps a small handful of others, comparatively. There have been numerous reviews thus far of both Hardy and also reviews which have tested FF3, and all of them are just shy of glowing with praise. FF3 is already well known for its vast speed improvements and wonderful innovations over FF2, it is scheduled to lose its "beta" tag very, very soon, and is considered already well past the beta stages in testing. In short, there is no hard data to justify saying that Hardy is "the worst", or "the best", of any release from Canonical, however, I think based on overall reviews and reports from around the net (plus my own good experiences with them and my friends who all use Ubuntu), this release definitively has been the best of them all.

---

### Post by 23meg on 2008-05-12
> **lespaul_rentals said:**
> If it's "way past beta quality" then why is it causing system crashes?

Where's your evidence that it's causing system crashes?

---

### Post by randomnick on 2008-05-13
> Where's your evidence that it's causing system crashes? 

Where's *your* evidence it's not? An substantive number of users have reported issues with the beta browser.

> Hardy is the best thing since sliced bread, and runs 100% error free.

This is outright denial. In actuality 8.04 is *filled* with  Launchpad accepted open bugs;
[https://bugs.launchpad.net/ubuntu/]("https://bugs.launchpad.net/ubuntu/")

> This issue is solely YOUR issue, and perhaps a small handful of others, comparatively

The release of buggy code is every users issue. 
Most people download and install an OS in order to use it, as opposed to scour the forums looking for unwieldy workarounds to correct known bugs that were not corrected before release. 
Out of a poll of end users 49% (!!) ,at current count, reported issues with Hardy.
[http://ubuntuforums.org/showthread.php?t=766982]("http://ubuntuforums.org/showthread.php?t=766982") 
I would not call that a small handful.

> In short, there is no hard data to justify saying that Hardy is "the worst", or "the best", of any release from Canonical, however, I think based on overall reviews and reports from around the net (plus my own good experiences with them and my friends who all use Ubuntu), this release definitively has been the best of them all.

This statement is self contradictory. By this reasoning all those who have had a bad experience with Hardy, and their friends, could just as equally state that this release definitively has been the worst of them all.

Rather than attacking those who bring up issues they have found with Hardy with unsupportable statements, and the aggressiveness of a rabid fanboy, maybe your energies would be better spent helping make Ubuntu the distro you *wish* it was.

If Canonical / Ubuntu ever hope to gain a broader market share, and increased hardware support of vendors they are going to have to better than this.  The current state of quality control is simply unacceptably poor. Imho the 8.04 release is a disastrous trainwreck of half-baked, code seemingly strung together with duct tape and bailing wire.

---

### Post by hyper_ch on 2008-05-13
> **randomnick said:**
> Where's *your* evidence it's not? An substantive number of users have reported issues with the beta browser.
You cannot prove anything non-existance... you can only say it's highly unlikely... so proof requires to be positive hence that it is the fault of FF Beta... as there are many people without issues running FF Beta it is unlikely that FF causes that.

> **randomnick said:**
> This is outright denial. In actuality 8.04 is *filled* with  Launchpad accepted open bugs;
[https://bugs.launchpad.net/ubuntu/]("https://bugs.launchpad.net/ubuntu/")
So is every other Ubuntu release... however what does that mean?


> **randomnick said:**
> The release of buggy code is every users issue.
Tell me one piece of software that has no buggy code at all?

> **randomnick said:**
> Most people download and install an OS in order to use it
Most people do not install an OS... they buy a machine with an OS preinstalled and preconfigured on hardware that is tested to work with the OS.

> **randomnick said:**
> Out of a poll of end users 49% (!!) ,at current count, reported issues with Hardy.
[http://ubuntuforums.org/showthread.php?t=766982]("http://ubuntuforums.org/showthread.php?t=766982") 
I would not call that a small handful.
You think that poll is representative? There are less people in this poll than I have served CD-images during the first 25 1/2h of the Hardy release...

> **randomnick said:**
> This statement is self contradictory. By this reasoning all those who have had a bad experience with Hardy, and their friends, could just as equally state that this release definitively has been the worst of them all.
All the people I know think it's the best release ever...

> **randomnick said:**
> Rather than attacking those who bring up issues they have found with Hardy with unsupportable statements, and the aggressiveness of a rabid fanboy, maybe your energies would be better spent helping make Ubuntu the distro you *wish* it was.
Bring issues, submit bugs, ... but don't rant ;) if you want to rant, then make it better first yourself ;)

> **randomnick said:**
> The current state of quality control is simply unacceptably poor.
Yet it's still better than M$ Vista...

---

### Post by Gatemaze on 2008-05-13
and the worst bit is that i got the heron t-shirt, which is very nice :D, except that it promotes the buggiest version of ubuntu :(.

---

### Post by chewearn on 2008-05-13
I found one Gutsy lock-up thread, which 65 pages long:
[http://ubuntuforums.org/showthread.php?t=587905&page=65](http://ubuntuforums.org/showthread.php?t=587905&page=65)


Let's continue feed the trolls.  Soon, this thread will be at least 100 pages.

Granted, the discussion in the gutsy thread is far more civil than this one.
At least, the few pages I read (seriously, anyone reading all of it will go crazy.  Crazy I say).


Interestingly, Firefox 2 in gutsy was suspected to be one cause of the freeze.  Deja vu?


.

---

### Post by karellen on 2008-05-13
> Yet it's still better than M$ Vista...
I guess it's pretty risk to simplify things like this: "this OS is better than other because of....". there are likes and dislikes, pros and cons, choices and personal needs...

---

### Post by darrenn on 2008-05-13
I have the same laptop as the original writer of this post (acer 3680). And I am NOT having lockup problems. I am starting to think Jim March is a troll.

---

### Post by LaRoza on 2008-05-13
> **squidmaster said:**
> Reverted to Firefox 2
lockups and reboots went down by 1/2
still have tons of problems with Flash.

I believe it has something to do with rendering on some chipsets?
For instance, my intel chipset mobo has no problem with FF3 and flash, though FF3 will freeze sometimes it did the same thing on my XP and vista installs. But now we go to my nVidia chipset board (both of them) and I have constant lock ups.
Just what I have been able to decuce though.
Computer that is 100% intel, CPU, GPU, Chipset, has no problem at all, so that means most of you Dell boys and Laptop boys will have very little problems, but when it comes to something (maybe even VIA, I need to test that) nVidia, the lockups happen.


I use Opera 9.50b2 and Flash with no problems. I use wmii (no GNOME or Compiz) as well. 

I have Intel for everything also.

---

### Post by sports fan Matt on 2008-05-13
Honestly, I have nothing more to say on this thread.  Let the trolls play, I simply dont care.

---

### Post by gpgp on 2008-05-13
Funny i had great success with hardy so far. First it recognized all the hardware gutsy didn't on my dell inspiron 6000. Last week i replaced every other os in the house except my 12yr old laptop that is running puppy. i think hardy is the best ubuntu i have used.

---

### Post by fiddledd on 2008-05-13
I'll start by saying I haven't used Linux since Ubuntu 7.10, I use Vista and XP and am more than happy with both as far as performance is concerned. I do however want to use Linux again when it fully meets my computing needs, as I like the idea of a helpful Community and Open Source Software. It's not relevant to this thread why Linux and me don't quite fit yet (you can search my posts if curiosity gets the better of you). 
  Anyway, I hope you gather from what's typed above that I am not a Ubuntu Fan Boy by any means.
  So to this thread, this long thread with over 400 posts and nearly 30,000 views. Now I could reiterate some of the general points that's been posted, but instead, could I make a couple of suggestions, no? well I'm going to anyway:)

 Firstly to those that respond with zeal and some anger to these threads, if people post complaining without filing bug reports or asking politely for help, ignore them. They didn't ask for help, so you can't help them.
 Secondly to those starting these threads, could I suggest you ask for help with a full description of your problem, hardware specs etc. There are many many people here ready to help if they can, and it won't cost you a penny. If you can't fix your problem after asking for help then file a bug report. In the end you'll have Ubuntu working fine on your Computer, which is what you wanted all along, wasn't it?
 And thirdly to the trolls, assuming there's at least one that's posted here, well done, you got a community at each others throats, so to speak. Unfortunately for you it won't last, most bugs will be fixed and posts will go back to asking and giving help (until the next release, when it will all start over again.)
 These are just my thoughts, they mean nothing to anyone except me. :)

---

### Post by 23meg on 2008-05-13
[QUOTE=randomnick]Where's *your* evidence it's not? An substantive number of users have reported issues with the beta browser.[/QUOTE]

The burden of proof is on the person who asserts that something whose presence is contested exists. "Issues", true, there are issues. But there's no evidence of system lockups caused by FF3 that I know. You're welcome to point to evidence if you have it.

---

### Post by bigbrovar on 2008-05-13
> The burden of proof is on the person who asserts that something whose presence is contested exists. "Issues", true, there are issues. But there's no evidence of system lockups caused by FF3 that I know. You're welcome to point to evidence if you have it.
i dont know what kind of evidence u want .. all i know is that when i was on hardy .. my system would freeze as soon as i start ff3 and the only way to recover would be thru a hard reset ... it happened 3 times consecutively.. i did a search on Google and i found out that many pple also have the problem .. funny thing is  the locking stopped after i started using seamonkey ...  even then the whole system bcam unstable and i had to downgrade ... i have since had a very stable system  using gutsy ... i love Ubuntu very much .. its the only os i run and i was really hoping that hardy would be very stable .. alas it wasn't in my experience .. i know some pple are having it smooth which is good shows, that it is not all that bad .. but what pissed me is when they try to make pple that complain of problems trolls .. or make us think we are imagining things

---

### Post by erginemr on 2008-05-13
@bigbrovar,

I hear you. And I don't think you are trolling at all. I also love Ubuntu right down to my bones, but there are many crash reports coming from a number of threads that it is an undeniable fact that Hardy doesn't quite work for some of us here.

An inexplicable wave of dead-freeze crashes also hit the shores of my computer last few weeks. I could put an end to those unnerving, out-of-the-blue stalls by disabling Compiz altogether and installing and using Opera as my primary web browser. For you to try...

---

### Post by 23meg on 2008-05-14
> **bigbrovar said:**
> i dont know what kind of evidence u want .. all i know is that when i was on hardy .. my system would freeze as soon as i start ff3 and the only way to recover would be thru a hard reset ... it happened 3 times consecutively.. i did a search on Google and i found out that many pple also have the problem .. funny this is that the locking stopped after i started using sea monkey ...  even then the whole system bcam on stable and i had to downgrade ... i have since had a very stable system since using gutsy ... i love Ubuntu very much .. its the only os i run and i was really hoping that hardy would be very stable .. alas it wasnt in my experience .. i know some pple are having it smooth which is good shows that it is not all that bad .. but what pissed me is when they try to make pple that complain of problems trolls .. or make us think we are imagining things

Sounds like [bug #215718]("https://bugs.launchpad.net/bugs/215728"). It's not a system crasher; it causes excessive disk I/O, which may make your computer unresponsive especially if it's slow. It's been fixed; did you install the update? If you did, and it still persists, try this:

[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/](http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/)

---

### Post by THAiSi on 2008-05-14
I also agree..

Under Gutsy, everything was working perfectly. I was really enthusiastic. Compiz worked great, etc. Because I was so happy about Gutsy I had doubts about upgrading but thought. Hey, this can only get better right? Wrong :-(

My videocard is suddenly not supported at all (8800 GTS) tried installing it with envy and lots of other possibilities found on the forums here and elsewhere. but no success. everytime an annoying 'could find monitor or graphic card drivers' and the switch to safe graphics mode or how it is called.

the open source 'nv' drivers work and the 'vesa' drivers work, but no 3d acceleration anymore. I am really frustrated because it worked so nicely in gutsy.

---

### Post by buntunub on 2008-05-14
> **THAiSi said:**
> I also agree..

My videocard is suddenly not supported at all (8800 GTS)



What complete and total nonsense! Mine worked right out of the box on fresh install of Hardy using the Restricted Driver Manager, which downloaded and installed the 169.12 Nvidia Driver. Check your setups and try again. There are numerous guides/how-to's on these and other forums and wiki's which can walk you through the process. Simply could not be any easier, even on Windows XP, which does not want to play nicely at all with my 8800, while Hardy seems to simply love it.

---

### Post by odin79 on 2008-05-14
I just lost 20 mins of work due to a KERNEL PANIC WHICH I NEVER GOT IN GUTSY! I have got these panics quite often recently, can somebody tell what is causing this because it is FU***G ANNOYING! I am already overworked and the last thing I need is a crash!!!!

---

### Post by Gorgofdoom on 2008-05-14
I recently upgraded to Hardy and i have yet to have a problem. my graphics drivers work ok, but probably not as well as they can work on windows due to support issues (Nvidia) with a Gforce 5k, and Linux has yet to crash for me. ever.
(but thats probably because I'm using what other people have already pre-debugged and processed) anyway, I'm a Linux supporter all the way, even if it does come up with a few problems. Besides, its free, ain't it? :P

---

### Post by bigbrovar on 2008-05-14
> **23meg said:**
> Sounds like [bug #215718]("https://bugs.launchpad.net/bugs/215728"). It's not a system crasher; it causes excessive disk I/O, which may make your computer unresponsive especially if it's slow. It's been fixed; did you install the update? If you did, and it still persists, try this:

[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/](http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/)

awesome ! sadly though i have already downdraged to gutsy and it mgith take a while b4 i use hardy .. might as well just wait till October then i would upgrade to ibex

---

### Post by jrusso2 on 2008-05-14
> **buntunub said:**
> What complete and total nonsense! Mine worked right out of the box on fresh install of Hardy using the Restricted Driver Manager, which downloaded and installed the 169.12 Nvidia Driver. Check your setups and try again. There are numerous guides/how-to's on these and other forums and wiki's which can walk you through the process. Simply could not be any easier, even on Windows XP, which does not want to play nicely at all with my 8800, while Hardy seems to simply love it.

Nonsense my 8800 GTS works perfectly on Windows XP, couldn't be easier.

---

### Post by Gatemaze on 2008-05-15
> **odin79 said:**
> I just lost 20 mins of work due to a KERNEL PANIC WHICH I NEVER GOT IN GUTSY! I have got these panics quite often recently, can somebody tell what is causing this because it is FU***G ANNOYING! I am already overworked and the last thing I need is a crash!!!!

Odin, I am afraid that you should avoid using hardy for the time being on your production machines until the stability issues with the heron kernel is resolved... hopefully you still have your old system on another partition...

---

### Post by Gatemaze on 2008-05-15
> **bigbrovar said:**
> awesome ! sadly though i have already downdraged to gutsy and it mgith take a while b4 i use hardy .. might as well just wait till October then i would upgrade to ibex

The whole issue of heron is that it is a long term support release so even if ibex comes out you still have the choice of heron as it simply will last longer than ibex. Personally, I have no desire of upgrading my system every 6 months or so...

---

### Post by Gatemaze on 2008-05-15
I have only one question... how will we find out that the issues with heron have been resolved? i doubt canonical will have an announcement on their front page?

---

### Post by bigbrovar on 2008-05-15
> The whole issue of heron is that it is a long term support release so even if ibex comes out you still have the choice of heron as it simply will last longer than ibex. Personally, I have no desire of upgrading my system every 6 months or so...Good point .. how come i never saw it that way .. anyway gutsy is working for me awesomely and i dont think i will be making any upgrade soon .. why fix it if it isnt broken..
> 
I have only one question... how will we find out that the issues with heron have been resolved? i doubt canonical will have an announcement on their front page?well i think the devs are working on it right now .. once there is a fix u would get it thru the update system ....

---

### Post by RavenD on 2008-05-15
Got Kubuntu on one machine, Ubuntu on another - both hardy. And I've played with it in some virtual machines (KDE4 remix, etc). Aside from KDE4, seems rock solid stable, although I have had a couple reports of wifi issues.

---

### Post by odin79 on 2008-05-15
Thanks for reply Gatemaze, I was just overworked and tired yesterday with a deadline looming just around the corner. But now after a good night's sleep I'm happy again. Anyways, I really like Heron so hope they resolve this Kernel issue soon.

Note: On Gutsy I had problems with Kernel Panic when using ndiswrapper. But this I solved by using the Broadcom driver instead.

---

### Post by 23meg on 2008-05-16
> **Gatemaze said:**
> I have only one question... how will we find out that the issues with heron have been resolved? i doubt canonical will have an announcement on their front page?

Subscribe to the bug reports.

---

### Post by joe57005 on 2008-05-16
I am also having frequent freezes (total lock up with caps-lock flashing), but it seems to only happen when on the internet. it will happen randomly on firefox after a few minutes to a few hours of normal use. torrent downloading is flawless, but nntp (usenet) downloads freeze very, very frequently. (though often whole downloads will complele without any trouble) i could not find any suspicious errors in the system log, but i think it's a driver issue (in my case). everything else works fine. does the flashing caps-lock say anything about the cause, or is it just ubuntu telling me the obvious- that it crashed. 
i'm here looking for help, not to flame ubuntu or debate it's usefulness, as far as i'm concerned, it does what i need, it's free and anything not-microsoft is fine by me. (no drm!)

---

### Post by cubeist on 2008-05-16
> **joe57005 said:**
> I am also having frequent freezes (total lock up with caps-lock flashing), but it seems to only happen when on the internet. it will happen randomly on firefox after a few minutes to a few hours of normal use. torrent downloading is flawless, but nntp (usenet) downloads freeze very, very frequently. (though often whole downloads will complele without any trouble) i could not find any suspicious errors in the system log, but i think it's a driver issue (in my case). everything else works fine. does the flashing caps-lock say anything about the cause, or is it just ubuntu telling me the obvious- that it crashed. 
i'm here looking for help, not to flame ubuntu or debate it's usefulness, as far as i'm concerned, it does what i need, it's free and anything not-microsoft is fine by me. (no drm!)

If FF3 does not work for you, remember it is a beta...bugs should be expected, there are two options, downgrade to FF2 which solves a lot of problems, or try another browser like Epiphany or Opera.

---

### Post by erginemr on 2008-05-16
@joe57005,

I was also having hard-lock freezes while browsing the web with Firefox 3. Here are my two cents:

* I have installed Opera 9.50b2 and started using it

* I have disabled Compiz and enabled the compositing extension of Metacity (Gnome's default window manager)

* Third measure you can take is to install the driver of your video card via EnvyNG if you have an NVidia or ATI card.

* The latest updates included a patch for Compiz freezes and an updated Xorg driver for Intel video cards.

---

### Post by joe57005 on 2008-05-16
i'm not having problems with firefox, in fact, i really like ff3. yes, my system does freeze when browsing with ff3, but not very often, it actually crashes far more often when other programs access the internet. namely newsreaders. i've tried several different ones and they all do the same thing. i think it's a hardware/driver compatability problem with my wireless card, not firefox 3. to humor erginemr i will try using the nv driver for my nvidia cards rather than the nvidia driver, (i have three monitors, two are on nvidia chipsets) but i seriously doubt that it will make any manner of difference whatsoever, as i used the same driver with gutsy and feisty with no problems.

---

### Post by rpwdh on 2008-05-16
Dunno... seems to be working fine for me.

Your mileage may vary...

---

### Post by bcscomp on 2008-05-16
I'm sitting here reading all these post about how bad Hardy is on my Asus A6000 laptop running Ubuntu 8.04. The only things that didn't work out of the box were the wifi, this was fixed by using ndiswrapper, also the built-in web cam (this still doesn't work but I knew when to quit and spent $15.00 on a generic Taiwanese product that just plugged and played, aMSN detected it immediately and worked, so all is sweet) I have a sophisticated network with file/media/mail servers all mixed with GNU/Linux and Windows - no problems there at all. I'm sorry if this sounds like a good news story for Hardy Heron, and maybe it is in the wrong thread, but I felt that something positive needed to be said for what is, possibly not the best distro on the planet but without doubt the most user friendly. (and I have used a few!) My experience of open source operating systems is that however hard you look, whatever distro you decide to move to - there is no, "one size fits all'. There will always be something that doesn't work right away. I have lost count of the hours I have spent tweaking this or that with no result at the end of it - frustrating yes, with an uppercase f, but at the end of the day I send my invoice for time spent to the department of Freedom

---

### Post by joe57005 on 2008-05-17
I'm going to try using the manufacturers drivers from their site, instead of the ubuntu included driver, if that doesn't solve my issue, i'm going back to gutsy.

---

### Post by simoncullen on 2008-05-17
Without going into details -- or reading terribly much of this thread, I will add my own experience to the spirit of its topic.

I'm a big Ubuntu supporter.  I've just reinstalled Gutsy.  The numerous troubles Hardy gave me over a few short yet painful days (inc random lockups) were a complete pain.

Not sure what happened with Hardy, but judging from the threads here and on what friends who've experimented with it say (some persisting, others, like me, recoiling), it's been a bit of a disaster.  Hope things get sorted out soon.

On an up note -- Gutsy is a truly wonderful OS which I love as much as any man ever loved his operating system.

edit: I should add that I've been running Hardy's kernel with Gutsy since it was still in development.  So, apart from the headaches, I didn't find really anything new or of interest in Hardy.

---

### Post by Modplanman on 2008-05-17
The biggest problem here is what someone said here earlier, but in reverse.

Just because you have an issue, does not make it a genuine step back or mean the OS in general is ****, it just means you happen to have an issue. No OS is ever error free, and there will always be chances of some bit of hardware or something else going wrong for numerous reasons, I would assume most common being new features (as 8.04 has plenty, along with it's new kernel).

People calling this the worst release ever are completely over exaggerating, probably basing it entirely because they have one or two certain issues (as appears to be most of the people in this thread), and completely forgetting that this is a new release, and with every new release of anything, there will be bounds of problems aplenty.

This probably isn't the first time, nor the last that threads like this and calls of a release being the worst will come about because of a lack of foresight and narrow mindedness by the users themselves.

Not to mention, any "ZOmg look at these forums!!2" is forgetting this is primarily a support forum, therefore it's bleedin' fecking obvious there's gonna be threads and threads devoted to these problems. Combine that with the above, and you have a recipe for this thread.

Anyways, no problems here. The new kernel doesn't work with the solution for my broadcom USB wireless, but all I have to do is go back to my older kernel (2.6.22-14), problem solved.

---

### Post by tc101 on 2008-05-17
> **Gatemaze said:**
> I have only one question... how will we find out that the issues with heron have been resolved? i doubt canonical will have an announcement on their front page?

I have the same question.  I will eventually upgrade to to heron, but I am in no hurry.  I guess I'll just keep looking for conversations like this and when people stop posting and saying heron is bad I will know it is OK to upgrade.

Is there any better suggestion?

---

### Post by psychomichael on 2008-05-18
I have been reading and decided weeks ago not to upgrade to Hardy Heron until all issues are resolved, but have been installing the regular updates....now Gutsy is crashing for me randomly for no reason. I haven't changed anything, and the most I've been doing is downloading a single torrent at a time. It crashed last night while watching a movie and this morning while in screensaver mode. 

This is no longer just a Hardy Heron issue...I think it's starting to bleed backwards into Gutsy...and I am unable to get error information.

---

### Post by bonestonne on 2008-05-18
you know, normally I'm not one to interject my opinion in threads like this, however I see an unrivaled amount of naivety here.
1) Saying you wont install an OS until all the bugs are out is incredibly foolish, especially when its free. Developers could just come up with a final version and if it doesn't work for you, that just sucks for you. But they don't. Why do you think Ubuntu has Hardware Testing on the OS? It's not there for fun and games, its there to gather information from as many setups as possible so that they can support as much hardware as possible.
2) Yesterday I was reading around looking for SATA support. I saw so much stupid flaming about the lack of support that it made me somewhat sick. I, as many other had been, was affected by the SATA problem. Well, I read around a little more, and saw that if you change it to RAID mode, it changes how the drives are presented to the OS. It has nothing to do with setting up your drives in RAID. And look where I am now, happily updating my fresh Hardy install.

I hope you can all realize that you just need to put up with stuff. I use 64 bit so I get even more limits on support than 32 bit users. Using linux means that you're willing to find workarounds for yourself.

This isn't Windows or Apple. Either try (my favorite) Google-A-Fix, or find a workaround. If you're going to use Linux, quit your bitchin' because the people who make it do it for the good of everyone, they don't have your exact computer in front of them to work out the kinks.

---

### Post by Hadraniel on 2008-05-18
I was experiencing these random system freezes ever scince I upgraded from my rock solid 7.10. Today I finally figured out, that it was not due to CPU heat issues, but to some bug in the hardy standard kernel, being discussed in numerous forums as well as in this thread.

But my faith in Ubuntu has been restored by now, at least temporarily, by applying the patch mentioned at posting #45 in this thread: switch zu linux-rt kernel.
Setting kernel options like pci=noacpi, nohz=off, highres=off and irqall were of no effect.

With linux-rt the system lockups are gone. At least for now.

---

### Post by hvacr on 2008-05-18
I am also getting constant freeze ups that I never had in gutsy. This is a desktop system with a radeon 1800 graphics card. This system would freeze up doing anything. I tried the different graphics drivers with no luck. I removed and re installed compiz, nothing. The only way I fixed the issue was to remove compiz all together, and run with out it. I guess I have 2 choices, go back to gutsy or wait for the next upgrade to heron.

---

### Post by Panzerino on 2008-05-18
Yes,Hardy is BY FAR the worst Ubuntu version yet.

Two day install after install. Fresh install, dedicated HDD, no Windows partition etc. Whole 80Gb HDD-Ubuntu only.
Not able to install ATI Linux driver for my ATI Radeon 1650 Pro AGP card in ANY WAY:

*with EnvyNG-white screen. Nothing help.
*with traditional ATI install, or Ubuntu type of driver install-black screen after reboot.
*install within Synaptic-black screen on reboot.
*install within note :"Install the ATI driver for your hardware"-black screen on reboot.
*Install from Live CD on HDD, without the ATI driver nightmares->>my incredible sound card Terratec Phase 28 give me in Ubuntu cliping sound, low volumes, etc. No help-no alsamixergui tweaks, no any single tweak inside audacious work, no change from ALSA to OSS work too.

Sorry-i will not tray anymore!
Shame on you Ubuntu creators, if one regular intelligent user **must have degree in computer science** in scope to install simple graphic driver. If there is a problem->> POST ONE good solution, instead of put us to search thousand posts with dubious information from personal experiences.
**Let make it clear-YOUR GRAPHIC DRIVER INSTALLATION PROCEDURE FOR SOME NEW ATI card is awful, and WORST-DOES NOT WORK!!!!!!!**

Sorry-i go back to my old XP- there, all is in work condition. And work flawlessly. Why to spend my time 5 day of endless installations and ruin my hardware, in scope to make one printer to work? or one graphic card to work properly? 
Sorry boys-you are in 1978, not in 2008.  Or you have plenty of time to spend.

---

### Post by 56Post on 2008-05-18
I have 2 Dell laptops one D510 with 6.06 installed and a 600m with 8.04 Hardy.Both of them are dual boot.The 6.06 is stable and does everthing I need except network with my HP C4385 printer. The Hardy install was easier on a fresh dual boot install and also works with the HP printer. I did have to research the ATI adapter and was able to get compiz working with minor issues. I have been using Ubuntu for years now and can remember when wireless and printing was impossible for me. It has come along way and I am not going to complain because it is free. For Ubuntu to be a true Windows replacement it has to be able to do all these things with minimal work from the end user. It is headed in that direction and the support forum is outstanding. My skills are limited but with a little  time on the forum site all problems seem to get fixed in time. I have a Vista desktop that can't even burn a disk so I use Ubuntu. For me Hardy is the best version because it is the first time the laptop does all my home office needs using Linux. I hope with input from others  these lock up issues some people are having will be fixed. I am sticking with Hardy.

---

### Post by Panzerino on 2008-05-18
"It has come along way and **I am not going to complain because it is free**."

->Not argument for me. Please give me ONE **working solution** HOW TO install successfully the ATI Linux driver for my card-quick and efficiently. And i will give the Ubuntu second chance.
Tell me how to monitor the ink level of my printer cartridges (Canon iP4300)without to be computer genius.
These are simple questions, not luxuriously solutions.
"Linux is not Windows". Sure. But how to make my work so efficiently like i make her in Windows XP (vista is garbage)? By read forums and computer books day by day??

---

### Post by 56Post on 2008-05-18
Panzerino,
Here is the best I can do for you for the ATI card.
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)
I was not replying to your message but just giving my experience with Ubuntu. And what you say is true. It does take a lot of work sometimes to use Ubuntu and the point I was trying to make is these things such as ink levels are important to users like us who are not computer techs. Wish I could help you more but I am sure you have  already went through the forums. Hopefully soon Canon HP ATI ect will start to support Linux.

---

### Post by Babstar on 2008-05-18
> Tell me how to monitor the ink level of my printer cartridges (Canon iP4300)without to be computer genius.
These are simple questions, not luxuriously solutions.

It would appear that it is not easy to get it going under windows either
> 
The documentation that comes with the printer claims that this will not run with NT or Win 3.1. However, the canon site has links to drivers for NT. Printing under non-Win9X systems is accomplished by setting the printer to DOS emulation mode. Under this mode, the printer is driver compatible (according to Canon) with several printers including the Epson LQ2550 and LQ2500 and the Canon BJC 4300 and 4400. The resolution in this case is claimed to be the maximum supported by the driver.
I tried it out with the bj600 and it works. Resolution at which it prints is not known. I have not tried the scanner. 
 source:[_Linuxprinting.org IP4300 database entry_](http://openprinting.org/show_printer.cgi?recnum=Canon-iP4300)



Tell me, did Canon provide the printers spec's without requiring a Non-Disclosure Agreement (NDA) to the community?  How about your ATI card, are public specs available?  Linux would support almost ALL hardware well if spec's were availble without a NDA.  This is NOT a linux/Ubuntu issue. The issue you have is with the printer vendor. Given the reverse engineering required to get some hardware to work the way it does under linux, it is a testament to determination of the community,  in spite of the obstacles provided by the microsoft/vendor parasitic relationship (that is, you the user are the host).

Linux will support your hardware if the vendors release the documentation.  This is the cause of the problem for the vast majority of users.  Vent your anger at the manufacturers, better still, vote with your wallet where you can & choose linux friendly hardware.

---

### Post by 56Post on 2008-05-18
I believe ATI is a little more Linux friendly after AMD bought them in 2006. You are right vote with the wallet.

---

### Post by roderick on 2008-05-18
In my experience, I always choose Intel Video cards... best supported.

With ATI and nVidia, it's a real crap shoot. Sure, they are generally better cards, but their drivers are not as good as the openly supported and developed intel video drivers. 

ATI (now that AMD owns them) is starting to open up, but still very slow. So, you are still stuck with a binary only driver that can have conflicts each time the kernel is updated.  The same is true of nVidia. 

The free radeon driver and nv drivers do not come close (yet) to providing all the necessary 3D capable in those cards, but they do at least get updated to match changes in the kernel.

For those experiencing issues using ATI or nVidia cards, try 1) using the free driver to see if it at least works (in at least some limited fashion) or 2) try using an older kernel like a 2.6.22 and see if the binary driver works with it.

Until a free driver implementation that is fully functional exists, users of ATI and nVidia will always have hiccups. This is NOT the fault of Linux or any distros like Ubuntu - get over it. 

This is why I openly support Intel - they support us. Now with their new X3100 series cards, they will start to compete direclty with ATI and nVidia, and Linux users will begin to reap this benefit as Laptops and many motherboards will have these integrated video chips.

---

### Post by barf1 on 2008-05-19
> **sirdilznik said:**
> I had problems with the 2.6.24 kernels too.  Manually compiled and installed 2.6.25 and everything is A-OK!

Hi I'm a long time Fedora user and I'm now trying out Ubuntu LTS Server and I was looking for a answer to a problem when I came across this thread. Just thought you'd like to know that the 2.6.24 kernel caused alot of probs in Fedora as well with machines freezing up just after the network gets started. Oddly enough thats what started me looking for another distro.

---

### Post by Hadraniel on 2008-05-19
I want to add something to my last posting: I changed to the linux-rt kernel and my lockups are history.

AND: my system is way more responsive and stable regarding audio and video playback. No dropped frames or sound glitches anymore.

I have to add, that my PC is pretty old, though: AMD XP1600+ (1.4GHz) with 1GB DDR1 PC2700 RAM, USB2 and SATA PCI-Cards, nVidia GF7600GS. Virtually everything I do, especially surfing the web, reading mails, listening to audio and watching video ramps up my CPU load to 100%.

So .. I'll keep sticking to linux-rt kernel from now on for two reasons: it's stable (the default ubuntu kernel is not), and on my ancient PC it's just way better.

---

### Post by OmniCloud on 2008-05-19
> The problem is not the length of the release cycles, but the number of new features that are being crammed into each release. Sure, Ubuntu looks very innovative that way, but it hurts stability. Although my current Ubuntu system is working very well, there are some minor issues, and some of my past installations had show-stoppers which were eventually fixed but very inconvenient nonetheless.

What we DON'T need, are over-the-top threads like this one. It doesn't take much to realise that the majority of Hardy users are getting on just fine. This sort of scaremongering and denouncements only hurt Ubuntu's development, while doing nothing to fix the actual problems behind the complaints.

Please just read what he said...Ubuntu is like Sid--works for some, others um..not so much. 

It'll iron out eventually. This unfortunately, is just how Ubuntu releases get down. Debian might be too slow for some, but there idea of releasing a distro "when it's ready" is arguably just...better:)

I still love my bunut tho. I usually always come back.

---

### Post by Gatemaze on 2008-05-20
> **Hadraniel said:**
> I want to add something to my last posting: I changed to the linux-rt kernel and my lockups are history.

AND: my system is way more responsive and stable regarding audio and video playback. No dropped frames or sound glitches anymore.

I have to add, that my PC is pretty old, though: AMD XP1600+ (1.4GHz) with 1GB DDR1 PC2700 RAM, USB2 and SATA PCI-Cards, nVidia GF7600GS. Virtually everything I do, especially surfing the web, reading mails, listening to audio and watching video ramps up my CPU load to 100%.

So .. I'll keep sticking to linux-rt kernel from now on for two reasons: it's stable (the default ubuntu kernel is not), and on my ancient PC it's just way better.

What are the differences between the real time kernel and the normal one? Are there any guidelines on how to install it? Thanks.

---

### Post by Tech Eddie on 2008-05-20
Hi Guys

Here is what seems to be wrong:

1: Kernel 2.6.24 is not completely stable. This can be seen with wireless devices in particular. This issue is not limited to the ubuntu distro. Compile and install 2.6.25 instead.

2: If you have firefox 3 then install firefox 2 instead. FF3 is beta!

3: The latest nvidia driver should be at nvidia.com (Don't know anything about ATI cards - sorry)

4: There may also be problems with SATA controllers crashing the PC.

If you can avoid / fix the above then chances are you will be OK.

---

### Post by odysseusjak on 2008-05-20
I have to change my toon.  I was on 7.10, then went to 8.04.  I initially had some problems and went back to 7.10.  After a month, and looking through the forum, I found that my main problem FF and then I used a devs technique for getting my Ati Radeon 9000 to work with compiz.  Now, everything is working extremely smooth.  So, I have to recant and say, like ALL OSes, one must do a little tweaking to get it to work.  Heck, I remember I had a difficult time with 3dFX card in my Windows box and that took a while to get it worked out.  And I do this for a living!  For over 10 years!  Again, I understand that some people have problems with 8.04, but there is a difference between the 'worst Ubuntu version yet' and what's actually going on.  I guess it might be correct to state that it is/was the 'worst Ubuntu version yet' for the original poster.

---

### Post by oasick on 2008-05-20
I think that that Hardy must to delay the launch, like dapper 2 years agor. Firefox 3 is unstable with many pages and very slowly

---

### Post by Gatemaze on 2008-05-20
well, i am not convinced (at least in my case) that my heron system is crashing due to firefox 3, as it has crashed when i was not running it or when i was running epiphany.

---

### Post by senorian on 2008-05-20
Quote:Originally Posted by Gatemaze  
I have only one question... how will we find out that the issues with heron have been resolved? i doubt canonical will have an announcement on their front page?

This question has been seconded by a few posters.
Every day there seem to be many updates (from my experience using 6.06)
Are these updates incorporated into the version that one downloads; or is it necessary to first download and then update?
This seems to involve a lot of extra downloading time.
Perhaps I have not understood how the process works.
so:
"how will we find out that the issues with heron have been resolved?"
thanks

---

### Post by chewearn on 2008-05-20
> **senorian said:**
> This question has been seconded by a few posters.
[I]
...edit...[/I]

"how will we find out that the issues with heron have been resolved?"


You will never really find out.  Why?  Nobody has access to your PC, except you.  If you don't install and check the problem is still there, who will know?

If tomorrow I develop telepathic powers, maybe I might somehow tell you the problem has been resolved.  :mrgreen:

However... no fear.  No despair.  In July, we will get 8.04.1.  There should be a new iso for this.  Download it, try it.

.

---

### Post by Gatemaze on 2008-05-21
> **AstalaVista said:**
> You will never really find out.  Why?  Nobody has access to your PC, except you.  If you don't install and check the problem is still there, who will know?

If tomorrow I develop telepathic powers, maybe I might somehow tell you the problem has been resolved.  :mrgreen:

Ehm.... I am not sure I fully comprehend you. If you fix a bug then you know that it is fixed. You don't need any kind of telepathic powers to do that.

> **AstalaVista said:**
> 
However... no fear.  No despair.  In July, we will get 8.04.1.  There should be a new iso for this.  Download it, try it.
.
That's good news I guess.

---

### Post by roderick on 2008-05-21
I have been following and providing feedback throughout the thread. 

I have found this to be a fine release personally. However, I do believe this to be due to my situation... I use Kubuntu, which is KDE based.

From all the issues posted here, all the problems seem to be related to the following:

1) Gnome/GTK+ (Firefox, GVFS)
2) Proprietary Video Drivers (ATI/nVidia) with Compiz

Under my system, I run KDE, and hence no GTK+ and I use Konqueror which uses the Qt library. Never had any issues what so ever with Konqueror.

As well, I have an Intel Video card and have had no issues with it, even when I enabled the desktop effects (other than the occasional kde decorator crashing which is simple to restart with fusion-icon installed and running in the system tray).

Kubuntu does not come with compiz pre-enabled, which I think was the best decision they could have made regarding the desktop effects. I believe if the Ubuntu distro had not pre-enabled compiz, you would see less grumbling as I am sure many of the reported issues are related to compiz + GTK+ + Proprietary drivers (anyone else using Kubuntu/Konqueror that can confirm)? 

Just some observations....

Anyway, I just re-installed using a fresh CD install, and no updates, and ran through it 100% flawlessly. Tested the system and found no problems with slowdowns, lockups or otherwise. My equipment was detected 100% (Acer Aspire 9410).

Hats off to the Kubuntu team for a great KDE release (3.5.9).

---

### Post by tbranham on 2008-05-21
I've been doing some digging of my own, like roderick just mentioned, and the more I tick things off of the list which could cause the problem, the more difficult the problem seems to become.

If you take a look at the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996) you'll see that this is happening to all types of hardware. As soon as somebody says "I think it's x, y or z," someone comes along with a counter-example.

We have 1 laptop which is having problems which has ATI graphics, and one desktop with Intel graphics. To top it off, there are individuals with headless servers experiencing the problem too. So, scratch X, right?

Quite a few people have experienced the problem with wireless cards -- we're not using one.

Firefox 3? My girlfriend is using Opera.

SATA vs. PATA: We've got both with problems.

Use a real-time kernel? No dice.

Use the Gutsy Kernel? No dice.

Anyway, this bug is quite frustrating. My girlfriend does not have the time to change distros at the moment, so her lappy will continue to have problems; but I'm going to migrate the desktop to something else until the problem is solved.

If anybody is interested (and doesn't mind wading through the hundreds of posts) there are a boat-load of log files attached to the bug report. Perhaps somebody can find something in there that everybody else is missing? Maybe, if I can find the time, I'll compile a list of the hardware configurations from those logs which are having the trouble. Maybe that will shed some light?

---

### Post by Gatemaze on 2008-05-21
> **roderick said:**
> I have been following and providing feedback throughout the thread. 

I have found this to be a fine release personally. However, I do believe this to be due to my situation... I use Kubuntu, which is KDE based.

From all the issues posted here, all the problems seem to be related to the following:

1) Gnome/GTK+ (Firefox, GVFS)
2) Proprietary Video Drivers (ATI/nVidia) with Compiz


I am sorry but I had to respond to this... I also don't think that it is a Gnome's fault and that the KDE does not suffer from it considering that:
1. There are KDE users that have reported the same lockups
2. AFAIK other recently released Gnome based distros do not suffer from lockups at the moment, although I am not aware which if they use a different version of Gnome from Heron. They certainly use the latest kernel in contrast to the one in Heron.

The issue is that there is absolutely no pattern of what might be the cause, at least to us the users. I  really hope there is as by no means I would like to be in the position of the Ubuntu hackers at the moment as their debugging job is extremely difficult.

Heron is by far the best release of Ubuntu so far for me, as everything worked right out of the box (even at Drake I had to do some minimal tweaking), except from the instability problems that it currently has, making it inappropriate for development pcs. For whover his/her system works are lucky, for whoever not (including me) very tough luck. Even worse for people that have eradicated their older systems when upgrading to Heron (was lucky enough to avoid that). But, the thing was that there were high expectations from Heron, considering that it is a long term support release, and many people (including me) (falsely?) believed that stability was taken for granted in this particular release.

I am confident though that the developers are trying their best to resolve the issues and we will soon have an Ubuntu for all.

The Heron strikes back.

---

### Post by malangaman on 2008-05-21
> **senorian said:**
> Quote:Originally Posted by Gatemaze  

Perhaps I have not understood how the process works.
so:
"how will we find out that the issues with heron have been resolved?"
thanks

I have read every post in this thread so far and I monitor this thread regularly. When the frequency of negative posts decreases, I will know the problems are being corrected. When the negative posts decline to zero, I may consider an update to Heron. Meanwhile, I am as happy with Gutsy as it is possible to be with an operating system.:guitar:

---

### Post by stalkier on 2008-05-21
Latest Hardy is good on both my systems. Laptop is Compaq Presario V2000 series, 120GB hdd, 128MB ATI 200M, 1.5GB DDR. Desktop is a custom built AMD Athlon XP+ OC'ed to 1.54GHrz, 512MB DDR, 40GB hdd, 64mb ATI graphics (AGPx8).

No issues at all, even using Broadcom chipset. Perhaps I am lucky.

---

### Post by decoherence on 2008-05-21
Something seemingly random like this is usually the result of bad interaction between two or more pieces of software.

I haven't had the problem, and I haven't read this thread from end-to-end (though I did make use of the search feature) all the same I'd like to see more people trying to ssh in to their crashed systems.

One common thread is X11. If X goes down, the computer will appear to be completely crashed. I see people trying Ctrl Alt Backspace, but that just restarts X, possibly making it crash again.

My search didn't turn up anyone who tried Ctrl Alt F1, so that'd be something to try for anyone experiencing this. Also found one mention of not being able to ssh in to the machine... anyone else?

The system should not become completely unresponsive for any reason short of a kernel panic. sshd or a console must surely still be running?

---

### Post by tbranham on 2008-05-22
> **decoherence said:**
> ...all the same I'd like to see more people trying to ssh in to their crashed systems.

...My search didn't turn up anyone who tried Ctrl Alt F1...

The system should not become completely unresponsive for any reason short of a kernel panic. sshd or a console must surely still be running?

Most of your suggestions are good, general purpose ways to (gracefully) recover from a catastrophic crash. We've tried all the usual bunch: Ctrl-Alt-Del, Ctrl-Alt-Bksp, Ctrl-Alt-F1, etc. We have had zero luck with these. I have had 2 occurances (one on each of our affected boxes) where the magic Alt-SysReq-_ commands will work.

In my case, SSH does not work. I've tried 6 times on my partner's laptop with no success.

My girlfriend has, on occasion, been able to interact with an open terminal. As strange as that sounds, she has been able to issue a halt command. The characters take, on average, 30 seconds to appear on the screen; naturally, knowing this, we have left the laptop running for 20+ hours while in this state, just to see if it will "clear up" on its own. It doesn't.

I think the issue here is actually more frightening than you think -- the kernel is clearly in a panic, but it is not even responsive enough, at a low level, to do what it is supposed to in such circumstances.

---

### Post by Gatemaze on 2008-05-22
> **decoherence said:**
> Something seemingly 
The system should not become completely unresponsive for any reason short of a kernel panic. sshd or a console must surely still be running?

Oh yes it does, nothing is responding (in my case at least). No X restart, no exit to a terminal, not even my caps lock is highlighting, not even my hardware mute button (i think).

I have never seen a linux system crashing as such before :D. The only warning is a half a second stuck of the music I am usually playing and then kaboom.

---

### Post by decoherence on 2008-05-22
tbranham and gatemaze, thanks both for your patient replies. I'm reading through the kernel bug report now. "Frightening" is a good word for it. 

I wish I could reproduce it so I could help more in fixing it. This sort of thing is supposed to never, never happen. The folks in "the Cathedral" must be feeling pretty smug, reading this.

Anyway, I'll keep reading...

cheers,

---

### Post by gimmic on 2008-05-22
I've been running hardy since release without problems in the office. Now that I'm on the road, I'm getting random hard freezes. I've narrowed it down to my network card(intel 4695 AGN) causing the problem. Under heavy network traffic it seems to cause some kind of panic and my system hard-locks.

What steps should I do to get some diagnostic information(if any) to where it needs to go? Rather annoying..

---

### Post by starcannon on 2008-05-22
I disagree with the OP, I am having a stellar experience with Hardy, its my favorite release to date.

My only beef with Hardy is FF3, but thats as simple as downloading an older version of Firefox and installing it myself /shrug no biggy.

---

### Post by geezerone on 2008-05-23
But isn't FF3 still in Beta? When it gets released hopefully this will sort any FF3 issues.

---

### Post by Tech Eddie on 2008-05-23
Hey people

Just a thought:


Anyone tried this: removing their network card or disabling their network chip. Turn the power off for the PC for a few minutes and then boot Ubuntu.

See if it is now stable.

---

### Post by gimmic on 2008-05-23
> **Tech Eddie said:**
> Hey people

Just a thought:


Anyone tried this: removing their network card or disabling their network chip. Turn the power off for the PC for a few minutes and then boot Ubuntu.

See if it is now stable.

My lockup is very clearly due to my wireless nic / drivers. Worked fine in feisty and previous. Hardy is 100% stable if my wireless isnt in use.

---

### Post by keithpeter on 2008-05-24
> **Kaparen said:**
> Yeah, got the same problem. I use 'blank screen' as my screensaver and it made Ubuntu 8.04 freeze. I took the easy way and turned off my screensaver completely and I haven't had a problem since. I think I will giver Kernel 2.6.25 a shot later tonight. 

I use the 'Blank' screen saver on my Asus Pundit AMD dual core. Networking is cabled into an ADSL modem/router, no setting up was needed. Not using wifi. Wakes up fine, although I've noticed the fan comes on when the screensaver starts.

I had some issues with Firefox on the beta (going grey and quitting). Not seen similar since clean install from the release ISO and subsequent upgrades.

---

### Post by jfl on 2008-05-24
[FONT="Comic Sans MS"]I've upgraded 2 machines, a Lenovo Laptop and a "homebrew desktop from 7.10 to 8.04 - and did it the risky way, with the "Update Manager".
I was too lazy to burn a CD !!!
Both have been running for a couple of weeks with no problem (knock on wood).
Actually, the upgrade "fixed" a video glitch I had on boot-up ...

[/FONT]Sometimes you are the bug and sometimes the windshield !!!

---

### Post by u-slayer on 2008-05-24
I agree. 30% of the time when I startup and double click on a video to launch it with VLC, the whole system locks up completely. I am seriously considering downgrading to gutsy.:(

---

### Post by Th3Professor on 2008-05-24
> **fdimmling said:**
> Me not. 

Installed Hardy on an Acer 4652 LMi with 1GB RAM and Intel 940 Graphics. Works quite well except for ugly Chinese characters which is due to a font substitution problem. 

Friedrich

OT?: How do you resolve the Chinese font issue?

---

### Post by Hypo_Mix on 2008-05-24
> **erginemr said:**
> Here is a candidate for the origin of hard freezes:
[http://forum.compiz-fusion.org/showthread.php?t=8065](http://forum.compiz-fusion.org/showthread.php?t=8065)
this seems to be very similer to my problem..
so thats my vote.

---

### Post by mooscape on 2008-05-25
I have switched to the _real time _ kernel of Hardy, as I was having random total crashes. Even at startup and shutdown. Since then no crashes at all ...touch wood, just sometimes seems a bit tardy.  I will be happy to hear that this problem is acknowledged (yeah, if you haven´t experienced it, that doesn´t mean the problem´s not there!) and resolved. I like Hardy and would like to move it onto all my machines.

---

### Post by Rayaz on 2008-05-25
Newbie here, have been with Ubuntu for just two months. Started out with Gutsy and later a clean installed Hardy. I haven't had any lock ups yet. My laptop is a Compaq Presario, Intel Celeron 1.6 GHz, I.5 GiB RAM and an 80 GiB Hard drive. I am really confused as to why some people should have lock ups and have to move to other Linux distros or Windows and some like me have no problems? What does one make out of all these posts? Could we have some developer input here?

---

### Post by decoherence on 2008-05-25
> I am really confused as to why some people should have lock ups and have to move to other Linux distros or Windows and some like me have no problems?

Well, Mr. Newbie, I'd say you've hit the nail right on the head! What makes this such a distressing issue is that there is a lot of bad behavior going on for some users, but it isn't particularly consistent, though the end result is always having to reboot your system. Users who you might think would share the problem don't necessarily, and users who don't seem to have anything in common are experiencing these similar issues. 

I think that may indicate that there is more than one problem at work here. It's generally when you have a couple of issues that affect each other that you see this 'random' bad behavior. Basically, you have to assume that the behavioral pattern is so complex that nobody has noticed it yet. Some people thought they did but eventually their theories get blown out of the water by somebody else's experience. Which again indicates to me there are at least two different issues. Possibly a failing of a certain subsystem that manifests differently in different programs/libraries/modules that rely on it.

> What does one make out of all these posts? Could we have some developer input here?

If you're looking to know what the developers think, I suggest the mailing lists, launchpad.net and the irc channels. I'm not sure the developers you're looking for are monitoring this thread. We're of course interested in hearing about any correspondence you have.

---

### Post by keithpeter on 2008-05-25
> **miksuh said:**
> As I said, I'm not trying to convert anyone. but if you have problems with Ubuntu then try Debian. If you can use Ubuntu then you can use Debian too. Debian Etch is wery easy to use.

And so it is, packages are older (OpenOffice 2.0 instead of 2.4) and no 'bling' with the nv driver for the Geoforce 6150 integrated graphics :(.

---

### Post by RSingh on 2008-05-25
Well it seems people have noticed it. Even I am having the same issue. Run a video and the system freezes. Audio runs, i Can move my mouse and thats it. I cant ever end the session via the 'kill xserver' key combo. IT seems to be a animation plugin bug by the look of it:
[URL="http://forum.compiz-fusion.org/showthread.php?t=8065"]
http://forum.compiz-fusion.org/showthread.php?t=8065[/URL]

---

### Post by Hypo_Mix on 2008-05-25
> the full fix isn't in the packages yet (though it should be in soon)

i haven't been around linux long, how long are we talking (ballpark) when they say soon?

---

### Post by senorian on 2008-05-26
I've just read through the 52 pages (obviously I'm retired and have too much time on my hands)
My main observation:

Data accumulates but is not cumulative.

No-one commented on miksuh's observation that the number of applications in each succeding version is increasing; so that however appropriate a 6 month release might have been in the past,it will at some point become insufficient time. ( or the number of developers must increase) 

Some years ago I read on some forum that, in the poster's opinion, there were 10 times as many "installers" as "users" of Linux systems. This may be a smaller ratio now but the comment still seems applicable to some extent. Perhaps a consequence of this is that many posts from "installers" do not acknowledge that a "user" needs a working box.Many of the posters here talk about having a lot more than one computer. So that if one screws up they still have another to fall back on.
Yet I cannot remember seeing any Linux promoter advising newbies that they should have at least 2 computers, so that they have a way of getting on-line to get help (although perhaps not from this thread!)
I am using 6.06.
I have looked at each of the subsequent versions with an eye to upgrading but have been put off by the problems that apparently come with the upgrade.
The Hardy situation seems similar to the earlier vesions.
Must I buy a second computer?

---

### Post by roderick on 2008-05-26
Dual boot is much cheaper. Better still, a live CD will do in a pinch. I've used that to rescue me from problems and found a solution in 5 minutes that got me back online.

Dont be so dramatic :) Theatre major perhaps :P

---

### Post by Th3Professor on 2008-05-26
> **senorian said:**
> I've just read through the 52 pages (obviously I'm retired and have too much time on my hands)
My main observation:

Data accumulates but is not cumulative.

No-one commented on miksuh's observation that the number of applications in each succeding version is increasing; so that however appropriate a 6 month release might have been in the past,it will at some point become insufficient time. ( or the number of developers must increase) 

Some years ago I read on some forum that, in the poster's opinion, there were 10 times as many "installers" as "users" of Linux systems. This may be a smaller ratio now but the comment still seems applicable to some extent. Perhaps a consequence of this is that many posts from "installers" do not acknowledge that a "user" needs a working box.Many of the posters here talk about having a lot more than one computer. So that if one screws up they still have another to fall back on.
Yet I cannot remember seeing any Linux promoter advising newbies that they should have at least 2 computers, so that they have a way of getting on-line to get help (although perhaps not from this thread!)
I am using 6.06.
I have looked at each of the subsequent versions with an eye to upgrading but have been put off by the problems that apparently come with the upgrade.
The Hardy situation seems similar to the earlier vesions.
Must I buy a second computer?

There is one all-inclusive summary that can be derived from the general development of Linux and Linux-based systems: It is not Unix.

If you have experienced frustrations from using Linux systems, give Unix a try.

(I like both, so I don't discourage either; actually, I encourage both. For what it's worth: both are great... depending on the task at hand, one is just right, and the other is just right for another task.)

One outlook on Linux and Unix, put back to back...

Some might perceive Unix as an operating system that is geared for a specific audience that comes with a particular set of applications that have been optimized for that system. Consistency from version to version is something of a strength in Unix operating systems.

Some might perceive Linux systems as more diverse, including developers from several different backgrounds, though systems with more lenient of a standard. Not having so strict a set of standards has perhaps introduced the inconsistencies that exist, and have existed, with Linux systems.

Although Unix operating systems, either SysV or BSD, have spanned out to allow for functionality closer to that of Linux set-ups, the Unix systems still maintain the clear and concise operating capabilities that they've always had, since before Linux came about. Linux systems, on the other hand, while perhaps less "solid" are probably more well-known for their ability to emulate characteristics of both SysV and BSD Unix systems. However, Unix systems, also, now emulate the same characteristics. So, in some cases you can just flip a coin. (In some cases.)

All of that can apply to differences - or similarities - in commands, tools, file systems and their tools, software releases and updates, and documentation. Or more, you tell me...

I figure: there isn't one system to rule them all... nor is there truly one system that realistically covers every single imaginable need. There is the right system for a specific task, and another right system for another task.

---

### Post by majickmann on 2008-05-27
WOW !!!  

Considering myself very lucky!  Hardy installed on four computers, 2 PC's and 2 laptops...  all running fine without any difficulties.

Just my 2 cents...
:-)

--majickmann

---

### Post by tefflox on 2008-05-27
**** the stats.  I just downright agree.  Hardy sucks.

***Hey, teachers, leave them kids alone!***

---

### Post by tefflox on 2008-05-27
oh yeah, i googled "make you cry +hardy +ubuntu" to get here, in case any admins could give a **** (or even be able to choose which one, if they coulllllld!)

---

### Post by Bubba64 on 2008-05-27
> **tefflox said:**
> oh yeah, i googled "make you cry +hardy +ubuntu" to get here, in case any admins could give a **** (or even be able to choose which one, if they coulllllld!)

If your trying to get banned why not just save yourself the hassle and quit posting. There must be better things that might be of interest to you.

---

### Post by RSingh on 2008-05-27
Hey guys lets not diverge.

I had 3 lockups in a row yesterday. Last one on playing a normal AVI. Whats strange that System Log doesn't register anything.

Also a few things I have noticed that even though there is a lockup, The system still keeps running. I noticed this when I was running exaile in the background, I tried playing the video and the screen froze. I could still move the mouse. I waited for the song to finish and strangely the song ended and the next one started. Its as if only the Xserver freezes but the system in the background is still running!!!!:confused:

Also, I noticed that this crashed seems to happened on the first video played on boot. If the first video plays correctly then any other video if played will not create the similar crash.

---

### Post by saugumas on 2008-05-27
LOOKS like there are MICROSOFT employees writing in this forum, I wont be surprised if ms are giving bonus to they salary for such posts.. :)

I have upgraded to Hardy few weeks ago and have to say it is very stable, even if I made errors when experimenting with stack and pointers in C++, so far OS have never locked up!
 My friends from university using Hardy too, and don't have problems.
I am using Acer Aspire 5110, amd turion x2, mobility radeon x1600.

---

### Post by ukripper on 2008-05-27
Upgraded from Gutsy to Hardy.I am having lockups under 2.6.24.17 kernel with compiz enabled. Disabling compiz doesn't lockup my machine but not running compiz really makes my machine living hell without compiz as typing gets very slow. I am probably going to give kde a try. Perhaps it is just locking up under gnome. 

It could be my ndiswrapper drivers which I manually installed and blacklisted in modprobe and loading from rc.local(due to system hanging at boot, if i don't blacklist  ndiswrapper during boot then system fails to go past init). This locckup is bizarre on my machine as it is completely freezing up the whole system, not just the xserver. Only hard reboot recovers the xserver back, no other key combination works.

My next step would be to try KDE and if it doesn't work, i am going to compile the latest .25 kernel.

I still have to say Ubuntu devs done a great job with Hardy LTS, everything just runs much quicker than gutsy on my machine except freezing issue which i know will be fixed soon otherwise I have to hunt it down to fix it.

---

### Post by G33 on 2008-05-27
I have to agree, i have had no success with Hardy. Still Ubuntu is better than any Microsoft OS.

---

### Post by Antman on 2008-05-27
[http://ubuntuforums.org/showthread.php?t=809281]("http://ubuntuforums.org/showthread.php?t=809281")
Explains why I'm giving Hardy another shot.

---

### Post by RSingh on 2008-05-27
I have to agree with the above post. Just today after checking for updates I got around 50 megs. A major kernel revision has come along with other fixes. Hopefully they should iron out some of the issues.

---

### Post by DrumScum on 2008-05-27
I'm one of those people with lots of Hardy issues, but I'm not complaining. I just went back to 7.10, which runs rock solid, and will give 8.04 another chance in a month or two, or maybe skip it completely and wait for 8.10.

I also had to skip 7.04 because it didn't like my PC, so I stayed with 6.10 back then. No problem for me.

Now I only miss the new transmission (wonderfull bt-client) en FF3. Liked those very much in Hardy.

---

### Post by ukripper on 2008-05-27
> **ukripper said:**
> Upgraded from Gutsy to Hardy.I am having lockups under 2.6.24.17 kernel with compiz enabled. Disabling compiz doesn't lockup my machine but not running compiz really makes my machine living hell without compiz as typing gets very slow. I am probably going to give kde a try. Perhaps it is just locking up under gnome. 

It could be my ndiswrapper drivers which I manually installed and blacklisted in modprobe and loading from rc.local(due to system hanging at boot, if i don't blacklist  ndiswrapper during boot then system fails to go past init). This locckup is bizarre on my machine as it is completely freezing up the whole system, not just the xserver. Only hard reboot recovers the xserver back, no other key combination works.

My next step would be to try KDE and if it doesn't work, i am going to compile the latest .25 kernel.

I still have to say Ubuntu devs done a great job with Hardy LTS, everything just runs much quicker than gutsy on my machine except freezing issue which i know will be fixed soon otherwise I have to hunt it down to fix it.

Switched back to 2.6.24.16 kernel revision and no lock up so far. So I guess there was something latest in 24.17 rev which didn't like my hardware.

happy so far...going to give 2.6.25 a go if I get any freezes in .24

---

### Post by RSingh on 2008-05-28
> **RSingh said:**
> I have to agree with the above post. Just today after checking for updates I got around 50 megs. A major kernel revision has come along with other fixes. Hopefully they should iron out some of the issues.
 Well update from last post.

Even after the kernel update, the lockup problem is still there.
I believe its got something to do with Compiz. From now on I'm gonna disable Compiz before running a video. I'm tired of hard rebooting my system. I've already done that 25 times!

If only this problem is fixed, then I have don't have any other issues with this release. Therefore I'm gonna stick with Hardy. I believe Hardy is a good improvement over Gutsy in multiple areas.

---

### Post by bigbrovar on 2008-05-28
i dont know about the new updates .. but i use to have lockups the first time i installed hardy heron.. i downgraded to gutsy and it stopped and the system became so stable that i got bored.. decided to give hardy another try and i have not had one lockup since .. and that was a week ago.. system is still rock solid..

---

### Post by Tech Eddie on 2008-05-29
> I believe its got something to do with Compiz. From now on I'm gonna disable Compiz before running a video. I'm tired of hard rebooting my system. I've already done that 25 times!

I'm going to try disabling compiz when I get home. Thinking back my troubles started around the time when I installed compiz fusion. Looking at the version number I am now almost certain that this is the culprit.

---

### Post by mooha on 2008-05-29
I agree ... this is the worst ubuntu version yet !!!

---

### Post by vikramaditya on 2008-05-29
My box is approaching 5 years old.  I've used Feisty, Gutsy, and now Hardy (all clean installs) with virtually zero issues.  Compiz doesn't do well, but I figure that might be blamed on my old ATI Radeon 75 PCI graphics card.  I've tried KDE with both Gutsy and Hardy, but the eye candy imposes a performance hit I can do without.  Still, I've *never* experienced a lockup or any of the other craziness that gets posted around here.  I can only surmise that most problems occur at or near the junction of new hardware and unrealistic expectations.

---

### Post by neslot on 2008-05-29
You might try checking this link:
[http://www.edspace.com/blog/?p=161](http://www.edspace.com/blog/?p=161)
I don't know if this has been mentioned in this thread yet.. sorry..  didn't go through all 54 pages..  :)
seems that tracker is running unthrottled and high priority.. 

tony

---

### Post by neslot on 2008-05-29
You might try checking this link:
[http://www.edspace.com/blog/?p=161](http://www.edspace.com/blog/?p=161)
I don't know if this has been mentioned in this thread yet.. sorry..  didn't go through all 54 pages..  :)
seems that tracker is running unthrottled and high priority.. 

tony

---

### Post by mlemanczyk on 2008-05-29
Yeah, it's locking up randomly for me, too. There are better days, when it doesn't lock up and much worse, when it locks up every few mins :-(

Yesterday I decided to get back to Windows, but luckily I found out this thread. I'm on -rt kernel right now & we'll see, how it goes :-)

---

### Post by SSJxGojita on 2008-05-29
NOT FOR ME.

$ uname -a
Linux LT10E17 2.6.24-17-rt #1 SMP PREEMPT RT Thu May 1 16:23:33 UTC 2008 i686 GNU/Linux
$

I've installed Ubuntu Studio 8.04 (clean install), did a kernel upgrade once and so far nothing is broken. No hang ups whatsoever unlike Ubuntu 8.04 where occasionally I get the BusyBox screen. :guitar:

---

### Post by Tech Eddie on 2008-05-30
Disabling compiz made my system stable! :guitar:

Rsingh is definately onto something.

Should that not help try Neslot/Tony's suggestion:

> You might try checking this link:
[http://www.edspace.com/blog/?p=161](http://www.edspace.com/blog/?p=161)
I don't know if this has been mentioned in this thread yet.. sorry.. didn't go through all 54 pages..
seems that tracker is running unthrottled and high priority..


If you're still having trouble after that check if you're networkcard/chip is the problem. Shutdown the PC and remove the networkcard/disable the networkchip in the bios. Boot ubuntu and see if it's stable. If you have a wireless internet connection you can see it's stability status here:

[http://linux-wless.passys.nl/query_hostif.php](http://linux-wless.passys.nl/query_hostif.php)

Hope this helps you...

---

### Post by Mighty_Joe on 2008-05-30
> **vikramaditya said:**
> I can only surmise that most problems occur at or near the junction of new hardware and unrealistic expectations.

Yes, we all know extrapolating from your single data point is a valid statistical method for determining what is wrong in everyone else's situation.
I have a system that's rock solid with Fiesty and hangs  [within 10 minutes of booting Hardy]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/227882") (live CD, hard disk, doesn't matter).  
The same system runs Fedora 9 flawlessly. I replaced Hardy's kernel with the Intrepid Ibex kernel as detailed in the link above and had no problem with hangs.
How is it an "unrealistic expectation" that Hardy "just work" like the Fiesty, Ibex and Fedora?

---

### Post by Lowcountry on 2008-05-30
> **Mighty_Joe said:**
> I replaced Hardy's kernel with the Intrepid Ibex kernel as detailed in the link above and had no problem with hangs.


Can you elaborate how to do that?
Thanks

---

### Post by Mighty_Joe on 2008-05-30
> **Lowcountry said:**
> Can you elaborate how to do that?
Thanks

There's links in the bug I posted above and more consise instructions are in [this post]("http://ubuntuforums.org/showpost.php?p=5047838&postcount=119").
Fedora 9 is based on the same kernel version (2.6.25) as Intrepid Ibex with some distribution-specific patches.  If you suspect the same problem I'm seeing you may want to try the [Fedora 9 live CD]("http://fedoraproject.org/en/get-fedora") before screwing around with your hard disk install.
If that fix works for you, feel free to follow up in my bug or [this topic]("http://ubuntuforums.org/showthread.php?t=765510")

---

### Post by mooha on 2008-05-30
> **HunterThomson said:**
> Why move to Fedora? Why not just use Gusty which worked so well? That is what I did.:KS

Give freedom to people, let them say what they feel, the man is sick and tried, if he feels like going to what ever, he is free !!

---

### Post by starcannon on 2008-05-30
No lockups at all here.

I have it running on 
[LIST]
[*]Asus Eee 4g and 8g
[*]Dell Inspiron | 5100
[*]HP dv2600
[*]Custom desktop with twin 7950gt's sli'd
[*]Custom desktop with 6600gt
[*]Dell 1420n
[/LIST]

Not a single one locking up. Indeed my experience has been so far that Hardy has been the easiest and most stable (i don't use FF3b5 though).
Anyway, I can see that your very frustrated, but if its really as bad as all that I'd just backdate to Gutsy and wait for the next incremental release perhaps (assuming you did put /home on its own partition)

GL

---

### Post by wateenellende on 2008-05-31
Oh irony ... I wanted to post "It's not so bad." but my computer froze.

---

### Post by chewearn on 2008-05-31
> **wateenellende said:**
> Oh irony ... I wanted to post "It's not so bad." but my computer froze.

That's an undocumented feature, lol

---

### Post by mlemanczyk on 2008-05-31
Well, I have had partial success with -rt kernel. It didn't lock up. But on a regular basis wireless was loosing the connection and couldn't connect anymore, so I had to reboot anyway. I just could do it in a clean way.

Now comes the interesting part. My lock ups seem to be definitely related to wireless. What's more interesting, it seems to be related to key ring interval & WPA encoding. Today I'm in a different network, connected to Asus wireless router. So far so good. Wireless in -rt didn't stop working.

I'll see, if wireless problems come back :-)

---

### Post by gasparov on 2008-05-31
I agree 100% .... hardy sucks sucks and again sucks. 
Jes....this is the worts release ever And I can tell cause I've been using ubuntu since it was born in 2004.

I have a laptop that doesn't suspend and hibernate (it used to. "implemented" in hoary 5.04) , I have no virtual consoles, and mostly this s**t hangs for no reason and the kernel panics just because you leave it there for an hour.

Is thereany MS guy working in ubuntu right now? Jesus, I've tried a few distro (my main distro is gentoo ) and I've never seen something so bad...

---

### Post by weaver4 on 2008-05-31
My computer locks-up when no one is around.  It is a desktop that I  do not put into standby, but I do have it turn off the monitor.  The computer is just sitting there and it may sit for 4 hrs to 4 days before it locks up.  Nothing going on, I may have Thunderbird and Firefox still running but that is it.  It is not just a video problem because the computer disappears from the network too.

When it locks up I need to do a hard reset of the machine.  I know it is not hardware because 7.10 ran fine on it and my other dual-boot is Windows and it runs fine.  (Windows runs fine, Linux lock up; that sounds strange).

Absolutely nothing in the log files to help me diagnose the problem.

Any ideas on how to fix the problem?

---

### Post by SiN_AmoR on 2008-05-31
guys, I updated my system and believe it or not ..
it didn't freeze since then !!
even though i'm using the Generic kernel !!

---

### Post by ShangTsungOmega on 2008-05-31
I have a slightly different lockup scenario. It only happens when I install either the ati drivers from the ubuntu repo or the proprietary drivers from ati. From what I gather though it is an Xserver issue. I ran the live cd and hardy worked fine. I installed  on one of my hd's. It only locks up when starting the Xserver. If I dont install the drivers it doesnt so Yeah it really is random issues.

---

### Post by weaver4 on 2008-05-31
Which generic kernel? And where did you get it?   I noticed that 2.6.25.1-generic is no longer available at ppp.launchpad.net anymore.

---

### Post by dad311 on 2008-05-31
My system (Ubuntu) had been rock soild for 3 + years.  After upgrading to Hardy Im also getting lockups.  After dealing with this for the several weeks, Im going to give Fedora a try.

---

### Post by hogwartsnigel on 2008-05-31
Hi Guys,
Newb here and always will be..have to agree Ubuntu has sent me to the arms of openSUSE (I'm blind eyeing the whole MS thing). I have tried for a week to get help with the familiar NVIDIA config issues...I am so over it. I've tried latest NVIDIA drivers, inc beta, compiled for the latest kernel, i've messed with the xorg (Phew) and I am sat here on dual monitors 800x600. It is killing me. I'll come back maybe on 8.10 but Suse 11 looks appealing.
Saying that Hardy is working great on a box with an fx5700-deluxe in it and looks great and no lockups.

anyone wanna help I have a death of NVIDIA thread stating my probs.

Ta
Nigel

---

### Post by Stik on 2008-06-01
Shut off powernowd 2 days ago and not one lockup since....

---

### Post by ukripper on 2008-06-02
2.6.24-16-generic kernel , Hardy 8.04 - Uptime 12 days no lockup at all since using 24-16

---

### Post by SiN_AmoR on 2008-06-02
I'm using 2.6.24-17-generic ..
more than a week since the last lockup !!

---

### Post by seulas on 2008-06-03
> **SiN_AmoR said:**
> I'm using 2.6.24-17-generic ..
more than a week since the last lockup !!

For me, its even worse with that version...

---

### Post by ukripper on 2008-06-03
> **SiN_AmoR said:**
> I'm using 2.6.24-17-generic ..
more than a week since the last lockup !!

For me it hangs my xserver every 15 mins while running even one app.

No problem with 24-16 in that matter.:)

---

### Post by fiestytom on 2008-06-03
I haven't had my computer freeze more than my windows box (which is like never) the only problem with this ubuntu release is that i can't specify more memory for my video card... maybe xorg will send a patch?

---

### Post by ukripper on 2008-06-03
> **fiestytom said:**
> I haven't had my computer freeze more than my windows box (which is like never) the only problem with this ubuntu release is that i can't specify more memory for my video card... maybe xorg will send a patch?

Don't  you have to use BIOS to set shared memory  for onboard graphics card? :confused:

---

### Post by MDSmith2 on 2008-06-03
> **wateenellende said:**
> Oh irony ... I wanted to post "It's not so bad." but my computer froze.
Lol that sounds more like Windows.
I think that hardy is the best Linux distro i have used (I have used SUSE 7.3 pro, Xandros 4.0, Fedora 8 (Which was pretty good but there was no out of box support for athros card or nvidia card) and Ubuntu since feisty.) Its the most stable and easyist (if I were to start linux cold turcky again, it wouldn't be as hard as SUSE 7.3) Its open source and free and isn't a microsoft puppit (unlike Xandros) it has out-of-the-box support for athros and nvidia cards (my only complaint from Fedora) and is the best of the ubuntu distro (give it some time, it will get better when its got more updates in the next few months).
I have a
AMD athlon MP 1800+
nvidia geforce4
pc chips m484a
and geniric every thing else and can still run flightgear.

---

### Post by wolfen69 on 2008-06-03
isnt this thread solved yet? or is it the goal of everyone here to keep this going for years? nobody is going to go thru all 500 posts. let it die already. everyones point is duly noted. can you say recurring discussion?

---

### Post by weaver4 on 2008-06-03
No it is not solved yet!!  It appears to be a kernel problem and we are all waiting.....for a fix.

---

### Post by hvacr on 2008-06-03
Not even close to being fixed it seems.

---

### Post by jimv on 2008-06-03
I added this repo to my sources list, and I can see a 2.6.24-18 kernel, so I'm going to give that a try.  2.6.24-16 and 17 both have been randomly locking up...though today it seemed worse than before.

```
deb http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main
```

I'll post how it works.

---

### Post by erginemr on 2008-06-04
I have read somewhere that the realtime kernel **linux-image-2.6.24-*-rt** that you can install from Synaptic puts an end to the hard lock-ups at the cost of several miliseconds delay while starting applications.

Worth a try if you ask me...

---

### Post by ukripper on 2008-06-04
Has any one tried the latest 25.4 yet? [http://www.kernel.org/](http://www.kernel.org/)

i am going to give it a go this weekend, although my issue is resolved by using 24-16 but let see if it makes any difference  during bootup as in speed.

---

### Post by sargetech on 2008-06-04
> **adityakavoor said:**
> I agree:mad:

Well I think It's like using a new recipe!!!!
not everyone uses the same oven!!! aka Hardware!!
I'm still using Dapper Drake and it works fine and dandy!!!
I use a total of 5 Internet browsers for Web access.
have made friends with the terminal!!!! (using command line).
love it, love it, love it,:guitar: I just refuse to upgrade
something that just works so well.... so much better than
Mr.Gates Windows XP- Xtra Pathetic.... Pappy was right!!!
If it ain't broke Don't fix it.....:)

---

### Post by Mighty_Joe on 2008-06-04
> **ukripper said:**
> Has any one tried the latest 25.4 yet? [http://www.kernel.org/](http://www.kernel.org/)


2.6.25 fixes the hang problem for me. 
[bug report here]("https://bugs.launchpad.net/ubuntu/+bug/227882")

---

### Post by dlinear on 2008-06-05
What is going on? It appears that the 2.6.25 kernel will fix this lockup but the devs have removed it from the ppm. Why is there no easy way to go to 2.6.23 or 2.6.25?

I made my own 2.6.25 vanilla kernel (without sound!! dammit) but have no interest in figuring out why the nvidia driver I compiled for this version is no longer loading. 

Since this appears to have been known for 2-3 months with no fix in sight (since it breaks normal kernel logging) and appears on varied hardware I have no option but to go to a different distro (fedora). (I cannot use an older version since most of my hardware is not supported). I am just plain tired of not being able to sleep through the night wondering if disabling (_fill in the blank here_) will fix my kernel locks.

A system which freezes randomly is useless as a server or desktop, period.

EDIT
Forgot Fedora, after install I was in bad place. I am attempting a 7.10 install now, hopefully it won't be to tricky getting my hardware working on this... AND that this mysterious bug is not there.

---

### Post by fishdude21 on 2008-06-05
> **Jim March said:**
> Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

A bug has been issued to the kernel team, priority high, marked "triaged":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

Today I did a fresh install from the release CD, standard 32bit, Intel945 video, Atheros WiFi, all standard parts on an Acer laptop that handled Feisty and Gutsy like a champ.  No overheating.  1.5gigs RAM, swap stats show zero use so it's not corrupted swap.

I don't think the devs are going to be able to fix this one easily.  There's just NO feedback or debugging info possible.  When Fedora 9 releases I may be forced to abandon ship.

This really sucks.

I had this problem as well.  First time linux user and i have an acer 64 bit with atheros wireless.  Everything was working fine and then all the sudden Ubuntu froze up on me.  I did a manual restart and when i came back into ubuntu wireless card just wouldnt connect.  Anyone got any suggestions?

---

### Post by geezerone on 2008-06-05
Have a look at the Atheros posts in the Wireless/Networking section.

I read in this post that maybe the Indexing service is taking too many resources, so try setting that lower (look a page or two back to see here).

---

### Post by hogwartsnigel on 2008-06-06
OK a bit of light relief and humour at my expense (please appreciate my honesty).
Rebuilt my box in celebration of the new UBUNTU beta (yes it goes back that far.
My new Lilan server case, housing a recycled 450w psu, k8ne-Deluxe MB,AMD 3400+ 2400ghz, Nvidia 7300gt, 2gb ram gskill, Dell 1905fp and Mitsubishi 2070sb, 1 lg dvdr/w 1 lg dvd/r,1 3200gb seagate IDE, 1 250GbMaxtor IDE, 2 SATA western d. 120gb (Non raid), 2 USB HDD 250gb Maxtors.
finished hardware at 2am began familiar Ubuntu install, chased the location selector etc and all went well til reboot when I had low resolution issues on cloned monitors, did full upgrades and applied proprietaries etc. Unisntalled NVIDIA everything and installed the latest Nvidia drivers etc...failed. Uninstalled went and used ENVY failed...asked for help, gave up installed SUSE 11beta2 all went well and same thing also got frustrated with the one click install (I liked this previous as being beta was no options for this), tried to install nvidia drivers from site gave up....asked for help then left it and worked on a simultaneous system I was building (wont bore you with the specks but Hardy works beautifully except for a wifi lock out (spontaneously offs the connection and locks you out til reboot) Everything else so bloody easy it was a dream...then back to the old box after downloading Ubuntu Ultimate.
 Installed as regular Ubuntu 8.04 but gave me a head start on the software..but not much good, manual changed suggested xorg, used nvidia settings received xserver errors etc. Reported a like wise low res issue on launchpad blah blah.
Wiped all four drives on my system clean using a secure wipe program only 3 wipes but still and started again...tried a Mandriva disc I had lying around and it gaveit a whirl selling failsafe boot on the live disc it was the first to point to xserver graphics issue...hardware to be checked becasue well quite frankly I was jaded...and guess what....
I forgot to attatch in my late night install the power cable to the graphics card..my check of cables ensuring tightness didn't help as I hadn't put it back in...i laughed I cried I laughed again and In 2 hours have a perfect working ubdated ultimate ubuntu and dual screens at 1600x1200 phew and compiz is sweet.

I Love Linux not in a fanboy sense but in the free community sense and respect all the time and consideration of developers etc. How true that it feels wrong to berate that which is given freely. The moral also is that even the most familiar and easy task can go wrong with the simplest of errors..and gawd how simple can you get...ME!
Please treat me nice, I've been the victim enough here even if it was to my self. Now to cancel that bug report..LOL

---

### Post by reubix on 2008-06-06
I agree and this is bad PR for people switching to a new OS.  I know its free and a lot of people put in their time to release Hardy on time but there has to be better QA in your next release.   There seems to be a lot of problems with Hardy and I hope the next release is rock solid for server and desktop use.

Gutsy was quite stable but Hardy will lock up on me after a while of not using the system and if I move my mouse (EX110 wireless keyboard/mouse combo), the pointer will jitter all over the place,    no disk activity and the system locks up (cant even ssh).  This has happened ever since I fresh installed hardy.

---

### Post by ynnorj on 2008-06-06
what is lockup? is that the same as hanging? Well, I actually just installed hardy yesterday and apparently I'm a newbie...
I've tried to test the sounds, but it just hung up. So I restarted. Then I use wobble effect on the windows, then it also hung up. So I guess I'll switch back to windows until everything is stable with hardy.

---

### Post by Magnes on 2008-06-06
> **ynnorj said:**
> what is lockup? is that the same as hanging? Well, I actually just installed hardy yesterday and apparently I'm a newbie...
I've tried to test the sounds, but it just hung up. So I restarted. Then I use wobble effect on the windows, then it also hung up. So I guess I'll switch back to windows until everything is stable with hardy.

Install updates first and try running a memory test. The reason for a lot of OS crashes is bad memory.

---

### Post by ukripper on 2008-06-06
> **dlinear said:**
> What is going on? It appears that the 2.6.25 kernel will fix this lockup but the devs have removed it from the ppm. Why is there no easy way to go to 2.6.23 or 2.6.25?



There is a very easy way to go and compile the kernel automatically and then install it automatically using kernelcheck app written in python. Check this link - [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563) i installed 25.4 using this app without any problem. Mind it,it may take couple of hours to finish the compilation and installtion process depending on machine. My machine took 2 hours 10 mins for custom kernel on Dual core 3 ghz 1GB DDR2 SATA2.

---

### Post by dlinear on 2008-06-06
> **ukripper said:**
> There is a very easy way to go and compile the kernel automatically and then install it automatically using kernelcheck app written in python. Check this link - [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563) i installed 25.4 using this app without any problem. Mind it,it may take couple of hours to finish the compilation and installtion process depending on machine. My machine took 2 hours 10 mins for custom kernel on Dual core 3 ghz 1GB DDR2 SATA2.

Actually I did it, but since having a custom kernel breaks parts of ubuntu and my video driver was being retarded. 

Instead I installed Gutsy (7.10) and spent the night getting the alsa drivers working and the nvidia drivers working (both by hand). Guess what? No crash!!!!

Also 8.10 alpha is supposed to be released in a week or so. Even though it's prealpha I bet it will be more stable then Hardy.

---

### Post by mdsmedia on 2008-06-06
> **dlinear said:**
> Actually I did it, but since having a custom kernel breaks parts of ubuntu and my video driver was being retarded. 

Instead I installed Gutsy (7.10) and spent the night getting the alsa drivers working and the nvidia drivers working (both by hand). Guess what? No crash!!!!

Also 8.10 alpha is supposed to be released in a week or so. Even though it's prealpha I bet it will be more stable then Hardy.Sorry, but you complain about Hardy being unstable, then you talk about alpha being more stable. Is the problem possibly that YOU want the latest but don't want bugs? Possibly 8.10 will support YOUR hardware better.....maybe not.... but if 8.10 is more stable for you, that's no reflection on Hardy. It seems to me that if you were using Feisty there'd be no problems and then there'd be no complaints....but then you haven't tried 8.10 so you have no idea whether it's better or not.

In short, if you want rock solid, stop looking for cutting edge. If you want cutting edge, stop looking for rock solid. OR, use, say, Dapper....and install your own cutting edge packages, then complain about the packages being buggy.

---

### Post by mocha on 2008-06-07
A few pointers for newbs to Linux:

1)  DON'T apply "tips and tweaks" to your system.  I'm not talking about compiling tweaks, I'm talking about blindly following howto's that tell you to change settings in configuration files.  Trust me, the system is already optimized.  This isn't Windows.

2)  Don't leave your web browser open 24/7.  Get a session manager to automatically reopen your pages the next time you open it and close it down when you don't use it for extended periods of time.  I think this alone would save most folks from system lockups.  There are a lot of bugs in Firefox and Flash especially.

3)  Use programs from the official repos only.  If you MUST install something that isn't in the repos, compile it from source.  Don't add any repositories to to your sources.list except the official ones.  I keep all the progs I compiled from source in /usr/src so I can keep track of what I installed and can uninstall it if necessary or re-compile it when a major kernel update comes.  You'll also learn a lot more about your system and Linux in general when you compile programs.  It's not that hard after you do it a few times.

4)  Make sure your hardware is supported.  Double check the hardware compatibility lists to make sure there are no known bugs with your hardware.  Check your memory at least once before concluding that your hardware is ok.

My personal experience is that Linux is very stable compared even to Windows XP.  I've used many operating systems over the years personally and professionally and wouldn't consider ever going back to Windows now that I've harnessed the power of Linux.  I don't have anything against Windows though, I just think it's more limited and kludgy to use.  It's still great for playing a lot of 3D games though.

---

### Post by tucurious on 2008-06-07
I agree that this version has been more of a problem than normal.
However in a fairly short time I got everything to work.  At this
time I have no regrets. My skill level is probably below the norm
for posters. It helped to load Hardy on a clean hard drive and
keep my old Feisty available for awhile.
Don't panic at the criticism, but don't ignore it either.

---

### Post by doktormiod on 2008-06-08
Hi, I experienced this lockups too and i've tried every solution i found on this forum but none of them solve the problem. I read that this can be 2.6.24 kernel problem so finally i compile 2.6.25 and for a day or so everything seemed to work fine. Eventually I wanted to run compiz therefore I had to install fglrx. I installed the latest version from ati, run compiz --replace and a few seconds after my system froze on **2.6.25** kernel! To confirm that it's not kernel issue I installed some older gutsy kernel (2.6.22) and after some time it also froze :/. When i was using this kernel on gutsy it never locked up so here's what i think - It's not kernel issue and not compiz couse my system freezes when compiz is off too. It seems that proprietary driver for readeons is the problem becouse my freezes started after i installed it. Compiz and things like that could be kind of a trigger for real issue.

So why freezes happens to nvidia users too? ATI/Nvidia released buggy drivers simultanously? I don't think so :/

---

### Post by tyk on 2008-06-08
i have had hardy (kernel 2.6.24-18 now) on my quad core q6600 with 4gigs ram and a ati x300 of old. i pretty much had to upgrade (sound was eeerrrppp on my 7.1 through my incessant playing around with it :) there was a choice to reinstall 7.1 but i thot wtf and did a fresh install of hardy.
with all updates and still decent amounts of 'playing around' with it, i seem to have a perfect system. mind you the playing around was not to solve problems but to add some stuff like x-plane, virtualbox, vmware player and other such fun things that if you dont do, i dont see what you are doing..
i still have a particular freeze, easily reproducible and also nominally solvable. if i log off from my session while another user is also logged in, the session automatically tries to shift to the other users and boing, it freezes. i tried it with the two real users and made a test user to try it too. everytime it happens. the solution was to simply not to log off but to reach the login screen by 'switch user' option. it never froze hung gave any probs whatsoever...
syslog recognized the problem with the same entry everytime:
non-syntax: firegl-fglrx component has effed up and i am dying....
i am using the catalyst 8.3 or 8.4, drivers.
i say can anybody else try this log off thing?
lastly i cant agree with this topic, the heron is magnificent :)

---

### Post by weaver4 on 2008-06-15
It has been two months!  When is this problem going to be fixed?

I have dual boot machine, windows and Ubuntu 8.04.  Windows runs so much more reliable on the same hardware.  My machine will freeze or even reboot when no one is touching it.  

Has the problem been identified?  Is a fix in the works?  I would of never guessed that Ubuntu would of allowed such a major problem to go unfixed for so long.

My machine is a simple Intel 3100 graphics  with no special chipsets.  Unit never goes into standby.

My machine has auto updated the kernel twice since the initial release, I keep thinking this update will fix it and it doesn't.

Ubuntu -- at least give an update to the community.  If you are ignoring the problem then tell us so we can move on.

---

### Post by Chainz on 2008-06-15
Unfortunately I have the same problem on Hardy, Kernel: 2.6.24-18 :(

Have tested it on two completely different machines (totally different architectures) - it hangs on both :( 
From time to time... It even hanged during installation once (from Live CD), then right after fresh install... then randomly.

I found one thing (one small pattern) that always can hang my system:
when I select "Molecule" (or something like this) screen saver.

For me it's something related with graphics.

---

### Post by nomeat on 2008-06-15
I have been a satisfied Ubuntu user since 5.04 but since Hardy I have become a satisfied Open SuSE user.
Both Kubuntu and Ubuntu Studio 8.04 have left me with only head aches.
Spontaneous errors that I only know from Windows and I can't reproduce except the screen saver issue. Shutdown only with mains switch on the power supply.
If it is my crappy hardware or my total incompetence, why do the former Ubuntu versions work? 

I really wish  there was some feed back from the authorities.
It seems all the ppl who complain here are considered morons or something.

---

### Post by Th3Professor on 2008-06-15
> **nomeat said:**
> I have been a satisfied Ubuntu user since 5.04 but since Hardy I have become a satisfied Open SuSE user.
Both Kubuntu and Ubuntu Studio 8.04 have left me with only head aches.
Spontaneous errors that I only know from Windows and I can't reproduce except the screen saver issue. Shutdown only with mains switch on the power supply.
If it is my crappy hardware or my total incompetence, why do the former Ubuntu versions work? 

I really wish  there was some feed back from the authorities.
It seems all the ppl who complain here are considered morons or something.

If you cannot reproduce the incident, maybe you could look into various log files, such as /var/log.

---

### Post by Ludwig9 on 2008-06-15
I have no experience with Linux before using Hardy. Recently my computer has begun to crash (screen goes dark, nothing works, must turn off machine and restart it). It does this mainly when I am in Evolution mail, and especially when I click on a url link in an email. Any suggestions: is there a better mail system than Evolution?

---

### Post by Gatemaze on 2008-06-15
> **Ludwig9 said:**
> I have no experience with Linux before using Hardy. Recently my computer has begun to crash (screen goes dark, nothing works, must turn off machine and restart it). It does this mainly when I am in Evolution mail, and especially when I click on a url link in an email. Any suggestions: is there a better mail system than Evolution?

Although a bit off the main topic.... there are many alternatives (not necessarily better, my favourite being mozilla thunderbird (with the lightning plugin you can have a calendar too).

---

### Post by ukripper on 2008-06-15
> **Ludwig9 said:**
> I have no experience with Linux before using Hardy. Recently my computer has begun to crash (screen goes dark, nothing works, must turn off machine and restart it). It does this mainly when I am in Evolution mail, and especially when I click on a url link in an email. Any suggestions: is there a better mail system than Evolution?

thunderbird is quiet good and also i mainly use kmail and like the way you can customize that thing very easily just like thunderbird.

---

### Post by Th3Professor on 2008-06-15
I've used Thunderbird, it's not bad.

I generally enjoy MUTT... though the computer with Ubuntu Studio uses the default (Evolution).

...never had any probs with lock-ups using Evolution.

Actually, no lock-up problems of any sort, not sure if there could be one unifying cause for other hardy-version users experiencing lock-ups.  ???

---

### Post by ukripper on 2008-06-16
I find Evolution most stable and quicker app as compared to kmail or thunderbird, its downside is customization(look wise).

---

### Post by Gatemaze on 2008-06-16
Well, I guess if you are a Gnome user evolution or thunderbird are much better options than kmail considering the memory savings that would be required from kmail. And they also startup faster.

Any latest news on the main topic? From what I see not much progress, unfortunately. I can also verify that after applying all updates on my system, it still hangs. :(

---

### Post by Th3Professor on 2008-06-16
> **Gatemaze said:**
> Well, I guess if you are a Gnome user evolution or thunderbird are much better options than kmail considering the memory savings that would be required from kmail. And they also startup faster.

Any latest news on the main topic? From what I see not much progress, unfortunately. I can also verify that after applying all updates on my system, it still hangs. :(

Real quick OT: disregarding the gnome vs kde thing, how do evolution and kmail compare?

---

### Post by karellen on 2008-06-16
> **Th3Professor said:**
> Real quick OT: disregarding the gnome vs kde thing, how do evolution and kmail compare?

I prefer KMail over Evolution, it's faster and it does everything I need

---

### Post by ukripper on 2008-06-17
Kmail has more features and looks good but not as fast as evolution under ubuntu probably under kubuntu it might be quicker.

I do use both on same machine under ubuntu. Evolution is really quick to open up and does the job for me of retrieving and sending mails using SMTP and POP3 and very straight forward to configure. 

Kmail imports my dbx files easily through wizard from my other windows machine, that is why I use it and also very customizable.

---

### Post by dlinear on 2008-06-18
To get back on topic...

> **Th3Professor said:**
> If you cannot reproduce the incident, maybe you could look into various log files, such as /var/log.

Unfortunately that is the main problem with this lockup. It leaves nothing in the logs.

---

### Post by Killer Cop on 2008-06-18
> **adityakavoor said:**
> I agree:mad:

Yeah Hardy really sucks unfortunatly... But it live up to it's name... Hardy Heron... A hardy Heron? Oh I'm so scared...

There's nothing to it what so ever.

I have already switched back to 7.10 again. So I guess I made the switch back even they said I wouldn't.

---

### Post by phoenix_abhi on 2008-06-18
This was there when upgraded from Gutsy to Hardy. I made fresh installation of x86 first and very satisfied. Now playing with x64 and fine except Java. CCSm desklets emerald everything enabled. Going like lightening . I know when Vista was launched there were some bashing from xp users, same stands for the gutsy users they required a little bit more hardware requirements in hardy. But bashing or calling it a worst is not the solution. Do u people want Ubuntu lag behind ? I prefer Hardy over everything

---

### Post by psychomichael on 2008-06-18
> **phoenix_abhi said:**
> I know when Vista was launched there were some bashing from xp users, same stands for the gutsy users they required a little bit more hardware requirements in hardy. But bashing or calling it a worst is not the solution. Do u people want Ubuntu lag behind ? I prefer Hardy over everything

Bashing it and calling it the worst IS the solution...because "in theory" it should alert the developers and others involved in making it a package that "just works" *work*.

I think it's depressing that these issues have not been addressed and anyone who posts a problem is ostracized as a whiner. I have not upgraded to Hardy for that simple reason. Until they come up with a final product that doesn't have the outcry of the current version, I won't upgrade. 

You use Vista as an example, but part of the reason for Microsoft's problems is that they have always been in a hurry to release a product that isn't ready for the public as a whole. Ubuntu, in my mind, was better than that. They put out a development version for the geeks and a stable version for those who don't want to spend months trying to figure out how to fix the myriad problems that come up. We just want a product that works!

Having said that...I do appreciate all the hard work that goes into the releases and those that work tirelessly, and most times thanklessly, to bring out cool versions of Linux. BUT PLEASE! PLEASE don't make the same mistakes that Microsoft made. There's a reason people are flocking to the various forms of Linux.

---

### Post by dmizer on 2008-06-18
> **psychomichael said:**
> Bashing it and calling it the worst IS the solution...because "in theory" it should alert the developers and others involved in making it a package that "just works" *work*.
people are turned off by the "squeaky wheel" method of requesting change.

> **psychomichael said:**
> I think it's depressing that these issues have not been addressed and anyone who posts a problem is ostracized as a whiner. I have not upgraded to Hardy for that simple reason. Until they come up with a final product that doesn't have the outcry of the current version, I won't upgrade.
this exact same thread has been started for every single release of ubuntu. just in case you don't believe me:
[Breezy](http://ubuntuforums.org/showthread.php?t=113385)
[Dapper](http://ubuntuforums.org/showthread.php?t=199838)
[Edgy](http://ubuntuforums.org/showthread.php?t=287486)
[Feisty](http://ubuntuforums.org/showthread.php?t=432273)
[Gutsy](http://ubuntuforums.org/showthread.php?t=611595)

if you read through these threads you'll find that most of the time, the symptoms are identical for a variety of users, but the causes for these symptoms are wide and varied.  everyone seems to assume that since you are suffering the same symptoms that your causes must also be the same.  but this is not true.

> **psychomichael said:**
> You use Vista as an example, but part of the reason for Microsoft's problems is that they have always been in a hurry to release a product that isn't ready for the public as a whole. Ubuntu, in my mind, was better than that. They put out a development version for the geeks and a stable version for those who don't want to spend months trying to figure out how to fix the myriad problems that come up. We just want a product that works!
the best way to avoid this is to participate in the testing of the development releases.  currently intrepid ibex is in testing.   if you participate in this testing, report bugs you find, and work closely during its development you're more likely to end up with a functional release.  more information here: [http://ubuntuforums.org/showthread.php?t=383067](http://ubuntuforums.org/showthread.php?t=383067)

> **psychomichael said:**
> Having said that...I do appreciate all the hard work that goes into the releases and those that work tirelessly, and most times thanklessly, to bring out cool versions of Linux. BUT PLEASE! PLEASE don't make the same mistakes that Microsoft made. There's a reason people are flocking to the various forms of Linux.
if fedora is more stable than ubuntu on a particular machine, there's no reason to force the issue with ubuntu.  i still have one laptop that has never wanted to run ubuntu, but works perfectly fine with fedora.  if it's all about usability rather than involvement with the community and development, then you're better off with something that works for you, even if that means you have to use windows.  there is absolutely nothing wrong with that.

---

### Post by Gatemaze on 2008-06-19
> **dmizer said:**
> 
this exact same thread has been started for every single release of ubuntu. just in case you don't believe me:
[Breezy](http://ubuntuforums.org/showthread.php?t=113385)
[Dapper](http://ubuntuforums.org/showthread.php?t=199838)
[Edgy](http://ubuntuforums.org/showthread.php?t=287486)
[Feisty](http://ubuntuforums.org/showthread.php?t=432273)
[Gutsy](http://ubuntuforums.org/showthread.php?t=611595)

if you read through these threads you'll find that most of the time, the symptoms are identical for a variety of users, but the causes for these symptoms are wide and varied.  everyone seems to assume that since you are suffering the same symptoms that your causes must also be the same.  but this is not true.


Hahahahaha. That's so funny.... But, check the number of pages:
Breezy: 4
Dapper: 1 LTS I repeat 1
Edgy: 13
Feisty: 3
Gutsy: 2

The number of pages here are over 60 and also if you look better there are quite a few threads reporting the same thing. Where there is so much smoke there is usually a fire.

Also in the threads you are referring, with a quick look, people reported sound problems, graphics problems, etc. Here there are so many people which their system completely crashes...

Yes you may have given me a Ferrari but what shall I do with it if it has a 2 litre depot?

---

### Post by psychomichael on 2008-06-19
> **dmizer said:**
> 
the best way to avoid this is to participate in the testing of the development releases.  currently intrepid ibex is in testing.   if you participate in this testing, report bugs you find, and work closely during its development you're more likely to end up with a functional release.

I'll probably do that when I get another computer. I use this one too much.

[quote=dmizer]
If it's all about usability rather than involvement with the community and development, then you're better off with something that works for you, even if that means you have to use windows.[/QUOTE]

Isn't that the purpose of these 60+ pages? By posting here, we are ALL involved in the community and by reporting bugs and problems we are trying to get some help with the issues. A minor problem with sound or video is nothing compared to unexplained crashes. I haven't upgraded to Hardy...so I am not saying that I personally have had any problems or that I even would have problems...but it seems to me that if the previous releases only had a maximum of 13 pages, and this one has over 60, then isn't that cause for action?

I'm happy with Gutsy. It works for me and I haven't had too many problems when compared to the horrors of Windows...but the people posting in this thread are reporting system crashes...which makes it really no better than Windows. Isn't Linux as a whole supposed to be *better*??

---

### Post by an4rew on 2008-06-19
any news on how to fix the lockups, i'm not that experienced with Linux and the only fix i've seen so far is updating the kernel (seems tricky):(

---

### Post by keithyw on 2008-06-19
i just wanted to contribute my 2 cents (yen?) to this thread.  i've been having numerous lock ups with Hardy as well on a home made Shuttle bread box type of system with an NVIDIA card.  at the moment, i have all the recent patches but most of my problems involving system lock ups seem to be derived from Firefox or multimedia.  I don't know if other people are experiencing the same issues, but i've noticed that is where most of the common place lock ups would occur.

So what i had done is try to isolate the problem a little more.  I had rolled back my firefox to a hand installed 2.0.0.14 version (i needed some plugins), got rid of Flash temporarily, took out the CPU power scanner (which i heard caused issues), turned off some features in Compiz (although I don't think it's enabled for my Kubuntu but I did it regardless)  and my system seems fine for the moment.  i've had an uptime of about 3 days now.  This is with the 2.6.24.19 kernel.

This weekend i might try some more intense testing like playing video alongside web browsing.  I noticed most of my crashes came about when I was playing a video and browsing the web simultaneously.  Right now, Firefox is getting some odd "smudging" (for lack of a better term) whenever I move between pages, so I'm not sure if this is because of the NVIDIA driver which got upgraded a few days ago.  If this goes okay, I'm going to try the Flash 10 Beta plugin again.  If things go well for a few days, I'll assume that the recent updates might've cured my problems.

I also have a Dell Inspiron 600M with an ATI card.  I use it as a kind of test machine.  It was playing flash 9 with Firefox just fine.  So I'm thinking that some of my problems might be hardware related on my Shuttle breadbox (most notably the NVIDIA card, which had problems even when I tried upgrading to 7.10 from 7.0.4).

That all said, one comment I have is that I used to be a Fedora Core user but ended up migrating to Ubuntu when Fedora started to become buggy bloatware.  Ubuntu was said to be a very stable and reliable distribution.  When I got my breadbox and installed 7.0.4, I had a great system that was very reliable.  Almost no problems.  Lots of tutorials and such that made me a believer in Ubuntu.

8.0.4 came along and I figured it was time to upgrade my system.  Just going from 7.0.4 to 7.10 was a disaster, probably because of my video card issues.  My laptop was much smoother.  So I ended up backing up all my data files, getting a new hard drive and doing a clean install with 8.0.4.  There was some bugs in the install process, but I managed to get through.  Then occasionally the screen during the login process would lock up and Flash would just lock my system up.  I ended up losing a lot of my favorite applications like XMMS, Gaim (which migrated to Pigeon), and Multi-Gnome-Terminal.  I managed to get these back one way or another, but it was highly disappointing that these applications were simply tossed out in favor of "newer" versions.  No backward compatibility whatsoever, except for Gaim.  Just for XMMS, I ended up losing my playlist which took me years to build an organize.  I went through a lot of pain getting back Multi-Gnome-Terminal as well.

Now, that all said, I have to say that for Ubuntu/Linux to survive or move forward they definitely need to be more customer focused.  Yeah, that does mean it's more "business-like" than just community oriented, but of all the distributions, Ubuntu seems like one of the better, more friendly desktop distributions.  It seems like it has a very good chance of becoming a mainstream desktop, especially with deals with companies like Dell.  However, I've been reading for years about how each new version or particular distribution is taking another step to become a mainstream desktop.

This recent release makes me lose faith in this process.  Obviously, I can't really complain too much since I'm not paying for something like this.  And fortunately, I'm just technical enough to be able to read a few boards or Google around for my answers.  However, most people aren't going to be like me.  This situation from a business viewpoint or the average, every day joe just isn't acceptable.

My friend, who is a FreeBSD nut, was trying to encourage me to move away from Linux/Debian/Ubuntu distributions because of how their process works in terms of maintaining a stable distribution and the fact that you can grab any version of a piece of software that you want, rather than being limited to a version dependent type.  My problem with FreeBSD is that the documentation seemed limited the last time I tried it (which was around the time of version 4).  Maybe it has changed.  But my friend does have some excellent points about some of the chief advantages to using FreeBSD.

For myself, I honestly don't want to have to switch to yet another distribution and re-learn everything. I simply don't have the time for that.  Still, it is tempting when you want a good, stable system.  

Now, I'm not trying to knock the developers or the community.  I really appreciate everyone's effort, which is why I ended up picking Ubuntu after being a loyal Redhat/Fedora user for 4+ years.  But at the very least, I'm hoping that Ubuntu can put more emphasis on the stability and "just works" aspect rather than being a bleeding edge desktop.  To me those areas are what users want ultimately.  It's kinda like Apple's 80-20 philosophy.  You build for 80% of the market; the 20% are features very few people end up dealing with.  Well, maybe people should start reviewing what that 80% of the market with Ubuntu is so that they can nail down the stability aspect and deliver an excellent competitor to the desktop market.

---

### Post by gashcr on 2008-06-20
> **Jim March said:**
> Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

A bug has been issued to the kernel team, priority high, marked "triaged":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)

Today I did a fresh install from the release CD, standard 32bit, Intel945 video, Atheros WiFi, all standard parts on an Acer laptop that handled Feisty and Gutsy like a champ.  No overheating.  1.5gigs RAM, swap stats show zero use so it's not corrupted swap.

I don't think the devs are going to be able to fix this one easily.  There's just NO feedback or debugging info possible.  When Fedora 9 releases I may be forced to abandon ship.

This really sucks.

Well, just something think about... I tried to install opensuse 11 without any success today... It couldn't detect my video card on the live cd, so I couldn't even look at it. So, even when for some people ubuntu seems so bad... At least it works with my hardware.

---

### Post by ukripper on 2008-06-20
> **an4rew said:**
> any news on how to fix the lockups, i'm not that experienced with Linux and the only fix i've seen so far is updating the kernel (seems tricky):(

What kernel are you using currently?

can you do this in terminal:
```
uname -a
```

post output here.

---

### Post by maria-n on 2008-06-20
I'm using Ubuntu (nowadays Kubuntu) since Dapper Drake on a Compaq laptop and - desktop. Only ever had one minor crash. Hardy works also great on the Compaq, installed smoothly and no freezes.

However I just for the first time built my own computer and there Hardy gives all the symptoms as mentioned in this thread. As soon as I start downloading something it locks up, but also when working offline. First I blamed it on my system, so it's a huge relief to see that these problems seem more related to Hardy than to the hardware, especially since XP does work (how much I hate to be forced to use XP, which I didn't touch since using Dapper).
Today I'll try to install Gutsy on this new pc and wait for updates on Hardy that will solve the problems.

It's so sad that this instability in Hardy undermines one of the most strong arguments pro Linux in the "battle" against Microsoft.

---

### Post by ukripper on 2008-06-20
> **maria-n said:**
> I'm using Ubuntu (nowadays Kubuntu) since Dapper Drake on a Compaq laptop and - desktop. Only ever had one minor crash. Hardy works also great on the Compaq, installed smoothly and no freezes.

However I just for the first time built my own computer and there Hardy gives all the symptoms as mentioned in this thread. As soon as I start downloading something it locks up, but also when working offline. First I blamed it on my system, so it's a huge relief to see that these problems seem more related to Hardy than to the hardware, especially since XP does work (how much I hate to be forced to use XP, which I didn't touch since using Dapper).
Today I'll try to install Gutsy on this new pc and wait for updates on Hardy that will solve the problems.

It's so sad that this instability in Hardy undermines one of the most strong arguments pro Linux in the "battle" against Microsoft.

You should try latest proposed updates hardy kernel revision **2.6.24-19** generic, this kernel has fixed problem for many users while helping them i asked in support forum to give this a try and it fixed the freezing problems for them.

You will need to enable proposed updates in system-->Administration-->software sources

and then in terminal run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

after you have sucessfully received the update then just update your grub using below command:
```
sudo update-grub
```

and reboot.

Select the new kernel 24.19 generic from grub menu at bootup.

---

### Post by Gatemaze on 2008-06-20
> **ukripper said:**
> You should try latest proposed updates hardy kernel revision **2.6.24-19** generic, this kernel has fixed problem for many users while helping them i asked in support forum to give this a try and it fixed the freezing problems from them.


I conquer.... from updates from 19th June, my system seems more stable.... still though I had two lockups in 24 hrs.... I will give it a couple of weeks and then post back... but it definitely seems better now....

---

### Post by Supersaiyan.IV on 2008-06-20
I've Narrowed Down The Problem.

I can reproduce the freeze if I repeatedly initiate reads from an ntfs drive. I suppose **ntfs-3g** is the culprit. Otherwise I experience no freezes.

---

### Post by phoenix_abhi on 2008-06-20
By far Ubuntu ditro is the best one I used. My level of experience dating from Windows 3.1, Used Fedora 9 and totally unhappy, Mandriva 2008 good but far below to Ubuntu.
about the lock p- luckily not yet had one. Having Hackintosh, Vista and Ubuntu, I proud of the Ubuntu and pledged rest of the life for it.
Some one has pointed out the number of pages in the threads regarding previous Versions . From Breezy's days Ubuntu have traveled a long journey and arguably the second popular OS in the world. Ubuntu's user base increased 4 fold from Fiesty days and people are started using non intel machines also

The hardware issue is the main culprit behind the lockup, I believe. Is any user of Total Intel PC, have  ever faced these type  problems ?

---

### Post by Mach1US on 2008-06-20
> **Supersaiyan.IV said:**
> I've Narrowed Down The Problem.

I can reproduce the freeze if I repeatedly initiate reads from an ntfs drive. I suppose **ntfs-3g** is the culprit. Otherwise I experience no freezes.

Generic DELL 610 wit centrino ,intel 915 graphics and intell 2200BG wireless yet still... :(

I have the same :( problem since i upgraded to HH this monday. :(
It was working seamlessly until the upgrade.
I'm running 2.6.24-19-generic and it is still doing it.
I have noticed that it happens when the HD-indicator-light is flashing, at first i thought my HD was going but when i booted in XP it was fine so Hardy was definitely at fault.
One more thing i can add that i can kind of control it by stopping my mouse or track pad.
When it start to jam i just let go of my touchpad and it it starts working after a second or two but any time i try to continue it freezes permanently .
Hej developers , please get some solutions , pleeease[-o< ... :cry: ... [-o<

---

### Post by Splinterhood on 2008-06-20
Yep, I didn't try to fix it because I didn't have the time or the know-how for that. When I had Hardy installed, it wouldn't unmount my optical drives, even after I logged out, and sometimes they would disappear all together with my internet. I will stick with gutsy for now. My biggest concern is what is going to happen to the newbies. I started in feisty and it was the ease of use that kept me with linux. I was always woried that Ubuntu was going to get out of control by trying to accomodate everyone with new and neat features that pMS Winblows has or might have. I installed most of the popular distros since then, and stuck with Ubuntu. However, for a newbie user who doesnt know what a terminal is, like me when I first started, this is going to be a very short adventure into unknown territory when simple things don't work like they should.

---

### Post by psychomichael on 2008-06-20
> **Splinterhood said:**
>  I started in feisty and it was the ease of use that kept me with linux. I was always woried that Ubuntu was going to get out of control by trying to accomodate everyone with new and neat features that pMS Winblows has or might have. I installed most of the popular distros since then, and stuck with Ubuntu. However, for a newbie user who doesnt know what a terminal is, like me when I first started, this is going to be a very short adventure into unknown territory when simple things don't work like they should.

Yeah, that's what worries me...I think that new users will be turned off by it. I know if I would have had the problems that everyone is having when first trying Ubuntu, I would have scrapped the idea of Linux altogether.

---

### Post by linkdesink on 2008-06-20
Guys i don't know why you are experience important problems with hardy.For me is the best linux distro ever used.

I installed hardy when released and i think it's more stable than gutsy.

Gutsy for me was very buggy.Randomnly crashes all the time.Hardy is rock solid in my system.

I think that 8.04.1 will solve a lot of your problems.

---

### Post by KrazyPenguin on 2008-06-20
> **Caesum said:**
> Just tried that, lasted for five minutes before total lockup, which is a lot less than usual!

This works for my laptop.  Sometimes after a new kernel update I can go days before a lockup, I reboot, and noapic and nolapic to the stanza, and problem solved.

;-)

---

### Post by zutronius on 2008-06-21
My system crashes were caused by running Avant Window Manager. Disabled it and no system crashes since.

---

### Post by upwinger on 2008-06-21
I dont get it! HH works perfect on one of my laptops. It works perfect on my other Dell as long as I dont try to install and just run it off of live disc...if I try to install it locks up on 5% partition formatting bar. It wont load at all on my new desktop. I am watching the updates on this to see what solution develops.

---

### Post by ukripper on 2008-06-23
problem is not Hardy at all...it is compiz, device drivers, wireless drivers not properly set and kernel compatibilty with them. Till now what i have seen is if I try using different kernel the latest one then there is no issue at all. My issue was just related to  ati drivers not properly loading up during bootup within kernel 24.16, disabling compiz evrything worked. But i had to resolve this issue as i want to use compiz so I used envy for latest ati drivers and instead of using xorg-drivers-fglrx I installed xorg-drivers-fglrx-envy and after that my screen was so smooth that even windows driver would envy it! no lockups anymore for me whether i use 24-16 .18 .19 or even my custom build kernel .25. Everything is just working as expected now..

---

### Post by ukripper on 2008-06-23
> **upwinger said:**
> I dont get it! HH works perfect on one of my laptops. It works perfect on my other Dell as long as I dont try to install and just run it off of live disc...if I try to install it locks up on 5% partition formatting bar. It wont load at all on my new desktop. I am watching the updates on this to see what solution develops.

your problem looks like more of a cd problem rather than lockup issue.

Try burning the cd image again.

---

### Post by markonhismobile on 2008-06-23
I'm experiencing system lockups on my laptop (Philips X57) - although they only seem to occur when using Firefox. At first I thought it might be something to do with it being a beta, but it hasn't stopped since the upgrade to the current version.
The whole system will become un-responsive and either requite a hard reboot or SSH'ing into and rebooting - which can only be done when I'm around as thankfully I've managed to load Putty onto my wifi enabled works mobile (save having to fire up another PC!)

I can see errors in my syslog, but they don't turn up results on google or in here. Once I get access to the laptop again I will try posting them here.

---

### Post by omar8 on 2008-06-23
> **markonhismobile said:**
> I'm experiencing system lockups on my laptop (Philips X57) - although they only seem to occur when using Firefox. At first I thought it might be something to do with it being a beta, but it hasn't stopped since the upgrade to the current version.
The whole system will become un-responsive and either requite a hard reboot or SSH'ing into and rebooting - which can only be done when I'm around as thankfully I've managed to load Putty onto my wifi enabled works mobile (save having to fire up another PC!)

I can see errors in my syslog, but they don't turn up results on google or in here. Once I get access to the laptop again I will try posting them here.

The exact same thing happens to me. It seems to occur when there is some kind of flash running in the browser.
It crashed when I was watching BBC iPlayer, Youtube and the WoW Trial Making website (flash based). I tried avoiding flash and it did not crash all day, then I tried to visit as many flash sites as possible (youtube, miniclip etc) and managed to crash it in about 10 minutes.

---

### Post by ukripper on 2008-06-23
> **omar8 said:**
> The exact same thing happens to me. It seems to occur when there is some kind of flash running in the browser.
It crashed when I was watching BBC iPlayer, Youtube and the WoW Trial Making website (flash based). I tried avoiding flash and it did not crash all day, then I tried to visit as many flash sites as possible (youtube, miniclip etc) and managed to crash it in about 10 minutes.

What graphics card are you using?

---

### Post by cdoebbler on 2008-06-23
Hummh... running Hardy on a Sony Vaio PCG-TR3A and have had some glitches but no major  lockups. Sometimes OOWriter seems to fail with large documents, especially with track changes. I find Hardy supports more hardware and is as stable as Gutsy. It also includes some additions that make it more competive to MS's opeating systems. As long as the tech keep working at it I will keep trying.

What I don't see is automatic bug reporting in Hardy...is it in running the background? Could I have disabled it upgrading?

---

### Post by markonhismobile on 2008-06-23
Just had another lockup, the wife has left the laptop on and here's the last entries from the syslog:

kernel: [ 1779.103170] NVRM: Xid (0001:00): 6, PE0000 0408 00000000 0000de20 00000000 00d6d4d2
kernel: [ 1779.120926] NVRM: Xid (0001:00): 36,  L1 -> L0

My guess would be nvidia driver related....any options considered tho!
The laptop has a Geforce Go7400 and I have Compiz Fusion enabled, along with Avant Window Manager if that helps at all, but as the lockups normally occur in Firefox I'm thinking these might not be related. I will however try some heavy flash based sites later to see if that causes any issues - break.com here I come :-)

---

### Post by ukripper on 2008-06-23
> **markonhismobile said:**
> Just had another lockup, the wife has left the laptop on and here's the last entries from the syslog:

kernel: [ 1779.103170] NVRM: Xid (0001:00): 6, PE0000 0408 00000000 0000de20 00000000 00d6d4d2
kernel: [ 1779.120926] NVRM: Xid (0001:00): 36,  L1 -> L0

My guess would be nvidia driver related....any options considered tho!
The laptop has a Geforce Go7400 and I have Compiz Fusion enabled, along with Avant Window Manager if that helps at all, but as the lockups normally occur in Firefox I'm thinking these might not be related. I will however try some heavy flash based sites later to see if that causes any issues - break.com here I come :-)

Are you using restricted drivers or Envy?

and which kernel version are you using do this in terminal:
> uname -a

---

### Post by MONODA on 2008-06-23
> Just had another lockup, the wife has left the laptop on and here's the last entries from the syslog:

kernel: [ 1779.103170] NVRM: Xid (0001:00): 6, PE0000 0408 00000000 0000de20 00000000 00d6d4d2
kernel: [ 1779.120926] NVRM: Xid (0001:00): 36, L1 -> L0

My guess would be nvidia driver related....any options considered tho!
The laptop has a Geforce Go7400 and I have Compiz Fusion enabled, along with Avant Window Manager if that helps at all, but as the lockups normally occur in Firefox I'm thinking these might not be related. I will however try some heavy flash based sites later to see if that causes any issues - break.com here I come
what is your computer model? I have an HP pavillion dv6395ea with the same graphics card and get the same problems. The problems you are experiencing are most likely due to the fact that the driver is not good, bugs in ubuntu and compiz fusion. I suggest you try another distro.

---

### Post by ukripper on 2008-06-23
you can use envy to install latest drivers rather using restricted drivers from ubuntu repos.

---

### Post by markonhismobile on 2008-06-23
OK, quick update and I'll try to address the questions asked!
I'm running a fully updated Hardy, kernal 2.6.24-19 I think at last check!
The Nvidia drivers are the ones that come as part of the nvidia-glx-new package, and NOT the envy ones!

After a quick google on some of the error's I did see a suggestion to try the slightly older nvidia drivers (nvidia-glx) which I have now installed (after another lockup, could still access via SSH/webmin), but can't test as the laptop is on wireless and no one is there to log it in so I've lost access to it for the time being. Should be able to get back on this evening once I'm finished at work!

---

### Post by omar8 on 2008-06-23
> **ukripper said:**
> What graphics card are you using?

I am using an ATI x1650 Pro AGP with the default restricted drivers (compiz works :) )
I also have kernel 2.6.24-19-generic and following advice from this thread I also installed 2.6.24-19-rt and booted into it, still the same issue.

---

### Post by markonhismobile on 2008-06-23
Had another lockup with the older driver...guess I'll go back to the new one and start trying other things!

---

### Post by ukripper on 2008-06-23
> **markonhismobile said:**
> Had another lockup with the older driver...guess I'll go back to the new one and start trying other things!
 try using 24-18 generic kernel instead of .19

---

### Post by markonhismobile on 2008-06-23
I don't think that's gonna help as the problems have been occuring pretty much since updating to Hardy, and persisted through each of those incremental kernal upgrades!

---

### Post by keithyw on 2008-06-23
just ran Adept this morning and it seemed to have installed the 2.6.24.19 generic image on my system along with a new version of compiz (but i mostly disabled it).  Had to reboot the system for the upgrade to take effect.  After logging in, I ran Thunderbird, which apparently required an update on its own.  Then it halted.  Tried manually killing it with root privileges and that wouldn't work.  Bizarre.

In my terminal, I tried exiting out and then my terminal locked up.  Tried rebooting and the whole system froze.  Had to hard reboot my system.

Went back to 2.6.24.18 generic image.  No problems thus far with that image.  I'm running Kubuntu/KDE and I think I don't have compiz enabled for it.  So I don't know if my problems are compiz related, NVIDIA (i'm using a GEForce 7300GT graphics card) related or if it's the 2.6.24.19 kernel related.  I did cut down on all the visual effects with compiz as some people suggested, killed powernowd from the services and am currently not running flash on my browser (I'm using a hand installed Firefox 2.0.0.14 btw) with the 2.6.24.18 generic image kernel running.  That seems to be a good combo.  My uptime with that combo was over two weeks.

Perhaps with the 2.6.24.19 generic image an old bug was introduced.  I'm still very wary about employing flash on my browser for the moment.  Maybe I might give flash a go tonight and see if I encounter the system lockups I was experiencing two weeks ago.

I have a Dell Inspiron 600M with a built-in ATI card running Hardy as well.  Haven't had a single system freeze yet with that one.  I'll try upgrading it to the 2.6.24.19 generic image kernel and see if I encounter any system freezes there.  If not, I'm willing to bet that this bug might be hardware related.

---

### Post by Mach1US on 2008-06-24
24.18 kernel with all compiz packages removed an using 915 intel grafics chipset but still gettin lockups, never had this problem before ,showed up this monday with upgrade from GG to HH ???
It still happens regardless i use .18 or .19 kernels.

---

### Post by keithyw on 2008-06-24
> **Mach1US said:**
> 24.18 kernel with all compiz packages removed an using 915 intel grafics chipset but still gettin lockups, never had this problem before ,showed up this monday with upgrade from GG to HH ???
It still happens regardless i use .18 or .19 kernels.

have you tried turning off powernowd?  i've read some recommendations that this might be causing an issue.  ever since i switched it off, at least 2.6.24.18 has been working fairly well for me.  most of my noticeable lock ups seem to be derived when using Firefox or using Firefox while watching a movie (non-Flash).

---

### Post by cuby on 2008-06-24
I agree.
I use Ubuntu since 6.? and this is the one with more bugs... I don't even care to report them any more.
List:
 - Cannot clean trash if nautilus is runing as root. (You have to erase the files by command line)
 - several bugs on nautilus related to attribute, user and group changes, especially as root.
 - Nautilus (again) crashes all over the place when you use an ssh mount, taking gnome with him!
 - My dear gnome radio crashes when I try to change the name of my favourite station.
 - Synchronize time with a server has bugs on install, needed to restart x to be able to sync the clock.
 - Dam kernel updates are driving me crazy! They are very large files and I need to reinstall the virtualbox kernel module each time.
 - Ignoble nvidia memory leak is still there after a year. Ok, this is not a Ubuntu problem... but it is very annoying the lack of pressure over nvidia.
 - In one of my laptops the wi-fi stop working with this version and the fault prevented the boot of the machine. (solution: install gutsy, no time the learn how to blacklist modules, at that time)
 - [EDIT] Since a week ago, the only way I can logout is to ctrl+alt+backspace my X because gnome (I presume) stalls on exit and I don't know why. 
 - Etc... I lost track.

Last but not least, almost all this things worked well in gutsy, I don't know what happened. 
But the worst are the continuous updates of the same packages... Provides lack of confidence to the user.

---

### Post by Supersaiyan.IV on 2008-06-24
> **Mach1US said:**
> 24.18 kernel with all compiz packages removed an using 915 intel grafics chipset but still gettin lockups, never had this problem before ,showed up this monday with upgrade from GG to HH ???
It still happens regardless i use .18 or .19 kernels.

The lockups are not kernel related, nor related to any installed program. But are related as to HOW the system is configured during install.

I have FIXED these lockups/freezes on my laptop. The SOLUTION is to make a redistributable & bootable backup with remastersys. Then install the backup on the system again.

Somehow it worked for me, and im glad it did.

---

### Post by starcannon on 2008-06-25
I've now got all my computers, even the Asus Eee's running Hardy, no lockups, no problems, nothing but smooth sailing here.

---

### Post by doktormiod on 2008-06-25
I got ati X1800 and my system is rock solid on default mesa driver - not a single lockup. Freezes start when i install fglrx, i don't even have to use compiz or kwin effects so the system freezes. 2 dyas ago there was an kernel and fglrx upgrade which i hoped would solve the problem but obviously it didn't...
For me fglrx is the problem, i hope someone would finally take care of it...
Really, it's been 2 months since official realese, how much longer can we wait?

---

### Post by malangaman on 2008-06-25
Starcannon, please describe "all my computers", it would help to know how you use them also, to see if certain hardware is more prone to lockups.

---

### Post by MetalheadGautham on 2008-06-25
Lets see...

I run a Pentium 4 Prescott A 2.6GHz Processor with 1MB L2 Cache, an intel D915GLVG motherboard with onboard RealTek ALC880 audio and Intel GMA900 graphics, and 256mb RAM. Quite low, but was once just perfect for linux.:(

1. I am not able to hibernate. it results in just locking session instead.
2. KDE takes hell of a time to start
3. partitions not automounted at startup; needed to do configuration manually
4. can't multitask without risk of crashing
5. increased system requirements to unfairly high values
6. everything, including special effects is unstable
7. Gnome 2.22 sucks compared to Gnome 2.18

And I am talking about Ubuntu 8.04, released an year after Ubuntu 7.04, the OS that introduced linux to me and helped make me a pro.

Infact, ubuntu is so spoilt now, that I needed to switch in order to make my system any good. First I tried Debian Lenny (ditched in 2 days flat), then (and still rocking) Sidux.

I doubt if I would ever see ubuntu once again as the most loved OS in linux land, because it was so fast, stable and secure yet newbie friendly.

Ubuntu has lost mainly the speed and stability it inherited from debian.

The only thing ubuntu has still, and is not available elsewhere is availablity of pre-compiled software in large numbers, with nearly every software ever released available, and all these spread in lots of mirrors which are also easily selectable from GUI tools.

---

### Post by ukripper on 2008-06-25
> **MetalheadGautham said:**
> 
Infact, ubuntu is so spoilt now, that I needed to switch in order to make my system any good. First I tried Debian Lenny (ditched in 2 days flat), then (and still rocking) Sidux.



you may want to change your signature :)
> **Linux is NOT exclusively for geeks I use Ubuntu mainly for gaming and leisure**

---

### Post by starcannon on 2008-06-26
> **malangaman said:**
> Starcannon, please describe "all my computers", it would help to know how you use them also, to see if certain hardware is more prone to lockups.

HP Pavilion dv2600 special edition dual core intel, nvidia 8400m gs, 2gb of ram, 160gb 7200 rpm hdd, intel wifi. The built in webcam doesn't work, but never has (works for 30seconds then crashes).

Self Built Desktop, AMD dual core (x2? i forget), twin Nvidia 7950 gt's sli'd together, 2gb ram. 250gb x2 sata hdd

Asus Eee 4g w/2gb of ram x2, Asus Eee 8g w/2gb of ram.

Self Built Desktop, AMD XP CPU, Nvidia 6600 gt, 2gb ram, 250gb x2 sata hdd

Everex Cloudbook w/vesa driver and 1gb of ram, and 60gb 4200rpm hdd

Dell 1420n with Nvidia 8400m gs, 2gb of ram
Dell 1420n with intel x3100, 2gb of ram

and a couple client machines, I don't remember the specs, but they are running nicely.

---

### Post by malangaman on 2008-06-26
Well, 6 out of 7 have 2GB of RAM and most have large Nvidia cards: could be a factor. More cpu "elbow room".

---

### Post by Mighty_Joe on 2008-06-27
> **Supersaiyan.IV said:**
> The lockups are not kernel related, nor related to any installed program. But are related as to HOW the system is configured during install.

[My experience]("https://bugs.launchpad.net/ubuntu/+bug/227882") has been that it is kernel-related and the 2.6.25 kernel from Fedora 9 or Intrepid Ibex fixes the problem.  It appears that my experience [is not unique]("https://bugs.launchpad.net/ubuntu/+bug/204996")
YOUR problem may not be kernel-related, but my no means is everyone's problem not kernel related.

---

### Post by erginemr on 2008-06-27
Some users have also reported to have put an end to the freezes by replacing the stock kernel with realtime "*-rt" kernel from Synaptic...

---

### Post by ukripper on 2008-06-27
Taken from [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/204996/comments/192)

may help few looking for Ibex .25 kernel.
 
"
[B][B][B]If the issue still persists with the 2.6.24-17 kernel, would you be willing to then test the Intrepid Ibex 8.10 kernel which is currently being pulled together and was most recently rebased with the upstream 2.6.25 kernel. It is available for testing at the following PPA: [https://edge.launchpad.net/~kernel-ppa/+archive](https://edge.launchpad.net/~kernel-ppa/+archive) . The steps to test from a PPA are similar to testing from hardy-proposed except create a file /etc/apt/sources.list.d/kernel-ppa.list to include the following two lines:

deb [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main

Run 'sudo apt-get update' as you did before. You should then be able to install the linux-image-2.6.25 kernel. Once you've finished testing please feel free to remove the files you created in /etc/apt/source.list.d/ and run 'sudo apt-get update' once more to restore your system to its original state. Please let us know your results. We'd appreciate hearing back from you. Thanks Again.[/B][/B][/B]"

---

### Post by PadreSol on 2008-06-27
That bug report that the OP posted is hard to follow, it's kind of incoherent.  Looks like a dumping ground for disparate issues.

I've had lockup problems that look like they are related to evolution but maybe there are networking issues.

I have the latest kernel.org kernel (2.6.25.9 ) and do not use initramfs, do not use loadable modules not using wifi.  There were some evolution updates yesterday, so far today evo has been stable.

Also in the newer kernel there are some USB related errors messages on boot and it does seem that scanning the USB bus takes longer.

My first time with Ubuntu so I don't have a comparison to previous.

---

### Post by shinji257 on 2008-06-27
I'll add here that I am currently running Ubuntu 8.04 x86_64 and it is working just fine.  So far I have not had any lock ups.

Dell E1705
Core 2 Duo 2.0Ghz
Nvidia 7900GS
Intel 3945ABG Wireless
3GB RAM + 4GB SWAP

Snipplet from free (amount in MB) and uname
```

shinji@shinji-laptop:~$ free -mot
             total       used       free     shared    buffers     cached
Mem:          3023        781       2242          0         15        363
Swap:         4118          0       4118
Total:        7141        781       6360

shinji@shinji-laptop:~$ uname -a
Linux shinji-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

```

Note that a driver issue may be the cause of the lockups reported in this thread.  The reason that upgrading (or downgrading) the kernel may fix the issue is because you are not just replacing the kernel.  You are replacing all the driver modules too.  In some cases you will be replacing them with a newer or older version depending on if you are upgrading or downgrading your kernel respectively.

---

### Post by wak_wak on 2008-06-27
With all due respect, I completely disagree.

First off, I'm not one to knock any Linux distro.  After all, not only would I not be able to make the whole thing myself, it's not like I paid for it.

That being said, go back to 7.04.  It's still supported, yes?

All that aside, I've had nothing but a pretty great experience with it.  CODEC support seems much improved, the beta of Firefox it comes with seems great, I've had 0 stability issues and nothing to complain about as yet.

I've got it running on an XPS M1530, Inspiron E1705, Inspiron 530 and have absolutely no problems with any.  But your hardware config does seem a bit more custom perhaps...  Who knows, there's always the last great OS, VAX/VMS.  It's been opened up:)

---

### Post by psychomichael on 2008-06-29
I finally got the chance to put Hardy on a friend's computer. She has an old Dell Dimension 2400 and I wanted to see what all the fuss was about. I've had it on for about a week and the only thing I can complain about is how slow Firefox is at times, but that can be explained away by the lack of memory. The screensaver doesn't work very well with some of the higher-end graphix, but that can be explained away by not having a very big graphix card. 

Overall...pretty decent on this box. Also, I haven't been able to find the system tab that gives me the hardware specs. It was easier to find on Gutsy...

---

### Post by mooscape on 2008-06-29
I switched to the real time kernel several weeks ago and have had no problems since....

---

### Post by rlacroix8 on 2008-06-29
Same here, two lockups, necessitating power disconnection and battery removal on my Dell Latitude D810. I am new to Linux and thought that this type of lockup was a Windows disease.

---

### Post by weaver4 on 2008-06-30
I installed OpenSuse11 and ran the exact same applications on the exact same system and had no lockups.  So it is (IMO)a Ubuntu problem.  Even if it is a kernel problem there is no reason Ubuntu could not use a more robust kernel, like OpenSuse or Fedora did.

---

### Post by ForksHolder on 2008-06-30
Guys,
From what i see now, Hardy is MUCH faster and stable.

I didn't have any Kernel peoblem so i'm staying here.

You can move to Fedora, But APT package manager just rulez.

~ForksHolder

---

### Post by ukripper on 2008-06-30
From what I have seen so far this freeze problem is related to graphics drivers or kernel. So if you are using Ati drivers from restricted drivers and having this issue. 

I would suggest you manually install catalyst drivers using this link - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

use method 2 from this guide, only if you have Ati card. This guide is not intended for any other graphics card but just Ati.

---

### Post by misterhead on 2008-06-30
> **rlacroix8 said:**
> Same here, two lockups, necessitating power disconnection and battery removal on my Dell Latitude D810. I am new to Linux and thought that this type of lockup was a Windows disease.

I to have a latitude d810 currently dual booting Gutsy w/ XP Pro. A few months ago I replaced Gutsy w/ Hardy-Beta. Fans were spinning outa control until lockup, sometimes reulting in an automated complete shutdown in a matter of seconds. Switched back to Gutsy w/ no problems. Downloaded a Hardy live cd this weekend but haven't tried it on my Latitude yet, and not sure if I want to. 
I would like to keep in touch with you, considering we have the same laptop. I'm asuming yourshas the same ATI Mobility Radeon X600?

---

### Post by S1xp4ck on 2008-06-30
> **ukripper said:**
> From what I have seen so far this freeze problem is related to graphics drivers or kernel. So if you are using Ati drivers from restricted drivers and having this issue. 

I would suggest you manually install catalyst drivers using this link - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

use method 2 from this guide, only if you have Ati card. This guide is not intended for any other graphics card but just Ati.

Thanks mate, this seems to be what I need. :)

---

### Post by weaver4 on 2008-06-30
I do not believe it is a graphics driver because I do not have a avi or nividia graphics chip; I have a plane-jane intel 3100 that comes on all their newer chipsets.

But I do believe that it is a kernel problem and graphics drivers are one of many things that can cause it to freeze.

---

### Post by markonhismobile on 2008-06-30
I'm fairly certain the lockups I was experiencing where down to graphics drivers in some way, even though I have tried it with both the nvidia-glx and nvidia-glx-new drivers, the error's reported in Dmesg indicate an Nvidia problem. some people on the nvidia forums reported problems arising from using AWN so I have disabled that and will report back in a week or so if that has helped or sooner if I get another lockup! I had one last night and after SSH'ing into PC AWN was using the most CPU - only 5 or 6% but was just sitting there at the top of the output from top.....

---

### Post by americano70e10 on 2008-06-30
I got to ask, after seeing many of you promissing to go to fedora, is fedora any diferente from the 7 version, cause I dont know if it was only me, but my experience with fedora was a negative one, it was noticebly slower then ubuntu, along with other weird bugs. Is the fedora 8 or 9 diferent? Faster? Cause if it is, I might migrate also, I am a bit disapointed with this version of ubuntu, I installed linux mint and I dont know why, but it was better... I thought to switch to that, but I feel like trying something a bit more diferent, like fedora or opensuse...

---

### Post by kanpachi on 2008-06-30
what if i get random black screens?
the screen just goes black at random times and i have to restart my machine to make it work again
plus, login window manager takes FOREVER to load
maybe it has to do with the fact that i'm using it on a mac mini

---

### Post by zutronius on 2008-06-30
I've also been experiencing lockups on my Compaq F500 laptop. It seems to occur when I am either playing music or watching videos. IT got so bad I had to downgrade to Ubutnu Studio. I'm willing to give 8.0.4 another try. I'm just tired of instability.

---

### Post by mdsmedia on 2008-07-01
> **zutronius said:**
> I've also been experiencing lockups on my Compaq F500 laptop. It seems to occur when I am either playing music or watching videos. IT got so bad I had to downgrade to Ubutnu Studio. I'm willing to give 8.0.4 another try. I'm just tired of instability.If you're so tired of instability, why are you using the latest Ubuntu release? Nothing against Hardy, but if instability is a problem, why are you using Hardy?

I've used Dapper for quite some time. I have absolutely no problem. My desktop has been recently upgraded to Hardy....but it's a machine that isn't relied upon.

Are you after stability or cutting edge? If you want stability, why are you using Hardy? If you are upgraded to Hardy, why are you complaining about stability? Please decide between stability and cutting edge.

---

### Post by armandh on 2008-07-01
a few lock up problems with totem but not with VLC
adding a usb extension and moving the wireless mouse rcvr to a better place helped too. 
IN FACT NOT A HARDY PROBLEM

---

### Post by Mighty_Joe on 2008-07-01
[Intrepid Ibex Alpha 1]("http://www.ubuntu.com/testing/intrepid/alpha1") fixes the random freezes that I was experiencing (described [here]("https://bugs.launchpad.net/ubuntu/+bug/227882")).  I've got 12 hours of uptime with Intrepid as opposed to ~10 minutes with Hardy.

---

### Post by ukripper on 2008-07-01
> **Mighty_Joe said:**
> [Intrepid Ibex Alpha 1]("http://www.ubuntu.com/testing/intrepid/alpha1") fixes the random freezes that I was experiencing (described [here]("https://bugs.launchpad.net/ubuntu/+bug/227882")).  I've got 12 hours of uptime with Intrepid as opposed to ~10 minutes with Hardy.

As it is alpha I won't use it on my production system or daily day to day system. Use it on spare partition for testing only. 

But you may use Ibex kernel's under Hardy as explained by my previous posts in this thread.

---

### Post by weaver4 on 2008-07-01
> **mdsmedia said:**
> If you're so tired of instability, why are you using the latest Ubuntu release? Nothing against Hardy, but if instability is a problem, why are you using Hardy?

I've used Dapper for quite some time. I have absolutely no problem. My desktop has been recently upgraded to Hardy....but it's a machine that isn't relied upon.

Are you after stability or cutting edge? If you want stability, why are you using Hardy? If you are upgraded to Hardy, why are you complaining about stability? Please decide between stability and cutting edge.

I am using 8.04 because it had LTS support.  Also, personally, I thought that Ubuntu would have this problem fixed in a few days; not a few months.  So instead of going back to 7.10 I have been trying to wait this problem out.

---

### Post by Mighty_Joe on 2008-07-01
> **ukripper said:**
> As it is alpha I won't use it on my production system or daily day to day system. Use it on spare partition for testing only. 
But you may use Ibex kernel's under Hardy as explained by my previous posts in this thread.

Would using an alpha kernel in a "stable" release be much different from just using an alpha release? Personally, I'm sticking with 7.04 until this issue's fixed.
BTW, [your instructions]("http://ubuntuforums.org/showpost.php?p=5272511&postcount=647") reference kernel 2.6.25. Intrepid is now using 2.6.26.

---

### Post by markonhismobile on 2008-07-01
Had another lockup last night, even with AWN disabled :-( Was up for most of the day fine tho so I'll leave it off and see if I get them as much as before...

---

### Post by ukripper on 2008-07-01
> **Mighty_Joe said:**
> Would using an alpha kernel in a "stable" release be much different from just using an alpha release? Personally, I'm sticking with 7.04 until this issue's fixed.
BTW, [your instructions]("http://ubuntuforums.org/showpost.php?p=5272511&postcount=647") reference kernel 2.6.25. Intrepid is now using 2.6.26.

yes it will be different because you won't receive security updates from package manager for IBEX due to its alpha nature but you will receive for Hardy. Therefore if you run certain packages like openssh or evolution you won't receive security updates for that and if vulnerabilty is found your system can be compromised. I won't suggest anyone to use alpha release on their main box but create separate partition to use it for testing and bug reporting.

hope that helps.

---

### Post by StormPCs on 2008-07-01
I have been using the 64 bit Hardy on my Asus G1Sn for two weeks now without a single lockup.  I don't know if it is beginner's luck or what, but I am extremely impressed with it.  I run Vista and XP VM's with Sun xVM Virtual Box on this laptop as well, and everything runs flawlessly.

If you are having random lockups it is your hardware, not a bug.  Bugs are repeatable and thus very easy to fix.  My guess is that it's not a bug.

---

### Post by carl_pr on 2008-07-01
i am having the same issues. I used Fedora a few years back and now installed ubuntu and i love it but it freezes constantly after few hours of use.

---

### Post by Mighty_Joe on 2008-07-01
> **StormPCs said:**
> 
If you are having random lockups it is your hardware, not a bug.  Bugs are repeatable and thus very easy to fix.  My guess is that it's not a bug.

My guess is that you are not a software developer.  There's a whole class of bugs [which are elusive and difficult to fix]("http://en.wikipedia.org/wiki/Heisenbug").
In my case, my hardware is stable with Feisty Fawn, unstable with Hardy, but stable with Intrepid (details [here]("https://bugs.launchpad.net/ubuntu/+bug/227882")). 
There is also a [bug report against Hardy of similar symptoms marked fixed in Intrepid]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996"), so I'd venture to say that at least a few people are reporting software bugs, not hardware issues.

---

### Post by animaniac on 2008-07-01
For a LTS, Hardy is quite shaky. I expect Intrepid to be just as rough with all the proposed changes i believe are going to come. Although id guess 9.04 will be Ubuntus "snow loapard" with everything happening under the hood.

I do look forward to 9.04.

---

### Post by doktormiod on 2008-07-01
A day ago i migrated to Interpid, seems everything is working fine, except for fglrx which caused freezes in hardy so i can't tell you if migration was a solution :/ At least i hope so...

---

### Post by Gatemaze on 2008-07-02
Does anybody know what happened to 8.04.1, a patch to 8.04? Cheers.

---

### Post by kevdog on 2008-07-02
Anyone else had success with the Ibex alpha install?

---

### Post by doubtintom on 2008-07-02
I've had success with a kernel rebuild using 2.6.25 running without a freeze for 48 hours and counting. I'm much relieved after so many reboots per day for weeks that I don't want to even try to count.

It looks to me like these problems are kernel problems and have nothing to do with all of the remedies everyone is trying to do with 2.6.24.

First, let me amplify the cautions of the author of the instructions I used. I'd put it this way, compiling the kernel is something no one should ever do for the first time. I have 24 years of experience with writing and building c programs, makefiles, etc. I've compiled and installed plenty of _applications_ from source on my Linux boxen. But this was my first _kernel_ compile. It took me three compiles to get it right. They take 3 hours or so each. I want to fine tune it one more time to get rid of a floppy disk module that is useless on my machine, and making my boots take an extra minute or two.

I'm not trying to scare anybody off, but if you have someone who is experienced with the kernel or at least knows how to program and debug c, you'll be better of with them by your side. You could wind up with a non-working system.

That said, I'm a happy camper and productive once again.

Here are the instructions I followed:
[http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html]("http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html")

best luck
Tom

AMD Athlon 64 X2 Dual Core 4800+, 4GB RAM, WD Caviar 320 GB SATA, A8N32 SLI Deluxe, KDE 3.5.x, 2.6.25, Nvidia GeForce 6600, nvidia-glx-new driver

---

### Post by Mighty_Joe on 2008-07-02
> **Gatemaze said:**
> Does anybody know what happened to 8.04.1, a patch to 8.04? Cheers.

I believe that's just a roll-up of the updates so far released, so if one is installing fresh, they don't have to download a gigabyte of updates.

---

### Post by Gatemaze on 2008-07-02
Yes you are right, latest pack of updates are marked as 8.04.1 in grub.

---

### Post by weaver4 on 2008-07-02
> **doubtintom said:**
> I've had success with a kernel rebuild using 2.6.25 running without a freeze for 20+ hours and counting. I'm much relieved after so many reboots per day for weeks that I don't want to even try to count.

It looks to me like these problems are kernel problems and have nothing to do with all of the remedies everyone is trying to do with 2.6.24.

First, let me amplify the cautions of the author of the instructions I used. I'd put it this way, compiling the kernel is something no one should ever do for the first time. I have 24 years of experience with writing and building c programs, makefiles, etc. I've compiled and installed plenty of _applications_ from source on my Linux boxen. But this was my first _kernel_ compile. It took me three compiles to get it right. They take 3 hours or so each. I want to fine tune it one more time to get rid of a floppy disk module that is useless on my machine, and making my boots take an extra minute or two.

I'm not trying to scare anybody off, but if you have someone who is experienced with the kernel or at least knows how to program and debug c, you'll be better of with them by your side. You could wind up with a non-working system.

That said, I'm a happy camper and productive once again.

Here are the instructions I followed:
[http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html]("http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html")

best luck
Tom


So when will there be a "automatic" 2.6.25 update for all of us idiots?

---

### Post by doubtintom on 2008-07-02
weaver4

I don't know how to specify a kernel for general use or I would do it. The instructions in Gunblade IV's tutorial (link below) are for a kernel specialized to your machine, assuming it already has Hardy installed on it.

I doubt that you are an idiot. I meant no disrespect by my warnings about the difficulty of building a kernel. I was just trying to give others some data to use in deciding whether they should dive into that process. To get in over one's head and fail could add more discouragement to the existing problem. Trying it myself greatly increased my respect for Linus and the kernel developers. I managed to blunder through it, and I don't think it is a newbie task. Everyone will have to judge for themselves where they stand on the learning curve.

One of the most frustrating things about this freeze problem (or set of problems) for me was the lack of clear information about it. Only by spending a lot of time searching and reading has anything like a coherent picture started to arise. These are some of the best links I found.

This fellow gives a pretty good summary of "where we're at"
[https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9](https://bugs.launchpad.net/ubuntu/+bug/227882/comments/9)

The first part of this post, the quote from Ubuntu Brainstorm, gives additional data, although some of the details are arcane to me.
[http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html](http://blog.gunbladeiv.com/2008/05/ubuntu-kernel-2625-on-hardy.html)

If you want to try the kernel compile, I suggest reading up on *menuconfig*. That was the part that threw me the first couple compiles. You have to explicitly enable ALSA there, and possibly other hardware you have, or disable hardware you don't have. If the *menuconfig* screens and options freak you out when you see them, I'd say that is the time to get in touch with a local Linux user group and get some face time with someone who can advise. But if you're into figuring things out and reading up on stuff that's unfamiliar, hey, give it a shot.

And follow Gunblade IV's instructions to the letter.

Of course these forums are full of actual kernel hackers much more savvy than I am, so you've got lots of support if you want it.

best luck
Tom

---

### Post by beerorkid on 2008-07-02
sigh....

I think I fingered out how to solve it for me.

I am running hardy on 3 HP PC's, but only have problems on my work PC
HP w9300
AMD opteron 250
2gb RAM
nvidia 9700

I had the lockups big time and almost always compiz was involved.    More of a slight freeze with severely twitchy cube flips that would restart X.  Went to mint, fedora 9, Ibex, and now back on 8.04 and after googling to figure out how to disable powernowd which I mentioned many times in this thread I found [this thread.]("http://ubuntuforums.org/showthread.php?t=567109")

> I assume that you disabled all power-saving features in the BIOS. Also, set Plug-N-Play OS to "NO"

Disable the parallel port and serial port (temporarily) to free up interrupts in case its an interrupt conflict.

Now I am only 15 minutes into this apparent fix, but it seems to have solved my issues.  Just an FYI

---

### Post by pedrogent on 2008-07-04
I've found going back to 7.10 i386 on my desktop has solved all lock-up issues.

Mind you, I use 8.04 on my eeePC and have never had any lock-ups on that.

---

### Post by Paul86fxr on 2008-07-04
In my opinion, it had a few small fixes to start but has great potential, never under estimate the developers,

---

### Post by rastatech on 2008-07-04
hey experienced Linux Wizards, ("I'm not worthy!") I'm just an Ubuntun00b but as I'm new to linux but old to computing, I think my perspective might be a useful addition to this thread. 
I'm using 8.04 which i downloaded just a couple months ago as the first linux i have ever tried to use as my primary machine. I've played with several various other versions over the years, but Hardy is the first Linux flavor I've tried to use day-to-day for everything I do, which is a lot. ;)

I have to say, I was wondering where the legendary Linux stability was. 

I've had multiple issues that were distinctly Windows-ish in flavor, such as unexpected reboots, system lockups, and [app weirdness]("http://ubuntuforums.org/showthread.php?t=849418"). Coming from the abusive family that is Windows, and having had a Fedora3 install for a while that was also very flaky and unstable, it didn't occur to me that this was all that out of the ordinary. I just figured that rock-solidness of Linux that I've been hearing about for years was just fanboy hype, until I came across this thread which I see has stirred up quite a hornet's nest. 

I'm very gratified to learn that the behavior I've been experiencing is atypical for Ubuntu and Linux in general. For semi-geeks like me who know just enough to know that we don't know nearly enough to go about compiling kernels and such, how should I plan to address this issue? Will I have to re-install a newer Ubuntu when it becomes available, or what?

I Hope that my experience can add some parallax...
twin dual-core AMD64 Athlon if that makes any diff....

---

### Post by pedrogent on 2008-07-04
Hi rastatech.

If you are aiming at avoiding the lock-ups, in this case I would recommend 'downgrading' to 7.10. It's been out in the wild much longer than Hardy so most, or at least more, of the kinks are ironed out now.

I was having constant horrendous lock-ups with Firefox in my 8.04 install. The machine was completely unusable. But since moving back to 7.10 things have been rock solid. (Incidentally, I also moved from an amd64 to i386 ISO which may have helped things too.)

There aren't that many compelling features that 8.04 has that 7.10 doesn't in my opinion.

So if you have the time & energy this is what I'd recommend that you do.

---

### Post by YaroMan86 on 2008-07-04
I haven't had ANY issues with Hardy whatsoever.

---

### Post by steve_c on 2008-07-04
> **rastatech said:**
> I have to say, I was wondering where the legendary Linux stability was.
If you're aiming for the 'legendary' stability of Linux, then Ubuntu, on the whole, isn't the right distribution. The enterprise, mission-critical class stability Linux is known for is better found in distributions like Slackware and probably best of all Debian. Ubuntu is actually derived from Debian because Debian tends to have ridiculously long release cycles. On Debian, you're frequently using versions of applications that have been released for at least a few years.

The upside to that is that after a few years of testing and bug fixing, Debian is solid as granite. The downside is that any new features for those applications or for Linux in general that have been developed in the last few years will be absent from Debian.

That's why Ubuntu was created. They start off with a snapshot of Debian so they have a stable base, then they update some packages (using Gaim, for instance, is almost painful if you've used the updated versions, which are now called Pidgin; you also won't see compiz-fusion in Debian--which may or may not be a bad thing) and they add some features to improve usability and make it more friendly to inexperienced users.

That said, with exceptions such as this thread, Ubuntu is usually good enough. I had no qualms running even Ubuntu Desktop on one of my servers. The newer packages, to me, are worth the small trade-off in stability. If my server were responsible for air traffic control systems or something like that, I might look somewhere else (Debian if I were sticking with Linux, although at that point I'd lean toward QNX).

Also there's more going on in a desktop install of Ubuntu than just the 'legendarily' stable Linux. Desktops add layers of complexity and are more prone to errors. On top of the kernel, you've got the shell (usually a non-issue cause it's pretty rock solid), you've got X11 (which adds waaaaay more problems and potential for error), you've got Gnome on top of that (fewer problems than X in my experience, but still error-prone), and then in newer versions of Ubuntu you've got the compiz window manager on top of that (probably buggiest of all, but that's because it's also the newest and least tested). When I'm saying there are more problems I'm not trying to knock these softwares nor their developers. These are all *very* large and complicated softwares, and considering the degree of difficulty I think they all do very very well. Ubuntu Desktop is easily as stable as most versions of Windows out of the box, and after months and years of use I would almost guarantee Ubuntu Desktop would be considerably more stable and less slowed down from time and use than any version of Windows.

Sorry, that was a really long rant, but I wanted to answer your question thoroughly cause I've heard it several times before.

> **rastatech said:**
> For semi-geeks like me who know just enough to know that we don't know nearly enough to go about compiling kernels and such, how should I plan to address this issue? Will I have to re-install a newer Ubuntu when it becomes available, or what?
Since this particular problem is a kernel issue, either you can read and follow some of the instructions for recompiling a new kernel, you can try switching kernels with aptitude/synaptic, or you can wait for the (hopefully) fixed, updated kernel to be released into the repositories.

Hope this helps.

---

### Post by rastatech on 2008-07-04
@pedrogent & steve_c:
Thanks for the excellent background and info, you guys rock
Ubuntu has a really great communnity, and I've been part of many over the years...

---

### Post by mdsmedia on 2008-07-04
> **Gruss2 said:**
> Can anyone tell me what will I lose if I downgrade back to Gutsy?
I don't want to lose the programs I installed or my settings.It's probably best to start [a new thread]("http://ubuntuforums.org/showthread.php?p=5327573#post5327573") on this. Your question will probably get lost in this thread.

---

### Post by deepclutch on 2008-07-04
my 2 cents: those who dont want to compile and want bleeding edge Linux kernel ,try [http://rarewares.org](http://rarewares.org) repository for 2.6.26 zen sources kernel .debs -they provide nvidia-173.14 IIRC.also ,linux-headers and source too :) 
**The kernel is based on Zen Sources!**
Here is the direct link to the packages:
[http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/)

kernel - for prescott/core2duo and above -
[http://www.rarewares.org/debian/packages/unstable/linux-image-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/linux-image-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb)

headers- 
[http://www.rarewares.org/debian/packages/unstable/linux-headers-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/linux-headers-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb)
nvidia driver-
[http://www.rarewares.org/debian/packages/unstable/nvidia-kernel-2.6.26-rc8-zen1-x0-core2-smp2_173.14.09-2+2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/nvidia-kernel-2.6.26-rc8-zen1-x0-core2-smp2_173.14.09-2+2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_i386.deb)
source(only if u want to recompile):
[http://www.rarewares.org/debian/packages/unstable/linux-source-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_all.deb](http://www.rarewares.org/debian/packages/unstable/linux-source-2.6.26-rc8-zen1-x0-core2-smp2_2.6.26-rc8-zen1-x0-core2-smp2-0rarewares1_all.deb)

**for amd -**
[http://www.rarewares.org/debian/packages/unstable/linux-image-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/linux-image-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb)
headers-
[http://www.rarewares.org/debian/packages/unstable/linux-headers-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/linux-headers-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb)
nvidia driver- 
[http://www.rarewares.org/debian/packages/unstable/nvidia-kernel-2.6.26-rc8-zen1-x0-k8-smp2_173.14.09-2+2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb](http://www.rarewares.org/debian/packages/unstable/nvidia-kernel-2.6.26-rc8-zen1-x0-k8-smp2_173.14.09-2+2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_i386.deb)
source(only if u want to recompile) -
[http://www.rarewares.org/debian/packages/unstable/linux-source-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_all.deb](http://www.rarewares.org/debian/packages/unstable/linux-source-2.6.26-rc8-zen1-x0-k8-smp2_2.6.26-rc8-zen1-x0-k8-smp2-0rarewares1_all.deb)

I posted this if someone would have saved from the lock-ups that is happening with current 2.6.24 kernel :roll:

not good to add this repo to your list IMO .you can download whatever packages necessary :)

Best of Lucks!

---

### Post by dlinear on 2008-07-05
> **mdsmedia said:**
> Sorry, but you complain about Hardy being unstable, then you talk about alpha being more stable. Is the problem possibly that YOU want the latest but don't want bugs?

Am I asking too much? 

Regardless I went back to 7.10 with custom audio, worked great for 1 month (no random Lockups).

Now for two days I have been running 8.10 alpha with great success. After installing the nvidia driver from nvidia things have been working more or less perfect.

---

### Post by mexpolk on 2008-07-05
> **Jim March said:**
> Hardy is BY FAR the worst Ubuntu version yet 

Totally agree with that (but only on Desktop)!!!

---

### Post by ukripper on 2008-07-05
> **mexpolk said:**
> Totally agree with that (but only on Desktop)!!!

I tend to disagree from my experience of installing Hardy on 4 desktops with different hardware configurations.

---

### Post by mikesfx on 2008-07-06
Hi all, just to add some of my experiences in to this thread, I began suffering from lockups since fresh install of 7.10 Gutsy, same symptoms as the rest of you (music keeps playing and all). I also tried upgrading to an RT or realtime kernel and 8.04 LTS but this didn't work in my specific case, as I still had the lockups but I was able to interact with GNOME but couldn't click on anything or use the keyboard. I yearned for the days when I was using 7.10 w/ no problems, then I realized that when I had no problems, it was when I was using a "server" kernel, as the only CD I had handy was a Gutsy Server CD.

I am trying to reinstall the server version of the kernel now through Synaptic. I will add another post if it is successful and solves some of these crashing/lockup problems for me.

-Mike

---

### Post by markonhismobile on 2008-07-07
I had a lockup yesterday evening and as I was sitting next to the wife who was using the laptop at the time I thought I'd try something different to just a plain reboot. I restarted gdm and the machine was once again usuable :-) Admittedly I did this via SSH from my PDA but I can't remember if I've ever tried the keyboard combination to get round it. As I haven't experienced a total lockup yet (i.e completely frozen, can't move mouse) I might be having different issues to the one's reported on here. If/when it happens again I'll try restarting X using the keyboard and report back!

---

### Post by weaver4 on 2008-07-07
Well I guess "freezing" is not going to get fixed.  I will need to go back to 7.10 until 8.10 comes out.

One thing that I have come to love in 8.04 is FireFox 3.  Can I use update in 7.10 to get FF3?

---

### Post by ukripper on 2008-07-07
> **weaver4 said:**
> Well I guess "freezing" is not going to get fixed.  I will need to go back to 7.10 until 8.10 comes out.

One thing that I have come to love in 8.04 is FireFox 3.  Can I use update in 7.10 to get FF3?

yes you can use ff3 on 7.10 it ain't in repos you have to manually install it and it works fine i am using that on 7.10.

check this thread - [http://ubuntuforums.org/showthread.php?t=833036](http://ubuntuforums.org/showthread.php?t=833036)
i used the instructions from here to install mine.

---

### Post by mlekodukye on 2008-07-07
can't even get the internet working on 8.04. on 7.04, i had it working right, so to speak, by default, without any tweaking.

---

### Post by BobSongs on 2008-07-07
I'm currently downloading the ISO for **[Ubuntu's Hardy Heron 8.04.1]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html")**.

Has anyone tested it yet?

On my PC I've gotten powersaving errors as well as some networking message errors. (AMD Athlon XP with nVidia graphics adapter.) I've seen posts and word has it that these bugs are being looked at.

But I was wondering if anyone's tried it yet. My copy of Ubuntu won't automatically update to 8.04.1, so I'm going for "the fresh install".

Well. Here's hoping.

:-D

---

### Post by ukripper on 2008-07-08
> **mlekodukye said:**
> can't even get the internet working on 8.04. on 7.04, i had it working right, so to speak, by default, without any tweaking.

Is it related to lockups? if no then please create another thread in Absolute beginner forum where someone will help you out.

---

### Post by markonhismobile on 2008-07-08
Had another locktup last night, and unfortunately the keyboard combination to restart X had no effect :-( At least restarting gdm from a command line is a bit quicker then a full blown reboot!

---

### Post by MONODA on 2008-07-08
if people are still having problems like these with hardy, why not switch to another distro temporarily? I did and things are going great.

---

### Post by ukripper on 2008-07-08
Well people can always switch back to 7.10 which is officially supported till April 2009 with updates from package manager! By then ibex will be rolling

---

### Post by Igzilla on 2008-07-08
I've been experiencing random lock ups too using Hardy 8.04. It would generally happen when browsing with firefox or copying files over the network, though it would also happen just on the desktop with no programs running. Finally, I reinstalled from scratch, installed the restricted nvidia driver and bang - lockups left right and centre.

So, I installed 8.04.1 and left it downloading another distro all day. I didn't do any updates or change any settings. All fine when I got home 9+ hours later. I installed the latest nvidia driver via EnvyNG..so far so good. No lockups, all my programs installed, network files copied across, all without incident.

In my case, it does seem that the restricted drivers are aptly (or even ironically) named. I would advise anyone to avoid them at all costs. I can't vouch for the ati driver - I have a second machine running 8.04 with an ati card, but I just haven't had the time to test in any way, but I guess I will just go ahead and use EnvyNG without even trying to experiment.

---

### Post by ingvildr on 2008-07-08
> **BobSongs said:**
> I'm currently downloading the ISO for **[Ubuntu's Hardy Heron 8.04.1]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html")**.

Has anyone tested it yet?

8.04.1 so far seems to have solved all of my problems, even the no usplash on logout is fixed for me so i am now finally back on ubuntu :)

---

### Post by mocha on 2008-07-08
Just some tips about these lockup problems.  I've had similar issues in the past and gained some experience troubleshooting them.

First, if you are overclocking your system, even slightly, I recommend resetting CPU/FSB/memory/video etc all back to stock speeds.  I had a Core2Duo system that was overclocked and locking up during heavy disk I/O even though memtest would pass with flying colors and CPU burn in programs didn't have any problems.  Overclocking does weird things to your system after a while.

Use the LiveCD to verify that your lockups occur not only within your installed system.  This is a useful method to determine if you are having hardware or application issues, and can narrow down where to look.

Nvidia drivers, wireless cards, and Firefox/Flash seem to be the most troublesome issues in desktop linux.  Try the free nv driver and Opera or some other browser and see if that fixes the lockups.  Physically remove your wireless card and see if that helps.

Make use of the system logs and terminal.  Run programs thought the terminal, sometimes you might see an error message appear when the machine locks up.  Also use the terminal to monitor system logs, "tail -f /var/log/syslog" or kern.log or dmesg or whatever log you want to monitor.  You might get lucky and see a message appear as the lockup takes place.  You can use egrep to search all the logs in /var/log for keywords, or use the nice GUI searchmonkey in the repositories.

In general it's been my experience that lockups that occur without logging messages are typically hardware related problems.  These are very frustrating problems.  Sometimes you need to bite the bullet and purchase or borrow a new video or wireless card.  As far as disks are concerned, boot with the LiveCD and run fsck with block checking on all your drives.  If you have NTFS partitions, put those disks in a Windows machine to test for bad blocks.  If you have 2 sticks of RAM, remove one then swap with the other, retest, even if memtest says they're ok.

Check which IRQs are being shared.  I believe the GUI hardinfo or sysinfo shows this.  Some hardware doesn't like to share IRQs, try moving cards around in slots or check your motherboard manual for the IRQ sharing information if it's a homebuilt computer.

Anyway, those are just some tips I wanted to share.  I've run Ubuntu on many machines from Athlon XP, Barton, Core2Duo, etc, since Dapper.  I use many periperals, TV card, DVB card, wireless, serial, USB, firewire, I have experienced many lockups over the years but always found out in the end that they weren't really random, there was always a reason.

---

### Post by Chelidon on 2008-07-08
I've had hard lock ups in Gutsy, which were pretty random. Thanks to the above poster I think I've narrowed it down to overclocking. My poor machine was installed with Vista and I suspect Toshiba overclocked it to make Vista run at a reasonable speed.

---

### Post by weaver4 on 2008-07-08
I would doubt that Toshiba would overclock a CPU; getting a 5% speed increase for lower reliability is not something a large company is likely to do.

In this case it does appear to be a problem in the Linux kernel.  The kernel with 7.10 works fine with the same hardware and if you do an unsupported upgrade to the 2.6.25 kernel the problem also goes away.  So this problem appears to be isolated to version 2.6.24 of the kernel.

The kernel developers claim that they found the problem and it corrected in the latest kernel.

---

### Post by mocha on 2008-07-09
Here are some useful commands for troubleshooting:

To search all logs for keywords:

```
sudo egrep -i 'keyword1|keyword2|keyword3' /var/log/* > ~/errors
```

Note I am directing the output of the egrep search to a file in the home directory named "errors".  It's easier to look and search through the file instead of scrolling though the terminal.

To get info on your partitions:

```
sudo hdparm -I /dev/sda > ~/sda_info
```

Again the output is directed to a file for easier viewing.

To run SMART tests on your hard drive, first install smartmontools, then:

```
sudo smartctl -t long /dev/sda
```

Then a few hours later run the following to see the final results:

```
sudo smartctl -l selftest /dev/sda
```

You can also look at the history of SMART errors being logged by the drive:

```
sudo smartctl -a /dev/sda
```

To check a drive for badblocks, boot with the live CD, don't mount the drive, find out which partition you want to scan using "sudo fdisk -l", then:

```
sudo badblocks -nvs /dev/sda
```

You can also do this, check the man page for more options:

```
sudo e2fsck -cfp /dev/sda1
```

The following will tell you if there are any blocks marked as bad on your partition:

```
sudo dumpe2fs -b /dev/sda1
```

This command lists all the IRQs and the devices assigned to them:

```
cat /proc/interrupts
```


Overclocking certainly does strange things to a PC.  I've had systems that were overclocked for a year running 24/7 without problems and then begin to exhibit strange errors and lockups.  Setting components back to default speeds would fix it.  I don't know if that means the components were stressed permanently from running at the faster speed but luckily no long term damage was apparent since I caught it in time I suppose.

---

### Post by oygle on 2008-07-09
I have only been using Ubuntu for a few years, but I'd have to agree that Hardy is the worst version I have used.

See the problems with Nautilus, at [http://ubuntuforums.org/showthread.php?t=784259&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=784259&highlight=nautilus) , plus I don't know how many times I have had to reboot, it reminds me of a Windooze computer now. The "add/remove" just hangs wen I try to use it, I can't see another computer on the network with Nautilus (but Firefox can see it).

There have been other occassions of Hardy just freezing/hanging, I guess that's what others have called 'lockups'.

Not impressed really. :(

---

### Post by keithyw on 2008-07-13
right now, my system has become fairly stable.  i have not installed Flash with Firefox yet, which is my final issue.  i'm still procrastinating.  but some of my previous issues are gone such as watching video while browsing the net on firefox.  my system is fully updated too.

sometimes it can be a little slow (mostly firefox).  but i simply reload the browser.  i've had a perfect uptime of over 19 days.

just a thought.  i think it's best to upgrade after 3-4 months.  watch the various posts on message boards like these and see how many people are encountering any major issues.  then once the major issues die down, it'd probably be a good time to upgrade.  i think this is a safe bet for any type of system, not just Ubuntu.

anyway, i'm still looking forward to the next release of Ubuntu this fall.  but i think i'll wait until at least winter before upgrading this time around ;)

---

### Post by Vorian Grey on 2008-07-13
I waited until 8.04.1 came out to install Hardy and I have had 0 problems. Like keithyw, I believe it's better to wait a bit before upgrading.

---

### Post by wackyiniraqi on 2008-07-13
My Compaq Presario works just fine.  It's slow because of it's age but no lock ups to speak of.  My desktop has been running Hardy for less than a week.  It locks up constantly.  Sometimes even during start up and loops the login screen sound.

Desktop is AMD Athlon(tm) XP 2400+, 1.5gb Ram, GeForce 6200, and Atheros wireless card on a KT400 Mobo.

I had Compiz going and it would lock up....got rid of compiz and it still locks up....

I've tried the restricted drivers and Envy nothing seems to fix this problem.

well i'm running the 2.6.24-19-generic kernel.  I have no idea how to upgrade kernels as I'm new to Ubuntu (2 months)--does this even solve the problem?

---

### Post by TonyGould on 2008-07-13
> **wackyiniraqi said:**
> 
well i'm running the 2.6.24-19-generic kernel.  I have no idea how to upgrade kernels as I'm new to Ubuntu (2 months)--does this even solve the problem?

there's been a bunch of suggestions earlier on this thread. One thing which *seems* to have made a difference on one machine I have is to use the real time kernel -- although it's very early days. Just bring up Synaptic from System/Administration and search for and install linux-rt. That should automatically change the menu you get when booting; you might need to select a different option when you boot the machine up depending on which kernel gets to be the default.

Also, note that this thread, [http://ubuntuforums.org/showthread.php?t=851434](http://ubuntuforums.org/showthread.php?t=851434), has some tips that it seems everyone who's experienced knows about for dealing with crashes and figuring out how severe they are. (Your problem might be the core of the machine locking up, or it might only be the windowing system locking up. These are different problems, with the former being more severe). 

hth

Tony.

---

### Post by dahlheim on 2008-07-13
just for info's-sake,

dell xps m1210, core 2 duo, nvidia 7400 go, 4gb ram.  worked fine w/feisty, had hard (complete, unrecoverable, with num/caps lock LED's flashing, requiring hard reboot) lockups with 8.04 32-bit.  just installed 8.04.1 64-bit today and they seem to be gone (so far, but i would have had several by now).  suspend is working "out of the box", everything seems a bit better than before.  i was not happy, now i am 
:guitar:

---

### Post by weaver4 on 2008-07-19
I can't say it is fixed for sure, but I was having lockups once a day or once every two days. Now I have gone a complete week without a lockup.

I installed 2.6.24-19-rt (run time) version of the Kernel. Now my machine works flawlessly.

It is easy to install too. Just open System->Administration->Synaptic Package Manager find "linux-headers-2.6.24-19-rt" and "linux-image-2.6.24-19-rt" and install them. Reboot your machine and pick that kernel in Grub.

---

### Post by TonyGould on 2008-07-19
> **weaver4 said:**
> I can't say it is fixed for sure, but I was having lockups once a day or once every two days. Now I have gone a complete week without a lockup.

I installed 2.6.24-19-rt (run time) version of the Kernel. Now my machine works flawlessly.

It is easy to install too. Just open System->Administration->Synaptic Package Manager find "linux-headers-2.6.24-19-rt" and "linux-image-2.6.24-19-rt" and install them. Reboot your machine and pick that kernel in Grub.

Similar experience here :). I was going to wait until 2 weeks for deciding it was fixed "for sure" but I have had 12 days of crashless operation with the real time kernel. With the generic kernel I was getting 2-3 hangs a day (couldn't Ctrl-Alt-F1, couldn't ssh in).

The description in synaptic recommends to install the kernel is with the linux-image-rt metapackage.

This is an Athlonx2 5000 running x64 linux, nvidia graphics, in case that's of any relevance.

Tony.

---

### Post by phidia on 2008-07-19
I'm mostly at the help forums but I have seen this thread. I had used Hardy both before and after it's official release but for some quirky reason decided to stay with my gutsy install. 

I had of course seen quite a few reports of problems but I don't recall anything noteworthy when I was using it.

Today I came across [this thread]("http://ubuntuforums.org/showthread.php?t=864072") in the beginner forums. I guess it could be more complicated; perhaps the person needed to do all the updates or there's some other reason for the failure but for a final release to fail to find a wired LAN connection seems like bad PR to me.

I've been using ubuntu along with other distros since warty and I really like it and will continue to do so. I'm just suprised that there are so many people reporting problems and that it is continuing.

---

### Post by daimaru on 2008-07-19
Hel yeah 8.04 has only been frustration. I personally have Grafix problems. Using nvidia drivers which worked fine under 7.10 I get some refresh problems on 8.04 meaning that when I start the update manger for example, the screen is greyed out while I input my admin password.  Sad thing is that the grey stuff stays even after I did all the upgrades etc it seems that the screen does not refresh so my whole screen is kinda grey and i have to click on my desktop and the whole screen so it refreshes pixle by pixle and stops being grey ...that sucks. Said before that maybe ubuntu should not upgrade every 6 month, its nice, but they should make sure that it works.  I'd rather have a working version for a year instead of a crappy 8.04 version after 6 month.

---

### Post by Shippou on 2008-07-19
Too bad for Canonical. Microsoft's influence? I hope not.

---

### Post by rrnwexec on 2008-07-20
> **cjpetrie said:**
> Ubuntu 8.04 2.6.24.16 won't boot after upgrade on my Actius MM20 PC.
The screen goes black and the disk light comes on solid. For hours.

Kernel 2.6.22.14 does boot however. I don't see a .25 option.

Can anyone let me know how to get to the latest version that works please?

Hello...
This bug and a workaround is documented here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/220852]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/220852")

Hope this helps.
rrnwexec.

---

### Post by wesswei on 2008-07-20
wow! many posts. 

I'm going to have to stay with hardy at the moment. Gutsy was PERFECT however and hardy seems to be a few steps forward with a few more backward though. At the time of this reply, I have updated to the .24-19 kernel. Everything is going ok for now. 

Before with the original hardy install kernel my comp totally froze, randomly shut down (baddd!) and would not respond with my ati.

I think the freezing was due to incompatibility with my wireless usb adapter as it only happened there, but since updating the kernel, no crashes of that magnitude. 

I don't really want to compile a brand new kernel as there's so many kernel dependent built apps, I'm just not ready to recompile...

---

### Post by fidamehran on 2008-07-21
Wow. So many opinions against hardy 8.04? My one's working okay? Save for one little problem. "Synaptic can't install Kernel Image". The problem nobody's giving me the solution to. Anybody care to check out and help me out?
[http://ubuntuforums.org/showthread.php?t=839339&highlight=synaptic+can%27t+install+kernel+image&page=6]("http://ubuntuforums.org/showthread.php?t=839339&highlight=synaptic+can%27t+install+kernel+image&page=6")
I'd appreciate help.

---

### Post by fidamehran on 2008-07-21
Wow. So many opinions against hardy 8.04? My one's working okay? Save for one little problem. "Synaptic can't install Kernel Image". The problem nobody's giving me the solution to. Anybody care to check out and help me out?
[http://ubuntuforums.org/showthread.php?t=839339&highlight=synaptic+can%27t+install+kernel+image&page=6]("http://ubuntuforums.org/showthread.php?t=839339&highlight=synaptic+can%27t+install+kernel+image&page=6")
I'd appreciate help.

---

### Post by 6@dG3r on 2008-07-22
I am very surprised to see so many problems.  I have only been using linux for a couple of months now and I have not had any problems with Hardy.  I have it on an Apple Macbook, an MBA and just a couple of days ago I put it on my new Lenovo X300.  I would like to thank everyone that has helped make my experience a pleasant one.  As for all the people talking about jumping to Fedora, I would like to share a couple of experiences.  I had Ubuntu on my Macbook and no stability problems when I first made this switch.  A friend of mine suggested that Fedora was much better and so I decided to try it.  It ran into constant problems and I finally ended up locked completely out of the system within a few days.  I found little support in the Fedora forums.  A couple of days ago when I got my X300, I gave it a shot again.  4 hours into it, I was tired of trying to solve all the problems and loaded Hardy on it.  Not an issue since the install.  I haven't chased down the sound problem that everyone has had with this model but I see lots of documentation on how to do it, so no worries.  If you are considering a switch I would definitely suggest checking their forums first because this is by far the best around for information on building and maintaining your system.

---

### Post by love2share on 2008-07-22
Hardy is the first hard drive install on my work pc and it&#347; been like windows hell when in Windows 95, not a blue screen but total lockups, sometimes four times in 2 hours and no decent way to reboot than to reset. For the rest I like eveything about this vesion of Ubuntu and a most of it does work.
The lockups with me are related to Firefox entering textboxes like this, firefox using Youtube/flash related sites(solved); wireless device, Ati driver (solved), and playing video files in mplayer and vlc.

I don't know how much longer I can/will take this disappointing situation. Sorry to be so negative, because When it just works, it really brings back the fun for me....

Btw I have a 4 year old Medion pc with 1 gig memory and installed version 8.04.1.

---

### Post by wildman4god on 2008-07-22
I used to have alot of problems with ubuntu 8.04 but then i found out it was because i had the pre release and backports update repos enables, once i disabled them I haven't had a problem with 8.04 it has forzen up on me mabey 3 times in six months and a logout fixed it. also acers are pure junk computers, they are not linux freindly because they are made from the leftover parts of other computer manufactures, i had to friends who both had the same model laptop but the laptops had slightly differnet hardware inside. and a lot of acers hardware are obscure name brands that don't have linux drivers. and if your computer freezes hold the power button for 7 seconds to force a shutdown.

---

### Post by whoaitsme on 2008-07-22
I have been using Ubuntu for about a month, and while I occassionally got the BusyBox error, I am now getting it permanently.  I can no longer boot into the Ubuntu system (I have it dual booted with Vista through Wubi)...I think the problem is due to me shutting down the computer via the button when Ctrl+Alt+Backspace did not work.  

The BusyBox error seems like a constant problem for many people, and I am just getting sick of dealing with it.  Is there an actual solution to it?  I tried editing the command line when entering GRUB and also shutting down my computer properly through Vista...but enough is enough, it's not working!

---

### Post by Gatemaze on 2008-07-23
with the latest updates i observed that my system is much stabler till noon... in the afternoon it usually crashes a few times as before... i think that my heron must be needing its siesta...

---

### Post by gasparov on 2008-07-23
New laptop e new ubuntu updates, now everything is ok. It seems that we should take those habit that windows users have that is never update to the first release that come out, wait for the "-r1" one.

---

### Post by ukripper on 2008-07-24
> **gasparov said:**
> New laptop e new ubuntu updates, now everything is ok. It seems that we should take those habit that windows users have that is never update to the first release that come out, wait for the "-r1" one.

Not true for everyone. Majority of my machines worked out of the box.

So my suggestion is when new distribution is released, try it on separate small partition first. If it works and you have migrated your settings from earlier version's partition and done all stability and functional tests then use live cd  gparted to extend your partition and delete the previous version.:)

---

### Post by senorian on 2008-07-27
It seems that some (all?) of the problems have been identified.
See 
 A possible bug in Foxconn boards BIOS affects Linux ACPI
This silences all the warnings from Hardy's kernel and lets mmconfig work as well.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)

  
  	Updates of resolution od Foxconn bug ( no debates please just updates)
[http://ubuntuforums.org/showthread.php?t=871311](http://ubuntuforums.org/showthread.php?t=871311)

---

### Post by Jim_in_Omaha on 2008-07-28
I was having the lockup problem (some form of it) with both the 32 and 64bit 8.04 when it first was release and gave up for a spell. Today I thought I would try it again. Today a fresh 64 bit install to remove the other distro that I had tried. It installed fine. Went through like 250+meg updates. 


After 6 hours from reboot for the updates, no lockups.... cool

Something got fixed.

---

### Post by vpsville on 2008-07-28
Hardy Server has been excellent for our customers in a virtual environment.  Ubuntu did a great job as usual.

My 2 cents: On the desktop side they are almost supporting more hardware than Microsoft does right now, a few people with problems is inevitable given the incredible variety of hardware out there.

---

### Post by fahad on 2008-07-30
this is the worst ubuntu version :(
the updates is released all day long.
but the performance is still bad enough :mad:

---

### Post by ukripper on 2008-07-31
> **vpsville said:**
> Hardy Server has been excellent for our customers in a virtual environment.  Ubuntu did a great job as usual.

My 2 cents: On the desktop side they are almost supporting more hardware than Microsoft does right now, a few people with problems is inevitable given the incredible variety of hardware out there.

+1 on that!Ubuntu server 8.04.1 has improved miles. 24-19-server kernel detects all my hardwrae now.

---

### Post by ukripper on 2008-07-31
> **fahad said:**
> this is the worst ubuntu version :(
the updates is released all day long.
but the performance is still bad enough :mad:

I wonder what is causing performance issues for you?

---

### Post by fahad on 2008-07-31
well many programs freezes like ndiswrapper gui manager, archive creator
also i cant browse the web, firefox every minute crash without notice,
before crashing i got many small blanks windows like popup but without ads and when i close them firefox crash .

---

### Post by ukripper on 2008-07-31
> **fahad said:**
> well many programs freezes like ndiswrapper gui manager, archive creator
also i cant browse the web, firefox every minute crash without notice,
before crashing i got many small blanks windows like popup but without ads and when i close them firefox crash .

What graphics card u using?

---

### Post by utnubuuser on 2008-07-31
Hardy's not so bad.  It's a brand new OS.
I'm still using Feisty, because it's rock solid on my hardware.
I don't know much about the technical side of things, and I'm of the opinion that the newest releases, such as Hardy, aren't really releases, but still release candidates, and after 6 months or so of general use will they be improved enough to qualify as full public releases.
I've also noticed that Gnu/Linux is like a living kernel, and can have hugely differing effects on a variety of hardware.  What works for one set up wont necessarily work for a similar one.
My experience with Hardy is good so far, but there are a couple of programs, (Gimp and Screem), which are critical to me, that work perfectly under Feisty, crash under Gutsy, and are quirky under Hardy.
But I know of people with very similar hardware, who have no probs at all.
It's all very hardware specific.
Still amazing if you ask me.

---

### Post by keylime on 2008-08-01
I run Hardy on two chassis:

NC8430 HP and a Dell D630, both laptop, both very alien to one another.

The HP machine is not a happy camper, it isn't snappy or crisp. The Dell tho, rides on rails and I have been quite fortunate. 

I do believe Hardy is sensitive to hardware combinations.

---

### Post by EnGorDiaz on 2008-08-01
> **Jim March said:**
> **Tell me something I don't know.** The bug is still open against -16 and is crashing machines in unchanged fashion across the entire Hardy alpha, beta AND release cycles.  Which is why I posted to that thread that a brand new production-Hardy install was breaking in the same fashion.

In desperation I've installed an am running the Hardy realtime (-rt) kernel from the repos. Dunno if that'll help.  It might, as whatever is going on is "load related" and -rt alters the load handling process.

If this breaks I'm compiling 2.6.25.



Having a system with a fundamentally broken error handler is bad luck for all of us.  We do NOT know the cause, only that this is happening.  YOU have no idea what tiny tweak will bring this hell down around your ears.

excuse my language ubuntu staff but holy **** i havent seen a linux kernel that seems to be as badly bugged as this one this bug is gunna be a very hard one to fix and there still doing nothing about shame

---

### Post by fahad on 2008-08-01
intel 855 GM.
right now iam using opensuse 11.0 its good, no problem for now.

---

### Post by matt79 on 2008-08-01
I have a intel. Mine seems to freeze when it is trying to come out of a screen saver. I always have to pull the plug. Does anyone know what the main differences are between hardy and gusty?

---

### Post by dad311 on 2008-08-02
I love Ubuntu because its so easy to use. I've used Linux for the last 10-12 years as a server and/or desktop.  HOWEVER, tonight I spent 6+ hours loading/converting to Fedora 9.  I just couldn't do the lock-ups any more.

As of today with Fedora 9, I can do "tar xvfz", surf the web with Firefox and run Virtualbox ALL AT THE SAME TIME.  Any of these tasks were toublesome at best with Ubuntu.

Goodbye Ubuntu, Ill miss you!  Maybe I be back for the next release.:(

---

### Post by shaka_zulu on 2008-08-02
I am running Kubuntu 8.04 and i just can not believe what i am reading here. Since i have installed Ubuntu/Kubuntu i didn't have any significant problem. I am so happy i am part of this community. I am using Asus A6000U with some integrated graphic card, 1GB RAM, integrated microphone etc. I have to say that only my card reader and IRC didn't work and still don't but i just didn't want to bother myself. All other things were immediately recognized. Also i have to say that with Ubuntu my graphic was awful and it needed some adjustments so i tried Kubuntu and it recognized immediately so i picked Kubuntu for my permanent OS. :)

---

### Post by cjpetrie on 2008-08-04
> **rrnwexec said:**
> Hello...
This bug and a workaround is documented here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/220852]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/220852")

Hope this helps.
rrnwexec.

This workaround did in fact work. THANK YOU!

After having researched it a bit, it seems that this kind of thing has
been happening on efficeon chips since 5.10, so it's kind of fluky
that it happens now to me only on certain versions of 8.04. But this
workaround works.

---

### Post by jhenager on 2008-08-05
No problems at all with the 64 bit version. I upgrade about two weeks after every release since 6.06.
All home built systems, Intel, AMD, AGP, PCIx, IDE, SATA, no matter - all good.

---

### Post by griz on 2008-08-05
Hi,

I'm running Hardy on a desktop pc that i use for a basic file server for backups and downloading public domain movies.  Also use it on a Toshiba Satellite A200 that originally had Vista on it.  Have to admit that i don't get the hangups with Hardy that I did with Vista.  I can live without good webcam support (who'd wanna look at my ugly mug lol), but have to say that Hardy has been very stable on both computers.  I do have some complaints about Linux distros in general, but nowhere near as many as I had with MS operating systems.  BTW, I'm not talking philosophical complaints regarding the problems with proprietary software, but problems with security and overall stability.  

Griz.

---

### Post by FTBPrimeEvil on 2008-08-05
here's my 2 cents [-o<
Ubuntu is Awesome, but i had to fix my sound, network, video, bluetooth devices, email and half dozen other things, but now it is Awesome, currently running with no issues, it only took me 1 month to solve the issues, LOL

```
deanjw@Ubuntu:~$ uname -a
Linux Ubuntu 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

```

---

### Post by thesuker on 2008-08-05
when hardy first came out, i formated my hard drive, dumped windows xp and installed ubuntu. also installed steam (via wine) and played counterstrike 1.6 without any problems until... WHAMP! computer locked up and only way to turn it off was with the button.  so, i had to install windows and everything else again (including WOW, updates and all)  i'd like to know if this issue has been solved (lockup due to ati overheat, haven't ever had that problem on windows xp) so I can go back to ubuntu ^^

---

### Post by Jim_in_Omaha on 2008-08-06
> **Jim_in_Omaha said:**
> I was having the lockup problem (some form of it) with both the 32 and 64bit 8.04 when it first was release and gave up for a spell. Today I thought I would try it again. Today a fresh 64 bit install to remove the other distro that I had tried. It installed fine. Went through like 250+meg updates. 


After 6 hours from reboot for the updates, no lockups.... cool

Something got fixed.

An Update:
For what it's worth;
I had mine lockup again a few days ago. What I discovered was that I had the wireless PCI card selected. Since the last fresh install and updates I was hooked up via cable to the router. And I had turned on the wireless card to see how it worked and left it on. Later while on Firefox (don't remember where I was) it locked hard. Rebooted, saw that it was on wireless, switched back to wire, and have not had a problem since. I now notice that there are mundo posts regarding the problems with wireless networking..

---

### Post by Vorian Grey on 2008-08-06
Mine started freezing just this week. I really hadn't changed anything so I'm not sure what the problem is. I thought it might be compiz so I turned that off. Then I stopped my screensavers. I think my problem, from what I've read, is something going on with my ATI card driver. It sucks, whatever it is.

---

### Post by psychomichael on 2008-08-06
> **thesuker said:**
> when hardy first came out, i formated my hard drive, dumped windows xp and installed ubuntu. also installed steam (via wine) and played counterstrike 1.6 without any problems until... WHAMP! computer locked up and only way to turn it off was with the button.  so, i had to install windows and everything else again (including WOW, updates and all)  i'd like to know if this issue has been solved (lockup due to ati overheat, haven't ever had that problem on windows xp) so I can go back to ubuntu ^^

You can go back to Ubuntu...just use Gutsy...or get the advance Ibex.

---

### Post by bishman on 2008-08-06
I installed hardy on my laptop - it was freezing at first but since the .19 kernel it stopped having that issue ;)

---

### Post by hellknight_mnd on 2008-08-06
Yeah.. exactly.. I've been using Ubuntu since very long time.. I installed Ubuntu 64-bit on JFS filesystem and then on XFS file system. It freezed after a short time of work. Even Ctrl+Alt+Backspace didn't worked. Then i installed it on ext3 filesystem.. here everything worked properly.. I don't know why JFS and XFS bothers Hardy

---

### Post by carusoswi on 2008-08-07
> **vexorian said:**
> huh trollish title.

How many people have experienced this in the retail version anyway?, 3, five?  of all those who installed hardy since it was released...

I have, for one.  Never, ever had a previous version of Ubuntu just lock up.  Hardy locks up several times a week.  I'll be browsing the net or editing photos and, out of nowhere, I lose any ability to make my machine respond.  No keyboard, no mouse, no soft reboot possible.  The only option is to hit the on/off or reset button on my machine.

I would not be surprised by such an event if I were running windows, but am surprised to see this in Ubuntu.

I would also add that I run both Wine and Crossover.  Upgrading to Hardy has broken both.  Those few XP Aps that I rely upon were working fine in 7.10.  I could run Access, build or open Access databases, close them, transport them to my XP office machine, open them in XP, work on them, transport back to my Ubuntu box, open, work, etc.

So far, Access simply won't work in 8.04.  I cannot open existing Databases, no matter the platform on which they were created, cannot build new databases.  Access in wine/crossover simply doesn't work in 8.04.  I've tried Crossover 6 (that I used in 7.10) and Crossover 7 (the upgrade that was supposed to work with Hardy).

I know Ubuntu is (and will always) be a work in progress.  But, this version seems more bug-plagued than any previous versions.  Too bad.

Caruso

---

### Post by carusoswi on 2008-08-07
> **agim said:**
> Why do some long-time ubuntu people write this crap? I understand when someone new comes on and just wants to argue, or when someone has legitmate comments, but to just use flame bait language to start a post is just plain stupid. For people who have used Ubuntu for a long period of time to just come out and say that the entire OS is crap is just senseless, especially around a new release. We want people to come into the community. 

To the people who have been here since Feisty or even longer who are making these kinds of remarks: you know that problems with ubuntu are often limited to a single machine, rarely a whole class of machines, and NEVER to every machine. So why make such stupid remarks? Stick with Gusty, move to Arch, whatever. Just don't come onto the forum and make idiotic remarks that scare newcomers away.

If any newcomer is reading this... I am not a computer programmer, I had little or no knowledge of linux 8 months ago. Hardy is my third Ubuntu release, and each one has been better than the last. If you have any questions or problems, most of us are pretty helpful, and I am sure 95% of you will be happy you made the switch to Ubuntu.

Why do some long term ubuntu write this crap?  Because we have come to expect better from Ubuntu.  I've been on board through four or five versions.  If I didn't have the patience to sort things out, I would have abandoned Ubuntu from the first get-go.  But, for me, it was a refreshingly new OS, so I stuck it out.  I (and I believe "we") understand that Ubuntu and Linux have to contend with hardware that was, for the most part, designed with Windows in mind, so, it doesn't bother me so much that I have to regress to XP in order to use my favorite printer (Canon i960 . . . best and fastest photo printer ever made!!), and, while disappointed, I can live with regressing to XP to use MS Access that won't function under 8.04 in wine or crossover, but, to have my system randomly lock-up is akin to having it invaded by some rogue virus.  By definition, we should not have to be concerned with viruses (and, in my experience, viruses are, indeed, a non-problem in Ubuntu).  Almost by definition, we have grown accustomed to freedom in Ubuntu from "blue screens of death" and other system lockups.  

I believe the Ubuntu community expects and can live with compatibility issues; but system lock-ups run against the grain that defines Ubuntu.

I am certain most of us are willing to give Ubuntu the benefit of the doubt, but we are also married to the notion that its development is guided by certain principles that insure that we remain free of the fundamental Windows flaws that, in a big way, influenced most of us to migrate to Linux in the first place.

With all due respect, the OP has not posted "crap" and, instead of defending the Ubuntu community in light of this flaw, we should continue to express our expectation of releases free from Windows-like fundamental flaws.

Caruso

---

### Post by carusoswi on 2008-08-07
Thank you for the detailed instructions.  I followed them, but am sorry to report that, on my system, the RT version of Hardy runs glacially slow.  When I rebooted into RT, I received a notification that updates were available.  However, clicking the update icon gave me a greyed out udate dialog box that never fully loaded, so that I could not initiate the upgrade.  My browser also stalled.  Looks like RT is not an option for my setup.  What do you think could cause this problem.  Obviously, if it is working for you, either I did something wrong, or there is some anomaly in my system that is causing a problem.

Any suggestions welcome.

Caruso

> **Jim March said:**
> In part, the title was to get people's attention.  However, Linux in general is NOT supposed to hard-lock like this while giving no clue as to what blew up.  That's not acceptable.  It means error-checking is wonky, and it's going to be a cast-iron bi+ch to fix because hey, guess what, no error messages/logs AT ALL.

My Acer lappy running the -rt kernel has a SATA drive.  So at a minimum that CAN work.

Matt and others, **here's how to add the -rt kernel**.  Note that the GRUB instructions are set up to allow you to test-jump to different kernels on boot which I think is a good place to be while we sort this out.

---

Assuming you have a working Internet connection:

1) Under the "System" menu find "Administration", go into "Synaptic". This is a more advanced version of the "Add/Remove Programs" tool.

2) In Synaptic hit the "search" button, change "look in" to "name" and under the keyword to search for type "linux" (no quotes). Hit "Search".

3) It's now showing you everything you can add to your system that has the word "linux" in it's title. Make this window bigger and stretch the"package" column wider (look for the vertical line just left of "installed version", drag it to the right).

4) Scroll down until you spot each of the following:

linux-headers-2.6.24-16-rt
linux-headers-rt
linux-image-2.6.24-16-rt
linux-image-rt
linux-restricted-modules-2.6.24-16-rt
linux-restricted-modules-rt

For each one, hit their checkbox and mark them as "to be installed". Hit the "apply" button when done.  It'll download and install the stuff.

DO NOT reboot yet!

5) Pull up the "terminal" under "Applications>Accessories". Copy and past this next line in exactly as written - use the mouse's right-click in the terminal to do the "paste" as "CTRL-V" won't work in the terminal window:

sudo gedit /boot/grub/menu.lst

6) You're now editing a file in a simple "notepad" type program. Look for the line that says "timeout" and raise the number of seconds. I recommend 20.

7) Find the word "hiddenmenu" sitting on it's own line and put a hash ("#") in front of it to turn "hiddenmenu" off.  Save this edited file.

8) Do a normal shutdown or restart.

When you come back up, a menu will pop up showing all of your kernel flavors available. Pick the one that ends in -rt (realtime) and hit enter to start with that kernel. Run it for a while, see if this helps.

Explanation:

The "realtime" kernel alters the way multiple tasks are scheduled ("prioritized") between each other. It will run fractionally slower for most apps but any app that requests it can be bumped way up in priority. This is for situations where the computer has to be doing something on schedule, tied to other needs such as on an assembly line or something, and can give a critical task it's whole attention.

Something about it's scheduling difference has fixed the lockups on my system and some others.

When regular kernel updates come along, I'll check and see if those fix the lockups and report back to this thread.

---

### Post by carusoswi on 2008-08-07
> **samjh said:**
> While I understand the pent-up frustrations of those whose Hardy installations are not working properly, I do wonder whether it's worth scaring new users away by posting those complaints in this very prominent forum.

Fact is, the vast majority of users are satisfied with Hardy ([Hardy Heron Satisfaction Survey](http://ubuntuforums.org/showthread.php?t=766982)).  It's a fairly good result for the Ubuntu team.

Most users can install Hardy and work with it just fine, so this sort of mass-complaining seem to be hysterical rather than rational.

If you have problems, report it on Launchpad.  Or else discuss it on more appropriate forums: [Testimonials and Experiences](http://ubuntuforums.org/forumdisplay.php?f=103) and [General Help](http://ubuntuforums.org/forumdisplay.php?f=331).  Keep in mind also that some problems cannot be solved by Ubuntu developers or MOTUs, and require fixes upstream.

IMO, new users will more likely come to trust and rely upon Ubuntu if they get the straight shots concerning its strengths and weaknesses.  If, indeed, (as I suspect) there are problems in 8.04 that are not present in 7.10, better for new users, if they read these posts, to be guided to a more stable version and a more positive initial experience with Ubuntu than for them to download a version subject to lockups which should never occur in Ubuntu.  

If we express the problems we've found in 8.04 and guide new users to more stable versions, their experience should be positive.  If we conceal the 8.04 problems, how will a new user react when comparing the relative stability of Ubuntu to Windows when, out of nowhere, Ubuntu freezes on them.  I would think they would tend to conclude that the claims of superior stability inherent in Ubuntu are nothing more than hype.

So, which approach does less damage to the acceptance of Ubuntu . . . hide the problems from newbies, or lay out those problems so that the newbie can avoid them?

I suggest the latter approach to be more conducive to the wide acceptance of Ubuntu.

Respectfully,

Caruso

---

### Post by carusoswi on 2008-08-07
Flame war?  I see no flaming, and I believe that Ubuntu is sufficiently strong to withstand constructive criticism.  Glad 8.04 works without glitches for you.  Unfortunately, the same is not true for me and countless other users who continue to support Ubuntu while simultaneously advocating for bug fixes.

Caruso

> **Saint Angeles said:**
> this weekend i installed hardy on the 8th computer i've tried it on.

i've installed it a pentium III, 3 pentium 4s (totally different kinds though), an old athlon, a dual core... and a couple i didn't even care to find out.

i've never had a single problem (other than having to use ndiswrapper on my sister's computer)

please think about your thread titles before trying to start a flame war. just because you have had bad luck does not make hardy a bad OS.

report your bugs and thats it. i saw nowhere that you are supposed to report a bug then complain your butt off on ubuntuforums.

PS red hat, mandrake, gentoo, debian, winXP... are all the worst OSes by your standards because i've had problems with those.

---

### Post by carusoswi on 2008-08-07
> **FredB said:**
> OK with you. But the problem is like another people said : *hysterical* posts. 

If people don't like this version, why the h*** do they install it ? Don't they have the opportunity to grab live cd and see if it works before installing it ?

Anyway, integrism is bad, as you said too.

Integrism?  What's that?

Caruso

---

### Post by carusoswi on 2008-08-07
> **swoll1980 said:**
> I have had no problems with Hardy, and find it quite enjoyable to use. As for a lot of people having these problems I think that is exaggerated (considering how large the Ubuntu user base is) if 60,000 people had the problem it would be about 1% of the total user base that hardly seems like a lot. Someone commented that because there was 11 pages dedicated to a thread on this that it must be affecting a large number
of people. What is that like 20 people? when the number of affected people reaches 1%
Then I think the Ubuntu devs can be concerned.

If you are experiencing the problem, it is not exaggerated.  Those of us experiencing the problem are really experiencing the problem.  Why do you seek to trivialize us?  The number of posts on this subject are only the number of posts.  It says nothing about how many others who have not bothered to post have (or have not) experienced the same problem.

I had not previously posted until today concerning this problem.  Actually, I ascribed the problem to my hardware, however, in retrospect, and, after coming across this thread, I realized that the problem only cropped up after I upgraded to 8.04.

Most of us "naysayers" here do not seek to discard Ubuntu. On the contrary, we'd like to define the problems so that they may be fixed.

I like Ubuntu, and, regardless the version, will continue to look to it as my default OS.

Still, when I see problems confirmed by similar accounts from others, I feel no need to "protect" ubuntu by hiding my observations.

Caruso

Caruso

---

### Post by kkolk on 2008-08-08
I had Ubuntu 8.04 installed on two systems and I've been nothing but disappointed in it.  It's still on one of them for now.

First system was a fresh install on an Athlon64 3500+ w/ 2GB RAM and an Nvidia 6800GT.  This box serves as my home email / web server and as the backend for my MythTV DVR.  It has one older ATI TV Wonder (bttv based) tuner and accesses a HDHomeRun network HD tuner.  This system has been experiencing lockups for the last 2 months.  Sometimes it would happen twice in one day, sometimes it would be weeks apart.  In the last day it happened a whopping 3 times and I've finally given up on it.  I've reinstalled 7.04 on it and I'm hoping things improve.  

I tried to troubleshoot the problems on it but it looks like short of setting up another system on a null modem cable to get the Kernel Panic error off the com port I'm not going to be able to see what is causing the issue.  When it locks the keyboard freezes with flashing numlock+scroll lock and while if you are on tty1 you can see the crash dump the size of the dump is so much that even with many extra lines and smaller fonts enabled on a framebuffer running in 1680x1050 I still couldn't see what driver or module was causing the crash.  I don't feel like setting up a terminal to monitor it given that it seems to be a fault in the distro rather then my hardware.
 
Second system is a Dell Latitude D620.  This laptop has worked very very well with that last two releases of Ubuntu (6.10 and 7.04) but in Hardy it has problems.  Firefox constantly likes to at random freeze up and/or crash.  Seemingly at random sometimes when accessing flash, sometimes when not.  Meh, it's annoying.  It also will from time to time have a similar Kernel Panic as my home server, but only when shutting down so it's not too big of a deal.

Overall I have to rate this as the worst edition of Ubuntu I've ever worked with.  I hope they get things sorted but after waiting several months with the bugs I'm disappointed that a so called LTS version is off to such a rocky start.

I'll likely be rolling my laptop back to 7.04 soon, but for now I simply can't afford to take the time to rebuild it since I use it daily at work and the problems aren't that bad.  :(

---

### Post by zipperback on 2008-08-09
As with any new release there are always initial problems that plague a small number of users. You fall into that group. If Hardy isn't working then just go back to the previous version or work through the problems.

- zipperback
:popcorn:

---

### Post by malangaman on 2008-08-09
> Overall I have to rate this as the worst edition of Ubuntu I've ever worked with.  I hope they get things sorted but after waiting several months with the bugs I'm disappointed that a so called LTS version is off to such a rocky start.

I'll likely be rolling my laptop back to 7.04 soon, but for now I simply can't afford to take the time to rebuild it since I use it daily at work and the problems aren't that bad.  :(

Why not roll back to Gutsy 7.10?
It runs sweet.

---

### Post by iamBevan on 2008-08-10
> **zipperback said:**
> As with any new release there are always initial problems that plague a small number of users. You fall into that group. If Hardy isn't working then just go back to the previous version or work through the problems.

- zipperback
:popcorn:

Indeed

---

### Post by cgerman77 on 2008-08-10
Hi there. I installed the 64 bit version a few months ago and I never had a lock up problem with Hardy. 

I have an Intel Core2Duo, Motherboard Asus P5B Deluxe, GeForce GT8500, SATA HDs and SATA DVD-RW, RT8187 wireless card and Sound Blaster Xtreme. The only issue that I had was manual configuration of wpa_supplicant to enable WPA-PSK security because it did not work from Gnome UI.

My kernel version is 2.6.24-19.

Regards,

Germán.-

---

### Post by BuntuFreak on 2008-08-10
I never saw I would say this.

Old Windowers know that "upgrading" to a new version of Windows is crap shoot. If you are smart, you'll do a clean install. Hardy to Gutsy upgrade has shown, Ubuntu is no different.

My machine is unusable. It seems like between my mouse and the OS, I'm using a 14.4K modem to send my commands.

If anyone knows how to "downgrade" to Gutsy, please post links.

Thanks much.

P.S. I cannot believe I'm thinking of going back - notice I'm not saying downgrade - to XP. I never ever thought I would say this.

---

### Post by slyrogue on 2008-08-10
Ouch; I guess I haven't been paying attention to the posts in a while.  I knew Hardy was having a few issues, I didn't realize so many people are running into such hardcore problems.  I'm glad people post though; at least this way I have a head's up in case it does happen to me so I don't go into a frenzy of trying ridiculous things to fix it and only make it worse.

I have been having a few issues, but it seems to pertain more to compatibility problems with some software releases (games, in particular).  I have experienced lock-ups and slow-downs; though I think most of my issues stem from my willingness to compilie and run in-dev software as opposed to waiting for a stable release, or a release geared towards Ubuntu use.  Plus I have just about every library under the sun installed since I'm not good at purging my system when I get rid of software.  I'm impatient, what can I say?

By way of contrast though:  My Compaq Presario F700 laptop runs Hardy like it was written specifically for it (as long as I keep above mentioned in-dev software off it)!  So far, so good.

---

### Post by Xizorbg on 2008-08-11
Sorry to add to the flame-

But I am writing this on my wife's Evil Empire - running laptop.  I am running Hardy on an AMD64 w/ and Nvidia GeForce4 card and am completely miserable.  Someone needs to start a wiki and troubleshooting page.  The OS is becoming almost unusable.  Further I cannot find trouble-shooting tips in the forums, online, or in my logs.

Please, developers, help fix this broken distro ASAP.

Thanks,
X

---

### Post by solwic on 2008-08-11
> **Xizorbg said:**
> Sorry to add to the flame-

But I am writing this on my wife's Evil Empire - running laptop.  I am running Hardy on an AMD64 w/ and Nvidia GeForce4 card and am completely miserable.  Someone needs to start a wiki and troubleshooting page.  The OS is becoming almost unusable.  Further I cannot find trouble-shooting tips in the forums, online, or in my logs.

Please, developers, help fix this broken distro ASAP.

Thanks,
X

I don't know that the distro is broken, but it needs a lot of work in specific areas.  

IMO, anyway.  :D

:cool:

---

### Post by EnGorDiaz on 2008-08-11
im using hardy im having no lock up problems at all and i have an old dimension 2350

---

### Post by Roundel on 2008-08-11
> **Xizorbg said:**
> Sorry to add to the flame-

But I am writing this on my wife's Evil Empire - running laptop.  I am running Hardy on an AMD64 w/ and Nvidia GeForce4 card and am completely miserable.  Someone needs to start a wiki and troubleshooting page.  The OS is becoming almost unusable.  Further I cannot find trouble-shooting tips in the forums, online, or in my logs.

Please, developers, help fix this broken distro ASAP.

Thanks,
X

I agree.  I'm not sure too many of the key people actually read these posts though.  I am using an HP ZD7000 and have been getting periodic hard-locks.  I'm seriously considering reverting to gutsy, which ran fine.  I don't know why I even bothered to upgrade to Hardy.  It's slower and glitchy.  ](*,)

---

### Post by RedPandaFox on 2008-08-11
I have not had a problem with Hardy yet. I think its great!
The only problems I have had were faults of mine.
Ironical, it seems My system is running well when more advanced users arnt, When normally, I can have a perfectly healthy system, I get neer it, and it dies. I blue screened my housemates Windows 3 times when trying to open My Documents... He hadn't had a blue screen in 3 years...

I just seem to be lucky this time.

---

### Post by deepclutch on 2008-08-12
I have just upgraded my PC h/w to c2d and 945GC mobo. installed hardy 8.04.1 x86_64 .I must say ,I havent faced any issues.it is actually working smooth :D  with nvidia 7300GT card.

used a alternate install cd(debian installer ncurses based).

I think ,it is laptop users ,who are facing more issues? someone should've compiled and provide them latest 2.6.26rc kernel with all drivers :| =>problem almost solved.

---

### Post by ezsit on 2008-08-12
> If anyone knows how to "downgrade" to Gutsy, please post links.

Backup your files and install Gutsy from scratch, I do not know of any way to reverse an upgrade to Hardy.

BTW, I have an older Celeron 2.0ghz machine with 1gb of ram, Nvidia gforce 400 AGP card, and a 320gb hard drive that Hardy just loves and runs perfectly. I always install fresh and I waited for 8.04.1 to hit the mirrors before installing, but I have yet to have a single problem

---

### Post by ColdSpider on 2008-08-17
man, I'm having the same problem whever I click on anything! I just switched to Ubuntu a few days ago and it was working fine until just now. I'm gonna give gutsy a try, right now I'm being woefully reminded of why I switched to Linux from Windows in the first place :'(

---

### Post by Crafty Kisses on 2008-08-17
Yeah, I compiled a kernel that works really good with my setup, haven't had ANY problems with Hardy what so ever, I know some of my friends are having issues, but I'm not at all.

---

### Post by willyboy666 on 2008-08-18
here is some news about my tablet pc c-120x gateway

freeze freeze freeze ,overheat much faster then vista or xp.
with my tablet over 55c fan never runs high ,with xp or vista over 52-53 c fan begin to get the heat out.
no body seem to help me....
i will go back to gusty .

cpu is intel ulv 7600 1.2gh

---

### Post by ukripper on 2008-08-18
> **willyboy666 said:**
> 
no body seem to help me....
**i will go back to gusty .**



Well you have helped yourself by going back to Gutsy.

---

### Post by hufferd on 2008-08-18
> **ColdSpider said:**
> man, I'm having the same problem whever I click on anything! I just switched to Ubuntu a few days ago and it was working fine until just now. I'm gonna give gutsy a try, right now I'm being woefully reminded of why I switched to Linux from Windows in the first place :'(


I don't know what all this talk is about I am a new user to Ubuntu have been on 8.04 for about 5 months now and had NONE of these issues the only issue I have had is the whole 64 /32 bit deal....  Maybe these "Lockups" are more an issue of hardware then anything else

---

### Post by Brandon.Viking on 2008-08-19
Kernel 2.6.24-19-generic ... craps my laptop with I/O errors and a little audiable clicking sound coming from the hard drive ... 2.6.24-18-generic no problems. Fresh install 8.04.1? Still IO errors ... same kernel.
HW T40 IBM Thinkpad with 1.5GHz CPU, 512M RAM

I have tried the noapic on the boot parameters ... no difference still IO errors....
I have tried just about every fix posted in a forum. Kernel issue no doubt but seems to be IO related.

This is bad.

---

### Post by ukripper on 2008-08-19
> **Brandon.Viking said:**
> Kernel 2.6.24-19-generic ... craps my laptop with I/O errors and a little audiable clicking sound coming from the hard drive ... 2.6.24-18-generic no problems. Fresh install 8.04.1? Still IO errors ... same kernel.
HW T40 IBM Thinkpad with 1.5GHz CPU, 512M RAM

I have tried the noapic on the boot parameters ... no difference still IO errors....
I have tried just about every fix posted in a forum. Kernel issue no doubt but seems to be IO related.

This is bad.

Use 24-18 if that works fine for you! go to synaptics and search for 2.6.24-18 generic and install it and add it to your grub. reboot and use that.

---

### Post by codeking on 2008-08-19
uh, do you happen to be running Skype?  Mine was always freezing up too, but I got rid of skype and now it runs fine.

---

### Post by ukripper on 2008-08-20
> **codeking said:**
> uh, do you happen to be running Skype?  Mine was always freezing up too, but I got rid of skype and now it runs fine.

your system spec?

---

### Post by vikramaditya on 2008-08-20
> **hufferd said:**
> Maybe these "Lockups" are more an issue of hardware then anything else
dingdingdingdingding!  **hufferd**, you've won a 2-week, all-expenses-paid safari to fabulous *kamchatka*, where you'll be hunting those pesky giant brown bears to the verge of extinction!

---

### Post by ukripper on 2008-08-20
> **vikramaditya said:**
> dingdingdingdingding!  **hufferd**, you've won a 2-week, all-expenses-paid safari to fabulous *kamchatka*, where you'll be hunting those pesky giant brown bears to the verge of extinction!

:lolflag: good one!

---

### Post by codeking on 2008-08-20
> **ukripper said:**
> your system spec?

Well, its just froze like 3 times in 30 minutes last night, so I guess removing skype didn't help.

Well my comp is a pentium IV 3.0GHz, 2GB DDR2 RAM, very nice motherboard (not sure what brand or model it is), crappy graphics card, and no swap.

---

### Post by hardyn on 2008-08-20
have you tried running memtest86 for a few hours? maybe in windows, or a distro that you didn't have trouble with, run superPI for a few hours as well, see if you can coax a crash?

---

### Post by TomMK on 2008-08-22
Just installed Hardy 8.04.0 on my HP NC6400 and got my first of these hard lockups within an hour. My other laptop, an older Inspiron 510m, does not suffer from these.

Shame, I thought I'd got away with never seeing one of these well documented cases. I'll try 8.04.1 tonight...

---

### Post by Mach1US on 2008-08-26
Don't want to speak too soon but since last kernel update all is GOOOOD \\:D/
Even while running both at the same time full blown XP sp3 via VMware and Hardy.

---

### Post by cknight725 on 2008-08-27
I dunno about lockups, but upgrading from 7.10 to 8.04 completely bricked my laptop.  Gnome Settings Daemon error would come up 7 out of 10 times, Wireless and Wired networking never worked even though it was getting DHCP IP and Gateway info just fine.

Heron is awful ... its the Vista of Ubuntu ...

---

### Post by Confusatron on 2008-08-31
Have to throw my hat in the ring on this one (sadly). I love the usability of Hardy but it has become completely unstable and I'm at a loss as to how to manage it. I've been running linux in some form since 1997, but Ubuntu/Kubuntu has been great at making me forget all the low-level debugging stuff because (until Hardy) everything just *worked*, and I don't do this stuff for a living. 

The hard locks seem to be X related, but I don't have an nvidia card (VIA K8M890 running vesa driver) or wireless and it is hard locking now with *nothing* running other than gnome and grsync (desperately trying to back up files to USB drive)...

Longest uptime I've had in August was 7 days. Longest today, 2:46 (yes 2 hours).

Really frustrated, typing this from an XP laptop :(

---

### Post by Paul86fxr on 2008-08-31
Hate to say it but "too much too fast" I love ubuntu, I use 7.04 and leave hardy completely alone. Ubuntu almost went mainstream until 8.04, now we are set back to the times of slackware, they need to slow down and build on proven code, ease of use and not new distros every three months, more is sometimes less! everyone reinstall .04 and wait for the devs to sort this out.

---

### Post by ukripper on 2008-09-01
> **Paul86fxr said:**
> Hate to say it but "too much too fast" I love ubuntu, I use 7.04 and leave hardy completely alone. Ubuntu almost went mainstream until 8.04, now we are set back to the times of slackware, they need to slow down and build on proven code, ease of use and not new distros every three months, more is sometimes less! everyone reinstall .04 and wait for the devs to sort this out.

First of all, going back to 7.04 is not a viable option as update support for 7.04 is coming to an end, this month.

Secondly, not three months, new version release is on every 6 months release cycle.

Thirdly, one can stick with what they like in GNU/linux world. If you are not happy with ubuntu you have thousands of distros available including the king of stability - Debian. 

Finally,why the release cycle is scheduled for every 6 months, is a recurring discussion not worth going over again on this thread but can be started under a new thread in recurring discussion forum. [http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by DemonBob on 2008-09-01
Never had a problem with Hardy, running it on 3 totally different systems. Running Ibex on my laptop.

---

### Post by nomeat on 2008-09-01
I did the latest kernel upgrade as per update button and so far I have no lock up but still some temporary freezes. However I have hardly been using it anymore.

I have been using OpenSuse 10.3 for quite sometime and now have 11.0 on the same disk as Ubuntu.
It is just a easy to install as Ubuntu but runs lightning fast and no lockups what so ever.  

If you are starting to pull out you hairs like I did, do yourself a favour and try OpenSuse 11. It also has a great community.

I was also pulling out my hairs with Windows, which was the reason why I switched to Linux but if a particular Linux flavour doesn't work for you any more then it is time to move on. There are plenty of other excellent distros.

---

### Post by ukripper on 2008-09-01
> **nomeat said:**
> I did the latest kernel upgrade as per update button and so far I have no lock up but still some temporary freezes. However I have hardly been using it anymore.

I have been using OpenSuse 10.3 for quite sometime and now have 11.0 on the same disk as Ubuntu.
It is just a easy to install as Ubuntu but runs lightning fast and no lockups what so ever.  

If you are starting to pull out you hairs like I did, do yourself a favour and try OpenSuse 11. It also has a great community.

I was also pulling out my hairs with Windows, which was the reason why I switched to Linux but if a particular Linux flavour doesn't work for you any more then it is time to move on. There are plenty of other excellent distros.

Good advise, but i would urge people to try few more distros and then make the transitions what best suits for them. Start with linux Mint (is good option and works pretty much like ubuntu),opensuse 11(although i am not fan of rpms), debian(very stable), Fedora 9(yet again rpms), puppy linux(my personal favourite for old hardware running 64mb -128mb RAM), Damn small linux( for very old hardware 16MB - 64mb RAM).

Ubuntu Hardy to Intrepid all works perfect for me so would stick to them!

---

### Post by Paul86fxr on 2008-09-01
Boy, I guess  UKRIPPER told me off didnt he? but like Hardy, he missed the point.

---

### Post by ukripper on 2008-09-01
> **Paul86fxr said:**
> Boy, I guess  UKRIPPER told me off didnt he? but like Hardy, he missed the point.

No mate, I haven't told you off! I've just helped others for not falling for incorrect info.

---

### Post by malangaman on 2008-09-01
> **DemonBob said:**
> Never had a problem with Hardy, running it on 3 totally different systems. Running Ibex on my laptop.

Can you list your system specs?

---

### Post by jimbean on 2008-09-14
worked for me

great until i installed all of the third party stuff

like media codecs and 


got greedy wanted all for nothing

---

### Post by noneofthem on 2008-09-14
I had some major problems with Hardy, too. My harddrive would start maknig noises and spin for no reason. Also I wasn´t able to mount some cds and dvds. When copying stuff to external devices I got r/w errors. The same errors came up while listening to locally saved movies or music. One harddrive even died because of that. I got another one but the same problems came back. So in the end I had to reinstall Gutsy. Everything seems to be fine again now. Really disappointed in Hardy. I really hope this issue will be resolved in the next release.

---

### Post by zoeken on 2008-09-14
I'm tottaly new to linux (except some storys from friends) and in the last month i installed Ubunutu 8.04 i386, Kubunutu 8.04 i386, Ubunutu 8.04-64, Kubuntu 8.04-64, Kubuntu 8.04 KDE4-64.
My computer is an AMD64 X2 3800+, 2 Gb DDR2, nvidia graphiccs 7600GT, SATA II Hdd 250 Gb Seagate and 250 IDE Hdd Seagate, nForce 5 motherboard chipset with LAN and AUDIO, SATA DVD-RW, Blue Soleil Bluetooth, internet using a cable modem but i have also a PCI Conexant modem.
Everything works quite well in all distrubution with some minor exception:
- All Kubuntu version works bit slowly than Ubuntu, don't lockup or freeze but i get all the time a Knotify message with some errors. I said i'm a beginner so i don't have a clue why and how to report. Kubuntu KDE4 didn't get any error but is way too futuristic for a beginner (better said : for me)
- Ubuntu 8.04 instead, works way faster than any other (i coul say any other operating system). With the i386 version i've had some trouble: Mozilla stop working but only when i open and close the aplication very fast severeal time one after another. The sound driver became unfunctional when i use Amarok and try skype in the same time, but i read some post around here and i'm starting walk to light :). So far the solution was: go to System monitor and kill Amarok then restart skype.
    Now i have Ubuntu 8.04-64 and so far everything works well(including compiz-fusion :D): no freeze, no lockup, faster then everything i used before. Altough the audio problem with skype is on the job menu :P.
    I think if a begginer like me can face Ubuntu then it is not so hard as it is look like...... I must say the kernel is 2.6.24-19 generic.

---

### Post by Babstar on 2008-09-14
> **zoeken said:**
>  The sound driver became unfunctional when i use Amarok and try skype in the same time, but i read some post around here and i'm starting walk to light :). So far the solution was: go to System monitor and kill Amarok then restart skype.
    Now i have Ubuntu 8.04-64 and so far everything works well(including compiz-fusion :D): no freeze, no lockup, faster then everything i used before. Altough the audio problem with skype is on the job menu :P.
    I think if a begginer like me can face Ubuntu then it is not so hard as it is look like...... I must say the kernel is 2.6.24-19 generic.
The sound issues are well known, and not related to lockups.  Basically, the sound driver ALSA only allows one application to access the hardware at at a time.  There is a solution - Pulseaudio which allows multiple applications to access the hardware simultaneously.  I administer three kubuntu 8.04 systems, one with pulse, and two without.  Pulse works well for Skype and Amarok. Pulse audio is included with Ubuntu Hardy by default, but not Kubuntu
Generic Ubuntu instruction to set up Pulseaudio are can be found here:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
see also [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by quill3033 on 2008-09-15
The sound issues are well known, and not related to lockups. Basically, the sound driver ALSA only allows one application to access the hardware at at a time. There is a solution - Pulseaudio which allows multiple applications to access the hardware simultaneously. I administer three kubuntu 8.04 systems, one with pulse, and two without. Pulse works well for Skype and Amarok. Pulse audio is included with Ubuntu Hardy by default, but not Kubuntu
Generic Ubuntu instruction to set up Pulseaudio are can be found here:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
see also [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

I have actually installed 7.10 on one disk (external usb that I take with me everywhere) and have 6.06 on my internal disk because of Skype. The sound in Skype was just shocking on Hardy and I tried a few things suggested in forums and it didn't help. I could hear people perfectly but they couldn't hear me. But it was my understanding that Pulseaudio was the problem not ALSA. On my old 6.06 (with duplex sound card) I had no problem having Skype and music on at the same time and Skype would ring through the music even. I've decided to stay with both these versions until canonical stops support for them next April and then will upgrade to Hardy. Other than that Hardy worked like a dream for me. Oh, yes, occasionally Firefox 3 would close for no reason, but if I re-opened it, it would 'restore session' with no problems. 
I'm hoping by next April Hardy (and other distros that use Pulseaudio) and Skype people will have sorted out the sound problem.

---

### Post by Samizdat on 2008-09-15
I cannot speak to whether Hardy is the worst of the Ubuntu flavors, but I can safely say Hardy is light-years more interesting, challenging, and utilitarian than Windows.  Linux makes you think, makes you learn the command line, whereas Windows conditions you to avoid the command line at all costs.

If I had one request to make for the next version of Hardy, which I've read is due in a few weeks, it would be, kindly keep the new version listed as pre-stable if it's anywhere near as buggy as 8.04 is.  Kindly fight the urge to list anything as stable which, for each app one fixes, installs or reinstalls, fifteen more break.  A recordMyDesktop which doesn't require my restarting my computer every time I make a fresh recording, for instance, would be cool.

One last thing, then I'm done bitching (for tonight), I promise: don't get me wrong -- I'm so done with Windows that I resist with every ounce of moral fiber in my body, any urge to regress to wine, Windows emulators, Windows-under-Linux VMware, or any such bastardizations.  However, even as new to Linux as I am, I do believe methods and tools for porting Windows apps to Linux could be made more accessible, streamlined, and, for lack of a more honest word, *sane*.

Thanks for taking the time to read this lowly peon's paean from his modest quarter of the mountain-grown Ubuntu bean-hill.

---

### Post by twitch2197 on 2008-09-21
hardy's been pretty good for me. at first, i had some lockups but i only had a 15g partition for it, and now that i dedicated my whole hard drive to hardy i only get lockups when playing development versions of games (probably don't have the best video card, and that's what i get for not reading the fine print: "this version still contains critical bugs").
I personally wouldn't go back to any other system.

---

### Post by Timothy Taylor on 2008-09-21
I'm a Linux newbie and I recently installed Ubuntu on an old HDD in my PC. After the first lock-up, I thought I'd done something *seriously* wrong: the PC was completely locked - only the reset button could get my PC working again.

Ubuntu continued to lock my PC, so I tried wiping my HDD and re-installing.  Same problem - locks my PC within 20-30 minutes.  Absolutely useless.

I'm back to using WinXP now.  Searching for an answer to the lock-up I found this thread, which I see has been running for almost 5 months now.

To me, it seems crazy to have this released as a "proper" version when a significant number of users find that it falls over every few minutes.  Even windows isn't this bad!  I can't remember the last time I had a blue screen on XP.  

This is appalling.
:(

Is there anywhere I can download a previous version which might work, or should I try a different Linux?

---

### Post by malangaman on 2008-09-21
I am running version 7.10 released July 2007 and supported until April 2009. I am delighted with it. It is fast, responsive and every thing one could wish for in an OS.
Link to download is here:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by psychomichael on 2008-09-21
Count me as an Ubuntu user who will never switch back to Windows. I've been using 7.10 for awhile now and am really happy with it's performance. I'm waiting for Intrepid Ibex before I upgrade again.

---

### Post by darrenn on 2008-09-22
Can somebody tell that ******* jim march that his laptop (acer 3680) no longer lockups anymore when using hardy.

---

### Post by darrenn on 2008-09-22
Since his thread is so popular I thought he would like to know that his old laptop (acer 3680) no longer locks up when using Ubuntu hardy. I have been happy with hardy for sometime now. I guess some people like to complain.

---

### Post by ukripper on 2008-09-22
> **darrenn said:**
> Can somebody tell that ******* jim march that his laptop (acer 3680) no longer lockups anymore when using hardy.

I guess he probably moved to some other distro or most probably back to windows!

---

### Post by Timothy Taylor on 2008-09-22
> **malangaman said:**
> I am running version 7.10 released July 2007 and supported until April 2009. I am delighted with it. It is fast, responsive and every thing one could wish for in an OS.
Link to download is here:

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)Thanx for that.  7.10 d/loading now...

---

### Post by John164918a on 2008-09-22
My Hardy locks up all the time especially when I try to play a video with VLC or totem. Its really annoying and not really acceptable in an operating system.

But who agrees with this:

Its still way way better than windows!

---

### Post by John164918a on 2008-09-22
OK guys ignore that I think I've fixed it. I was still booting an old kernel from an instance of grub that wasnt in the ubuntu partition. Ubuntu Hardy now that it works it is the best!!!! Thankyou for this awesome awesome OS! I will not be leaving Hardy any time soon and will keep lecturing my friends and anyone who will care to listen about it!

Thankyou Ubuntu ppl!

:guitar:

---

### Post by TranceWarp on 2008-09-22
I wish the live cd had the same kernel as the updated Hardy.  I reinstalled Win XP MCE recently (I still play some games on that OS).  Trying to reinstall GRUB to the MBR was a chore with the Live CD (old kernel, so random lock-ups).  I finally managed to get it done on the, ohhh, 7th try. :D

---

### Post by Timothy Taylor on 2008-09-22
> **Timothy Taylor said:**
> Thanx for that.  7.10 d/loading now...Have installed and now running 7.10, which is working fine so far.

I'm impressed - tho I suspect there is quite a learning curve for a Windows escapee to clamber up.  :)

Pity about Hardy...

---

### Post by the.allstar on 2008-09-22
I'm having the same problem, and looks like a lot of people are.  I'm really disappointed with this version of Ubuntu - 7.10 was working so well for me - I never should've touched it :-(

Is moving back to 7.10 the only known solution?

---

### Post by starcannon on 2008-09-22
> **John164918a said:**
> My Hardy locks up all the time especially when I try to play a video with VLC or totem. Its really annoying and not really acceptable in an operating system.

But who agrees with this:

Its still way way better than windows!

I'd not use it if it locked up all the time, and it doesn't. If one installs 8.04 properly, it is the best release yet. If it locked up all the time I'd use something else; however, I use Ubuntu Hardy.

---

### Post by jheaton5 on 2008-09-22
At the beginning of the summer, I started experimenting with knoppix.  I quickly moved to debian with a fresh install (single boot) on an old x86 platform.  I worked with that for a couple of months and then decided that I wanted to ditch my Windows Vista on the new laptop.  I looked around to see what was available for laptops.  I picked Ubuntu 8.04 Hardy...  OK, I had to locate a driver for my wireless card and for my wireless printer but everything works great.  I have a wide (17") screen with an nvidia graphics card.  It all works great.  Maybe it's just dumb beginner's luck, but I don't see what all the fuss is about.  Hardy Heron 8.04 is the best thing that I have stumbled into in a long time.  Good-bye Mr. Gates.

I also had a medium-sized database using MS SQL Server and an Access front end.  Well all of that is now migrated to MySql and I couldn't be happier.

---

### Post by carusoswi on 2008-09-23
The thread title (worst ubuntu version yet), I suppose, is somewhat subjective.  Worse for me were versions of Ubuntu where I had to jump through hoops to get my wireless working.  It took me, I estimate, six months, during which time, whenever I needed wireless net access, I had to use XP.

I would say that, for me, was worse than the lockups that have now become commonplace on my system with 8.04.  It's a shame so many in the 'community' exhibit such thin skin when any of us is critical of Ubuntu.

I am a user, not a developer, so, while I can comment on and report problems, I cannot do much more in the way of fixing them.

Given all the growing pains I experienced in switching my head from XP to Ubuntu, I can truthfully say that I was motivated through that pain by the promise that I saw in Ubuntu of an OS that did not bog down or lock up, ever.

For 8.04 to simply freeze several times a day blasphemes that promise that has kept me around since the early versions of Ubuntu 6.x.

That anyone in the community should get defensive when we report problems, or to state that we should just ignore the problem and go back to version 7.10 (I've been told more than once (in effect) that I'm really just a Windows guy who really just wants a free version of XP, and that if that is who I am, what I want, then, I should just go back to XP and skip Linux altogether) is an insult to our intelligence and willingness to support Ubuntu (by USING it).

Unless Ubuntu really wants to be an OS for geeks only, then, complaints (even those that fall under a somewhat inflammatory thread title) need to be taken seriously.

That the problem continues this late into 8.04's release leads me to belive that it is either so elusive or that development juices have been directed in other directions so that it may never be fixed.

. . . and, not that my influence as a single user (ok, I run a small company, and I'm  responsible for our computer decisions/implementations, but, in relation to the size of this pond, I'm a truly small drop, indeed) will make that much of a difference, but, when I see problems of this nature not taken seriously, not approached with aggressive problem solving, then it is, for me, the beginning of the end.

I will start looking (as I started looking back in the day that I found Ubuntu).

I may not switch right away, maybe never, but I will start looking for some alternative.

The thinned skinned here will overlook my committment to Ubuntu as a user.  I have not forgotten that Ubuntu is free.  It should also, by definition, be the greatest OS going.

I hope this problem is important enough within Ubuntu's development community that those voices (and heads) bent on finding a solution are louder than those who would defend Ubuntu against factual criticism.

. . . and, yes, my system locks up, also.  It's a desktop, nothing exotic, but not slow or weak, either . . . plenty of HD space, memory, 3.0 gHz processor, etc.

Lock-ups will occur several times in an eight hour day, no matter if I'm working on or off line.

Caruso

---

### Post by carusoswi on 2008-09-23
Ha!  Received a forum message refusing my post because 'one can only post once every x seconds, minutes,' I don't remember which.  I had only tried to post once, but the forum wouldn't believe me - hence a double post which, with this little bit of diatribe, I have corrected (sort of).

Caruso

---

### Post by psychomichael on 2008-09-23
well said, caruso. Everyone seems to be looking to Intrepid Ibex as a future solution so that we can move on and forget this blight that is Hardy. 

My answer to anyone who says we should just go back to XP: I can't go back. I can't unring the bell and use Windows anymore. I had to help a friend who is still stuck in that world and it just frustrated the hell out of me because I was helping him fix things that I don't have to with Ubuntu. So, no. I will not go back to Windows. Give me the excellence that I have come to expect from Ubuntu! Give me the promise that was made when Ubuntu was formed: "It just works"!

---

### Post by cygnus-X1 on 2008-09-27
OK. So this is the only useful thread that I've found so far that is even looking at this lockup problem. It may be a little late in the thread, I just hope I can find some direction to address this problem, as I too am suffering from this among other problems. And being rather new to Linux in general, even a little help would be greatly appreciated!

SYSTEM INFO: MB - Abit AN-M2HD
            CPU - AMD 4850e X2
            Mem - Super Talent DDR2 2x1GB
            HDD - WD 160GB 7200rpm 8M buffer
      CD/DVD-RW - Samsung SH-S203-N
Ubuntu 8.04 Hardy Heron AMD64 OS - downloaded version - Kernel 2.6.24-19

SYMPTOMS: Random hard lockups and shutdown after initial boot.

Let's pretend I'm dumber than dirt (< a noob) and want to diagnose and fix the problems. What would be the "best" way to do this? Things like locating and reading the error logs (if any), and methods of rectifying the problems based on both the logs and good old trial-and-error. Jim March seems to have a pretty detailed fix on page 5 that looks interesting, and I may give that a try after seeing what shows up over the next few days. Is there any clue as to when the dev team will have a fix? 

Huge Thanks to All! :guitar:

Like I stated earlier, I'm rather new to Linux and have seen many complaints from hardcore Linux/Ubuntu Linux users on this thread, and it makes me wonder if any Billy's friends ended up sneaking in... Never mind. Does anyone remember SCO a couple years ago??? :twisted:

I'm converting from a Win 2K system, used XP for a short while, and won't even think of Vista (Dev name CE-ME-NT)[Funny Vista Commercial]("http://www.youtube.com/watch?v=jOh6Nh8w6f8").

---

### Post by quinnten83 on 2008-09-27
I've got the lockups too, but I think it is a bit unfair to say that the Ubuntu developers are not trying to solve the problem. I think these lockups are difficult to solve. They happen randomly, I could be using my pc for day without any problems, and then it might lockup several times in one day. And you can't relate it to hardware because everyone has different hardware, there is no common thread.
The reason why the developers seem to be focusing on intrepid is because it has new and improved version of pretty much everything, so with bugs worked out. I can understand that. I know that solving problems in IT is a daunting task.
I think that everyone would be more sympathetic if the developers would just say that they don't know how to solve this problem yet, though.
But I also think we need to stop shouting at the developers because it does not work.

---

### Post by bigbrovar on 2008-09-28
I had random lockups when i first installed hardy.then i downgraded to gutsy for a while after which i upgraded again.this time everything went smooth and i had no more locks,not one and its over 5 months now

---

### Post by stans on 2008-09-28
For the record, I'm having random lockups as well on 8.04.

BTW - names ('Hardy') and release levels ('8.04') are used interchangeably on these forums and it is very confusing to know what someone may be talking about. Is there a cross reference somewhere ? I've looked around...

---

### Post by Riffer on 2008-09-28
> **stans said:**
> For the record, I'm having random lockups as well on 8.04.

BTW - names ('Hardy') and release levels ('8.04') are used interchangeably on these forums and it is very confusing to know what someone may be talking about. Is there a cross reference somewhere ? I've looked around...

the release is 8.04 with code name "Hardy Heron".  The next is 8.10 with the release code name "Intrepid Ibex".  The release cycle is every 6 months in April the 4th month of the year and November the 10th month, hence the '04 and 10 in the release number.

---

### Post by gjoellee on 2008-09-28
I am using Intrepid and I have never used a better distro!

---

### Post by ukripper on 2008-09-29
> **gjoellee said:**
> I am using Intrepid and I have never used a better distro!

countdown has begun!
[https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)

---

### Post by ThermiteJMJ on 2008-09-29
I still think gutsy is best.  works like a charm on Dell D600.

---

### Post by Darkangel14615 on 2008-10-03
> **Riffer said:**
> November the 10th month...

Read that over one more time...
Lockup problems are gone in Intrepid, just use it, despite a bug here and there it works fine.

Unless you have Intel wireless, of course.

---

### Post by GeoffreyBernardo on 2008-10-04
> **Jim March said:**
> Switching to the -rt kernel is easy - you just pull the kernel modules ending with "-rt" out of Synaptic, edit your grub menu and reboot.  Lots easier than a kernel compile and you can quickly back out if needed.

How do you edit the grub menu? And what do you edit?

My computer is still downloading the -rt files through synaptic.

Thanks.

---

### Post by malangaman on 2008-10-04
> **GeoffreyBernardo said:**
> How do you edit the grub menu? And what do you edit?

My computer is still downloading the -rt files through synaptic.

Thanks.

Here are two sites that will help you to edit Grub.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by vikramaditya on 2008-10-04
This thread deserves a bunch of roses for having long legs (started April 26th) & for reminding me of "Lost in Space" (WARNING, WILL ROBINSON!) everytime I read that kooky title. :lol:

---

### Post by psychomichael on 2008-10-05
> **vikramaditya said:**
> This thread deserves a bunch of roses for having long legs (started April 26th) & for reminding me of "Lost in Space" (WARNING, WILL ROBINSON!) everytime I read that kooky title. :lol:

heheh...I'm just glad Intrepid's coming out finally.

---

### Post by squee on 2008-10-08
> **psychomichael said:**
> heheh...I'm just glad Intrepid's coming out finally.


Not to burst your bubble or anything but Im running Intrepid, came searching through here and found this thread trying to find a cause/solution to my random lockups and flashing caps lock.

You had better just hope that the problems are fixed for the final release.

---

### Post by aged hippy on 2008-10-08
> **squee said:**
> Not to burst your bubble or anything but Im running Intrepid, came searching through here and found this thread trying to find a cause/solution to my random lockups and flashing caps lock.

You had better just hope that the problems are fixed for the final release.

I'm running Intrepid on both the Gnome and KDE desktops, and i second that.

"Nightmare" is probably the best word to describe Intrepid at the moment, in my experience .... at least, on the KDE desktop.

"Bad dream" is possibly more suitable for the Gnome. :)

---

### Post by psychomichael on 2008-10-08
Yeah, I have to agree at least about the KDE version so far. It wouldn't even load on one of my computers and barely on the one I'm using now. I had to disable graphics support. I submitted some bug reports...if they don't fix the problems that exist on Hardy and are problematic on Intrepid so far, they're going to lose a lot of the market share of linux users really fast.

---

### Post by squee on 2008-10-08
Come on now. I think we are really overreacting calling it a nightmare. Its still weeks from official release. If the problems persist into mid November then there is a problem. A lot of people who are on Hardy wont be prompted for the update since Hardy is LTS.

By the time they remember, the problems /should/ be fixed. I think its something to be expected when everyones machine is unique in the software and hardware it has. Compared to most vista machines which have the same software. The price we pay I suppose. If you dont like whats happening, teach yourself to program and fix it, or use a stable release.

Myself, Im not doing either of those. I just like living on the bleeding edge! :guitar:

---

### Post by night-wing on 2008-10-09
> **ThermiteJMJ said:**
> I still think gutsy is best.  works like a charm on Dell D600.

I agree to this. The only issue on my hp is the headphone jack.

On hardy, there are issues without end. Intrepid already works better.

---

### Post by Keymaster on 2008-10-09
I haven't had many issues with Hardy, nor have I heard of anything so serious as the original post, until I saw this thread.  I'm just waiting for Intrepid so I can install the latest version on my gaming laptop.

---

### Post by cygnus-X1 on 2008-10-13
I tried the fix posted by Jim March. ](*,) No dice. ](*,) The machine still locks, reboots or shuts down at random. I have a spare drive, so I'll try the Intrepid Beta and see what it does. If it craps out, I'll try Gutsy. Hopefully I won't be forced to go to another distro. I hate having to relearn things! 

Like most everyone reporting in so far, We cannot afford to have our PCs do this. Especially when running editing or other long process ops. If anyone finds an answer or a potential fix, I think everyone here would appreciate a detailed how-to post.:guitar:

Thanks and good luck!

Follow up: Random shutdowns and reboots are Mobo related (Abit AN-M2HD).
           Random lockups/freezes are definitely 8.04/hardy related!

Resolved (finally!): Initially thought it was the Mobo. Turned out to be the memory. The Super Talent memory was only rated at 1.8v and Mobo's minimum was 1.85v. Moved to G.Skills 1.8-1.9v rated memory, and lock-ups are a thing of the past. Of course it would have been nice to know about the voltage incompatibility before hand, but at least it's fixed now.

---

### Post by DrMilo on 2008-10-13
I simply don't know what to make of it. I get lockups for a few days in a row and then go months without any. It seems to correlate with a lot of graphics displaying, either video or jpegs but it's not consistent. I have left it locked up and walked away for hours to see if the OS will sense something, it doesn't. Nothing but a reboot will punch through when this happens either, not even ctrl alt backspace! Also my numlock may or may not be on at any given time.

---

### Post by sosaudio1 on 2008-10-14
Think someone needs to dumpster dive into the kernel and see if there is new code added that is causing this. Sounds like kernel panic...i haven't gone thru all 85 pages of notes but the last few talking about flashing lock lights makes me run to kernel panic and disconnect. How far back can you go with a kernel? Give a old kernel a try and see what you get

---

### Post by radtek on 2008-10-14
I've experienced the random lockups with Hardy when using FF while posting on forums mainly, or when I try to open a new instance of FF. It had gotten better for a period of time when I had disabled Java & JavaScript. Then it started acting up again much worse than ever. Flashing caps lock light and hard reboot required instead of CTRL+ALT+BKSP just about every time I use FF.

I just installed Intrepid. Like the looks and the fact that my wifi card was instantly recognized. FF seems a little laggy performance wise. I haven't had much time to explore since I've rushed myself off to the ER with a serious laceration (I'm there now) with my Acer Aspire One. 

I had set my Toshiba to download the 275 updates or a partial upgrade. Let's see what it is like when I make it home.

IMO the lockup problems probably based on the user's own System & Hardware config and not just one thing in Gutsy or Hardy.

I've never submitted a bug report on the issue so I only have myself to blame.

---

### Post by sosaudio1 on 2008-10-14
With all these hard lock-ups, is there a utility that we can run to help smooth out the HDD? I have had a couple here and there but mine come from making Miro go full-screen and usually after watching something in the smaller default scale. This is with a Dell Dimension 2400 running the 2.40G Processor and on-board intel GPU and a gig of RAM

Thankful that I am not experiencing all the lock-ups that you guys are...wish I could help

---

### Post by Chainz on 2008-10-16
I have just replaced my Graphics card in my PC, from ATI Rage 128 to ATI HD 3450...
And guess what? NO MORE LOCKUPS!!! :D

---

### Post by squee on 2008-10-16
I've had no lock ups since the last kernel upgrade on ibex. Maybe it was fixed

---

### Post by thrasher6900 on 2008-10-17
try intrepid and install scrollkeeper and nautilus via terminal.  You won't get a dexktop at first so you have to hit ctrl F1 to get into the command prompt.





All my bugs are fixed and it's still in beta.

---

### Post by spawn. on 2008-10-17
Nothing is perfect. I remember a time when my cube locked up during movement. I had to Alt +F9 and make sure it wasn't anything serious. IF I were going to leave the Ubuntu community, I would move to OpenSuse 11.

---

### Post by cliff01 on 2008-10-25
System seems stable after last update. Been running for 30 hours and all is well. (Fingers crossed, waiting for final release of Intrepid)

---

### Post by cliff01 on 2008-10-25
%^*$%$%^& I spoke too soon. No sooner did I leave my last posting when BLOOOOOEY it locked up.
The 30th, right??

---

### Post by codeking on 2008-10-25
Darnit.  I though Ibex would fix all these freeze-ups.  You would think after 6 months they would have it fixed :(

There's still hope I guess, since its only beta.

---

### Post by DrMilo on 2008-11-01
One last night and last weekend. The thing is that I do almost exactly the same things every time I'm on my computer, so why do I go days, weeks, months, between lockups? I'm tempted to think that it's some sort of Internet attack!

---

### Post by antrunner85 on 2008-12-31
I must say that being a newbie  at Ubuntu, Hardy heron has been a painful experience. I started working in ubuntu 7.04 and I must say that I was the most confortable with 7.10. 
Ubuntu Hardy has had so many down sides ( no global menu, brightness control makes my computer crash, problems with skype, screen flickers when coming back from screen saver, flash keeps crashing in firefox, etc,etc, etc) that makes me want to start all over with a new fresh installation of Ubuntu 7.10
:(

---

### Post by solwic on 2008-12-31
> **antrunner85 said:**
> I must say that being a newbie  at Ubuntu, Hardy heron has been a painful experience. I started working in ubuntu 7.04 and I must say that I was the most confortable with 7.10. 
Ubuntu Hardy has had so many down sides ( no global menu, brightness control makes my computer crash, problems with skype, screen flickers when coming back from screen saver, flash keeps crashing in firefox, etc,etc, etc) that makes me want to start all over with a new fresh installation of Ubuntu 7.10
:(

This tired old thread is still going on?  :P

A lot of people liked 7.10.  I think it's kind of funny that there's such a concerted opinion that the Ubuntu devs did their best work two releases ago, though.  

Anyway....go Ubuntu! :)

---

### Post by zipperback on 2008-12-31
> **Jim March said:**
> Some users, myself included, are experiencing random total lockups.  The systems are freezing up so tight there's no way to get diagnostics info.  It's affecting different video chipsets, different WiFi chipsets, some Ethernet users, there is NO pattern to the hardware involved.

EDITED DOWN TO MAKE THIS SHORTER...


This really sucks.






I have Hardy installed on an Acer Aspire 5050-3371 and it works for me without any problems.

My wife and I both share this laptop so it gets heavy use under a wide range of conditions and usage needs.

What us your specific hardware? Perhaps I can help you get your system up and running.

- zipperback
-:popcorn:

---

### Post by psychomichael on 2008-12-31
> **jrock612 said:**
> I think it's kind of funny that there's such a concerted opinion that the Ubuntu devs did their best work two releases ago, though.

Truly. 7.10 is still working great on my machine while the others won't even boot.

---

### Post by jrusso2 on 2009-01-01
What ever problems Hardy had they seem to be fixed.  I have used it for months with no problems, no lockups, etc.

---

### Post by zero244 on 2009-01-01
Ive only been using Hardy for about a week. I had some issues for one I had to enable apic=off which reduced the freeze ups by 95 percent.
I am still having occasional lockups.
Im beginning to wonder if its related to compiz.
Im just running compiz with the default settings plus the scale plugin. Im not doing the cube and most of the other special effects.
Its odd though I can have my computer running all day no lockups.
Reboot to clear the memory and Have a lockup in 10 minutes or 2 hours later.
I do run a VM on and off during the day with vmplayer 2.5, Im a little auspicious of vmware player might possibly be causing this.

Random anything is hard to pin down.
I like Hardy overall better than any Ubuntu Ive installed to date.
I hope I can resolve this issue.
On thing I did do was wait till mid December to try Hardy. Ive noticed a lot of people having problems were early adapters.
Previously I have been running Edgy on this machine since the release.
Once I got rid of a bad out of the box video card, Edgy has not froze up on me once. Not one freeze up in over a year of constant use.

Other than a occasional lockup Hardy runs smooth as silk, its fast and has a very solid feeling.
Im hoping the lockup is a software related problem and not a kernel problem. I dont really want to update my current kernel because I will have to reinstall my video drivers.
Time will tell.

---

### Post by phlembob on 2009-01-01
This worked for a couple first time frozen systems.  Download Hardy from the weather National Severe Storms Lab.  They use Linux Kernel with their programmers as their base, and have experienced government people archiving.  Their machines are well maintained.  This eliminates any injected problems from inexperience or poor maintenance.

---

### Post by EricNMiller on 2009-01-05
I have had problems with my home network where Ubuntu Linux hangs at boot up with my RJ-45 cable connected to the integal NIC on my Intel motherboard D946GZ15.  This goes back to Fiesty.  I am running Hardy 8.04 now with the same result.  Initially I found that everything boots OK if I always disconnect the RJ-45 cable upon shutting the desktop PC down.  An error display pops up in the upper left corner of the screen at boot up with the network cable connected reading: "There was an error starting GNOME settings Daemon.  Something such as themes, sounds or background settings may not work correctly."  "The last error message was:Did not receive a reply. Possible causes include: the remote application did not send a reply.  The message bus security policy blocked the reply, the reply timed out, expired or the network connection was broken.  GNOME will still try to restart the settings Daemon next time you login."  At this time only the desktop image loads and I must disconnect the network cable and reboot.  My problem seems to be exactly opposite to jtbalt post 36.

---

### Post by xaco1234 on 2009-01-05
is it posible to spam more thingy87654321?

on topic: only problem i had with 8.04 was flash, same problem i still have for that matter.

---

### Post by thingy87654321 on 2009-01-05
sorry about all the agrees, i needed to get up to 75 posts to beable to send messages to other people on ubuntuforum.org

---

### Post by jesuspresley on 2009-01-05
I do not have any problems with Hardy, but with Intrepid there was some pain getting the VPN connection up and running.

Hardy works fine on my Desktop and Intrepid on my Laptop. No crashes so far, except for some misconfiguration issues in Compiz.

---

### Post by owend on 2009-01-24
Marathon post! My experience is Hardy is generally great, but not with kernels after -16 (-19 gave a couple of freezes, and -24 freezes sometimes even before fully booted). I've gone back to -16, and no problems (Acer laptop with AMD Turion). 

Only problem was my own making - garbled everything by trying another distro (Fedora; not its fault, bad partition instruction from me!); clean installed Hardy, again perfect with kernel -16. 

If you update, keep the last safe kernel!

FYO: I've tried Kubuntu 8.10, didn't like it - panels kept coming apart and for some reason it wouldn't load Thunderbird.

---

### Post by zero244 on 2009-01-24
I was having lockups so I added this line to the end of my Kernel line in grub menu.lst

apic=off highres=off nohz=off irqpoll

Since making this change Ive had only one freeze in the last month and that was on boot up so it might of just been a fluke.

I think with my machine its a irq conflick with the video and the powermanagment system.
Both my video and acpi are on the same irq.
At anyrate I dont seem to having any lockup problems.

Hardy when stable is a great OS.
Its smooth and fast and very well put together.

Ive considered upgrading to Intrepid but I dont think if offers enough to make it worth the trouble.

Plus support for Hardy still has a couple of years left.

---

### Post by LeeHB on 2009-01-26
With Intrepid 8.10 running in Wubi in a New Asus dual-core MB with 2gig ram...NVidia 8600GTS...

Regarding the 'lockup' phenomenon...I just had a weird thing happen for the second time...while searching for a particular file in Nautilus, the screen began to dim as tho the screensaver was going to kick in...no mouse or keyboard actions had any effect on it...the screen blacked out...there was no screensaver...nothing at all...we were D.O.A...

I WAS able to do a ctl-alt-backspace to restart the desktop which worked fine. The desktop came back - My screensaver had been set to go off after 20 minutes...I disabled it...so far no more problems. I'll keep an eye on it.

LeeHB

---

### Post by malangaman on 2009-01-26
I have monitored this thread from the very beginning and held off upgrading my Gutsy installation to Hardy out of respect for problems detailed in this thread . Two days ago I finally upgraded my favorite box to Hardy 8.04. It took less than an hour and the results have been outstanding. Everything works and my applications all run faster. 

Intel Pentium III 1GHZ cpu, 1GHZ RAM, ATI 64MG video card, SOYO MB

---

### Post by kspncr on 2009-01-27
At least it seems like people are happier with Hardy now. Personally, I've loved Hardy from the very beginning. It has NEVER crashed on me. Ever. I never knew what all the lockups and problems people kept mentioning are all about.

---

