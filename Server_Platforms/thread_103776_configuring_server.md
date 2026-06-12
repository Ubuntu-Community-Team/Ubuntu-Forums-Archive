---
title: "configuring server"
date: 2005-12-14
forum: Server Platforms
---

### Post by boetheus on 2005-12-14
I work in an all Windows environment.  I needed a way to run some Open Source stuff, so I was allowed to set up a linux setup.  I used a Dell GX150, PIII-1.3 Ghz,256 Mb Ram.  I was new to Linux so a I installed the default.  I have set it up with MySql, PHP and Apache, installed my web programs and all is running fine.  I think that it does not run as well as it could because of all of the stuff that was installed by default.  I want to streamline it for performance.  I had about 77 people hitting my site today and it seemed to slow down.  I do not if it was network resources or my set up.  I was considering upgrading the RAM.  Is that a good idea, if so, will this screw up things because the Swap partition is set? What is the best direction? I want to keep my GUI interface.

---

### Post by diebels on 2005-12-14
'rm /etc/rc2.d/S13gdm'
Having GUI running by default on a server is stupid unless it has to much ram(possible?). Start up the GUI when you need it
'/etc/init.d/gdm start'
and shut it down when you stop using it
'/etc/init.d/gdm stop'
Adding more ram never hurts..

If the network is slow, mod_deflate helps

---

### Post by boetheus on 2005-12-14
If I add ram, will i have to adjust the settings?

---

### Post by diebels on 2005-12-15
[QUOTE=boetheus]If I add ram, will i have to adjust the settings?[/QUOTE]
Which settings. You don't have to do anyting no. Just stick in the ram.

Maybe it would be smarter to analyze the cause of the apparent slowdown. Adding ram will not help you if the network is too slow. Then see my previous post.

---

### Post by simon w on 2005-12-15
As diebels said, find the cause of the problem before you try to fix it.

[QUOTE=boetheus]I had about 77 people hitting my site today and it seemed to slow down.[/QUOTE]

Your hardware should cope fine with only 77 visitors.  Was it a regular or server based install (please don't say regular)?

---

### Post by Liberteh on 2005-12-15
server based doesnt include the GUI, does it?

---

### Post by boetheus on 2005-12-15
Okay, let me say this again.  I know of Linux from web dev buddies that I have.  I run some websites, and I moved them to Linux through my hosting service, and I have been very pleased ever since.  In this case, I am doing the setting up.  I am learning this as I go.  I installed the regular because I did not exactly know what I was doing, but I knew what I wanted and wanted to do, also I was on a time constraint.  I had to get something up and fast.  Ubuntu alllowed me that and I am very pleased with the results so far.  I just want to optimize what I have done. I appreciate the advice so far.   I will definitely check the problem before changing anything.  Let me say that the problem is not bad.  I just couldn't navigate Joomla's backend as fast as I thought I should be able to since I was on Linux.  Things got kinda of slow when I had about 77 people viewing the site and signing up for classes through it.  I believe that we do have some network issues, no doubt.  
My question about ram came about because someone told me that if I change the ram configuration after installation, my server could possibly crash  because the swap was set to the original ram configuration.  I just want to know the truth.  I am learning how to operate without the GUI,but for time sake the GUI gets done what I need.  I would like to be able to stop it and start it when needed though.

---

### Post by grendelkhan on 2005-12-15
adding more memory won't make you change any configurations.

---

### Post by diebels on 2005-12-15
[QUOTE=boetheus]
I will definitely check the problem before changing anything.  Let me say that the problem is not bad.  I just couldn't navigate Joomla's backend as fast as I thought I should be able to since I was on Linux.  Things got kinda of slow when I had about 77 people viewing the site and signing up for classes through it.[/quote]The joomla backend isn't among the fastest software. And firefox 1.0.7 on Ubuntu is painfully slow for some reason. If you want to keep a GUI on the server, you could save a bit of ram usage by throwing out gnome and installing xubuntu-desktop.
[QUOTE=boetheus]I believe that we do have some network issues, no doubt.  
My question about ram came about because someone told me that if I change the ram configuration after installation, my server could possibly crash  because the swap was set to the original ram configuration.  I just want to know the truth.  I am learning how to operate without the GUI,but for time sake the GUI gets done what I need.  I would like to be able to stop it and start it when needed though.[/QUOTE]
The swap partition should be around twice the size of ram. If you run out of swap, the server could crash. But I don't think that's likely. More ram will reduce the swap usage too. Watch top and see for yourself. I don't know if you could shrink another partition, and enlarge the swap partition.
```
sudo fdisk -l /dev/hda
```

---

