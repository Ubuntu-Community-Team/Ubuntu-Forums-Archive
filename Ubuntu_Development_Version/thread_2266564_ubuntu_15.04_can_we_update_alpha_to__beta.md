---
title: "ubuntu 15.04 can we update alpha to  beta"
date: 2015-02-23
forum: Ubuntu Development Version
---

### Post by krishnagkashyap on 2015-02-23
Hi I just downloaded Alpha2 (Ubunntu Alpha2), and installed onto my system, so far it is doing great!!
Now, i would like to know in general weather Ububtu can be upgraded from Alpha2 --> Beta[1,2] --> Stable build?

---

### Post by sammiev on 2015-02-23
If you update everyday, then you will always have the newest and the latest everyday.

---

### Post by fantab on 2015-02-24
Yes. Keep updating your Ubuntu regularly and you will reach the stable release.

---

### Post by krishnagkashyap on 2015-02-24
Thank you for replying  [[COLOR=#000000]sammiev[/COLOR]]("http://ubuntuforums.org/member.php?u=628319")[COLOR=#000000]  and [/COLOR][COLOR=#000000][[COLOR=#000000]fantab[/COLOR]]("http://ubuntuforums.org/member.php?u=1275004") .. this is my first post in ubuntu and i got a good response..

am performing sudo apt-get update -y && sudo apt-get upgrade -y every day, since, i installed Ubuntu 15.04, will continue to do so until i hit the stable as you mentioned[/COLOR]

---

### Post by ventrical on 2015-02-24
Look here.. [https://wiki.ubuntu.com/VividVervet/ReleaseSchedule](https://wiki.ubuntu.com/VividVervet/ReleaseSchedule)

---

### Post by grahammechanical on 2015-02-24
Welcome. You have taken your first step to becoming a Ubuntu+1 tester. When you are ready give some consideration to this

[https://wiki.ubuntu.com/QATeam/Roles/Tester](https://wiki.ubuntu.com/QATeam/Roles/Tester)

[http://community.ubuntu.com/contribute/find-a-task/#!/toplevel/communicate](http://community.ubuntu.com/contribute/find-a-task/#!/toplevel/communicate)

And do not forget to share your experiences with using the development release in this section of the forum. If we cannot suggest a work around we can certainly sympathise. 

Regards.

---

### Post by Cavsfan on 2015-02-28
> **krishnagkashyap said:**
> Thank you for replying  [[COLOR=#000000]sammiev[/COLOR]]("http://ubuntuforums.org/member.php?u=628319")[COLOR=#000000]  and [/COLOR][COLOR=#000000][[COLOR=#000000]fantab[/COLOR]]("http://ubuntuforums.org/member.php?u=1275004") .. this is my first post in ubuntu and i got a good response..

am performing sudo apt-get update -y && sudo apt-get upgrade -y  every day, since, i installed Ubuntu 15.04, will continue to do so until  i hit the stable as you mentioned[/COLOR]

I do exactly as you mentioned but I do not give it the -y option as I like to see what's being updated before it actually updates.

Use **sudo apt-get update && sudo apt-get upgrade** which will give you normal updates. 
And if you see packages are being held back and not upgraded, there is probably some new packages that need to be installed too.
When you see this, enter **sudo apt-get dist-upgrade** and you will see.
This happens when a new kernel is added to your system. 

if you want to simplify this you can add aliases in your .bashrc file by entering **gedit ~/.bashrc** in terminal and add this after line 84 or so where you see other aliases.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

```

Then logout and back in to get it to take effect.

From then on you just have to enter **ud** in terminal and it will ask for your password and check for updates.
If there are packages held back enter **ud2** and you will see what packages will be upgraded and what new packages will be installed.
The 3rd one **ud3** is for when one or more packages are no longer needed and in terminal it says to autoremove it/them.

It's not necessary but it makes it simpler with a lot less typing.

Welcome to the forum.

---

### Post by Elfy on 2015-03-01
> **Cavsfan said:**
> ...

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

```....

It's obviously up to you, but I'll ask as others with little bandwidth might blindly copy :)

Why apt-get clean rather than apt-get autoclean.

Difference being autoclean will just remove packages that are no longer installable, clean removes them all - there's always a chance you might need to reinstall something, using -clean you'd have to download the same package all over again.

---

### Post by Cavsfan on 2015-03-01
> **Cavsfan said:**
> 
...

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get [COLOR=#ff0000]auto[/COLOR]clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'

```
...


> **Elfy said:**
> It's obviously up to you, but I'll ask as others with little bandwidth might blindly copy :)

Why apt-get clean rather than apt-get autoclean.

Difference being autoclean will just remove packages that are no longer installable, clean removes them all - there's always a chance you might need to reinstall something, using -clean you'd have to download the same package all over again.

I guess the problem was that *I* blindly copied that from someone in this forum and have been using it ever since. I was typing the commands and the aliases were a huge plus.

I never did the research to find the differences between clean and autoclean and didn't think it necessary.
I have a pretty a pretty fast internet connection myself and never gave it a thought but I see your point for those with little bandwidth.

What you are saying makes a lot of sense and I will change it. 

Thanks again Elfy! :)

---

### Post by jerrylamos on 2015-03-02
You can keep updating.  
Note especially in development more and more clutter accumulates.  
Old linux images can be removed with synaptic.
Also,
 ```
#! /bin/bash
df
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
df
exit 0
```
removes some more of the clutter.
Since this is a Development forum where we're looking for bugs, I do installs maybe every couple of weeks.  
Ubuntu installs have been good for a number of launchpad bug reports.
After installing the new partition space can be noticeably smaller than the endlessly updated version even after clean, autoclean, autoremove.

---

