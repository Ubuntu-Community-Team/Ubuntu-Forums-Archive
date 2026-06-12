---
title: "qemu on 14.04 unusuably slow, kswapd0 may be the culprit"
date: 2015-08-16
forum: Virtualisation
---

### Post by Lars Noodén on 2015-08-16
When I try to run qemu on Ubuntu 14.04, it slows down to the point of it and the whole system being unusably slow and hesitant.  Even the consoles turn sluggish while qemu is running.  The only major difference I can spot between when qemu is running and when it is not is that kswapd0 seems to be using between 50% to 100% of the CPU when things are sluggish.  Killing qemu makes kswapd0 disappear from top.  I used to be able to use qemu on this system.  What needs to change so that I can use it again?

I start qemu like this:

```

qemu-system-i386 -enable-kvm -m 2048 -hda qemu.img -net nic -net user,hostfwd=tcp::7777-:22 -cdrom /home/lars/Downloads/ubuntu-14.04.2-server-i386.iso -boot d

```

And it makes the machine unusably sluggish whether I boot from the DVD image, any image I have in stock, or from a pre-existing VM.

---

### Post by TheFu on 2015-08-16
Hi Lars!

So what are the specs of this system (CPU/RAM/type of HDD)?  Is VT-x enabled?  

All my KVM VMs are setup and run using libvirt and I don't see these slowdowns.  I suspect it is the default disk driver being use. Virtio needs to be specified.  Same for networking.  It this VM host really not a 64-bit system?

---

### Post by Lars Noodén on 2015-08-16
Thanks.  I used 32-bit in the example, but the problem is there even with 64-bit.  The VM image is qcow2

```

qemu-img create -f qcow2 qemu.img 7G

```

The host has 8GB or RAM (7.7 GiB) plus some swap.  The CPU is an Intel Core i7-4810MQ CPU @ 2.80GHz × 8.  The drive is a RAID1 with two devices each of which is a different brand/model of SSD.  

What is VT-x in this context?

---

### Post by TheFu on 2015-08-16
VT-x is a BIOS setting that enables CPU HW support for virtualization.  KVM requires it, so it is 99% enabled. In theory, if it wasn't enabled, the VM wouldn't run.

Are you willing to use libvirt, virsh and virt-manager to try a different method?  The args for libvirt created systems are long ... but well tested and perform well.

BTW - even if I have a 32-bit OS running, I use qemu-system-x86_64. It supports newer, faster emulated HW and moved bits in larger chunks just like a 64-bit processor does when compared to a 32-bit CPU.

---

### Post by Lars Noodén on 2015-08-16
I can try the method(s) you suggest.  

I tried the 64-bit again, running the 32-bit DVD image, and it just locked up faster.  

I noticed this in the syslog, when I was able to kill it:

Aug 16 15:49:14 gazp9 kernel: [106902.766779] Out of memory: Kill process 957 (qemu-system-x86) score 473 or sacrifice child
Aug 16 15:49:14 gazp9 kernel: [106902.766802] Killed process 957 (qemu-system-x86) total-vm:5493392kB, anon-rss:3818244kB, file-rss:3824kB
Aug 16 15:49:14 gazp9 kernel: [106902.767330] Purging GPU memory, 0 bytes freed, 684032 bytes still pinned.

It's just a bit strange because I used to run qemu just fine.

---

### Post by TheFu on 2015-08-16
I tested with
```
# qemu-system-i386 -enable-kvm -m 2048 -net nic -net user,hostfwd=tcp::7777-:22 -cdrom ./ubuntu-14.04-server-amd64.iso  -boot d
```

and it seemed fast - really fast.  No HDD connected, as you see. Didn't let it go too far in the installation process. Could there be some HW error?  Log files have any warnings/errors?

Also - is the machine busy with other things? Is the RAM over-committed?

---

### Post by Lars Noodén on 2015-08-16
The machine's not under much load and has a lot of free RAM.  qemu does seem to bother the CPU, too.

```

top - 17:13:08 up 2 days, 21:16,  5 users,  load average: 1.41, 0.78, 1.07
Tasks: 439 total,   2 running, 437 sleeping,   0 stopped,   0 zombie
%Cpu(s): 16.8 us,  2.6 sy,  0.0 ni, 80.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8094860 total,  4558568 used,  3536292 free,    35944 buffers
KiB Swap:        0 total,        0 used,        0 free.  1364624 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2206 lars      20   0 2532132  39220  18360 S 100.4  0.5   1:01.24 qemu-syste+

```

---

### Post by Skaperen on 2015-08-19
it could be I/O. kswapd is involved there, too.

what i have done is make a tmpfs (my swap is disabled) and put the ISO and HD images there.  then run qemu on the ones in RAM.  I timed a full install of Slackware and it took a minute and 3 seconds.  the host was 12G and the guest was 5G. everything was done in RAM so that is where the speed came from. maybe RAMFS would work.   a lot of your swap slowness could be the writing of other stuff out to make way for what is active.

can you get more RAM?  i am up to 16G now and have a new box with 64G i am getting ready to be my new server.

when RAM is overused and nothing is available to be swapped out then the kernel (maybe kswapd) uses a lot of CPU (maybe because nothing else can at that point) looking around for something to swap out.

---

