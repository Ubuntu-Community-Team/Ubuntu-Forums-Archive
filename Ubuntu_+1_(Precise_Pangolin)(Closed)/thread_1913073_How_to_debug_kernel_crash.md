---
title: "How to debug kernel crash?"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 67GTA on 2012-01-21
I have had a problem with a kernel crash since 3.0 and up. 12.04 has the 3.2 kernel and has the same crash. Kernels 2.6.39 and below are fine. This is a completely random system crash/freeze with no logs written to give any clues. Everything is completely frozen. A hard shutdown/reboot is the only way out. I can't find any way to consistently recreate it. The machine is unresponsive to ssh. I can't send any crash dumps out either. I need to report this, but can't find any clues to help debug the crash. Any other ideas? This is a Dell Studio laptop with i5 M430 @2.27 GHz x4, ATI Raedon HD 4570, Hitachi HTS72505 500GB HDD. The graphics driver makes no difference. The freeze happens with ATI and radeon driver.

---

### Post by effenberg0x0 on 2012-01-22
Hi, 

If you just need to get some dump you can report/analyse, see if you can get it with sysrq+c. You might need to sysrq+k first.

You can try sudo apt-get install linux-crashdump but have a look here too: [http://www.dedoimedo.com/computers/crash-analyze.html](http://www.dedoimedo.com/computers/crash-analyze.html) 

If it's unclear, or you want to really debug the function that caused the crash yourself, I had posted some very raw info on how to use dbg to do that that may serve as a start point here: 
[http://ubuntuforums.org/showthread.php?t=1886024&highlight=debug+kernel](http://ubuntuforums.org/showthread.php?t=1886024&highlight=debug+kernel)

Regards,
Effenberg

---

### Post by 67GTA on 2012-01-22
The keyboard, mouse, xserver (everything) freezes. Sysrq won't work. I was trying to catch it as it froze today with "tail -f /var/log/kern.log". It froze just after a cron job started and I got a couple of lines about a stalled cpu before it froze. After rebooting, the syslog showed red zeros during the freeze up until I rebooted, and then started logging as normal. I've never seen that before.

---

### Post by effenberg0x0 on 2012-01-22
This is a difficult one.
I'd start by being absolutely sure about the hardware. I'd check the BIOS for any setting that might be risky, maybe load it's defaults, unplug/disable as much non-essential stuff/features/peripherals as possible. Also, I wouldn't disregard a broken memory module. I'd either test them with memtest or boot with each of them separately. I'd also check how things are in the CPU thermal-wise. A broken cooler, missing thermal paste, etc, could cause the system to crash in such a strong way that it leaves no info behind, nt even lkcd....
 
Hardware aside: It seems some people that had crashes associated with the "Stalled CPU" message you mentioned could avoid them by using clocksource=tsc (default=hpet) and nohz=off (default=on) in the kernel command line. You might want to give it a try. Completely turning off acpi (acpi=off) seemed to work for some people: It always does lol. 

But this is all a guess. I was really hoping that using kexec/kdump we could get some info.

**EDIT:**
> **67GTA said:**
> After rebooting,  the syslog showed red zeros during the freeze up until I rebooted, and  then started logging as normal. I've never seen that before.
I don't think anyone ever did! I have searched for this symptom and the only occurrences are reported by you.

---

### Post by xyzzyman on 2012-01-22
What's the longest you've gone from a cold boot without this happening? Also where are you testing these kernels? Within 12.04 only or have you run an earlier release previous to these crashes? Using the kernels from Ubuntu's repository or have you tried mainline (They are stock without ubuntu's patches) Do you still have Windows on the system or any non-debian distro's of Linux and do they error or lock up?

Even with those said, I would definitely do as effenberg said and run a memtest (Multiple passes are sometimes necessary to bring about errors), run BIOS as close to defaults as possible (Maybe even an update from DELL), maybe even run a hard drive scan (DFT, Seatools, etc) as the one for the mfg of your hard drive will usually also check the memory on the drive's controller. Your kernel crash isn't a normal one. 

If that all passes, and if you don't have another OS on the system such as Windows, maybe you might want to run under a LiveCD of say Fedora for awhile and see if it anything happens. Then you could rule out any paticular changes Ubuntu makes in the kernel (It sometimes happens, for example they enabled IOMMU for intel chips in the kernel for 3.2 during the RC phase and it caused issues for a number of us.)

---

### Post by 67GTA on 2012-01-22
All hardware is fine. The first thing I did was run memtest, but only for about an hour. I will let it run overnight to be sure. I dual boot with Windows 7, and it runs fine. The same crash is present with openSUSE 12.1 running kernel 3.1.6. This started with 11.10, but installed 12.04 hoping this had been magically fixed in 3.2. The freeze is random, sometimes 5 minutes to 2 hours. I've tested every even numbered kernel release since 3.0, and even 3.3 on 11.10 and 12.04. I've gotten them from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") Are these really vanilla (mainline)? I haven't tried any straight from kernel.org. If the over night memory test checks out, I will try some of the boot arguments to see if they help over the next couple of days.

---

### Post by 67GTA on 2012-01-22
The memtest finished quicker than I thought. No errors. Hard drive smart status shows fine. Nothing is overheating. I booted with various acpi related arguments with no change. It still randomly locks everything up HARD. I turned off the screensaver and opened a terminal full screen. I was watching the output of "tail -f /var/log/kern.log". The last entry was ```
INFO: rcu_sched_state detected stall on CPU 2 (t=15000 jiffies)
``` I have also ran cpuburn with no shutdowns. I have seen dozens of threads about this on the forums, but no one can get any info to nail it down. The Intel i5 procs seem to be the majority affected. This is going to be bad for a LTS release. I would pull out some hair if I had any:-)

---

### Post by effenberg0x0 on 2012-01-22
There's a kernel dump [here]("https://lists.launchpad.net/ubuntu-x-swat/msg144964.html") that seems to match what you describe and the last message you gave us (INFO: rcu_sched_state detected stall on CPU 2 (t=15000 jiffies)).
Time-wise / kernel versions it seems to match your description. 

I've been giving it a read (not an ATI user). So maybe this thing is entirely ATI/Radeon related? If true, we might simply have a situation in which current ATI  driver/kernel module has some compatibility problem with kernel >  2.6.39. One can diff what has changed in kernel/video/ati-related from  2.6.39 to 2.6.40 and get a good lead on this. But there are some options to try:

Test 1: Can you please go VESA and test stability? Just remove/blacklist everything, do a basic xorg.conf if you have to. modinfo, lsmod | grep, to make sure of what vga stuff you have loaded.

Test 2: Softer approach: Use FOSS driver, but disable KMS. Boot with radeon.modeset=0 in kernel command line.

Test 3: Even softer: "Late" KMS: Use FOSS Driver, but load KMS later in boot. Check/adjust /etc/modules|modprobe.d and make sure to recreate initramfs. Boot with pci=nomsi radeon.modeset=1

Test 4: "Forget about FOSS" approach: What about catalyst?

Regards,
Effenberg

---

### Post by 67GTA on 2012-01-22
Nice catch. I didn't see that bug report. I'm using the fglrx driver now. I can try vesa and radeon tomorrow. I was getting the freeze before with radeon, but didn't play around with KMS settings.

---

### Post by effenberg0x0 on 2012-01-22
> **67GTA said:**
> Nice catch. I didn't see that bug report. I'm using the fglrx driver now. I can try vesa and radeon tomorrow. I was getting the freeze before with radeon, but didn't play around with KMS settings.

Honestly, it still puzzles me. Why don't you get a proper crash? What are the red zeros you mentioned?
But, that aside, let's work with the info we have. 
Please post once you manage to test the stuff I posted above. 

Regards,
Effenberg

---

### Post by 67GTA on 2012-02-03
Well, it took me a while, but I finally finished testing everything. It definitely has something to do with the x-server/radeon/fglrx. So far the results are 3.0.16, 3.2, and 3.3:

Ubuntu Unity with radeon/fglrx: CRASH

Kubuntu with 3D effects and radeon/fglrx: CRASH

Unity 2D and Kubuntu with no effects (vesa): NO CRASH

Lubuntu (doesn't have any 3D related stuff) NO CRASH

Booting to kernel only: NO CRASH

Using the nomodeset option seemed to delay the crash long enough to get a crash dump in the terminal, but I opened the dash to get to the system monitor and then it froze. I'll have to try it again so I can copy the dump info to add it to the bug report. I read in the 12.04 alpha 2 release notes that some fixes were backported from 3.3, so I will test
it this weekend.

---

### Post by effenberg0x0 on 2012-02-03
> **67GTA said:**
> Well, it took me a while, but I finally finished testing everything. It definitely has something to do with the x-server/radeon/fglrx. So far the results are 3.0.16, 3.2, and 3.3:

Ubuntu Unity with radeon/fglrx: CRASH

Kubuntu with 3D effects and radeon/fglrx: CRASH

Unity 2D and Kubuntu with no effects (vesa): NO CRASH

Lubuntu (doesn't have any 3D related stuff) NO CRASH

Booting to kernel only: NO CRASH

Using the nomodeset option seemed to delay the crash long enough to get a crash dump in the terminal, but I opened the dash to get to the system monitor and then it froze. I'll have to try it again so I can copy the dump info to add it to the bug report. I read in the 12.04 alpha 2 release notes that some fixes were backported from 3.3, so I will test
it this weekend.

Good work :)
[QUOTE=67GTA]
This is a Dell Studio laptop with i5 M430 @2.27 GHz x4, ATI Raedon HD 4570, Hitachi HTS72505 500GB HDD. [/QUOTE]
Now it's time to search Google and Launchpad for reports that are likely to be about the same issue on the same hardware. We know that, for some reason, fglrx works for most people, but fails in this hardware with the kernels you tested. If you do find report, you can probably add a lot more info now to help developers fix it. If you don't, you can create a good report. If you manage to get the dump, it would be great.

Regards,
Effenberg

---

### Post by xyzzyman on 2012-02-04
Do you do anything graphics intensive in Windows? Maybe you should try 3DMark or something and really stress the card in Windows to verify it's not a faulty GPU that just craps out when it's hit a certain way. I know it doesn't happen with <3.0 kernels but the fact you get a crash with red zero's which no one else has ever seen is just so odd.

---

### Post by kevpan815 on 2012-02-04
> **67GTA said:**
> I have had a problem with a kernel crash since 3.0 and up. 12.04 has the 3.2 kernel and has the same crash. Kernels 2.6.39 and below are fine. This is a completely random system crash/freeze with no logs written to give any clues. Everything is completely frozen. A hard shutdown/reboot is the only way out. I can't find any way to consistently recreate it. The machine is unresponsive to ssh. I can't send any crash dumps out either. I need to report this, but can't find any clues to help debug the crash. Any other ideas? This is a Dell Studio laptop with i5 M430 @2.27 GHz x4, ATI Raedon HD 4570, Hitachi HTS72505 500GB HDD. The graphics driver makes no difference. The freeze happens with ATI and radeon driver.

Simple, Install 3.3.0 RC2 or 3.3.0 Nightly Builds from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) Just FYI.

---

### Post by effenberg0x0 on 2012-02-04
> **kevpan815 said:**
> Simple, Install 3.3.0 RC2 or 3.3.0 Nightly Builds from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") Just FYI.

Sure, and whatever it was that caused the bug the OP had it won't get properly reported and fixed. Therefore it's probably gonna come back and bite him and more users in future updates and releases. That's exactly what Open Source and Ubuntu Testing is all about... Picking the easy way out and not providing anything useful for the community. That's what everyone else here is doing. We're just trying to get our PCs working, for our own sakes.

This is Ubuntu Testing. The goal is to face problems, find bugs, report them, get them fixed. Improve Ubuntu for others. Just FYI.

Effenberg

---

### Post by xyzzyman on 2012-02-04
Most likely the issue still exists in 3.3 daily's if it is a bug in the code. kevpan815 blames all kernel panics on the realtek card reader bug that appeared during the 3.2 RC's and just now has been patched in the last week in 3.3 and backported to 3.2. Just FYI.

---

### Post by 67GTA on 2012-03-08
This bug isn't present in the latest 12.04 beta. I guess someone was able to get the debug info and fix it upstream. I installed from the Kubuntu 12.04 daily live CD last night and let it run until I made this post tonight. No freezes!

---

