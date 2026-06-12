---
title: "Kernel Team Meeting Minutes"
date: 2010-05-26
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-05-26
**Meeting Minutes**

 [IRC Log of the meeting.]("http://irclogs.ubuntu.com/2010/05/25/%23ubuntu-meeting.txt")

 

 **Agenda**

 [2010-25-05 Meeting Agenda]("https://wiki.ubuntu.com/KernelTeam/Meeting#Meeting:%20Tues,%2025%20May%202010")

 

 **Outstanding actions from last meeting**

   **Item:  ** ogasawara to email out reminder regarding blueprint disposition  **Status:** done       **Item:  ** smb to add work item for updating karmic fsl-imx51 in line with lucid  **Status:** done       **Item:  ** jfo to explain new bug review process  **Status:** in progress  

 **Maverick Release Status: Bugs**

                   Alpha 1 Milestoned Bugs (0) Release Targeted Bugs (34 accross all packages)   linux            0  1   

 **Bugs with Patches Attached: 130 (down 2 from last week)**

 [Launchpad Report]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bugs?field.has_patch=on")
 
[Breakdown by status]("http://qa.ubuntu.com/reports/ogasawara/csv-stats/bugs-with-patches/linux/")

 

 **Blueprint: kernel-maverick-apparmor**

 Working on dfa translation for the compatibility patch for old kernel interface, and will use this to cross verify the upstreaming interface changes.  So current upstreaming code isn&#8217;t yet compatible with lucid

 

 **Blueprint: kernel-maverick-firewire-stack**

 I emailed out a description of what needs to be done, and why we need to do it to the ukml. Waiting on responses.  Looks like we need help from foundations, will CC foundations on the email.

 

 **Blueprint: kernel-maverick-misc**

 Tim has pulled out the -preempt flavour from Maverick with a view to it being a community supported flavour from its own source package.  The new ubuntu-debian.git repository is up and seeded with Maverick debian plus some fixes developed following testing on Karmic and Lucid; scripts now exist to apply this back to those releases.  Finally the broadcom wl driver has been fixed for Maverick.

 

 **Blueprint: kernel-maverick-new-kernel-on-lts**

 LTS backport is undergoing tests (no problems so far). I&#8217;ve uploaded to the kernel PPA at [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu). I&#8217;ve also created a new branch in the Lucid repository called lts-backport-maverick

 

 **Blueprint: kernel-maverick-pv-ops-ec2-kernel**

 Playing with paravirt-ops kernel for legacy /dev/tty and /dev/sdX used by EC2 and integrating in to the virtual kernel, currently /dev/hvc -> /dev/tty changes require !VT Have built and Produce kernels with paravirt-ops enabled for testing, but they aren&#8217;t quite ready for hand off to scott and others for further testing

 

 **Blueprint: kernel-maverick-tracing-support**

 I&#8217;m currently in the process of reviewing the configs for tracers in maverick, other work (tooling packaging) has yet to be started

 

 **Blueprint: kernel-maverick-ubuntu-delta-review**

 I&#8217;m hoping to update iscsitarget today.  apw had a rather large set of patches associated to his name during the delta review, so I could see him extending this work item to Alpha2.  manjo only has one patch to follow up on, so I suspect he should be able to complete this by next week, ie. Alpha1.

 

 **Blueprint: kernel-maverick-union-mounts**

 kernels are up for testing in my purple PPA, no feedback as yet from foundations

 

 **Blueprint: kernel-maverick-config-review**

 The two bugs/work items are Fix Committed and should close when I upload today.  This will then complete the blueprint.

 

 **Blueprint: kernel-maverick-bug-handling**

 Working on the wiki pages with input from apw, ogasawara and smb. This work will be reflected on this BP and will be removed from the kernel-maverick-misc BP.

 

 **Blueprint: kernel-maverick-upstart**

 Leann has written up the new modules.builtin rules exceptions.  Other progress is slow but still hoped to hit Alpha-1.

 

 **Blueprint: kernel-maverick-reducing-dkms-packages-required-for-hardware-enablement**

 Nothing new this week.

 

 **Blueprint: kernel-maverick-bios-test-automation**

    * Identified some tests "low-hanging fruit"  * Git repo: [http://kernel.ubuntu.com/git?p=cking/ubuntu-firmware-test-suite/.git;a=summary](http://kernel.ubuntu.com/git?p=cking/ubuntu-firmware-test-suite/.git;a=summary)    * Test suite framework complete (fancy logging, execution mechanism, kernel log parsing, etc..)    * Test added in past week:      * dmi_decode:  test DMI/SMBIOS tables for errors      * acpiinfo:    general ACPI sanity check      * syntaxcheck: check for DSDT AML syntax errors      * klog:        check for generic errors in kernel log      * wakealarm:   ACPI wakealarm test      * s3:          suspend/resume test (in progress)      * with the help of some code lifted from the Intel Firmware Test kit    * Working on:      * common:      check common kernel log errors      * s4:          hibernate/resume test      * semanticAML: some semantic AML checking 

 **Maverick: Lucid**

 It&#8217;s been almost a week since I&#8217;ve uploaded and I&#8217;ve accumulated quite a bit of patches since then.  We&#8217;ve pulled in the -omap flavour, tweaked multiple config options per our UDS config review, and dropped a number of patches based on our UDS delta review.  We&#8217;re also now carrying the two security kernel hardening patches for hardlink/symlink protections.  That being said, I&#8217;ll be uploading 2.6.34-4.11 today (note the ABI bump).  I&#8217;ll likely do one last upload on Friday, so get your patches to the list and ack&#8217;d before then if you want something to land in the Alpha1 kernel. Also, please test once 2.6.34-4.11 is uploaded if you are able to.

 

 **Security & Bugfix Kernels**

    * Dapper:      2.6.15-55.83  (updates)  * Hardy:       2.6.24-27.69  (updates)  * Intrepid:    --- End of Support ---  * Jaunty:      2.6.28-18.60  (updates)  * Karmic:      2.6.31-21.59  (updates)     - mvl-dove  2.6.31-213.27 (updates)     - fsl-imx51 2.6.31-111.27 (updates)     - ec2       2.6.31-306.14 (updates)  * Lucid:       2.6.32-22.33  (updates)     - mvl-dove  2.6.32-204.16 (release)     - fsl-imx51 2.6.31-607.13 (release)     - ti-omap   2.6.33-500.6  (release)     - qcm-msm   2.6.31-800.2  (release)     - ec2       2.6.32-305.9  (release) 

 **Incoming Bugs: Regressions**

 Current regression stats (broken down by release):

 **regression-potential (up 130)**

   Maverick Lucid      3        302        **regression-update**

   Lucid Karmic Jaunty Hardy  25    9      5      2      **regression-release**

   Lucid Karmic Jaunty Hardy  149   50     20     3      **regression-proposed**

   Lucid Karmic      1      1           

 **Incoming Bugs: Bug day report**

 Bug Days will start back next week. I plan to send out an announcement for the next one later this week with a reminder the business day before. The current plan is to review Bugs with Patches attached to eliminate misreported patches and prepare the list for team review.  I am however, open to suggestion should the Bug day topic need to change.  I assume we&#8217;d like to focus on those as a team at some point as well so we can see what is cruft and what is not so I am open to a Kernel Bug Day soon too.

 

 **Open Discussion or Questions**

   abogani  Who could review my -lowlatency package ([https://lists.ubuntu.com/archives/kernel-team/2010-May/010707.html](https://lists.ubuntu.com/archives/kernel-team/2010-May/010707.html)) ?     cnd and apw have it on their lists to review.       cjwatson would it be hard to get at least fbcon built-in in the near future ([https://wiki.ubuntu.com/FoundationsTeam/Grub2BootFramebuffer)?](https://wiki.ubuntu.com/FoundationsTeam/Grub2BootFramebuffer)?)  I guess vesafb might require a bit mo</p>  ogra vesafb might get tricky with arm   ogra  agrees fully on fbcon   ogasawara  I can look into it, can you open me a bug so it doesn&#8217;t fall off the radar   

[More...](http://fridge.ubuntu.com/node/2041)

---

