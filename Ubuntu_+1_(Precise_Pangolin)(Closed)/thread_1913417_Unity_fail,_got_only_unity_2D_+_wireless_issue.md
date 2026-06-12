---
title: "Unity fail, got only unity 2D + wireless issue"
date: 2012-01-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by TheNessus on 2012-01-22
And Shell works fine too.
This issue with Unity not working started when I did an upgrade one day which also resulted in a Libreoffice dependency problem (solved by now). If I start Unity I get to the desktop, but there is no panel and launcher. all else seems to function ok.

I wonder how can I fix this. I upgraded to unity 5 but to no avail.

Another issue is that when I change a network connection, the whole systen hangs for about 20 seconds. And when waking from sleep, I sometimes get no network connection at all, it's like the wireless driver failed to wake up, and I have to do a hard reboot (broadcom 4313)

---

### Post by mc4man on 2012-01-22
Maybe you're using the "Default" profile for the ubuntu session (unity-3d) instead of the "unity" profile
(or maybe  you're using the unity profile but the Ubuntu Unity plugin is disabled

What does this file have in it, if anything (on a fresh install the file is blank
```
gedit ~/.config/compiz-1/compizconfig/config
```

---

### Post by TheNessus on 2012-01-22
> **mc4man said:**
> Maybe you're using the "Default" profile for the ubuntu session (unity-3d) instead of the "unity" profile
(or maybe  you're using the unity profile but the Ubuntu Unity plugin is disabled

What does this file have in it, if anything (on a fresh install the file is blank
```
gedit ~/.config/compiz-1/compizconfig/config
```

it has this:

[gnome_session]
profile =

---

### Post by TheNessus on 2012-01-22
wow, unity plug-in was indeed disabled, how the hell did that happen? And to think I purged and re-installed the hell out of unity.

---

