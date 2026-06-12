---
title: "Safe way to upgrade server software?"
date: 2006-05-01
forum: Server Platforms
---

### Post by OneSeventeen on 2006-05-01
Ubuntu is more stable than previous server operating systems I've used, and I have had no issues of corrupt data, hacked scripts, etc. etc. in the past 6 months.

This combined with the "if its not broke, don't fix it" attitude has lead to me running an out-of-date ubuntu server.

Now that one of our major applications is going to go live in the next few weeks,  I'd like to upgrade the system, since I know there has been at least one kernel upgrade, and numerous server software upgrades.

What is the safest way to upgrade everything?  I am assuming I can just apt-get update then apt-get upgrade, reboot, reconfigure my IP addresses, and I'll be just fine.

*but* there's always that fear that something will go wrong, or I'm missing something that every web-server administrator should do before an upgrade.

I have a .tgz file of everything but the proc, lost+found, mnt, and sys folders, so I guess if I royally screw things up I should be able to just restore that file, but I just wanted to check here first so I can avoid doing that.

Any tips on safely upgrading a server?

---

### Post by nagilum on 2006-05-01
There's a --simulate option to apt-get, but I don't know of how much use that is. If a post-inst script failes for some reason this won't catch the error I guess.
One better possibility might be to try the upgrade in a chroot environment. Copy your hole system (except /proc etc. of course) to a temporary directory, chroot to this directory and try the upgrade. If that runs fine the real upgrade most probably will also. There's still the chance that some software will no longer work as expected. You can additionally stop the servers from the actual system and run those from the chroot to see if everything works as before.

---

