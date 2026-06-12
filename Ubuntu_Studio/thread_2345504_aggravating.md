---
title: "aggravating"
date: 2016-12-04
forum: Ubuntu Studio
---

### Post by metalbiker on 2016-12-04
Can someone tell me why the software center for ubuntu studio keeps closing/crashing? this is highly annoying because i'm trying to find some software to use and this blasted thing keeps closing down. I love the new look but my goodness, how can anyone use it if it keeps crashing? Aggravating as hell. 

There needs to be a major fix put into place for the software center.

---

### Post by howefield on 2016-12-05
Try..

```
sudo apt update
```
```
sudo apt install --only-upgrade gnome-software
```

If that doesn't work, there are a few workarounds in this [launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1606238/"). There are likely to be many more bug reports.

---

### Post by ajgreeny on 2016-12-05
I would recommend that until the bugs have been squashed you use synaptic; it used to be the default package maneger for Ubuntu until a few years ago, and in my opinion is much more flexible in use than any of the software-centers.
```
sudo apt update
sudo apt install synaptic
```
Hopefully for those who prefer the software-centre or gnome-software, the bugs will eventually be squashed, but until then you will still have a GUI application that works very well.

---

### Post by CrocoDuck on 2016-12-05
Not an Ubuntu dude anymore, but I recall never been a fun of software centers. I always used synaptic (at the beginning) and later the terminal. I found that browsing online for programs and then check whether there is a package for them is much more effective, fast and easy than using a software manager, which are usually slow and may even report not accurate info. Also, they often not install packages properly: I had awful experiences with the old Ubuntu software center. All these software centers are just graphical front ends for the command line utilities, so by using the command line you gain efficiency, control and versatility. At least this is the point of view of guy like me...

Anyway, if you like graphical software centers and you feel they are really a good feature (even if they are just a quirky inconvenient way to use apt from my point of view) I suggest to contribute to the project. You will probably have to file a bug report to the gnome-software [package maintainers]("https://launchpad.net/ubuntu/+source/gnome-software") (as perhaps Ubuntu devs are modifying this software with respect [upstream]("https://wiki.gnome.org/Apps/Software#Getting_in_Touch")). Notice that there are 43 bugs open, so make sure to not open a duplicate one. You might want to [read about how to file a bug properly first]("https://help.ubuntu.com/community/ReportingBugs"). This makes you also understand that the devs are working to solve the problems.

---

