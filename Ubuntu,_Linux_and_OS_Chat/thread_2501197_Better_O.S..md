---
title: "Better O.S."
date: 2024-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by raleigh3 on 2024-09-26
I have been using Ubuntu Mate for over 5 years and have been happy with it.

However, when I upgraded to UM 24.04 I started having problems.

Scripts that used to work, stopped working.

I also had other anomalies pop up.

Is that the case with "regular Ubuntu" ?

---

### Post by guiverc on 2024-09-26
You've provided few specifics, such as no clues as to  what libraries/toolkits/programs your scripts use, so we (I?) can only be *generic*.

Software changes over time, and this impacts loads of things.

Qt4 was announced as EOL back in 2012, but wasn't removed from Debian & Ubuntu until 2019; Qt6 the current version & Qt5 now in *maintenance*. GTK3 is now in *maintenance* mode on its way to being declared EOL, with GTK4 the current GTK version; but MATE was created *long ago* because *someone(s)* didn't like the end of GTK2/GNOME 2...

You may find the issue is your scripts use tools that are *outdated* and should have been altered? thus switching to another desktop, or even a different OS may not help (*except temporarily where its using an older software stack*)

I'd check you're not using features/tools that are *deprecated*..  I have backup scripts myself that use features that are going to get removed (*I've noted the messages of that in logs, but for now they still work so I'm ignoring it; but it'll eventually bite me I know*).

FYI:  *I consider myself a Ubuntu user, but use multiple desktops including MATE; but to me if you're using Ubuntu MATE 24.04 you're using Ubuntu 24.04 LTS anyway... the difference between the flavors is just what gets installed by default due to different seed files being used to create the various ISOs; all of which are built using the same tools/procedures/builder.*

---

### Post by wildmanne39 on 2024-09-27
Moved to Ubuntu, Linux and OS Chat sub-forum.

---

### Post by raleigh3 on 2024-09-27
Thanks. Here is one example. 

I am trying to figure out why this is not working. I could not find any login info in syslog.

```
$ sudo nano /etc/lightdm/lightdm.conf.d/autologin.conf

Once opened, insert the following lines and ensure to replace "USERNAME" with the preferred user to activate auto-login.

[SeatDefaults]
autologin-user=andy
autologin-user-timeout=5
```

---

### Post by guiverc on 2024-09-27
( Also asked at [https://ubuntu-mate.community/t/is-there-a-file-with-login-information/28271/](https://ubuntu-mate.community/t/is-there-a-file-with-login-information/28271/) 

I don't use `lightdm` myself, so I'm not familiar enough with it to know if changes have occurred etc, and today (Saturday locally) what time I have is spent on *Ubuntu News* work, so I don't (currently) have time to explore it either.

Chris.

( *It's Ubuntu 24.04(.1) though the .1 doesn't matter much to me as release is 24.04; 24.04.1 just shows you've been applying some security fixes etc.   FYI:  A lightdm config isn't what I'd consider a script; but that doesn't matter *)

---

