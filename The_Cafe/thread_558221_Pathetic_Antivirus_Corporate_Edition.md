---
title: "Pathetic Antivirus Corporate Edition"
date: 2007-09-23
forum: The Cafe
---

### Post by skillllllz on 2007-09-23
In an _experiment_, I spent the last week attempting to clean out a friend's badly infected Windows XP box. When I say badly infected, I mean horridly bad. It was literally a mind-blowing cornucopia of hundreds and hundreds of different Virii, Spyware, Malware, Dialers, Trojans and several different Rootkits. I'm totally amazed this thing even booted up (even though it took over a half hour to do so).

Initially, I figured it was infected with a virus or some type of Malware. So, I took the hard drive out and added it to another Windows box which I use specifically for scanning & removing crud like that. This other Windows box I use contains (among many other utilities) Symantec Antivirus Corporate Edition 10.2 (aka SAVCE), which is always updated and tweaked to catch and remove all that is known to be unholy (minus the sloppy OS I run it atop) or so I thought...

Immediately, SAVCE began to report several hundred infected files. When I saw how exorbitantly bad the infection was, I decided to pull out all the stops; I threw every utility I had in my arsenal at this to see what each could find. I ran McAfee, F-Secure, Spybot, Panda, HiJackThis, AdAware, ClamWin, to name a mere few...

Now, mind you, most of these utilities are gratis, but out of all the commercial products I own and use, SAVCE is the most expensive, and often touted as one of the best. It claims to find and remove not just Virii, but most of the other malicious junk I mentioned earlier. That is precisely why I and many others gladly paid for it.

Well, what took place when I used one of the other utilities, turned my stomach, but proved something I had always  suspected; it found numerous infections that SAVCE missed entirely. To be sure **I** wasn't missing something here, I left these infections alone and did not remove them; then before I moved on to try the next utility, I used SAVCE to see if it might somehow find these other infections. Each time it reported nothing.

At this point I decided that its entirely possible that these infections are so new that, somehow, some way, Symantec hadn't included them in the newest definitions yet. So, I waited a few days, updated to the latest and greatest definitions and tried yet again. Lo and behold... nothing! Absolutely nothing... not one new infection out of the handful each and every utility is additionally reporting.

At this point, I'm aggravated (and tired), yet I decided to wait another few days and try again. Yet again, same story... the other utilities are still finding all these other Rootkits, Dialers, and Virii.

How terribly sad; an expensive, commercial-grade, enterprise-level utility and this is as far as it takes its end-users? I know nothing is perfect, but I find this to be unacceptable.

Alas, I resort to using every other utility to clean out more and more crud SAVCE left behind, until there was nothing else being reported. Out of all of them, ClamWin had reported the most found. So, I left that one for last and it did remove a bunch of remaining infections left behind by all the rest. It's too bad ClamWin doesn't have real-time autoscan yet. With that, it would probably do the best job overall.

Needless to say, you and I both know that you can't rely on any of these utilities to completely abolish infections, as they only remove "known" threats (and sometimes further destroy the OS while doing so). I just find it particularly sad that a commercial product, which people pay good money for, happens to be the poorest at what we're told it does.

---

### Post by n3tfury on 2007-09-23
avg ftw for me.  5 years strong on my windows boxen.

---

### Post by starcraft.man on 2007-09-23
Geez, sounds pretty bad. Hope ya got the guy to reformat that drive after cleaning it out and backing up the good files. Only way to get it right again after massive infection.

As for Symantec, I've known for quite a while their products have been going down hill. I tell people not to use them or Mcafee, I find both to be bloated and overly resource intensive to a degree and neither seem to the best anymore either in terms of detection and fixing. I also have a personal vendetta against Symantec for buying out and promptly ruining my favourite firewall for Windows XP, Sygate 5.6. Karma will get them one day, I know so.

Anyway, for free scanners, AVG is my choice to recommend, it ranks pretty good and is light. For a review of AVs, check [AVcomparatives.org ]("http://www.av-comparatives.org/"). You can draw your own conclusions on recommendation.

---

### Post by init1 on 2007-09-23
Wow. That **is** pathetic.

---

### Post by skillllllz on 2007-09-24
Thanks for the tips guys. Yes, I backed up their personal data, reformatted, and reinstalled. That's how I always remedy bad/questionable infections. This attempt to use a bunch of utilities to clean up & remedy the situation was purely an experiment.

---

### Post by FuturePilot on 2007-09-24
Some of the best things are free. Look at Ubuntu.

---

### Post by blithen on 2007-09-24
I've always hated Mcafee and Symantec.
Back when I had windows. Avast and Sygate FTW!!
They pwned. Never had a problem with them.

---

### Post by nabaashraf on 2007-09-24
Hello all (I need help)
we are using a ldap server version 3 in debian sarge server
and knoppix client .all user profile (home folder) are stored in a single server and all user home directory automatically mounted using nfs anf autofs and it working fine without any problems.Now we updated our client pc operating system into kubuntu and retained old ldap server and home folder mounted using /etc/fstab.after some time ldap server process (slapd) consumes 99.9% cpu and server crashed with a kernel panic error
Please infor any information regarding this problem

---

### Post by Arathorn on 2007-09-24
Symatec itself has an even worse impact on your computer then the malware it's supposed protect you against. For the paid scanners, NOD32 is the absolute winner. Avast is good too, but needs a lot of resources. Unfortunately Sygate stopped developing their firewall years ago after being taken over by... Symantec. So now I recommend Comodo Firewall (or Linux off course, but people don't like it when that's the first thing you suggest, and frankly, when friends would recommend OSX or XP as solution for my problems I would be annoyed as well).

---

### Post by lisati on 2007-09-24
You think that's bad? A few months back Symantec's AV system falsely reported the "Pegasus Mail" email client as a virus, and cause major problems for their users. Talk about major fiasco!

[www.pmail.com](www.pmail.com)

---

### Post by Spike-X on 2007-09-24
Where are these people going and what are they doing to get all this crap on their computers in the first place?

---

### Post by julian67 on 2007-09-24
> **Spike-X said:**
> Where are these people going and what are they doing to get all this crap on their computers in the first place?

1: the internet
2: using windows

as a more serious comment I think the last thing you should do with an infected drive or suspected infected drive is connect it to a running windows pc to run AV on it. AV can only detect known problems, or heuristically *some* unknown problems. That windows PC is now certainly infected with undetected malware of all kinds which it is passing on to every box it connects to. If you have a suspect drive then you need to scan and analyse deal with it using non-writeable media, i.e. a bootable CD containing security tools like Hiren's Boot CD or System Rescue CD or one other of the numerous available. The better made malware attacks Windows AV, disables their updaters, renders them even more useless than they were before, walks right through the firewall by disabling it or creating rules to allow itself :D  I've repaired and cleaned numerous Win PCs on which the  AV was reporting no problems despite numerous malicious programs residing and running on the hard drives, IE being hijacked etc.

---

### Post by PmDematagoda on 2007-09-24
There was a period when Norton was very good, but now it is useless and uses up a huge amount of resources. My mom's Compaq laptop having:-

Core 2 Duo(1.6Ghz) 
512 RAM
128Mb Intel VGA

Takes 20 minutes just to start up Windows XP:mad:. Imagine wasting all that time, money and not to mention battery power for nothing. The virus guard in use is Norton Internet Security 2006. And as skillllllz has done, I maintain it every week. Keep it up to code and all that, but does the AV give me break with it's time wastage? No, I never count on it to be fast enough.

Now Kaspersky, that is a very good AV. I currently have Kaspersky for Windows Workstations on my desktop with:-

P4 HT CPU(3.2Ghz)
1 Gb RAM
256Mb Nvidia

 and it works like a charm. Detects every virus, spyware, adware, you name it.
And updates are quick and painless, as are the disinfection routines.:)

So Norton Antivirus is very bad, I wouldn't even use it if it was free. But Kaspersky has my whole-hearted support:lolflag:(for now).

P.S. When you compare prices, Kasperky is cheaper than Norton, but Kaspersky does a 10 times better job than Norton does.:lolflag:

---

### Post by bash on 2007-09-24
No offense, but you don't really use any of the products known for their good detection and removal. Symantec is not back. McAffee, Panda and Clam though have quite low detection rates.

I would recommend you take a look at the [av-compartives](http://www.av-comparatives.org) (Direct linking to the results is not allowed, so click on the Comparatives button and then chose the most recent one) or to take a look at the results posted [here](http://blog.chip.de/0-security-blog/microsoft-verbessert-seinen-virenscanner-20070821) (test is in german, but results are numbers so you should be able to figure it out).

So I would recommend that you use intead of McAffee, Panda and ClamWin: [Antivir](http://www.antivir.com) (free), [Kaspersky](http://www.kaspersky.com), [NOD 32](http://www.eset.eu). If you need any further information or help I would recommend you this forum: [www.wilderssecurity.com](www.wilderssecurity.com)

And besides that, pluggin an external drive to another windows machine, might already be enough to infect the machine. Much better is to boot up a livecd (of whatever distro you want) and install a couple of Virusscanners for Linux on it (yes they scan for Windows viruses). Good choices here would Antivir, AVG, Avast, maybe even ClamAV.

Oh and edit:

No scanner can detect everything. Bottom line. So its quite normal that one scanner finds something that the other missed. Thats why you use more than one. Right? So you can't really blame Symantec for not finding everything. You could just blame 'em for not finding as much as for example AntiVir

---

### Post by karellen on 2007-09-24
I could never stand symantec. in windows I use avg/nod32 as antivirus and zonealarm as firewall.

---

### Post by n3tfury on 2007-09-24
> **julian67 said:**
> 1: the internet
2: they're morons



^fixed

---

### Post by julian67 on 2007-09-24
> **n3tfury said:**
> ^fixed

Actually that's unfair. You don't have to visit dubious sites or do anything stupid to get compromised. There are plenty of legitimate sites with no ill intention who have been hacked and browsing them makes the user vulnerable to cross site scripting attacks which are very sophisticated and likely to succeed.  Lots of people knowingly host ads for a higher than normal fee per view knowing they are connecting unsuspecting users to bots which scan for vulnerabilities. If you visit web forums where people discuss how to maximise their pay per click/pay per view revenue you can learn some scary stuff.

---

### Post by skillllllz on 2007-09-24
> **lisati said:**
> You think that's bad? A few months back Symantec's AV system falsely reported the "Pegasus Mail" email client as a virus, and cause major problems for their users. Talk about major fiasco!

[www.pmail.com]("http://www.pmail.com")


Wow, that's totally craptastic!

PS - what a blast from the past.. I used to use Pegasus Mail back in 1997. :)

---

### Post by skillllllz on 2007-09-24
> **ubun-two said:**
> <snip> ...No scanner can detect everything. Bottom line. So its quite normal that one scanner finds something that the other missed. Thats why you use more than one. Right?... <snip>

Actually this is why I normally do not waste my time. If I suspect a Rootkit or Virus, and not just some annoying Spyware, it takes far less time to backup important data, wipe the drive and reinstall. This is the only way to be certain the machine is no longer compromised.

Again, this was an experiment to see which utility finds what. In this situation, I had no intentions of trusting some utilities to replace my preferred method of reinstalling.

---

### Post by Arathorn on 2007-09-24
Antivirus software often conflict with each other, so it's not a good idea to have multiple ones running. From the best scanners you can expect close to perfect detection rates.*

*The best protection against malware is off course an educated user.

---

### Post by n3tfury on 2007-09-24
> **julian67 said:**
> Actually that's unfair. You don't have to visit dubious sites or do anything stupid to get compromised. There are plenty of legitimate sites with no ill intention who have been hacked and browsing them makes the user vulnerable to cross site scripting attacks which are very sophisticated and likely to succeed.  Lots of people knowingly host ads for a higher than normal fee per view knowing they are connecting unsuspecting users to bots which scan for vulnerabilities. If you visit web forums where people discuss how to maximise their pay per click/pay per view revenue you can learn some scary stuff.

with as many viruses/spyware/malware that that person had, there's no way that machines antivirus was installed and/or up to date.  surfing on the net w/o antivirus software on a windows box is moronix, plain and simple.

---

### Post by skillllllz on 2007-09-24
> **n3tfury said:**
> with as many viruses/spyware/malware that that person had, there's no way that machines antivirus was installed and/or up to date.  surfing on the net w/o antivirus software on a windows box is moronix, plain and simple.

Yep, the AV was five years outdated! You'd be surprised how many people just assume that because they have it installed, they are protected; and as we all know, a false sense of security is the worst. Pair that with a lack of understanding of the threats out there and how they can get in, and you've got a combination that can ruin much more than just a PC.

This was the case with a bunch of folks I've encountered over the years. In the past year, I've helped a few get started on Ubuntu, my sixty-three year old father being one of them, and they have had very little or no complaints. For most of them, I immediately set up VMPlayer to host a clean WinXP install w/ no Ethernet adapter (hehe) and just a few apps they were not willing to part with.

---

### Post by Lucifiel on 2007-09-24
Nod32 is better than any of the other antivirus utilities I've tried over the years. :)

---

### Post by n3tfury on 2007-09-24
> **skillllllz said:**
> Yep, the AV was five years outdated! You'd be surprised how many people just assume that because they have it installed, they are protected; and as we all know, a false sense of security is the worst. Pair that with a lack of understanding of the threats out there and how they can get in, and you've got a combination that can ruin much more than just a PC.

This was the case with a bunch of folks I've encountered over the years. In the past year, I've helped a few get started on Ubuntu, my sixty-three year old father being one of them, and they have had very little or no complaints. For most of them, I immediately set up VMPlayer to host a clean WinXP install w/ no Ethernet adapter (hehe) and just a few apps they were not willing to part with.

the problem people have is clicking on "remind me later" when prompted to purchase once the trial runs out.  i don't feel sorry for these people.

nice of you to help them out though.  i ran out of patience with those types a LONG time ago :D

---

