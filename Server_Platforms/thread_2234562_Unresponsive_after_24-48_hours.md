---
title: "Unresponsive after 24-48 hours"
date: 2014-07-15
forum: Server Platforms
---

### Post by bkanuka on 2014-07-15
I need help diagnosing/fixing a freezing/halting issue.

Running 14.04 Server. Completely fresh install + apt-get upgrade + ssh server. Very stock/normal install.
If I leave the server on, it becomes completely unresponsive/freezes after 24-48 hours (usually overnight). By unresponsive I mean, *completely unresponsive*. The monitor is on waiting for login on tty1 and does not respond to keyboard input (there is no blinking cursor). On a previous install I had serial console (getty) set up, and it was also unresponsive on the serial console. Trying to connect via ssh fails, and the server does not respond to pings.

**After a hard reset:**
/var/log/syslog shows nothing abnormal. cron/anacron runs every hour and then it doesn't. that's the end of the log.
dmesg shows no messages past boot messages.
I have a server-grade motherboard [Supermicro A1SAi-2750F]("http://www.supermicro.com/products/motherboard/Atom/X10/A1SAi-2750F.cfm") with logging enabled. There is nothing in the logs.

**To diagnose hardware issues:**
I have ECC RAM. Using memcheck tools shows nothing abnormal.
I have replaced the PSU with one from a working machine. Motherboard also shows normal voltages on the PSU, pre and post freeze.
I have replaced the hard drive and SATA cables (from a working machine)

I believe the only parts I have not replaced is the motherboard and the RAM. They are both expensive parts.

Part of what makes this a difficult problem to diagnose is that I must wait days after changing something to see if the freeze will happen again. I have not idea how to initialize the halt.

Thanks in advance for any help.

EDIT: Based on this thread [http://ubuntuforums.org/showthread.php?t=2187009](http://ubuntuforums.org/showthread.php?t=2187009) I have uninstalled pm-utils and powermgmt-base (although I did not see any power logs?).  I won't be sure if that did anything until a few days have passed.

---

### Post by tgalati4 on 2014-07-15
An 8-core Atom processor?  That is impressive.  And only 20 watts.  I would declock the computer in BIOS and run it at it's lowest speed and see if it is stable.  It could be a motherboard issue or a CPU issue.  There could also be a bug in the kernel that needs fixing for new hardware.  Without any logs, there is not much you can do.

Because you are not getting flashing keyboard lights, nor any useful logs, you are not getting a kernel panic--that would point to a hardware issue.  I would burn a 12.04.4 desktop USB stick and boot off of that.  You need to monitor the machine (and the desktop gives you some visual monitoring tools).

Install *htop* and monitor the machine using ssh from another machine on the network.  That way, when it freezes, you will get a snapshot as to what was running during the freeze.  It could be a rogue process.

Because this is a low-power server, it is possible that some power-saving mode is kicking in.  Check BIOS for "Allow USB devices to Wake"

---

### Post by bkanuka on 2014-07-15
Thanks for appreciating the Atom! Usually I tell people it's an Atom and they go "oh..." like it's nothing. This thing is a beast though 8 cores at 2.4GHz.

I've had a feeling that this freeze only happens when idle. One test I did was to run 'stress' for 2 days and nothing froze. The night after the stress test, the computer froze.
This does point to some type of power saving. Is there some way to disable all power saving in the kernel?

I will follow up on your other suggestions later today

---

### Post by tgalati4 on 2014-07-15
Install *acpitool* and post:

```
sudo apt-get install acpitool
acpitool -w
```

This creates a list of devices that have power (enabled) during different sleep modes (S0 through S5)  You can change them with the -W switch.

If your system is stable under a stress test and falls asleep then doesn't wake properly, I would file a bug against the kernel version that you are running.  It seems like a kernel/acpi interaction problem.  You could try turning acpi off with a kernel boot switch.

Look for a BIOS upgrade from your motherboard support site.

Imagine a smartphone with an 8-core Atom.  It would make a nice hand warmer in the winter.

---

### Post by bkanuka on 2014-07-16
I uninstalled pm-utils and powermgmt-base, and added acpi=off to grub. I wasn't able to figure out acpitool so I decided to just disable acpi completely. I don't think I need it in a low-power always on server (agreed?).
It's now gone one night without freezing, which is good but not unheard of. I will probably wait a week before calling this solved.

Regarding a bug, could be something regarding the S0 or C1 power states. We'll know more in a week or so.

Thank you for your help.

---

### Post by lukeiamyourfather on 2014-07-16
I would double check the memory by running a test, I think the Ubuntu install disk has a test that can be run. Also check if the machine is showing any uncorrectable memory errors (or a lot of correctable errors). I think the counts reset when the machine is rebooted so it might a good thing to check after a while like 12 hours, 16 hours, whatever before it crashes.

```
sudo apt-get install edac-utils
edac-util -v
```

---

### Post by tgalati4 on 2014-07-16
This is a difficult problem to troubleshoot:

If acpi is turned off and you have stability (for several days, weeks, months), then it could be a BIOS bug with the motherboard or a kernel bug interacting with acpi and the hardware.

If acpi is on and pm-utils and powermgt-base is uninstalled and you have stability, then perhaps something in the power management daemon needs fixing.  You could manually activate suspend and check the pm-* logs in /var/log.  Any errors in trying to wake should get captured.

It could be a subtle hardware fault--clock speed, front side bus timing issue.  With 8 cores, all it takes is one to act up.  Linux doesn't handle hardware faults very well.

I would reseat and test the RAM as suggested.

---

### Post by Ken_Gledhill on 2014-10-12
> **bkanuka said:**
> I uninstalled pm-utils and powermgmt-base, and added acpi=off to grub. I wasn't able to figure out acpitool so I decided to just disable acpi completely. I don't think I need it in a low-power always on server (agreed?).
It's now gone one night without freezing, which is good but not unheard of. I will probably wait a week before calling this solved.

Regarding a bug, could be something regarding the S0 or C1 power states. We'll know more in a week or so.

Thank you for your help.

I have had a similar problem with this motherboard, but with the lockups happening only about once a month. Nothing in logs, etc. Machine is still going and answers ping but that is all. I have now made the changes you suggest. Did they work for you long term?

Cheers, Ken

---

### Post by bkanuka on 2014-10-12
Sorry for not following up.

No! the acpi and power management stuff did not fix it. I did end up finding error messages in my `kern.log`. I thought that a new file was created on every boot so I wasn't looking in the right place. The errors had something to do with the CPU.

What fixed it, was installing a vanilla kernel `linux-image-3.16.0-999-generic`.  This kind of makes sense because I was using a very new CPU, so I guess the newer kernel just had better support.  Sorry I can't help much more.

---

### Post by daniel284 on 2015-06-16
> **Ken_Gledhill said:**
> I have had a similar problem with this motherboard, but with the lockups happening only about once a month. Nothing in logs, etc. Machine is still going and answers ping but that is all. I have now made the changes you suggest. Did they work for you long term?

Cheers, Ken

Hi Ken,

I got a similar Problem. I bought my mainboard a year ago. At first I didn't notice freezing problems, because the server didn't freeze, but restart. But files got damaged and so I noticed. I know this is ubuntuforums, but I was running Debian Wheezy and after the freezes began I did a fresh install with Debian Jessie. From the temporal point of view my freezes are like yours, once a month or so. I checked temperature, replaced the power supply and so on. Did you work out what's going on? Did you find a solution?
Right now I updated my BIOS to Version 1.1. I will have a look for freezes. If they still occur I will try experimenting with acpi and so on or install ubuntu ...

If you have any information regarding this issue, I'd be glad if you share :)

Thanks,
Daniel

---

