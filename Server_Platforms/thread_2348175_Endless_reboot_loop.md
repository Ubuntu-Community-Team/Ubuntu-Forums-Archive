---
title: "Endless reboot loop"
date: 2017-01-01
forum: Server Platforms
---

### Post by daniel-jonsson on 2017-01-01
Hello,

Yesterday I had short power black out and my UPS did not kick in so my server went down. And now when I try to start it, it reboots after app 2 seconds, and keeps doing it over and over again.
If I choose to start in Recovery mode and then directly choose Resume start, it works. I have tested several times, all with the same result.

Nothing gets logged from the boots when it reboots. Nothing.
And when I tries to look at the screen to see what happens the text flashing to quick to be able to see were in the startup it reboots.
I have tried the film it with my phone, and it is still hard to be able to see exactly when it rebbots.

The best movie I manage to take it looks like the last lines before reboot is:
```
[    1.473732] ata1: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51100 irq 34
[    1.474797] ata2: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51180 irq 34
[    1.475873] ata3: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51200 irq 34
[    1.476957] ata4: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51280 irq 34
[    1.478059] ata5: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51300 irq 34
[    1.479164] ata6: SATA max UDMA/133 abar m2048@0xfeb51000 port 0xfeb51380 irq 34
[    1.494447] fb: switching to radeondrmfb from VESA VGA

```
And if I boot the server with Recovery - Resume I can not find the last line in syslog.

When trying to find out what is wrong I also noticed that the server the last week has been rebooting it self about one time every day. Without shouting down or anything in the loggs about going down. I can only see it has been starting up.

ANy one have any suggestions how to continue to find out what has happened?

---

### Post by ian-weisser on 2017-01-01
Smells like a hardware problem to me.

The reboot-every-two-seconds could be either hardware or software, if the reboot is triggered before logs get written. However, software or filesystem failure that early in the boot cycle will normally crash-and-halt, not crash-and-reboot.

The reboot-once-a-day seems classic hardware failure. Ubuntu simply does not have a force-a-reboot-without-logging-anything function. You CAN'T software-trigger a reboot in Ubuntu without leaving a log trace (unless you do stuff like editing the logs).

My suggestion: Swap the power supply first. Then look at the motherboard (POST and temperature sensors)

---

### Post by daniel-jonsson on 2017-01-02
I agree that the random reboots is hardware. And at the moment I suspect the UPS. There seems to be something not working with it any more. The server has now been up for 40 hours with the UPS disconnected and it seems to be fine.

But the boot loop is something different. How else can you explain that:
- it is booting up and working every time if I start in Recovery and then choose Resume
- it gets stuck in boot loop every time I tries a normal start.


If I analyze the logs and compare with the movie from a boot loop start up I notice the following:

The last line before reboot in a boot loop start up is:
```
[    1.494447] fb: switching to radeondrmfb from VESA VGA
```

But when I start in recovery I find this instead:
```
[    1.408880] [drm] VGACON disable radeon kernel modesetting.
[    1.408936] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!

```

From a former boot up log (before boot loop problem) I noticed:
```
[    1.494447] fb: switching to radeondrmfb from VESA VGA
[    1.494883] Console: switching to colour dummy device 80x25
[    1.495242] [drm] initializing kernel modesetting (ARUBA 0x1002:0x9996 0x1462:0x7721).
[    1.495261] [drm] register mmio base: 0xFEB00000
[    1.495265] [drm] register mmio size: 262144
[    1.495312] ATOM BIOS: 113
[    1.495417] radeon 0000:00:01.0: VRAM: 768M 0x0000000000000000 - 0x000000002FFFFFFF (768M used)
[    1.495424] radeon 0000:00:01.0: GTT: 1024M 0x0000000030000000 - 0x000000006FFFFFFF

```... and several other entries about graphics.

The only problem is that one of the first things I did trying to solve the issue was to update all packages, and therefore also the kernel. So the last log with a normal boot is with a earlier kernel...
But could it be something with the video driver that is messing up the system?

The computer has a AMD A4-7300 3.8GHz Radeon HD8470D processor and I am using the built in graphics in the processor.

---

### Post by ian-weisser on 2017-01-02
You are quire right ito blame software for the reboot loop. Sorry, I read that, but then forgot.

Perhaps it's the video driver, but perhaps not.
Since that older kernel is probably still on your system, use GRUB to boot into the older kernel.

At that point, you have more options
1) Reinstall the graphics drivers
2) Purge and reinstall the entire newer kernel, including graphics drivers
3) Ignore the newer kernel entirely, awaiting the next new kernel.

You may wish to  apt-mark the best working older kernel as 'manual' until resolved, so apt doesn't mistakenly autoremove it.

---

### Post by daniel-jonsson on 2017-01-02
Ok. So it was the radeon module that was causing the boot loop.
Googling all day and found several others with problems with the driver, but all on previous kernels and dists and all with blank screens, no boot loops.

By booting with the kernel parameter 'radeon.modeset=0' I have solved the problem.
Did not help to start with an earlier kernel.

But I am guessing it is in combination with something else. Otherwise Google would have given me this answer yesterday. Don't know how to figure out what...
So for me this is solved since it is ha headless server, and I don't care about graphic performance. But if someone would give me tips how to continue to investigating the real cause of the problem, I would gladly do it to find the real bug here.

And if not I will continue with the suggestion no 1 and 2 above, before I mark it as solved.

---

### Post by daniel-jonsson on 2017-01-19
Did not help to go back to an earlier kernel. I had purged all earlier except 4.4.0-53.
So kernel 4.4.0-53 and 4.4.0-57 caused the boot loop.

But now after updating the kernel to 4.4..0-59 the loop had ended and all is fine again. So my conclusion is that there was a bug in at least these to kernels and in the radeon module.

---

