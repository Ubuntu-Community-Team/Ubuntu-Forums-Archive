---
title: "Dash and HUD regressions?"
date: 2013-09-27
forum: Ubuntu Development Version
---

### Post by fluteflute on 2013-09-27
I upgraded to Ubuntu+1 a few days ago. For the most part, very little has changed! But two issues:

[LIST=1]
[*]I'm not able to get any files/folders showing up in the dash (even if I go explicitly that lense)
[*]I can't get Suspend (or other items from the top right System indicator) in the HUD
[/LIST]

---

### Post by Mateusz Stachowski on 2013-09-27
For your first problem you could try removing or moving out of the directory this file:

~./local/share/zeitgeist/activity.sqlite

That's a hidden directory in your Home folder (press CTRL + H in Nautilus). Then you have to log out and log in back again or restart unity (press ALT + F2 and type unity the ENTER). Note that this will remove your previous activity but new open files should appear.

---

### Post by danboy on 2013-09-27
Having the same problem.

Unity HUD just says "Sorry, there is nothing that matches your search" tried removing the contents of the zeitgeist dir, but that didn't do anything.

Currently launching everything with alt+f2.

Anyone else seeing this?

---

### Post by Mateusz Stachowski on 2013-09-28
If deleting zeitgeist didn't work than try this:

```
[FONT=Ubuntu Mono]rm ~/.cache/software-center -R[/FONT]
```

it will delete contents of that folder. Next you should reset Unity the recommended way of doing this in Ubuntu 12.10 and newer has been described on [AskUbuntu]("http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration").

---

### Post by mc4man on 2013-09-28
For empty Dash make sure "unity-scope-home" is installed

---

### Post by danboy on 2013-09-28
Thanks mc4man that solved it! Not sure how that package disappeared.

---

### Post by fluteflute on 2013-09-30
mc4man's fix also solved my problem #1. I've reported a bug: [https://bugs.launchpad.net/ubuntu/+source/unity-scope-home/+bug/1233029](https://bugs.launchpad.net/ubuntu/+source/unity-scope-home/+bug/1233029)

I'd still like to get Suspend back in the HUD (but I suspect this was a design decision)

---

### Post by GWBouge on 2013-09-30
I've been wondering about the HUD bit as well, since I decided to check out Saucy last week.  My primary (only, really) use for it was accessing items on the tray.  I'm really hoping it wasn't a design choice, but I haven't been able to find anything on it.

---

### Post by fluteflute on 2013-10-01
> **GWBouge said:**
> I've been wondering about the HUD bit as well, since I decided to check out Saucy last week.  My primary (only, really) use for it was accessing items on the tray.  I'm really hoping it wasn't a design choice, but I haven't been able to find anything on it.

Suspend is my most common use of the HUD.

I reported a bug at [https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1233712](https://bugs.launchpad.net/ubuntu/+source/hud/+bug/1233712)

---

