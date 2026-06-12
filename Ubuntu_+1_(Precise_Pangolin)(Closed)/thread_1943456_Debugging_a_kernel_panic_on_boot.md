---
title: "Debugging a kernel panic on boot"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by drbcladd on 2012-03-19
Configuration: Alienware m17x with Kingston 120GB SSD as sda, Hitachi 500GB as sdb, nVidia GTX260M, Intel Core2 Quad.

Install: Most current updates of 12.04 including linux-3.2.0-19-generic x86_64. 

Problem: When booting any 12.04 kernel other than 3.2.0-17-generic (I believe it happened with 3.0.0-16; know it happens with 3.2.0-18 and -19) grub comes up and permits me to make my selection. Then, whether I select standard or recovery, the machine locks up after 2.5 seconds.

The numeric and caps lock leds begin blinking.

The 2.5 seconds is determined by watching the crash on the screen when booting a recovery configuration. Unfortunately the screen information shoots by very quickly and I haven't time to read anything before the crash stack dump. I can get the last few lines of that if it helps. 

The problem is that there is no writable device for logging so I cannot see the error on subsequent boots back in -17. How can I either: get the boot trace to print to the screen with a smaller font (or larger resolution) so I can see more to copy down? Or get it to log somewhere else (have thumbdrive in or something?).

Looking at the trace of a working boot, it appears to be the moment that the SSD is being queried is where the lockup occurs. The drive is formatted with ext4 and is one big partition with a swap partition. I configured it before I understood where the swap should go and haven't moved it since the second spindle still boots fine and I can get work done over there. I will backup and move swap once 12.04 boots reliably. 

I want to report on what is going wrong but I really don't know what tools to use to capture a boot log before the boot log is recorded.

Thanks for any assistance,
-bcl

---

### Post by dino99 on 2012-03-19
from the boot line, remove "quiet splash" to let you see the boot process in verbose mode.

what you describe is a kernel panic, so you might test with some boot settings like noacpi or nomodeset or ...

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

then you will decide to report or not your problem on launchpad with: ubuntu-bug linux

---

### Post by gliderdad79 on 2012-03-28
Have you done any testing yet or reported it? I went and upgraded today and got the same so had to re install 11.10.

---

### Post by drbcladd on 2012-03-29
I have not reported it because I cannot capture enough information about it. I know it is a kernal panic, I am pretty sure it is happening during the mount of sda1, the primary installed partition. I deduce this from watching it enumerate the USB devices and then pause for almost a second.

That is where the ext4 file mount happens in a standard boot sequence that succeeds, something like 3.5 seconds in to the boot with an SDD.

I can watch the information print out on the screen but the font size leaves only 25 lines on the screen, nothing approaching the top of the call stack that is dumped. The problem is somewhere in a pagefault or fast_path. I have tried activating a swap partition on a rotational device and it had no effect.

Kernel 3.3.999 (the dailies from 21-28 March) get past this point in booting but appear to crash out on something having to do with the IR driver. 

I have been playing with video settings on boot to see if I can get it to print to a screen with 43 or 50 (or more) lines so that I could actually see the stack trace. No joy. The settings I have cause a working kernel (3.2.0-17 generic x86_64) to print in a larger video window but no non-recovery kernel other than 17 seems to print anything to the screen. The recovery marked boot lines appear to suppress the video mode going into the kernel (makes sense, actually) but that means I don't get any benefit from the settings.

So, I keep booting -17 from almost two weeks ago and upgrade twice a day, always hoping that a change to the kernel will permit me to boot the new one. If I can devise a way to get more information, I will report the error; right now it is just a "why doesn't it work on _my_ machine!?!"

---

### Post by kakalos12 on 2012-03-29
The same problem and using alienware m17x too. I have reinstalled ubuntu 11.10 and hope that this problem will be fixed soon

---

### Post by drbcladd on 2012-03-29
3.3.0-999 for 20120329 appears to work. I haven't built the nvidia drivers for it yet but it appears to boot and run. 

Will report in a couple of hours if the boots remain happy or not.

-bcl

---

### Post by NHclimber on 2012-03-29
> **drbcladd said:**
> I have been playing with video settings on boot to see if I can get it to print to a screen with 43 or 50 (or more) lines so that I could actually see the stack trace. No joy. The settings I have cause a working kernel (3.2.0-17 generic x86_64) to print in a larger video window but no non-recovery kernel other than 17 seems to print anything to the screen. The recovery marked boot lines appear to suppress the video mode going into the kernel (makes sense, actually) but that means I don't get any benefit from the settings.

To get a 50-line vga display on the boot console with grub2 requires editing the grub2 menu entry. On boot:
1. Highlight the grub2 menu entry and press 'e'.
2. Navigate (with cursor keys) down to 'linux ...' line and replace 'linux ...' with 'linux16 ...'
3. Navigate to end of same line (cursor keys or 'End' key) and replace '... quiet splash vt.handoff=...' with ' vga=0xF01'
4. Navigate to 'initrd ...' line and replace 'initrd ...' with 'initrd16 ...'
5. Ctrl-x to boot.

---

### Post by gliderdad79 on 2012-03-29
Hopefully that kernel will stay working and hopefully will get in before the kernel freeze, or at least figure out whats causing it.

---

### Post by Wise Ferret on 2012-03-30
I suffer from the same problem on a dell xps studio laptop with nvidia 9500m card. But when I download and install the kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/) I receive errors regarding the proprietary drivers: 
```
run-parts: executing /etc/kernel/postinst.d/dkms 3.3.0-999-generic /boot/vmlinuz-3.3.0-999-generic
ERROR (dkms apport): kernel package linux-headers-3.3.0-999-generic is not supported
Error! Bad return status for module build on kernel: 3.3.0-999-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
ERROR (dkms apport): kernel package linux-headers-3.3.0-999-generic is not supported
Error! Bad return status for module build on kernel: 3.3.0-999-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/295.33/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.3.0-999-generic /boot/vmlinuz-3.3.0-999-generic

```
Is there any way to solve this?

---

### Post by drbcladd on 2012-03-30
Sadly the 3.3.0-999 from yesterday didn't survive a second reboot. I worked on installing nVidia drivers and it lost its mind, rebooted a second time and it panicked early. 

I will try the linux16 trick and see what I can see.

[Added]

(1) NHclimber's recipe worked like a charm. Unfortunately it did not expose the whole stack trace. The last oops before locking up is a failure to sync in an interrupt handler. That handler appears to have been called in response to another error since there is still a stack trace rolling off the top of the screen.

Both end inside a page fault handler. 

(2) I have Wise Ferret's error building nvidia-current for 3.3.0-999. Missing asm header file or so it appears. Tried copying generated header files, something suggested for installing 295.20 on the 3.3 kernel series but could not find system.h in the generated tree. I will keep an eye out for information on nVidia on 3.3 kernels.

(3) Page fault to the contrary, I am not convinced this is an ext4 error. I keep thinking that it is an nVidia driver issue.

Questions: Is anyone having this sort of error running any graphics other than nVidia? What bios configuration is your video in (hybrid enabled/disabled, embedded enabled/disabled)? Number of video cards? 

What version of the BIOS are you running? Is this an issue with A07 only or is someone with A06 still in there having the problem, too.

What type of drive is your linux boot drive (where does grub find the boot images)? I am using a Kensington SSD (HyperX, I think the name is). 

Can you boot a live CD of the versions you cannot boot after install? Last I checked, I could not (I haven't burned any since -19 because I was so disappointed; could try -21 since it dropped yesterday).

Could someone point me to notes on building kernel modules for a different kernel than the current one? I want to build the nvidia-current package for all installed kernels and see if that helps. I admit to grasping at straws since I don't know what is wrong.

---

### Post by NHclimber on 2012-04-02
> **drbcladd said:**
> (1) NHclimber's recipe worked like a charm. Unfortunately it did not expose the whole stack trace. The last oops before locking up is a failure to sync in an interrupt handler. That handler appears to have been called in response to another error since there is still a stack trace rolling off the top of the screen.

Both end inside a page fault handler.

You can try '... vga=0xF07' which will give you a 60-line display (at least it does on my Quadro :) ).
Hopefully that's enough lines to show the entire stacktrace (amd64 kernel stacks are only 8K...)

> **drbcladd said:**
> Could someone point me to notes on building kernel modules for a different kernel than the current one? I want to build the nvidia-current package for all installed kernels and see if that helps. I admit to grasping at straws since I don't know what is wrong.

dkms is the framework ubu uses to build/install/manage specific kernel modules for installed kernels.
To build nvidia-current v295.20 against all installed kernels:
```
sudo dkms build -m nvidia-current -v 295.20 --all --verbose
```To install the nvidia kernel module for a specific kernel, e.g. 3.2.0-21 generic amd64:
```
sudo dkms install -m nvidia-current -v 295.20 -k 3.2.0-21-generic/4
```PS - Sorry I didn't reply to this earlier, but because you edited the post, I didn't know that you had updated this thread (I don't think ubuntuforums sends a re-notification in this case -- at least, it didn't to me).

---

### Post by drbcladd on 2012-04-02
No problem with the response. I figured out that I probably should have made a new entry after I edited the one...Not a big deal in any case. I can use -17 and so I can actually get work done.

So I just installed 3.4 rc1. Will build nvidia current for the other kernels and try a booting all of them. I will post a new reply when I have something to report.

---

### Post by gliderdad79 on 2012-04-02
nVidia Corporation G92 [GeForce GTX 260M] (rev a2)
Bios- A05
Intgrated and hybrid disabled in bios
Seagate Momentus XT 500GB 7200 RPM 2.5" SATA 3.0Gb/s with NCQ Solid State Hybrid Drive

When it was building the nvidia when I updated it built the current version one.

---

### Post by drbcladd on 2012-04-02
3.3-999 and 3.4rc1 both fail to compile the nVidia module. The error message is the same: 

```
In file included from /var/lib/dkms/nvidia-current/295.33/build/nv.c:13:0:
/var/lib/dkms/nvidia-current/295.33/build/nv-linux.h: At top level:
/var/lib/dkms/nvidia-current/295.33/build/nv-linux.h:114:75: fatal error: asm/system.h: No such file or directory

```

I built the 295.33 modules for all the installed kernels (thanks for that NHclimber; should have just man'd dkms...) and tried -18 and -21 (first and last failing 3.2.0 kernels). No joy. I managed to get a screen shot of the trace and, because the camera on the phone is crap, I transcribed it from the full-sized image. The scaled image is attached, too, in case there is interest in the code offsets and addresses reported in the stack trace.

```
                ?  ite_cir_isr
                ?  wakeup_preempt_entitity.isra
                handle_irqevent_percpu
                ?  check_preempt_curr
                handle_irq_event
                handle_edge_irq
                handle_irq
                do_IRQ
                common_interrupt
                ?  system_call_fastpath
RIP value
 (null)>]       (null)

io- not syncing: Fatal exception in interrupt
comm: upstart-udev-br Tainted: G   D    3.

                panic
                oops_end
                no_context
                __bad_area_nosemaphore
                ? native_send_call_func_single_ipi
                bad_area_nosemaphore
                do_page_fault
                ?  scsi_request_fn
                ?  blk_complete_request
                ?  scsi_done
                ?  ata_scsi_go_complete
                page_fault
                ?  ite+cir_isr
                ?  wakeup_preempt_entity.isra
                handle_irqevent_percpu
                ?  check_preempt_curr
                handle_irq_event
                handle_edge_irq
                handle_irq
                do_IRQ
                common_interrupt
                ?  system_call_fastpath

```

ite_cir is the infrared transciever, right? I am not even sure my box has one. Interestingly that is where the 3.3 and 3.4 kernels report a failure to handle the kernel or a failure to handle a NULL (NULL). Just interesting.

I am going to go and look for nVidia compiling information for the given error and see if that helps with 3.3 or 3.4. Any other suggestions happily accepted.

---

### Post by drbcladd on 2012-04-02
I have 3.3.0-999 20120329 booting. Added "nomodeset" at the end and it booted. 3.4.0 has error messages including "cannot handle this kernel" so I am guessing that the nVidia driver, though built, is checking the kernel version.

I managed to get the nVidia kernel compiling for the 3.3 and 3.4 kernels. See [http://ubuntuforums.org/showthread.php?t=1951457](http://ubuntuforums.org/showthread.php?t=1951457) for guidance. 

Oddly, though the nvidia module is installed for 3.3, it is using lower resolution drivers and I cannot convince it to use the nVidia driver.

On my miridian, it is time to put my boy to bed so I am going to have to put the experiments on hold, perhaps for 24 hours. As stated above, additional guidance or suggestions happily taken.

---

### Post by NHclimber on 2012-04-02
Congratulations! You have indeed discovered a real-life kernel crashing bug.

According to this [http://forum.notebookreview.com/alienware-m17x/471528-infrared-m17x.html](http://forum.notebookreview.com/alienware-m17x/471528-infrared-m17x.html)
the Alienware m17x does indeed have an ITE ir port.

The crash occurs because the isr (ite_cir_isr) jumps through a function table that the probe function (ite_probe) hasn't initialized before registering the isr. ite_probe also hasn't initialized the hardware yet either -- that's bad.

You should report this crashing bug on linux-kernel mailing list.

Why this happens now is because IRQ remapping (CONFIG_IRQ_REMAP) has been config'd on by default now. Even though IRQ remapping is experimental, it's on now for security reasons. Not sure why it immediately triggers an interrupt -- something to do with how the iommu performs remapping.

I'll post more later with some options for moving forward.

---

### Post by gliderdad79 on 2012-04-02
Meant to post I am running m17x.

---

### Post by drbcladd on 2012-04-03
Hate to seem stupid but where do I report the bug? `ubuntu-bug linux` is not happy because I am not running a supported kernel (of course I am: beta and an out-of-date beta at that). I am happy to provide all the information I can now that there is information to provide but I am not familiar with where I should file it.

---

### Post by NHclimber on 2012-04-03
Not at all stupid.

Probably easiest would be to make a Launchpad account and report the bug directly against the 'linux' package. Its actually an upstream bug but the ubu kernel team is pretty good about stuff like that. For one they'll want to blacklist that driver now.

I'd provide links but I'm replying from my phone right now, sorry. I can provide more details later today for suggested workarounds, ok?

---

### Post by NHclimber on 2012-04-03
To create a Launchpad account, go here [https://login.launchpad.net/+login](https://login.launchpad.net/+login) and click 'Create a new account'.  Do the whole thing including making a RSA key and signing the code of conduct. Hassle at first but -- trust me -- you're going to find other bugs and will want to comment on them ;)

After creating a Launchpad account, go here [https://bugs.launchpad.net/ubuntu/precise/+source/linux](https://bugs.launchpad.net/ubuntu/precise/+source/linux) and click 'Report a bug' over on the righthand column.

Title the bug something like 'Kernel panic booting Alienware M17x'. Make sure to report that this is for 3.2.0-21-generic on amd64. Provide the hand-copied stack trace and attach the photo.  Submit the bug.  Note the bug #.

In a terminal,
```
apport-collect -p linux <bug#>
```If you want to report this upstream (you should :) ), go here [http://bugzilla.kernel.org/enter_bug.cgi](http://bugzilla.kernel.org/enter_bug.cgi)
and make sure the bug report contains:
```
uname -r
lspci -vvvn
lspnp -vvv   <<=== you might need to install pnputils to get this
cat /proc/interrupts
```Good luck!

---

### Post by [Neurotic] on 2012-04-04
Thanks to all who are looking into this - I just ran into the same issue, and was about to update to 12.04 in an attempt to fix it - sounds like that won't work.

---

### Post by drbcladd on 2012-04-04
Thanks to NHclimber helping me gather enough information to figure out what bug report to file (and then give advice on filing the bug), I filed a new bug upstream at kernel.org [[https://bugzilla.kernel.org/show_bug.cgi?id=43042]](https://bugzilla.kernel.org/show_bug.cgi?id=43042]) and Launchpad [[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972723]](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972723])

I will keep an eye on the bugs to see if there is anything I can add to help them more. I finally understand why the booting of 3.3.0-999 was so hit or miss: it appears to be a race condition so if the cards all fall in just the right way, the driver initializes before it is needed. Otherwise...panic.

---

### Post by NHclimber on 2012-04-04
Good report on Launchpad. I added some commentary so that the ubu kernel team can make a quick decision regarding the bug. IMO, probably simplest to blacklist the driver for right now.

You mentioned in that report that the stack traces are different for 3.3 and 3.4 kernels. I know it's a hassle but just to be sure there's not something additional going on, would you post here photos of the other stack traces?  I can see the info in the photos just fine -- no need to hand-copy the traces.

Speaking of blacklisting, do your working kernels boot into the same root as the non-working kernels? I ask because, if so, I can provide simple instructions for building an initramfs that blacklists that driver so we could see if that is a sufficient workaround.

---

### Post by drbcladd on 2012-04-04
They all boot to the same root.

I will reboot for photos in the morning (call it 9 or 10 hours). I am preparing class lectures right now so I want to keep working. I will also build the initramfs then.

Thanks again for all the assistance.

---

### Post by gliderdad79 on 2012-04-04
Thank you drbcladd and NHclimber for your work in tracking and reporting!!

---

### Post by NHclimber on 2012-04-05
To blacklist (not load) the suspect driver (ite-cir) for a specific kernel (say, 3.2.0-21-generic), boot with a working kernel into the same root. Then,
```
echo "blacklist ite-cir" | sudo tee /etc/modprobe.d/ite-cir.conf
sudo depmod -a 3.2.0-21-generic
sudo update-initramfs -u -k 3.2.0-21-generic
```Reboot and test.

Note that subsequent kernel updates will also use the blacklist so you won't need to continually depmod/update-initramfs (that will happen automatically).

There is no automatic way for depmod to be run against already existing known kernels. It has to be run individually.
update-initramfs can generate matching initramfs for all known kernels with
```
sudo update-initramfs -u -k all
```

---

### Post by Wise Ferret on 2012-04-05
NHClimber, this has solved my problem with dell xps studio 1340! Thank you very very much!
I am writing proudly using a working 3.2.0-22 kernel.

---

### Post by drbcladd on 2012-04-05
NHClimber - Fixes the bug for me with all 3.2.0 kernels (in the precise mainline): -18 through -22. -17 continues to boot as normal with the module blacklisted.

3.3.0-999 and 3.4.0-999 both panic on boot. It is a weird panic in that there are two distinct sets of core dumping: one dump, ten to fifteen seconds, then another screen of output with another core dump (or so it appears). Snapped pictures at the first and second screens (may have missed some lines between). 

The snaps are of 3.0.4.999, Apr 04 2012 daily. I used the "16" trick to permit the vga parameter and I specifed nomodeset (since one of the boots seemed to have a video problem).

This is after blacklisting the driver for all installed kernels. 

So: Good news that I can reliably cold boot and warmboot any of the 3.2.0 kernels (I, too, am proudly using 3.2.0-22); not so good news, kernels at or above 3.3 still panic though with different error messages than when the module was not blacklisted.

I am guessing you'll want to see the error message for 3.4.0-999 with the module. I will unblacklist it and see what I can do. Note that the numbers after the file name are local time stamp so you can order them.

---

### Post by NHclimber on 2012-04-05
> **drbcladd said:**
> NHClimber - Fixes the bug for me with all 3.2.0 kernels (in the precise mainline): -18 through -22. -17 continues to boot as normal with the module blacklisted.

Good to know. You should update both bug reports indicating that when you blacklisted ite-cir, the kernel panic did not occur. Don't mention results for 3.3 or 3.4 -- those are confounding variables at the moment.

> **drbcladd said:**
> 3.3.0-999 and 3.4.0-999 both panic on boot. It is a weird panic in that there are two distinct sets of core dumping: one dump, ten to fifteen seconds, then another screen of output with another core dump (or so it appears). Snapped pictures at the first and second screens (may have missed some lines between). 

The snaps are of 3.0.4.999, Apr 04 2012 daily. I used the "16" trick to permit the vga parameter and I specifed nomodeset (since one of the boots seemed to have a video problem).

I think this is a different problem. The first crash is the only relevant one: the second photo is the kernel recognizing that a CPU is no longer schedulable.  Too bad the entire trace wasn't captured.  Let me mull on this one.

> **drbcladd said:**
> I am guessing you'll want to see the error message for 3.4.0-999 with the module.

No need to do this - the relevant code in that module is unchanged up to and through mainline.

---

### Post by drbcladd on 2012-04-05
I have a decent digital video rig at school; tomorrow I will try filming the boot sequence and see if I can piece the whole sequence together. No idea if it is shooting fast enough (never had to think about it before) or if there will be tearing or timing issues (lcd display so probably not...no refresh interval).

---

### Post by drbcladd on 2012-04-06
Well, now I know: the scroll speed on the laptop exceeds the frame rate of the camera. Or, at least, it is possible to get some really smeared frames. 

I had thought I could capture individual frames and paste them up into a panarama. Instead I left it in the form of a .dv video (didn't want to lose any of the limited fidelity). I left the font size as large as possible to make it easier to read and trimmed it down to fifteen seconds (which are about two seconds in the boot sequence). 

The 7z compression is amazing: it compressed the file from 52 to 3 MB (about triple the upload quota for this forum). Put it on my pages: 

[http://cs.potsdam.edu/faculty/laddbc/KernelPanic3.4.0Alienware.dv.7z](http://cs.potsdam.edu/faculty/laddbc/KernelPanic3.4.0Alienware.dv.7z)

---

### Post by moerch13 on 2012-04-07
Just want to join the cheering crowd. Thanx to this thread i finally got my XPS 1340 running 12.04. I had to start off with the beta1 image to get a working kernel installed from which i could then use the blacklist option on the newer kernels as described here. Now running .22 image without a hiccup. Thanx again.

---

### Post by NHclimber on 2012-04-09
> **drbcladd said:**
> 3.3.0-999 and 3.4.0-999 both panic on boot. It is a weird panic in that there are two distinct sets of core dumping: one dump, ten to fifteen seconds, then another screen of output with another core dump (or so it appears). Snapped pictures at the first and second screens (may have missed some lines between). 

The snaps are of 3.0.4.999, Apr 04 2012 daily. I used the "16" trick to permit the vga parameter and I specifed nomodeset (since one of the boots seemed to have a video problem).

I'm pretty sure these panics are nvidia-related.  Check out this thread  [http://ubuntuforums.org/showthread.php?t=1952729](http://ubuntuforums.org/showthread.php?t=1952729)

---

