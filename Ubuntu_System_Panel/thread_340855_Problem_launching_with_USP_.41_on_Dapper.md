---
title: "Problem launching with USP .41 on Dapper"
date: 2007-01-17
forum: Ubuntu System Panel
---

### Post by ardchoille42 on 2007-01-17
I installed USP .41 on Ubuntu 6.06.1 LTS and added USP to my panel and restarted USP.. this was last week. Today I installed k9copy, k3b, bibletime and krecipes (all KDE apps) from the repos with:

sudo aptitude install k9copy bibletime krecipes k3b

When I launch k9copy or krecipes from the default gnome Menu Bar that is in the panel, they both launch immediately. When I launch k9copy or krecipes from USP, nothing happens. Some info about the apps after attempting to launch them from USP:

```

[~ @ 17:42:35] ps aux | grep k9copy
ianmac    5247  0.0  0.0   2876   796 pts/0    S+   17:43   0:00 grep k9copy
[~ @ 17:43:03] ps aux | grep krecipes
ianmac    5522  0.0  0.0   2876   792 pts/0    R+   17:50   0:00 grep krecipes

```

It appears that the apps either launch and immediately close, or they just don't launch.. and I see nothing on the screen to indicate anyting about the status of the apps.

K3b and bibletime launch correctly from both the gnome menu bar and USP, so I don't think it is KDE apps that have this problem. There seems to be something specific to k9copy and krecipes that aren't playing well with USP .41 on Dapper.

I haven't noticed this problem with any of my other gnome apps

---

### Post by chanders on 2007-01-18
The launching mechanism has changed in USP2Alpha. When it is finally released it should work no problem..

---

### Post by Malac on 2007-01-18
> **chanders said:**
> The launching mechanism has changed in USP2Alpha. When it is finally released it should work no problem..In the mean time try creating your own gnome-panel "custom" launchers and use those to launch the apps in question from USP.

---

### Post by ardchoille42 on 2007-01-18
Yeah, already created custom launchers. I look forward to the release of USP2 with much enthusiasm :)

---

### Post by sefs on 2007-07-10
I am on USP ver 2.00 Beta ... from the SVN.  Still unable to launch K9Copy, although able to launch fine from the normal gnome menu.

---

