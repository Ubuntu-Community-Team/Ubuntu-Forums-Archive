---
title: "Kernel Team Meeting Minutes - June 1st, 2010"
date: 2010-06-03
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-06-03
**Meeting Minutes**

 [IRC Log of the meeting.]("http://irclogs.ubuntu.com/2010/6/1/%23ubuntu-meeting.txt")

 

 **Agenda**

 [2010-6-1 Meeting Agenda]("https://wiki.ubuntu.com/KernelTeam/Meeting#Meeting:%20Tues,%201%20Jun%202010")

 

 **Maverick Release Metrics**

 

 **Bugs**

                   Alpha 1 Milestoned Bugs (0) Release Targeted Bugs (40 accross all packages)   linux            0  5   

 **Blueprints**

 
[LIST] 14 Blueprints (includes HWE blueprints) 
[/LIST]
 

 **Bugs with Patches Attached: 130 (down 2 from last week)**

 

 
[LIST] 
[*][Launchpad Report]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bugs?field.has_patch=on") 
[*][Breakdown by status]("http://qa.ubuntu.com/reports/ogasawara/csv-stats/bugs-with-patches/linux/") 
[/LIST]
 

 **Blueprint: kernel-maverick-apparmor (jjohansen)**

 Nothing new this week.

 

 **Blueprint: kernel-maverick-firewire-stack (manjo)**

 Nothing new this week.

 

 **Blueprint: kernel-maverick-misc (apw)**

 There are two outstanding items for Alpha-1, getting mainline builds to include linux-tools and progressing the -preempt pakcages.  These are both non-release tasks.  The first is likely to slip to alpha-2 now, the second is progresing but also likely to slip.

 

 **Blueprint: kernel-maverick-new-kernel-on-lts (tgardner)**

 LTS backport kernel and meta package are in the kernel-ppa. Its tracking maverick as its released.

 

 **Blueprint: kernel-maverick-pv-ops-ec2-kernel (jjohansen)**

 Slow progress, more testing without success. Will have to try pv-ops on HVM drivers this week.

 

 **Blueprint: kernel-maverick-tracing-support (cnd)**

 Kernel config is set, confirmed with upstream. No new work other than that yet.

 

 **Blueprint: kernel-maverick-ubuntu-delta-review (ogasawara)**

 There are only two work items still open for Alpha-1, both of which are not critical for Alpha-1&#8217;s release.

 apw, manjo: if you don&#8217;t think you&#8217;ll get to those before Thurs, I&#8217;ll move them under the Alpha-2 milestone.

 

 **Blueprint: kernel-maverick-union-mounts (apw)**

 Still no testing feedback from foundations on union-mounts, there is talk of another drop occuring from upstream which will simplify the patches.  It is unclear when this new drop will occur however.
 
We also have an issue with aufs2 in maverick which is leading to aufs2 panics during boot on the live-cd.  I have an update for aufs2 which I am attempting to test to see if that fixes the issues.  It is likely we will have to update aufs2 as soon as we are on 2.6.35-rcN.  The update does appear to be good, and we are being asked to respin with aufs2 updated.  Will get patches out shortly.

 

 **Blueprint: kernel-maverick-bug-handling (jfo)**

 Continuing work on the wiki pages with input from apw, ogasawara and smb. I plan to send some e-mail out on the ongoing effort today.
 
Also, I have some prep work happening that will move several topics to INPROGRESS.

 

 **Blueprint: kernel-maverick-upstart (apw)**

 We have patches pending for the remaining Alpha-1 deliverable, waiting on testing from Foundations.  These would most readily be applied post Alpha-1.

 

 **Blueprint: kernel-maverick-reducing-dkms-packages-required-for-hardware-enablement (cking)**

 Nothing new this week

 

 **Blueprint: kernel-maverick-bios-test-automation (cking)**

    *  Added functionality:     *   Test for common BIOS error messages     *   APIC edge/level trigger test     *   acpiinfo: common kernel log ACPI checks     *   Common S3/S4 PM kernel error checks     *   S3 multiple suspend/resume cycle tests     *   S4 hibernate/resume test     *   Add in test run order/priority     *   Rework kernel log scanning + execution of some user space tools     *   Rework wakealarm code into common library calls     *   Add ability to take pre-captured input from dmidecode, /proc/acpi/dsdt and dmesg  rather than at run time     *   Manoj added a test from the test suite into kernel-qa dev to prove the test suite  integrates in okay. 

 **Status: Maverick (ogasawara)**

 We uploaded the 2.6.34-5.12 Alpha 1 kernel last Friday.  There will be no further uploads until after Thurs.  Unfortunately the first iso&#8217;s were just spun yesterday and have uncovered 2 bugs we need to be aware of (thanks apw and tgardner for already taking ownership):

 
[LIST] 
[*][Launchpad bug 587888 in linux (Ubuntu Maverick) &#8220;aufs oops in au_do_open() on maverick live system boot&#8221; [Critical,Triaged]]("https://launchpad.net/bugs/587888") 
[*][Launchpad bug 587893 in linux (Ubuntu Maverick) &#8220;linux-image-2.6.34-5-virtual is oversized, results in oversized server ISO&#8221; [High,In progress] ]("https://launchpad.net/bugs/587893") 
[/LIST]
 I should take that back, we might upload for the aufs bits.  Also note that 2.6.35-rc1 was released so I&#8217;ll be rebasing Maverick today.

 

 **Security & bugfix kernels &#8211; Karmic/Jaunty/Intrepid/Hardy/Others (gnarl/smb)**

    * Dapper:      2.6.15-55.83  (updates)  * Hardy:       2.6.24-27.69  (updates)  * Intrepid:    --- End of Support ---  * Jaunty:      2.6.28-18.60  (updates)  * Karmic:      2.6.31-21.59  (updates)     - mvl-dove  2.6.31-213.27 (updates)     - fsl-imx51 2.6.31-111.27 (updates)     - ec2       2.6.31-306.14 (updates)  * Lucid:       2.6.32-22.33  (updates)     - mvl-dove  2.6.32-204.16 (release)     - fsl-imx51 2.6.31-607.13 (release)     - ti-omap   2.6.33-500.6  (release)     - qcm-msm   2.6.31-800.2  (release)     - ec2       2.6.32-305.9  (release) Status unchanged from last week. Security release nearly out (probably tomorrow).

 **Incoming Bugs and Regression Stats**

 **Incoming Bugs:**

   Version Count   Maverick               5 (+1)                   Lucid                  1005 (-129)              **Current regression stats:**

   Version Potential Update Release Proposed    maverick                5 (+2)                                lucid                   262 (-40;)              26 (+1)                 146 (-3)                1                         karmic                      9                       50                      1                         jaunty                      5                       20                            hardy                       1 (-1)                  3                            

 **Incoming Bugs: Bug day report (JFo)**

 This week&#8217;s Bug Day will be on Thursday. I plan to send out an announcement for it later today with a reminder going out tomorrow. The current plan is to review Bugs with Patches attached to eliminate misreported patches and prepare the list for team review. Additionally, i will resume our use of the &#8216;cherry-pick&#8217; tag to identify bugs with upstream commit SHA1s in them for us to review and react accordingly. You can see the list of these from [this url]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bugs?field.tag=cherry-pick")

 

 **Open Discussion or Questions: Anyone have anything? (raise your hand please)**

   jfo Just wanted to draw your attention [here]("http://status.qa.ubuntu.com/qapkgstatus/linux")        bjf Pointing to [here]("http://status.qa.ubuntu.com/qapkgstatus/alsa-driver")        apw Remember we discussed the b43 driver not working, i&#8217;ve confirmed that it does not work in the current release kernel in lucid due to dma errors, etc.      With smb&#8217;s latest stable 32.13 the b43 does work pretty well, and i am using it now   tgardner Is compat-wireless any better?   apw Can&#8217;t say i&#8217;ve tried it no   Originally posted to the [Canonical Voices -Kernel Team Blog]("http://voices.canonical.com/kernelteam/?p=4027") by Brad Figg on Wed, June 2nd, 2010

 

[More...](http://fridge.ubuntu.com/node/2054)

---

