---
title: "Updates breaking my system"
date: 2013-11-20
forum: Ubuntu, Linux and OS Chat
---

### Post by feeno49 on 2013-11-20
For the third time in four months, an update has hosed my machine.  And this is 12.04 LTS.  Is the S for Support or Suffering?  Do you test ANYTHING before you release?  I know its free, but  you should take some pride in your work.  It seems to me that the quality of Ubuntu has degraded continuously since the commitment was made to use Unity, which is a worthless on a desktop and I will never use it.  It looks like the switch to Debian is imminent.

---

### Post by tgalati4 on 2013-11-20
Linux Mint Mate works pretty well.  Mint rates updates with a 1 to 5 scale--don't update level 4 or 5 without making time for fixing breakage.  In general, updates to the kernel or xorg will cause breakage, so don't apply them until you have done a backup and you make time to fix the breakage.

This doesn't look like a support request, so perhaps you can add a support question to your post.

---

### Post by Bucky Ball on 2013-11-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. 

Urm, with all due respect, you are barking up the wrong tree. We are volunteers on this, a Ubuntu support forum. If you want to whinge about the direction Ubuntu has taken, or is taking, then Canonical would be your best bet. Ubuntu is not 'made' here. In fact, far from it. Your complaints are probably least likely to get heard by anyone you want to hear them here.

It would help if you actually mentioned what is getting hosed. I, along with a multitude of others, haven't had these issues with 12.04 LTS. Could be something specific about your hardware/software configuration. Anything. 

You are obviously frustrated about this but drawing a long bow and, if I may say, your arrows are misdirected. ;)

---

### Post by monkeybrain20122 on 2013-11-20
It would be more helpful if you can tell us exactly which update and how it broke your machine.

---

### Post by Bucky Ball on 2013-11-20
> **monkeybrain20122 said:**
> It would be more helpful if you can tell us exactly which update and how it broke your machine.

+1. Please post that one in a support section.

> **tgalati4 said:**
> 
This doesn't look like a support request, so perhaps you can add a support question to your post.

Don't do that. See above.  ;)

---

### Post by deadflowr on 2013-11-20
> **tgalati4 said:**
> In general, updates to the kernel or xorg will cause breakage, so don't apply them until you have done a backup and you make time to fix the breakage.


Don't you mean can possibly cause breakage?
Will makes it seem as if it does with absolute certainty, which isn't so.

But, yeah, one should make backups what they want regardless of updates anyway.

---

### Post by jdeca57 on 2013-11-20
> **feeno49 said:**
> It looks like the switch to Debian is imminent.
Freedom is the essence of Linux... ;-) But since your experience doesn't match what many others encounter daily perhaps it's also worthwhile to look ad your own hardware. Just to be sure.

---

### Post by lykwydchykyn on 2013-11-20
Again, someone posts with the assumption that his/her problems are universal, and is thus prepared to believe that people who write software are completely mental, incompetent, or stupid rather than assume that the problem is specific to his/her hardware or configuration.

---

### Post by rrnbtter on 2013-11-20
Greetings,
You should switch your update manager to download securtiy updates only. Absolutely any OS can be hosed. If the LTS is working properly then leave it alone.  Linux has always had a reputation for being technical but that doesn't mean you have to participate. By the way, there is some substance in the posts that reference hardware. I personally think Linux in general does a pretty good job keeping compatibility over a large range of hardware that wasn't originally shipped with Linux. However that compatibility isn't absolutely tied to Ubuntu.

---

### Post by buzzingrobot on 2013-11-20
To be frank, I've never had an update break a Linux installation, on Ubuntu or any other distribution.  I just spent several weeks using pre-betas of the unreleased Fedora 20.  Even the frequent and voluminous updates there didn't break the install.

An inverse relationship exists between the chances for a successful update and how much a user has modified a system beyond its baseline configuration. Software doesn't do magic.  Update software has to assume a certain level of consistency in the systems it is updating.  If the user has changed things, the update software will proceed in complete ignorance of those changes.

In Ubuntu, this specifically applies to software installed via PPA's.  Before doing an update, remove the PPA's from your sources list and remove the software you installed fronm there.

---

### Post by monkeybrain20122 on 2013-11-20
I am not sure if OP is even interested in finding a solution. He joined the forum in 2009 but only has four posts here, the one before this one was back in July 2012 (guess, complaining about Unity)

---

### Post by Copper Bezel on 2013-11-20
Routine updates never break my machine - they might break a small feature here or there, usually in a fixable way, but never the whole system. Version upgrades I tend to have less luck with - I've had my machine become essentially unusable for one reason or another after an upgrade. But less so in recent releases - I'm even starting to trust the updater instead of doing a fresh install every six months (not that the latter isn't really a better habit in any case.)

---

### Post by Bucky Ball on 2013-11-21
> **monkeybrain20122 said:**
> I am not sure if OP is even interested in finding a solution. He joined the forum in 2009 but only has four posts here, the one before this one was back in July 2012 (guess, complaining about Unity)

A drive-by whinging, perhaps. It happens. :-k

---

### Post by tgalati4 on 2013-11-21
Yes, I meant that kernel and xorg updates can break things--it is not a certainty.  I've had a few mishaps with such updates, but overall, they were  things that could be fixed with a little research.

---

### Post by monkeybrain20122 on 2013-11-21
Kernel update going wrong is easy to fix, just boot into an old kernel and delete the new one and then reboot. I have had troubles updating with xorg-edgers but ppa-purge fixed them. Now I would simply clone the / partition before such updates and if something goes wrong, it takes about 10 minutes to restore the image.

---

### Post by orb9220 on 2013-11-22
> ***"how much a user has modified a system beyond its baseline configuration"***

+1 to that as the major contributing factor with No. 1 being using proprietary drivers.
And another +1 that breakage is a real factor that has to be entered into the equation and planned for.
That is why doing regular backups is essential. I use [Redo Backup]("http://redobackup.org/") and back up my root and /home partitions before any major upgrades. Than breakage is a 20min. fix at most.

Tho I do challenge the stability of Level 4 & 5 security updates. As never seen any real world reasons for them beyond the theoretical threat.
And wonder if they are really needed in lieu of losing stability? What's the point of them if they give a higher degree of instability?

If someone more knowledgeable can chime in with the reasons specifically Level 4 & 5 am always willing to learn new things.
But haven't had any issues keeping them off my system as they do come with additional stability risk. Or am I mis-informed?
And exactly how in a real world scenario I'm being unsafe? Not the imaginary threats that could happen?
.

---

### Post by craig10x on 2013-11-22
I think that is why Upgrades go so well for me...i don't make major modifications on my Ubuntu...all i lose are a couple of ppas, Ms Core Fonts and Chrome (all easily put back of course) everything else gets smoothly transferred over (including all my important data like music, videos, docs, etc)...also..i do it from the live iso which seems to be a very reliable way to go about it...

And updates are always very smooth...can't remember the last time an update messed anything up on my system...

---

### Post by tgalati4 on 2013-11-22
The Risk Level assessment is based on how low into the kernel the changes take place.  Changes to DBUS for instance (the basic messaging service between processes) have a high risk of breakage.  Changes to Firefox will generally only affect the running of Firefox and not other applications, so the risk is lower--2 or 3.  Similarly, changes to xorg--the graphics server can cause a blank screen--which is severe, because it is difficult to troubleshoot.  Proprietary drivers are plugged into the kernel and to the graphics server--so again, changes to the kernel or the graphics server cause a higher level of breakage for those with proprietary modules installed.

I put off these higher level updates, until I have the time to spend to both reboot the system and to test the basic functionality.  If there is breakage, then it is not as traumatic, because I have prepared for it.

---

### Post by buzzingrobot on 2013-11-22
I keep fonts, must-have deb's from PPA's, edited /etc entries, crontab entries, tweaked config files, icons, themes, etc., stashed away on Dropbox. When I reinstall or update, I install Dropbox, go have some coffee while it syncs, and then move things into place manually.

I could put these things on a USB stick, which would eliminate the need to wait while Dropbox synchs.  But, I'd lose the convenience of moving files to the Dropbox folder as I change or add them. Of course, if I was clever, I'd just remember to copy the Dropbox folder to the USB stick just before I reinstalled. :)

---

### Post by mJayk on 2013-11-22
> **buzzingrobot said:**
> To be frank, I've never had an update break a Linux installation, on Ubuntu or any other distribution.  I just spent several weeks using pre-betas of the unreleased Fedora 20.  Even the frequent and voluminous updates there didn't break the install.



Have to say ... what :D

---

### Post by Copper Bezel on 2013-11-22
No kidding. People say things like this, and I think, are we even using the same OS?

Edit: With that said, my system is usually heavily tweaked.

---

### Post by lykwydchykyn on 2013-11-22
> **mJayk said:**
> Have to say ... what :D

Probably depends on your definition of "break".  What "breaks" an OS for one person may be a minor configuration snafu for another user.

---

### Post by buzzingrobot on 2013-11-22
> **lykwydchykyn said:**
> Probably depends on your definition of "break".  What "breaks" an OS for one person may be a minor configuration snafu for another user.

I take it to mean "doesn't work", as in won't boot or boots to an empty nonfunctional screen. And, I mean running routine updates, not upgrading in place from one release to the next. (That, I seldom do.)

Writing over or otherwise eliminating personal tweaks made to a system is not breakage.  It's to be expected.

I've certainly screwed up plenty of systems on my own.  But, I don't run updates automatically, I pay attention to reports of problems and avoid installing those packages until the issue has been resolved.

I also avoid oddball or cutting edge hardware, which reduces update risks.

---

### Post by SeijiSensei on 2013-11-22
> **mJayk said:**
> Have to say ... what :D

Having recently spent an hour or two resolving version conflicts among Perl modules on a CentOS 5.8 machine, I have to say "what" myself.  I also have had various close encounters with ClamAV versioning issues.  Despite what you might think about the relative stability of servers and desktops, I've had more server issues.  Probably that is because I use pretty vanilla desktops and more complex servers.  They are usually running some combination of ntpd, bind9, sendmail with spam/virus scanning, dovecot, apache with PHP, PostgreSQL, and MySQL.  With ever-moving targets like ClamAV, something is going to break eventually.

---

### Post by linusti on 2013-11-22
You're lucky on things not breaking, buzzingrobot.  Seems that one of the updates they did on Nov 2, for 13.10, with Perl, fries all sorts of dependencies.  Can't install MySQL.  Can't install X2Go server.  Can't install texinfo.  Can't install Pidgin.  Three out of the four break me badly and the way they did the update, you can't, without a lot of effort, force-downgrade the busted Perl stuff.

---

### Post by linusti on 2013-11-22
> **Copper Bezel said:**
> Routine updates never break my machine - they might break a small feature here or there, usually in a fixable way, but never the whole system. Version upgrades I tend to have less luck with - I've had my machine become essentially unusable for one reason or another after an upgrade. But less so in recent releases - I'm even starting to trust the updater instead of doing a fresh install every six months (not that the latter isn't really a better habit in any case.)

Heh...  I was the same way until today.  I can't even do what I was planning on doing work-wise right at the moment.  I don't quite know what they were thinking when they did this, but on Nov 2, they pushed some updates to Perl and updated the dependency chains for the same.  It broke a lot of things with no graceful way to un-break them on the system until they push the missing extra packagings.

I'll be quite a bit more cautious and leery of doing upgrades from here on out.  Hell, I couldn't even really do a clean-install with the stuff in the repos in the state it's in.

---

### Post by buzzingrobot on 2013-11-22
> **linusti said:**
> You're lucky on things not breaking, buzzingrobot.  Seems that one of the updates they did on Nov 2, for 13.10, with Perl, fries all sorts of dependencies.  Can't install MySQL.  Can't install X2Go server.  Can't install texinfo.  Can't install Pidgin.  Three out of the four break me badly and the way they did the update, you can't, without a lot of effort, force-downgrade the busted Perl stuff.

Note how I defined "break".  As long as it boots and gives me a screen I can use, I don't call it breakage.  Messing with libraries, breaking individual apps, screwing up dependencies?  That's just a PITA.

---

### Post by monkeybrain20122 on 2013-11-22
> **linusti said:**
> Heh...  I was the same way until today.  I can't even do what I was planning on doing work-wise right at the moment.  I don't quite know what they were thinking when they did this, but on Nov 2, they pushed some updates to Perl and updated the dependency chains for the same.  It broke a lot of things with no graceful way to un-break them on the system until they push the missing extra packagings.

I'll be quite a bit more cautious and leery of doing upgrades from here on out.  Hell, I couldn't even really do a clean-install with the stuff in the repos in the state it's in.

Hmm.. May I ask how did you update? I have not gotten any update to Perl on Nov 2 or since. My current version is 5.14.2-2build1, which I think is the same version since install. Also, did you get no warning for unmet dependencies? 

It is possible that you might have installed something from a ppa and then disabled the ppa, or might have installed something from Saucy-proposed and then disabled it so some dependencies might have the wrong versions. I have tried to install some -dev files and got tons of unmet dependency errors because somewhere in the past I have installed something from Saucy-Proposed and then disabled it so some versions were pumped up, to fix it I reactivated Saucy-proposed  just for this one time everything then went through. This is a test install on an external drive, if it were a real working installation I won't mess with proposed.

I am leery of graphic driver updates and I do use a ppa to get the latest. So usually I would clone the root partition with fsarchiver before any such updates and if anything goes wrong, it can be restored in 10-15 minutes.

---

### Post by acodea on 2013-11-22
I have to suggest that there must be problem file/folder/program(s) which Ubuntu is giving trouble. My 12.04 o/s has worked consistently since I installed it three months ago. I have been a member that long. I would ask you to find the trouble and not install that program or, find another operating system or flavour of Ubuntu. I know this is one of the most frustrating areas for you now and hate to see you go, but...

---

### Post by Copper Bezel on 2013-11-25
Ha. Ironically, I just updated to Saucy (clean install,) and it was the smoothest transition ever. I think I put more time into clearing out my Windows partition to make room for it than I did actually setting up after the install....

---

### Post by Bucky Ball on 2013-11-25
> **Copper Bezel said:**
> Ha. Ironically, I just updated to Saucy (clean install,) ...

You didn't update, you upgraded to a newer release. The OP was originally talking about regular, run of the mill updates, all in 12.04 LTS. Nothing about upgrading the release killing their system or having a problem with that. ;)

---

### Post by coffeecat on 2013-11-25
The OP started this thread four days ago and has not been back since. 

@feeno49, if you had really been interested in constructive debate, you would have extended the courtesy to those who have posted by responding to the points they have made long before now. And...

> **feeno49 said:**
> Do you test ANYTHING before you release?  I know its free, but  you should take some pride in your work.

As Bucky Ball has already pointed out, the members of this forum are volunteers, ordinary users such as yourself. 

Thread closed.

---

