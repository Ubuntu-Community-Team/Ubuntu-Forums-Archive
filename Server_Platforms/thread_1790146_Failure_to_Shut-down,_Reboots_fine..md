---
title: "Failure to Shut-down, Reboots fine."
date: 2011-06-24
forum: Server Platforms
---

### Post by y3ahright on 2011-06-24
I've googled for days now to try and find a solution to my problem with no avail.

My server is running the latest kernel (2.6.38-8 )and ACPI version in the BIOS is set to 2.0 (I've tried 1.0 and 3.0 version, with the same issues).  

When shutting down the server with:

 ```
sudo shutdown -P now
``` 

it runs through the process and it notes:

```
Killing remaining processes                 [failed]
```

Runs through the rest of the list (I can't remember the rest of them but they all say ok) followed by a line telling me it is configuring ACPI for state s5 i believe and the last line is

"Disabling non use CPUs" -- Here the system will hang.  I've left the system over night and it stayed at the same spot.

the code:

```
sudo reboot now
``` along with CTRL+ALT+DEL restarts the machine just fine.

Would anyone care to take a shot at what the problem might be?

--Thanks.

---

### Post by Jake.Debord on 2011-06-24
Could you post some of the error log? That may give better explanation as to where its getting stuck

---

### Post by CharlesA on 2011-06-24
Does running this make any difference?

```
sudo halt
```

---

### Post by y3ahright on 2011-06-24
> **Jake.Debord said:**
> Could you post some of the error log? That may give better explanation as to where its getting stuck

boot.log gives me:

```
fsck from util-linux-ng 2.17.2
Main: clean, 76046/60792832 files, 42124177/243141888 blocks
 * Setting sensors limits       ^[[80G
^[[74G[ OK ]

```

and boot just says "nothing has been logged yet.

Any other specific logs you might find helpful?  I'll shut the server down in around an hour to try and post the exact errors for everything.

> **CharlesA said:**
> Does running this make any difference?

```
sudo halt
```

I'll try that as well and give you my result when I can.  Thanks for suggesting something.

---

### Post by CharlesA on 2011-06-24
Curious, if you are able to switch to another tty when it gets stuck there.

Try Ctrl + Alt + F2 to see if you can access another tty.

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> Curious, if you are able to switch to another tty when it gets stuck there.

Try Ctrl + Alt + F2 to see if you can access another tty.

I've attempted that before and after it states "disabling non use CPU's" the keyboard doesn't work, CTRL+ALT+DEL nor Crtl+ALT+F2

---

### Post by CharlesA on 2011-06-24
> **y3ahright said:**
> I've attempted that before and after it states "disabling non use CPU's" the keyboard doesn't work, CTRL+ALT+DEL nor Crtl+ALT+F2
Strange. Does the [magic sysreq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device") work?

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> Strange. Does the [magic sysreq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device") work?

That does not work either.  The only way I've found to get out is to just hold the power button.

---

### Post by CharlesA on 2011-06-24
> **y3ahright said:**
> That does not work either.  The only way I've found to get out is to just hold the power button.
It's like the machine is totally locked up.

Does it have more then one physical cpu?

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> It's like the machine is totally locked up.

Does it have more then one physical cpu?

Yes its an:
ASUS KFSN4-DRE/SAS motherboard 
2x Dual-Core AMD Opteron
4x 1GB Kingston memory

---

### Post by CharlesA on 2011-06-24
Is it possible to turn off one of the CPUs and see if it still has problems shutting down?

Just a shot in the dark, since I've not run into that error before and I didn't find anything on google.

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> Is it possible to turn off one of the CPUs and see if it still has problems shutting down?

Just a shot in the dark, since I've not run into that error before and I didn't find anything on google.

I'm not too sure how to disable one of the CPU's.  I'll try it if you could tell me what file to set to disable one.

The actual shutdown message:

```
sudo shutdown -P now
```

```

*Asking all remaining processes to terminate     [OK]
*killing all remaining processes                 [Fail]
*Deconfigure network interface                   [OK]
*unmounting weak file systems                    [OK]

EXT4-fs (dm-1): remounted OPTS:(null)
*Will now halt
md: stopping all md devices
sd: 1:0:0:0 [sdb] Synchronizing SCSI Cache
sd: 1:0:0:0 [sdb] Stopping disk
md: 0:0:0:0 [sda] Synchronizing SCSI Cache
md: 0:0:0:0 [sda] stopping disk
ehci_hcd 0000:00:02.1 PCI INT B disabled
ohci_hcd 0000:00:02.0 PCI INT A disabled
ACPI: Preparing to enter System sleep state s5

Disabling non boot CPU's

```

From then on nothing happens.

I appreciate the time helping me.

---

### Post by CharlesA on 2011-06-24
s5 is supposed to be "off"

[http://software.intel.com/en-us/blogs/2007/01/10/all-about-system-power-states-s0-s5/](http://software.intel.com/en-us/blogs/2007/01/10/all-about-system-power-states-s0-s5/)

Are you able to turn off ACPI and see what it does?

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> s5 is supposed to be "off"

[http://software.intel.com/en-us/blogs/2007/01/10/all-about-system-power-states-s0-s5/](http://software.intel.com/en-us/blogs/2007/01/10/all-about-system-power-states-s0-s5/)

Are you able to turn off ACPI and see what it does?

```
sudo halt
```

Gives me the exact same as sudo shutdown -P now does.

As for turning off ACPI I've added into my grub acpi=off and it does not change the shutdown process.

---

### Post by CharlesA on 2011-06-24
I kinda wondering if it's just halting without powering off the PC.

Reboots work fine, and judging from the message, it's just seems like it's not doing a "soft off" when you go to shut it down.

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> I kinda wondering if it's just halting without powering off the PC.

Reboots work fine, and judging from the message, it's just seems like it's not doing a "soft off" when you go to shut it down.

That's my thought as well I just have no idea on how to go about fixing that.

This problem was also happening on version 10 as well which makes me almost certain its hardware.

---

### Post by CharlesA on 2011-06-24
> **y3ahright said:**
> That's my thought as well I just have no idea on how to go about fixing that.

This problem was also happening on version 10 as well which makes me almost certain its hardware.
I'm thinking it's hardware as well. Maybe a buggy APCI or something.

Have you contacted Asus support and asked about it?

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> I'm thinking it's hardware as well. Maybe a buggy APCI or something.

Have you contacted Asus support and asked about it?

Unfortunately every time I call them (it has been 4 times now) I get some message saying all of their reps are busy and they will call me back (which they have yet to do).

But anyways thanks for the help on trying new things.  At least now I can tell my boss its not my fault Haha.

---

### Post by CharlesA on 2011-06-24
I thought they had online support?

---

### Post by y3ahright on 2011-06-24
> **CharlesA said:**
> I thought they had online support?

If its anything like their phone support I'm screwed either way.  I will try that on Monday.  Thanks for the tip.

---

### Post by CharlesA on 2011-06-24
> **y3ahright said:**
> If its anything like their phone support I'm screwed either way.  I will try that on Monday.  Thanks for the tip.

Ouchie.

Good luck!

---

### Post by trundlenut on 2011-06-25
When the system is running how many processors does it think there are?

What does ```
cat /proc/cpuinfo
``` report?

---

### Post by trundlenut on 2011-06-25
One thought, is the bios on the machine up to date?

---

### Post by volkswagner on 2011-06-25
Curious if you tried acpi=force instead of acpi=off?

About updating the BIOS.... I have a ten year old desktop that I was trying to get recognize more than 512MB RAM.  I ran an updated BIOS, which broke ACPI=force.  So just a warning to the wise, updating the BIOS may not always bring all functions up to date.  I ended up downgrading the BIOS.

I am also curious if running a live CD like 10.04 desktop provides a proper shutdown.  If it does, then you may have a chance of getting the server edition to do the same.

One more thing, are you sure the fan is not running and the PC is actually off?  I have a Dell Poweredge server that has the fan run in poweroff state.  I believe there was a setting in the BIOS to turn that feature off.

---

### Post by trundlenut on 2011-06-26
I will admit bios updates can be a double edged sword.  A desktop machine I have wouldn't shut down after I installed a wireless network card.  A bios update fixed the shutdown issue but left me with the case fan running at max speed the entire time.

My poweredge server has the fan in the power supply running as long as it is plugged in too.  I hadn't realised you can potentially turn this function off though.

---

### Post by y3ahright on 2011-06-29
> **CharlesA said:**
> Ouchie.

Good luck!

Their online support is useless.  It takes upwards of 30min to get a connection and if you don't answer them within 1 minute they close your IM and ask you to take a survey...



> **trundlenut said:**
> When the system is running how many processors does it think there are?

What does ```
cat /proc/cpuinfo
``` report?

Reports 4 processors.

> **trundlenut said:**
> One thought, is the bios on the machine up to date?

Yes it is up to date, had to update it in order to fix another little issue.

> **volkswagner said:**
> Curious if you tried acpi=force instead of acpi=off?

About updating the BIOS.... I have a ten year old desktop that I was trying to get recognize more than 512MB RAM.  I ran an updated BIOS, which broke ACPI=force.  So just a warning to the wise, updating the BIOS may not always bring all functions up to date.  I ended up downgrading the BIOS.

I am also curious if running a live CD like 10.04 desktop provides a proper shutdown.  If it does, then you may have a chance of getting the server edition to do the same.

One more thing, are you sure the fan is not running and the PC is actually off?  I have a Dell Poweredge server that has the fan run in poweroff state.  I believe there was a setting in the BIOS to turn that feature off.

I've tried both acpi=force as well as off with no change.

> **trundlenut said:**
> I will admit bios updates can be a double edged sword.  A desktop machine I have wouldn't shut down after I installed a wireless network card.  A bios update fixed the shutdown issue but left me with the case fan running at max speed the entire time.

My poweredge server has the fan in the power supply running as long as it is plugged in too.  I hadn't realised you can potentially turn this function off though.

I looked through the motherboard manual and there is no setting for the fans during power off, but thank you for that idea I hadn't thought of that.

---

### Post by CharlesA on 2011-06-29
Have you tried booting off a livecd and seeing it it'll shutdown that way?

---

### Post by y3ahright on 2011-06-30
> **CharlesA said:**
> Have you tried booting off a livecd and seeing it it'll shutdown that way?

I planned to do that today but they put me on some other project so that got dismissed.  I will try that tomorrow.  I have an identical motherboard running 10.10 which shuts downs just fine.

---

### Post by CharlesA on 2011-07-01
> **y3ahright said:**
> I planned to do that today but they put me on some other project so that got dismissed.  I will try that tomorrow.  I have an identical motherboard running 10.10 which shuts downs just fine.

Hope it works out.

---

### Post by y3ahright on 2011-07-01
> **CharlesA said:**
> Hope it works out.

Shutting down with a LIVE CD works.  So it must be some software issue?  

Now I'm more confused then when I started.

Would you happen to have any other ideas to try?

---

### Post by CharlesA on 2011-07-01
> **y3ahright said:**
> Shutting down with a LIVE CD works.  So it must be some software issue?  

Now I'm more confused then when I started.

Would you happen to have any other ideas to try?

I'm not sure. Did you use the same version of Ubuntu that you have installed?

Not sure what the difference between doing a shutdown via livecd and shutdown via sudo halt is.

Did you shut the machine done from the GUI or use the terminal?

---

### Post by y3ahright on 2011-07-01
> **CharlesA said:**
> I'm not sure. Did you use the same version of Ubuntu that you have installed?

Not sure what the difference between doing a shutdown via livecd and shutdown via sudo halt is.

Did you shut the machine done from the GUI or use the terminal?

I used an old live cd from 9.04 and I used the GUI shutdown.  I'll download the latest live cd and try shutting down via terminal.

---

### Post by CharlesA on 2011-07-01
> **y3ahright said:**
> I used an old live cd from 9.04 and I used the GUI shutdown.  I'll download the latest live cd and try shutting down via terminal.

Good luck! I hope it helps narrow down what the problem might be.

---

### Post by y3ahright on 2011-07-05
> **CharlesA said:**
> Good luck! I hope it helps narrow down what the problem might be.

With the 11.04 Live-CD the server kills all processes within 2 seconds and shuts down fine (using the GUI shutdown as well as sudo shutdown -P now).

So it must be some sort of software problem, I'm just not too sure of where it is hanging. 

Is there a way to log the shut down for the Live-CD as well as the server shutting down itself?

---

### Post by CharlesA on 2011-07-05
Not sure if there is a way to log the shutdown.

Are you able to pop another drive in and reinstall the OS?

---

### Post by y3ahright on 2011-07-05
> **CharlesA said:**
> Not sure if there is a way to log the shutdown.

Are you able to pop another drive in and reinstall the OS?

I've actually re-installed three times and the last time I switched out the hard drives.

What I did notice was that in /sys/power/disk it states:

```
[platform] test testproc shutdown reboot
```

from: [http://www.kernel.org/doc/Documentation/ABI/testing/sysfs-power](http://www.kernel.org/doc/Documentation/ABI/testing/sysfs-power)

it states: 
> The /sys/power/disk file controls the operating mode of the suspend-to-disk mechanism.  Reading from this file returns the name of the method by which the system will be put to sleep on the next suspend.

'platform' - the memory image will be saved by the kernel and the system will be put to sleep by the platform driver (e.g. ACPI or other PM registers).


That makes me think the problem is when the disks are suspending it calls this and ACPI takes over and is messing up.

Although I can be totally wrong and this have absolutely nothing to do with the shutdown process.

Update:
I wanted to see if I could make the system respond at all after it says "Disabling non-boot CPUs" so I popped out one of the hard drives and it does acknowledge that a hard drive link is down and when I replace it, it syncs back.

---

### Post by CharlesA on 2011-07-07
> **y3ahright said:**
> 
Update:
I wanted to see if I could make the system respond at all after it says "Disabling non-boot CPUs" so I popped out one of the hard drives and it does acknowledge that a hard drive link is down and when I replace it, it syncs back.

That's odd. It's like it's getting stuck, but not completely stuck.

You are running 11.04 on it, right?

---

### Post by y3ahright on 2011-07-07
> **CharlesA said:**
> That's odd. It's like it's getting stuck, but not completely stuck.

You are running 11.04 on it, right?

Thanks for your help trying to solve this confusing problem.  I recently switched to debian and all is well (shuts down just fine).

---

### Post by CharlesA on 2011-07-07
> **y3ahright said:**
> Thanks for your help trying to solve this confusing problem.  I recently switched to debian and all is well (shuts down just fine).

Which version of debian? Squeeze?

Glad you got it working. :)

---

