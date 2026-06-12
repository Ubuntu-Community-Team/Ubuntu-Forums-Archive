---
title: "iTALC master"
date: 2010-05-31
forum: Server Platforms
---

### Post by map7 on 2010-05-31
I'm running Ubuntu 10.04 64bit on my LTSP server and using iTALC.  On one of my clients I accidentally logged in as the same user as my server is logged in as, now I cannot start italc on the server.

I get this message

There seems to be no iTALC service running on this computer or the authentication-keys aren't set up properly.  The service is required for running iTALC.  Contact your administrator for solving this problem.

How do I start the iTALC server/daemon again?

---

### Post by meditatingfrog on 2010-09-30
I'm actually having the same error just after installing iTalc on ubuntu 9.10.  Here's the error i get.  [IMG]http://imagebin.org/116427[/IMG].  i've tried googling for answers, but all i found was information for windows users.

---

### Post by map7 on 2010-10-03
We'll I'm still stuck with this problem and haven't found a way around it.

---

### Post by meditatingfrog on 2010-10-03
> **map7 said:**
> We'll I'm still stuck with this problem and haven't found a way around it.

Did you try rebooting or logging out and back in?  Someone on IRC channel #ltsp on irc.freenode.net recommended this for a bug i created in launchpad (don't have a link: the bug was closed).

---

### Post by map7 on 2010-10-03
Yes rebooting and relogging in works, but that's a pain as I don't like to log out of all my work everytime the iTALC stops working.

---

### Post by meditatingfrog on 2010-10-04
> **map7 said:**
> Yes rebooting and relogging in works, but that's a pain as I don't like to log out of all my work everytime the iTALC stops working.

I'd recommend creating a bug in launchpad then.  

If you haven't created a bug before use

```
ubuntu-bug italc-master
```

wish i could help, but i'm not a developer :(.

---

### Post by ch0i on 2010-10-25
Hi All,


Seems that it is working at my end. Just type ica-laucher in your shell then after click on Application --> System Tools --> iTalc master interface.

For example:
root@dlcb0110104:~# ica-launcher

in Windows System the service is called "ica" so I tried to type ica + I press the Tab in the keyboard and there I saw these ica and ica-launcher.

root@dlcb0110104:~# ica
ica           ica-launcher


I just have one question: I know I'm a newbie on Ubuntu, the only question in mind is that where are these files "ica" and "ica-launcher" located? I tried to browse all the service but none of these were listed.

---

### Post by map7 on 2010-10-25
I'm pretty sure the ica and ica-launcher are in the /usr/bin directory.

You can check by typing
$ where ica
or 
$ where ica-launcher

into a terminal window.

---

