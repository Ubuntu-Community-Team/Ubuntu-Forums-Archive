---
title: "Does this mean my system's been hacked into and remotely accessed?"
date: 2014-10-31
forum: Security
---

### Post by jamal5 on 2014-10-31
Hi all,

Recently, I turned on GUFW to check the connections running. I saw something I don't think I've ever seen before, "vino-server" running from ports 5800 & 5900.

I looked it up and it's a remote access program. I've never used anything like that, and it can be used to remotely administer a system by an attacker.

Immediately I ran   sudo apt-get purge vino   and removed the program, and blocked ports 5800 and 5900. It was apparently installed and running on my system- despite it not appearing in system monitor- I definitely didn't put it there, does anybody know if vino is included in the default 14.04 installation? Because it seems that that could be the only explanation other than an attacker with root access putting it on my system...

After that I ran rkhunter and it didn't find any rootkits but it gave me some warnings which I don't know what to make of- here are two screenshots of what it came up with

[ATTACH=CONFIG]257647[/ATTACH]
[ATTACH=CONFIG]257648[/ATTACH]


So can somebody with more knowledge than me give some insight into what this might mean and what I should do at this point?

Thanks a lot

---

### Post by pfeiffep on 2014-10-31
Vino is the VNC server for the GNOME desktop environment. A VNC server is a program that shares a desktop with other computers over the Internet. You will need a VNC server if you want other people to see your desktop.  TryRead about it on this [link]("https://help.ubuntu.com/community/VNC/Servers")

---

### Post by jamal5 on 2014-10-31
Exactly what I'm worried about- I never used this kind of software, and having someone remotely access my machine is my fear...

---

### Post by ian-weisser on 2014-10-31
If you don't use it, you can easily uninstall it. 

Look at /var/log/auth.log.
If the log is missing or empty, that's a sign you may have an unwanted intruder.
Otherwise, the log should show each login, sudo, root cronjob, and lots of kernel messages for the day. Look at all the logins.

Here's what a valid login looks like:
```
Oct 31 21:44:31 my_computer lightdm: pam_unix(lightdm:session): **session opened for user ian by** (uid=0)
```

If there are logins by other users, or at unusual times, ask a few questions.

It is an imperfect indicator: Logs can easily be tampered with, they are just text files. But it takes time and effort that an intruder may not want to waste on a log you probably don't even know to look at.

---

