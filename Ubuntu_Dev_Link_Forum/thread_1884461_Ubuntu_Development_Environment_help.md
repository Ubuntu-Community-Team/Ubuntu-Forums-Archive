---
title: "Ubuntu Development Environment help"
date: 2011-11-21
forum: Ubuntu Dev Link Forum
---

### Post by jkozer26 on 2011-11-21
Hi All,

I am looking for some help/suggestions to set up a scalable and faster development environment using ubuntu and running eclipse. 

Right now all of our developers are running windows 7 as a base operating system with Outlook for email and will use Visual Studio  for development. In other words getting rid of Windows completely is not an option as much as I would like to.

Right now we have ubuntu desktop edition 11.04 with eclipse running on Oracle Virtualbox. As you can probably guess this is very SLOW and will often spike VM up to 90% on my laptop with an intel I5 core with 4GB of ram. 

I know another option is do a dual boot but this has disadvantages as as well because we will not have access to email or our internal corporate IM utility - by Microsoft also - unless we reboot. 

Another idea is to have a centralized server and each developer can use a remote utility like Tight VNC or something like that. My concern here is latency since we can do that now with a development server in the same building and it is painful to use.

Is the ultimate solution going to be that each developer has to get their own desktop specifically for open source development? I am hoping that someone out there has had this problem and perhaps can provide some details on how they solved it. Thanks!

---

### Post by skotos on 2011-12-14
Probably I miss something because I have been personally running Eclipse natively under Linux without any virtual machine and on Windows as well.

The only thing I particularly appreciate is running Eclipse by [Pulse]("http://poweredbypulse.com") because this small app is available for free even for commercial purposes as long as you do not need centralized profiles to share with your coworkers (that you might probably later appreciate).

I generally download and run it on every system I have an account on: this app lets me install any Eclipse version starting from 3.3 up to the latest.

Building one or more personal Pulse profiles will let you have all the required software plugins automatically installed on whatever system you like: it is just a matter of providing it your personal email and password and choose your configuration.

Further on, whenever you need a plugin that is not in the list, you can simply add your repo and find it immediately, and automatically deliver it to your other workstations as soon as you run the Pulse update (at least once a week) on each of them.

Using Pulse, in fact, the configuration issues and redundancies are cut down quite a bit, but they are on a user base: I mean that Pulse will not give you a system wide installation, but a user one, as far as I know.

Every time I run a system wide installation, be it on Ubuntu either on  Arch, I always get - in the mid term - into some security/configuration issue that I never  face when I run it by Pulse that automatically takes care of all for me.

To work happily with it, you just have to avoid local modifications that the Pulse installer is not aware of.

If you are not satisfied, you can simply modify/uninstall it by running Pulse again.

Since I have no experience with Visual Studio, I think that you might get problems if you need to run Windows only plugins on a Linux box because there is no way to run them without a virtual machine, but that I think it should be the only case.

I have been running the free Pulse versions for a few years to develop on PHP (PDT) and C/C++ (CDT) and I am very comfortable with it, so much that when I suggest it people sometimes suspect I work for them, but I am not.

If I were you I would simply give it a try to check whether it answers your question.

---

