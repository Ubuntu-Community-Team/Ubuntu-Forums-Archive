---
title: "Mantic Desktop arm64 daily-live builds don't boot to live environment"
date: 2023-06-19
forum: Ubuntu Development Version
---

### Post by perockwell on 2023-06-19
Mantic arm64 desktop daily-live builds do not boot to the live environment. Instead they boot to a graphical login widget where it's asking for a username. Any username and password provided fails to log in (and I've tried both 'ubuntu' and 'mantic' users). I see a number of errors during the boot noting that user name 'ubuntu' does not exist. (I verified that 'ubuntu' doesn't exist by booting the daily-live to single user mode). 

As a side note, Mantic server daily builds boot and install fine, and adding ubuntu-desktop to an installed server works as well.

I suspect that there's a packaging error in the arm64 desktop daily-live builds. Either that or they don't work and should not be posted as a daily-live.

Any thoughts on how best to report this as a bug? Obviously since I can't log into the live environment it's pretty difficult to submit a bug report to Launchpad in the usual manners.

---

### Post by guiverc on 2023-06-19
> **perockwell said:**
> 
Any thoughts on how best to report this as a bug? Obviously since I can't log into the live environment it's pretty difficult to submit a bug report to Launchpad in the usual manners.

Just report a bug, and ensure you report it on the ISO QA tracker.

If using today's DAILY that would be [http://iso.qa.ubuntu.com/qatracker/milestones/446/builds/280733/testcases/1303/results](http://iso.qa.ubuntu.com/qatracker/milestones/446/builds/280733/testcases/1303/results)

But I'd generally recommend you start at the mantic daily (446/build) being [http://iso.qa.ubuntu.com/qatracker/milestones/446/builds](http://iso.qa.ubuntu.com/qatracker/milestones/446/builds)

and follow the links down (ie. Ubuntu Desktop, arm64 etc) to the actual ISO/test you're performing, so you don't report the issue on an old ISO, as my prior link will report it only as an issue on ISO 20230619

Have you filed bugs before?  Ubuntu bugs are reported on launchpad (a bug tracker), and the ISO.QA tracker will link an actual QA test with the filed bug report (if you file the launchpad bug ID in the appropriate field) so it appears on the appropriate teams testing reports (Ubuntu Desktop in this case)

The usual/best reference for bug reporting will be [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) 

FYI:  Since you couldn't get the session to start; close your report on the ISO QA tracker as a FAILED report.

---

