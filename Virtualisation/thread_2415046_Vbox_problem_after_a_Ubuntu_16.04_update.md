---
title: "Vbox problem after a Ubuntu 16.04 update"
date: 2019-03-19
forum: Virtualisation
---

### Post by Gingalone on 2019-03-19
[ATTACH=CONFIG]282821[/ATTACH]I have WindowsXP running in Vbox installed in Ubuntu 16.04. After an update of Ubuntu a few days ago, Vbox does not start the WindowsXP machine with two warning boxes -see the attached screenshot. I did as instructed by the warnings:```
~$ sudo /sbin/vboxconfig
[sudo] password for ginus: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-setup.log to find out what went wrong.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.

```I had a look on the /var/log/vbox-setup.log file but, I have to admit, its content is beyond my linux expertise (I am a civil engineer, sorry about that!!).
I tried to solve the problem (as suggested by some post on web) removing completely VirtualBox with Synaptic, reinstalled it but got just the same result (process tried twice).
To my unskilled eye it looks the Ubuntu update removed something that was useless to Ubuntu but necessary to Vbox...
Thanks in advance for any help !

---

### Post by slickymaster on 2019-03-19
*Thread moved to **Virtualisation**.*

---

### Post by ajgreeny on 2019-03-19
Do you still have all the same folders and files in your /home that you had previously, particularly the hidden ~/.config/Virtualbox folder which is essential for running the VMs already on your machine.

Was your upgrade from 16.04 to 18.04 done online or was it a clean install?
Have you a separate /home partition or did you keep just your old data files, eg, Documents, Music, Videos, etc etc?

---

### Post by Gingalone on 2019-03-19
Thank you  ajgreeny, 
- the ~/.config/Virtualbox folder is there, 
- I did not upgrade from 16.04 to 18.04, I am still on Ubuntu 16.04, what messed my vbox machine was a normal Ubuntu update through Ubuntu update manager... 
- I have not a separate /home partition.

---

### Post by ajgreeny on 2019-03-20
What packages were upgraded at that recent upgrade?

Show us the output of ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and look for the date of the upgrade in the list of packages that will appear.

Someone here may be able to give you a clue about possible causes of your problem.

---

### Post by Dr._B on 2019-03-21
I have just had this exact same issue happen to me. Completely removing virtualbox (sudo apt autoremove --purge virtualbox*), followed by reinstalling from Ubuntu Software half-fixed the problem.

My half-fixed, I mean that windows will now "boot", but it only gets as far as the black screen with the blue window and the swirling circle of dots. Its been stuck on that screen for a good 20 minutes. EDIT: the correct version of the extension pack is installed, so that is not the issue.

[ATTACH=CONFIG]282830[/ATTACH]

And ideas what is going wrong?

---

### Post by slickymaster on 2019-03-21
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by Gingalone on 2019-03-22
Thank you ajgreeny, to avoid a long code box, I put the response of the command you suggested ```
grep -i " upgrade " /var/log/dpkg.log.1 /var/log/dpkg.log
```in the attached <VboxTrouble_Log-grep.txt> text file.[ATTACH]282831[/ATTACH]

---

### Post by Dr._B on 2019-03-22
I have found out what is going on. This is not a ubuntu issue, but rather due to an [incompatibility between the recent linux kernel update and virtualbox]("https://forums.virtualbox.org/viewtopic.php?f=7&t=91814"). 

Virtualbox is aware of the issue, but unfortunately it has not yet propagated the fix to a regular virtualbox distribution. The solution is to install a test build of virtualbox:
[LIST=1]
[*]Uninstall your current virtualbox distribution
[*]Download the [current virtualbox test build]("https://www.virtualbox.org/wiki/Testbuilds")
[*]Make the downloaded file executable
[*]Run from the terminal, using sudo (e.g. *sudo ./VirtualBox-6.0.5-129423-Linux_amd64.run* for today's  build)
[*]Update the guest additions in your guest(s)
[/LIST]

This has fixed my windows 10 guest in Ubuntu 16.04. Downside to doing this is that virtualbox will not auto-update, and if you want to update (or move to the normal distribution once the fix propagates to that) you need to use the .run file to uninstall the test build (e.g. *sudo ./VirtualBox-6.0.5-129423-Linux_amd64.run [COLOR=#000000][FONT=Verdana]uninstall[/FONT][/COLOR]*[COLOR=#000000][FONT=Verdana])*[COLOR=#000000][FONT=Verdana][/FONT][/COLOR]*

Bryan[/FONT][/COLOR]

---

### Post by Rick St. George on 2019-03-22
Also see my Post Here for step by step instructions and commands --> [https://ubuntuforums.org/showthread.php?t=2415212](https://ubuntuforums.org/showthread.php?t=2415212) which fixed same problem.  ;-)

---

### Post by ajgreeny on 2019-03-22
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 
It is a great help to users searching the forum.

---

### Post by Gingalone on 2019-03-22
Thank you Rick St. George, it looks the next update of Vbox (6.x something) will solve this bug (hopefully). I am more willing to wait for that rather than try to install a test version...

---

### Post by Gingalone on 2019-03-22
Thank you Rick St. George. I tried your fix and it worked for me as well! Thank you very much! 
I wonder if this incompatibility problem exists also with Ubuntu 18.04 (I have to install Vbox also in a new machine).

---

### Post by ajgreeny on 2019-03-23
> **Gingalone said:**
> Thank you Rick St. George. I tried your fix and it worked for me as well! Thank you very much! 
I wonder if this incompatibility problem exists also with Ubuntu 18.04 (I have to install Vbox also in a new machine).

No, it's not a problem in Ubuntu 18.04 as that does not use the same 4.4 series of kernels as 16.04; 18.04 uses the 4.15 series, and that has, so far at least, been perfectly good with VBox.

You might be able to overcome the problem in 16.04 by utilising the hwe updates to move your 16.04 install to the most recent kernel and xorg versions.
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for more information

---

