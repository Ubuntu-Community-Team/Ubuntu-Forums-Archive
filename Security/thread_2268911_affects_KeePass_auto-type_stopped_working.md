---
title: "affects KeePass auto-type stopped working"
date: 2015-03-12
forum: Security
---

### Post by fr33z0n3r on 2015-03-12
**SOLVED** - A reboot fixed the issue with auto-type for KeePass.  Quite odd behavior, that I've never seen before.  Not directly caused by the kernel update (security update) it seems.

There was a kernel update that I just installed via Software Updater today. ( I reoboted as needed)

It seems like a personally very important feature/package has been broken by this change.  KeePass uses an auto-type feature, and it seems to have been completely broken with this kernel update.  It was working yesterday when I needed the feature.

The kernel update is:
3.13.0-46.79

The related package is:
xdotool

[B]
Can anyone else comfirm this conflict?[/B]

I will restart Ubuntu to ensure it isn't some transient issue (which has NEVER happened before).

---

