---
title: "Ubuntu Cleaner"
date: 2020-08-21
forum: Ubuntu, Linux and OS Chat
---

### Post by exploder on 2020-08-21
I watched a YouTube video about Ubuntu 20.04 recently and the guy mentioned installing Ubuntu Cleaner. I was curious because I had installed Ubuntu for a family member that ran into an issue with so many old kernels that the computer would barely boot up. Most of us know the command to take care of this pretty easily but this guy had no interest in learning commands, he was just a computer user. Mint has tools that remove old kernels but he really likes Ubuntu. Bleach Bit could do the job but there is no way I wanted this guy using it.

After seeing Ubuntu Cleaner in the video I did a search and found it.

[http://ubuntuhandbook.org/index.php/2016/12/ubuntu-cleaner-ubuntu-tweak-alternative-janitor/](http://ubuntuhandbook.org/index.php/2016/12/ubuntu-cleaner-ubuntu-tweak-alternative-janitor/)

The tool seems harmless enough that a new user could clean up their system without trashing it, lol. I wonder why Ubuntu stopped including this kind of tool? Years ago Ubuntu came stock with Computer Janitor or something like that. Ubuntu Tweaks had this feature, this is forked from it. Wouldn't it be a good idea to include this or maybe modernize it a little?

---

### Post by TheFu on 2020-08-22
Kernels should be removed automatically. But there are 50+ different ways to install any Linux, so it is possible to setup a system that either has nearly unlimited space for kernels or is really tight on space for kernels.  The person who does the install handles that.

I've never seen the point of cleaning software.  Just automate any cleanup in a script that gets run every day - week - month. Put the running of the script into the user's crontab or for system level stuff, put it into one of the crontab /etc/cron.* directories.  Daily, weekly, monthly.  Easy peasey.  Handled.

---

### Post by exploder on 2020-08-22
@ TheFu

I don't disagree with you. I was mainly referring to new users with no experience. There are claims that more people are moving to Linux for various reasons we won't get into here. My thoughts were about making system maintenance easy for those that install a distro on their own. The guy I used as an example really grew to like Ubuntu, he had used it a few years before he had the issue with a slew of kernels on his system. It took minutes to fix the problem when he brought me his computer. If he had a simple tool he could have solved the problem himself. You and I are experienced users, we take care of this type of thing and never give it a thought.

---

### Post by TheFu on 2020-08-22
Years ago, I wrote an article about this stuff.
[https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)
It is slightly dated by the backup choices, but still relevant for most other stuff.

Over the years, I've updated it here: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

The best maintenance happens automatically, so we don't need to think about it at all, provided it does no harm and actually does what is needed, when needed.

---

### Post by exploder on 2020-08-22
Very nice!

---

### Post by zebra2 on 2020-08-23
Other than deleting unneeded kernels an running autoremove I don't use cleaner programs.  They are common is Windows but not much needed in Linux unless /root space is getting whelmed. Plus, cleaners can take you to the cleaner.  In the same vein, as the Ubuntu OS gets larger and the hard drives get larger it wouldn't hurt to reevaluate your space needs and increase the size of your /root partition.  If you run out of /root you will crash. Seems to me.

---

### Post by exploder on 2020-08-31
Got the chance to test out Ubuntu Cleaner with removing old kernels today. It did the job, left a few residual configs but seems like a good solution for new users.

---

### Post by TheFu on 2020-08-31
> **exploder said:**
> Got the chance to test out Ubuntu Cleaner with removing old kernels today. It did the job, left a few residual configs but seems like a good solution for new users.

```
sudo apt autoremove
sudo apt autoclean

``` Since 16.04, nothing else should really be necessary.

I would NOT suggest people blindly increase the size of /, unless it is less than 30G.  If it is over 30G, something else is wrong and steps should be taken to correct those other issues.
```
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   17G  8.5G  7.4G  54% /

```
That's a 20.04 desktop.  The trick is that /home is mounted to different storage.
```
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-home ext4   12G  6.0G  5.3G  54% /home

```
/boot is part of / on this system - it uses legacy boot, not UEFI.  On systems with a separate /boot/, then I'd run **sudo apt autoremove** every 2 weeks.

---

### Post by exploder on 2020-08-31
@ TheFu

Thank you for the clarification about the commands. There is a lot of old information out there. You've got me thinking that maybe it would be a better idea to explain this to new users and save the information in a text document until they get used to the commands. You drove home the point that there really isn't that much to keeping things cleaned up. The user that had the issue was using legacy boot.

---

### Post by lammert-nijhof on 2020-09-07
I use Ubuntu Cleaner and I have used it for a long time. It works reliable for the LTS releases, it did not work for for 19.10. Basically I run it after each update and I can assure you, that it removes stuff every time I use it!!! How much depends on the flavour of Ubuntu. For some flavours it removes hundreds of megabytes. You can use apt autoremove, autoclean and clean, but I prefer the GUI.

---

### Post by SeijiSensei on 2020-09-07
If you want to run autoremove and autoclean regularly, I suggest setting up a cron job.  Create a file in /etc/cron.daily/ as root with sudo (e.g., "sudo nano /etc/cron.daily/cleaner") with these lines
```

#!/bin/bash

apt autoremove
apt autoclean

```
then make it executable with "sudo chmod u+x /etc/cron.daily/cleaner".

You should be all set. You don't need "sudo" in front of the apt commands because all these scripts run with root privileges.

---

### Post by exploder on 2020-09-07
That's a great idea! Thanks!

---

### Post by TheFu on 2020-09-07
> **exploder said:**
> @ TheFu

Thank you for the clarification about the commands. There is a lot of old information out there. You've got me thinking that maybe it would be a better idea to explain this to new users and save the information in a text document until they get used to the commands. You drove home the point that there really isn't that much to keeping things cleaned up. The user that had the issue was using legacy boot.

There are thousands of commands and options that users could use, but until they are ready, it is almost always a waste of time to provide them in advance.

With each release, something changes.  What changes is always different.

There are all sorts of beginner guides out there. Some are written by knowledgeable people and others are not. When someone is really new, they should only follow guides for the exact release they are running and written by reputable people or posted on reputable sites.

Linux knowledge isn't like an encyclopedia. It is like a novel.  Windows skills are like an encyclopedia.  Even if you don't really know what you are doing, you can jump to the middle of the "T" book, find a guide for some task that begins with "T" and follow the steps.  That's good and bad, because it means if you don't want to do it the way those steps say or you want to swap out one of the components for a different solution, then you cannot.  

Linux isn't like that. Skills build on other skills. If you jump to the "T" chapter in the novel, you'll be lost, because you didn't learn A, B, C, .... R, S, first.  Also, there are usually 3-10 solutions for any step in a problem. Sure, we can all run BIND for DNS, but some people only need dnsmasq or one of the 5 other lite-DNS solutions.  The solution just requires DNS, period. It doesn't care which solution we plug in.  Same for most things.  

Which file system should a desktop use?  On Windows there's 1 choice. NTFS. On Linux, there are 20 choices, each with a specific set of pros/cons.  How do you explain that to someone who never new or considered that NTFS wasn't the only file system for a hard drive or SSD?  They don't know to think that way, but file system choice is very important for a server and to extend the life of any flash storage.

So, how do we provide the right information at the point when a user needs it?  Historically, mentoring was how that happened. Today, if you don't work in a group with some Linux mentor assigned, these forums and a local LUG are the way to get that knowledge transfer.  My LUG has at least 2 meetings every week and one major meeting a month. These happen at 3 different locations around our metro area, so people from all over can probably make it to one of them. One is on weekends, the others are weeknights.  Most areas have LUGs, IME.  And if your area of the world doesn't, now is a great time, since COVID has made lots of LUGs move online. That means that anyone can join from anywhere in the world.  If you seek a mentor-like situation, use the web search tool you like and search for a LUG in your part of the world. You may be surprised. Don't just look by city. Use informal regional names and colleges and universities too.  Usually, even if they meet at a college, there's no requirement to be a student to attend LUG meetings.

---

### Post by exploder on 2020-09-08
@ TheFu

You are right of course. I remember when my step dad was alive, he would buy out of date books on Ubuntu and wonder why the information was useless. He could never get the hang of installing multimedia codecs. I kept telling him the instructions were in the forum and all he had to do was copy and paste into the terminal. He kept on buying the books and I kept installing the codecs for him! I have used forums for over 16 years and the occasional Google search these days. There are no local Linux groups around here... Most people don't even know what you are talking about when you mention Linux!

The tech school I went too claimed I had to use Windows and Microsoft Office. Office crashed and I lost a paper I had spent hour on. I used LibreOffice after that and just saved as a .doc, they never knew the difference. Ball College proclaim themselves as a Mac campus. They used to teach "advanced computing" at the tech school. My step dad took the class. I helped him with his homework once, they were using Ubuntu. I rattled off all the answers in a couple of minutes. He asked me how I knew all the answers, I told him it was all basic stuff a new user learned right off the bat.

Asking questions on a forum goes a long way in my point of view. You can get many points of view and new things to think about.This post alone has given me different ways to tackle a problem I had not thought about.

---

### Post by aaronrv2008 on 2020-09-09
Ubuntu Cleaner is a great tool, I have been using it for a long time and just works.

I have heard about Stacer, but the PPA does not work a expected. BleachBit is good too, but Ubuntu Cleaner because the UI is simple to navigate.

---

### Post by CelticWarrior on 2020-09-09
> 
[COLOR=#000000]I have heard about Stacer, but the PPA does not work a expected.[/COLOR]

If you're running 20.04 then Stacer is to be installed from the repos, not the PPA.
```
sudo apt install stacer
```

---

