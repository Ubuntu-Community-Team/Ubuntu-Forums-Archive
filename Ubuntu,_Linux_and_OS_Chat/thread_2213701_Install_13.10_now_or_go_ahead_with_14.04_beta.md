---
title: "Install 13.10 now or go ahead with 14.04 beta"
date: 2014-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Dr. McKay on 2014-03-28
Here's my situation : I've recently switched from OS X to Linux and in the past two weeks, I've been trying out different linux distros.
I finally decided to install Xubuntu.
Question is, do I install 13.10 now and face the hassle of a reinstall in a couple of weeks for 14.04 (not to mention copying over all of my pictures, music, etc. once again), or do I take a leap of faith and install 14.04 beta now ?
I suppose, if I install 14.04 beta now, it will automatically update to the final version when it's released in a couple of weeks. 
I know I can upgrade from 13.10 to 14.04 without reinstalling but somehow I think there's more chance of breaking stuff than when going from 14.04 beta to 14.04 final.

What do you guys think ?

---

### Post by TheFu on 2014-03-28
Betas DO NOT upgrade - at least I wouldn't trust it.  All sorts of problems can happen, like data corruption due to program issues. The newer programs wouldn't attempt to fix that sort of issue, since there is an expectation that beta/alpha testers understand this aspect.  Betas are not meant to be used on production systems or by non-developers/testers.

Newer is not always better.

If you don't want to update (not always an "upgrade") every 6 months, stay on LTS releases for 2 yrs at a time.  LTS-to-LTS releases upgrade.  That's what I've been doing since 2008.  Stability is more important than 'new' to me.  Check my signature for more reasons to LTS.

I looked for an official statement from Canonical about beta releases being updated to the full release. Couldn't find anything official. [http://fridge.ubuntu.com/](http://fridge.ubuntu.com/) has the announcement for the latest beta release today. There is no mention of updates to GA.

[http://ubuntuforums.org/showthread.php?t=1134381](http://ubuntuforums.org/showthread.php?t=1134381) is very old, but ...   the key thing in that post that many people do not follow is to run a dist-upgrade, not just a normal upgrade.  So, my normal weekly patching remains unchanged.
* sudo aptitude update
* sudo aptitude dist-upgrade
should bring us up to current, final, GA, once released. In theory.  I will be wiping and reinstalling. Production is too important.

---

### Post by Dr. McKay on 2014-03-28
> **TheFu said:**
> Betas DO NOT upgrade.

Whoops, my bad. 
I remember reading something that a final beta release (released today) will be updated to final with just normal updates...
I'm puzzled.

---

### Post by TheFu on 2014-03-28
[http://askubuntu.com/questions/227352/upgrading-beta-to-full-version-work-without-bugs](http://askubuntu.com/questions/227352/upgrading-beta-to-full-version-work-without-bugs) says that betas are like a rolling release - not certain I believe that.  OTOH, what do I know.  With a beta, I expect data loss and plan to reload from scratch once the full, official release happens.

Reloading Linux isn't like other, commercial, OS reloads.  Backup your data, your list of apps and any machine settings you may have done, then wipe and restore fresh. Should take 40 minutes - tops.  Plus you will KNOW how to do it going forward. We all need backups and we all need to test our recovery processes.

So ... I feel the need to edit my prior post to prevent confusion.

---

### Post by pqwoerituytrueiwoq on 2014-03-28
personally i would go with the [beta]("http://cdimage.ubuntu.com/xubuntu/releases/trusty/beta-2/") or the [daily]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/"), at this point we are close enough to the release date, only major thing left is the kernel freeze if we are lucky we will get 3.14 instead of 3.13, but we are cutting it close, 3.14 should arrive this weekend and the kernel freeze is the 3ed
the beta will become a final release by installing norm updates, same thing applies to pre-alpha testing installs (assuming they still work after all that testing)

if you did install 12.10, 12.04 or 13.10 you could upgrade it to 14.04 without reinstalling
just don't overlook the xfce whiskers plugin for you panel and alt+scroll to zoom the desktop in 14.04, if you upgrade you may overlook the plugin

if you have something line 1mb dsl grab the daily on what ever day before the final release and save your time on updates

---

### Post by texpat on 2014-03-28
> if you did install 12.10, 12.04 or 13.10 you could upgrade it to 14.04 without reinstalling 
This.

Version upgrades are relatively painless. I usually wait a couple of weeks till after the release date to a) wait until the hype is over and the servers become available again and b) give the guys some time to iron out any issues that made it through quality control.

---

### Post by Dr. McKay on 2014-03-28
Ok, thx everyone, look like I've got some reading to do... ;)

---

### Post by 3rdalbum on 2014-03-28
Dr McKay, I don't know how long the other people have been here, but I have been here since 2005.

By the time an Ubuntu version hits beta, it is usually very stable. I mostly upgrade even before the beta. I am on Ubuntu 14.04 beta now and it is just fine, no problems. The beta version DOES become the release version if you run the ordinary system updates. Always has, always will. The update is quite risk-free.

By comparison, upgrades from version to version (like 13.10 to 14.04) are less well-tested because it is so time-consuming to test. I have upgraded from version to version in the past and while it often goes well, occasionally there are issues that are minor to fix, if you know how. And intimidating to figure out if you are a newcomer. You might not have a problem especially if you have only just installed 13.10, but you are correct in saying that the beta of 14.04 is safer than an in-place upgrade.

---

### Post by Dr. McKay on 2014-03-28
> **TheFu said:**
> Betas DO NOT upgrade

> **3rdalbum said:**
>  The beta version DOES become the release version if you run the ordinary system updates.

Well, I am a Linux novice. But as in my Mac days, answers to questions on forums always run off in different directions.
One of you says that BETAS DO NOT UPGRADE, you tell me that the beta version DOES become the release version.
I like 3rdalbum's answer better (i.e. that's what I thought myself) but I don't know if I can take that as a matter of fact ;-)

---

### Post by buzzingrobot on 2014-03-28
Ah, decisions, decisions.

If you install 13.10 now, you can do an in-place upgrade to 14.04 later.  That should work. Most likely will work.  But, sometimes it doesn't work, often because the user has added/changed/modified things.

Or, you could install the 14.04 beta now and simply upgrade your way to the actual release. That's what I typically do. (I don't upgrade in-place to a new release.) It's what I'm doing now. I've been on 14.04 and, generally, it's been a smooth ride. Annoyance free? No.  Crashing disaster free? Yes. 

What are the chances that installing 14.04 now will go better than upgrading 13.10 to 14.04 later?  Who knows? You'll find lots of admant advice to do one or the other. Some folks insist they won't touch a new release for weeks.  As the cliche goes, YMMV.  

Me?  I'd install the 14.04 beta, keep an eye on the Ubuntu+1 forum here, and go with it. It really is a nice release.

---

### Post by Bucky Ball on 2014-03-28
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Beta 2 will become final if you keep updating/upgrading. I did a full update/dist-upgrade on 14.04 LTS today and am running this kernel: 3.13.0-19-generic. Very stable. Not much will change now. Time for bug crushing until the final release.

Just keep doing regular updates/dist-upgrades and you'll get there. ;)

PS: The betas for a heap of flavours, including Xubuntu, were released today, . 

[http://news.softpedia.com/news/Xubuntu-14-04-LTS-Final-Beta-Trusty-Tahr-Officially-Released-Is-Based-on-Xfce-4-11-434555.shtml](http://news.softpedia.com/news/Xubuntu-14-04-LTS-Final-Beta-Trusty-Tahr-Officially-Released-Is-Based-on-Xfce-4-11-434555.shtml)

PPS: Xubuntu 14.04 LTS has three years support, not two. ;)

---

### Post by kurt18947 on 2014-03-28
I think a question would be how critical is this machine?  If downtime would cost you business/$$$, the answer would be different than if this is just a casual use machine.  I've been using Ubuntu Gnome since about Dec. 2013. I find it quite stable now but still keep current versions of any important files off-machine.  As TheFU says, reinstall is pretty quick if you have a list of add-ons and preferences at hand.

---

### Post by Dr. McKay on 2014-03-28
Upgrading from 14.04 beta to 14.04 final seems more logical to me, really. So I guess I'll be downloading the final beta tonight...
But just to be on the safe side : if I install 14.04 final beta tonight, it will update itself to 14.04 stable on 17th April, just by using the software updater in xubuntu. Right ?

On a side note : on OS X, I had Time Machine (automatic and incremental backup of my internal drive).
Anything like that for Linux ?  I have a desktop with two internal HDD's (2 x 500 gb) and a clone of the first disk on the second would be nice to have...

---

### Post by Bucky Ball on 2014-03-28
> **Dr. McKay said:**
> But just to be on the safe side : if I install 14.04 final beta tonight, it will update itself to 14.04 stable on 17th April, just by using the software updater in xubuntu. Right ?

Right.

> **Dr. McKay said:**
> On a side note : on OS X, I had Time Machine (automatic and incremental backup of my internal drive).
Anything like that for Linux ?  I have a desktop with two internal HDD's (2 x 500 gb) and a clone of the first disk on the second would be nice to have...

The stuff of another thread perhaps, but yes, there's options. I use Lucky Backup, but no idea if that's like Time Machine.

---

### Post by pqwoerituytrueiwoq on 2014-03-28
> **Dr. McKay said:**
> On a side note : on OS X, I had Time Machine (automatic and incremental backup of my internal drive).
Anything like that for Linux ?  I have a desktop with two internal HDD's (2 x 500 gb) and a clone of the first disk on the second would be nice to have...

you could use raid 1 if there is a option for that in your bios, then you would get faster read speeds in addition to having a clone of your system if one drive fails
now if you delete a important file it will be deleted on both hard drives, but i assume you want backup for hard drive failure, not user error.
raid 1 requires no extra effort than setup, and turning it off if one of you hdds fails,

if you are worried about user error look here
[http://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/](http://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/)

---

### Post by TheFu on 2014-03-28
> **Dr. McKay said:**
> On a side note : on OS X, I had Time Machine (automatic and incremental backup of my internal drive).
Anything like that for Linux ?  I have a desktop with two internal HDD's (2 x 500 gb) and a clone of the first disk on the second would be nice to have...

The closest thing to Time Machine is "**Back in Time**." It is great for personal backups ... less-than-great for system backups, though with some careful effort, it can be used.  There are 50+ ways to backup a linux system - DejaDup is the default. Never used it myself.  I use **rdiff-backup** - which is like **rsync** but with versioning and compression for older data.  rsync is an amazing tool and should become part of your toolkit as much as ssh is.

I wouldn't touch RAID before having a good, recoverable, 100% working backup solution. Backups solve all sorts of issues that RAID doesn't.

If you want specific backup help, then a new thread with a specific tool in the title is the best way.

---

### Post by buzzingrobot on 2014-03-28
There is Cronopete, which seems to attempt to directly mimic Time Machine. ([http://www.rastersoft.com/programas/cronopete.html](http://www.rastersoft.com/programas/cronopete.html)). I have not used it.

Time Machine's selling points are twofold: It's easy and it's automatic.  Backed up files can be browsed based on a snapshot of any given day.

I used Time Machine for several years. It's nice and it worked as advertised.  I haven't come across anything for Linux that is as dead-simple to set up.  But, that's not to say they're difficult. I use LuckyBackup.

If the backup tool creates and maintains the backups as standard files in a standard filesystem, then a user can browse and recover files using, if necessary, nothing besides a file manager.

If the backup tool creates and maintains the backups in some kind of compressed or archived state, and/or maintains the differences that will be applied to another file to create the full version of whatever it is you're trying to recover, then you may be  constrained to using that tool to recover files.

---

### Post by pqwoerituytrueiwoq on 2014-03-28
i remember reading about a new partition formant (btrfs) that supports snapshots available in 14.04 (not default as far as i know)
perhaps that works something like your old time machine software

---

### Post by carl4926 on 2014-03-28
I can confirm that the 14.04 beta is running perfectly here
It will update with normal updates.
I would say, it's possible you could see an odd hiccup. Just don't panic. Fixes come thru pretty quick

---

### Post by Elfy on 2014-03-28
> **pqwoerituytrueiwoq said:**
> i remember reading about a new partition formant (btrfs) that supports snapshots available in 14.04 (not default as far as i know)
perhaps that works something like your old time machine software

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs) I guess you mean

---

### Post by monkeybrain20122 on 2014-03-29
If you want the thrill of gambling whether something will break the next update then go ahead and install 14.04 beta as your working system. :) Otherwise install 13.10 and do a clean install of 14.04 in around mid july when 13.10 reaches end of life,--that is still almost 4 months of support,-- by then 14.04 will be solid ('Upgrade' takes a long time and is problematic, I always do clean install. To save you troubles you can make a separate /home partition and don't format it during install)

Some people tell you betas are very solid, that is not my experience. In fact I find most Ubuntu new releases kind of buggy especially if you, say, use proprietary graphic drivers. It takes at least a month after official release for outstanding bugs to be fixed and new found bugs to be filed. It is not at least until 2 - 3 month s after release that you have a solid OS.

When people tell you they find daily very stable it means either they don't use those buggy features or the bugs don't bother them. But you may need those features or the bugs others consider 'minor' may be a major show stopper for you (e.g the login  bug in 14.04 that remains unfixed after 100+ reports is a show stopper for me, but evidently doesn't bother the people who claimed that 14.04 alpha was 'solid') Also for some people a beta is 'very stable' if it doesn't have major breakage to the point that they can't boot, but your standard of stability for a production system may be different.

Finally, bear in mind that before release bug reports are filed only by a small community of testers, their hardware configurations and use cases are relatively limited. More bugs will be discovered after official release.

---

### Post by buzzingrobot on 2014-03-29
14.04 here now is better than 13.10 here now.  13.10 displays several bugs, once only just after the install, that 14.04 doesn't.  After that, 13.10 has been fine for me.

Upgrading duration depends, of course, on your net connection.  Mine take a minute or two.  I've been updating 14.04 once or twice a day with no issues. (Just did. Kernel is at  3.13.0-20.)

Beta code is called beta code for a reason. But, stability is relative.  Much depends on an individual's hardware, their use habits, the amount of risk they are willing to accept, and how much they modify a system. (I don't consider a typical home user's system as being a legitimate "production machine".  Mine certainly is not. If a business depends on its system, that's a production machine.) In general, I have very few problems with any contemporary Linux distribution that I tried. 

That said, if someone is problem averse and wants, for whatever reason, a system that is most likely to produce the fewest bugs and the fewest surprises, I would suggest they install 12.04.04 LTS with the enablement pack. (Outside Ubuntu, CentOS/RHEL is boringly stable. It's also well-aged and not capable of use as a contemporary desktop, sadly.)

I've become a naysayer on proprietary graphics drivers. Because they are delivered to Linux as digital blobs, kernel developers are always playing catch up with a moving target. Someone who actually needs reliable high-performance video might be better off with Windows or Apple, or moce to the most recent Intel chips and avoid the whole proprietary driver albatross altogether,  I don't need high-performance video and find my little IvyBridge chip works just fine.

But, as I said before, it's a mixed bag of possibilities. The OP might have nothing but trouble with the beta, or nothing but trouble with 13.10.

---

### Post by carl4926 on 2014-03-29
I have to concur with our mechanical friend above
14.04 is the best so far for me in the Unity range I have used over recent years.

---

### Post by manishbhoola on 2014-03-29
I am an Ubuntu user since the start. i just upgraded my 13.10 with 14.04 beta. perfect - rock solid !

---

### Post by monkeybrain20122 on 2014-03-29
> **buzzingrobot said:**
> 
I don't consider a typical home user's system as being a legitimate "production machine".  Mine certainly is not. If a business depends on its system, that's a production machine..

Well I work freelance and my laptop is my production machine  (for research, running codes, computation experiments etc) and it is also my entertainment all in one machine so I refuse to run outdated software in 12.04 (I have multiple clones and 'test' installations and am quite careful about updates even though I get the bleeding edge, running kernel 3.13.6 and mesa 10.2 now).  If you are a university researcher/grad student your laptop is probably your production machine too. Not everyone who works are employed by a 'business' sitting in front of a work station running 2004 software and MiroSoft Office, screw them business. :)

---

### Post by monkeybrain20122 on 2014-03-29
> **buzzingrobot said:**
> 
I've become a naysayer on proprietary graphics drivers. Because they are delivered to Linux as digital blobs, kernel developers are always playing catch up with a moving target. Someone who actually needs reliable high-performance video might be better off with Windows or Apple, or moce to the most recent Intel chips and avoid the whole proprietary driver albatross altogether,  I don't need high-performance video and find my little IvyBridge chip works just fine.


Well  Nvidia's support of Linux is on par with Windows (the blob, not nouveau, nouveau is decent and is useful in some cases but if you pay for a Nvidia card you may as well get the most out of it) Intel card uses open source drivers and so that leaves only Amd (I don't really know, never use one myself) Now steam is coming to linux, so sorry I completely disagree with "Someone who actually needs reliable high-performance video might be better off with Windows or Apple".

---

### Post by buzzingrobot on 2014-03-29
> **monkeybrain20122 said:**
> Well I work freelance and my laptop is my production machine  (for research, running codes etc) and it is also my entertainment all in one machine so I refuse to run outdated software in 12.04 (I have multiple clones and 'test' installations and am quite careful about updates even though I get the bleeding edge, running kernel 3.13.6 and mesa 10.2 now).  If you are a university researcher/grad student your laptop is probably your production machine too. Not everyone who works are employed by a 'business', screw them business. :)

If you're selling your time and talents, you're a business.  Sorry. :)  (I wouldn't put betas on my hardware if I was in that position, either. Or, if I was in academia.)

Yep, 12.04.04 is getting old, even with a kernel and video stack bump.  That's the tradeoff. 

(Just for jollies, I've done a 14.04 minimal install with Mate 1.6 from their repos and added the MintMenu from Mint's repo. Three days and it hasn't fallen apart.  Not that I'd recommend it...)

---

### Post by buzzingrobot on 2014-03-29
> **monkeybrain20122 said:**
> Well  Nvidia's support of Linux is on par with Windows (the blob, not nouveau, nouveau is decent and is useful in some cases but if you pay for a Nvidia card you may as well get the most out of it) Intel card uses open source drivers and so that leaves only Amd (I don't really know, never use one myself) Now steam is coming to linux, so sorry I completely disagree with "Someone who actually needs reliable high-performance video might be better off with Windows or Apple".

If the Nvidia driver works for them. Didn't always for me and it seems problematic for a good many folks. 

Have no experience with AMD in the last few years. Last one I bought was large, hot and noisy.

If someone's "high performance" video need is playing games and entertainment, that's one thing.  If paying the bills depends on it, I dunno that I'd try to persuade them to use Linux just for the sake of using Linux. Depends, I imagine, on the software they need. 

 I have a photographer friend who owns and runs a studio. She recently switched the studio from all-Windows to all-Mac.  She hired someone to spec out and manage the switch, borrowed the money for the new hardware, and passed the numbers along to her tax preparer. I wouldn't even have tried to sell her on Linux for her business.

---

### Post by Lancro on 2014-03-29
I would wait, why?, well in my case i have to wait, yes or yes, I tried to update my system to 14.04, it broke my system, I tried a clean install, It dont boots in efi mode, so... That thing that 14.04 its stable and that stuff, Im not with it, It cant upgrade a clean install of 13.10 in my case, and even cant boot the live usb (tried with dvd too), so I think they have much to do until final release, I wont try any betas, basically for 2 reasons, the first, I dont like reinstalling my system, and the second, it cant boot, so when someday, I get 14.04 working, I will stick with it at least 2 years, unless mayor changes appears, and another thing, nvidia drivers dont go like in windows..., in windows if you install a nvidia propietary driver, it doesnt last 20 seconds more to boot showing you a tty, I have been using ubuntu since 10.04, and always with nvidia drivers because of games, and always with a bug on boot, but I prefered the old bad resolition on the splash purple screen of ubuntu loading than this one of no splash screen and 20 seconds waiting for nothing.

Resuming, install 13.10 and update when the day comes, you dont want to have a bad ubuntu experience, betas are betas, for testing purpose only, if you are not looking to test anything, stick to the current version.

---

