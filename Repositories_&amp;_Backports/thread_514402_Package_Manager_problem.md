---
title: "Package Manager problem"
date: 2007-07-31
forum: Repositories &amp; Backports
---

### Post by pah99 on 2007-07-31
I have a problem. When I run Package Manager it will  open a .deb file just fine. However, after I click on install and I type in my password, it tells me that only one Package manager, Aptitude, or Synaptic is allowed to run at one time. I can't do nothing. I have tried going into process manager and clossing all other programs that seemed to do with Updates (I found one: Update notifier). After closing everyting, it still did the same thing. Any help please. i searched the forums but I haven't found anything.

---

### Post by smartboyathome on 2007-08-01
Have you tried restarting the computer (or using control+alt+backspace)? That will sometimes clear it up, as it resets all processes.

---

### Post by pah99 on 2007-08-01
I did restart the computer once after the problem, but its been about two weeks now since the problem started and the computer is shut off every night, rebooted the next day. And even now it still does it.

---

### Post by Seisen on 2007-08-02
Try ```
sudo dpkg --configure -a
``` in the terminal

---

### Post by pah99 on 2007-08-07
After opening a terminal, I typed in the following (in bold);

pasha@pasha-desktop:~$ **sudo dpkg --configure -a**

Password:
** (I typed it in)**

and got this right after a brief pause:

pasha@pasha-desktop:~$ 


Now, whenever I choose to install a deb file with GDebi Package Installer, I says that i need to install one package which is *orbital-eunuchs-sniper_1.30+svn20060923-2_i386.deb*. This is a game that I tried to install at one point earlier on before the problem existed, but I couldn't due to the fact that I was missing some packages. When I try to install that package, it says that an existing version is already installed (Even though I clearly know I never have installed it). When I went into Synaptic Package Manager to delete it, it said that it is in a critical state, and needs to be reinstalled before it can be deleted. 

So basically, I can't remove the package (*orbital-eunuchs-sniper_1.30+svn20060923-2_i386.deb*) to reinstall it, and I can't install it using GDebi either. And I can't install anything else that is not connected to that program either, as it says that I am missing that 

The computer that I am using is old and I don't have an internet connection on it, so I can't download any packages or anything, but have to do it on a different computer and then transfer it onto this one with a flash drive. (Just a maybe useful piece of information).

Any help would be great. Thanks.

---

### Post by bapoumba on 2007-08-07
What is your sources.list:
```
cat /etc/apt/sources.list
```
and the complete output to:
```
sudo aptitude update
```

---

### Post by pah99 on 2007-08-16
Thanks for all the help guys. I'm not exactly sure of what happened, but it somehow stopped doing it, and Gdebi Package Installer works fine now.  Thanks though.

---

### Post by jacob01 on 2007-08-17
i have had random things like that happen but usualy there is like the update manager running or something else like that but usualy i loosit in a pile of windows

but yea glade you got it fixed

---

