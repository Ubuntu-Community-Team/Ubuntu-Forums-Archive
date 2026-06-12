---
title: "Quantal-proposed in use already"
date: 2012-06-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-06-05
Just noticed that proposed repository is already in use in Quantal.
Look here:
1) [https://launchpad.net/ubuntu/quantal/+source/gnome-desktop3/3.5.2-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/gnome-desktop3/3.5.2-0ubuntu1)
2) [https://launchpad.net/ubuntu/quantal/+source/gsettings-desktop-schemas/3.5.2-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/gsettings-desktop-schemas/3.5.2-0ubuntu1)

---

### Post by philinux on 2012-06-05
From Kate Stewart.

 Dear Developers,

It's that time in the cycle to chill the archive again for Alpha 1.

As a result of the successful pre-release use of -proposed last cycle, we'd like to take things a step further for Alpha 1 this cycle. We don't yet have tools to make scalable use of -proposed for all uploads, but -proposed is open; so instead of asking developers not to upload packages to quantal at all during the milestone preparation, as for past soft freezes, we are instead only asking you to redirect your uploads to quantal-proposed.

For this experiment, the following rules apply: - If a package is needed to fix a bug that would block the milestone, it should still be uploaded to quantal. - If a package does not touch any of the images, it can still be uploaded to quantal. - All other uploads should be done to quantal-proposed first. In particular, an upload that will increase the count of uninstallable packages in main, even temporarily, MUST be done to quantal-proposed instead of to quantal. Affected uploads include: - all shared library packages (due to multiarch) - any uploads that will leave packages uninstallable on one architecture while the autobuilders catch up (due to out-of-sync Arch: all / Arch: any binary packages) - any packages that introduce new versioned Conflicts/Breaks and require coordination between multiple source packages

Auto syncs of packages from Debian Unstable have been stopped until we release A1.

If you have any questions about where you should upload, please ask on #ubuntu-release first.

Thank you for your help with this experiment,

Kate Stewart on behalf of the Ubuntu Release Team.

---

### Post by zika on 2012-06-05
In other words, stay off from proposed if You're not brave or idle enough... ;)

---

### Post by jppr on 2012-06-06
I always use Proposed updates to that but I do not recommend the faint of heart :popcorn:

---

### Post by zika on 2012-06-06
> **jppr said:**
> I always use Proposed updates to that but I do not recommend the faint of heart :popcorn:I was joking... ;)
It is nice to see testing process divided into such branches so everybody can pick a path for himself... ;)

---

### Post by handaxe on 2012-08-23
Ah, I have just been told by apport retracer that my stuff is out of date and I must refile the bug report if it persists after an update. Thing is, I am up-to-date in terms of standard updates but re-tracer wants the version in proposed.

Not the best situation - as it rather forces ones hand, eh?

---

### Post by dino99 on 2012-08-23
> **handaxe said:**
> Ah, I have just been told by apport retracer that my stuff is out of date and I must refile the bug report if it persists after an update. Thing is, I am up-to-date in terms of standard updates but re-tracer wants the version in proposed.

Not the best situation - as it rather forces ones hand, eh?

he may find some package(s) on your system coming from prior proposed archive activation: clean/autoclean/autoremove should help

---

### Post by handaxe on 2012-08-23
> **dino99 said:**
> he may find some package(s) on your system coming from prior proposed archive activation: clean/autoclean/autoremove should help

Good thought but it seems not, as the version of libre-office the apport service mentions is in proposed and not updates. Not a biggie, but if I am right it does rather negate the purpose of the updates/proposed distinction for the development... And I will admit, as I had carefully updated just before I had the crash and bug-report, I got mildly irritated ...

---

