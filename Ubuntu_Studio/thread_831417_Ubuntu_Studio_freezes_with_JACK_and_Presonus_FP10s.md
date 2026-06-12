---
title: "Ubuntu Studio freezes with JACK and Presonus FP10s"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by SamFrew on 2008-06-16
Hi all,

I am trying to record 24 audio channels using three daisy-chained Presonus FP10s and Ardour 2.4.1 running in Ubuntu Studio 8.04 with the real-time kernel. 

I have a continuing issue with the setup, whereby the entire system will freeze and I will have to do a hard restart, because even the keyboard does not respond. This freeze always occurs after JACK has started and the lights on the FP10s are blue, but the time between starting JACK and the freeze occurring is unpredictable - sometimes a few seconds, sometimes 15 minutes or more. I can often start Ardour and record a few minutes of audio before it freezes, but in the end the freeze always happens. Nothing is displayed in the Messages of JACK before the freeze.

I have tried many things to fix the problem:
- using only one FP10
- a different FireWire chipset (using a Cardbus to FireWire card)
- almost every combination of JACK settings
- increasing the locked memory for real-time process

Most recently I have been using JACK as:
jackd -R -P88 -t2000 -dfreebob -r48000 -p256 -n3 -D

The FP10s all have the latest firmware (v 2.46).

The laptop is a Dell Latitude D630 with 2GHz Intel Core 2 Duo processors and 2GB RAM.

Does anyone have any ideas on how to fix this problem or has anyone come across it themselves?

Anything is appreciated at this stage.

Thanks,
Sam

---

### Post by Stochastic on 2008-06-17
Try adding nohz=off to your grub's menu.lst file; do sudo nano /boot/grub/menu.lst then change your default entry to read something like: ```
title           Ubuntu 8.04, kernel 2.6.24-16-rt
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-rt ro quiet splash nohz=off
initrd          /boot/initrd.img-2.6.24-16-rt
quiet
```
If that doesn't fix it, try with a different firewire cord (not all are created equal).  If that still doesn't fix this, then you might want to consider compiling FFADO as they're in beta testing stage and are claiming to have similar functionality to freebob.  Lastly, you might want to do a dual-boot into 64Studio to check if there's still issues there (could point to a hardware problem if that's the case).

---

### Post by SamFrew on 2008-06-25
Thanks for your advice Stochastic. I tried adding nohz=off, a new firewire cable and the latest FFADO driver, but none fixed the problem - the laptop always freezes.

I decided to hold off installing 64Studio for now and work in Windows XP, where everything works without freezing, while I wait for any other ideas people may have.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Here are few ideas:

a)"sudo swapon -s" if there is something more or less then one swap partition, then fix it, as it gives freezing issues.

b)edit /etc/gamin/gaminrc and put there "fsset nfs poll 10" "fsset ext3 poll 10" "fsset vfat poll 10". Gamin server is a program that reads frequently hard drive for new changes and in some situations it may cause freezes.

c) run memtest+ over night. it is one of the ubuntu boot options. If you have some errors, then remove all your memory chips and put one and check it over night with memtest+ and next night add next memory chip and check it. If some night you get errors, then you know which memory is giving your problems with freezes.

d)try running your apps with computer offline. Totally offline like there must be no network connection what so ever. If you don't get freezes, then it is this hackie network.manager related issue. It is solvable.
[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)

I certainly fixed my freezes by removing network-manager. For entire month I was under suggestion that my graphic card's driver was at error. Not any more.

---

### Post by nalmeth on 2008-06-26
I've only chained 2 firepods together before, and I can't say for sure what is causing your hard freezes. 
However, if it happens again, use this trick to restart your computer - its safer than just hitting the restart button.

Hold Alt and PrintScreen - then type these keys in succession: R E I S U B
(BUSIER backwards)

Each key performs a different action - getting the keyboard back, unmounting devices, etc.
It's still not good for your system, but better than a hard reset.

Anyway, good luck solving your problem

Edit: Anyone know if there is a log file that jack can dump to? Perhaps the jack-debug version does this, its probably worth looking into. It might spit out some messages that will indicate what is going on.

---

### Post by SamFrew on 2008-07-29
Thanks for all your help.

Odrodzona-Sarmacja, I tried all your suggestions a) - d), but with no success. The laptop still freezes.

Also, nameth, your suggestion for a softer reset didn't work for me and I still have to hold down the power button.

My next step is to try a different laptop.

Sam

---

### Post by SamFrew on 2008-08-05
I tried another laptop (ASUS W6F - 2.3GHz, 512MB) running under Kubuntu Hardy and no longer have any system freezes. I really have no idea why it works when the Dell does not. The ASUS uses a RICOH chipset, which is apparently worse than either of the ones I tried on the Dell.

However, I am still having some troubles with the new setup. I can get the three FP10s connected at the same time (all lights blue), but for capture only, not playback. Sometimes only two FP10s will connect, in which case the one closest in the daisy chain to the laptop will does connect. The two that do connect are able to capture and playback.

Generally, I will see a message as jackd starts along the lines of:

[INDENT]showDevice: not implemented
Error (configrom.cpp)[84] initialize: Could not parse config rom of node 2 on port 0showDevice: not implemented
[/INDENT]
This can appear in either scenario: three FP10s connected with no playback or two FP10s connected with playback.

Any ideas what may be causing this?

Thanks.

---

### Post by bbkz on 2008-08-16
i have a similar or the same with the "freeze" problem with my desktop pc i whould like to refer to my post:

[http://ubuntuforums.org/showthread.php?t=891505](http://ubuntuforums.org/showthread.php?t=891505)

as i think here was a workaround done. hope mine will not be a workaround.

---

### Post by ussndmac on 2009-02-11
> **SamFrew said:**
> Hi all,

I am trying to record 24 audio channels using three daisy-chained Presonus FP10s and Ardour 2.4.1 running in Ubuntu Studio 8.04 with the real-time kernel. 
<snip>


I was wondering what your latest experience is with multiple FP10's?

Regards,
Mac

---

### Post by carlotheman on 2009-05-31
This is actually not an UbuntuStudio specific issue, but affects at least the generic i386 and probably all kernels.

Installing the custom mesa package in this post worked for me. I have an ATI Radeon 200M card.

Carlo

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049/comments/21](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049/comments/21)

---

### Post by carlotheman on 2009-05-31
Correction: The mentioned package actually did *not* work for me. It's still an Ubuntu issue though, not an UbuntuStudio issue.

---

### Post by kayosiii on 2009-06-01
Have you posted this on the ffado mailing list???? You should be able to find people who can give you deeper insight there.

---

### Post by carlotheman on 2009-06-06
I was able to resolve the freezes, as well as improve my real time performance, by installing the latest [64studio kernel]("http://ubuntuforums.org/showpost.php?p=7380975&postcount=26"), as described in the original post.

---

### Post by kayosiii on 2009-06-07
For running multiple FP10's it might be worth posting on the ffado mailing list.

---

