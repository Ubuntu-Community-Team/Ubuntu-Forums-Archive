---
title: "Software updater does not fetch updates"
date: 2017-05-10
forum: Security
---

### Post by juan53 on 2017-05-10
Software updater does not fetch updates.

Hi everyone

I have two platforms with Ubuntu, one with Ubuntu Mate and the other with Ubuntu Gnome. The thing is I installed yesterday Ubuntu Gnome and I updated it with the command "sudo apt update && sudo apt upgrade". It did well.
Today I have checked at the same time both platforms for updates. Just ony Ubuntu Mate grab the packages of today. Ubuntu Gnome did't. I prompted "sudo apt update && sudo apt upgrade" and this time the system recognised a package to update.
I have checked the repositories and keys and both are right.
I don't know what's the problem, and I ask you, if you have any idea how to fix it.

Thanks.

---

### Post by ian-weisser on 2017-05-10
It's intended behavior.
Each Ubuntu system (16.04 and newer) randomizes it's update time. And re-randomizes the time every day.
It's a cron.daily job

---

### Post by deadflowr on 2017-05-10
Software Updater (aka update-manager) implements a the function known as phased-updates.
Phased updates pushes updates out to a few users at first, then based on how many error come back, they either expand to all users or pull the packages.
apt-get and other updating mechanism do not use phased updates.

More here: [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

---

### Post by juan53 on 2017-05-11
Thanks to both for the answer. Very valuable information in those. In addition, to make sure that the software updater works fine, I have made the assistant only notify the updates rather than installing automatically.

---

