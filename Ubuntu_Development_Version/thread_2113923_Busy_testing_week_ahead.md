---
title: "Busy testing week ahead"
date: 2013-02-08
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-02-08
Lots of stuff going on; Nicholas, or someone, is uploading the 12.04.2 iso-testing images as I type (not all images are ready yet):

[http://iso.qa.ubuntu.com/qatracker/milestones/254/builds](http://iso.qa.ubuntu.com/qatracker/milestones/254/builds)

And Cadence week #6 begins tomorrow:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

And both Edubuntu and Kubuntu have a Raring Alpha 2 dropping on the 14th:

[http://iso.qa.ubuntu.com/qatracker/milestones/255/builds](http://iso.qa.ubuntu.com/qatracker/milestones/255/builds)

So it's a good time to test and report bugs on the QA tracker :D

I have a few Precise bugs that I'm going to try and focus on first ........ hope I have time to get in some Lubuntu Cadence testing also :guitar:

---

### Post by kansasnoob on 2013-02-08
Wow, I see they've updated the Raring i386 mini.iso:

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/37095/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/37095/downloads)

And even the Precise mini.iso:

[http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/36919/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/36919/downloads)

So maybe we should call it, "name your poison" week :lolflag:

---

### Post by ventrical on 2013-02-08
I test everyday in some capacity or another.

 Thanks for the heads up.

---

### Post by kansasnoob on 2013-02-08
> **ventrical said:**
> I test everyday in some capacity or another.

 Thanks for the heads up.

Do you record your bugs on the QA Tracker? I really do find that to increase the bug heat substantially :)

Of course there is never a 100% guarantee that any bug will be fixed but I believe no effort is truly wasted.

---

### Post by kansasnoob on 2013-02-08
I think my two hottest Precise bugs are:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1101073](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1101073)

I wrote a sort of "test case" for that (step #4):

[http://ubuntuforums.org/showpost.php?p=12463934&postcount=31](http://ubuntuforums.org/showpost.php?p=12463934&postcount=31)

And:

[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454)

I have a couple other pet peeves but they're fairly easy to work around:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089)

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/988290)

---

### Post by kansasnoob on 2013-02-08
My hottest bug for Raring is:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

Everything I use in Lubuntu has just been working other than that :D

---

### Post by kevpan815 on 2013-02-09
> **kansasnoob said:**
> Lots of stuff going on; Nicholas, or someone, is uploading the 12.04.2 iso-testing images as I type (not all images are ready yet):

[http://iso.qa.ubuntu.com/qatracker/milestones/254/builds](http://iso.qa.ubuntu.com/qatracker/milestones/254/builds)

And Cadence week #6 begins tomorrow:

[https://wiki.ubuntu.com/QATeam/Cadence/Raring](https://wiki.ubuntu.com/QATeam/Cadence/Raring)

And both Edubuntu and Kubuntu have a Raring Alpha 2 dropping on the 14th:

[http://iso.qa.ubuntu.com/qatracker/milestones/255/builds](http://iso.qa.ubuntu.com/qatracker/milestones/255/builds)

So it's a good time to test and report bugs on the QA tracker :D

I have a few Precise bugs that I'm going to try and focus on first ........ hope I have time to get in some Lubuntu Cadence testing also :guitar:

If you notice: the Website says NOT to begin 12.04.2 Testing yet, just to clarify things, so no one jumps the gun and has a False Start. :-)

Correction: It says to start testing 12.04.2 BUT Do NOT Start 13.04 Alpha 2 just yet, my Mistake. :-)

---

### Post by kevpan815 on 2013-02-09
> **kevpan815 said:**
> If you notice: the Website says NOT to begin 12.04.2 Testing yet, just to clarify things, so no one jumps the gun and has a False Start. :-)

Correction: It says to start testing 12.04.2 BUT Do NOT Start 13.04 Alpha 2 just yet, my Mistake. :-)

Sorry guys for the Mix Up, Avast 8.0 Public Beta is making Windows 7 run so SLOW that I am having to use my Sprint Apple IPhone 5 with 4G LTE just to post here! :-(

---

### Post by grahammechanical on 2013-02-09
I have just run update-grub on one of my Raring installs (trying to install Ubuntu on a btrfs formatted partition messed up the Grub menu - another story) and update-grub tells me that my 2 x 12.04.1 installs are now 12.04.2 LTS.

Update: I have now booted into one of those 12.04 installs and lsb_release -a says 12.04.2 LTS. It still has Grub 1.99 and Unity 5.12. A decision has been made not to update the logo images. So, do not expect to see any reference to 12.04.2 in GUI utilities. In fact the 12.04.1 logos were replaced by 12.04 logos in an update the other day.

Regards.

---

### Post by kansasnoob on 2013-02-09
> **grahammechanical said:**
> I have just run update-grub on one of my Raring installs (trying to install Ubuntu on a btrfs formatted partition messed up the Grub menu - another story) and update-grub tells me that my 2 x 12.04.1 installs are now 12.04.2 LTS.

Update: I have now booted into one of those 12.04 installs and lsb_release -a says 12.04.2 LTS. It still has Grub 1.99 and Unity 5.12. A decision has been made not to update the logo images. So, do not expect to see any reference to 12.04.2 in GUI utilities. In fact the 12.04.1 logos were replaced by 12.04 logos in an update the other day.

Regards.

That came up earlier:

[http://ubuntuforums.org/showpost.php?p=12497190&postcount=47](http://ubuntuforums.org/showpost.php?p=12497190&postcount=47)

---

### Post by jerrylamos on 2013-02-09
Ringtail 3.8.0-5 here, updated as of yesterday.  Slowed down and stopped only thing that worked was power off.  Booted O.K. a little slow, did today's update and running O.K.  Nothing in /var/log/crash.

Usual problems with wireless WPA encryption automatically disconnects on boot.  Manual connect required every time.  LTS automatically connects as it should....launchpad bug written weeks ago, it's a problem with NM scripts changed since LTS.  My guess, none of the NM people are looking at Launchpad.  Occurs on netbook and notebook.  My tower is wired.

Also running LTS.  I zsync'd 12.04 daily live current this month, plus daily apt-get updates.  They say 12.04.2 running fine on netbook, notebook, tpwer.

---

### Post by screaminj3sus on 2013-02-09
ubuntu online accounts seems to be mostly broken in raring: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449)

The only accounts that actually work are facebook google twitter and windows live

---

### Post by kansasnoob on 2013-02-09
> **kevpan815 said:**
> If you notice: the Website says NOT to begin 12.04.2 Testing yet, just to clarify things, so no one jumps the gun and has a False Start. :-)

Correction: It says to start testing 12.04.2 BUT Do NOT Start 13.04 Alpha 2 just yet, my Mistake. :-)

I guess I should more clearly state my reasoning behind posting notices like this ;)

I've truly found that getting the QA tag added to a bug report is always beneficial. That doesn't mean there's a guarantee that a bug will be fixed, but it does at least get the bug on the radar *so-to-speak* :D

The best thing is to subscribe to the tests you're truly willing to perform at the QA Tracker, then you'll get a notification when the milestone images are ready to test.

But "Cadence Testing" changed things. Since there are no actual "alpha" images for most flavors you just have to depend on mailing lists and the posted schedule.

Right now I'm much more concerned with 12.04.2 than I am with Raring because Lucid (desktop version) will soon reach EOL, so we'll have a lot more users upgrading to Precise :)

---

### Post by Cavsfan on 2013-02-09
> **screaminj3sus said:**
> ubuntu online accounts seems to be mostly broken in raring: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1116449)

The only accounts that actually work are facebook google twitter and windows live

Good luck on them fixing that with it affecting 2 people. They are not even going to fix the read only file system in recovery. :-(
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454)

---

### Post by kansasnoob on 2013-02-09
> **Cavsfan said:**
> Good luck on them fixing that with it affecting 2 people. They are not even going to fix the read only file system in recovery. :-(
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454)

That is a very sad bug :(

Supposedly it's maintained:

[https://launchpad.net/ubuntu/+source/friendly-recovery](https://launchpad.net/ubuntu/+source/friendly-recovery)

But you'll notice there are 28 "new" bugs.

---

### Post by smartboyhw on 2013-02-09
BTW, the Ubuntu Quality Assurance team will have quite a few sessions about submitting test results and ISO tests and such.

11th February, 2013 (Monday) 18:00-19:00 UTC Nicholas Skaggs (balloons) will be at #ubuntu-quality on irc.freenode.net and also on Ubuntu on Air! to demonstrate the process of going through the testcases.

13th February, 2013 (Wednesday) 13:00-15:00 UTC Howard Chan (smartboyhw, aka me) will be at #ubuntu-classroom and #ubuntu-classroom-chat on irc.freenode.net to host the finale of a series of QA Team Classroom sessions. It will be about ISO testing, and I will demonstrate how to test the 12.04.2 and the 13.04 Alpha 2 images. Nicholas, Phill Whiteside (phillw) and others will also be on #ubuntu-classroom-chat to answer questions from the community.

14th February, 2013 (Thursday) **Ubuntu 12.04.2 and Kubuntu/Edubuntu 13.04 Alpha 2 release day** 14:00-15:00 UTC Nicholas will be at #ubuntu-quality to help everybody submit their test results up to the QA Trackers. **Everyone try to be at the Ubuntu QA Team IRC channels on that time**, since final testing of 12.04.2 and 13.04 Alpha 2 should be on that time.

(I remember testing 12.04.1 alternates for Xubuntu at 14:00-15:00 UTC on release day so that it can be released)

Just a friendly reminder: Lubuntu will not be participating in 12.04.2 LTS since Lubuntu is not supporting LTS releases. Only Edubuntu/Kubuntu will be having 13.04 Alpha 2 releases.

Have a great time testing, [COLOR=Red]a happy Chinese New Year of the Snake and a happy Valentine's day on 12.04.2 and 13.04 Alpha 2 release day!!!!!!

[COLOR=Black]smartboyhw[/COLOR]
[/COLOR]

---

### Post by jerrylamos on 2013-02-10
> **kansasnoob said:**
> I guess I should more clearly state my reasoning behind posting notices like this ;)

I've truly found that getting the QA tag added to a bug report is always beneficial. That doesn't mean there's a guarantee that a bug will be fixed, but it does at least get the bug on the radar *so-to-speak* :D

The best thing is to subscribe to the tests you're truly willing to perform at the QA Tracker, then you'll get a notification when the milestone images are ready to test.more users upgrading to Precise :)

I get bugs that aren't in the prescribed QA tests, write launchpad bugs, which aren't looked at by the relevant developer(s).  How do you put a QA tag on bugs that aren't in the prescribed list?

Thanks, Jerry

---

### Post by kansasnoob on 2013-02-10
> **jerrylamos said:**
> I get bugs that aren't in the prescribed QA tests, write launchpad bugs, which aren't looked at by the relevant developer(s).  How do you put a QA tag on bugs that aren't in the prescribed list?

Thanks, Jerry

If it regards a faulty app the basic [live session testcase]("http://iso.qa.ubuntu.com/qatracker/testcases/1303/info") includes:

> Use and execute the default apps ..... 
**[COLOR="Red"]All apps should function without error[/COLOR]**

So, just as an example, I use abiword which is a default app in Xubuntu so I can test the 12.04.2 Xubuntu live image to record these:

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/1019621)

[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/960089)

If it involves 'ubiquity' that's a problem I think we need to talk to Nicholas about because the installer does now offer options that are not adequately included in the testcases:

[http://ubuntuforums.org/showpost.php?p=12463934&postcount=31](http://ubuntuforums.org/showpost.php?p=12463934&postcount=31)

---

### Post by Cavsfan on 2013-02-10
> **kansasnoob said:**
> That is a very sad bug :(

Supposedly it's maintained:

[https://launchpad.net/ubuntu/+source/friendly-recovery](https://launchpad.net/ubuntu/+source/friendly-recovery)

But you'll notice there are 28 "new" bugs.

Ouch 28 bugs and this is an LTS. I hope that part definitely gets fixed.

---

### Post by kansasnoob on 2013-02-10
> **Cavsfan said:**
> Ouch 28 bugs and this is an LTS. I hope that part definitely gets fixed.

The "28 new bugs" effect more than just Precise, but it's aggravating when a bug like that persists :(

Given the fact that the package name is 'friendly-recovery' they should at least consider a name change :biggrin:

---

### Post by grahammechanical on 2013-02-10
> How do you put a QA tag on bugs that aren't in the prescribed list?

We cannot report a test failure on the QA tracker without including a Launchpad bug number. The system will not let you submit. We can submit our own bur report in Launchpad or search for a previous report of the bug and included that number in the QA tracker failed test result. This will put a 'reported on the QA tracker' tag on the bug.

Regards.

---

### Post by VinDSL on 2013-02-10
> **kansasnoob said:**
> The "28 new bugs" effect more than just Precise, but it's aggravating when a bug like that persists :(

Given the fact that the package name is 'friendly-recovery' they should at least consider a name change :biggrin:
Bwahahaha!  First LoL_of_the_day.

Thanks, for that!  :D

---

### Post by kansasnoob on 2013-02-10
> **grahammechanical said:**
> We cannot report a test failure on the QA tracker without including a Launchpad bug number. The system will not let you submit. We can submit our own bur report in Launchpad or search for a previous report of the bug and included that number in the QA tracker failed test result. This will put a 'reported on the QA tracker' tag on the bug.

Regards.

I think he was talking about test-cases that truly don't exist, but I'm not sure.

There are corner issues that are hard to find a valid reason for reporting on the QA Tracker but I can assure you that Nicholas is trying his best to get things fixed in QA.

As part of my testing I've installed 10.04.4 three times to perform upgrade tests and trust me ............... that was NO picnic!

There have been both improvements and regressions :D

---

### Post by mc4man on 2013-02-10
> **kansasnoob said:**
> 

There are corner issues that are hard to find a valid reason for reporting on the QA Tracker but I can assure you that Nicholas is trying his best to get things fixed in QA.


Don't think it's only "corner"  cases, many of the tests are so basic that they don't fail & don't always represent current state of an app.
(current ex. is the nautilus tests - was able to fail nautilus on 2 tests by lightly re-interpreting the tests while I believe staying within bounds.

There is a 3rd fail but won't report as it strays too far, - the search test.
(the truth is that search in nautilus is bad, but the test only looks at finding a file/folder in current dir. If the testcase searched for the file inside the 'test' folder, (moveme.txt),  it would fail.

---

### Post by kansasnoob on 2013-02-10
> **mc4man said:**
> Don't think it's only "corner"  cases, many of the tests are so basic that they don't fail & don't always represent current state of an app.
(current ex. is the nautilus tests - was able to fail nautilus on 2 tests by lightly re-interpreting the tests while I believe staying within bounds.

There is a 3rd fail but won't report as it strays too far, - the search test.
(the truth is that search in nautilus is bad, but the test only looks at finding a file/folder in current dir. If the testcase searched for the file inside the 'test' folder, (moveme.txt),  it would fail.

You're right ...... some test reporting is either non-existent, redundant, or inadequate. But I read enough of the QA posts on my Lubuntu QA mailing list that I know work is in progress :D

---

### Post by kansasnoob on 2013-02-11
> **mc4man said:**
> Don't think it's only "corner"  cases, many of the tests are so basic that they don't fail & don't always represent current state of an app.
(current ex. is the nautilus tests - was able to fail nautilus on 2 tests by lightly re-interpreting the tests while I believe staying within bounds.

There is a 3rd fail but won't report as it strays too far, - the search test.
(the truth is that search in nautilus is bad, but the test only looks at finding a file/folder in current dir. If the testcase searched for the file inside the 'test' folder, (moveme.txt),  it would fail.

I just thought to add that most (or all) of the iso-tests include a bug reporting link for the specific test case:

[ATTACH]231278[/ATTACH]

I haven't looked at the individual app testcases because I'm usually just busy with ubiquity :(

But I wonder if there is a testcase for 'friendly-recovery' :confused:

---

### Post by kansasnoob on 2013-02-11
I see this AM that some of the 12.04.2 images are already being updated, but still no upgrade testing. So things are definitely still in progress :D

---

### Post by kansasnoob on 2013-02-11
Proof that communication does work :D

I sent a PM to Nicholas and quickly got a reply:

> No, your not being impatient -- looks like these were not automatically
added :-( I'll get them on the tracker and ping you when ready. Thanks
Lance!


Nicholas

On 02/11/2013 02:16 PM, Lance wrote:
> Sorry to be a nuisance but I've been doing some 12.04.2 iso testing and I'm a bit concerned about the lack of Lucid-->Precise and Oneiric-->Precise upgrade test-cases.
>
> Maybe I'm just being impatient but I wanted to check with you to be sure it wasn't overlooked. I'm prepped and ready to run both tests when they pop up on the tracker.
>
> Many thanks,
>
> Lance

---

### Post by balloons on 2013-02-11
> **mc4man said:**
> Don't think it's only "corner"  cases, many of the tests are so basic that they don't fail & don't always represent current state of an app.
(current ex. is the nautilus tests - was able to fail nautilus on 2 tests by lightly re-interpreting the tests while I believe staying within bounds.

There is a 3rd fail but won't report as it strays too far, - the search test.
(the truth is that search in nautilus is bad, but the test only looks at finding a file/folder in current dir. If the testcase searched for the file inside the 'test' folder, (moveme.txt),  it would fail.

mc4man, I saw your bug reports and test results. First, thanks for testing! It's obvious you are thorough and you write good bugs.

Second, I agree with you on the testcases. If you were able to see my livestream of cadence testing today I went through the same nautilus cases. The video didn't come out so high-res, but you might enjoy hearing my thoughts while I test anyway. [Here's a link to it]("https://www.youtube.com/watch?v=aOkbMiyJIbI&feature=plcp").

At several points I went "further" than the test called for and explored and tested the features. That's part of testing. But, that said, I want you to know you can report bugs against the testcases, and even go further by helping to write/update them. So all those "extra steps" we take and explore can be rolled back into the testcase. Check these links out:

[https://wiki.ubuntu.com/QATeam/ContributingTestcases/Manual](https://wiki.ubuntu.com/QATeam/ContributingTestcases/Manual)
[https://launchpad.net/ubuntu-manual-tests](https://launchpad.net/ubuntu-manual-tests)

Indeed, I filed [this against the nautilus testcase]("https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1122293") today after running through it. It was just updated by another community member to bring it inline with many of the changes from the old test. It's already SO much better, and we can take it further. Lets iterate together on this stuff!

---

### Post by mc4man on 2013-02-11
> **guitara said:**
> 

Indeed, I filed [this against the nautilus testcase]("https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1122293") today after running through it. It was just updated by another community member to bring it inline with many of the changes from the old test. It's already SO much better, and we can take it further. Lets iterate together on this stuff!
I did notice that (black vs. blank),  but didn't what to seem too picky by mentioning.
The other thing I noticed was the nautilus testcase on creating a empty docu - 
 > In Home folder right click on a blank section and select **Create Document**, Empty Document. Name the resulting file 'moveme.txt'

Again a very minor issue but the context menu item is "New Document", not "Create Document"
So that leads to wondering if those writing the tests are actually using what is being tested? (in this case 13.04/nautilus-3.6.3

As far as nautilus most of these type bugs will end up as "wishlists" other than focus issues which may or may not get fixed

---

### Post by balloons on 2013-02-11
> **mc4man said:**
> I did notice that (black vs. blank),  but didn't what to seem too picky by mentioning.
The other thing I noticed was the nautilus testcase on creating a empty docu - 
 
Again a very minor issue but the context menu item is "New Document", not "Create Document"
So that leads to wondering if those writing the tests are actually using what is being tested? (in this case 13.04/nautilus-3.6.3

As far as nautilus most of these type bugs will end up as "wishlists" other than focus issues which may or may not get fixed

Semantic are semantics, but we want the tests to be correct. Please do be picky! Your excellent at picking up little details like this -- makes you a great tester :-) I'll let you file the bug for the nautilus test:
[https://launchpad.net/ubuntu-manual-tests/+filebug](https://launchpad.net/ubuntu-manual-tests/+filebug)

---

### Post by smartboyhw on 2013-02-12
> **guitara said:**
> Semantic are semantics, but we want the tests to be correct. Please do be picky! Your excellent at picking up little details like this -- makes you a great tester :-) I'll let you file the bug for the nautilus test:
[https://launchpad.net/ubuntu-manual-tests/+filebug](https://launchpad.net/ubuntu-manual-tests/+filebug)

And I fixed that bug already:P

BTW, NEWS: Edubuntu would NOT have Alpha 2 for 13.04. So just Kubuntu for Alpha 2 testing:)

Regards,
smartboyhw

---

### Post by jerrylamos on 2013-02-12
> **kansasnoob said:**
> I see this AM that some of the 12.04.2 images are already being updated, but still no upgrade testing. So things are definitely still in progress :D

Such a relief to install, run, and update 12.04.x on my 3 test pc's.  It works. Slight oddity, I can get 2D on one machine (preferred, sharp, crisp, efficient) and not on another. Oh, well, back to struggling with raring.  What's next after "r"?  "s"?

---

### Post by ventrical on 2013-02-12
> **jerrylamos said:**
> Such a relief to install, run, and update 12.04.x on my 3 test pc's.  It works. Slight oddity, I can get 2D on one machine (preferred, sharp, crisp, efficient) and not on another. Oh, well, back to struggling with raring.  What's next after "r"?  "s"?

Smart Simian! ?
 hehehe:)

---

### Post by ventrical on 2013-02-12
> **kansasnoob said:**
> I see this AM that some of the 12.04.2 images are already being updated, but still no upgrade testing. So things are definitely still in progress :D


 I just zsynced to the 12.04.2 and I am going to put that on my borked Btrfs experiment. :)

---

### Post by ventrical on 2013-02-12
That was an extremely  snappy install of 12.04.2!!

---

### Post by ventrical on 2013-02-12
:)

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
ventrical@ventrical-PY028AA-ABA-A1106N:~$

---

### Post by ventrical on 2013-02-12
Finally a seamless install on Ati graphics:

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV350 AP [Radeon 9600] (Secondary)
ubuntu@ubuntu:~$ 

```

[http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/37466/testcases/1300/results](http://iso.qa.ubuntu.com/qatracker/milestones/243/builds/37466/testcases/1300/results)

---

### Post by Cavsfan on 2013-02-12
Deleted.

---

### Post by Cavsfan on 2013-02-12
Never mind. I realize it is too late and it is probably too much for me anyway.  :-s

---

