---
title: "Upgrade testing"
date: 2014-02-14
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2014-02-14
[https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038081.html](https://lists.ubuntu.com/archives/ubuntu-devel/2014-February/038081.html)

> [FONT=monospace]Hello all,[/FONT]

[FONT=monospace]I'm pleased to announce that after lots of fixing packages,[/FONT]
[FONT=monospace]infrastructure, and scripts, automatic testing of distro release[/FONT]
[FONT=monospace]upgrades is now back:[/FONT]

[FONT=monospace]  [/FONT][https://jenkins.qa.ubuntu.com/view/Upgrade/](https://jenkins.qa.ubuntu.com/view/Upgrade/)[FONT=monospace]?[/FONT]

[FONT=monospace]All except one scenario now succeed, and that red one is a problem[/FONT]
[FONT=monospace]with the test scripts (it already succeeded several times, I'm looking[/FONT]
[FONT=monospace]into that now).[/FONT]

[FONT=monospace]We test a number of different scenarios like desktop, server, server[/FONT]
[FONT=monospace]tasks, on i386 and amd64, from 12.04.{0,1,2,3.4} (different due to the[/FONT]
[FONT=monospace]backported LTS enablement stacks) and 12.10 to 13.10 and trusty.  This[/FONT]
[FONT=monospace]is also running various post-upgrade tests that X still starts up, all[/FONT]
[FONT=monospace]python modules work, conffile prompts did not happen, and similar:[/FONT]

[FONT=monospace]  [/FONT][http://bazaar.launchpad.net/~auto-upgrade-testing-dev/auto-upgrade-testing/trunk/files/head:/share/post_upgrade_tests/](http://bazaar.launchpad.net/~auto-upgrade-testing-dev/auto-upgrade-testing/trunk/files/head:/share/post_upgrade_tests/)

[FONT=monospace]If you have an idea what else we should be checking after upgrades, or[/FONT]
[FONT=monospace]how the existing tests can be improved, please file a bug here:[/FONT]

[FONT=monospace]  [/FONT][https://bugs.launchpad.net/auto-upgrade-testing/+bugs](https://bugs.launchpad.net/auto-upgrade-testing/+bugs)

[FONT=monospace]Many thanks to Maarten Lankhorst for fixing the upgrade from[/FONT]
[FONT=monospace]12.04.{1,2,3,4} and to Jean-Baptiste for his patience with all my[/FONT]
[FONT=monospace]questions![/FONT]
[FONT=monospace][COLOR=#888888]
Martin[/COLOR][/FONT]

---

### Post by kansasnoob on 2014-02-14
That is good news and I know that Martin Pitt is trustworthty, so this further improves the LTS HWE stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I hope we get a 12.04.5 :^)

---

### Post by cariboo on 2014-02-14
> **kansasnoob said:**
> That is good news and I know that Martin Pitt is trustworthty, so this further improves the LTS HWE stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I hope we get a 12.04.5 :^)

From what I've seen on the mailing list 12.04.5 should come out in August, or early September, it also looks like all the derivatives have opted in.

---

