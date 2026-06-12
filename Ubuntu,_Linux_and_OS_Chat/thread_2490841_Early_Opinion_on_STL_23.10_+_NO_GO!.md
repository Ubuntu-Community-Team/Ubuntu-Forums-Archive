---
title: "Early Opinion on STL 23.10 + NO GO!"
date: 2023-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2023-09-18
Hello All,

I’m posting at the “water cooler” because I don’t have a specific problem to resolve but just want to make some comments about the next STL Ubuntu iteration 23.10, due on October 12.

I’ve been running Linux since Ubuntu Dapper Drake, before that I started with RHEL, a boxed version with paid phone support (I needed one phone call!). For a while I ran SuSE side by side with Ubuntu.

Although I miss the additional panels of MATE and the ability to configure them precisely, as well as place apps on the Desktop, MATE has a lot of glitchy stuff. What I like best about Ubuntu is that, at least for me, nothing is broken, the OS stays out of my way and let’s me do work or have fun without being bothered by persistent failures that have no solution.

At the moment I’m running 22.10. It no longer supports updates and upgrade fails with error messages. Over the years, I’ve assembled a Dropbox "Linux Clean Install" folder that allows me to do a pretty rapid configuration, after a clean install, in about two or three hours. For example, for CLI install commands of various programs, I will copy/paste history from the terminal. I will take a screenshot of my Desktop and note the order of programs on my Taskbar, etc.  Sometimes, it’s easier for me to do a clean install than it is to resolve a problem such as, in this case, an error message indicating failure to upgrade. 

In addition to wanting to do a clean install for the above reason, I also want to switch from a 0.5 TB ssd to a 2.0 TB ssd. 

So I thought I would check out 23.10 in a virtual machine and wait for October 12. 

Sure, it’s too early in the game to make pronouncements about 23.10, but based on my experience thus far, it comes up “all bad news.” I didn’t even complete my normal configuration, and already I have a list of six problems. My conclusion is to avoid 23.10 and install LTS 22.04.3 which is supported through 4/27. Since I’m 70 years old, it could outlive me!

Here are the problems. A given single problem is not a sufficient deal breaker but, collectively, the problems indicate a deal breaker. I seriously doubt that all these problems are magically going to disappear when the final version comes out.

(1) There are lots of default Ubuntu apps that I never use and always uninstall. This time, when I go to Store, to find the list of installed apps, from which I can uninstall, it doesn’t exist. There appears to be no way to uninstall apps!

(2) As a workaround, I used CLI to purge Mines. Bad news! A whopping 150 MB and many files from LibreOffice were also purged! What the hell? A game with LibreOffice dependencies? So I don’t trust that work around.

(3) Further, when I go to the grid for my installed apps and confirm that, yes, Cheese is installed, which I want to remove, I then go back to the store, search for Cheese in order to remove it and the Store says it is not installed = false! Another deadend.

(4) Constant freezes and crashes of the VM—never happens with other test distros.

(5) Gmail in Chromium has weird graphics defects—no go for this browser and gmail.

(6) Heretofore, Activities as the default workspace switcher has worked great. Now it is replaced with a bar and dots icon. O.K. But I only have two desktops and I can find nothing in the switcher or in settings that allows me to designate how many workspaces I want. Maybe there is a way but it’s hidden. Workspaces are critical to my workflow and this is bad news.

I was much looking forward to this iteration but I’m staying away and installing the LTS.  Not one of the above problems will exist in the LTS. 

Thoughts, opinions?

---

### Post by Dennis N on 2023-09-18
> (1) There are lots of default Ubuntu apps that I never use and always uninstall. This time, when I go to Store, to find the list of installed apps, from which I can uninstall, it doesn’t exist. There appears to be no way to uninstall apps!

By "Store" you mean the "App Center"? From what I understand, this replaces "Ubuntu Software", but for now at least there are only snap packages. If you want to install or remove .deb packages, use Synaptic Package Manager, Gnome Software, or the terminal. You will first have to install either of the first two with apt in the terminal.

Note:
These comments are based on the daily build of Sep 8.

---

### Post by grahammechanical on 2023-09-18
It is my understanding that from Ubuntu 23.10 onward the installer will let us choose between doing a Normal installation or Minimal installation. 

See this thread

[https://ubuntuforums.org/showthread.php?t=2490772](https://ubuntuforums.org/showthread.php?t=2490772)

The Minimal install brings in a web browser and basic utilities. I expect the same situation will exist for 24.04 LTS when it comes out and onward.

Regards

---

### Post by grahammechanical on 2023-09-18
Some added information regarding the change from Ubuntu Software to the App Center. 

[https://www.omgubuntu.co.uk/2023/09/ubuntu-app-center-app-arrives](https://www.omgubuntu.co.uk/2023/09/ubuntu-app-center-app-arrives)
 
As we know, standard support versions of Ubuntu are places where change/improvements are trialled. Hopefully, the new App Center will be working as intended by the time 24.04 is released.

Already in 20.04 and upwards many of the usual Gnome apps are available as snap packages that can be installed as replacements for the deb version.. I suspect that fresh installs of 23.10 and 24.04 will have these Gnome utilities as snap packages by default.

Upgrades from 22.04 to 24.04 may result in deb packed utilities being replaced by the snap versions.

Regards

---

### Post by ian-weisser on 2023-09-18
> **Kurt_Alan said:**
> I’m posting at the “water cooler” because I don’t have a specific problem to resolve

Seems like you found at least five specific problems (bugs) that you want resolved.
Please take a few minutes to troubleshoot and report the bugs properly.
This is the perfect time to file 23.10 bugs. Don't wait; the window closes in two weeks (Final Freeze), so get those bugs reported NOW.

---

### Post by Kurt_Alan on 2023-09-19
> **Dennis N said:**
> By "Store" you mean the "App Center"? From what I understand, this replaces "Ubuntu Software", but for now at least there are only snap packages. If you want to install or remove .deb packages, use Synaptic Package Manager, Gnome Software, or the terminal. You will first have to install either of the first two with apt in the terminal.

Note:
These comments are based on the daily build of Sep 8.

Thanks. Maybe so. But this is a non-issue in 22.04.3 LTS, which I've now installed and configured.

---

### Post by Dennis N on 2023-09-20
> Thanks. Maybe so. But this is a non-issue in 22.04.3 LTS, which I've now installed and configured. 
Yes, most here (myself included) would recommend and use the LTS versions for daily use. The pre-release daily iso version you must have used is going to have temporary problems of one kind or another. So you should wait for the actual release of Ubuntu 23.10 for best results.

I install these short-term releases in VMs to see the evolution of the OS. The first appearance of Gnome 45 is the big feature in Ubuntu 23.10. If you want to see how that is different from Gnome 44 or 43, you take a look.

---

### Post by Kurt_Alan on 2023-09-20
> **Dennis N said:**
> By "Store" you mean the "App Center"? From what I understand, this replaces "Ubuntu Software", but for now at least there are only snap packages. If you want to install or remove .deb packages, use Synaptic Package Manager, Gnome Software, or the terminal. You will first have to install either of the first two with apt in the terminal.

Note:
These comments are based on the daily build of Sep 8.

Yeah, "Store," "App Center," "Ubuntu Software," it's all the same, call it what you wish. Whatever happens to be the latest name, it's the new GUI repository that's the new "go to" after Synaptic.

---

### Post by Kurt_Alan on 2023-09-20
What scares me is that the complaints I've noted may not be temporary problems but new and permanent features of this OS iteration. Workspaces is a disaster. I spent half an hour trying to figure out how to add workspaces and couldn't do it. In the LTS it was a no brainer. In two minutes I found the setting where I could choose dynamic workspaces or set a fixed number. And the Store? Not being able to uninstall unwanted (installed apps) is a step back, not forward.

---

### Post by Kurt_Alan on 2023-09-20
These are not bugs! These are new features that, in my estimation, represent a step back and seriously impede work flow.

---

### Post by ian-weisser on 2023-09-20
> **Kurt_Alan said:**
> (1) ... when I go to Store, to find the list of installed apps, from which I can uninstall, it doesn&#8217;t exist.

Seems clearly a bug. Please report it properly. What leads you to believe this is intended behavior or a design decision?

> **Kurt_Alan said:**
> (2)...I used CLI to purge Mines. Bad news! A whopping 150 MB and many files from LibreOffice were also purged! What the hell? A game with LibreOffice dependencies?

I could not reproduce this in a test environment. If true, seems like a bug. Please report it properly with enough information to be reproducible.

> **Kurt_Alan said:**
> (3)...Cheese is installed, which I want to remove, I then go back to the store, search for Cheese in order to remove it and the Store says it is not installed = false!

Seems clearly a bug. Please report it properly. I could not reproduce this in a test; cheese showed up in the store and was uninstallable.

> **Kurt_Alan said:**
> (4) Constant freezes and crashes of the VM

Assuming your VM has enough resources (check that!), please report freezes and crashes properly to the bug tracker. Include the .crash file or core dump, of course.

> **Kurt_Alan said:**
> (6)...I can find nothing in the switcher or in settings that allows me to designate how many workspaces I want....

That one is indeed a design decision. Send your feedback to Gnome, who made it that way.

I stand corrected: Four bugs instead of five. Great that you found them!

---

### Post by Dennis N on 2023-09-20
Fixed Workspaces:
Settings > Multitasking > Workspaces
Change from Dynamic to Fixed and enter how many you want.

---

