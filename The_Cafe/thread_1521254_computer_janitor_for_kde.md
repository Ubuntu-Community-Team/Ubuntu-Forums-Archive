---
title: "computer janitor for kde?"
date: 2010-06-30
forum: The Cafe
---

### Post by cespinal on 2010-06-30
quick question... I have bloated my system with lots and lots of software I am not using anymore... 

I dont know for sure if linux gets slower over time, but I do believe refreshing my system just wont harm 

is there any friendly way to achieve this? doing a fresh install just beats one of the main points of migrating from windows...so I would like to run an app or command that gets rid of a whole bunch if installed apps...  

thanks for the advices kiddos :P

---

### Post by ajgreeny on 2010-06-30
Just remove the applications you definitely don't use, then either in synaptic use the **Status->Installed (auto-removable)** from the left hand column, or simply use ```
sudo apt-get autoremove
``` in terminal to get rid of any dependencies of those applications.  I prefer the synaptic route, as it is much easier to see what is about to be removed, and decline to allow some of those to go by using the **Custom Filters->Marked Changes**, again available in the left column.

Or, of course you could just do nothing!  Ubuntu and other Linux distros do not generally get slower when applications are added; it may make the menus more difficult to navigate, but there is no huge registry file that can bog down the system, as Windows has

---

