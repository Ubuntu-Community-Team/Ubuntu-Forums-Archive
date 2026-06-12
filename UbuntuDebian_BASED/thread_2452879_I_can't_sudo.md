---
title: "I can't sudo"
date: 2020-10-29
forum: Ubuntu/Debian BASED
---

### Post by kevinix on 2020-10-29
Halp. I just installed linux for a few days and have been trying to configure it.

I was following some guides from google and copy pasting in stuff.

I think I did: ```
usermod -aG /data kevin
``` while following a guide to automount my drives.

though I'm not sure why that would ruin my sudo.

But now, after restarting my computer, I can't sudo.

it says: 

```


kevin@pop-os:~$ sudo gnome-disks
[sudo] password for kevin: 
kevin is not in the sudoers file.  This incident will be reported.


```

So I try this:

```


kevin@pop-os:~$ usermod -aG sudo kevin
usermod: Permission denied.
usermod: cannot lock /etc/passwd; try again later.


```

Do I need to reinstall the OS? >_<

---

### Post by QIII on 2020-10-29
***Moved to Ubuntui/Debian BASED.***

Although a derivative based on Ubuntu, Pop_OS is not an official flavor of Ubuntu.

---

### Post by learnlinux-on-yt on 2020-11-21
You didn't add the user to the 'wheel' or 'sudo' group, which is why you're getting that message. I think Pop! OS uses the 'sudo' group, so you shouldn't need to mess with '/etc/sudoers'.

To add your user to the 'sudo' group, gain root privileges by other means, then use: `usermod -G sudo kevin`

WARNING: Do not under any circumstances run a graphical program with `sudo`, or by otherwise getting direct root access; this will mess with the permissions of your files and cause you hassle later on. Use something like `gksudo` or whatever people are using these days. You can find some information on this, as well as an *apparent* alternative approach: [https://itsfoss.com/gksu-replacement-ubuntu](https://itsfoss.com/gksu-replacement-ubuntu)

---

### Post by TheFu on 2020-11-21
Linux is fun, once you get the hang of it.
When you are really new, it is best **not** to use google for answers, because people posting don't know what system, which GUI, what your skills and often they only know a little more than you do. Beware.  Don't copy/paste random commands that you don't understand.
BTW, **usermod -aG /data kevin** is a bad command and won't do what you want.  There isn't any /data group, so this makes no sense.

Best to get your knowledge from reputable sources - a general rule of thumb would be to only follow guides written for your exact OS release AND only from websites with **Ubuntu** in the domain name.

When posting questions, please always say the exact OS release and the exact DE being used so we don't have to guess.

When first starting out and trying to use a shell (also called terminal or CLI), it is best to realize that beginning skills build on other skills which build on other skills.  Trivial issues come up when someone jumps into a higher skill than their current level, so they get frustrated. Whereas learning these skills in the proper order will ensure you don't get thrown into learning 10 things just to do the 1 thing you need.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Start with that book, Chapter 1 and work through the chapters, in order, until around page 250.  That will provide a reasonable basis of knowledge to where you can jump off and move into advanced-beginner stuff like screwing with sudo and other groups.

IMHO.

Whenever people ask me how to learn Linux, here's my answer: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

---

