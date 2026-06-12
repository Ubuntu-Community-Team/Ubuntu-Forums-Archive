---
title: "Possible Infection?"
date: 2013-06-06
forum: Security
---

### Post by kevinharper on 2013-06-06
A few days ago I hooked up to a client's network. Some of the computers on the network were infected w/ various trojans, malware, and viruses.

Since then, when I turn on my computer, a couple of blank Chromium tabs launch on their own. Usually they wait for me to type my root pwd into the keyring.

I have not seen any processes running and nothing new has been added to my startup programs.

I did not install anything while on the network. What is the likelihood that my Ubuntu 12.10 desktop is infected? What could be causing the Chromium tabs to launch on their own at start up?

Additional note: I have been unable to install updates since.

Thanks guys.

---

### Post by CharlesA on 2013-06-06
What messages do you get when you try to update the machine?

---

### Post by cariboo on 2013-06-07
You more than likely are suffering from a browser hijack, I'd suggest you completely delete your chromium profile, located in ~/.config/chromium, and if you let google save your settings, log out, to see if that makes a difference.

---

### Post by kevinharper on 2013-06-08
@CharlesA:
This is the error:
> 
The installation or removal of a software package failed.


Details:
installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 301226 files and directories currently installed.)
Preparing to replace mac-os-x-icons 3.6~quantal (using .../mac-os-x-icons_3.6.5~quantal~NoobsLab.com_all.deb) ...
Unpacking replacement mac-os-x-icons ...
dpkg: error processing /var/cache/apt/archives/mac-os-x-icons_3.6.5~quantal~NoobsLab.com_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/mac-os-snow-icons/actions/gtk/media-playback-start.png', which is also in package mac-os-lion-icons-v2 3.0~quantal~NoobsLab.com
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mac-os-x-icons_3.6.5~quantal~NoobsLab.com_all.deb
Error in function: 



@cariboo907 I do not log into my Google profile. I removed and reinstalled Chromium, but it did not solve the issue: 2 blank Chromium tabs launch as soon as I enter my root password into the keyring.

---

### Post by CharlesA on 2013-06-08
You might have to purge the mac-os-lion-icons-v2 3.0~quantal~NoobsLab.com package and install the newer version. That shouldn't happen, though.

---

### Post by kevinharper on 2013-06-09
@CharlesA Yeah, I thought about that so I decided to simply uninstall 12.10 and install 13.04. Finished configuring this new install a couple of hrs ago.

:) Glad to report that it is running slightly faster than before and I am having no issues what-so-ever.

I kind of wish I hadn't installed the new OS because I really want to know what was going on w/ Chromium.

Thanks a bunch guys.

Edit: Sorry guys, not seeing the "Solved" option in "Thread Tools" drop-down; Forced to leave it as is.

---

### Post by CharlesA on 2013-06-09
> **kevinharper said:**
> 
Edit: Sorry guys, not seeing the "Solved" option in "Thread Tools" drop-down; Forced to leave it as is.

Marked it as solved for you. You can find out how to mark it as solved from here:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by paperplate9 on 2013-06-09
> **kevinharper said:**
> I decided to simply uninstall 12.10 and install 13.04

That's no fun! ;)

---

