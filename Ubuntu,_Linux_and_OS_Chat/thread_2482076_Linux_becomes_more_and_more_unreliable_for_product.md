---
title: "Linux becomes more and more unreliable for productive use"
date: 2022-12-18
forum: Ubuntu, Linux and OS Chat
---

### Post by KMK_ECS on 2022-12-18
Hi all,

I apologize in advance for this posting but I am getting increasingly frustrated over the recent years with Linux and was wondering if I am just unlucky or if this is a general trend.

I have noted that over the last few years I have more and more crashes on Linux. It started on Linux Mint Cinnamon with random crashes during Zoom conferences when I was using Open Office as well. The computer would just freeze and only a hard reset would make it usable again. I thought it might be Mint and the Asus laptop I was using so I upgraded to a Framework laptop and Ubuntu 22.10. Now the Desktop environment crashes randomly, often when I am using Freecad but also unpredictably at other times. Sometimes I can login again and it may have the programs still running, sometimes it requires a reboot through another terminal. This is not weekly but may occur 1-2x/month. As I am using my computer for productive work, this is not acceptable. My windows PC at work is much more reliable.

I can understand that single programs may crash at times but it speaks of bad design of the Desktop Environment if a program can crash the whole desktop environment. I am starting to wonder if the developers have lost track of their code and we are working with systems that are full of bugs. I even cannot help finding the issue as there is no error message, not even in the logs (at least I cannot find one). I suspect the crashes may have something to do with my setup as I am using the internal computer screen and two external 4k monitors. Also, I am not using stock Gnome but have installed the ArcMenu and Dash to Panel extensions. If this suspicion is correct then it would support the notion that the software is not properly written with appropriate error handling but just made to work on a mainstream setup. 

I am really starting to consider switching to Windows or even try out Mac. I am using Linux since  nearly 20 years (mainly Ubuntu, then Mint Cinnamon to avoid Unity) and it has always been rock solid until about 2-3 years ago.

Has anybody observed a similar trend? Are there any suggestions on how to avoid such issues? 

Many thanks and best wishes

Karl

---

### Post by QIII on 2022-12-18
No, I haven't noticed any such trend.  Rather the opposite.

And if Windows or Mac work better for you, then use them.

---

### Post by Tadaen_Sylvermane on 2022-12-18
I've had the occasional crash over the years. Not often. If Linux or Ubuntu isn't working for you there is nothing wrong with another distro, personally I'd pick Debian, or go back to Windows. No one will be offended. You have to do what works for you. Sometimes it won't be what you want but  if it does the job properly then so be it.

---

### Post by zebra2 on 2022-12-18
I haven't had any problems and I stay on the cutting edge where problems are expected.  Usually production machines are spec'ed out by IT professionals to meet the requirements of the objective task. With Linux that usually means Linux Certified systems which can't be altered by the end user. If I were you I would consult with your IT department and see if they can design something more appropriate to your production needs.  
That would be my suggestion. I'm sure there are others.

---

### Post by agentl074 on 2022-12-19
Hmm... weird... I use both Mint and Ubuntu and I have found both to be significantly more stable than Windows. I have had some crashes, but to be fair, this was due to my experimentation with extensions rather than proven apps. I have also noticed that some hardware contain blobs and some other things that do not play well at all with Linux. While Ubuntu is generally very friendly with most machines, some machines do contain modifications to the hardware that may not work 100%. Ubuntu certified machines -- or machines that are custom built -- would secure the best experience. 

I have found that the older Asus machines with Intel hardware work beautifully; however, the newer Asus with AMD hardware also had some blobs or custom BIOS that did not play well with regard to the display functionality. 

You can try the old sudo apt update && sudo apt upgrade and see if that helps -- this solves a lot of Linux issues since Linux likes to be up to date.

---

### Post by TheFu on 2022-12-19
Computer crashes can almost always be traced back to 
a) hardware faults
b) improper configuration
c) crappy drivers

An application program should never cause a system crash.  However, some application programs can push hardware beyond the limits and that might cause a system crash.  

If there aren't any errors/warnings in the system logs, I'd suspect a power supply issue or GPU driver problem, especially if using a laptop or nvidia GPU.

The last system crashes I had was about a year ago and some transcoding software seemed to be causing the issue.  "Seemed" being the key word.  It was pushing all 6 cores (12 threads) hard and that was causing some unmatched RAM faults/failures.  In my case, I set the RAM to be a little slower in the BIOS until it became stable.   It has been very stable since:
```
# uptime
 13:16:54 up 14 days,  4:05,  5 users, 
```
Another system:
```
$ uptime
 13:17:27 up 14 days, 18:22,
```
I reboot after patching and only when needed due to a new kernel or libc.  I don't run bleeding edge software.  New is the enemy of stable. Always remember that.  I don't patch daily.  I run dangerous software inside constrained containers.  I don't use the fancy GUIs either.  My WM has been stable with few changes since 2005-ish.  This is good because the new, fancy, DEs don't impact me and I don't have to figure out much that is new.  New isn't better. It is usually just new and full of new bugs.

All software has bugs, usually thousands to millions of bugs, depending on complexity.  Long ago, I worked on software that being bug-free was the main goal, regardless of cost.  The year I changed jobs, it was believed no more critical bugs existed in the software.  Alas, the govt program kept running for another 16 yrs (or so).  During those 16 yrs, over 100 critical bugs were found that existed in the software when it was declared bug free.  A critical bug was something that would cause "total loss of vehicle and crew".  What this shows is that any non-trivial software, even when being perfect is the main goal, will have bugs, serious bugs.

BTW, MS-Windows bug list was over 350K last time I looked.  So they are just better at hiding or ignoring the bugs.  Everywhere I worked, we had monthly rebooting for MS-Windows Servers, "just because", not for any specific need.  Unix and Linux systems would only be rebooted as needed and only during pre-approved maintenance windows.

Desktops are completely different and people are willing to have less stability to have "pretty" interfaces.  That's been proven since MS-Windows 1.x was released.  People forget how unstable Windows has been over the years.  NT4 was the first time I'd get good uptimes from Windows.  WinXP wasn't as good. Win7 was a massive improvement over Vista, if you didn't need to patch.

Now that MSFT forces patching, their uptimes are terrible again.  It is one things to have nags that a reboot is needed and completely different to force a reboot like MSFT does.  Canonical is headed in that way, it seems with their snap packages.  
[https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/](https://www.circusscientist.com/2022/12/18/ubuntu-snap-update-spoiled-the-world-cup/) ... a guy was watching the World Cup finals through a paid streaming service ... then the firefox snap decided to update.  He ended up watching the rest of the game on his phone, because the snap updates and his attempt to get the game back left the system in a non-booting state.  Sure, this was self-inflicted ... but we shouldn't blame Linux for Canonical's choices.

---

### Post by KMK_ECS on 2022-12-20
Dear all,

Many thanks for the feedback!

I am starting to wonder if this may be related to the extensions I was using. I have now resetted the whole cconfiguration to default values ( dconf reset -f / ) and will only use the standard Ubuntu extensions. Hopefully that solves the issue.

---

### Post by monkeybrain20122 on 2023-02-01
I have not had any crash. I have gotten into troubles but they are all self induced because I was messing around with the system, not Linux fault.

---

