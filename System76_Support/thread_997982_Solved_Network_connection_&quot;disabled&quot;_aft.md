---
title: "Solved: Network connection &quot;disabled&quot; after suspend. (Intrepid/panp4i)"
date: 2008-11-30
forum: System76 Support
---

### Post by phyzome on 2008-11-30
Sometimes after suspending and resuming, I find that the network manager applet shows networking as disabled. Nothing seems to bring it back on line.

What I've started doing is this:
[LIST=1]
[*]Right-click on nm-applet
[*]Uncheck "Enable wireless"
[*]Suspend
[/LIST]

When I resume, I re-enable wireless.

It's a little bit annoying, but so far I haven't experienced the bug.

---

### Post by swizman on 2008-11-30
Instead of checking / unchecking  "Enable wireless",  try this:

Next time, after resume, open a terminal and issue the command 
sudo /sbin/ifup wlan0 

If this command works and connects to the network, you can make it permanent by adding this command to the script
 
/usr/lib/pm-utils/sleep.d/10NetworkManager 

>> under the section

case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		/sbin/ifup wlan0		# <<<  add this here		 
		;;
	*)
		;;
esac



This works perfectly for me using Hardy. Try it on Intrepid and post if successful.

---

### Post by phyzome on 2008-11-30
> **swizman said:**
> Instead of checking / unchecking  "Enable wireless",  try this:

Next time, after resume, open a terminal and issue the command 
sudo /sbin/ifup wlan0

Can't try it right now, but I'll stop using my trick and see if I can reproduce the bug, then try your trick.

I suppose the real solution is to figure out why this happens at all, and fix it in the code. What logs should I look at when this happens next?

---

### Post by phyzome on 2008-12-01
I suspended my laptop for the night (which can trigger a few different bugs), and in the morning, I got "Networking disabled". Interestingly, another suspend-resume cycle fixed the problem!

Attached are:
[LIST]
[*]A screenshot of the "Networking disabled" (left-click on nm-applet)
[*]daemon.log for a normal suspend/resume
[*]daemon.log for a buggy suspend/resume
[*]kern.log for a normal suspend/resume
[*]kern.log for a buggy suspend/resume
[/LIST]

I did not try the command you suggested—I'll try that next time.

---

### Post by swizman on 2008-12-02
I just looked at your log files and compared them with mine after a resume. 

The kernel log (bad) shows that a whole bunch of stuff is not activated. Basically, after the entry “PM: Finishing wakeup”, I have 28 different task more than you (usb, pci, etho, iwl, etc).

The same goes for the daemon.log (bad), where the network manager is not activated at all (but maybe this is because the network cards are not activated first).

Now why this stuff is not activated, I do not see in those logs. Basically, suspend & resume seems to be difficult in Linux. 

I think that my trick will not help you in this case, sorry about that.

Good luck.

---

### Post by phyzome on 2008-12-04
> **swizman said:**
> I just looked at your log files and compared them with mine after a resume. 

The kernel log (bad) shows that a whole bunch of stuff is not activated. Basically, after the entry “PM: Finishing wakeup”, I have 28 different task more than you (usb, pci, etho, iwl, etc).

So, there are two levels of fail that I've seen. One is where the networking is broken, the other is that and:
[LIST]
[*]System monitor applet has disappeared
[*]Computer refuses to suspend or hibernate
[*]Some processes are frozen
[*]Shut down stops part way
[*]etc.
[/LIST]

The latter happened this morning. I grabbed the logs (attached), and it looks like NetworkManager is causing a general protection fault. It may be the following bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/286370](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/286370)

---

### Post by ethanay on 2009-01-01
Hmm, Phyzome, I'm running 8.04 and this sounds very similar to some problems I'm experiencing with any kernel newer than 2.6.24-19 right now:
[http://ubuntuforums.org/showthread.php?t=995625]("http://ubuntuforums.org/showthread.php?t=995625")

If this looks familiar to you, try installing and running the 2.6.24-19 kernel...I'm curious to know if that addresses these specific issues for you!

---

### Post by obscenic on 2009-05-26
Anyone know how to force the situation to occur? I usually experience this once out of every 4 or 5 resumes.

I've spent the last hour hibernating repeatedly, and it's worked every time so far, but I haven't even started trying to fit it at all! Must recreate bug...

---

### Post by ethanay on 2009-05-31
as an update to my original reply to Phyzome:  

kernels after 2.6.24-23 have generally solved the system-related issues.

however, networking is still occasionally disabled on resume, and i have to manually force a networking restart

there has also been a difference between auto-suspend and manually requesting a suspend, for example:
[https://bugs.launchpad.net/ubuntu/gutsy/+source/gnome-power-manager/+bug/149665](https://bugs.launchpad.net/ubuntu/gutsy/+source/gnome-power-manager/+bug/149665)

---

### Post by theNthDoctor on 2010-08-19
I did an adaptation of this advice, which I found to be simpler.

First, install cnetworkmanager.  Odds are good it's already installed by default, but just in case:

# sudo apt-get install cnetworkmanager

Next, modify the sleep/wakeup script that swizman mentioned, but differently:

/usr/lib/pm-utils/sleep.d/??NetworkManager 

(Replace ?? with whatever yours has)

swizman suggested using ifup, but it's simpler than that - especially for my case, where wlan0 was disabled until I right-clicked the nm-applet and enabled it.  Here is the original snippet to look for:

```
thaw|resume)
   resume_nm	
;;
*)
```

After "resume_nm" simply add:

```
  /usr/bin/cnetworkmanager --wifi=true
```

Since making this change, my wifi has been reconnected faster than I can login from the locked screensaver.

---

