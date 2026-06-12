---
title: "Optimizing USB audio latency"
date: 2010-10-29
forum: Ubuntu Studio
---

### Post by windeguy on 2010-10-29
I have a Lexicon Omega that works fairly well with Ubuntu Studio on my laptop.  I have read that there are tweaks that can be done to get the audio latency down to the 3 to 5 ms range and that would be great if possible. For example I have seen this information:

[B]Tuning USB devices for minimal latencies

On linux-audio-user Christoph Eckert brought up the question about how to get better latencies out of USB audio devices, and USB guru Clemens Ladisch had a very good tip: The snd-usb-audio module accepts a module option called "nrpacks", which according to modinfo, sets the: Max. number of packets per URB. (int). Setting this to "nrpacks=1" should allow latencies in the area of 4-6 msecs.

Unfortunatly on some systems/kernels nrpacks=1 conflicts with a feature called "USB bandwidth allocation" in the kernel. Here's the way out:

    * In the kernel config ensure that both options (taken from a 2.6.10) are disabled:: 

:[   ] Enforce USB bandwidth allocation (EXPERIMENTAL)
:[   ] Dynamic USB minor allocation (EXPERIMENTAL)

    * Ensure to load the snd-usb-audio module with the parameter "nrpacks=1", maybe including it into one of the boot scripts:: 

modprobe snd-usb-audio nrpacks=1

    * Or use the module configuration line (e.g. in /etc/modprobe.conf): 

options snd-usb-audio nrpacks=1

    * Now invoke JACK with the following command (or entering the corresponding values into Qjackctl): 

jackd -R -P89 -dalsa -dhw:2 -r48000 -p256 -n3 -S

You can omit the "-S" if your card supports 24bit or 32bit access as well and you want to use that. [/B]

 I am not finding the exact files that are mentioned above. 
Where would I put "modprobe snd-usb-audio nrpacks=1" ?
Will this method work in Ubuntu Studio and how do I apply it?

---

### Post by Pablo_F on 2010-10-29
Hi again, 

You can put the line:

**options snd-usb-audio nrpacks=1**

in this file:

**/etc/modprobe.d/alsa-base.conf**

You have to edit it as administrator, so you can do a:

**sudo gedit /etc/modprobe.d/alsa-base.conf**

add the line and restart the alsa modules with:
[B]
sudo alsa force-reload[/B]

With the above way the snd-usb-audio module with this nrpacks option is loaded automatically at boot so you don't need to modprobe it (sudo modprobe from a terminal) every time.

To check the kernel config options, I think that you can look for them in 

/usr/src/linux/.config

But I am almost sure that both options are disabled in a modern ubuntu. 

The jack command line example is a bit obsolete. You don't need the -S or the -R. Just start the server as you always do, but make sure you choose 48000 Hz and 3 periods per buffer as this seems to be the best option for usb cards.

Cheers! Pablo

---

### Post by AutoStatic on 2010-10-30
nrpacks is obsolete also: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html)
Achieving the aformentioned low latencies is all about properly configuring your system: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

Best,

Jeremy

---

### Post by Pablo_F on 2010-10-30
Cool, thanks Auto!

Paradox: As Linux audio configuration gets easier (in general) in each distro release, it gets more difficult at the same time because the info grows and grows and we users tend to look at the wrong places where obsolete recipes are, even if they were written by authoritative people!.

Alvin Toffler pointed out:
&#8220;The illiterate of the 21st century will not be those who cannot read and write, but those who cannot learn, unlearn, and relearn.&#8221;

Linux must be a futurist SO even if it is easier than ever. But then, go figure the problem when you have one! :lolflag: I am kidding, we just have to learn to look at the right places, like the docs in your own computer, the LAU mailing list and some advanced users' posts in several fora.

Cheers! Pablo

---

### Post by windeguy on 2010-10-31
Thank you AutoStatic and again to Pablo for being of assistance. 

I had made the educated guess as to where to put 
options snd-usb-audio nrpacks=1 
and did not see that it made any difference after making that addition.  

My next questions were going to be where I could optimize the system to reduce overhead and increase speeds and AutoStatic anticipated that. 

One thing I noticed in the links provided was that ext3 file format is supposed to be better than ext4.  I wish I would have known that before. 

I am sure I will have questions as I slowly explore the optimization process.

---

### Post by AutoStatic on 2010-10-31
> **windeguy said:**
> One thing I noticed in the links provided was that ext3 file format is supposed to be better than ext4.  I wish I would have known that before.I put it there in the LinuxMusicians Wiki after reading some articles on the Phoronix site. But maybe I should change it in the Wiki because regarding audio I don't think it really matters. Ext4 should be just fine.

Best,

Jeremy

---

### Post by windeguy on 2010-10-31
I ran uname -a and go this result:


mike@mike-laptop:~$ uname -a
Linux mike-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

I then went to Synaptic and typed in  real time kernel. 

Synaptic showed that I have

linux-rt 2.6.31.11.13 installed along with other files that seem to indicate I have the real time kernel. 


Am I running a real time kernel?  If not how do I install the real time kernel?

---

### Post by Pablo_F on 2010-10-31
Hi, 

It is not a matter of having it installed, you must boot your computer with one kernel or another. You should see it as a boot option when you reboot. Then run uname again just to make sure.

Then run "lsusb" and "cat /proc/interrupts". That's about your hardware configuration, which you need to know to take advantage of having a linux-rt kernel. If you wish, post here the results and we will try to help.

Cheers! Pablo

---

### Post by windeguy on 2010-10-31
Feeling like a dummy. I was just booting from the first option which was non real time and never even noticed the real time option to boot from several lines below. (I guess you cannot trust the Jack GUI which was showing RT mode as active)

After booting to the real time kernel here are some results from the commands uname -a, lsusb and cat /proc/interrupts. 

Please note that I have a Behringer Keyboard attached to a USB port and a Lexicon Omega attached to another USB port. 

Please let me know if there are any tweaks I am missing. 



mike@mike-laptop:~$ uname -a
Linux mike-laptop 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux

mike@mike-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 008: ID 0451:3200 Texas Instruments, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1397:01b0 BEHRINGER International GmbH 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


mike@mike-laptop:~$ uname -a
Linux mike-laptop 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 12:28:53 UTC 2010 i686 GNU/Linux
mike@mike-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 008: ID 0451:3200 Texas Instruments, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1397:01b0 BEHRINGER International GmbH 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mike@mike-laptop:~$ cat/proc/interrupts

mike@mike-laptop:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        147          0   IO-APIC-edge      timer
  1:        603          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:      25868          0   IO-APIC-fasteoi   acpi
 12:     284130          0   IO-APIC-edge      i8042
 14:      12301          0   IO-APIC-edge      ata_piix
 15:       4446          0   IO-APIC-edge      ata_piix
 16:         38      16368   IO-APIC-fasteoi   uhci_hcd:usb5, i915
 18:       6246     846263   IO-APIC-fasteoi   uhci_hcd:usb4, eth1
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 22:       1018          0   IO-APIC-fasteoi   tifm_7xx1, mmc0, yenta, HDA Intel
 23:         37       3286   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
283:          0          0   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:    1271723    1280813   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:     980277     776473   Rescheduling interrupts
CAL:      18557      21056   Function call interrupts
TLB:      28568       4914   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          5          5   Machine check polls
ERR:          1
MIS:          0
mike@mike-laptop:~$

---

### Post by Pablo_F on 2010-10-31
> (I guess you cannot trust the Jack GUI which was showing RT mode as active)

Jack realtime mode has nothing to do with the kernel being rt or generic. It has to do with the realtime priority scheduling which can be gained by a user if the pam limits are properly configured, which can be done in a generic modern kernel (the lines rtprio and memlock in /etc/security/limits.d/audio.conf). Check with "ulimit -r -l". See [http://jackaudio.org/realtime_vs_realtime_kernel](http://jackaudio.org/realtime_vs_realtime_kernel)

Your audio card is connected in Bus4, in IRQ 18, sharing interrupt number with eth1.

You can try installing the rtirq script (just install the package "rtirq-init") and then edit as superuser the configuration file (/etc/default/rtirq). 

Try setting the RTIRQ_NAME_LIST variable to "rtc usb4". Reboot and check priorities with htop in a terminal (I suggest terminator which does not have F10 conflicts). F2, display options, do not hide kernel threads. F6, sort by PRI. Check if IRQ18, usb4 is high (with -90 or so, before other IRQ's).

Needless to say, you have to decrease the periods / buffer number in qjackctl's setting and see if lower latencies are xrun free.

Another important tweak is cpufreq. You don't want ondemand. (There is a gnome panel applet). 

The realtime configuration quickscan script in linuxmusicians is very helpful. See also [http://www.rncbc.org/drupal/node/107](http://www.rncbc.org/drupal/node/107)

Cheers! Pablo

---

### Post by windeguy on 2010-10-31
When I booted in the RT Kernel, I noticed that I am not getting latencies as low as in the normal kernel.   Using my USB audio device I can get down to 256 frames using the normal kernel  where things start to break up, but I can only get to 1024 frames in the ReatTime Kernel before I see problems.  This is unexpected.  Any ideas on that from what you see in my post above.

Also, how do I run the realtimeconfigquickscan script?  Being a newbie in Linux I am not sure how to do that.

---

### Post by windeguy on 2010-10-31
I now understand the point about JACK running in real time mode being independent of a real time kernel. 

The rtirq script was already installed. 

This was the existing line in rtirq:

RTIRQ_NAME_LIST="rtc snd usb i8042"

I changed it to: 

RTIRQ_NAME_LIST="rtc usb4"

Checking in htop for irq18 shows that it now has a priority of -86 right behind irq/8rtc0 which is -91.


Unfortunately,  the normal kernel is working better than when I boot from the RT kernel.  I can run at 512 frames per second in the normal 
kernel but that frame rate stutters and skips badly in the real time kernel. Since I realized today I was always
using the normal kernel, are there some other changes I need to make to the RT kernel?

---

### Post by Pablo_F on 2010-11-01
> how do I run the realtimeconfigquickscan script?

1. Install mercurial, perl-tk and download the script:

**sudo apt-get install mercurial perl-tk**
**hg clone [https://realtimeconfigquickscan.googlecode.com/hg/](https://realtimeconfigquickscan.googlecode.com/hg/) realtimeconfigquickscan **

2. Run the GUI script

**cd realtimeconfigquickscan**
[B]
perl QuickScan.pl[/B]

3. For completeness, run the original script

**perl realTimeConfigQuickScan.pl**

See:

[http://www.linuxmusicians.com/viewtopic.php?f=27&t=452](http://www.linuxmusicians.com/viewtopic.php?f=27&t=452)
[http://www.linuxmusicians.com/viewtopic.php?f=27&t=2798](http://www.linuxmusicians.com/viewtopic.php?f=27&t=2798)
[http://wiki.linuxmusicians.com/doku.php](http://wiki.linuxmusicians.com/doku.php)

Cheers! Pablo

---

### Post by windeguy on 2010-11-02
Thank you again for all the suggestions.  I was able to install and run the RealTimeCofigQuickScan and make the suggested changes to the IRQ settings. 

However, even after going through the IRQ settings, running both versions of RealTimeCofigQuickScan and correcting 5 situations that were found so that I am now "good" on all results, I am at a loss as to what to do next.  

I still get better latency running the "generic" kernel than I do with the 
RT Kernel. 

What else can I check?


This might be relevant: When I boot using the RT Kernel, I get this message for  few seconds:

**mount: mounting none on /dev failed: no such device**
Then I see a number of other messages flash by quickly. 
I do not see this same behavior when I boot the generic kernel. 
Is this potentially relevant?

---

### Post by AutoStatic on 2010-11-02
> **windeguy said:**
> However, even after going through the IRQ settings, running both versions of RealTimeCofigQuickScan and correcting 5 situations that were found so that I am now "good" on all results, I am at a loss as to what to do next.  

I still get better latency running the "generic" kernel than I do with the 
RT Kernel. 

What else can I check?I think you might benefit from a -realtime kernel instead of the -rt kernel that is available for Lucid. The 2.6.31-11-rt kernel doesn't seem to perform that well on a notebook or netbook. You could try the one from Alessio Bogani's PPA: [https://launchpad.net/~abogani/+archive/ppa/+packages](https://launchpad.net/~abogani/+archive/ppa/+packages)


> **windeguy said:**
> This might be relevant: When I boot using the RT Kernel, I get this message for  few seconds:

**mount: mounting none on /dev failed: no such device**
Then I see a number of other messages flash by quickly. 
I do not see this same behavior when I boot the generic kernel. 
Is this potentially relevant?No: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/599396](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/599396)

---

### Post by windeguy on 2010-11-02
> **AutoStatic said:**
> I think you might benefit from a -realtime kernel instead of the -rt kernel that is available for Lucid. The 2.6.31-11-rt kernel doesn't seem to perform that well on a notebook or netbook. You could try the one from Alessio Bogani's PPA: [https://launchpad.net/~abogani/+archive/ppa/+packages](https://launchpad.net/~abogani/+archive/ppa/+packages)



No: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/599396](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/599396)
It is good to know that the mount issue is a harmless bug.

Thank you for the advice. It does seem that there is an issue with the -rt kernel for Lucid.

Since I am still a newbie with respect to Linux, I do not yet know the procedure to install the kernel you recommend since I have been using the SYNAPTIC manager to this point.  Can you describe how I would install the kernel you recommend?

---

### Post by AutoStatic on 2010-11-02
64bit: [https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_amd64.deb](https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_amd64.deb)
32bit: [https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_i386.deb](https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_i386.deb)

Download the one you need, doubleclick it and it should install.

---

### Post by windeguy on 2010-11-02
> **AutoStatic said:**
> 64bit: [https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_amd64.deb](https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_amd64.deb)
32bit: [https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_i386.deb](https://launchpad.net/~abogani/+archive/ppa/+files/linux-image-2.6.33-29-realtime_2.6.33-29.1_i386.deb)

Download the one you need, doubleclick it and it should install.

Hi Autostatic, 

I downloaded the .deb package for 32 bit and installed it.  Now I do not get a menu on boot up where I can choose which version of linux to boot, it defaults to the new version. 

uname -a shows this result: 

mike@mike-laptop:/etc/default/realtimeconfigquickscan$ uname -a
Linux mike-laptop 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 20:14:20 UTC 2010 i686 GNU/Linux

For some reason, I cannot use wireless access for the internet, (perhaps I need to add support back for my wireless card?) but the wired connection is still working. I did a check of all the other settings I went through and they seem to be intact.  I will now see if the latency is better.

---

### Post by windeguy on 2010-11-02
After loading

Linux mike-laptop 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 20:14:20 UTC 2010 i686 GNU/Linux


The latency is worse than it was before. And I don't have the option of booting one of the other kernels since this version now boots directly. 
How do I take a step back or is there something else to try?

---

### Post by AutoStatic on 2010-11-02
> **windeguy said:**
> Now I do not get a menu on boot up where I can choose which version of linux to boot, it defaults to the new version.That's weird, you should always get a menu when you have a dual boot system. You can invoke the GRUB boot menu by holding down the Shift key during boot up. But it should appear, otherwise you can try to reload the boot menu configuration by running **sudo update-grub**

> **windeguy said:**
> mike@mike-laptop:/etc/default/realtimeconfigquickscan$ uname -a
Linux mike-laptop 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 20:14:20 UTC 2010 i686 GNU/LinuxLooks good to me. Except for the fact that the realtimeconfigquickscan script shouldn't be in */etc/default* ;) It's a user script, so no need to move it out of your home directory.

> **windeguy said:**
> For some reason, I cannot use wireless access for the internet, (perhaps I need to add support back for my wireless card?) but the wired connection is still working. I did a check of all the other settings I went through and they seem to be intact.  I will now see if the latency is better.That is because a -realtime kernel does not contain any closed source drivers and no specific Ubuntu patches. But who knows, maybe wireless is the potential bottleneck. I have it disabled when I'm doing music related things. Just like all the other drivers and services that cause overhead or that are simply distracting (Bluetooth, cups, saned, PulseAudio, wireless, network-manager, cpu frequency scaling etc. etc.).

---

### Post by windeguy on 2010-11-03
Yesterday I upgraded to the latest version of Ubuntu Studio. That took about 5 hours to download and install. 

I just ran **sudo update-grub**, but that does not bring back the  boot menu despite looking like it created a new boot file with the proper list. 

I have to hit the shift key on bootup to see the menu.  Is there something I need to do manually to get the automatic boot menu back?

---

### Post by Pablo_F on 2010-11-03
You need to change something in /etc/default/grub (I am not sure what exactly) and then run "sudo update-grub" again. Look at [http://ubuntuforums.org](http://ubuntuforums.org) /showthread.php?t=1195275

---

### Post by AutoStatic on 2010-11-03
From [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

These are the default settings:```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```Settings you should check are GRUB_HIDDEN_TIMEOUT (it should be commented) and GRUB_TIMEOUT (should be set to a number of seconds. Default is 10).

---

### Post by windeguy on 2010-11-04
Thank you for telling me what to look for. 

Going to this link as Pablo suggested

[http://ubuntuforums.org](http://ubuntuforums.org) /showthread.php?t=1195275

Told me that I have to edit to comment out the line by changing it to

**#GRUB_HIDDEN_TIMEOUT=0** in the **/etc/default/grub** file


and not the **/boot/grub/grub.cfg ** file  (Yes Pablo did mention this was the correct file and 
AutoStatic had the correct line to modify)

Then run the command 
**sudo update-grub**

and the **/boot/grub/grub.cfg ** file is automatically regenerated and 
I have the boot menu back.

However, preliminary testing is showing me that there isn't any significant difference in performance between running 
the generic kernel and the "tweaked" -realtime kernel I recently added with respect to latency.  
Either there is some other tweak still to be made or they both work about the same.

---

### Post by sgx on 2010-11-04
A good performance test is to play a sustained chord on a complex zynaddsubfx patch, and keep adding it in the 16 available parts, and compare when the first audio corruption occurs.
Cheers

---

### Post by Pablo_F on 2010-11-04
As a side note, you can measure the real latency of the jack-audio card system with jdelay. 

Cheers! Pablo

---

### Post by windeguy on 2010-11-08
Thank you all again for your help. I now have my ACER laptop running quite well with Ubuntu Studio and the -realtime kernel suggested in this thread. Latencies using my USB connected Lexicon Omega are sub 10ms with usable latency so far looking like about 5ms. 

I actually am getting better performance using the -realtime kernel when running Ardour.  If I use REAPER under WINE, the difference is not as big between to two kernels.   I anxiously await the release of ARDOUR 3, which is one of those any day, any week, any month but no date known yet releases. :popcorn:

I will start a new thread about my experiences with installing Ubuntu Studio over the past couple of days. I used the same advice in this thread to optimize that PC.  I have a continuing issue with an NVIDIA graphics card that I need some help with.

---

