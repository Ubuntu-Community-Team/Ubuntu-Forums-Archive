---
title: "laptop-mode-tools 1.11"
date: 2006-01-10
forum: Requests
---

### Post by AgenT on 2006-01-10
This package in Dapper is currently at version 1.11. In Breezy, it is 1.05. A lot has [changed]("http://www.xs4all.nl/%7Ebsamwel/laptop_mode/tools/index.html") with bug fixes and new features, yet it does not depend on any new package. Many people use laptop-mode-tools [for those that don't know, you should install this on top of the old and very outdated laptop-mode package] so this update would be nice to have.

I have not tested whether or not this package will compile, but seeing that the requirements have not changed from the older version, it is safe to assume that it will.

---

### Post by tenshu on 2006-01-11
i don't know how people could use laptop-mode-tools
because it is just a fork started a year ago from laptop-mode wich is not mainted anymore by it creator.

If you try to use it it will be in conflict with laptop-mode
if you want to uninstall laptop-mode it will prompt you to uninstall unbuntu-desktop.

Hope dapper team will fix this :-/ (includin laptop-detect which fail to dectect laptop even if you activated it )

---

### Post by AgenT on 2006-01-11
First, while you are correct that laptop-mode-tools is an old fork of the kernel laptop mode, it is not actually a fork of laptop-mode. The package laptop-mode is a script that controls laptop mode, and is what seems to be an Ubuntu specific package. This whole issue is very confusing, but the nice thing is that it is not important when it comes to backporting this package.

A lot of people use it without problems, myself included. There is no conflict. If you look at what files both packages install, you will notice that laptop-mode-tools is just an updated version of laptop-mode (which is very limited). The package laptop-mode is installed by default in Ubuntu, and when laptop-mode-tools is installed, it replaces the scripts that laptop-mode uses (and adds a few extras). Understand that laptop-mode-tools is just a much more up to date with many more features version of the laptop-mode package. Installing laptop-mode-tools over laptop-mode is just like upgrading, except you now have two packages listed instead of one. But you are right, this is a bad way of dealing with this issue and laptop-mode should be replaced by laptop-mode-tools. The package laptop-mode should just become an empty package.

---

