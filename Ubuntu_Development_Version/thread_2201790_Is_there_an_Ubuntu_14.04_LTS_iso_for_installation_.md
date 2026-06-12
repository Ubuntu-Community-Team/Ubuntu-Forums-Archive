---
title: "Is there an Ubuntu 14.04 LTS iso for installation already?"
date: 2014-01-25
forum: Ubuntu Development Version
---

### Post by renato3 on 2014-01-25
Hi guys, I'm looking forward Ubuntu 14.4 LTS. Is there an ISO for this version already?

---

### Post by QIII on 2014-01-26
*Moved to **Ubuntu + 1***

Hello!

14.04 is still in development and is not for everyday use unless you are either testing or willing to tolerate potential frequent breakage. 

You may download the daily builds [here]("http://cdimage.ubuntu.com/daily-live/current/").

Again, this is a development version.

---

### Post by renato3 on 2014-01-26
Thanks for your reply, I have some questions about it. 

1. Since it has daily builds, how do I keep my OS up to date? Can I use apt-get as usual, or do I have to download these daily builds to manually upgrade the system?
2. What is a "potential frequent breakage"? Does it mean my system will stop working out of nowhere or that I may experience some package version incompatibility, that prevent me to install new software?
3. When Ubuntu 14.04 LTS is officially released, do I have to format my computer and reinstall it using the official ISO or can I just upgrade the system and keep it running?

---

### Post by buzzingrobot on 2014-01-26
Yes, you can update as usual.

Problems may range from none to "won't boot".  It's in test mode. Updates will install new packages that are there to be tested. (Actually, there is no guarantee that any given daily image will work.)

Yes, you should be able to update into the actual release.

---

### Post by grahammechanical on 2014-01-26
To answer your questions

1) Those of us using Trusty Tahr (code name for 14.04 under development) usually update every day. Some of us use apt-get. Some of us use the Update Manager called Software Updater. After all Software Updater also has to be tested. Sometimes we get more information when the update process fails by running apt-get.

2) Trusty Tahr, like Raring Ringtail before it, is very stable. So stable as to be boring. But things can go wrong. Recently an update to a certain package broke the Ubuntu Loading process. We report these things on this section of the forum. Sometimes we can share workarounds. I have found it useful to become familiar with Recovery Mode as a means of doing updates as things can get fixed when the troublesome package is replaced by an update.

3) Once we install a development version and do regular updates it becomes the released version by release date.

It is not sensible to have a development version as your only version of Ubuntu. Create another partition and install Trusty Tahr into that. Dual/triple boot into Trusty Tahr. Then if it breaks you will still have a Ubuntu that you can use.

Get a note book (paper) and make a note of the workarounds that people suggest for fixing things and not only in this section but from other sections. Here is a good source of terminal commands.

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

Remember, sometimes/often the easiest and simplest way of fixing a broken installation is to download the latest daily image and re-install. 

Regards.

---

### Post by renato3 on 2014-01-26
Thank you very much for your attention, I understand it now :D

---

### Post by zika on 2014-01-26
> **grahammechanical said:**
> Remember, sometimes/**often** the **easiest** and simplest way of fixing a broken installation is to download the latest daily image and **re-install**.Regards.[IMG]http://www.sherv.net/cm/emoticons/hand-gestures/thumbs-down-gesture-smiley-emoticon.gif[/IMG][IMG]http://yoursmiles.org/csmile/goodbye/c0208.gif[/IMG]

---

### Post by jerrylamos on 2014-01-27
> **buzzingrobot said:**
> Yes, you can update as usual.

Problems may range from none to "won't boot".  It's in test mode. Updates will install new packages that are there to be tested. (Actually, there is no guarantee that any given daily image will work.)

Yes, you should be able to update into the actual release.

Daily build from yesterday updated with zsync:

live image would not connect to wireless.  Hmmmm.  Haven't had that trouble with Unity daily builds.  Might as well have stopped there.

install went O,K. except for no wireless internet during the install.

Booted to "busy box" would not even display "help".  DOA (dead on arrival).

Well, I have another 14.04 image I'm booted on previously installed.  Running O.K. but sure does occupy more and more disk space as updates are installed.

Since this is development, I've also got 13.04 and 13.10 partitions I can boot in case all the 14.04's go bonkers.

Yes you can update to the shipped image, but your install will still be a bunch larger than a fresh install.

Since this is development code, installs may find bugs to report.  Finding bugs is why we are running 14,04,

I'll wait a couple days, zsync to the latest image, and try again.  If the live image doesn't do wireless I'll stop there.  I've tried ubuntu-bug when ubuntu wouldn't connect to the internet and didn't have much luck getting anyone in launchpad to look at it.

---

### Post by renato3 on 2014-01-30
I can't wait for 14.04 official release :D

---

### Post by Bucky Ball on 2014-01-30
It is looking good, but as advised, don't go there to use as your main squeeze workhorse. Testing only.

Stick to a released stable. By all means, install 14.04 on another partition (or as a virtual machine), but reporting bugs and workarounds for 14.04 here is not the same as posting a regular support request in the regular sections of the forum that deal with released versions. Don't always expect answers as everyone's testing here and trying to find them. ;)

---

### Post by Bucky Ball on 2014-01-30
It is looking good, but as advised, don't go there to use as your main squeeze workhorse. Testing only.

Stick to a released stable. By all means, install 14.04 on another partition (or as a virtual machine), but reporting bugs and workarounds for 14.04 here is not the same as posting a regular support request in the regular sections of the forum that deal with released versions. Don't always expect answers as everyone's testing here and trying to find them. ;)

---

### Post by Clifford_Sarokoff on 2014-03-01
I've been using 14.4 problem free. That's because I prepared a Clonezilla Image as a backup (otherwise I would feel uncomfortable). Always better to have a plan "B"

---

### Post by 3dmatrix on 2014-03-03
What is the expected date of its official release ?

---

### Post by cariboo on 2014-03-04
The release schedule is located [here]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule").

---

### Post by Bucky Ball on 2014-03-04
See [here]("https://wiki.ubuntu.com/Releases"). Please do some searching before posting. ;)

Generally towards the end of the month.

* ninja-ed by cariboo907. ;)

---

### Post by 3dmatrix on 2014-03-07
Well, I did search before posting and that is why I asked about the date and not the month.
I expected there must be some developers from the team here who would be able to provide some expected date of release.
I wish to install Ubuntu in one of the comps. As I read 14.04 is very stable, I was wondering will it be worth waiting ? If it is early April then I can . . .  if end of April it will be too long a wait.
I hope you understand why the 'date' was asked.

---

### Post by 3dmatrix on 2014-03-07
> **cariboo907 said:**
> The release schedule is located [here]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule").

Thanks

---

### Post by bcschmerker on 2014-03-07
Thanks for keeping us apprised of how Ubuntu® Trusty Tahr&#8482; is progressing; 14.04.1-LTS should be on time, provided that a few High-priority bugs for crashes on startup are fixed.  I recently had to fresh-install 14.02b1 after routine Package upgrades borked X on my 14.01a2 test install - turns out, on my eMachines®/Acer® EL1210-09 as modified, the EVGA® GeForce® 8400 GS&#8482; half-height PCIe x16 video display adapter (nVIDIA® GT218 GPU) proved finicky about analog monitors, favoring the DVI-I port over the VGA port for primary display.  Notwithstanding existing High priority bugs for GNOME® Shell&#8482; and GNOME® Settings Daemon&#8482; (both Confirmed, SIGSEV on startup) at Launchpad&#8482;, I have run into few issues.

---

### Post by Buntu Bunny on 2014-03-08
Projected final release date is [April 17]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule").

---

### Post by 3dmatrix on 2014-03-10
Thanks

---

### Post by Chang_Doe on 2014-04-16
Hello Ubuntu community!

The [official release schedule]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule") names the 17th of April as release date for 14.04 LTS while the [list of 'other project schedules]("https://wiki.ubuntu.com/OtherProjectSchedules")' tells about the 24th as release date for the 14.04 Final Release.

Is there a difference between **14.04 LTS** and **14.04 Final Release**? I don't think so and google results don't indicate any difference as well. Even Conrad Adam (Ubuntu Release Team) [confirmed]("https://www.mail-archive.com/ubuntu-release@lists.ubuntu.com/msg02602.html") last week that the Final Release is going to be released on **17th of April**, not mentioning any differences.

---

### Post by cariboo on 2014-04-16
That listing was probably created by the Design Team who seem to have a hard time understanding what an operating system is, let alone what version we are using. :-P

---

