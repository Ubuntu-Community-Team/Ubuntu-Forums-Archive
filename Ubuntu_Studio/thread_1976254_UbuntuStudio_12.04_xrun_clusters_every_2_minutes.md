---
title: "UbuntuStudio 12.04 xrun clusters every 2 minutes"
date: 2012-05-08
forum: Ubuntu Studio
---

### Post by CrocoDuck on 2012-05-08
Well: after installing ubuntu studio 12.04 on laptop and spent some time on tuning the system, I found that I cannot eliminate xrun clusters that comes every ca 2 minutes. That happens with both integrated soundcard (HDAintel) and external USB soundcard (UCA202). When I look in /proc/interrupts I get:

```
           CPU0       CPU1       
  0:    1377358    1625643   IO-APIC-edge      timer
  1:        919       1041   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:       3329        108   IO-APIC-fasteoi   acpi
 12:     434305       8745   IO-APIC-edge      i8042
 16:      29754        248   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb7, ath9k
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb6
 20:          9         13   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 40:          0          0   PCI-MSI-edge      PCIe PME
 41:          0          0   PCI-MSI-edge      PCIe PME
 42:       8458      10862   PCI-MSI-edge      ahci
 43:          0          0   PCI-MSI-edge      eth0
 44:       6612       6287   PCI-MSI-edge      i915
 45:     577118     149127   PCI-MSI-edge      snd_hda_intel
NMI:          0          0   Non-maskable interrupts
LOC:    1431020     735683   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:    1204018    1323618   Rescheduling interrupts
CAL:        256        452   Function call interrupts
TLB:       8214       7854   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          6          6   Machine check polls
ERR:          0
MIS:          0

```

If I try to turn off the wireless device (by pressing the apposite button) the xrun number explodes. It smells like IRQ's issue (don't it?). I'd like to use new ubuntu studio 12.04 features on live performance, how can I menage IRQs on ubuntu? Or what if IRQ has nothing to do with that clusters?

P.S.: I tried realtime kernel, it freezes on "Loading initial ramdisk".

---

### Post by Sylos on 2012-05-08
Hello.

Just wondering if you have tried turning all none essential functions off in your BIOS (ie. wireless, ethernet, speed stepping/turbo boost etc). If you can then turning these off and testing may give you a hint as to what is causing the problem.

Could you post up your jack settings as well?

As far as managing IRQs is concerned there is an rtirq script but I havent used it and I think it will only work with the RT kernels (could be wrong on that). Where did you get the kernel you tried from?

Cheers

---

### Post by CrocoDuck on 2012-05-09
Thanks for your reply, so sorry to being able to answer just now. Unfortunately, my bios don't let me set the settings you said (only boot related things and passwords settings are aviable).

I tried 2 realtime kernels, one was from abogani repo, one from kxstudio. They gave both to me the same problem, I also tried to regenerate initrd.img-3.2.0-23-realtime unsuccessfully. Dont know if rtirq works with lowlatency (should do it at the current version), but I tried the commands that basically rtirq automatizes (following [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)). I probed priorities with

```
ps -eLo pid,cls,rtprio,pri,nice,cmd |grep -i "irq"

```

Then I used

```
sudo chrt -f -p -priority- -pid-
```

It was effective, reduced the events in the cluster, but I still have a cluster every 2 exactly minutes, if I turn off the wireless device I have a xrun every 4 seconds.

Here there is the .jackdrc file:

```
/usr/bin/jackd -P80 -t5000 -dalsa -r48000 -p128 -n2 -D -Chw:0,0 -Phw:0,0

```

I also tried this one:

```
/usr/bin/jackd -P89 -t5000 -dalsa -r48000 -p64 -n3 -D -Chw:0,0 -Phw:0,0

```

I must gain less than 10 msec of latency, even if 10 msec is the smallest audible latency for human ear, it waste everything you play, expecially if we talk of groove based genres like funk, R&B, soul etc... (that are the ones I try to play). So I think the biggest latency I want to ask to my laptop is 7 msec. Probably I'll give a try to rtirq.

---

### Post by Sylos on 2012-05-09
It seems odd that this is happening so regularly - at exactly 2 minute intervals. It suggests some service is causing the interrupt. I dont know how you can try and track it down at the moment.

For the sake of testing for now I would recommend bumping up your periods/frames to 256 and see what happens.

Are you running with cpu scaling enabled? If so try turning that off and see if it makes a difference. 

I dont understand why the RTKernel didnt want to play ball for you. I believe the abogani 12.04 kernel should be working (last time I looked I think it was).

EDIT: I wonder if running htop in a terminal while you run jack might help - you may see a spike from something when the xruns happen.

---

### Post by CrocoDuck on 2012-05-09
Thanks for advice! All the times I run Jack I'm usually set CPU governors to "Performance". Bumping periods/frames to 256 is not very effective, the clusters seems made of 2-3 events now (and if I turn off wireless a lot of xruns comes). Running htop while running jack looks like a good idea, and makes me feel like reading The Matrix :). I found some suspicious process, tried to tune priority or kill it... unsuccessfully. I'd like to view if some matching time regularity exist in CPU% by some process, but I don't think I can make it without a script. If I'll have enought time I'll try to write something can help me (if I can not found something online).

Tryng Tango Studio 1.2 (and than installing it on the same machine, dual boot) I've noticed that to prevent the only 1 xrun that came every 2 minutes I simply have to turn off the wireless! It becomes much more stable. I tried to point out why, in order to solve the problem on Ubuntu installation (of course, now I can try to use Tango for live performances, but I think that solve this issue may be useful for someone). On Tango I get that for cat /proc/Interrupts: 

```
           CPU0       CPU1       
  0:     103429     123966   IO-APIC-edge      timer
  1:         25        207   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:         42         39   IO-APIC-fasteoi   acpi
 12:      21579         68   IO-APIC-edge      i8042
 16:       5161         65   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb7, ath9k
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8
 19:          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb6
 20:         11          8   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:         83         84   IO-APIC-fasteoi   HDA Intel
 26:          0          0   PCI-MSI-edge      eth0
 27:       4112        870   PCI-MSI-edge      ahci
 28:         69       1156   PCI-MSI-edge      i915
NMI:          0          0   Non-maskable interrupts
LOC:      35514      17763   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:        707        771   Rescheduling interrupts
CAL:         43        186   Function call interrupts
TLB:        206        174   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          0
MIS:          0
```

HDA intel sits on 22, and not on 45. I had a surprise probing priorities:

```
:~$ps -eLo pid,cls,rtprio,pri,nice,cmd |grep -i "irq"
    4  TS      -  19   0 [ksoftirqd/0]
    6  TS      -  19   0 [ksoftirqd/1]
 1527  TS      -  19   0 grep --color=auto -i irq

```

Currently on Ubuntu the situation is this (I expected finding something like this on Tango too):

```
:~$ps -eLo pid,cls,rtprio,pri,nice,cmd |grep -i "irq"
    3  TS      -  19   0 [ksoftirqd/0]
    9  TS      -  19   0 [ksoftirqd/1]
   20  FF     50  90   - [irq/9-acpi]
   39  FF     50  90   - [irq/40-PCIe PME]
   40  FF     50  90   - [irq/41-PCIe PME]
   48  FF     50  90   - [irq/42-ahci]
   57  FF     50  90   - [irq/19-ehci_hcd]
   61  FF     50  90   - [irq/20-ehci_hcd]
   62  FF     80 120   - [irq/16-uhci_hcd]
   63  FF     76 116   - [irq/21-uhci_hcd]
   64  FF     77 117   - [irq/20-uhci_hcd]
   65  FF     78 118   - [irq/19-uhci_hcd]
   66  FF     79 119   - [irq/16-uhci_hcd]
   67  FF     79 119   - [irq/18-uhci_hcd]
   68  FF     74 114   - [irq/12-i8042]
   69  FF     75 115   - [irq/1-i8042]
   70  FF     50  90   - [irq/8-rtc0]
  296  FF     50  90   - [irq/44-i915]
  739  FF     20  60   - [irq/16-ath9k]
  798  FF     50  90   - [irq/43-eth0]
  997  FF     85 125   - [irq/45-snd_hda_]
 1078  TS      -  19   0 /usr/sbin/irqbalance
 3158  TS      -  19   0 grep --color=auto -i irq


```

Despite not know why on Tango I see only that few lines (maybe I only have to search the information somewhere else); everything makes me think that maybe the issue is hidden below some kind of strange bug or feature in the new 3.2 kernel, since on Tango I run 2.6.32-38-lowlatency. The thing I don't understand Is why under Ubuntu xrun number explodes if I turn off wireless. Is not a contradiction?

---

### Post by sgx on 2012-05-09
Maybe some startup nonsense polls the wireless,
expecting it to be on, and goes wild searching for it
when it's gone?

Turning off the webcam also can help. Having networks in
the off position, is a real plus, and removing pulseaudio
is another good thing, it's been an anchor on sailboats in
the open sea for years now.

A videocard with inclusive sound capabilites, also cam be an issue.

Use htop to see what runs at startup, and google them by name,
with audio and ubuntu in the search string.

I have 13 lines total in htop, its pretty lean.
Cheers  (glad Tango is working for you! )

---

### Post by Sylos on 2012-05-10
Just a thought - but maybe you could try finding what kernel module is used for your wireless card and then blacklist it. I expect it will either make the problem worse (xruns all the time) or maybe get rid of the issue. Might be worth a shot.

Cheers

---

### Post by CrocoDuck on 2012-05-11
Yeah Guys! Everything was easier than expected, but I could never get it without your help! Basically I applied the sgx's advice, starting from the script you can find here (I feel so stupid, I read that page a gazillion times...): [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf) , paragraph "Disabling everything you don't need". Just running it as it comes, I'm having a nice without-xrun-experience! I've found some other service I can remove in order to have MOAR performances! Sorry for my late reply, but I was finishing building a guitar stompbox (linux docet: everything is better if handmade!).

I post my latest jack configuration too, might be useful:

```
/usr/bin/jackd -P80 -t5000 -dalsa -r48000 -p128 -n2 -D -Chw:0,0 -Phw:0,0
```

So, thanks guys!

P.S.: is very stable now, is running from 30 minutes without xruns.

---

