---
title: "Where to register a bug report or feature request for pcmanfm-qt?"
date: 2020-03-02
forum: Ubuntu, Linux and OS Chat
---

### Post by buzlite on 2020-03-02
Currently using...
lubuntu 19.10
pcmanfm-qt 0.14.1


Please provide a link
Thanks

---

### Post by Bashing-om on 2020-03-02
buzlite; Hello :)

If you find a bug in Ubuntu or any of its official !flavors, please report it using the command « ubuntu-bug 
               <package> » - See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for other ways to report bugs.

[INDENT]hope this helps[/INDENT]

---

### Post by wildmanne39 on 2020-03-02
*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by mörgæs on 2020-03-03
Thanks for your interest in reporting bugs.

First question: Are you able to reproduce the bug in 20.04 (daily build)?

---

### Post by guiverc on 2020-03-03
I'll provide this  (the Bugs page for Lubuntu)

[https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/)

You'll note `pcmanfm-qt` is found in the *Core desktop environment* section, so the link will be [https://bugs.launchpad.net/ubuntu/+source/pcmanfm-qt](https://bugs.launchpad.net/ubuntu/+source/pcmanfm-qt) however please use

`ubuntu-bug pcmanfm-qt` on your actual system to report a bug.

If you report using the "Report a bug" on my provided link, you'll likely get a request to run `apport-collect` or your system shortly afterwards (*with a reasonable chance it'll be me asking*) which will gather the information that `ubuntu-bug` will collect for the report.

Added later: 

I missed the *feature request* part of your query.  If your question is a feature request I'd suggest trying out the current Lubuntu 20.04 daily (with luck it may already be implemented), and I'll provide [http://iso.qa.ubuntu.com/qatracker/milestones/](http://iso.qa.ubuntu.com/qatracker/milestones/) (or [http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds) for daily builds) which will allow navigating to the Lubuntu page where you'll find a download link near the top.  I didn't navigate down any further as new builds come out most days (or more than a build per day) so lower level links became *stale* pretty quick.

If it's a feature request, you maybe asked to make it upstream, or [https://github.com/lxqt/lxqt](https://github.com/lxqt/lxqt) but I'd start with a launchpad bug report anyway first; and it'll be there that the Lubuntu team will track it.

---

### Post by buzlite on 2020-03-03
I'm new at this. I don't know where the daily builds are found and I don't have a system where I can install and test new builds.

> **mörgæs said:**
> Thanks for your interest in reporting bugs.

First question: Are you able to reproduce the bug in 20.04 (daily build)?

---

### Post by guiverc on 2020-03-03
> **buzlite said:**
> I'm new at this. I don't know where the daily builds are found and I don't have a system where I can install and test new builds.

I'll provide

[http://iso.qa.ubuntu.com/qatracker/milestones/408/builds](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)

which is the link for the DAILY ISOs for 20.04


Navigate to Lubuntu, for example clicking *Lubuntu Desktop amd64 *for me now goes to [http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/208493/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/208493/testcases) which is the current build right now (208493) however it'll become stale on the next build available and won't offer any new details or new downloads. Thus until you work out the system use the first link I provided..

If you navigate to the 'Live Session' test, up the top is "*Link for download information*" which will allow you to download the ISO for writing to a thumb-drive.

A 'live' test only requires a thumb-drive, and pc/laptop to boot the thumb-drive, and you can select "Start Lubuntu" and no changes will be made.

[I]Note:  I've been told when I 'test' on other peoples hardware who only use windows, their clocks can be changed to UST/UTC time instead of local, so this consequence may occur.

[/I]
If you'd like to record your tests as part of our QA (Quality Assurance testing) please enter details on the iso.qa.ubuntu.com web site (you'll only need a launchpad ID to login). Bugs get reported normally via launchpad (best with `ubuntu-bug <package>`) and the bug ID goes in the Critical or Bugs fields, the comments can be any comments/notes you have.  I personally use the first line to reflect my hardware, for the box I'm writing this on that would be

dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)

which is brand/model for me, cpu, ram, gpu, I just copy/paste from a text file which has the 21 boxes I use for testing.  FYI: If the GPU card info looks imprecise, it's just from`lshw`.

If the test works for you, you PASS the test, to FAIL the test you need to have filed bugs so those bug report IDs can be entered in either BUGS or CRITICAL fields. I still PASS tests if the bug is really petty/minor but it's your decision.

Happy testing :)


The following is the best place to go for good advice : [https://phab.lubuntu.me/w/testing/](https://phab.lubuntu.me/w/testing/)

---

### Post by mörgæs on 2020-03-06
@buzlite, the post above is correct but maybe a bit complicated for a beginner. 

First, just create a USB stick with the daily build ISO and do a live boot. You don't have to install it. When that works we can take a look at the next step.

---

