---
title: "Why is there no Daily-Live Build for 06-20-2012?"
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kevpan815 on 2012-06-20
Why is there no Daily-Live Build for 06-20-2012?

---

### Post by linux12 on 2012-06-20
I dunno... so by daily, do they really mean every day?

---

### Post by thotz on 2012-06-20
Missing it too :(. Waiting for the next build :)

---

### Post by ronacc on 2012-06-20
better to wait , I zsync'd whatever is the current and it boots ok but when it gets to the drive selection for install it will not let me choose the drive/partition to install to .

---

### Post by philinux on 2012-06-20
[http://cdimage.ubuntu.com/daily/20120620/](http://cdimage.ubuntu.com/daily/20120620/)
ah soz thats alternate only.

---

### Post by philinux on 2012-06-20
> **thotz said:**
> Missing it too :(. Waiting for the next build :)

Why not just use zsync. Much better for keeping iso up to date.

---

### Post by thotz on 2012-06-20
philinux, thank you for the tip, haven't heard about this yet.

---

### Post by kevpan815 on 2012-06-20
> **philinux said:**
> Why not just use zsync. Much better for keeping iso up to date.

The problem is my Alpha 1 Build is Daily-Live, NOT Daily, I am all ready well over my Useage Limit for this month and can NOT afford to Waste any more Downloads by trying to Download the full Regular Daily Build, I need Daily-Live, NOT Daily Regular!

---

### Post by SpaceCeph on 2012-06-20
> **ronacc said:**
> better to wait , I zsync'd whatever is the current and it boots ok but when it gets to the drive selection for install it will not let me choose the drive/partition to install to .


Had the same yesterday. First I zsync'd and then downloaded regular, but was the same.

---

### Post by jerrylamos on 2012-06-20
> **ronacc said:**
> better to wait , I zsync'd whatever is the current and it boots ok but when it gets to the drive selection for install it will not let me choose the drive/partition to install to .Me too.  I opened bug [https://bugs.launchpad.net/bugs/1015578](https://bugs.launchpad.net/bugs/1015578).

Besides that, couldn't connect to WPA wireless so I drug a cable across the floor for wired.  WPA wireless couldn't configure because it wouldn't let me select the entries.  Strangely like the behavior you saw.

Jerry

p.s.  Sometimes especially near Alpha 1, Alpha 2, Beta the daily builds may stay static for a couple days.

Another reason is they're working on a bug and you don't really want a daily build with that bug.

---

### Post by ronacc on 2012-06-20
yeah my wireless network didn't come up automatically like it usually does but I was able to enter the ssid and get it up ( I don't use encryption  )

edit:  me too'd your bug .

---

### Post by balloons on 2012-06-20
Getting the builds spun up again -- they all failed to build last night due to evolution. Should be new builds shortly :-)

EDIT: Evolution still broke, still no builds..

"evolution-data-server : Breaks: libebook-1.2-12 (< 3.4) but 3.2.3-0ubuntu7 is to be installed"

---

### Post by stoneguy on 2012-06-20
Good reason to be doing incremental upgrades instead of d/l or zsync an entire iso (unless you're doing installation testing). All I've seen offered since yesterday are partial upgrades, so I've been shaking my head and walking away :(


> **guitara said:**
> Getting the builds spun up again -- they all failed to build last night due to evolution. Should be new builds shortly :-)

EDIT: Evolution still broke, still no builds..

"evolution-data-server : Breaks: libebook-1.2-12 (< 3.4) but 3.2.3-0ubuntu7 is to be installed"

---

### Post by ronacc on 2012-06-20
no guts no glory ! were here for the breakage .:p

---

### Post by jbicha on 2012-06-20
I believe [bug 1015723]("http://pad.lv/1015723") is what's blocking new daily builds.

---

### Post by stoneguy on 2012-06-20
My last apt-get upgrade resulted in[INDENT]The following packages have been kept back:
  evolution-data-server evolution-data-server-common libcamel-1.2-33 procps
  python-apt whoopsie xz-utils[/INDENT]

---

### Post by philinux on 2012-06-20
> **stoneguy said:**
> My last apt-get upgrade resulted in[INDENT]The following packages have been kept back:
  evolution-data-server evolution-data-server-common libcamel-1.2-33 procps
  python-apt whoopsie xz-utils[/INDENT]

You need to do a dist-upgrade

---

### Post by jerrylamos on 2012-06-20
Just for giggles tried amd64.  No go.  Same as i386.  Can't change partition to set file system, format, /

Kinda strange, the refusal of the change selection to work is similar to the refusal to set up wireless WPA on the startup .iso disk.  Selection doesn't allow wireless security to set WPA or anything else.

Patience, Hortense

Jerry

p.s. BTW it is Bug #1015497

---

### Post by kevpan815 on 2012-06-20
351 Updates offered with the I386 06-20-2012 Alternate Installation Build (Daily as opposed to Daily-Live) and an additional 50-100 Updates Held Back!

---

### Post by ventrical on 2012-06-20
> **ronacc said:**
> better to wait , I zsync'd whatever is the current and it boots ok but when it gets to the drive selection for install it will not let me choose the drive/partition to install to .


same here ronacc. I used "Install Ubuntu" <Something Else> and when I try to go and set the partition it will not let me choose [ext4] from the available dialog box.

---

### Post by ventrical on 2012-06-20
> **jerrylamos said:**
> Just for giggles tried amd64.  No go.  Same as i386.  Can't change partition to set file system, format, /

Kinda strange, the refusal of the change selection to work is similar to the refusal to set up wireless WPA on the startup .iso disk.  Selection doesn't allow wireless security to set WPA or anything else.

Patience, Hortense

Jerry

p.s. BTW it is Bug #1015497

same here jerry.

---

### Post by philinux on 2012-06-20
Up now. [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

---

### Post by stoneguy on 2012-06-20
Good tip. That looks like it'll run cleanly. 

When to use dist-upgrade isn't too clear. I'm already in QQ updated to Monday, so I'm not *really* upgrading to a new distro. I guess if a safe-upgrade (that's where I start) complains, I'll try dist-upgrade. Then if that objects, I can use upgrade to find out where. 

> **philinux said:**
> You need to do a dist-upgrade

---

### Post by kevpan815 on 2012-06-20
I finished the ZSync of today's Daily-Live Build (Using Alpha 1 as a Base for the ZSync) and so far I had some error messages before the DVD launched the GUI Interface, and now I have some Video Errors during Install, the bottom line: NOT fixed yet!

---

### Post by kevpan815 on 2012-06-20
Re: ZSync is still giving me 06-19-2012! Definitely NOT fixed yet, and NOT fully Uploaded either!

---

### Post by jerrylamos on 2012-06-20
> **philinux said:**
> Up now. [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Well, that link is a Lubuntu at 20 June.  From the States at 1800 EST still see 19 June for i386 and amd64.

?   I'll try later.  I looked at alternate but the zsync to that was starting at 3.1%.  Oof.

Jerry

---

### Post by ronacc on 2012-06-20
same problem wont let me select a partition for install see SS , note where the pointer is and where the highlighted entry is . do not use this partition can not be changed .

---

### Post by ronacc on 2012-06-20
I see the same as jerry , lubuntu is june 20 but ubuntu is still at june 19 .

---

### Post by kevpan815 on 2012-06-20
> **philinux said:**
> Up now. [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

Philinux, the Build that I am interested in is X86 Ubuntu Daily-Live Build, NOT Lubuntu Daily-Live, Just FYI. I will also note that Ubuntu X86 Daily Build 06-20-2012 offered me 351 Updates after install, and then another 50-100 Updates Held Back!

---

### Post by pressureman on 2012-06-20
I'm seeing similar symptoms to this "unable to select from combo box" just on normal desktop use (eg. trying to change the file type filter in a "file -> open" dialog).

You should be able to use up/down arrow keys once that combo box has focus, to cycle through the options of it.

It appears to be a GTK bug.

---

### Post by ronacc on 2012-06-20
arrow keys are not the solution in the installer , tried them > no help .

---

### Post by mc4man on 2012-06-20
> **pressureman said:**
> I'm seeing similar symptoms to this "unable to select from combo box" just on normal desktop use (eg. trying to change the file type filter in a "file -> open" dialog).

You should be able to use up/down arrow keys once that combo box has focus, to cycle through the options of it.

It appears to be a GTK bug.

Did file this the other day - didn't know if light-themes or gtk
(also maybe there is a prior?
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014481](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014481)
Edit: tried with the Adwaita theme & combo boxes are fine, so only a light-themes issue here

---

### Post by SpaceCeph on 2012-06-21
Installing todays build doesn't work too.
Can't select filesystem.

---

### Post by philinux on 2012-06-21
> **stoneguy said:**
> Good tip. That looks like it'll run cleanly. 

When to use dist-upgrade isn't too clear. I'm already in QQ updated to Monday, so I'm not *really* upgrading to a new distro. I guess if a safe-upgrade (that's where I start) complains, I'll try dist-upgrade. Then if that objects, I can use upgrade to find out where.

See man apt-get. Dist-upgrade is not upgrading to a new distribution.
[edit] also see this [http://ubuntuforums.org/showthread.php?t=1966935](http://ubuntuforums.org/showthread.php?t=1966935)

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently
           handles changing dependencies with new versions of packages; apt-get has a "smart"
           conflict resolution system, and it will attempt to upgrade the most important packages
           at the expense of less important ones if necessary. The dist-upgrade command may
           therefore remove some packages. The /etc/apt/sources.list file contains a list of
           locations from which to retrieve desired package files. See also apt_preferences(5)
           for a mechanism for overriding the general settings for individual packages.


---

### Post by jppr on 2012-06-21
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by jerrylamos on 2012-06-21
> **SpaceCeph said:**
> Installing todays build doesn't work too.
Can't select filesystem.

Any clue from Phillinux or Cariboo907 or Mc4man or Ventrical or whoever what's going on?

Is development working on a bug, or is it that they don't see a problem?

Same problem as SpaceCeph's quote from Monday, Tuesday, Wednesday no update, now SpaceCeph reports Thursday?

Thanks, Jerry

p.s  I'm having fits with WPA on my wireless, similar trouble, selection menu won't come up, very sluggish response to selection bars if at all, wireless refuses to conect, network won't connect, then plug in wire and bopopm! wireless connects right away, disconnect wired, wireless runs fine now.  Just won't start by itself.  I entered a bug a while ago I suspect i won't get anywhee until the "can't select" problem gets some attention.

---

### Post by SpaceCeph on 2012-06-21
Oh, there are three builds from today. I'll try the last one and report back.

---

### Post by pressureman on 2012-06-21
I'm not quite sure I understand exactly what's going on here. Are you people nuking your systems *every single day*, and trying to install a daily install each time? That sounds like a real hoot, but you will run into a lot of transient bugs. I'm fairly sure that the developers know about these bugs, but they're not a huge priority, since it's quite likely that a) a daily installer from a few days earlier was OK, and b) the bugs will be fixed in a few days when a new build comes out.

As ever, you could always try the alternate installer, which has far less to go wrong with it, since it's based on the very mature Debian installer (text mode). It's not hard to use, trust me.

Why not get a stable install running, and then just do a daily 'apt-get upgrade' ? That way, you'll have a reasonably stable system to work on, and you'll be able to help test the applications themselves, not just Ubiquity installer. IMHO, the installer is a much lower priority for testing than the applications themselves. *Most people* generally don't reinstall their systems each day. People do however apply system updates every few days. The installer really only needs to be stable and bug-free for each alpha, beta and of course final release. Anything in between those is really a case of "use at your own risk".

I've been running my current system since *before* Precise was released.... that's right, it started as an alpha install during the Precise testing phase. I haven't done a clean install on this box since February, because I *haven't needed to*. I may do a clean install sometime closer to the release date of Quantal, but most likely from a tagged alpha or beta release. I really don't find it surprising at all that daily installers give people problems (especially the live CD graphical installer).

---

### Post by SpaceCeph on 2012-06-21
Build.3 didn't even boot for me.

---

### Post by balloons on 2012-06-21
The archive is in a not so happy state -- if you guys are having failures (and obviously you are), please feel free to add those results on the tracker.

Ohh and as always, please bring to my attention any critical bugs or issues -- I can help get the bug more attention if needed, and I like to subscribe and keep it on my radar. Thanks!

---

### Post by jbicha on 2012-06-21
pressureman, actually the goal these days is for every daily image to work, therefore testing installation from the images is useful.

In the case of the broken dropdown lists, that won't suddenly start working in the daily builds until [bug 1015497]("http://pad.lv/1015497") is fixed.

---

### Post by pressureman on 2012-06-21
> **jbicha said:**
> pressureman, actually the goal these days is for every daily image to work, therefore testing installation from the images is useful.

If that's the case, wouldn't it be even more useful to implement automated testing, or some kind of CI? I know it doesn't account for the variety of funky hardware out there, but it would catch things like the GTK/theme bug that is preventing drop-down list selection.

---

### Post by ronacc on 2012-06-21
> **pressureman said:**
> If that's the case, wouldn't it be even more useful to implement automated testing, or some kind of CI? I know it doesn't account for the variety of funky hardware out there, but it would catch things like the GTK/theme bug that is preventing drop-down list selection.

it would still require the .iso to be put out for real world testing so the automated test would be redundant . most of us who test the daily's have at least multiple partitions so it isn't necessary to "nuke" anything to try a daily . as long as SDC will make a bootable stick it isn't even necesssary to waste a dvd .

---

### Post by philinux on 2012-06-21
> **ronacc said:**
> it would still require the .iso to be put out for real world testing so the automated test would be redundant . most of us who test the daily's have at least multiple partitions so it isn't necessary to "nuke" anything to try a daily . as long as SDC will make a bootable stick it isn't even necesssary to waste a dvd .

Plus with zsync and usb stick it's not that much of an effort.

---

### Post by balloons on 2012-06-21
> **pressureman said:**
> If that's the case, wouldn't it be even more useful to implement automated testing, or some kind of CI? I know it doesn't account for the variety of funky hardware out there, but it would catch things like the GTK/theme bug that is preventing drop-down list selection.

Sadly these "visual" bugs would be the hardest to automate for, so this kind of bug is a good example of how manual testing can fill the gap. Now, packages not installing, etc, that should be handled via automated installer testing.

---

### Post by jerrylamos on 2012-06-21
> **guitara said:**
> Sadly these "visual" bugs would be the hardest to automate for, so this kind of bug is a good example of how manual testing can fill the gap. Now, packages not installing, etc, that should be handled via automated installer testing.I thought that's what we're for.  Sometimes its a bit difficult to pin down a bug espeically with masses of updates coming in.

Jerry

---

### Post by pressureman on 2012-06-21
> **ronacc said:**
> it would still require the .iso to be put out for real world testing so the automated test would be redundant . most of us who test the daily's have at least multiple partitions so it isn't necessary to "nuke" anything to try a daily . as long as SDC will make a bootable stick it isn't even necesssary to waste a dvd .

Automated testing is never redundant. I can't tell you how often a unit test has alerted me to the fact that I've broken something, whilst I've been ploughing ahead on some other part of the code. Often a unit test failing is the first indication that a bug has crept into the code, long before any end users notice it.... this of course does require disciplined TDD, and taking the time to actually write unit tests.

> **guitara said:**
> Sadly these "visual" bugs would be the hardest to automate for, so this kind of bug is a good example of how manual testing can fill the gap. Now, packages not installing, etc, that should be handled via automated installer testing.

I used to think that automated testing of a user interface was near impossible too, but Selenium IDE ([http://seleniumhq.org/projects/ide/](http://seleniumhq.org/projects/ide/)) can do that for scripted/dynamic web pages... which are essentially a user interface. Maybe something similar exists for automated testing of GTK user interfaces.

---

### Post by kevpan815 on 2012-06-21
ZSync for Today's 06212012.3 Ubuntu NOT working at all! Several Failed Attempts! Download Server Very Slow!

---

### Post by ronacc on 2012-06-21
yes servers very slow , I both zsync'd the .2 and .3 and d/l'd the .3 because I was suspicious of the zsync'd .3  so it took quite awhile and was worthless in the end because even the .3 wouldn't let me select a partition to install to .

---

### Post by balloons on 2012-06-21
> **pressureman said:**
> Automated testing is never redundant. I can't tell you how often a unit test has alerted me to the fact that I've broken something, whilst I've been ploughing ahead on some other part of the code. Often a unit test failing is the first indication that a bug has crept into the code, long before any end users notice it.... this of course does require disciplined TDD, and taking the time to actually write unit tests.



I used to think that automated testing of a user interface was near impossible too, but Selenium IDE ([http://seleniumhq.org/projects/ide/](http://seleniumhq.org/projects/ide/)) can do that for scripted/dynamic web pages... which are essentially a user interface. Maybe something similar exists for automated testing of GTK user interfaces.

It's not impossible -- some of the members here pointed this awesome tool out to me. Give it a try:

[http://sikuli.org/](http://sikuli.org/)

This combined with UTAH ([https://launchpad.net/utah](https://launchpad.net/utah)) might just be the ticket to automating some of this. I know the good folks here are capable of demonstrating something cool in this area. I might try and announce the idea on a broader scale. Show me what you can cook up!

---

### Post by balloons on 2012-06-21
> **jerrylamos said:**
> I thought that's what we're for.  Sometimes its a bit difficult to pin down a bug espeically with masses of updates coming in.

Jerry

Yes, Jerry the funny thing about automated tests are someone still has to interpret the results -- the capabilities of your brain are still very handy and necessary tools to have! When the archive gets flooded with stuff and everything is broke, you need to be able to separate the wheat from the chaff. You need you :-)

---

### Post by kevpan815 on 2012-06-21
> **ronacc said:**
> yes servers very slow , I both zsync'd the .2 and .3 and d/l'd the .3 because I was suspicious of the zsync'd .3  so it took quite awhile and was worthless in the end because even the .3 wouldn't let me select a partition to install to .

Yeah, ZSync is running way too slow at the momment so I am going to try the full .5 Download from Windows 7 using my Verizon Wireless 551L 4G LTE USB Modem (which does NOT work with Ubuntu) and see if I have any better luck.

---

### Post by ronacc on 2012-06-21
you probablu won't have any better luck with the full d/l , I didn't , 3+ hrs for a little over 700 mb , usually takes me about 30 min .

---

### Post by kevpan815 on 2012-06-21
> **ronacc said:**
> you probablu won't have any better luck with the full d/l , I didn't , 3+ hrs for a little over 700 mb , usually takes me about 30 min .

Actually, the full download (on Verizon Wireless 551L 4G LTE USB Modem as opposed to ZSync on Regular 3G on my IPhone 4S's Personal Hotspot) went at 700 KB's a second and only took 30 minutes or so. It was the install itself that took forever (not to mention the fact that I had to step away from the compuer for dinner), but it worked, 20120621.5 Daily-Live is installed and working, so I am marking this Thread as Solved. Just FYI.

---

### Post by ronacc on 2012-06-21
hmm they got all the way up to .5 :D I guess I'll d/l 1 more . I'll try zsync first .

---

### Post by jerrylamos on 2012-06-21
> **kevpan815 said:**
>  It was the install itself that took forever (not to mention the fact that I had to step away from the compuer for dinner), but it worked, 20120621.5 Daily-Live is installed and working, so I am marking this Thread as Solved. Just FYI.On install attempt I still can't get by the "Change" drop down list to set filesystem type, and root.

All my disks are multiboot and I have a partition selected ahead of time.

How did you install, "whole disk" or "alongside" or "something else"?

Thanks, Jerry

---

### Post by kevpan815 on 2012-06-21
> **jerrylamos said:**
> On install attempt I still can't get by the "Change" drop down list to set filesystem type, and root.

All my disks are multiboot and I have a partition selected ahead of time.

How did you install, "whole disk" or "alongside" or "something else"?

Thanks, Jerry

Whole Disk, which worked just fine Jerry. I am no longer Dual Booting as I discovered that Dual Booting was leaving behind the Swap Drive's on each Reinstall as a Dual Boot with Windows XP Service Pack 3! Just FYI.

---

### Post by jerrylamos on 2012-06-21
> **kevpan815 said:**
> Whole Disk, which worked just fine Jerry. I am no longer Dual Booting as I discovered that Dual Booting was leaving behind the Swap Drive's on each Reinstall as a Dual Boot with Windows XP Service Pack 3! Just FYI.
A couple of my pc's are linux only with one swap partition per drive.  Another one has Windoze...7 on it, as far as I can tell ubuntu leaves it alone.

On a drive I usually have a couple Alpha's alternating in case one is busted plus a precise for recovery and a library of commonly used routines, documents, etc.  All backed up.

Jerry

---

### Post by kevpan815 on 2012-06-22
> **jerrylamos said:**
> A couple of my pc's are linux only with one swap partition per drive.  Another one has Windoze...7 on it, as far as I can tell ubuntu leaves it alone.

On a drive I usually have a couple Alpha's alternating in case one is busted plus a precise for recovery and a library of commonly used routines, documents, etc.  All backed up.

Jerry

Jerry, I used the Hard Drive Status App, and found that out of my 80 GB's Allocated for Ubuntu, only 71.5 GB was actually being used for Ubuntu.

I also discovered that out of the Remaining Hard Disk Drive Space, I had 4 Ubuntu Swap Drives, 1 Current, the other 3 from Old Ubuntu Installs.

---

### Post by cariboo on 2012-06-22
You only need one swap partition, no matter how many hard drives you have. My system has two 250 GiB hard drives, and only one swap partition.

---

### Post by kevpan815 on 2012-06-22
> **cariboo907 said:**
> You only need one swap partition, no matter how many hard drives you have. My system has two 250 GiB hard drives, and only one swap partition.

Cariboo907, I was just letting Jerry know that the Hard Disk Drive Partitioner was NOT clearing out the old Swap DriveS on my system as it was supposed to. That was the only purpose of my original post. I am well aware that you only need one Swap Drive.

---

### Post by jerrylamos on 2012-06-22
> **kevpan815 said:**
> Cariboo907, I was just letting Jerry know that the Hard Disk Drive Partitioner was NOT clearing out the old Swap DriveS on my system as it was supposed to. That was the only purpose of my original post. I am well aware that you only need one Swap Drive.Perhaps you are using one of the "automagic" set-ups such as "whole drive" and "alongside".  Good someone is testing them, I don't.

I was able to install 22 June daly build today by issuing:
gsettings set org.gnome.desktop.interface gtk-theme Adwaita
which is a wierd desktop, some text is black on black,
but drop down menus really work.
Have to mouse-over some areas to read the text.

Hope they don't change Adwaita.  What's the default gtk-theme?  The one that's busted?

Thanks, Jerry

---

