---
title: "Disabling GRUB splash screen on 10.04 Server"
date: 2010-07-22
forum: Server Platforms
---

### Post by Dymial on 2010-07-22
Hey,
 
I've recently upgraded to 10.04, but I need to be able to see the bootloader details instead of the splash screen. I've already tried
 
```

sudo nano /etc/default/grub

```
 
and adding
 
```

GRUB_CMDLINE_LINUX_DEFAULT="text"

```
 
and then restarting GRUB. This didn't work though. Anyone else have ideas?

---

### Post by wojox on 2010-07-22
```
sudo update-grub
```

To create a new config file.

---

### Post by Dymial on 2010-07-22
> **wojox said:**
> ```
sudo update-grub
```
 
To create a new config file.
 
I tried that, didn't work however. I get my choice of boot devices, but am still returned to the splash screen.

---

### Post by wojox on 2010-07-22
I don't know Dymial. I run 10.04 Server headless with no GUI. 

Since your using a GUI try [this]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")

It may or may not work with Plymouth.

---

### Post by arrrghhh on 2010-07-22
I still don't get why they put Plymouth on servers...

[This post](http://ubuntuforums.org/showpost.php?p=9104343&postcount=6) seems to have the right idea... it looks like you did something slightly different.  May be the issue.

Also, not sure if it makes a difference (shouldn't) but there's also ```
sudo update-grub2
```

---

### Post by Dymial on 2010-07-23
> **wojox said:**
> I don't know Dymial. I run 10.04 Server headless with no GUI. 
 
Since your using a GUI try [this]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html")
 
It may or may not work with Plymouth.
 
I don't use an X GUI for security reasons, also it's not necessary on my server so a waste of space and RAM ;) .
 
> **arrrghhh said:**
> I still don't get why they put Plymouth on servers...
 
[This post]("http://ubuntuforums.org/showpost.php?p=9104343&postcount=6") seems to have the right idea... it looks like you did something slightly different. May be the issue.
 
Also, not sure if it makes a difference (shouldn't) but there's also ```
sudo update-grub2
```
 
I tried sudo update-grub2 but apparently I don't have the grub2 package at all. In regards to the post you mentioned, if I try sudo apt-get remove --purge plymouth I also remove mysql and phpmyadmin, which I really can't do.

---

### Post by arrrghhh on 2010-07-23
> **Dymial said:**
> I tried sudo update-grub2 but apparently I don't have the grub2 package at all. In regards to the post you mentioned, if I try sudo apt-get remove --purge plymouth I also remove mysql and phpmyadmin, which I really can't do.

Wow... I guess I really haven't tried to remove plymouth myself.  Did you upgrade to 10.04 or do a fresh install?  I'm betting you upgraded...  That's probably why you have GRUB 'legacy'.

That's also really odd that plymouth is tied to mysql and phpmyadmin.  Not a clue why that would be.

Perhaps that's why the post suggests "Remove all of the plymouth-theme-* packages from your system,
including the text ones. Plymouth will remain installed to
permit boot-time prompts."

Did you try that?  I haven't removed plymouth... it is stupid, but my server isn't hooked up to a monitor.  I saw it the first few times when I first booted the fresh install of 10.04, scoffed, and promptly did my best to forget about it :P

---

### Post by Dymial on 2010-07-28
I actually have no idea why, but

sudo aptitude remove --purge plymouth-theme-ubuntu-text

did the trick.

---

