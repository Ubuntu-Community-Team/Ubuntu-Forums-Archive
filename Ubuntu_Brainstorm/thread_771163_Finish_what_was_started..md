---
title: "Finish what was started."
date: 2008-04-27
forum: Ubuntu Brainstorm
---

### Post by exploder on 2008-04-27
My idea is to finish a release, Hardy to be specific.

The floppy drive issue was not resolved before Hardy went final.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954)

Usplash problem.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

Leaving these kind of bugs in a final release is why Linux has the smaller user base, even that other OS would not make a public release with such obvious bugs left unfixed.

Certainly no one can fix everything but these bugs show a lack of quality control and should not just be forgotten about.

So, my idea is to actually finish work that was started. The distribution could go a lot further and gain a larger user base.

---

### Post by smartboyathome on 2008-04-28
If Hardy tried to resolve every bug that was out there, then it wouldn't be released. If your bugs were fixed, why couldn't someone else's be? This would go on and on forever, since you can never make it completely bug free AND up to date.

---

### Post by exploder on 2008-04-28
These are pretty serious bugs, not minor hardly noticed things. Could you imagine the reviews Microsoft would get if they released an operating system with these same bugs? 

These types of bugs not being fixed is why Microsoft's product is on most PC's. How can you offer support for a product that does not work properly in the first place?

Have you even looked at the number of bugs in Hardy? Linux in general has to do better if it is to compete with Microsoft. We as Linux user's just seem to accept all of the bugs in each release and hope the next release is better.

I have been using Linux for years, it has come a log way but without better quality standards it will never be competitive.

---

### Post by smartboyathome on 2008-04-28
1) Floppies are not used as much anymore, so it isn't very serious.
2) This bug doesn't ruin the usability for me, as it just says that and then shows the splash screen.
3) If you want that kind of stability go to Debian Sarge/Etch. Ubuntu tries to balance new release software and stability.

---

### Post by exploder on 2008-04-28
You find this acceptable when you shut down or log off?


Network Manager: <WARN> nm_signal_handler(): Caught signal 15. shutting
down

Network Manager: <info> caught termination signal

Network Manager: <debug> [1209069304,808145] nm_print__open socks(): Open sockets
List:

Network Manager: <debug> [1209069304,808366] nm_print_open_socks(): Open sockets
List Done.

Network Manager: <info> Deactvativing device eth0

Network Manager: <WARN> nm_hal_deinit(): libhal shutdown failed connection is
Closed

Network Manager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system
bus. Make sure the messagebus daemon is running!

Network Manager: <WARN> nm_dbus_signal_device_status_change: asserion `cb_data->data->d
bus_connect xxxx failed

The floppy drive worked in previouse releases. With the logic you are using maybe it would also be ok to drop support for DVD-ROM's, CD-RW drives because most computers now come with combo drives. 

I will stay right where I am. I spent six months testing and reporting bugs.

I would simply like to see the bugs fixed in this release. Seems like a good idea to me.

---

### Post by dualscreenman on 2008-04-28
You are twisting his logic. Combo drives are a DVD-ROM and a CD-ROM drive built in to one drive. You cannot un-support a DVD-ROM or CD-ROM drive without un-supporting the combo drive. Floppies are also really, really old and obsolete. CD-ROM drives are, on the other hand, still widely used and not quite so obsolete. In fact, the only way to get Kubuntu-KDE4 in a physical medium is to use a CD (No DVD). Your argument can't stand.

---

### Post by exploder on 2008-04-28
So you think the screen full of errors should be left as is?

Weather the device is old or not has nothing to do with the issue. It worked before and you can still purchase the drives.

Don't you think Ubuntu would be more of an alternative to Windows if it wasn't so full of bugs? 

There is no argument to make stand. My idea is to fix the bugs and make things work like they should.

Do you honestly think a large corporation would trust Hardy on their servers and desktops as it is right now? Hardy shows many improvements but even the IT Department where I work say it looks more like a beta than a finished product.

I am talking about fixing these extremely obvious bugs. Login Window is another, it takes 10 minutes to open the first time!

I present my idea plain and simple, "Finish what was started."

---

### Post by smartboyathome on 2008-04-29
> **exploder said:**
> Do you honestly think a large corporation would trust Hardy on their servers and desktops as it is right now? Hardy shows many improvements but even the IT Department where I work say it looks more like a beta than a finished product.

I don't know, ask the top fortune 500 companies what they use. I bet they use Linux, at least on their servers. No, they may not use Ubuntu, but it isn't made to be ABSOLUTELY STABLE, and maybe something changed where Floppies couldn't be supported. I don't think that we should waste time developing support for them anymore. The network manager text is manageable until the problem of the bug IS LOCATED, if you look on the bug no one has located what causes the bug, so no solution exists.

---

### Post by JamesUser on 2008-04-29
Hey.. I think exploder has a point. Why don't u stop accepting bugs for floppy drives then? That's not the issue. The issue is ubuntu is meant to be user-friendly. Desupporting devices which are available in the marketplace and error messages certainly aren't user-friendly.

@smartboyathome: Agreed. We cannot fix each and every bug. Maybe we can have a bug-fix release somewhere down the line.

I also get a lot of error messages during shutdown. I certainly don't have a floppy drive. ;-) I would be glad to help the developers if someone can give me the bug number.

---

### Post by exploder on 2008-04-29
There are currently two bug reports on the Network Manager errors.

[https://bugs.launchpad.net/ubuntu/+bug/221525](https://bugs.launchpad.net/ubuntu/+bug/221525)

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

The two reports appear to be related and the last entry stated that GDM could be the cause of the problem.

JamesUser, thanks for understanding what I was trying to convey.

---

### Post by Sophont on 2008-04-30
Both bugs are fairly minor from what I gathered from the bug reports (I don't see the usplash problem myself and wouldn't notice the floppy problem).

OTOH both would make Ubuntu appear clunky on affected machines so getting them fixed would be nice.

A good opportunity would be the planned minor release update in july (due to FF3 final I guess).

I guess floppy problems get easily overlooked because I assume only a very few developers still have floppy drives installed - and most of those probably don't get used anymore. (it's the age of cheap multi-GB RAM sticks - 1.44 MB floppies don't make sense anymore - unless your machine doesn't have a USB port - and a USB card is cheaper than a floppy drive).

I can understand why somebody would think it looks bad when you see those bugs - but what percentage of people is affected by this? Tiny is my guess. Certainly nothing that should have delayed 8.04.

BTW - all software products larger than a few hundred lines of code get released with bugs. I have heard of major software packages that use 10000 defects as threshold for release (most minor bugs, nothing too critical of course).

We don't know what the criteria for windows is - sadly no public bug database. But one thing we do know - it does not ship bugfree.
And the dominance of windows or lack of dominance for any alternative has not much to do with the kind of bug in this thread.

After all MS tolerated critical bugs in IE 6 for months - until the success of FF forced it to re-assemble a proper dev team for IE.

Nowadays windows keeps its dominance pretty much because - it is already dominant. Users are used to it. People want certain software packages (either because they are genuinely better or - again - because they are used to them). And most games don't run out-of-the box on Linux/OSX.

Windows survives mostly due to inertia now - but even that won't save it forever.

If this kind of bugs would kill an OS - people everywhere would kick Vista and switch to OSX right now. There's plenty of machines where Vista has trouble with this piece of hardware or that piece of software.

---

### Post by ibanez on 2008-04-30
> **exploder said:**
> There are currently two bug reports on the Network Manager errors.

[https://bugs.launchpad.net/ubuntu/+bug/221525](https://bugs.launchpad.net/ubuntu/+bug/221525)

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

The two reports appear to be related and the last entry stated that GDM could be the cause of the problem.

JamesUser, thanks for understanding what I was trying to convey.


I also understand ... Try searching out all the sound bugs on launchpad. 
Hardy was NOT ready for the desktop.. But when did the Devs EVER listen to us users ??
Trackerd still hogs resources, Pulse audio is causing major problems, new xorg is a newbs nightmare if it doesn't ( & frequently doesn't) detect your video hardware correctly.) The list goes on but you will always have the few that these problems don't affect denying their existence!.. Thats the Linux world unfortunately, not just tied to Ubuntu either. 
Fact is on the three boxes running Hardy here there are major annoyances, the Gutsy ones are running as they always have... sweetly. 
If you install a final release "exploder" is correct .. you DON'T expect problems like these. To me at least Ubuntu seems to be taking one step forward, Two steps back.

---

### Post by exploder on 2008-04-30
Very well put, ibanez. I have seen reviews calling Hardy a beta.The last of three machines I had Hardy on now has the screen full of Network Manager errors.

Ubuntu is selling support, how can you sell support for something that does not work right in the first place?

Feisty and Gutsy have the gnome-setting-daemon error that was never fixed. I do not want to see a LTS release left in this shape and it really makes the distribution look bad. Should user's just expect bugs to be present and never resolved? Each release seems to have more bugs than the previous release.

Wouldn't it be nice to see Ubuntu associated with quality? It is time to finish what was started, Attention to quality as well as innovation will enable Ubuntu to reach it's goals.

---

### Post by JamesUser on 2008-05-01
@exploder: Yeah. Eye candy may attract users but quality is what makes them stick to a piece of software.

IMHO, Ubuntu needs more developers and more people to coordinate with upstream developers.

Here's a list of bugs that need to be fixed. [http://daniel.holba.ch/really-fix-it/](http://daniel.holba.ch/really-fix-it/)

---

### Post by qamelian on 2008-05-01
> **ibanez said:**
> I also understand ... Try searching out all the sound bugs on launchpad. 
Hardy was NOT ready for the desktop.. But when did the Devs EVER listen to us users ??
Trackerd still hogs resources, Pulse audio is causing major problems, new xorg is a newbs nightmare if it doesn't ( & frequently doesn't) detect your video hardware correctly.) The list goes on but you will always have the few that these problems don't affect denying their existence!.. Thats the Linux world unfortunately, not just tied to Ubuntu either. 
Fact is on the three boxes running Hardy here there are major annoyances, the Gutsy ones are running as they always have... sweetly. 
If you install a final release "exploder" is correct .. you DON'T expect problems like these. To me at least Ubuntu seems to be taking one step forward, Two steps back.
It's ready for the 7 desktops and 2 laptops I've installed it on either with a clean install or, in 4 cases, from the update manager. It's is running flawlessly on every one of those systems. No issues with trackerd resource usage or pulseaudio. 

No OS is every 100% ready for every desktop, but based on the various machines I've tested Hardy on so far, you couldn't convince me it wasn't ready.

---

### Post by enchantedsky on 2008-05-01
Very interesting discussion, because the network bugs affect me too (and it's more of an eyesore just seeing Network manager errors when I shutdown Ubuntu Hardy Heron.) I mean, if the developers could even just HIDE the error messages, it would make people feel a lot better.

I have one more comment about floppy disks: People do not have to use *new* floppy disks. They may have old programs or data on *old* floppy disks that they have, and without the proper floppy drive support on Ubuntu, they won't be able to access their old floppy disks.

For instance, everyone who used computers in the 1980s may have used MS-DOS. I definitely have old DOS computer games on floppy disk, and YES, it can run on Ubuntu using the DOS emulator DOSBox. But how would I install the games on my hard drive if there is a bug with floppy disk drives? It forces me to go to Abandonware websites and download pirated DOS games.

So I think some people miss the point in saying floppy drives are irrelevant, especially if Ubuntu (through emulation) can run old programs on older floppy disks that people may have. People are not going to use floppy disks like a flash drive to store data these days; they only care about older data on floppy drives. It is a bug that needs to be fixed in 8.04

---

### Post by ibanez on 2008-05-01
> **qamelian said:**
> It's ready for the 7 desktops and 2 laptops I've installed it on either with a clean install or, in 4 cases, from the update manager. It's is running flawlessly on every one of those systems. No issues with trackerd resource usage or pulseaudio. 

No OS is every 100% ready for every desktop, but based on the various machines I've tested Hardy on so far, you couldn't convince me it wasn't ready.

Just like I said in my post .

you will always have the few that these problems don't affect denying their existence!..

I guess all the others experiencing these problems are just imagining them. :lolflag::lolflag:

Just because they dont affect you does not mean they dont affect others . Launchpad will tell you they exist for sure.

---

### Post by qamelian on 2008-05-01
> **ibanez said:**
> Just like I said in my post .

you will always have the few that these problems don't affect denying their existence!..

I guess all the others experiencing these problems are just imagining them. :lolflag::lolflag:

Just because they dont affect you does not mean they dont affect others . Launchpad will tell you they exist for sure.
I never said the problems didn't exist, so don't go putting words in my mouth. However, I get sick of hearing every release how the latest Ubuntu is not ready for the desktop when I and many others have been successfully using it on production desktops without any issues. It works both ways. You don't want people saying problems don't exist because they don't encounter those problems and I don't want people exaggerating or lying (which has happened, though not necessarily in this thread) about Ubuntu's desktop readiness. I have read threads in which one or more users have a particular problem and seem to insist that everyone else must also be having the problem or else be lying about it. It gets tiresome, especially when you start searching bug reports and see how few of the complainers have actually contributed anything useful ( or anything period) that might actually help resolve the problem that afflicts them.

---

### Post by exploder on 2008-05-01
You might want to have another look at those bug reports, they are growing fast! Also, Hardy has had some unfavourable reviews.Have a look in the "General" section of the forum.

What do you have against fixing the bugs anyway? If there are so few as you are suggesting, why not fix them?

---

### Post by qamelian on 2008-05-01
> **exploder said:**
> You might want to have another look at those bug reports, they are growing fast! Also, Hardy has had some unfavourable reviews.Have a look in the "General" section of the forum.

What do you have against fixing the bugs anyway? If there are so few as you are suggesting, why not fix them?
What makes you want to put words in my mouth?? I never, ever, under any circumstances, in any way, shape, or form, indicated that I didn't want the bugs fixed. Take the time to read exactly what I wrote and tell me where I said any such thing. What I said is that people should stop making blanket statements that Hardy is not ready for the desktop, when for most users that I know, this is simply not true. Do you think pretending I said something that I didn't magically makes it so?

Also, Hardy has had many very favourable reviews as well. Do some searching yourself.

---

### Post by exploder on 2008-05-01
If you do not like the idea I proposed, move on. I am glad your machines run flawlessly on Hardy. 

I won't waste my time arguing with you.

---

### Post by ibanez on 2008-05-01
View Poll Results: What was your hardy install/upgrade experience ?
Upgrade - worked flawlessly 		[COLOR="Lime"]199 [/COLOR]	12.68%
Upgrade - worked but had few things to solve 		[COLOR="Red"]459[/COLOR] 	29.25%
Upgrade - got many problems which i've not been able to solve 		[COLOR="Red"]276[/COLOR] 	17.59%
Install - worked flawlessly 		[COLOR="Lime"]144[/COLOR] 	9.18%
Install - worked but had few things to solve 		[COLOR="Red"]250[/COLOR] 	15.93%
Install - got many problems which i've not been able to solve 		[COLOR="Red"]241[/COLOR] 	15.36%

Well this kinda speaks volumes for me .... Note the differences between problems vs no problems ... 
That really doesnt signify a ready for desktop for the Majority of users, Your argument is seriously flawed.  OK it works for you, but it seems many many more are experiencing problems .

This is the last I have to say on this subject I choose not to FTT's.... 

[http://ubuntuforums.org/showthread.php?t=764847](http://ubuntuforums.org/showthread.php?t=764847)

---

### Post by smartboyathome on 2008-05-01
That doesn't accurately reflect the distro. People come to the forums BECAUSE they have problems, if they don't have problems they don't come to the forums and thus don't vote.

---

### Post by exploder on 2008-05-01
That would be an opinion because you have no data to back it up.

ibanez presented data.

1,569 people voted, that is a pretty significant number.

---

### Post by magicplayr2000 on 2008-05-01
Just throwing this out there, but 1,569 people voting in the poll doesn't make it an accurate assessment.  The first time I came to the forums was because of problems I was having in 7.04.  I would feel pretty comfortable that there are people who came here for the first time because of issues with a new install.  I didn't vote in the poll, for example, and I had a pretty clean upgrade on the 2 computers I have.  My friends who upgraded did so without any problems, and since they had no reason to come here to ask for help with it, they didn't vote.  A large sample size doesn't matter if the sample isn't evenly distributed.

I'm sure there are lots of people who've had problems, but it's come a long way.  I remember when getting wireless cards to work was almost a lost cause, and now it's not so bad.  After helping a lot of friends install Ubuntu on their laptops, I haven't had any problems with wireless cards.

---

### Post by qamelian on 2008-05-01
> **exploder said:**
> That would be an opinion because you have no data to back it up.

ibanez presented data.

1,569 people voted, that is a pretty significant number.
Since estimates of the number of Ubuntu users range as high as approximately 8,000,000, the number of users represented in that poll are almost insignificant. That doesn't mean that the bugs they are complaining about should be ignored, but you do need to be realistic. It is a factual impossibility to eliminate every single bug that affects every single user or, based on any numbers I can find, relatively small group of users. Ubuntu could have a 6 *year* release cycle and this would never be possible.

---

### Post by exploder on 2008-05-01
I agree with you that every single bug can not be fixed. I want to see the real obvious ones in my original post fixed.

Something else to give some thought to. Windows 95 was released by Microsoft with 256 bugs. How many bugs does Hardy have? Windows 95 was considered to be extremely buggy. (Just trying to illustrate)  

Ubuntu has the potential to be an enterprise solution, the key word though is potential. The system needs to be refined if it is to be considered anything more than a hobbyist distribution. 

I want to see Linux on the computer's of big corporations. Maybe my expectations are too high?

---

### Post by qamelian on 2008-05-01
> **exploder said:**
> I agree with you that every single bug can not be fixed. I want to see the real obvious ones in my original post fixed.

Something else to give some thought to. Windows 95 was released by Microsoft with 256 bugs. How many bugs does Hardy have? Windows 95 was considered to be extremely buggy. (Just trying to illustrate)  

Ubuntu has the potential to be an enterprise solution, the key word though is potential. The system needs to be refined if it is to be considered anything more than a hobbyist distribution. 

I want to see Linux on the computer's of big corporations. Maybe my expectations are too high?
Windows 95 also consisted of a much smaller codebase than the default Ubuntu install. Also, there were fare more than 256 bugs at release time. The bugs you are referring to were only the ones that were considered high profile bugs. If you do a little more digging, you'll find that you can add at least one digit to arrive at the number of actual bugs that had been documented prior to release, and many more were discovered after release. 

I can understand people being frustrated with bugs. I've encountered a few myself that I found seriously annoying in some releases of Ubuntu and pretty much every other distro. The reason I stick with Ubuntu now is because, overall on my hardware, Ubuntu has always played better than any other distro bar none. Neither OpenSuse nor Fedora have ever worked properly with the integrated sound on my laptop, and Mandriva is completely unuseable due to power management issues that cause the same laptop to overheat and shutdown to quickly to even examine any logs to find a clue to the problem! The Mandriva issue has existed in every single release after 10.2 and has never been addressed. I've never seen Ubuntu let a real show-stopper go that long.

---

### Post by nanog on 2008-05-01
+1 on additional time spent bug fixing this LTS release.

I have installed hardy on 10 boxes 2 servers and 3 laptops. There have been major annoyances on **every** box. IMO,  gvfs, pulseaudio, and FFbeta and the disappointing 2.6.24 kernel has made this the buggiest Ubuntu release yet. I really hope that developers and volunteers are focusing on the 8.04.1 release instead of Ibex. If it were up to me I'd vote to skip Ibex entirely. Edgy was a complete waste of time.

---

### Post by JamesUser on 2008-05-01
Interesting stats we've got up there. Out of 1600 people who participated in the poll, about 520 have not been able to solve the problems they have had. Though a fix might now be available for a few of their problems, the ratio doesn't look too good to me.

Now, the point is not whether Hardy looks like a beta release or not. Another interesting stat is, in the thread linked to by Ibanez, one guy who warned people about installing Hardy on production systems got a lot of thanks.

The point is to admit there are quite a few bugs which are causing unpleasant experiences to a fair number of users. Whether these need to be resolved or not, is the question. A few people say that from July, with the release of Firefox 3, things will start looking better for Hardy. With that quite a few bug fixes are being packaged from upstream.

---

### Post by MacUntu on 2008-05-03
Again: As you don't know the motivation of ppl coming here, those numbers are worthless (even for "minor problems" vs. "problems I couldn't fix").

---

### Post by Gina on 2008-05-05
Hardy has bugs, Gutsy, Feisty and previous versions have bugs (still not fixed), Win XP still has bugs after 8 years (M$ are releasing SP3), Vista has ooodles of problems I hear for some people - others no problems at all.  What I can say from a personal point of view (not having done an unbiased survey of Hardy users) is that Hardy is very much better than Gutsy.  No software is bug free - operating systems are more complex than individual apps and bugs are more serious.  I know of no OS that hasn't been followed by a bug-fix update (or 3).  Hardy has a bug-fix update due for July with minor updates in the meantime.

---

### Post by plun on 2008-05-05
> **Gina said:**
> Hardy has a bug-fix update due for July with minor updates in the meantime.

Well... UF is flooded  with questions and our devs has fixed major trouble

[https://lists.ubuntu.com/archives/hardy-changes/2008-May/thread.html](https://lists.ubuntu.com/archives/hardy-changes/2008-May/thread.html)

The Firefox bug is annoying beacuse it was discovered during development. :---)

Also all trouble with 3D drivers and Jockey.

Mostly all of them are available as proposed fixes... just to get them.

:)


(I tested Intrepid but it ended in a total breakage....):P  )

---

### Post by Saint Angeles on 2008-05-05
> **exploder said:**
> My idea is to finish a release, Hardy to be specific.

The floppy drive issue was not resolved before Hardy went final.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954)

Usplash problem.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

Leaving these kind of bugs in a final release is why Linux has the smaller user base, even that other OS would not make a public release with such obvious bugs left unfixed.

Certainly no one can fix everything but these bugs show a lack of quality control and should not just be forgotten about.

So, my idea is to actually finish work that was started. The distribution could go a lot further and gain a larger user base.
nobody is stopping you from trying to help. why don't you get those bugs fixed and then they can be added to hardy.

you dont seem to realize that ubuntu is free as a courtesy to you. if you have such a beef with it, move on or help with the bugs. then you can back up all your important data to your archaic floppies and the rest of us will stick to external USB drives and CD-ROMs.

---

### Post by Gina on 2008-05-05
I'm looking forward to getting my hands on Intrepid :)  Roll on Alpha 1 :lolflag:

---

### Post by plun on 2008-05-05
> **Gina said:**
> I'm looking forward to getting my hands on Intrepid :)  Roll on Alpha 1 :lolflag:

Well, start with Hardy...

**Menu System > Administration > Software Sources  > Tab Update**

check "Pre-release updates, Hardy proposed".

Back in testing again....:)

A new kernel and Firefox (Xulrunner) fixed.

and more according to earlier URL.

---

### Post by Gina on 2008-05-06
OK :)  Thank you - I'll give that a go on my test desktop :):)  Main desktop stays with more stable version for the present.

---

### Post by Gina on 2008-05-06
OK...  Updates installed on old desktop, rebooted and all seems fine so far :)  Firefox, wireless, audio etc.  Now listening to music from NAS drive over wireless network :)

---

### Post by plun on 2008-05-06
> **Gina said:**
> OK...  Updates installed on old desktop, rebooted and all seems fine so far :)  Firefox, wireless, audio etc.  Now listening to music from NAS drive over wireless network :)

Yup, I have them running on 2 PCs...

Also helped others within my country with trouble, I don't know
how Ubuntu has figured out howto test this...:confused:

Everyone asks when and why those fixes aren't out. 

"Finish what was started"....  name of the thread.

:)

---

### Post by exploder on 2008-05-06
I see updates coming regularly now. Maybe my idea is more popular than I thought!

At least I have some hope!

---

### Post by exploder on 2008-05-06
I discovered after installing all of the available updates today 05/06/08, the Network Manager errors on shut down and re-boot are gone! I re-booted the pc several times with good results!

I hope this is the end of that problem and it's great to see things getting fixed!

---

### Post by olskar on 2008-05-08
I still have the problems :(

---

### Post by GavinZac on 2008-05-08
exploder, don't use the "Thanks" button when someone agrees with you. Thats not what its for.

If the most serious problems are some floppy errors and a couple of extrenuous lines of text on shut down, it would be a heck of a release.

---

### Post by 23meg on 2008-05-08
There's an insane amount of work being done to "finish what was started", in the sense that the the OP means. A brief look at my bug mail shows proposed or already rolled out fixes for the following serious issues in the last few days:

[list]
[*] Firefox slowdown and CPU spike issue
[*] virt-manager unable to utilize CD-ROM drive
[*] gnome-system-monitor CPU spike issue
[*] kernel scheduler problems (CONFIG_FAIR_CGROUP_SCHED)
[/list]

That your particular issue hasn't been fixed doesn't mean issues aren't being fixed all over the place, and as usual, the "People are using Windows because $MYPETBUG isn't being fixed" line doesn't make statistical sense. As a non-technical user, you can help "finish what was started" by testing the existing proposed updates and the upcoming ones.

---

### Post by exploder on 2008-05-08
23meg, yes I have seen a great deal of progress lately.I also have the proposed updates installed.

This is not what I said.

"People are using Windows because $MYPETBUG isn't being fixed"

I did say that corporate IT where I worked looked at Ubuntu and stated that it was too buggy at this time and they would be staying with Windows XP.

I understand that it is nearly impossible to fix every single bug, The bugs I mention in my original post are in my opinion extremely obvious to someone looking seriously at the operating system for deployment.

I personally want to see the operating system gain corporate acceptance and be deployed on a large scale. I have submitted bug reports and supplied all of the required information when asked to do so. My original post is not an attempt to knock Hardy or the Developer's. I want to see Hardy meet it's goal!

The $MYPETBUG isn't being fixed phrase seems to be a standard answer for things that do not work. 

My idea is still the same as I originally presented it. I feel that if the obvious bugs are fixed before moving on to the next release the LTS release would gain acceptance in the corporate environment.

---

### Post by 23meg on 2008-05-08
[QUOTE=exploder]This is not what I said.

"People are using Windows because $MYPETBUG isn't being fixed"[/QUOTE]

You said:

[QUOTE=exploder]These types of bugs not being fixed is why Microsoft's product is on most PC's.[/QUOTE]

That's simply not true. The reason Microsoft's product is on most PCs is not the technical incompetence of Ubuntu or GNU/Linux. 

[QUOTE=exploder]I understand that it is nearly impossible to fix every single bug, The bugs I mention in my original post are in my opinion extremely obvious to someone looking seriously at the operating system for deployment.

I personally want to see the operating system gain corporate acceptance and be deployed on a large scale. I have submitted bug reports and supplied all of the required information when asked to do so. My original post is not an attempt to knock Hardy or the Developer's. I want to see Hardy meet it's goal!

The $MYPETBUG isn't being fixed phrase seems to be a standard answer for things that do not work.

My idea is still the same as I originally presented it. I feel that if the obvious bugs are fixed before moving on to the next release the LTS release would gain acceptance in the corporate environment.[/QUOTE]

What I don't quite get is your presenting what's already being done and what's standard procedure as an "idea", as if it were a thing that isn't being done, but should be done. Publishing post-release updates for existing bugs is standard procedure, with clearly defined criteria. If you aren't happy with the rate at which this is happening, which would be understandable, the best you can do is contribute at a greater rate than you already are, and/or encourage / help / hire others to do so. Saying "Hey, I have a great idea: why don't we fix the existing bugs in this release?" will just give you blank stares from the people who are already doing that full speed.

---

### Post by exploder on 2008-05-08
What I am referring to are bugs like the gnome-settings-daemon error in the last two release.The bug was never fixed in Feisty and Gutsy and they are still supported releases. (There is a work around for the problem.) The bug is fixed in Hardy.

Perhaps I not able to convey what I would like to see or express what I am thinking well enough.

I am not implying technical incompetence on anyone's part. The goal of the Hardy release was to be an enterprise class system and to be profitable. I am expressing a corporate point of view, not a developer or hobbiest point of view.

I worked for a very large corporation with thousands of pc's. I was responsible for over 300 machines at one site. I know exactly how software is looked at and what is looked at. I am also aware of corporate spending, the site I worked at had an IT budget of 6.5 million.

I am involved with bug reporting with Ubuntu because I want to see it reach it's goals. I would not dedicate so much of my time to a project that could not reach it's goals. Hardy can be an enterprise solution and can be very profitable if a few rough edges are worked out.

I will continue doing my part to see that the goals are met.

---

### Post by ibanez on 2008-05-09
> **exploder said:**
> I see updates coming regularly now. Maybe my idea is more popular than I thought!

At least I have some hope!


Haha good luck my friend :D ...   I run one 3d intensive game on both hardy and gutsy ..   On hardy I crash in minutes . on gutsy I run for hours sometimes 24 plus....  but the BNB will tell you its a hardware problem?? I'm truly pleased that you are seeing the updates that have a chance of fixing your distro, maybe when July comes everyones Hardy will work well, but for now at least for me its unusable in a heavy 3d open GL workspace, although I must give the devs credit , If I stay away from my "game" I can run in hardy , Its easy enough to boot to gutsy and play anyway, So for now 3D modeling and any type of heavy gameplay is Gutsy only for me, I can live with that as the eye candy that has been introduced makes heron a viable "future " alternative.... 
I still cant for the life of me though understand why a beta firefox was introduced into a LTS release , but what do I know the devs are all knowing and they know whats best for us ;-)
Things are working better since the latest updates though, & I don't feel such a need to desert/migrate,  although the BNB are still just that . !! 
Not diehards at all ...
I've been with Ubuntu since its conception, and it pains me to see this forum digress from the once helpful place it was to its current sad stereotypical of other Linux forums state, A minority granted but still it hurts the community. 
But hey .. this is typical Linux mentality sad but true...... My thoughts and views on the install process still stand though, of ALL the machines I installed Heron on ALL had issues,   surmountable in retrospect , but still issues. It really does amaze me ( maybe Aghast me is a better word) that some still claim ... I installed it on 10 -20 -15  machines and not one had a problem ... hmmmm .  personally I think rubbish. but since theres no way of them or me proving either way I'll just have to take their word albeit with a pinch of salt. 
But hey its kinda working good atm so I'll wait with anticipation and see what July brings. 
Peace.

---

### Post by exploder on 2008-05-09
This exert taken from the bug report "Usplash without progress bar on shut down", best illustrates where my concerns are.

I've done all of the updates to Hardy and I can't report the positive
outcome that you have.  This bug seems rather elusive but not uncommon.
I've read multiple threads on ubuntuforums.org which report the same
issue.

There's a bunch of people that I would like to upgrade to Hardy but I
simply can't because I will get numerous calls about their system being
"broken" if they see this crap every time they shutdown their computer.

Even if there was a workaround, I could live with that.  But I've tried
a few proposed methods to eradicate this issue and nothing has helped.


I have no problem with a beta version of Firefox in Hardy. I totally agree with the reasoning behind this decision. My concerns are mainly the Network Manager errors on shut down and re-start. 

I am sure this is being addressed and hopefully there will be a permanent solution for the problem. I know that the problem is apparently coming from GDM. I saw the exact same problem showing up in Fedora 9, (Not near as bad or as consistent.), the problem was resolved from an update to GDM. 

I appreciate the efforts of the Ubuntu Development Team and I can see that bugs are getting resolved.

---

### Post by Redrazor39 on 2008-05-09
> **exploder said:**
> Very well put, ibanez. I have seen reviews calling Hardy a beta.The last of three machines I had Hardy on now has the screen full of Network Manager errors.

Ubuntu is selling support, how can you sell support for something that does not work right in the first place?

Feisty and Gutsy have the gnome-setting-daemon error that was never fixed. I do not want to see a LTS release left in this shape and it really makes the distribution look bad. Should user's just expect bugs to be present and never resolved? Each release seems to have more bugs than the previous release.
[B]
Wouldn't it be nice to see Ubuntu associated with quality? It is time to finish what was started, Attention to quality as well as innovation will enable Ubuntu to reach it's goals.[/B]
PERFECT! RIGHT THERE IN BOLD IS WHAT I"VE WANTED TO TELL EVERYONE HERE FOR SO LONG!!!!!!!!!!!!!!!!!!!



I'm so excited that people understand this pefectly! We need to have some sort of quality standards or something. Ubuntu looks like a tester dev's dream almost, but not for the end user at all.

It's good that these bugs can be fixed with the easy bug reporting feature in launchpad, BUT obvious bugs like the ones in the first post HAVE to be fixed. It's these little things that people count as quality and polish. You have to look at what most end users see as quality and polish, and that's it. 

Bill Gates (yes, I know) once said "If you can't make it good, at least make it look good," and MS has demonstrated this for almost a decade now. It's time for Linux-- meaning Ubuntu in this case-- to make it both. Rock solid, full of features, and polished to a mirrored shine. 

All these obvious bugs need to be fixed, but smaller, more minor bugs should be the only ones that actually NEED reporting and fixing. Those could remain in a final release, but major showstoppers like the ones I've read about in hardy (and seen in the live CD) should've been fixed a LONG time ago. Even these look and feel "polish" bugs need to be fixed before a final release. Set the bug priorities like this:

[LIST=1]
[*]Major showstoppers that cause crashes or stop important things from working correctly
[*]"Polish" look and feel bugs that make ubuntu look cheap or "unfinished" to newbish end-users if left unfixed
[*]Minor bugs that only affect a small number of users (these can be discovered and reported by the users and fixed by updates and then the first point release could fix pretty much all of them. Make it so people who are early adopters are encouraged A LOT to report bugs-- even really tiny ones-- that they find.)
[/LIST]

---

### Post by k99goran on 2008-05-09
> **exploder said:**
> My idea is to finish a release, Hardy to be specific.

The floppy drive issue was not resolved before Hardy went final.

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197954)

Usplash problem.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/216266)

Leaving these kind of bugs in a final release is why Linux has the smaller user base
I don't think they've forgotten about the floppy drive issue, or any other remaining bugs.

---

### Post by High Roller on 2008-05-12
> **exploder said:**
> This exert taken from the bug report "Usplash without progress bar on shut down", best illustrates where my concerns are.

I've done all of the updates to Hardy and I can't report the positive
outcome that you have.  This bug seems rather elusive but not uncommon.
I've read multiple threads on ubuntuforums.org which report the same
issue.

There's a bunch of people that I would like to upgrade to Hardy but I
simply can't because I will get numerous calls about their system being
"broken" if they see this crap every time they shutdown their computer.

Even if there was a workaround, I could live with that.  But I've tried
a few proposed methods to eradicate this issue and nothing has helped.


I have no problem with a beta version of Firefox in Hardy. I totally agree with the reasoning behind this decision. My concerns are mainly the Network Manager errors on shut down and re-start. 

I am sure this is being addressed and hopefully there will be a permanent solution for the problem. I know that the problem is apparently coming from GDM. I saw the exact same problem showing up in Fedora 9, (Not near as bad or as consistent.), the problem was resolved from an update to GDM. 

I appreciate the efforts of the Ubuntu Development Team and I can see that bugs are getting resolved.

I've found a workaround [here]("http://ubuntuforums.org/showpost.php?p=4934956&postcount=10").
It appears this problem is indeed related to GDM.  This is an
odd way to fix the problem but it worked for me!

Let me know how well this worked out for you.  Also, I hope this now isolates the issue for those investigating.

---

### Post by Gina on 2008-05-12
Login Window took ages to appear - thought it wasn't going to...  cut, saved, pasted back and saved the text for shutdown and restart.  Worked for restart but not shutdown.  Will try again.

---

### Post by High Roller on 2008-05-12
> **Gina said:**
> Login Window took ages to appear - thought it wasn't going to...  cut, saved, pasted back and saved the text for shutdown and restart.  Worked for restart but not shutdown.  Will try again.

It should be noted that the computer will likely need to be rebooted once before you see the changes take effect.  This has been my experience.  I'm sure results may vary :)

---

