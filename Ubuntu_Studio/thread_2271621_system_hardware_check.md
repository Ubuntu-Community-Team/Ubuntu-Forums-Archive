---
title: "system hardware check ?"
date: 2015-03-31
forum: Ubuntu Studio
---

### Post by John_Kirk on 2015-03-31
Hi...

After a upgrade to a new hard drive and a bigger monitor im experiencing a sluggish performance.

What do I type into a terminal to findout the specs of my hardware ?
I am considering a dedicated graphics card and possibly more memory/better memory

but, I dont have any info on my hardware. I am presuming it would be obtained via terminal commands in Studio Ubuntu
I was hopeing to get some help about what my best options are on this forum after finding out what I have..

thanks

---

### Post by SeijiSensei on 2015-03-31
The command "sudo lshw" will tell you more than you would ever possibly want to know about your hardware.  If you run
```
sudo lshw > hardware.txt
```
it will put the output into the hardware.txt file where you can browse it more easily.

However I find it unlikely that either a new hard drive or monitor would noticeably affect performance.  Open a terminal window and run the "top" command.  Leave it open while you do other tasks and watch the system's CPU and memory usage.  Maybe a particular application is responsible for the slowdowns.

Usually the most effective solution for performance issues is adding more memory.

---

### Post by v3.xx on 2015-03-31
A couple of shortcuts.
Video
```
sudo lshw -c display
```
Ram
```
free -m
```

---

### Post by John_Kirk on 2015-03-31
*-display               
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:fa000000-faffffff memory:e0000000-efffffff memory:f9000000-f9ffffff memory:fbec0000-fbedffff


             total       used       free     shared    buffers     cached
Mem:          1749       1588        160          7          3         75
-/+ buffers/cache:       1509        239
Swap:         1787        463       1324

---

### Post by SeijiSensei on 2015-03-31
Did you run the "Additional Drivers" application to install the proprietary NVIDIA driver?  You can also install it from the command prompt with "sudo apt-get install nvidia-current".

It may not help with video though, as I believe it is [too old to benefit]("http://us.download.nvidia.com/XFree86/Linux-x86/190.32/README/appendix-a.html") from the "VDPAU" features that off-load video decoding to the graphics chip.

Adding another 2GB of memory if possible would likely help, too.

---

### Post by v3.xx on 2015-03-31
> -/+ buffers/cache: 1509 [COLOR=#ff0000]239[/COLOR]
Swap: 1787 463 1324
239M is all you have left out of two gig and that sends you to the dead slow swap.
Like Seiji said, find out whats using high ram.  Maybe xorg, maybe chrome.

You can look in the 'System Monitor', under Processes, click on memory.

---

### Post by John_Kirk on 2015-04-01
I have 2 memory strips inserted...

Can I find out by a terminal command what the motherboard can support ?

Additionaly, im using the mothorboard graphics and my new monitor resolution is quite big.

---

### Post by v3.xx on 2015-04-01
> Can I find out by a terminal command what the motherboard can support ?
I do not such a command, but you can find out which MB you have and check with the manufacture.

[http://ubuntuforums.org/showthread.php?t=1933736](http://ubuntuforums.org/showthread.php?t=1933736)

---

### Post by SeijiSensei on 2015-04-02
> **John_Kirk said:**
> I have 2 memory strips inserted...

Can I find out by a terminal command what the motherboard can support ?

Additionaly, im using the mothorboard graphics and my new monitor resolution is quite big.

The "memory" section of lshw will tell you what memory sticks you have installed:
```

     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CT51264BF1339.D16F
             physical id: 0
             serial: 00000000
             slot: Bottom - Slot 1 (top)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 812D7BCC
             slot: Bottom - Slot 2 (under)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)

```

However it won't tell you what the maximum memory could be.  For that, look to your manufacturer's specifications page for your computer.

---

### Post by Bashing-om on 2015-04-02
Hello ;

> **John_Kirk said:**
> I have 2 memory strips inserted...

Can I find out by a terminal command what the motherboard can support ?

Additionaly, im using the mothorboard graphics and my new monitor resolution is quite big.

'dmidecode' contains a wealth of information ..
Try:
```

sudo dmidecode | grep Memory

```
(that is a uppercase 'm' in "Memory")

[INDENT][INDENT]all in knowing how to ask the system
[/INDENT][/INDENT]

---

