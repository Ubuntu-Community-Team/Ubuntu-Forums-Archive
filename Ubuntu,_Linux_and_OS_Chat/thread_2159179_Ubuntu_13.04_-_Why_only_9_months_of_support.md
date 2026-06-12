---
title: "Ubuntu 13.04 - Why only 9 months of support?"
date: 2013-07-02
forum: Ubuntu, Linux and OS Chat
---

### Post by carmen2012 on 2013-07-02
I was just reading that most Ubuntu versions other then the LTS come with 18 months of support.

I was just wondering why Cannonical decided to go with 9 months of support for Ubuntu 13.04?

Thank you

---

### Post by mastablasta on 2013-07-02
First, this is not support request.

Second they moved so developers can focus more on adding and implementing new features. it's a compromise between roling release and previous release cycle. makes sense they did it, especially since new stable release comes out every 6 months.

LTS releases will have 5 years support.

---

### Post by andrew.46 on 2013-07-02
> **carmen2012 said:**
> I was just wondering why Canonical decided to go with 9 months of support for Ubuntu 13.04?

It is unusual in the Linux world to offer such a short time for support for what is still fundamentally a 'release'. Some will doubtless argue the semantics of both 'support' and 'release' :)

---

### Post by Erik1984 on 2013-07-02
Some more info: [http://www.omgubuntu.co.uk/2013/03/ubuntu-to-halve-support-window-for-regular-releases](http://www.omgubuntu.co.uk/2013/03/ubuntu-to-halve-support-window-for-regular-releases)

---

### Post by snowpine on 2013-07-02
> **carmen2012 said:**
> I was just reading that most Ubuntu versions other then the LTS come with 18 months of support.

I was just wondering why Cannonical decided to go with 9 months of support for Ubuntu 13.04?

Thank you

Because 13.10 comes out in October. That gives you 3 months to make the switch. :)
Also a long-term-support version (12.04) already exists.

---

### Post by grahammechanical on 2013-07-02
Let Mark Shuttleworth explain it.

[http://www.markshuttleworth.com/archives/1228](http://www.markshuttleworth.com/archives/1228)

[http://www.markshuttleworth.com/archives/1246](http://www.markshuttleworth.com/archives/1246)

I would not in the least be surprised if 13.10 was the last interim/standard release. 

> [COLOR=#333333][FONT=Lucida Grande]First, there&#8217;s real confusion around interim releases. Between 12.04 LTS and 14.04 LTS there will be three interim releases on our current approach, and lots of people will find that confusing.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Lucida Grande]Second, we have proven the LTS point release mechanism, which brings new hardware support and new software to the LTS releases.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Lucida Grande]Third, the daily quality story really has been impressive. The amazing work of a sizable quality team has transformed the widespread expectations of participants and contributors in Ubuntu[/FONT][/COLOR]

> [COLOR=#333333][FONT=Lucida Grande]And it&#8217;s worth looking hard at our practices to ask the question: how best to achieve that goal? Of those practices, interim releases are just as subject to evaluation and revision as any other.[/FONT][/COLOR]

Regards.

---

### Post by Elfy on 2013-07-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by buzzingrobot on 2013-07-02
The LTS point release mechanism probably hasn't received as much attention as it should.

---

### Post by craig10x on 2013-07-02
I was curious, does the LTS point releases bring in new versions of software, kernel updates and the like?  In other words, do the point releases bring in the "latest and greatest" as it were (lol) And if someone is running LTS  do they get those point upgrades automatically?

---

### Post by mips on 2013-07-02
Because after nine months it gives birth to a newer version.

---

### Post by buzzingrobot on 2013-07-02
> **craig10x said:**
> I was curious, does the LTS point releases bring in new versions of software, kernel updates and the like?  In other words, do the point releases bring in the "latest and greatest" as it were (lol) And if someone is running LTS  do they get those point upgrades automatically?

12.04 is the only example we have so far.  The bump brought in a new kernel and X, maybe a few bits more.  It's not intended to bring in new apps, etc.

there's an explanation of all this somewhere on the wiki. Believe users can opt in to the update.  (people running LTS on servers, including Canonical's commercial customers, don't want that kind of change happening automatically, if at all.)

---

### Post by craig10x on 2013-07-02
@buzzingrobot: thanks...it's just a shame that the only way you can have a "rolling" type ubuntu is by using the development...i love to get each new version of ubuntu but i am getting a bit tired of re-installing every 6 months...and from what i gather, "upgrades" are a crap-shoot, in other words they can be great or not so good...really a roll of the dice...

---

### Post by buzzingrobot on 2013-07-02
> **craig10x said:**
> ...it's just a shame that the only way you can have a "rolling" type ubuntu is by using the development...

I'm of mixed mind about commiting to a rolling release. (I'll define that as rapid turnaround of upstream releases as they happen.) On the one hand, it's fun and interesting to have the latest and greatest. On other hand, I don't really need everything to be the lastest and greatest.

Linux is mature enough that using an app that is a point release, or even an entire version, behind often makes little or no difference for me. I've used the same collection of applications that I use 90 percent of the time on distributions from 13.10 to CentOS 6.3, and a bunch with a vintage that falls in between those two. 

If I was going to try to stay current with all the upstream code on my system, I suppose I'd use Slackware and build the upstream updates myself. 

I'd like to see Ubuntu stay with the current LTS system, with a focus on backporting kernel patches, bug and security fixes, etc., much as Red Hat does with RHEL, and adding new functionality only when absolutely necessary, ideally only as a byproduct of a bug fix.

The duration of the non-LTS support cycle doesn't really affect me because I change things around often.  However, as Canonical moves to less dependence on upstream code from independent projects whose schedules aren't in synch with Ubuntu's (if they even have a schedule) to more reliance on in-house work, the potential for producing interim releases with fewer issues will increase.

---

### Post by monkeybrain2012 on 2013-07-02
> **buzzingrobot said:**
> I'm of mixed mind about commiting to a rolling release. (I'll define that as rapid turnaround of upstream releases as they happen.) On the one hand, it's fun and interesting to have the latest and greatest. On other hand, I don't really need everything to be the lastest and greatest.
.


I believe there is some middle ground between rolling the greatest and latest and get frozen for 5 years. If I am told to only use LTS then I would expect at least up to date bug fixes and some new features (not the latest, but only less old) in the point releases. I don't really need the latest and greatest from the repos for most applications. I use either ppas from the developers or compile my own, I am runing kernel 3.10 now on 12.04 which can be installed easily from mainline kernel and have mesa 9.2 and the latest nouveau from ppa which gives great graphic support even with the free driver, so my 12.04 installation is more up to date than a vanilla release of 13.04 on most things except for some system libraries and Unity.

But with things like Unity I would expect reasonably updated point releases if for no reason other than the fact that many annoying bugs were fixed upstream long ago. Now Unity 7 is gorgeous and with Compiz 0.9.10 many bugs in the previous releases are fixed. It is really smooth and stable in 13.04,  but it is also the last version of the series, it would be a shame if it dies with 13.04 in 6 months (may work with xmir in 13.10, but never know what kind of performance hit and bugs it will suffer, glad that I have a Nvidia card so it will fall back to X and I can use it for another 6 months  after 13.04 as is.) 
Meanwhile 12.04 LTS is only getting "upgrades" to another known broken version of Unity and Compiz. I am not even excited about such point-updates anymore as the versions are always stuck at 5.X, I mean, what is the point? I know as well as they that it is broken and the fixes have been released in later versions months ago.

---

### Post by tmos22 on 2013-07-03
I don't really have a problem with this. You can just upgrade when a new version is released.

---

### Post by craig10x on 2013-07-03
> **tmos22 said:**
> I don't really have a problem with this. You can just upgrade when a new version is released.

That's good with me too...but do you get smooth upgrades? (never did it before so i was wondering)...I like getting each new version...just tire of doing clean re-installs every time...

---

### Post by snowpine on 2013-07-03
Ubuntu has **always** supported upgrades, and you can read the instructions here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Always read the Upgrade Notes and Release Notes, and disable any 3rd-party software sources for the smoothest experience. :)

---

### Post by craig10x on 2013-07-03
Thanks snowpine...I will be try it (for the first time) to upgrade to 13.10 when the final comes out... I only have two 3rd party sources (ppas) Google Chrome and Oracle Java updater ppa from web8's site....
so i will disable the Chrome ppa before upgrading and re-enable afterwards, and as for the Java deb i will delete it, delete the Java and re-install Java with the newer deb that they will have for the 13.10 version...
I guess that should help it be as smooth as possible... :D

By the way, you can actually do the upgrades from the live session iso i noticed, rather then having the software updater in your current system do it...i would think that would be the better way to do it, would it not? It's one of the options that appears on the installer...you have a choice of installing the new version side by side, wipe the old version or UPGRADE your current system to the new version...

---

### Post by monkeybrain2012 on 2013-07-03
Instead of upgrade I prefer to have a separate /home partition, make a log of all installed software as in this thread [http://ubuntuforums.org/showthread.php?t=1946674](http://ubuntuforums.org/showthread.php?t=1946674)
Save a copy of my sources.list and sources.list.d and edit the version appropriately.

Then do a clean install on the root partition (/) and keep the same /home (not formatted) Then once reinstalled, replace the sources.list and sources.list.d with the saved and edited one and sudo apt-get update, then use the log in the above link to reinstall all your software, vola.

I just did that yesterday to go from Fedora 18 to Fedora 19 (the instructions are a bit different for rpm and yum, but idea is the same), after reinstalling firefox  it even kept all my open tabs (ff doesn't come with kDE spin) I just need to recompile a few packages. I saved the rpms compiled from F18, some installed again just fine, but  a few have dependency problems and need recompiling.

Upgrade takes a long time (a few hours) and something may go wrong without you even noticing, and to make sure that the upgrade doesn't screw up you have to restore the system to a pristine state(no third party software, no ppas, no proprietary driver..) well unless you are the kind of people who don't do any customization and use Ubuntu in all default settings it is a royal pain, and it still may screw up even then. In my method /home is always safe even if the install goes terribly wrong, all it takes is reboot to the live usb and  reinstall to / again, takes 20 minutes for Ubuntu (5 minutes for Fedora)

---

