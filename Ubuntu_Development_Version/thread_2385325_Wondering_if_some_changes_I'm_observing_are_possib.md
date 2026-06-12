---
title: "Wondering if some changes I'm observing are possible bugs"
date: 2018-02-19
forum: Ubuntu Development Version
---

### Post by raysatiro on 2018-02-19
I recently installed Bionic 2018-02-14 in a VM and i have noticed a few changes from Xenial. I am only sure [one of them]("https://bugs.launchpad.net/ubuntu/+bug/1750278") was a bug, but I would like to know should I file any of these below. I am not sure if these things are just meant to be changing or they're bugs:


Menu items don't appear on top bar, instead they appear in window
Tweaks > Top Bar > Show Application Menu is ON but I'm looking at Terminal right now and its menu isn't in the top bar.


Time is set to EST (New York, United States) but it defaults to 24 hour



Launcher popup menus looks different, worse, too much filler space.
xenial:
[ATTACH=CONFIG]278581[/ATTACH]
bionic:
[ATTACH=CONFIG]278582[/ATTACH]



Transparency of launcher is lost when app is next to top bar


Appearances is missing from settings, no 'Show desktop' icon.

unity-tweak-tool does have a show desktop icon and minimize single window apps on click but it may have caused my icons to disappear. or this is something I did somehow, I don't know.


[ATTACH=CONFIG]278583[/ATTACH]




trash icon on desktop now instead of in launcher like in xenial, instead of the launcher and I don't see a way to add it there.

---

### Post by Chanath on 2018-02-19
What you are noticing is a change of the desktop environment from Unity to Gnome-shell.

---

### Post by deadflowr on 2018-02-19
You'll get further with your bug by making it against the installer program, ubiquity.
Marking a bug against Ubuntu almost always gives you the response crichton posted, since Ubuntu is too generic a term for anyone to help, specifically.
(crichton) tells you exactly how to do this in that post.

Again, the package you want to mark it for would be ubiquity.

---

### Post by jbicha on 2018-02-19
@deadflowr, ubiquity is only the installer app. None of the issues mentioned in this thread have anything to do with ubiquity.

---

### Post by deadflowr on 2018-02-19
> **jbicha said:**
> @deadflowr, ubiquity is only the installer app. None of the issues mentioned in this thread have anything to do with ubiquity.

The link: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1750278]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1750278")

From the first line of the post.

Seems Brian Murray edited the bug and changed to the proper package.

---

