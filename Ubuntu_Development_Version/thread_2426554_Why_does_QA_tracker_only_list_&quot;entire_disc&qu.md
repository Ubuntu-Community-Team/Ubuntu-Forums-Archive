---
title: "Why does QA tracker only list &quot;entire disc&quot; installs for Lubuntu?"
date: 2019-09-10
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2019-09-10
Thought I'd ask here because I'm only tinkering with Lubuntu:

[http://iso.qa.ubuntu.com/qatracker/milestones/404/builds/199121/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/404/builds/199121/testcases)

I installed using manual partitioning because I have three hard drives and like to be 100% in control :)

That aside I'm quite impressed with Lubuntu since the change to LXQT.

By 2020 I intend to go QT for sure and I was leaning towards Kubuntu but Lubuntu may be more to my liking - minimalist approach.

---

### Post by mc4man on 2019-09-11
The way the QA thing always worked is it only shows test cases that someone created. So in the case of Lubuntu 2 test cases were created.
Overall it doesn't appear any of the QA blah, blah gets  much or even  any  activity anymore..

---

### Post by guiverc on 2020-06-11
This is very late... but I'll provide my 2c worth.

@mc4man is correct, and since the 18.10 cycle (*with Lubuntu using the `calamares` installer and new LXQt desktop*), we've primarily worked from a checklist on our phab instance; ie. [https://phab.lubuntu.me/w/release-team/testing-checklist/](https://phab.lubuntu.me/w/release-team/testing-checklist/)

At the end of the 19.04 cycle a task was created ([https://phab.lubuntu.me/T56](https://phab.lubuntu.me/T56)) which was hoped to be done for 19.10 which resulted in changes submitted from review that sat there for months. At the beginning of the year I wiped a home server's disk array (*errant `dd` command run on the wrong box*), bazaar didn't like my restored data so that change was aborted and a new one created. ([https://code.launchpad.net/~guiverc/ubuntu-manual-tests/lubuntu-calamares](https://code.launchpad.net/~guiverc/ubuntu-manual-tests/lubuntu-calamares)) 

Our testcases as written include

[COLOR=#333333][FONT=Ubuntu]testcases/image/Auto login (+31/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Custom partitioning on BTRFS (+30/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Custom partitioning on XFS (+30/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Custom partitioning with seperate home (+30/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption BIOS internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption BIOS offline (+39/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption EFI internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption EFI offline (+39/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption SecureEFI internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install encryption SecureEFI offline (+39/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption BIOS internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption BIOS offline (+37/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption EFI internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption EFI offline (+37/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption SecureEFI internet (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Full disk install no-encryption SecureEFI offline (+37/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Install using another language (+29/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Install with existing partition (+32/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Modern Live (+20/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Replace a partition (+30/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Upgrade using GUI (+36/-0)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]testcases/image/Upgrade using TUI (+33/-0)

But as stated, we follow the our [/FONT][/COLOR][https://phab.lubuntu.me/w/release-team/testing-checklist/](https://phab.lubuntu.me/w/release-team/testing-checklist/) checklist, we do record all details under our one install option on iso.qa.ubuntu.com (*see [http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/210756/testcases/1701/results](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/210756/testcases/1701/results) as an example, late in 20.04 cycle, sorry it's an example with bugs but they're easiest to find*) also noting our TESTCASE: options in the comment section for done tests.  

Successful tests get ticked off (tester/iso/completed.date) on our phab document.

---

### Post by guiverc on 2020-08-05
If you only just looked at the checklist; it's currently showing 20.04.1 (it would likely have still reflected 20.04 when I wrote my last post on this thread).

20.04.1 should be released in a little over 24 hours.

The current ISO (20200731) is the RC and with luck will be the actual release ISO (no re-spins are planned anyway)

---

