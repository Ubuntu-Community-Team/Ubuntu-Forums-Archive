---
title: "&quot;removing old config files&quot; hangs on installation"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by libihero on 2012-02-14
i tried to install the alpha 2 on another partition as a "/" and use my normal base "/home". however, in the very beginning of the installation, it hangs on "removing old config files" and wont progress for hours.

---

### Post by ranch hand on 2012-02-14
Are you using a unique user name for the 12.04 install?

If not you are going to have problems.

---

### Post by libihero on 2012-02-16
why do i have to use a unique user name??

---

### Post by cariboo on 2012-02-16
> **libihero said:**
> why do i have to use a unique user name??

You shouldn't have to use a unique user name, I use the same one for all my installs. I do setup a second user that I use most of the time, when not posting screen outputs. Have you check the install log in /var/log/installer/syslog, to see if there is anything there?

---

### Post by ranch hand on 2012-02-16
> **libihero said:**
> why do i have to use a unique user name??
If you are using the same /home for 2 different installs you need 2 user names.

This is because, as you know, the ~/.foo files are in the /home/<user name> directory.

Many of these files are not going to care one way or the other about where they are.  Some, however, are going to be different.  This will cause conflicts.

Now it is possible that I have completely misunderstood here and that you are simply installing a different but unique OS using the old /home.  I find that there are some rare occasions when doing that where removing the ~/.files is a good thing to do before installing the new / on the system.

This is usually when I install a completely different distro using the old /home partition.

I just installed the daily for Xubuntu 12.04-testing yesterday as my install seemed to have some strange problems.  I did not remove the ~/.files and it went fine.

One thing you may want to do is to, in the live session, run;
```

apt-get install ubiquity

```
This will upgrade ubiquity without upgrading the whole OS (you may not have enough ram for that).  Then try your install again.

This has worked for me several times in the past.  Worth a try.

---

### Post by libihero on 2012-02-17
awesome, thanks for the explanation. i was using /home for the same two different installs

---

### Post by ranch hand on 2012-02-17
If you play with the permissions so that one or both users are in the same "group" and give that group permissions on all files you can just use one set of /home/<user name> files.

This is more convenient as all you really need in the second users /home/<user name> directory is the ~/.files for the configuration of that second OS.

There was someone on here, don't remember who, that had all his/her installs using one /home.  I don't remember how many but the number 6 sticks in my mind for some reason.

I do know that what ever Ubuntu testing release we were using was one along with the newest stable and an install of Fedora.

---

