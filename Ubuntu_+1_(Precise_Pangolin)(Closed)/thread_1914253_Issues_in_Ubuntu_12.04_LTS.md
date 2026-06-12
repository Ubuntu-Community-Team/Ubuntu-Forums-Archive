---
title: "Issues in Ubuntu 12.04 LTS?"
date: 2012-01-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MrMarshmallow on 2012-01-24
Hi there, I know 12.04 is still in alpha stage, I am just wondering if there's any fixes yet for these two issues. It was all fine when i installed 12.04 until i updated over the air.

1. Flash is not working/very buggy in Firefox: shows up with a white box and nothing in it. 

2. Movie player is very buggy, lags and skips, fast forwards randomly, laggy CD music playing. 

I've waited almost a week yet its getting worse.

My computer is a HP Mini 110 series, came with windows XP that was unbelievably slow on performance and absolutely sucks in stability. Switched to windows 7, laptop was almost unusable. 

On Ubuntu 11.04, everything worked perfectly and i absolutely loved my laptop... Are there any fixes or will i have to go back to 11.10?? 

Thanks!

---

### Post by Paqman on 2012-01-24
There probably will be fixes, but a week isn't a long time to wait. With an Alpha you shouldn't be running it as your main system. You should expect things to break on a daily basis.

Have you reported the bugs and/or subscribed to the bug reports? The whole point of running the testing branch is to help with reporting bugs. You'll need a Launchpad account. You can either let the automated bug tool (apport) report them when you get a crash, or you can prompt it to file a bug by using:
```
ubuntu-bug packagename
```
In general, if you're a noob, I'd strongly suggest using a stable release as your main system. If you want to get involved in testing and learn how to do it effectively, install 12.04 on a separate partition, learn how to [file bugs]("https://help.ubuntu.com/community/ReportingBugs"), read up on [testing]("https://wiki.ubuntu.com/Testing") and get over to the [Precise forum]("http://ubuntuforums.org/forumdisplay.php?f=412").

---

### Post by coffeecat on 2012-01-24
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

> **MrMarshmallow said:**
> On Ubuntu 11.04, everything worked perfectly and i absolutely loved my laptop... Are there any fixes or will i have to go back to 11.10?? 

As you've realised, 12.04 is still in alpha and is best used only for testing purposes at the moment.

---

### Post by Harry33 on 2012-01-24
> **MrMarshmallow said:**
> Hi there, I know 12.04 is still in alpha stage, I am just wondering if there's any fixes yet for these two issues. It was all fine when i installed 12.04 until i updated over the air.

1. Flash is not working/very buggy in Firefox: shows up with a white box and nothing in it. 

2. Movie player is very buggy, lags and skips, fast forwards randomly, laggy CD music playing. 

I've waited almost a week yet its getting worse.

My computer is a HP Mini 110 series, came with windows XP that was unbelievably slow on performance and absolutely sucks in stability. Switched to windows 7, laptop was almost unusable. 

On Ubuntu 11.04, everything worked perfectly and i absolutely loved my laptop... Are there any fixes or will i have to go back to 11.10?? 

Thanks!

This is all I can tell At the moment.
1. Conserning flashplugin (Adobe) there are no such issues you have described.
So, are you using firefox 9.0.1 (stable) or 10 beta from Precise official repos?
And, do you use Adobe flashplugin?
I have several setups, all they have a working flashplugin.

2. You can always try the newest VLC player, directly from Precise official repos. It really is a good player.

---

### Post by jbicha on 2012-01-24
Which version of Totem/ Movie Player are you running?

---

### Post by Pilot6 on 2012-01-24
There was a bug with flash in Firefox on Nvidia drivers. It has been fixed in 295.06 beta.

---

