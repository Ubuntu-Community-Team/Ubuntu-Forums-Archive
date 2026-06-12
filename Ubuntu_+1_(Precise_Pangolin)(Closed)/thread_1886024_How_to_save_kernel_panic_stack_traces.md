---
title: "How to save kernel panic stack traces"
date: 2011-11-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jordanwb on 2011-11-24
Last night I installed linux-image-3.2.0-1-generic on my laptop and rebooted. Twice while chatting on IRC I got a kernel panic which I believe to be caused by the ath9k driver. How would I go about saving the stack trace and other stuff aside from taking a picture with my camera?

---

### Post by ventrical on 2011-11-24
I think that they may be saved in  kernel log files . I was just reading some the other day and they definitely save kernel panics.

just a sec...

yep 


  var/log/kern.log

and other logs also..

---

### Post by effenberg0x0 on 2011-11-24
Well, I'm far from being a kernel hacker. I'm gonna throw some of the things I do and others can add more and correct me if I'm wrong.

The relevant thing is: Can you get the function name or the EIP address? If you can, just take note of it, no photo needed.

Then, to investigate:
First, you need an uncompressed image, which is not installed by default.
[http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/)
 
You also need to compile your kernel with debugging info, so add -g1, -g2 or -g3 to MAKE and build it. Of course you should take out optimizations (-O0) and don't strip anything, so you have some debugging info when the crash happens.

Given you have that, and you have a crash now with a call trace displaying. If you don't know what function crashed, all you have to do is get the EIP address and throw it in gdb. You need gdm compiled with kernel debugging support too (to support the -K option)

sudo gdb -k ../../vmlinux (from the uncompressed image)
(gdb) disas 0xfbfffc00 (disas is short for disassemble)
sata_do_something+0x26/0x41
... You'll have a lot of output here, but all you need is the function that was on stack at that time.

At this point things become easier, because you can cd to your kernel sources directory and grep this function to find out which source/object file has it. Let's say it's sata_example.c/sata_example.o.

gdb sata_example.o
list *(sata_do_something+0x26)

This will show you the exact source code lines of sata_example.c which produced the object code (of sata_example.o) that was on stack when this function crashed.

The thing is, when you are debugging a running kernel, you can't change variable values, overwrite memory addresses, watch a breakpoint anywhere, etc. 

The professional guys here use a much more complex and complicated method, in which you have a "dumb terminal" PC connected via serial cable to their PCs. When a crash occurs, they can investigate things thoroughly by using this external terminal.

I think this is an art in itself, very complex. Professional Kernel dbg people are not from this planet.

---

### Post by Jordanwb on 2011-11-24
> **ventrical said:**
> I think that they may be saved in  kernel log files . I was just reading some the other day and they definitely save kernel panics.

just a sec...

yep 


  var/log/kern.log

and other logs also..

Okay I'll boot into SysRecCD and save the log when/if the kernel crashes again

> **effenberg0x0 said:**
> Well, I'm far from being a kernel hacker. I'm gonna throw some of the things I do and others can add more and correct me if I'm wrong.

The relevant thing is: Can you get the function name or the EIP address? If you can, just take note of it, no photo needed.

Then, to investigate:
First, you need an uncompressed image, which is not installed by default.
[http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/)
 
You also need to compile your kernel with debugging info, so add -g1, -g2 or -g3 to MAKE and build it. Of course you should take out optimizations (-O0) and don't strip anything, so you have some debugging info when the crash happens.

Given you have that, and you have a crash now with a call trace displaying. If you don't know what function crashed, all you have to do is get the EIP address and throw it in gdb. You need gdm compiled with kernel debugging support too (to support the -K option)

sudo gdb -k ../../vmlinux (from the uncompressed image)
(gdb) disas 0xfbfffc00 (disas is short for disassemble)
sata_do_something+0x26/0x41
... You'll have a lot of output here, but all you need is the function that was on stack at that time.

At this point things become easier, because you can cd to your kernel sources directory and grep this function to find out which source/object file has it. Let's say it's sata_example.c/sata_example.o.

gdb sata_example.o
list *(sata_do_something+0x26)

This will show you the exact source code lines of sata_example.c which produced the object code (of sata_example.o) that was on stack when this function crashed.

The thing is, when you are debugging a running kernel, you can't change variable values, overwrite memory addresses, watch a breakpoint anywhere, etc. 

The professional guys here use a much more complex and complicated method, in which you have a "dumb terminal" PC connected via serial cable to their PCs. When a crash occurs, they can investigate things thoroughly by using this external terminal.

I think this is an art in itself, very complex. Professional Kernel dbg people are not from this planet.

Oh boy this'll be fun. My laptop doesn't have a serial port so that's out. I'll try to compile an unoptimized kernel sometime today.

---

### Post by ventrical on 2011-11-24
Back in the old days of DOS we had a sharweware program called XRAY.  :)  It was not a kernel debugger but there was a lot of info there.

---

### Post by dino99 on 2011-11-24
kernel panic is often due to bios settings badly set and/or faulty ram stick (remove one to test or change voltage)

---

### Post by ventrical on 2011-11-24
> **Jordanwb said:**
> Okay I'll boot into SysRecCD and save the log when/if the kernel crashes again



Oh boy this'll be fun. My laptop doesn't have a serial port so that's out. I'll try to compile an unoptimized kernel sometime today.


Here is a link for maveric .. not sure if it will work with Precise...

[http://linux.slashdot.org/story/10/11/13/1351204/kernel-tracing-with-lttng-on-ubuntu-maverick](http://linux.slashdot.org/story/10/11/13/1351204/kernel-tracing-with-lttng-on-ubuntu-maverick)

 ok... I'm going to try this *[B]NOT*  :)

[/B]

---

### Post by MG&amp;TL on 2011-11-24
I think this should help for log file location: [https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")

---

### Post by Jordanwb on 2011-11-24
> **dino99 said:**
> kernel panic is often due to bios settings badly set and/or faulty ram stick (remove one to test or change voltage)

I don't think the problem is RAM since I didn't have this issue with the kernel originally installed with Pangolin (version 3.1) or on Oneric. Nevertheless I'm running memtest on it right now.

[Here's]("http://pastebin.com/JAmGEBch") the log if anyone is interested.

I've downloaded the source for linux-image-3.2.0-1-generic and I've edited the Makefile and changed the optimization and debug levels to 0 and 2.

Unrelated: I can't seem to get any sound through my headset. :???:

---

### Post by ventrical on 2011-11-24
I have the Acer Aspire 3620 and the Acer Extensa 4420(64bit). I am running Edubuntu (just the sweetest OS you ever saw) with the Precise 3.1 and will check on the Extensa as I installed Precise the other day but did not upgrade to 3.2 yet.

---

### Post by effenberg0x0 on 2011-11-24
> **Jordanwb said:**
> I don't think the problem is RAM since I didn't have this issue with the kernel originally installed with Pangolin (version 3.1) or on Oneric. Nevertheless I'm running memtest on it right now.

[Here's]("http://pastebin.com/JAmGEBch") the log if anyone is interested.

I've downloaded the source for linux-image-3.2.0-1-generic and I've edited the Makefile and changed the optimization and debug levels to 0 and 2.

Unrelated: I can't seem to get any sound through my headset. :???:

Is it snd.hda-intel module?

---

### Post by Jordanwb on 2011-11-24
> **ventrical said:**
> I have the Acer Aspire 3620 and the Acer Extensa 4420(64bit). I am running Edubuntu (just the sweetest OS you ever saw) with the Precise 3.1 and will check on the Extensa as I installed Precise the other day but did not upgrade to 3.2 yet.

Um okay. :confused:

> **effenberg0x0 said:**
> Is it snd.hda-intel module?

I think it's snd-usb-audio, my desktop's onboard sound chip is disabled (which used snd-hda-intel) because getting pulseaudio to work was a massive PITA on 11.04.

---

### Post by ventrical on 2011-11-24
> **Jordanwb said:**
> I don't think the problem is RAM since I didn't have this issue with the kernel originally installed with Pangolin (version 3.1) or on Oneric. Nevertheless I'm running memtest on it right now.

[Here's]("http://pastebin.com/JAmGEBch") the log if anyone is interested.

I've downloaded the source for linux-image-3.2.0-1-generic and I've edited the Makefile and changed the optimization and debug levels to 0 and 2.

Unrelated: I can't seem to get any sound through my headset. :???:


 I just loaded the 3.2 kernel on my Acer extensa 4420 (64bit) and here is what I got .. and she locked solid.

Funny thing . the error occured with the Broadcom driver .. ??

---

### Post by effenberg0x0 on 2011-11-24
> **Jordanwb said:**
> Um okay. :confused:



I think it's snd-usb-audio, my desktop's onboard sound chip is disabled (which used snd-hda-intel) because getting pulseaudio to work was a massive PITA on 11.04.

Can't help you then. For HDA Intel, one easy way of fixing thing is to use the daily build deb of alsa dkms. [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by ventrical on 2011-11-24
> **Jordanwb said:**
> Um okay. :confused:


.

Sorry if I confused you. I thought you were running an Acer Aspire with AMD processor and I thought that since I had near the same brand I could emulate the problem.

As you see in my recent post .. my system froze up while installing the 3.2.0-1.1 kernel.

Oy vey !

:)

---

### Post by Jordanwb on 2011-11-24
I've compiled the kernel with debugging and no optimization and have installed their deb packages. However comparing the my kernel is slightly smaller than the stock 3.2.0 available in the repos.

I can't connect to my router using the wifi chip when running the custom kernel.

```
[  958.179885] ath: Unable to set channel
[  958.239367] ath: Failed to stop TX DMA, queues=0x10f!
[  958.251079] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[  958.251081] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  958.359919] ath: Chip reset failed
[  958.359921] ath: Unable to reset channel, reset status -22
[  958.359930] ath: Unable to set channel
[  958.420446] ath: Failed to stop TX DMA, queues=0x10f!
[  958.432187] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[  958.432190] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  958.541433] ath: Chip reset failed
[  958.541435] ath: Unable to reset channel, reset status -22
[  958.541440] ath: Unable to set channel
[  958.601075] ath: Failed to stop TX DMA, queues=0x10f!
[  958.612804] ath: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
[  958.612807] ath: Could not stop RX, we could be confusing the DMA engine when we start RX up
[  958.721822] ath: Chip reset failed
[  958.721824] ath: Unable to reset channel (2412 MHz), reset status -22
```

> **effenberg0x0 said:**
> Can't help you then. For HDA Intel, one easy way of fixing thing is to use the daily build deb of alsa dkms. [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

My laptop uses snd-hda-intel, sound works I think


> **ventrical said:**
> Sorry if I confused you. I thought you were running an Acer Aspire with AMD processor and I thought that since I had near the same brand I could emulate the problem.

As you see in my recent post .. my system froze up while installing the 3.2.0-1.1 kernel.

Oy vey !

:)

My laptop's an Acer Aspire 5741, it's got an Intel CPU. We have the same brand laptop and probably same LAN chip but that's about it.

---

### Post by ventrical on 2011-11-24
> **Jordanwb said:**
> I've compiled the kernel with debugging and no optimization and have installed their deb packages. However comparing the my kernel is slightly smaller than the stock 3.2.0 available in the repos.



My laptop's an Acer Aspire 5741, it's got an Intel CPU. We have the same brand laptop and probably same LAN chip but that's about it.

 I had misread one of the lines of code in your log file.

---

