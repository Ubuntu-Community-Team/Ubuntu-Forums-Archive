---
title: "Did your X break with the update?"
date: 2006-08-22
forum: The Cafe
---

### Post by aysiu on 2006-08-22
Just curious, as I caught it in time, but it seems a lot of people were hit.

---

### Post by Donnut on 2006-08-22
It appears to be a 50-50 mix.  I can tell you, im not gonna try and test fate again.

---

### Post by Ramses de Norre on 2006-08-22
I updated X without having watched the forum first, restarted X and all went fine..

---

### Post by Rackerz on 2006-08-22
I haven't had the pleasure of booting into Ubuntu lately, I'm kind of dreading it. Should I update, or wait for a fix to be released?

---

### Post by aysiu on 2006-08-22
> **Rackerz said:**
> I haven't had the pleasure of booting into Ubuntu lately, I'm kind of dreading it. Should I update, or wait for a fix to be released?
Don't update.

---

### Post by Rumor on 2006-08-22
The update broke my X. I wasn't aware of it until I rebooted. I tried several things to fix it (unsuccessfully). I started backing things up to do a re-install, but it was late, so I decided to boot into Arch for the night and leave the re-install for this evening. 
When I checked the forums this morning, I found the fix and it worked for me, so I am very happy that I didn't wipe things out last night.

---

### Post by Bragador on 2006-08-22
Wooo what the hell are you all talking about ? What's happening ? Is my Ubuntu in perils ?

I don't understand...

And what's this "X" you are all talking about ?

---

### Post by bensexson on 2006-08-22
I have my desktop update automatically with a cron job.  the cron job does not reboot.  I got the update before I knew of the problem but I had not rebooted.  This is a file and print server so I reboot rarely.  My laptop was not updated yet.  I just got the latest updates but have not rebooted either yet.  I expect they will work.

---

### Post by cstudent on 2006-08-22
I didn't get zapped. I haven't updated anything lately. What struck me was the number of responses I saw that seemed to immediately jump into the "reinstall Ubuntu" fix. Must be all that Windows conditioning we've all had in the past.

---

### Post by saracen on 2006-08-22
A fix has already been posted and is in the repos.

---

### Post by Onyros on 2006-08-22
I updated, even though I read the warnings and was prepared to repair it, in case it broke.

In the end, it didn't break, at least in my laptop (with ATi proprietary drivers installed), so I guess I was just plain old lucky.

I'll have to update my wife's laptop as well.

This is worrying, really. How can an X update break with an update like that? Imagine you're someone whose Ubuntu box was setup by someone else, told to proceed with all updates... and in a second your X is broken and all you have is a commandline.

I'm just writing this because I've setup a couple of Ubuntu boxes for other people whose computer savviness is quite low, and I'm just expecting them to call me and tell me their computer is broken...

---

### Post by John.Michael.Kane on 2006-08-22
aysiu what is the version number of the xserv package thats causing the issues?

---

### Post by VirtuAlex on 2006-08-22
Voted other, because I actually have no idea if it did brake or not. Probably yes. I just did not restart my comp after 10.3 update, because it was some fix for intel and I do not have intel, so I did not feel any need to restart. Then I noticed announcement in the forum and after about 15 minutes there was 10.4 available. I installed it, rebooted and everything seems working fine. But it is defenitely day of grief in Ubuntu history - "Most users ever online was 3,401, 1 Hour Ago at 10:00 AM." I guess they were searching for soulution. And how many just did not get through to the forums? I just imagining them staring at black screens, with no access to the internet. Terrible...

---

### Post by jasay on 2006-08-22
> **SD-Plissken said:**
> aysiu what is the version number of the xserv package thats causing the issues?

1:1.0.2-0ubuntu10.3 is bad. 10.4 is up and reverts the changes.  Here's the changelog:
> xorg-server (1:1.0.2-0ubuntu10.4) dapper-updates; urgency=low

  * Reverted patch 005_pci_domain.dpatch -> breaks PCI setup for many users.
    This patch will need further work before it is reintegrated into
    xorg-server again.

 -- Rodrigo Parra Novo <rodarvus@ubuntu.com>  Tue, 22 Aug 2006 11:27:58 +0200

xorg-server (1:1.0.2-0ubuntu10.3) dapper-updates; urgency=low

  * Added 992_linux_bios_bug_6751.dpatch (Closes Malone #36461)

 -- Rodrigo Parra Novo <rodarvus@ubuntu.com>  Fri, 11 Aug 2006 14:00:07 -0300

---

### Post by VirtuAlex on 2006-08-22
> **jasay said:**
> Here's the changelog:
I like that: urgency=low

---

### Post by MaximB on 2006-08-22
I got lucky
I updated but did not reboot
then I opened ubuntuforums as always and saw the warrning
and then downgraded.
were is the fixed update ? I do not see it in the "update manager" .

---

### Post by frrobert on 2006-08-22
I updated but hadn't rebooted yet when I saw the notice.  I installed the fix before I rebooted and my machine rebooted fine.

---

### Post by Bragador on 2006-08-22
I updated 20 minutes ago. I rebooted to check if it was broken (whatever is supposed to be broken) after seeing all the fuss on the forums. It seems everything went fine since I'm here so I really don't understand what's going on.

---

### Post by insane_alien on 2006-08-22
i updated but then read about the problem on here and applied the fix before rebooting.

---

### Post by prizrak on 2006-08-22
I honestly don't know, I haven't had any update reminders in a while. Most likely because I was playing with Compiz and installed CVS snapshots of a few libraries, can't get any more up to date than that ;)

---

### Post by angkor on 2006-08-22
Other.

I didn't get a reminder to update yet....so I didn't.

---

### Post by bluenova on 2006-08-22
> **Onyros said:**
> 
This is worrying, really. How can an X update break with an update like that? Imagine you're someone whose Ubuntu box was setup by someone else, told to proceed with all updates... and in a second your X is broken and all you have is a commandline.

I'm just writing this because I've setup a couple of Ubuntu boxes for other people whose computer savviness is quite low, and I'm just expecting them to call me and tell me their computer is broken...

Yep, this is worrying me a lot at the mo. Imagine how many 1000's of Ubuntu boxes that are out there, setup by somebody else and the user is told here you have a stable system; just keep it up to date when it asks to update. Now those 1000's of people are sitting at a command prompt not knowing what to do.

---

### Post by jdong on 2006-08-22
All 4 of my PC's (with nvidia/ati/i855 video cards) survived the upgrade with no problems, but my friend's pc was not nearly as lucky :)

I'd be curious as to a technical explanation of when this update would break a system and when it wouldn't. From what I gathered it was a change in the way Xorg probed the PCI bus that caused the problem.

---

### Post by Perfect Storm on 2006-08-22
Was aware that it might break my system, but did it nonetheless. Works fine for my system.

Nvidia card here on 1:0:0 no problem.

---

### Post by Brws on 2006-08-22
Yes. Updated this AM. Messed up on reboot. Did complete reinstall excepting that particular update. OK now

---

### Post by bobbybobington on 2006-08-22
This kind of thing is not good:frown: . **Updates need to be tested and fixed if neccessary before being put out**.

---

### Post by m83 on 2006-08-22
I updated this morning, but I didn't restart X the whole day, so I don't know if the update would break X in my case. Later I found out about the problem and launched another update and saw that there was a xserver update. I ran the update and then I restarted X and it worked ok.

I guess I was kinda lucky not restarting X this morning after the update :D.

---

### Post by PathSpace on 2006-08-22
I didn't install any updates yet, and am still afraid to (because I fear that it might mess up my AIGLX/Compiz installation).  :confused:

---

### Post by r4ik on 2006-08-22
I never touch any updates before i had coffee.
Second stop news and weather.
Third the Forum or to keep it short i knew and held off.

---

### Post by jdong on 2006-08-22
> **bobbybobington said:**
> This kind of thing is not good:frown: . **Updates need to be tested and fixed if neccessary before being put out**.

I absolutely agree with you there. Ubuntu needs a much larger team of testers to screen updates (not just security updates, dapper-updates too) for problems like this before rolling them out to the masses. Especially if Ubuntu is to be enterprise-ready.

---

### Post by Nrvnqsr on 2006-08-22
My test desktop also broke but I didn't updated my main desktop, thank goodness that it is only my test, and I thank those whoever made partimage program saved me 52 mins of my life reinstalling the whole OS =D>

---

### Post by r4ik on 2006-08-22
> **jdong said:**
> I absolutely agree with you there. Ubuntu needs a much larger team of testers to screen updates (not just security updates, dapper-updates too) for problems like this before rolling them out to the masses. Especially if Ubuntu is to be enterprise-ready.

I cant get rid off the feeling this Forum is used as test/solution platform.

---

### Post by K.Mandla on 2006-08-22
Count me as one hit by the bug, plus one more for mom's computer.

---

### Post by nalmeth on 2006-08-22
Yes, but not mine.

A friend had just installed, we did some tinkering, got his updates, rebooted, and voila!

Good to know what went wrong though, I was a little baffled at the time.

---

### Post by bluenova on 2006-08-22
> **jdong said:**
> I absolutely agree with you there. Ubuntu needs a much larger team of testers to screen updates (not just security updates, dapper-updates too) for problems like this before rolling them out to the masses. Especially if Ubuntu is to be enterprise-ready.
Sounds like a great idea. Perhaps just a pre-release repository or something along those lines. I would use it, as I've never had a problem that I couldn't solve, but I know there are many desktop users that just had to reinstall Ubuntu today.

---

### Post by CronoDekar on 2006-08-22
It didn't break, but I also didn't restart X after the update so I can't say for sure that it wouldn't have broken.

---

### Post by AndyCooll on 2006-08-22
Well it "sort of" broke on my boxes, but the effect was minimal since by the time I was doing the update the 10.4 fix was available.

I'd run the update on one of the boxes before I knew about it but hadn't rebooted. I then read about the fault and also read that a fix was available. On reboot the X-Server of course was then disabled. Thankfully by just updating my sources again and doing another upgrade the fault was fixed. 

:cool:

---

### Post by Christmas on 2006-08-22
I installed the 10.3 version but forgot to restart the X Server. Then i read on IRC to install the 10.4 version so I waited until it was available on the Romanian repositories and updated then. So no break for me today. They call it "The Black Ubuntu Day" :)

---

### Post by chickengirl on 2006-08-22
I saw a thread on another forum linking to the thread on this one after I had updated and before I had rebooted. By the time I got here the fix was already up and I got it through the update manager. I still haven't rebooted.

---

### Post by az on 2006-08-22
To include a dapper-updates repo alongside the dapper-security (security updates) is very new.  Ubuntu never had it before and Debian never (and still does not) have it.

The policy has been to freeze package versions and only include a new package (or usualy new patches to old versions) in the security-updates repos if there was risk of data loss or security vulnerability.

I tried to look it up, but I could not find the policies for inclusion of new packages into the dapper-updates repo.

Anyone going to disable the dapper-updates repo because of this?  You still get security updates that way.

---

### Post by jimrz on 2006-08-22
sure wished I had checked here before updating my desktop...but did not, so did not know and wound up with broken X + I messed up xorg.conf trying to do the reconfigure thing...booted up laptop, found the info needed (correct ver# for known good ver, etc) here on the forums...used command line to revert to good ver + reinstall nvidia-glx then repaired xorg.conf, then all was good again...I love these forums!!!

even worked up the nerve to update both machines with the "fixed" update today, but not without first checking here to see that this one should be ok (not likely to make that mistake again).

---

### Post by cptjaben on 2006-08-22
I got hit without knowing it, but luckly it was later than most and there was plenty of info on the forums.

---

### Post by jdong on 2006-08-22
> **azz said:**
> 
Anyone going to disable the dapper-updates repo because of this?  You still get security updates that way.

Naw, Some of those updates in there are quite valuable to me. I think the devs have learned their lesson about being more careful with updates.

---

### Post by confused57 on 2006-08-22
I was reading the Ubuntu forums using Windows about 9 am this morning and read the post that the latest xserver-xorg update would break your system.  I realized that I had updated all 3 of my computers running Dapper, around 11 pm last nite, but just shut the computers down after doing so...I said to myself, nah, I've never had an update break my system...but out of curiosity I rebooted into my other hard drive with Dapper and sure enough, my xserver was broken. Checked the other 2 computers and all 3 were borked, disconcerting to say the least...I can only imagine how someone felt who's only been using Ubuntu for only a short time.
   Hung around the forums for awhile using Windows(guess I could have used the Live CD), tried tseliots suggestions at the beginning of the thread, but kept getting 404 error...and just a short time later, read that the xserver upgrade had been fixed in the repos...update & upgrade repaired all 3 computers.
The developers should be commended for getting the "fix" into the repos so quickly...human error is a fact of life, mistakes happen and we learn from them.
  I've always downloaded and installed updates ASAP, may have to rethink my approach...wait a day or 2.

---

### Post by wmcbrine on 2006-08-23
> **azz said:**
> To include a dapper-updates repo alongside the dapper-security (security updates) is very new.  Ubuntu never had it before and Debian never (and still does not) have it.I'm beginning to see the wisdom of this policy.

---

### Post by dada1958 on 2006-08-23
X broke on my Ubuntu desktop after an update. It wasn't the first time that that happened. Fortunately it isn't the only computer here so I could fix it thanks to this forum.
I'm not going to change distros but the developers should work things like this out:mad:

---

### Post by RAV TUX on 2006-08-23
> **aysiu said:**
> Just curious, as I caught it in time, but it seems a lot of people were hit.

Aysiu, if you are on line, please contact me via PM or email...

Thanks.

---

### Post by kenweill on 2006-08-23
I updated without knowing about the problems that arises to others.
Anyway, it works just fine in my system. Nothing's changed. Still works fine.

---

### Post by missmoondog on 2006-08-23
broke 3 out 7 computers yesterday. had to jump through hoops on this one, as that fix that was posted didn't quite work exactly right. got it together now though! :p 

thought it had broken a 4th one also, but that was something else. think i just clicked something to fast.

one of those 3 systems was just a plain jane intel onboard audio/video system. the others were with nvidia cards in them. was wondering if it only effected nvidia because you had to reinstall the drivers for that?

---

### Post by BuffaloX on 2006-08-23
I voted other (please explain)

I have automatic updates disabled, so it didn't brake my system.
But my wifes system broke, and she got quite upset about it. She had updated in the evening, and when she needed to use her computer next day, the system booted with X error.
Luckily she was able to access the forum from our server, and got it fixed quickly, but she was not happy about this, to put it mildly.

I guess getting the Live CD is a must...

PS
I wonder why no official statement has been made, I know this is a user forum, but I think an apology would be a good idea. Keeping totally silent about it from the devs/officials, seems a bit arrogant.

---

### Post by Brunellus on 2006-08-23
Let me take this opportunity to put this in the record for anyone who would want to run a development branch of Ubuntu (currently Edgy):

If you're mad/confused/irked by this breakage, and you have lost work/time/sleep/sanity....

NEVER.  EVER.  dist-upgrade to the development branch.

There are always a few users who do this, and are hit by this kind of issue.  If you're not prepared to live like this every week, please hold off on going to edgy or whatever future ubuntu version is in development.

I heard about the breakage and have not updated my xserver, so I'm OK, but I share a lot of the community's consternation at the dev team for letting a goof like this slip by.  I understand that the patch was intended to improve PCI-X autodetection, and that it was a good-faith attempt...but maybe something more needs to be done before patches of this nature are uploaded to the stable repos.

I should also note that this is probably the first major breakage issue in a stable branch of Ubuntu the infamous "plaintext password" fiasco in Breezy.  In the prior case, systems remained usable and security fixes were forthcoming within hours (!).  But I mention this to put it all into perspective:  an event of this type is notable for its rarity, even as it is also notable for its severity.

---

### Post by eriqk on 2006-08-23
I am going to change my morning routine after this.
I saw the notification icon and decided to do the update and then go for this forum. Heh.
Well, it b0rked X, I tried to reconfigure but to no avail, then decided to boot into XP to see if anyone else was hit. And... yes.

I didn't use the fix that was posted, couldn't be bothered really, and waited until this morning to see if the fix was in the repos yet. It was, I installed, fixed xorg.conf to fix my Wacom and was up again, as if nothing ever happened.

Easily fixed, from a user perspective, but unbelievable that this could ever happen.

Groet, Erik

---

### Post by Polygon on 2006-08-23
luckily when i updated, the updated version was already out so mine didnt break (it did freeze the computer when i tried to switch users though )

but if i had just simply turned on the computer eariler in the day, i would of gotten the bad update.

---

### Post by bigken on 2006-08-23
yet caught me out but the fix worked a treat =D>
realy feel sorry for ppl with 1 pc when this happens :(

---

### Post by sophtpaw on 2006-08-23
I take it as a matter of Faith, that updated provided by Ubuntu are good and there to update fix, maintain and polish my os.

err..err wrong

Yesterd, as per usual when i see the red button (gmt) i click to update to when i rebooted later that day, my X was borked. Never even occured to me that it could have anything to do with Ubuntu. Impeccable Faith you see. 

So i barked everywhere except up the right tree, blaiming myself for something i might have done. 

Wasted alot of time and a linux guru/friend trying to fix it with the desperate measure taken in the end to just remove X altogether!!!

I was relieved to know finally when i got on the ubuntu channels tht i wasn't the only one. 

In the end the fix was quite easy, but alot of stress, worry and time spent for nothing. 

Lesson: don't just update right away. Wait 24hrs. If there is a problem make sure it is not an Ubuntu global issue by checking the channels and forums

Amen

---

### Post by sophtpaw on 2006-08-23
Inexcusable
 By sbergman27 (1.82) on 2006-08-22 18:34:40 UTC
As a long time Fedora and then CentOS user who has been extremely impressed with Ubuntu, (enough to switch) and who recommends Ubuntu to new users, I must say that this is absolutely inexcusable. 

Considering Ubuntu's likely status as the most popular distro for newbies, this falls into the category of something that should NEVER, NEVER, EVER, EVER, EVER have been allowed to happen. 

I fixed this problem on my machine without realizing how widespread it was, and that's OK. I can handle that. It's my profession. 

But if Ubuntu is going to target newbies, they sure as heck had better practice due diligence regarding updates, ALL THE TIME AND EVERY TIME, WITHOUT FAIL. 

Ubuntu guys, a lot of water will have passed under the bridge before you gain credibility with me again. 

Sorry for the acid tone, but in light of the responsibility that Ubuntu carries, I feel it is appropriate. 

Edited 2006-08-22 18:35

---

### Post by Craig Caldwell on 2006-08-23
I waited until today to reboot. But I still broke x to get back that early ubuntu experiance when I was still...

---

### Post by Kvark on 2006-08-23
Dunno, haven't tried yet. I'll tell you a couple weeks from now when I eventaully happen to restart X for some odd reason. I guess it won't by then since the fix is out.

There should be two waves of updates that users can choose between "Right away when an update is available." or "After the first wave has discovered and solved any problems with the updates.". Then mission critical systems and newbies who can't surf the forums from the command line can avoid problems like this by being in the second wave and getting the updates a couple days or a week late.

It's ok to make mistakes but it's unacceptable to not discover a mistake like this before it goes out to the entire stable "reliable enterprise quality Dapper LTS serious competititor to RedHat"-release userbase.

---

