---
title: "100% guaranteed clean exit from Ubuntu live session"
date: 2017-09-27
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-09-27
The 17.10 Ubuntu live session (gdm3) can have 5 possible results when trying to shutdown or restart
2 lead to nolimit waits (systemd), they then require a hard shutown (mash the power button
1 leads to text output > hang, also then requires a hard shutdown
1 leads to text output > hang, keyboard combo can kickstart it (ctrl+alt+F7 works ok
1 leads to a proper shutdown/restart routine, typically shows the plymouth screen > remove media, ect.

What works all the time is to not start a in user  session shut down, instead go 
ctrl+alt+F1
login in to ubuntu user (user name = ubuntu
issue a restart or shutdown command from there.

As of comments today this will not be fixed till sometime in 18.04

---

