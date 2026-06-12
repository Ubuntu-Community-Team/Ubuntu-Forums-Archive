---
title: "Crash reports"
date: 2017-05-07
forum: Ubuntu Development Version
---

### Post by P-I H on 2017-05-07
What happens with crash reports?
I have gotten some on my system during daily use.
When I look at [https://bugs.launchpad.net/ubuntu/artful/+bugs](https://bugs.launchpad.net/ubuntu/artful/+bugs) there are no bugs listed that relates to crashes on the system.

---

### Post by fthx on 2017-05-07
Maybe your bugs are private ?
Did you check your bug reports in your launchpad account ?

---

### Post by Irihapeti on 2017-05-07
I've been noticing something similar. I've checked my bugs listing and nothing recent has been reported.

Previously, once the information had been uploaded, I'd be asked to login into Launchpad and complete the process. This hasn't been happening.

---

### Post by mc4man on 2017-05-07
Crash reports being uploaded to launchpad is disabled near the end of a dev cycle & not re-enabled in current development cycle for a period of time.
So like crashers in a release they are uploaded to a database. 
One can re-enable lp reporting in apport themselves but I'm sure this is not  appreciated at all so would never post how to.

---

### Post by P-I H on 2017-05-07
@mc4man
Shall I interpret this as it's meaningless to use Ubuntu+1 daily to provide info about crashes on the system?

---

### Post by mc4man on 2017-05-07
> **P-I H said:**
> @mc4man
Shall I interpret this as it's meaningless to use Ubuntu+1 daily to provide info about crashes on the system?
No, all crash reports are uploaded & looked at in some fashion (just not individually)
If you want to file a specific bug then use ubuntu-bug packagename

---

### Post by P-I H on 2017-05-07
OK, thanks

---

### Post by jbicha on 2017-05-07
The crashes that don't redirect you to Launchpad are reported to [errors.ubuntu.com]("http://errors.ubuntu.com") directly.

1. a. If you are using Unity, open System Settings and click Security & Privacy.
    b. If you aren't, install activity-log-manager and run that app.
2. Switch to the Diagnostics tab and click Show Previous Reports.

Each Ubuntu install has a unique identifier so that will only show you reports from your current install.

Although individual error reports are unlikely to be noticed, if an issue is causing a huge number of reports for a package in the default Ubuntu install, a developer may look into it.

---

### Post by P-I H on 2017-05-07
This is how it looks now. Some crashes on gnome-shell.

---

### Post by mc4man on 2017-05-07
> **jbicha said:**
> The crashes that don't redirect you to Launchpad are reported to ...
Right now I don't believe any crashers will go to LP. While not up on exactly when/why the switch is made it's generally after month 2 give or take.

I always figured that crashes early on are expected & no sense spamming Lp with them. On a couple of occasions in past I've had some that seemed prudent to go to Lp asap & in those few cases enabled it on a temp basis.

---

### Post by mc4man on 2017-05-07
What would be nice is if the option in apport to 'ignore future problems of this type' actually worked. The only thing it seems to do is remove the option on the next popup for same crash. screen shows option on a crash that has been happening for years that never is  fixed, never will be..., it would be nice to ignore it.

---

### Post by ventrical on 2017-05-08
> **jbicha said:**
> The crashes that don't redirect you to Launchpad are reported to [errors.ubuntu.com]("http://errors.ubuntu.com") directly.

1. a. If you are using Unity, open System Settings and click Security & Privacy.
    b. If you aren't, install activity-log-manager and run that app.
2. Switch to the Diagnostics tab and click Show Previous Reports.

Each Ubuntu install has a unique identifier so that will only show you reports from your current install.

Although individual error reports are unlikely to be noticed, if an issue is causing a huge number of reports for a package in the default Ubuntu install, a developer may look into it.

The link.

It reports 'no data available' for 17.10


The app.
Also it reports errors from since 2015 and this is a fresh install so it must have kept previous error logs since I didn't format the partition.

---

### Post by P-I H on 2017-05-09
This is what I get from the link errors.ubuntu.com
Quite interesting. The crashes on my system unattended-upgrades, [COLOR=#000000][FONT=Ubuntu]gnome-shell and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu]gnome-software are in the list.[/FONT][/COLOR]

---

### Post by corradoventu on 2017-05-09
Recently I'm using 2 Ubuntu 17.10 installed on different partitions of the same machine: one Ubuntu GNOME ant one Ubuntu Unity. If I look to the crash report I see the same list from both installations. I see also some old crash up to October 2015 (obviously it was not Ubuntu Artful!).

---

### Post by jbicha on 2017-05-09
Ok, but if you use VirtualBox, that install will have a different identifier at least.

---

### Post by Yellow Pasque on 2017-05-09
So is it working now?

```
apport (2.20.4-0ubuntu6) artful; urgency=medium

   * Disable report.test_add_gdb_info_abort_glib test case for now, as the
     glib assertion message is broken under current Ubuntu (LP: #1689344)
  * etc/apport/crashdb.conf: Enable Launchpad crash reports for artful.  <-----
```

[https://launchpad.net/ubuntu/+source/apport/2.20.4-0ubuntu6](https://launchpad.net/ubuntu/+source/apport/2.20.4-0ubuntu6)

---

