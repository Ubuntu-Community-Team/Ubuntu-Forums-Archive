---
title: "galternatives buttons not clickable"
date: 2014-04-17
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2014-04-17
galternatives is a convenient gui tool for switching between several versions of the same application (update-alternatives in the cli) in 14.04 I cannot add new paths and if I do this with the command line "sudo update-alternatives install.." the new path to the alternative shows up but not clickable. Since galternatives works in 13.10 and it is exactly the same version and build in 14.04 I think the problem lies elsewhere in 14.04 and probably some other applications also exhibit the same symptom.

Any thought or comment? Probably not too many people use this tools but I think I should give it a try..

---

### Post by monkeybrain20122 on 2014-04-18
Does not work on other de sessions either (lxde and gnome-session-flashback metacity) so it has apparently nothing to do with unity/compiz as I have suspected.

---

### Post by batden on 2014-04-18
Yeah, galternatives is unusable on 14.04 LTS. Shame.

---

### Post by zika on 2014-04-18
Men's work (CLI) should be left to men not to the boys (GUI)... ;)

---

### Post by monkeybrain20122 on 2014-04-18
I have created a bug report here [https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709](https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709)

---

### Post by monkeybrain20122 on 2014-04-18
> **zika said:**
> Men's work (CLI) should be left to men not to the boys (GUI)... ;)

Well everything can be done in CLI, but gui is convenient and I don't have to always check minor details like whether it should be 'sudo update-alternatives --configure' or 'sudo update-alternatives --config'. Real men have better use of their memory (as in the brain) than to memorize incantations and better use of their time than learning fast typing. :)

---

### Post by six5 on 2015-03-15
In case anyone interested, I fixed galternatives and repacked the deb. I've uploaded it to [http://www.tusfiles.net/73ubmk8jlv50](http://www.tusfiles.net/73ubmk8jlv50).

galternatives mistakenly referenced /usr/sbin/update-alternatives instead of /usr/bin/update-alternatives. So all references to it have been replaced.

Alternatively, you can create a link via `sudo ln /usr/sbin/update-alternatives /usr/bin`. This should work as well but the link may get removed during upgrades, etc.

---

