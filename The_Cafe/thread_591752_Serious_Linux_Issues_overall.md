---
title: "Serious Linux Issues overall"
date: 2007-10-25
forum: The Cafe
---

### Post by old_salt on 2007-10-25
Folks - we have a serious dilemma going on right now.

Based on countless hours of research since the release of E/K/U/Xbuntu release, we have a problem. It's a problem not with Canonical or the release of Gutsy; it's a serious problem for Linux and the community as a whole.

My research has led to the discovery of a SERIOUS kernel problem. An issue that dates back to the 2.6.15 release that slipped through the cracks so to speak. This currently spans 4 major distributions with commercial impact and affects the Linux community as a whole. While kernel developers are earnestly troubleshooting the issue, things aren't looking good. 

As everyone knows, Linux has fought tooth and nail for justification as a valid competing Operating System that can be used for both home and commercial use. While we were at the dawn of our emergence with backing from major global vendors such as IBM and DELL, it appears that a bug or mistake if you will has managed to cripple and jeopardize the hard work we have all put forth. 

Ubuntu 7.10 Gutsy release will be dubbed the biggest failure ever because of this. Timing is everything despite the monumental achievements this release has achieved. Even worse is the emerging acceptance of SUSE in the Enterprise and how this negligence will impact corporate acceptance and the embarrassment these vendors are having to deal with because of it. I'm confident we will lose considerable ground and credibility because of our efforts and claims of better code, performance, usability and bashing. 

While there's no need to add pressure to the kernel developers who are working diligently, the various distro's affected etc; I believe NOW is the time for the community as a whole to rally together regardless of flavor and current obligations to provide whatever assistance possible in efforts to expedite the resolution/remediation of this grave mistake while showing the world our resolve to quality and our claims to support and unity. 

The release of Gutsy and all distro's that updated to the 2.6.15 kernel release are overflowing with issues and so-called workarounds. Problem is; a kernel issue cannot be patched, worked around nor neglected and ignored. This issue must be expedited to the highest level from all angles in efforts to bring an acceptable solution or else the community as a whole will take a step back that may take several years or more to overcome - remember AMD ?

I challenge EVERYONE who has a sincere appreciation and desire to see to the success of Linux as a whole to support and encourage the remediation efforts of those involved and the mitigation of the impact from this from spreading out of control. 

One simple mistake, see where it's got us? We need patience, temperance and attention to detail! we need to put marketing back in it's place once and for all and get back to basics and do the right thing that we all know how to do and let the cards fall. 

Sincerely..........

---

### Post by hikaricore on 2007-10-25
Hi ummm... This is not the place to rant mmkay?
I didn't see anywhere where you mentioned an actual issue, you just kept referring to one and never clarified it...

Moved to General Discussion. (aka Community Cafe)

---

### Post by -grubby on 2007-10-25
what issue?

---

### Post by vambo on 2007-10-25
Bug report ? :confused:

---

### Post by osxcapades on 2007-10-25
old_salt, your post is missing something. Like the actual issue in question. At the moment I'm not going to rule out the possibility that you are just trolling, and that we shouldn't take you seriously.

**Edit:** See old_salt's post below. I overreacted in this post. I apologize.

---

### Post by old_salt on 2007-10-25
there are bug reports regarding this which were spurred from the countless issues regarding diminished hardware such as
- Hi - hi % -  processing utilization reports
- No USB
- Intermittent Firewire
- ntermittent Wireless (all brands)
- Diminished nVidia Video capabilities
- Lack of Resume,, suspend, Hibernate
- thermal shutdowns of newer laptops with multi-core processors both AMD and Intel.....

of which the results are common as reported  across FC7, Suse, Ubuntu. When analysis was reviewed, a kernel backtrack was initiated and they have found that the new EHCI and several other new hardware inclusions into the kernel beginning with 2.6.15 appears to be the culprit however further analysis is being conducted by kernel developers before a public announcement of the determination is made.

I'm sorry if this appears to rain on your parade however thousands of others have encountered serious issues according to the posts and bugtrack. I can't see how you've not seen it. I've never encountered such serious issues from any previous new distro version release as I have with 7.10. Not saying this is the culprit..... My 5 mo old HP DV9000z laptop is non-functional with this version while I had no issues with 7,04. Something isn't right here. Check the HP Laptop postings in this forum.

Reports from Bugtrack (about 2 different #'s) includes messages from all distro users who upgraded to or newer than 2.6.15 kernel (which spurred the backtrack) and when booting to the pre 2.6.15 version have no issues. Sabayon which uses the 2.6.23 kernel mentions similar issues as we\l while several posters who are running Gentoo and Debian have no issues and can't seem to understand what the problem is either. 

Before just discrediting an IT person with 20 yr experience, please take some time to investigate for yourself before sending a flame within minutes of my initial posting. As posted - I've spend counteless hours reading, tracking, cross referencing postings) It shows you haven't done your homework to substantiate your counter-remarks.  While you might not be having issues doesn't mean the rest of the world isn't.

I was very nice, neutral and cordial in my message and the content and intent demeans nobody, please refrain from your emotional rants just because you don't understand or haven't encountered the same issues or understand the angle I'm coming from please. I as well as many of you strive for the same goals so don't start some internal feuding.

Sincerely.....

---

### Post by Het Irv on 2007-10-25
Hmm... With 7.10
Wirless- much improved I have not had any problems yet and I have a WMP54GS (very hard  to get to work in Fiesty)
USB- Umm.. I have not had any problems with that so far

I have no personal experience with the rest of your list, so for all I know you could be right there.

---

### Post by old_salt on 2007-10-25
Look, all I'm asking here is for some help investigating on the same angle. If this is a substantiated or valid point, we all need to help wherever as it wouldn't take but a few days of bad publicity to set the entire community back years of hard work and effort. Don't think Microcrap wouldn't seize the opportunity either. We are on the dawn of breaking a monopoly here. I can't put into words what a lot of us feel about that.

---

### Post by old_salt on 2007-10-25
> **Het Irv said:**
> Hmm... With 7.10
Wirless- much improved I have not had any problems yet and I have a WMP54GS (very hard  to get to work in Fiesty)
USB- Umm.. I have not had any problems with that so far

I have no personal experience with the rest of your list, so for all I know you could be right there.

Yes wireless install was much improved however.... it works intermittently. Yes it took a few minutes to setup ndiswrapper but it was stable. USB comes and goes. plug in once- it works. remove and reconnect and nothing. reboot and still nothing. how about keyboards or Laptops that get so hot you can't touch them? How about unexplained runaway processes causing excessive CPU utilization? h.i. % for me averages 39%. Various boot options such as noapic - acpi_irq_balance - nosmp - nolapic, noirqdebug; nothing works and if it does, it's only temporary. The forum is bursting with way too many people making such claims to even think this isn't a serious issue.

---

### Post by some_random_noob on 2007-10-25
I think that old_salt has some points. I know nothing about this kind of stuff, but it sure seems odd that I get 37% CPU-usage when doing absolutely nothing except having an open browser while running "System Monitor" in the background. Then when I load a page in Firefox the CPU-usage jumps to 100%. Weird. Is this just because I have an Intel Celeron, or is this because Linux is screwing up on me? I'm also using 256MB of RAM while idle :confused: Scary!

---

### Post by manu456 on 2007-10-26
I second old_salt. I have been using ubuntu since breezy badger days and of late I have been wasting far too much time getting my system to be stable.

I have recently bought one of those dreaded HP laptops and I can't keep it stable with Gutsy over long periods of time no matter what I try. CPU, wireless, USB, audio I've faced problems with all of these.

If there is a problem how can we as a community help? I am going to try and install a versino of gentoo or debian with an older kernel on the same machine and post my results if that helps.

---

### Post by wolfen69 on 2007-10-26
old salt: -[B] Hi - hi % - processing utilization reports
- No USB
- Intermittent Firewire
- ntermittent Wireless (all brands)
- Diminished nVidia Video capabilities
- Lack of Resume,, suspend, Hibernate
- thermal shutdowns of newer laptops with multi-core processors both AMD and Intel.....[/B]

sounds familiar to vistas release......FUD

---

### Post by wolfen69 on 2007-10-26
my computer runs perfect. we as a group need to realize that it may never be perfect as a whole. but it can, and will be better than "other OS's". im a fairly demanding user, and for the most part, ubuntu does everything i ask it to. without the overhead. priceless. i would literally quit using computers if i was forced to use windows.

---

### Post by Polygon on 2007-10-26
all of those issues depend on the type of hardware you have, and whether there are correct drivers for them, whether they are open source and stuff

i have never heard any problems with thermal shutdown, mostly becuase the CPU is one of the better supported pieces of hardware in linux, cause intel and amd both provide good documentation and stuff

wireless - depends on the chipset. Im  using my atheros chipset wireless card flawlessly

suspend/hibernate - depends on a lot of things. for example, with fglrx installed, suspend/hibernate dont work for me...but if i use the open source ati driver,...then it does.

diminished video capabilities - comes from the fact that nvidia and ati spend more time on their windows drivers cause thats where like 98% of there business comes from.

firewire works fine for me

no usb? what are you talking about....usb has like been supported ever since it came out.

---

### Post by perce on 2007-10-26
Old_salt, I agree with you that there are far too many stability issues for an OS that markets itself as the stable OS. But why do you think there is THE bug behind it which is going to make everything collapse, instead of many small bugs introduced by a too fast development?

---

### Post by BigSilly on 2007-10-26
Hmmm. Something smells fishy here methinks. If there's a serious bug problem, why tell the forums? Why not contact the developers with your evidence? The OP certainly sounds like he's confident there is clear proof of an issue.

Something's not right about this discussion, and I know nothing of coding. With all due respect, both the OP's posts say everything and nothing. He could be talking about Vista for sure, but not any Linux, regardless of people's individual problems setting things up.

---

### Post by FuturePilot on 2007-10-26
> **Polygon said:**
> all of those issues depend on the type of hardware you have, and whether there are correct drivers for them, whether they are open source and stuff

i have never heard any problems with thermal shutdown, mostly becuase the CPU is one of the better supported pieces of hardware in linux, cause intel and amd both provide good documentation and stuff

wireless - depends on the chipset. Im  using my atheros chipset wireless card flawlessly

suspend/hibernate - depends on a lot of things. for example, with fglrx installed, suspend/hibernate dont work for me...but if i use the open source ati driver,...then it does.

diminished video capabilities - comes from the fact that nvidia and ati spend more time on their windows drivers cause thats where like 98% of there business comes from.

firewire works fine for me

no usb? what are you talking about....usb has like been supported ever since it came out.
I was thinking along these lines.

---

### Post by popch on 2007-10-26
I agree with quite a few members here that the OP (original post) is short on factual data. Issues are referred to but not named. Without naming the problems we can not see if they are show stoppers ore merely minor annoyances.

After the issues have been named, I can say that none of these appear to have had any influence on my own individual computing experience, although I am using two different 'infamous' laptops by hp. Of course I can accept that others are less happy than I am.

The point of the OP was not in itself that the kernel has some issues, but rather that this fact was damaging to the image and thus to the further spread of linux.

It takes a bit more than a list of issues to assess whether there is or is not any damage done. I point out that besides AMD and Linux there are also Intel, hp, Microsoft, DELL and so on who have quality issues and outright bugs on a regular basis. I don't think that anyone in this thread actually believes that those four are particularly absent from today's market on account of those shortcomings, even when they handled some of those issues really poorly.

---

### Post by manu456 on 2007-10-26
> **BigSilly said:**
> Hmmm. Something smells fishy here methinks. If there's a serious bug problem, why tell the forums? Why not contact the developers with your evidence? The OP certainly sounds like he's confident there is clear proof of an issue.

I agree with this thought that the original poster has not given any evidence or details about the 'serious issue' that he mentions.

I also agree that there are some stability issues around with rapid releases and fast paced development and in my personal experience I have found fesity to be less stable than edgy and gutsy less stable than feisty even on hardware that it is supposed to be compatible with(that's my opinion solely). But are these intermittent issues serious enough to threaten linux as a whole is highly doubtful.

---

### Post by old_salt on 2007-10-26
I think I must be talking to a bunch of attorneys here. The discrediting, blaming and lack of initiative of some.... 

My dekstop AMD 64bit clone has no isues with Gutsy. My TOP output is the best I've ever seen averaging 0.x%'s across the board at idle. I run Mythtv, edit video etc and no issues. 

My HP DV9000 laptop is another story - this model has been on the market over 1 year. After 2 full releases of just about every distro, I among thousands can't understand why it requires special kernel boot parameters to run a live CD, perform an install or even boot up the system. Appended kernel parameters are for troubleshooting only!!!!

I ran across the kernel bug report after a full day of following links in several postings. I don't remember the ID#, the link or anything. I obtained the info I needed and this posting was an afterthought. I do subscribe to the IVTV mail list and there's even mention about some kernel issues there. Hans does a good job summarizing kernel news to the list when needed. Especially when the IVTV tree is to be folded into the kernel on the 2.6.24 release. 

I'm only trying to raise awareness in efforts to muster assistance in properly identifying or collaborating the info I have learned. 

DELL PC's lack the wholescale issues that HP does when they suddenly came aboard after years of flaming the Open Source comunity. HP & IBM has always supported us, and has marketed Linux and Unix systems for as long as I can remember. 

To give you an example of I among many encounter on an HP 6000 - 9000 series laptop;

I used my laptop at work wired to the network and got everythng working except USB. I come home, no wired, no wireless or USB. Reboot and USB worked for 1 plugin and quit, still no wired or wireless. Reboot again and no USB, Wireless initialized but wouldn't connect and then dissapeared completely. Reboot and wireless and bluetooth are completely gone, non-initialized, no USB & no networking. Every reboot results in a complete change of working and non-working hardware. 

Thing is I'm not alone. Feisty has no issues. What happened here? Before you say go back to Feisty and other remarks about hardware limitation in support.... I am reverting to Feisty. HP support? They were selling *nix systems before Canonical and even RedHat came around. 

For the last time, I'm only asking for some assistance in looking into kernel bugs is all. If you don't want to help, then fine, but don't just discredit me or my claims because you have no issues or aren't running the same hardware I am. It's not what the community is about and most certainly not in keeping with the Ubuntu philosophy.

---

### Post by tehet on 2007-10-26
> **old_salt said:**
> For the last time, I'm only asking for some assistance in looking into kernel bugs is all.
That's kind of impossible if you fail to produce specifics time and again.

---

### Post by old_salt on 2007-10-26
> **manu456 said:**
> I second old_salt. I have been using ubuntu since breezy badger days and of late I have been wasting far too much time getting my system to be stable.

I have recently bought one of those dreaded HP laptops and I can't keep it stable with Gutsy over long periods of time no matter what I try. CPU, wireless, USB, audio I've faced problems with all of these.

If there is a problem how can we as a community help? I am going to try and install a versino of gentoo or debian with an older kernel on the same machine and post my results if that helps.

You are hitting the nail on the head here. I would be curious to your results. Please let me know as I may have to go the same route. The laptop model we have is awesome. I picked the model because the entire system is nVidia based which has had great success with Linux. Feisty had only the noapic option and a manual wireless install. Everything else worked fine.

---

### Post by sdowney717 on 2007-10-26
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72775)

here is an old overheating bug with a workaround. Polling frequency was set to off, so of course the fan never came on.

Question is how are laptops doing now regarding fans overheating bug in feisty and gutsy?
of course something like this would be a linux adoption killer. who would want their laptop to fry.

---

### Post by Mr. Scott on 2007-10-26
I have been using Ubuntu since the time of 6.10, and have never had any issues on my particular set-up. However, I am making the switch to Gutsy soon, and if I do start having problems, I'll do the necessary diagnostics/investigation and make sure that info gets where it needs to.

---

### Post by sdowney717 on 2007-10-26
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85894](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85894)

gutsy gets mentioned as still having overheat issue. One guy claims his hardware was destroyed.

---

### Post by old_salt on 2007-10-26
It's obvious here that all anyone wants to do is ignore the obvious and just celebrate a new release is all. Discredit the one person trying to call attention to what could be a big issue. "Silence the insubordinate"!!!

I've mentioned specifics, I've mentioned a kernel bug tracker (not Ubuntu) does exist (minus the # of course - sorry) and there's tons of postings throughout this forum and the Kubuntu Forums that substantiate and corroborate the issues on the HP laptops I mention. There is an entire model line (HP Pavilion) spanning multiple variants (Dv6000 series, Dv9000 series both Intel and AMD - 32bit and 64bit) that have serious hardware issues which should not be occuring. You realize how many people that is? I and many others submitted our systems to the Ubuntu HW Database in efforts to contribute and help development on this platform. It appears Cononical is only concerned with holding Dell's hand right now. 

I can't believe someone with more experience dealing with the bug track system hasn't performed a quick search? I guess eveyone just wants to bask in the celebration. 

I'll just find another distro that works and pass along my findings to as many HP Laptop users I can. I appreciate those who responded with an open mind and I wish you all the best. 



You may freeze or close this thread moderator.

---

### Post by n3tfury on 2007-10-26
> **hikaricore said:**
> Hi ummm... This is not the place to rant mmkay?


as a moderator, i think you could have said it a little less idiotic.

---

### Post by sdowney717 on 2007-10-26
i was thinking why does not the bios control the fan cooling. like when the CPU temp goes up, fan cools it down. Why would the OS even need to be involved here.
let this be controlled independently of the OS or whatever program is running.

---

### Post by DoctorMO on 2007-10-26
[SIZE="4"]**[COLOR="Red"]PANIC, PANIC, ALL HANDS TO THE PUMPS![/COLOR]**[/SIZE]

Look old_salt you've reported your findings in a *very* bad way; instead of reporting your findings in a non-emotive and professional fashion you've done the above. Scare mongering even with a valid reason is still scare mongering and I'd thank you not to do it.

Yes there may well be problems.
Yes, the ubuntu teams may need to re-prioritise stability
Yes, the kernel hackers may need to do more bug fixing.

But seriously, calm down before you hurt someone.

---

### Post by skillllllz on 2007-10-26
FWIW, I've found through my own experience that many HP laptops of the Pavilion model lineup have major BIOS bugs which cause most, if not all of the problems you mention.

I'm not saying that means there isn't a possibility of serious flaws in the kernel, as you claim. I just think it's possible that you are misinterpreting the cause of these problems.

---

### Post by Polygon on 2007-10-26
so if your laptop is having problems (laptops tend to have more problems since everything is just one big chipset rather then individual parts like a desktop computer) then that doesnt mean noone can use usb....doesnt mean that all cpu's overheat and die. there is an unlimited amount of hardware combinations out there and supporting them, especially when the vast majority of hardware manufacturers dont supply drivers is a pretty serious undertaking. Even microsoft doesnt do this, they use drivers that companies supply them with.

---

### Post by vambo on 2007-10-26
This might be of interest in relation to this thread [http://news.softpedia.com/news/Linux-Kernel-2-6-24-RC1-Released-69088.shtml]("http://news.softpedia.com/news/Linux-Kernel-2-6-24-RC1-Released-69088.shtml")
The interesting thing that struck me was the size of the change set.
Not sure how easy or other wise it would be to try and use this as a "Gutsy" kernel for testing. On a personal note, I don't have any issues with my install, so I'm not sure what I could investigate with no bugs apparent!

---

### Post by Toffeeapple on 2007-10-26
I'm new to linux, just three weeks and my only 'issues' are with Creative and ATI : ) both of which I have now dumped... along with XP and Vista.. but then I know squot about coding and stuff...

just a happy end user: )

---

### Post by skillllllz on 2007-10-26
I find that for most HP laptops the following kernel boot options are imperative for a stable/functional system:

```
noapic noirqdebug
```
noapic seems to work around the bugs in the BIOS, while noirqdebug restores USB functionality.

---

### Post by vexorian on 2007-10-26
> **old_salt said:**
> there are bug reports regarding this which were spurred from the countless issues regarding diminished hardware such as
- Hi - hi % -  processing utilization reports
- No USB
- Intermittent Firewire
- ntermittent Wireless (all brands)
- Diminished nVidia Video capabilities
- Lack of Resume,, suspend, Hibernate
- thermal shutdowns of newer laptops with multi-core processors both AMD and Intel.....

of which the results are common as reported  across FC7, Suse, Ubuntu. When analysis was reviewed, a kernel backtrack was initiated and they have found that the new EHCI and several other new hardware inclusions into the kernel beginning with 2.6.15 appears to be the culprit however further analysis is being conducted by kernel developers before a public announcement of the determination is made.

I'm sorry if this appears to rain on your parade however thousands of others have encountered serious issues according to the posts and bugtrack. I can't see how you've not seen it. I've never encountered such serious issues from any previous new distro version release as I have with 7.10. Not saying this is the culprit..... My 5 mo old HP DV9000z laptop is non-functional with this version while I had no issues with 7,04. Something isn't right here. Check the HP Laptop postings in this forum.

Reports from Bugtrack (about 2 different #'s) includes messages from all distro users who upgraded to or newer than 2.6.15 kernel (which spurred the backtrack) and when booting to the pre 2.6.15 version have no issues. Sabayon which uses the 2.6.23 kernel mentions similar issues as we\l while several posters who are running Gentoo and Debian have no issues and can't seem to understand what the problem is either. 

Before just discrediting an IT person with 20 yr experience, please take some time to investigate for yourself before sending a flame within minutes of my initial posting. As posted - I've spend counteless hours reading, tracking, cross referencing postings) It shows you haven't done your homework to substantiate your counter-remarks.  While you might not be having issues doesn't mean the rest of the world isn't.

I was very nice, neutral and cordial in my message and the content and intent demeans nobody, please refrain from your emotional rants just because you don't understand or haven't encountered the same issues or understand the angle I'm coming from please. I as well as many of you strive for the same goals so don't start some internal feuding.

Sincerely.....

Look, I am not going to fight your 20 years of experience, the thing is that ever since i used Breezy Badger the kernel ALWAYS had a lot of issues and problems with hardware etc, so I wouldn't rush into being as fatalist as your posts are, it will cause a lot of users headaches but previous versions did so as well. 

And the problems you listed are nothing compared to the hard drive killing bug in the feisty kernel...

Yes, issues should be fixed, and knowing the Linux devs they would be fixed (And at the same time they are going to add other bugs and serious issues), if you don't mind I'll see this as a warning not to install ubuntu on HP computers, or in my case not to buy an HP computer.


> I think that old_salt has some points. I know nothing about this kind of stuff, but it sure seems odd that I get 37% CPU-usage when doing absolutely nothing except having an open browser while running "System Monitor" in the background

It's called Tracker desktop search, disable it, be happy. (Not the kernel screwing you around)

---

### Post by professor fate on 2007-10-26
This is an interesting thread.  Particularly since I'm new to Ubuntu (and Linux in general).  I don't know if any of you have been reading my thread: The bet is on! Microsoft vs Ubuntu.  But I would certainly consider myself an above average PC user (having built them for over 25 years and do some web dev on the side), yet in spite of that I'm having one hell of a time getting my sound card to work.  (Vostro 1400 laptop).  Other than that Gutsy has been pretty good.  

Based on my three days of experience, I can see how some of these problems would discourage new users.  I mean, if I wasn't in a bet with my friend (of which you can get the details on my thread), I likely would have said, "forget this".  Seriously, between my Google research and the many suggestions I received from people here, this stupid sound card is the stick in the mud.  This sort of frustration can weigh heavily on new users and turn them the other direction.  I will stick it out though because it's a condition of the bet.

---

### Post by blueturtl on 2007-10-26
So there is a big bug in the kernel that causes _video and usb and cooling and wireless as well as other things_ to fail? Now I'm not nearly qualified to make any assumptions about the the kernel structure or code, but how can one bug affect so many areas of the kernel's functioning?

Secondly,
I installed Gutsy on my wife's laptop and it has been the best release to date as far as hardware detection is concerned; video, audio, wireless, usb, and even the software modem - all detected and functional. Granted I didn't actually install the restricted drivers because the functions they provided are unnecessary, but to me it would seem hardware detection is working it's way up.

No device in our household has stopped working, on the contrary. Can you please elaborate on this bug, what it does, and who are supposed to be affected?

We don't do denial in the OSS world, if there is something wrong with Gutsy I want to know about it, and if possible help fix it.

---

### Post by old_salt on 2007-10-26
> **blueturtl said:**
> So there is a big bug in the kernel that causes _video and usb and cooling and wireless as well as other things_ to fail? Now I'm not nearly qualified to make any assumptions about the the kernel structure or code, but how can one bug affect so many areas of the kernel's functioning?

Secondly,
I installed Gutsy on my wife's laptop and it has been the best release to date as far as hardware detection is concerned; video, audio, wireless, usb, and even the software modem - all detected and functional. Granted I didn't actually install the restricted drivers because the functions they provided are unnecessary, but to me it would seem hardware detection is working it's way up.

No device in our household has stopped working, on the contrary. Can you please elaborate on this bug, what it does, and who are supposed to be affected?

We don't do denial in the OSS world, if there is something wrong with Gutsy I want to know about it, and if possible help fix it.


Detection of everything works great. HPDv9000z Laptop. AMD Turion64x2, 2Gb RAM, Matsushita Drive (Lightscribe), nVidia chipset, nVidia 6800 Video, Broadcom BCM4318 Wireless, Ricoh Smart card reader and webcam. Sound is no issue for me.

USB is intermittent - works once then stops, doesn't work after reboot, works a few times after reboot changing a kernel boot parameter (acpi_irq_balance) then quits. Wireless has suddenly dissapeared altogether. Bluetooth was working but has disappeared as well when wireless disappeared. No signal, no hardware recognition of the broadcom chip even being loaded. Webcam has never worked on Linux - no problem for me for now. TOP output is extremely high for the hi%. 

Let me know what else you would like to know please and I will do my best to get you the info.

---

### Post by xArv3nx on 2007-10-26
What goes around comes around.

---

### Post by TameLion on 2007-10-26
I think the issue which is perhaps confusing some people, including myself, is the logic behind the conclusion of 'a SERIOUS kernel problem' from your given predicates. You have one PC which you say is fully functional under Gutsy and an HP laptop which has lots of faults. As most of these posts have pointed out; we are not doubting your experience to come to your conclusion, only asking for the logical reasoning and evidence for "THE bug" (as opposed to several problems with several pieces of hardware which happen to all be in the same machine) which presumably you must be keeping to yourself?

---

### Post by old_salt on 2007-10-26
> **TameLion said:**
> I think the issue which is perhaps confusing some people, including myself, is the logic behind the conclusion of 'a SERIOUS kernel problem' from your given predicates. You have one PC which you say is fully functional under Gutsy and an HP laptop which has lots of faults. As most of these posts have pointed out; we are not doubting your experience to come to your conclusion, only asking for the logical reasoning and evidence for "THE bug" (as opposed to several problems with several pieces of hardware which happen to all be in the same machine) which presumably you must be keeping to yourself?

What's confusing to most here is they aren't using the same harware. The issues I mention are all over the HP Pavilion topics throughout this forum and everyone is drawing a blank. My research earlier this week led to a kernel bug report (my evidence sorta) Bug Track # that I didn't write down that I read through. My fault!

The kernel bug report indicated that some new experimental options with the new EHCI modules had been mistakenly set and after a backtrace through the kernel versions found these options had been mistakenly set with Kernel version 2.6.15 and has remained undetected till now. According to the postings, Gutsy released with the kernel version with these parameters mistakenly set which according to some is the cause for a lot of issues to HP Laptops and some others to include other distro's. One person tested Feisty on a HP Laptop using a pre-2.6.15 kernel release; ran perfectly but with the 2.6.15 kernel experienced the same issues reported as those who were installing Gutsy whether fresh or upgrade. 

I wished I could explain more.

---

### Post by Miguel on 2007-10-26
The thing is, from what old_salt is saying, one could assume that the kernel module of his mobo's chipset is faulty. That's what it seems to me, but I am a physicist, not a kernel hacker. And, although old_salt's first post really looked like trolling, launchpad bugs #129910 and #131094 are indeed kernel issues that **must** be resolved. In fact, I think that LP #131094 should be enough to delay a release. I don't care if vista also has issues, or that OS X performs awfully as an apache server. I don't really dive a d***. But I really hate to see bugs in the kernel I've learnt to love.

---

### Post by Bannor on 2007-10-26
look I don't know what the point of this is.  But for one linux has a number of advantages over microsoft and microsoft has one huge advantage.  Most of you complaints about linux stem from that one main issue. 

advantages

1.)I have found linux powermanagement to be far better than Vista.  My battery run at least 25% longer with Ubuntu.  I think this might be because of the new code in the kernal. But I am not that techniqual. 

2.) Linux plays better with older machines.  God forbid you want to use you perfectly good Pc with windows 98 installed,  Microsoft will no longer support you. and Vista is far too much of a hog to work.  Ubuntu Suse etc.  will make they machine run like it was a teenager again. 

3.) Utility.  today at work I was ask to make a soundtrack for a side project we are doing.   I have never done this before and dont' own any audio editing programs.  However one look into the Add remove section of the menu and I had all the equiptment I needed to do it.  With MS that would cost at least $30 for a good audio edititing program. 

Windows advantages.

1.) the big windows advantage is size.  It is the biggest player in the market.  All the compaints of this poster stem from that fact.   It seems like every time linux figures our nvidia something breaks.  well that is because nvidia keeps inovating and linux drivers are an after thought.  Wireless cards are never quite fully compatible same problem.  Can't find a top of the line game or enterprise level computer program. Why would a software company build a for linux?  

The future. who knows?  

In the begining of linux the choice for most causaul uses was obvious Windows.  Linux was too different from the normal experiencel  But as computers move to the realm where they provide more power than almost any use needs.  Linux will have a chance to catch up.  Already programs like ubuntu with the help of gnome are showing people the same utility as Microsoft and it does so with zero cost.  What will the industry do when people no longer demand a faster computer?

---

### Post by FuturePilot on 2007-10-26
Hmm. I have one of these so called "infamous" HP laptops. It's an HP Pavilion dv6500t and Gutsy fixed just about every problem I had with it in Feisty. In Feisty I need to boot with special kernel parameters so I would be able to mount CDs. I had problems with the Feisty live CD, sound and graphics issues. But with Gutsy it's like a 99% improvement. The live CD worked, didn't have any issues with graphics drivers, sound was easy to get working and no more needing to use special kernel parameters.

:confused:

---

### Post by Officer Dibble on 2007-10-26
I worked with the worlds third largest hardware/software reseller for many years and could tell you about various common faults across the spectrum of computers from various vendors.

HP has always struggled with its BIOS, the things we had to tell them and request of them were always about the BIOS.

We configured systems for numerous corporations and the biggest configuration and after sale issues always came from customers who wanted HP kit. They improved somewhat after swallowing up Compaq, but evidently not enough.

You advised us to sift through the forums to find bug reports and the commonalities with the matters you purport... what percentage of your stats account for user error or user inexperience? If you go to hospital what percentage of the people are going to be ill? Now then, what percentage of them were genetic illnesses and what percentage were self-inflicted by some means? The illnesses they have, were they caused because some food outlet was selling some half-cooked burgers - as you would find with Microsoft Vista?

The overall picture I have of Ubuntu is, and this isn't only because the amount of hard work put into it is given freely, but it is a comprehensive, reliable, and enjoyable operating system. It's an OS made with intelligence and passion... I love it. ;)

---

### Post by old_salt on 2007-10-26
> **Officer Dibble said:**
> ... what percentage of your stats account for user error or user inexperience? 

The overall picture I have of Ubuntu is, and this isn't only because the amount of hard work put into it is given freely, but it is a comprehensive, reliable, and enjoyable operating system. It's an OS made with intelligence and passion... I love it. ;)

Yes I see your point. However I've used Linux exclusively at home for over 4 yrs now (Fedora2 & up, Debian, Suse9 & up, Mandrake and Mandriva) and incorporated Red Hat in business environments including under VMware. I've been using Kubuntu exclusively for a year now at home because I share your last statement.

Fact still remains with everything I've posted to date. There's too much of a drastic change between a version. also you don't mention whether you have tested your USB, Firewire, SD Media reader or Webcam at all. Yes the Wireless was a cinch to setup this time however it's no longer working and there's actually no sign that it's even been installed or setup. Who knows what's to happen on next reboot, if it boots at all. This is the problem and I'm not alone.

---

### Post by hikaricore on 2007-10-26
I've setup 4 different versions of Ubuntu across at least 30 different systems ranging from laptops to servers to desktops and had relatively few troubles that weren't caused by chite hardware or something of the like.  You mentioned trouble with your nvidia card, I didn't see it asked but I didn't read every post... exactly what driver are you using for your video setup?  Atleast a couple of the problems you mentioned can be caused by a beast of this nature..

---

### Post by old_salt on 2007-10-26
> **hikaricore said:**
> I've setup 4 different versions of Ubuntu across at least 30 different systems ranging from laptops to servers to desktops and had relatively few troubles that weren't caused by chite hardware or something of the like.  You mentioned trouble with your nvidia card, I didn't see it asked but I didn't read every post... exactly what driver are you using for your video setup?  Atleast a couple of the problems you mentioned can be caused by a beast of this nature..

I'm using the restricted drivers because without it, the SD Reader, Bluetooth, Webcam and USB won't work but until I install the restricted driver however Wireless works without installing the restricted driver (Broadcom). The entire Laptop uses the nVidia chipset - Video, Reader, USB & Webcam (even though it's a Ricoh) and Bluetooth. The webcam still requires some firmware to be installed however I've not successfully tested with it installed but I'm not concerened about a webcam right now.

---

### Post by aysiu on 2007-10-26
> **Bannor said:**
> look I don't know what the point of this is. > **old_salt said:**
> You may freeze or close this thread moderator. I agree with both of these posts. I don't see the point of this thread, and (at the request of the OP), I'm closing this.

If there's a serious issue, file a bug report. If a bug report is already filed, starting a thread entitled *Serious Linux Issues overall* isn't going to get that bug fixed any faster.

As someone else said, this is just scaremongering. It is not productive. We'd all love to see bugs fixed but I have seen several pages written on this topic and little productivity.

---

