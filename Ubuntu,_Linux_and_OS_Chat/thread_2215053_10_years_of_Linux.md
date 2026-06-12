---
title: "10 years of Linux"
date: 2014-04-04
forum: Ubuntu, Linux and OS Chat
---

### Post by gregmhyman on 2014-04-04
I posted this on launchpad, as that was the first link I was directed to from the canonical's "contact us" page.
The first response I received was to point out that I was not actually asking a question, which is a fair point.
So I am posting it here instead - not as an attempt too troll the forum, but rather as an attempt to post this somewhere where it may be seen by someone at canonical who will take it to heart.


I had intended on sending this directly to Canonical, but they do not seem to have a real "contact us" link (with the exception of sales or server support), and I really did not feel like calling them or sending snail mail.  So this will have to be the forum for this posting.


I have been using Linux for 10 years.  I should clarify - I have been using Ubuntu for 10 years.  Mandrake / Mandriva was my first attempt, but I seem to recall requesting, and receiving, several Ubuntu installation CDs in the mail that installed a much nicer OS.
Since then, I spent 2 years dual booting, and the past 8 using Ubuntu as my primary (or only) OS on 3 laptops and no fewer than 6 home (tower) systems.


It has been very educational.


I have become very adept at the CLI, I can troubleshoot and (usually) resolve most login / non-booting / grub problems without needing to go online, and troubleshooting sound, graphics, and wifi issues has become almost second nature for me.
I have been a vocal proponent of Unix on reddit, digg, and several other public forums, as well as to my coworkers - to the point I am generally labelled a 'fanboi'.


My family have become used to a new desktop or launcher or password every 6 months; our son (now 12) cringes any time he wants to play a windows-only game because he knows that the single dual-boot system we have will take at least 15 minutes to restart and (finally!) be ready for crysis, spore, portal, or rct3 (yes, I still have that one!)  


Today, however, and for the duration of the upcoming weekend, I am dumping all Linux systems, and switching everything we own over to Windows.  Exclusively.


I would like to explain my reasoning - this is what I had intended to send to Canonical directly, rather than post it here and be subjected to a hundred 'flame' posts; perhaps mentioning my decade-long history of being a supporter of Ubuntu will prevent that, but probably not.


Last night, I installed the latest handful of updates that showed up on our main computer (XUbuntu 13.10) and rebooted.  Understand - this was for me a 'background' task; I intended on moving our living room around to make room for our new furniture, and playing some music on the computer while we worked.  


Six hours later, I was still sitting in front of the computer trying to get it working.


I had done a clean install about 2 weeks ago; the prior installation of Ubuntu 13.10 had started acting up - programs that had been closed would not launch again, because they were still running - I could launch system monitor and close them that way, but only once - because then system monitor would not re-open because it was still running without a visible window.  My guess is that gnome was closing just the window, but not closing the program itself.  This behaviour was across the board - software center, chrome, nautilus, etc.  No error messages, they were just opening without a window.


After struggling with that for several weeks, and finding no definite answers anywhere online, I finally gave up, wiped the system, and did a fresh install from a new Xubuntu 13.10 cd.  My feeling was that gnome had developed a problem with my mobo or video card, and I seem to remember the update from 13.04 to 13.10 resulted in my spending an entire Saturday trying to coax ccsm to give me back my windows' menu bars and borders (fortunately I had been through this multiple times over the years on several machines, so it wasn't a new thing for me - as I said, I've gotten good at fixing things on my linux machines over the years), and reset the nvidia screensize to fit on my overscanning tv which does not have a menu option to disable overscanning, dealing with the video player crashing if I disabled the subtitles, an error log which now has invisible time and date stamps, and so on...)


So a fresh install of XUbuntu seemed like a viable option; I had grown weary of having to constantly question the stability of gnome after years of various quirks - perhaps xfce would be a little easier to maintain.


I had to go through the usual dance after a fresh install so I could watch a DVD, listen to an MP3, etc. but all in all, it was a fairly typical installation.
Well, the default video player wouldn't synch the picture and the audio (an hour of messing with it, and I finally went to VNC which works fine.)
... and the latest nvidia drivers seems to have an overscan option, but now we're back to needing xorg.conf (except last week, an update package dumped the overscan settings and I had to re-create them.)
... and tumblerd crashes every time I open thunar
... and on and on - which, as I said, is a fairly typical installation.


Yesterday, I installed the daily round of available updates as I said.
When I rebooted, it came up with a new one for me...  I tried to open the drive that has all of my music on it so we could listen to something while rearranging the living room.  But for some reason, the drive would not mount - I do not have permission to do that (internal hdd, no special partition, never had to manually mount it to open it before.)
I tried installing palimpsest, but the software center told me I was not authorized to install software.
I tried mounting it via the cli, but was repeatedly told that I do not have permission to do that.
I tired it as root, but was told I did not have any rights in sudoers.
I tried looking at my rights in users/groups, but I had no functionality there other than to change my name.
I tried rebooting my machine, but apparently now the reboot option only does a logoff, and there is no way of actually rebooting short of hitting the power button.
After cycling the power button, now my machine comes up to a terminal-style login: prompt for about 10 seconds, then goes on to the gui. (I had seen that in Ubuntu as well, I seem to recall having to reinstall cups, or my specific printer to make it go away.) (Yet I have not tried messing with my printer on this new installation; I never could get the scanner to work properly in Ubuntu, except on the remaining windows installation on my son's machine, so I have not yet even considered messing with it on Xubuntu - so who knows where the glitch is this time.)
But rebooting changed nothing.
Oh, and the overscan settings are gone again, so now I'm doing everything half-blind since everything from the launcher takes place at the top left of the screen, out of visibility.
Advanced options / root prompt at a power-button reboot would not allow me to delete the user, and the only new user I could create had the same rights and privileges as a guest account, even though I made certain to give it admin rights.


I ultimately booted up to the live CD and tried to fix things that way, but all I get from that is a nice message telling me that my primary hard drive is now a "read-only file system."


I said a few unkind words at that point; I still have 2 non-working sansa mp3 players and a microsd card that were bricked a few years ago as a result of an issue with nautilus - multiple files being copied over the usb cable go slower and slower until it finally stops altogether and then reports "read only file system" which, after a few days of fsck, dosfsck, and attempted reformatting yields nothing except "read only file system.")  (I have 2, because the first one I assumed was actually corrupted memory in the device, the second one and the new microsd card were from trying it again and being reminded that 'linux just can't do some things')


I ran fsck -c which found nothing.


I ran fsck -cc which also found nothing, which is a surprise, because trying to change the user rights immediately came back with "read only file system" - so how could fsck do a write test?


It was at that point, after six hours of working on the computer rather than spending the evening with my family (again) that I finally had an epiphany.


It is not worth it.


That was my moment of clarity.  I have spent years learning how to troubleshoot linux problems.  And a decade after starting, I am still getting better at troubleshooting, but I have finally seen that linux is not improving - rather, it is finding new ways to not work that require me to spend even more time learning how to troubleshoot.


I want to turn on my computer, watch a youtube video with my son, listen to some music, keep in touch with my sister in Germany, maybe plug in my phone and GPS and update them, watch a little porn, and play a few games.  Nothing special.
Linux is able to do all of these things, but only after patiently adjusting and tweaking and caressing more settings than a person should have to.


I have a 6-year old 24" monitor that never would work correctly until I spent an entire weekend learning about edid, and the proper way to set timings for every single mode and color depth in xorg.  All of which quit working the second the driver was updated.  It sits in the closet unused.
My 5.1 speakers sit in the closet unused as well because I got fed up with trying to get the system to output proper 5.1 channels, only to have to go through it several times over the years whenever an update would break it again.
I have never plugged my phone, tablet, gps, camera, or my son's media player into the computer for fear of having it turn them into a read-only systems (or worse)
I cannot count the number of hours I have spent stuck in front of my computer trying to make it work correctly, only to be rewarded with yet another round of updates that undo everything I have fixed, along with some new issues that start the cycle all over again.


Meanwhile, my wife's windows laptop is kept out of my reach, because she has suffered through a decade of watching me spend more and more time struggling to make linux work correctly.
And the thing that makes me sad, is that for all of my years of defending linux as the greatest thing since sliced bread, is that every time she turns on her laptop, it just works.
No constant tweaking, no cli, no limitations, no user permission errors... it just works.


I want a system that just works.


And for ten years, I have gathered enough data to prove to me that linux cannot provide that.  It is not ready for the home user, because it rarely "just works."


So thank you, canonical, for the education.


But the fact that a casual user has to have a ten-year education to find out that they are still not able to point, click, and listen to music, is a sign that the OS you have made available is not ready for the masses.


I bid you good luck, but I sincerely hope that you do a reality check from time to time to see if you are developing a system that is user-friendly enough to be made available for someone to use out-of-the-box without jumping through the hoops that seem to be accepted by the community.


In response to the question I was asked, "Just what is the question here?"
No question... just a post that will hopefully catch the attention of someone at canonical and provide them with what I feel is a valuable data point as far as feedback from their users.
If the only way they monitor the success of their OS is by the number of downloads, or the number of problems marked as 'solved' in the forums, then they are missing an important piece of feedback - the number of people who give up after actually doing as much as possible to make it work.


So, this is not a question, and perhaps does not belong here.  But there is really no other way that I can find to bring my sob story to the support staff that may actually care to hear it.

---

### Post by QIII on 2014-04-04
Since this is a volunteer user support forum and not a place Canonical employees frequent, this will likely not get Canonical's attention.

If Windows works for you, then use it.  There isn't anything to be gained by explaining yourself here, nor should you feel any obligation to offer one.

---

### Post by coldraven on 2014-04-04
My fully updated Xubuntu 13.10 is working happily away on my little eeePC 900. It plays music and streams video with no problems.
I've just returned from a month away with it in my rucksack. It was a great little tool for keeping in touch with the world.
I suggest that you need a break from all computers, I know that frustrated feeling. 
Wishing you well.

---

### Post by hakermania on 2014-04-04
Of course if things do not work out for you, just use Windows or anything else that works.

Just I want to point out that don't think that all of us that are using Linux on our daily basis have to go through all this. It just works. That's why I am using it.

It even requires less tuning than Windows in order to work. But that's just me. That's why you have (and you should have) the option to switch to anything you like.

---

### Post by buzzingrobot on 2014-04-04
I've had only about three days of Windows experience in the last ten years or so, but I hear updates there cause problems, too. ;)

I am convinced that most problems updating Ubuntu, or any other established distribution, are prompted by something the user did that altered the system beyond the stock system the update process must assume is there.

Ditto for Windows and OS X, I'm sure.

---

### Post by C.S.Cameron on 2014-04-04
Ten years with Ubuntu and this is your first Forum post?
If you had asked, you would have been advised that for stability use LTS.
Your complaints about Ubuntu are similar to mine about Windows, except for Windows add a big dose of viruses and malware.
No offense intended, but this post sounds like it came from someone under the pay of Microsoft, I believe it's called FUD.

---

### Post by gregmhyman on 2014-04-04
Not my first post; over the years I've been from hotmail to yahoo to gmail, and have posted from all of them. 
(And nobody ever suggested I use an LTS release, just a good collection of commands and settings to try and fix the issues at hand.) 
This forum has helped me quite a bit.
But - new job, new company - mandated email, and no access other than that one.  So this post is what I did at lunch.

And no, not being paid by microsoft to report the issues I've had over the years with ubuntu, and this is all fact, not just me spreading unfounded claims.

Ubuntu has been a learning experience, yet it continues to have major issues - case in point, installing an upgrade causes the sole user to suddenly have no access beyond 'guest', and the primary hdd suddenly being flagged as 'read only' but only for certain operations and commands.
If I could make up horror stories in an attempt to cause fear for the people reading these forums, I seriously doubt I could come up with worse stories than the ones that actually happened to me.

---

### Post by vasa1 on 2014-04-04
> **gregmhyman said:**
> ...  So this post is what I did at lunch.
...
That made me smile.

---

### Post by mastablasta on 2014-04-06
hmm... how can osmeone say the system has these issues when it's clear to me that most users do not have these issues nor were they reported on launchpad?!

i mean i installed two 12.04 LTS and one has 1 issue for which i found a workarround, while the other has none. i also have 2 13.10 that have no issues. hmm... when i find a problme that can't be solved i report it so someone can hopefully solve it. i mean the same can happen with windows. they work well on some mashicnes. so well that after 10 years i feel no need to change the OS (at least not yet) and i saw another computer with winxp that had constant issues, crashes, reboots etc. and it made me feel it's a hardware issue. until i stuck linux on it and everything works since.

---

### Post by tgalati4 on 2014-04-06
I've always felt it takes 10 years to learn linux.  For the OP, perhaps 10 years was enough to realize he prefers Windows.  The OP has developed his troubleshooting skills, only to realize that he does not like troubleshooting linux.  The OP sits down to lunch and instead rambles on about how he has wasted the last 10 years.  

I want to hear back in 10 years on the OP's Window's experience.  At lunch, no less.

---

### Post by dennisn77-ameritech on 2014-04-06
I started out with Ubuntu 9.10 and have been dual booting with Windows ever since.  Most of my problems have come from my mistakes/ignorance/lack of knowledge, you name it.  I currently have two computers with Ubuntu 13.04 and two with Ubuntu Studio 13.10.  There are a few things I need Windows for, but they are slowly fading away.  One 2002 vintage Dell Inspiron 1100 is Ubuntu Studio only.

Use what works for you.

---

### Post by 23dornot23d on 2014-04-06
> 
No offense intended, but this post sounds like it came from someone under the pay of Microsoft, I believe it's called FUD.                 


This is something I keep thinking - and having to bite my tongue .......

How much help - and the person is not here to get help - read their own past comments >>>  [http://ubuntuforums.org/showthread.php?t=2215326](http://ubuntuforums.org/showthread.php?t=2215326)

The same person was probably watching the other thread - that did the same thing >>> [http://ubuntuforums.org/showthread.php?t=2215285](http://ubuntuforums.org/showthread.php?t=2215285)

Nearly one a day ..... usually few prior posts if any at all .

____________________________________________________________

Maybe they just do it - while they know XP users may be popping on the site to see whats happening - only takes a few

paid trolls to make it look like things are bad ......... when in fact things are going to be the best I have ever known them to be  .........

---

### Post by grier-devon on 2014-04-07
I am sorry you have had so many problems with Linux, just pure unlucky. I have installed Ubuntu on about 30 different machines From Dells, HP, Asus, Vaios and Lenovos since I started using Ubuntu in 2008, not all mine but all working completely out of the box. I have never had ubuntu fail unless I broke something while attempting something I didn't understand. 

Part of being a Linux user sometimes requires understanding compatibility with external devices and what works best like selecting HP printer, cloud services for data transfer and music needs and among many other things. Screen problems just unlucky I guess as I have never seen that.

I am not saying you haven't had problems as I am sure you have but so does every platform, go to a Windows forms. I do sometimes to read about some peoples problems and people using Windows suffer from different problems then Linux users like bsod, infections, driver compatibility when updating, fragmented and slowing computer, bloatware and so much more.

Your wife has good luck with Windows and you have had bad luck with Linux, for me the flip. I have had great luck with Linux and my wife has had horrible luck with Windows from infections, corrupted data, broken drivers and crashes. Enjoy windows, you will be back to Linux especially after ten years of use. Windows would drive you up a wall.

---

### Post by help_me2 on 2014-04-08
tldr. I've always had too many problems with windows, hence my move to linux 7 years ago. Never had any problems. Good luck, and use what works for you.

---

