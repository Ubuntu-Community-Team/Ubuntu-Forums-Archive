---
title: "Ubuntu Studio Testing"
date: 2012-08-15
forum: Ubuntu Studio
---

### Post by smartboyhw on 2012-08-15
Hello all.

I'm Howard Chan, member of the Ubuntu Studio Testing Team.

I would like to issue a call for Ubuntu Studio Testing to all of you.

There has been only a few testers (indeed, it's just me and astraljava and len-dt mainly) who helped to test Ubuntu Studio ISO images. However, as the release of Ubuntu Studio 12.10 Beta and final release images is approaching, we need a number of testers.

Please visit [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) , then click either Precise Daily or Quantal Daily (Quantal Daily is recommended since 12.10 Beta releases is coming much more sooner that 12.04.2), then select Ubuntu Studio and your favorite architecture, then follow the test cases and report the results.

Please subscribe also to [https://lists.ubuntu.com/mailman/lis...u-Studio-users](https://lists.ubuntu.com/mailman/lis...u-Studio-users) (Ubuntu Studio Users mailing list) and [https://lists.ubuntu.com/mailman/lis...u-Studio-devel](https://lists.ubuntu.com/mailman/lis...u-Studio-devel) (Ubuntu Studio developers and contributors mailing list) to receive the newest information.

You may also go to #ubuntu-testing, #ubuntustudio and #ubuntustudio-devel on irc.freenode.net to find help on Ubuntu Studio testing.

If you wish you can join the Ubuntu Studio team in [https://launchpad.net/~ubuntustudio](https://launchpad.net/~ubuntustudio) and the Ubuntu Studio Testing Team in [https://launchpad.net/~ubuntustudio-testers](https://launchpad.net/~ubuntustudio-testers) so that you can receive more info on Ubuntu Studio.

Please help us to build a better Ubuntu Studio.

Thank you and wish you a very happy testing!

Regards,
Howard Chan

---

### Post by kufey on 2012-08-16
best wishes. I will install now. thank you verymuch

---

### Post by Sylos on 2012-08-17
Hello.

I would quite like to help with the testing but I dont really know what skill level is required etc. Could you explain a bit more about what is involved?

 Also, I spent ages making my current system work so I wouldnt want to mess about installing on it (even on another partition). Would it still be productive to test on an old system with fairly minimal resources?

Cheers

---

### Post by smartboyhw on 2012-08-17
> **Sylos said:**
> Hello.
 
I would quite like to help with the testing but I dont really know what skill level is required etc. Could you explain a bit more about what is involved?
 
Also, I spent ages making my current system work so I wouldnt want to mess about installing on it (even on another partition). Would it still be productive to test on an old system with fairly minimal resources?
 
Cheers
 
Hello Sylos.
 
You don't need much technical skills: Just run the instructions.
 
Testing... It is a major part of Quality Assurance.
 
It is actually quite easy: You download the latest build of Ubuntu Studio (or just any other flavor of Ubuntu), then maybe install testdrive or Oracle VM Virtualbox, then follow the instructions in iso.qa.ubuntu.com. Most possibly after entering click "Precise Daily" (12.04.1 is more urgent), then "Ubuntu Studio" and your version of infrastructure (either amd64 or i386), then follow the testcases listed there.
 
If it runs smoothly, report a pass result on the page. If it is not, report a bug on Launchpad and list the bug number on the ISO QA Tracker page.
 
That's all really.
 
On the second question, install a VM software.
 
Regards,
Howard Chan
Ubuntu Studio Team member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by smartboyhw on 2012-08-27
Anyway, now let's switch from 12.04.1 to 12.10. Click "Quantal Daily" when testing in ISO QA Tracker. Don't click Precise Daily for now, wait till time to release 12.04.2:)

Regards,
Howard Chan
Ubuntu Studio Team Member at [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by GeneralCody on 2012-08-29
I'm up for some testing of the new images.
I use three different soundcards, one FireWire, one USB and one internal (plus the Intel HD)

Besides I use both a Wacom Intous 4 and a Wacom Bamboo, plus some MIDI Equippment.

Just pm me when the help is needed ok?

---

### Post by smartboyhw on 2012-08-29
> **GeneralCody said:**
> I'm up for some testing of the new images.
I use three different soundcards, one FireWire, one USB and one internal (plus the Intel HD)

Besides I use both a Wacom Intous 4 and a Wacom Bamboo, plus some MIDI Equippment.

Just pm me when the help is needed ok?
Well, help is ALWAYS needed:) Actually we need help NOW to test the daily images, since it is upcoming 12.10 Beta 1. However due to build failure (not good) the builds are stuck at 20120821. You can of course test it, but then no new builds for 8 days:(

Regards,
Howard Chan
Ubuntu Studio Team Member at [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by michael-wd21 on 2012-09-21
Hi,

I have just installed the Ubuntu Studio Quantal daily on my laptop. I've been using Ubuntu Studio for a few years and I like it a lot.

I'm happy to do some testing and provide feedback.

I notice that the test cases seem only to cover installation and live CD use.

Where does functional testing take place?

For example, I have noticed that my web browser preference is not being retained between sessions (I installed Google Chrome as it's my preferred browser).

Also, I installed Thunderbird and configured it for my mail server,  but now it crashes immediately on startup with an error:

> (thunderbird:2477): GLib-GIO-ERROR **: Settings schema 'org.gnome.Evolution.DefaultSources' is not installed

Trace/breakpoint trap (core dumped)


Cheers


Michael

EDIT

Fixed that Thunderbird issue, bug and fix is here

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1038047](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1038047)

---

### Post by smartboyhw on 2012-09-22
> **michael-wd21 said:**
> Hi,

I have just installed the Ubuntu Studio Quantal daily on my laptop. I've been using Ubuntu Studio for a few years and I like it a lot.

I'm happy to do some testing and provide feedback.

I notice that the test cases seem only to cover installation and live CD use.

Where does functional testing take place?

For example, I have noticed that my web browser preference is not being retained between sessions (I installed Google Chrome as it's my preferred browser).

Also, I installed Thunderbird and configured it for my mail server,  but now it crashes immediately on startup with an error:



Cheers


Michael

EDIT

Fixed that Thunderbird issue, bug and fix is here

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1038047](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1038047)

Cheers michael-wd21. Thanks for testing:)

Uh huh, I DO need people working on testcases...See [https://lists.ubuntu.com/archives/ubuntu-studio-devel/2012-September/004449.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2012-September/004449.html)

It will be about post-installation things, and I will add it to the ISO QA Tracker once I think it is good enough.

Also 12.10 Beta 2 is coming up everybody, please DO test:)

Regards,
Howard Chan

---

### Post by michael-wd21 on 2012-09-22
> **smartboyhw said:**
> Cheers michael-wd21. Thanks for testing:)

Uh huh, I DO need people working on testcases...See [https://lists.ubuntu.com/archives/ubuntu-studio-devel/2012-September/004449.html](https://lists.ubuntu.com/archives/ubuntu-studio-devel/2012-September/004449.html)

It will be about post-installation things, and I will add it to the ISO QA Tracker once I think it is good enough.

Also 12.10 Beta 2 is coming up everybody, please DO test:)

Regards,
Howard Chan

I looked at [UbuntuStudioTestCase]("https://wiki.ubuntu.com/QATeam/QuantalTestcaseUpdates/UbuntuStudioTestcase").

It says log in with the Xubuntu session. Presumably it means the Ubuntu Studio session? Is Ubuntu Studio based on Xubuntu? Maybe I should first do some reading on how Ubuntu Studio is built. Is there some design documentation somewhere? I've looked but cannot find any.

Would I be right to say the Ubuntu Studio test case is a copy of the Xubuntu test case? It strikes me the users of Ubuntu Studio will have quite different expectations for the distro.

Cheers

Michael

---

### Post by michael-wd21 on 2012-09-22
I clicked on one of the "Extra..." buttons. It started Ubuntu Software Centre, and offered to install various applications. I clicked Install. It's stuck on Tiny Ear Trainer ("Applying Changes").

> 
user@host:~$ ps -ef |  grep tiny

user    6492  2158  6 Sep22 ?        00:05:23 /usr/bin/python /usr/bin/software-center non-daw,non-sequencer,non-session-manager,mixxx,traverso,rosegarden,jkmeter,japa,muse,jackeq,chuck,jacktrip,bitmeter,freewheeling,gigtools,gjacktransport,xwax,petri-foo,ebumeter,djplay,ll-scope,scolily,milkytracker,tinyeartrainer,lmms,mhwaveedit,

It's been stuck for about an hour or so.

---

### Post by Elfy on 2012-10-19
Thanks for your help testing 12.10.

Enjoy testing 13.04 :)

Closed.

---

