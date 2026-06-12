---
title: "Kernel panic during upgrade, and ensuing unpleasantness"
date: 2010-02-11
forum: System76 Support
---

### Post by Schrollini on 2010-02-11
My new Starling arrived today, looking ever so cute.  I played around with it for a bit, and everything seemed to be working just fine.  Noticing that the package definitions were a month out of date, I told Update Notifier to check for updates and to upgrade the hundred-some-odd eligible packages.  Downloading them went fine, but halfway through the installation, the machine froze solid.  The screen went black with a blinking white cursor and the Caps Lock light flashed slowly.  I couldn't switch to a VT, nor could I reboot with magic SysRq commands.  Therefore, I'm guessing this was a kernel panic.

I hit the power button to reboot.  The OS seemed to come up okay, but the keyboard and trackpad were inoperative at the login screen.  I managed to get to a VT by first setting the keyboard to raw mode (Alt-SysRq-R) and then switching to TTY1 (Ctrl-Alt-F1).  From there, I completed the update with `sudo dpkg --configure -a`.  This worked, except it needed to download something to complete the installation of the new kernel.  (I'm puzzled by this, since everything seemed to have been downloaded before the upgrade started.)  So I plugged in an ethernet cord and re-ran the dpkg command.

Another reboot later and the login screen was still locked up.  Luckily, the solution from [this post by thomasaaron]("http://ubuntuforums.org/showpost.php?p=8773317&postcount=2") worked for me.  (I ran the commands with sudo from a VT instead of using recovery mode.)

Another reboot and I could log in.  But now wireless wasn't working.  The network connections icon wasn't showing the wireless device at all, and `ifconfig` wasn't listing wlan0.  [This thread]("http://ubuntuforums.org/showthread.php?t=1400323") suggested that the new kernel was to blame, so I tried rebooting with an older kernel.  This didn't improve anything (other than that the network connections icon listed the wireless device, but informed me that it wasn't properly configured).  After a few dead ends (including reinstalling the System76 drivers), I recalled the problems I had upgrading the kernel, so I thought to reinstall those packages.  I decided to reinstall the most recent linux-headers and linux-image packages (linux-headers-2.6.31-19, linux-headers-2.6.31-19-generic, and linux-image-2.6.31-19-generic, in my case) through Synaptic (right click and select "Mark for Reinstallation").  One final reboot, and everything seems to be working again.

So why am I posting this story, if everything's working?
[LIST=1]
[*]I wanted to check if Update Notifier is the right way to go about updating them machine.  Is there a System76-specific way I should know about?
[*]I wanted to post my solutions in case they save someone else these headaches.
[*]I wanted to alert System76 to these problems, in case they can prevent them in the future.
[*]Finally, I have a few suggestions for mitigating these problems.  I don't know if they're at all feasible, but here they are:
[LIST]
[*]System76 could perform a dist-upgrade before shipping the machine.  This would both give them a chance to see these problems, as well as decrease the likelihood of users running into them later (as the users would not have as much to upgrade).
[*]Installing the System76 driver could trigger the reinstallation of the current kernel packages.  I notice that there seems to be some additional actions hooked onto the kernel installation that seem to be related to the drivers; it might be good to ensure that this gets run when drivers are updated.
[*]Perhaps System76 could host their own versions of the kernel that already have these additional drivers built in, so there doesn't have to be an additional, unexpectedly late download during the upgrade process.
[/LIST]
[/LIST]
I hope this is of some use to someone.

---

### Post by thomasaaron on 2010-02-11
> 1. I wanted to check if Update Notifier is the right way to go about updating them machine. Is there a System76-specific way I should know about?


Update Manager is fine.

   > 2. I wanted to post my solutions in case they save someone else these headaches.

Always a great idea.

   > 3. I wanted to alert System76 to these problems, in case they can prevent them in the future.

We're aware of the issue. But a) it doesn't seem to happen across the board, and b) we've not yet been able to isolate it.

   > 4. Finally, I have a few suggestions for mitigating these problems. I don't know if they're at all feasible, but here they are:
          * System76 could perform a dist-upgrade before shipping the machine. This would both give them a chance to see these problems, as well as decrease the likelihood of users running into them later (as the users would not have as much to upgrade).

We actually update our imaging server whenever a new *kernel* update comes down the pike. However, there is naturally a lag between the update becoming available, testing (and solving problems), and the server image being updated. 

Updating the image every time a *general* update comes down the pike, though, would be prohibitively time consuming, as would be running updates individually on every machine. I believe we *did* do this in the early days, when we were one-at-a-timing machines. But now we are producing on a much larger scale, and streamlining has become very important... and somewhere along the line running individual updates on every machine fell out of fashion. 

That said, I will bring it up to my managers. The idea isn't a bad one at all.

In this case, there seems to have been some problems with this -19 kernel. And since customers are constantly updating, it's inevitable that if there is a bug, customers will experience it before we've finished testing... as we see the updates the same time you do.

          > * Installing the System76 driver could trigger the reinstallation of the current kernel packages. I notice that there seems to be some additional actions hooked onto the kernel installation that seem to be related to the drivers; it might be good to ensure that this gets run when drivers are updated.

That's an EXCELLENT point. Here's what you're seeing. We're doing an experiment (and trying to refine it): Under 9.04, kernel updates would break the wireless driver (which was compiled against the kernel). This is something we definitely want to fix. It's ridiculous for customers' wireless to die every time there's an update, so we hooked in a re-compilation of the wireless driver after kernel updates. It has largely been successful, but it *may* be playing into some other problems. We're still working on it. If you have any insight or suggestions, please direct them to support...at...system76...dot...com and I'll fwd them to the driver guys.

> * Perhaps System76 could host their own versions of the kernel that already have these additional drivers built in, so there doesn't have to be an additional, unexpectedly late download during the upgrade process.


That one has been mentioned before, but it has been categorically ruled out. Our goal is to feed our fixes back into upstream Ubuntu so that, some day, most systems need NO system76 driver. We feel that hosting our own kernels is counter to that purpose. (Albeit, it would provide a short-term solution to some issues... yet create an even heavier workload for us.)

---

### Post by Schrollini on 2010-02-12
**thomasaaron**, thanks for taking the time to give such thoughtful replies!

> **thomasaaron said:**
> 
Updating the image every time a *general* update comes down the pike, though, would be prohibitively time consuming, as would be running updates individually on every machine. I believe we *did* do this in the early days, when we were one-at-a-timing machines. But now we are producing on a much larger scale, and streamlining has become very important... and somewhere along the line running individual updates on every machine fell out of fashion. 


This sounds like a good problem to be having.:)  Just to be clear, I was only suggesting this because the Starling is having problems with upgrades.  In general, I have no problem with doing a bunch of upgrades when I first get a computer.  (I think you understood this, but I thought I'd make sure.)

> **thomasaaron said:**
> 
That's an EXCELLENT point. Here's what you're seeing. We're doing an experiment (and trying to refine it): Under 9.04, kernel updates would break the wireless driver (which was compiled against the kernel). This is something we definitely want to fix. It's ridiculous for customers' wireless to die every time there's an update, so we hooked in a re-compilation of the wireless driver after kernel updates. It has largely been successful, but it *may* be playing into some other problems. We're still working on it. If you have any insight or suggestions, please direct them to support...at...system76...dot...com and I'll fwd them to the driver guys.


I think this process went wrong for me only because the kernel panic interrupted the upgrade, and then I attempted to resume it without an internet connection (in part because of the issues with the keyboard).  It sounds like you have a pretty good solution; I just managed to find a strange corner case.  (I have that ability.)  I'll send a description of this issue to the support address tomorrow.

> **thomasaaron said:**
> 
That one has been mentioned before, but it has been categorically ruled out. Our goal is to feed our fixes back into upstream Ubuntu so that, some day, most systems need NO system76 driver. We feel that hosting our own kernels is counter to that purpose. (Albeit, it would provide a short-term solution to some issues... yet create an even heavier workload for us.)

Sounds reasonable.  I'm assuming that the wireless driver needs to be recompiled for each new kernel version, and there will always be a lag in your release of compiled drivers.  Perhaps you could host unmodified kernels, but hold back on releasing them until you've compiled the drivers.  Of course, this doesn't address the workload issue, and it would slow the fixing of security issues, so maybe it's not such a good idea.

Thanks again!

---

