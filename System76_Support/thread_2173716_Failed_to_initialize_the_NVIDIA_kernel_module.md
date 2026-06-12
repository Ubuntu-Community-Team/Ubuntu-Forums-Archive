---
title: "Failed to initialize the NVIDIA kernel module"
date: 2013-09-11
forum: System76 Support
---

### Post by Newbunto on 2013-09-11
Sometimes when I boot I get the following problem.

[INDENT]The system is running in low-graphics mode
Failed to initialize the NVIDIA kernel module
[/INDENT]

What does this mean? Where should I be looking?

This started happening about a month ago.

I don't know whether it's relevant but because of my attempts to deal with this I now don't have an xorg.conf file.

Ubuntu 12.04 LTS
kernel is 3.2.0-53-generic
hardware is bonp5

---

### Post by isantop on 2013-09-11
Ubuntu isn't designed to use an Xorg.conf file. That should reset your configuration.

Try removing then reinstalling the nvidia driver.

---

### Post by Newbunto on 2013-09-30
This problem seems to come and go. While I have never reinstalled the nvidia driver explicitly (I wouldn't know how to), something must be doing that.

A day or so ago Ubuntu upgraded itself to the 3.2.0-54-generic kernel and the problem started happening again. Is this plausible? Does the nvidia driver come with the kernel?

How would I remove then reinstall the nvidia driver? Is it possible that there is a non-obvious way that I am causing this to occur behind the scenes?

I don't know whether this is relevant or not but the laptop came with Ubuntu 11.10 and then I let it upgrade to Ubuntu 12.04 LTS and I notice now that the relevant line in /etc/apt/sources.list.d/system76.list has been commented out with the comment "disabled on upgrade to precise". Is that badness? Is there something that I should be doing with that? If so, what are the commands? Do I just edit in order to uncomment?

---

### Post by Newbunto on 2013-10-01
Just flailing around here but I found something called "Additional Drivers". That said that I was currently using

[FONT=courier new]NVIDIA accelerated graphics driver (version 304)[/FONT]

I asked it to upgrade to

[FONT=courier new]NVIDIA accelerated graphics driver (version 319)[/FONT]

The install required a restart. After the restart the problem did not occur. However I would be looking for a few more shutdown and startup cycles before thinking that the problem is fixed.

Is any of this relevant?

---

### Post by houstonbofh on 2013-10-01
A while ago there was a update that went slightly out of order and broke nvidia.  Kinda...  The fix is to totally remove and reinstall the nvidia drivers.  You update probably fixed it as well, but...

Another post about it is here.

[http://ubuntuforums.org/showthread.php?t=2176311](http://ubuntuforums.org/showthread.php?t=2176311)

---

### Post by Newbunto on 2013-10-01
> **houstonbofh said:**
> Your update probably fixed it as well

It looked to me that updating from "304" to "319" removed "304" first and then installed "319" so probably had the same effect.

```
dpkg -l | grep -i nvidia
```

shows [FONT=courier new]nvidia-319[/FONT] present and [FONT=courier new]nvidia-304[/FONT] not present.

I note though that I still have [FONT=courier new]nvidia-304-updates[/FONT] and [FONT=courier new]nvidia-settings-304-updates[/FONT]. Should I be doing something about that?

---

### Post by houstonbofh on 2013-10-03
I would purge them, but that is just me.

Actually, I remove all nvidia totally, and reinstalled clean.  Paranoid by profession. :)

---

### Post by isantop on 2013-10-03
Nothing wrong with paranoid, as long as it doesn't dictate your life! ;-)

For future record, we're now supplying a "system76-driver-nvidia" package that will automatically keep your Nvidia driver up to date. It's available on 13.04 and up, and it's packaged in our PPA.

---

### Post by houstonbofh on 2013-10-03
> **isantop said:**
> Nothing wrong with paranoid, as long as it doesn't dictate your life! ;-)

For future record, we're now supplying a "system76-driver-nvidia" package that will automatically keep your Nvidia driver up to date. It's available on 13.04 and up, and it's packaged in our PPA.
And you did that because you hate us LTS users, right? ;)

Actually, that is not a bad idea at all.

---

### Post by isantop on 2013-10-03
We just don't have the resources to rewrite all of the support modules for an OS that's over a year old.

---

### Post by Newbunto on 2013-10-03
> **houstonbofh said:**
> I would purge them, but that is just me.

I've now done [FONT=courier new]apt-get remove --purge[/FONT] on each one and that took out a few extra, leaving me with just

[FONT=courier new]nvidia-319
nvidia-common
nvidia-settings-319[/FONT]

which seems about right.

---

### Post by isantop on 2013-10-04
Looks great! I think you're all set.

---

### Post by Newbunto on 2013-10-07
Hmmm. The problem that I was originally having (subject of thread) seems gone. In the process of all this I have rebooted lots of times and have not gotten the error. (I have also completely uninstalled all the nvidia packages and reinstalled nvidia-319 and nvidia-common. nvidia-settings-319 was picked up automatically along the way.)

However now when I use nvidia-settings it core dumps. (This was not happening when I had the "304" version installed.) Fortunately this occurs when I exit the program so is not a showstopper. This happens even if I do nothing while in the program i.e. type [FONT=courier new]nvidia-settings[/FONT] at shell prompt, the "NVIDIA X Server Settings" window comes up (looks fine), click Quit button, click Quit on confirmation dialog box, shell window shows message "[FONT=courier new]Segmentation fault (core dumped)[/FONT]". {I let it send a report the first time. It doesn't seem to want to report it again, which makes sense.} Anyone else experiencing this problem? In which directory do core dumps go anyway?

Still. That's about 10 steps forward and half a step back.

---

### Post by isantop on 2013-10-07
You don't need to use the Nvidia Settings program anymore, as the standard Ubuntu System Settings app is capable of changing the screen resolution and orientation.

---

### Post by Newbunto on 2013-10-07
I use my laptop primarily as a desktop replacement and with an external monitor connected by HDMI. I was using [FONT=courier new]nvidia-settings[/FONT] to configure for external monitor as primary display and laptop display disabled (whereas on booting up it was always configuring by default as a single double-width display, if that makes sense). Maybe the support of this type of configuration (Edit: dual monitor) has improved over the months.

---

### Post by isantop on 2013-10-07
It definitely has. The 319 Nvidia driver supports XRandR which lets Ubuntu manage the display automatically, rather than needing the Nvidia driver to do it exclusively.

---

### Post by Newbunto on 2013-10-20
> **isantop said:**
> You don't need to use the Nvidia Settings program anymore

It seems as if mucking around with the displays[FONT=courier new][/FONT] is still needed in a dual display config.

(Most of the time) I boot up with the lid closed and an external monitor connected. It's impossible to say what the built-in display is doing but things mostly seem to work on the external monitor i.e. can log in, dash home and launcher are on the external monitor, starting applications works and they come up on the external monitor.

However when I start Transmission, the launcher shows the application as running but it never comes up. I suspect that it is deciding to put its window on the built-in display.

Using [FONT=courier new]nvidia-settings[/FONT], it suggests that it is in "Twinview" mode (two displays side-by-side making a single larger display). Disabling the built-in display and *then* starting Transmission makes it work correctly (other than that [FONT=courier new]nvidia-settings[/FONT] core dumps on exit, as noted previously).

Are you saying that I don't need [FONT=courier new]nvidia-settings[/FONT] anymore because "System Settings / Displays" can do the same job?

What I really want is that I don't need to use *either* when I boot up.

---

### Post by isantop on 2013-10-21
Yes, using the built-in Displays tool will work without needing nvidia-settings.

First, you may need to enter this command in the terminal:

sudo rm /etc/X11/xorg.conf

Next, disable the built-in display in the Display settings, then click Apply. These settings should be automatically applied in the future, whenever you log in.

---

### Post by Newbunto on 2013-10-21
> **isantop said:**
> Next, disable the built-in display in the Display settings, then click Apply. These settings should be automatically applied in the future, whenever you log in.

Yes, that seems to be working. (Boot up and login from scratch and only external monitor is in use and all tested applications come up correctly on the external monitor.)

However the original problem as per the thread title is back. The kernel just upgraded itself from 3.2.0-54 to 3.2.0-55 and on the restart after that I get low graphics mode and "failed to initialize the NVIDIA kernel module". A further restart did not fix the problem. (When this problem is occurring I can reliably get a console login and do stuff.) So I decided to shutdown completely (shutdown with halt and power off) rather than just restarting and then press the laptop's power button to power on and boot up again and now it's OK. I have no way of knowing whether anything that I am doing is helping.

I think it would be fair to say that I rarely "restart" i.e. typically only on kernel updates. If I am shutting down at all then it would typically be a shutdown to halt and power off. So maybe there's some hardware state that isn't reset properly on a "restart".

On a restart after a kernel update I would normally open up the lid, just in case something has gone wrong with the update. (Again, though, possibly over the months the support for an external monitor has improved and this is unnecessary.)

---

### Post by Newbunto on 2013-11-01
This is still driving me nuts. I really have no idea what is needed to get this to work reliably.

I had to reboot about 5 times this morning in order to get the laptop to boot up to the login screen. Otherwise it gives the error as originally reported.

---

### Post by isantop on 2013-11-04
I'm thinking that upgrading to 13.10 should solve your problems. You can use our upgrade instructions on our website under support.

---

### Post by Newbunto on 2013-11-08
*11 hours* of upgrading later and I am at Ubuntu 13.10. A few too many loose ends remain for me to check whether I am still having problems with the NVIDIA driver.

(Worst problem I had was the *two* changes to the mount point directory for GVFS during that sequence of upgrades.)

---

### Post by Newbunto on 2013-12-02
Some weeks on and 13.10 does seem to fix the "Failed to initialize the NVIDIA kernel module" problem. I am marking this as "solved".

I wouldn't recommend upgrading to 13.10 without hesitation though because of other issues. The most obvious problem that I have is that Google Earth is problematic to install and highly flaky to run under 13.10. I also found that a large, complex spreadsheet that used to work stopped working, due to the change of LibreOffice version presumably. Still, because of the difficulties of using a computer with no graphics, it is a net gain in my environment.

Edit: PS PuTTY also seems funny under 13.10.

---

