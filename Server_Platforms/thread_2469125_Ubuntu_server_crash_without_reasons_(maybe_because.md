---
title: "Ubuntu server crash without reasons (maybe because of docker)"
date: 2021-11-20
forum: Server Platforms
---

### Post by matlam1001 on 2021-11-20
Hi, I have a Raspberry Pi 3B+ with Ubuntu server that has always worked fine, until about a month ago.
In fact this one has the cpu running at max and after a minute it stops responding to any command. In the connected monitor I have this message:
```
INFO: task worker/0:4:5680 blocked for more than 241 seconds.
Tainted: G C E 5.11.0-1021-raspi #22-Ubuntu
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disable this message.
```

While if I use HTop to monitor the event I see that the cpu is at 100% due to:
PID      USER    NI    VIRT     RES     SHR     S    CPU%    MEM%    TIME+   Command
11849  root       0     969M    491M   1900   S     393.      54.2       1:04.21 zstd -q -19 -T0 -c /var/tmp/mkinittramfs-MAIN_C3VkKM

Here you can see a complete image:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289501&stc=1[/IMG]

I've also tried with a new installation, but it's the same. This happens when docker is working with some container (run or create, only pull doesn't create problems) or sometimes with apt.
Hope you can help, thanks in advance!

---

### Post by MAFoElffen on 2021-11-21
Please run the script in my Signature line... From: 
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

Mostly wondering if, while your cpu is being pegged, what your swappaging and mem stats are... and the size of your swap.

---

### Post by matlam1001 on 2021-11-21
I tried to download the script, but I need to download some packages in order to run it and if I use apt the server hangs.
I'm basically blocked because apt cannot finish any installation.

But by using "top" in the raspberry terminal I can see this:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289507&stc=1[/IMG]

I see that the swap is not working for some reason :(.
Is there any solution to this? I've never ecountered this problem before...
I found some workaround, but if possible I want to solve this, thanks.

---

### Post by Tadaen_Sylvermane on 2021-11-21
almost pegging the ram. I'm also curious how you are on partition space. a full partition will crash out.

Just keep in mind. You can do a lot with the RPi's. But they are not full server machines. Limited ram and storage issues are an issue. I'm not sure what you are doing with docker but if you are running more than a couple containers it's probably just to much.

---

### Post by ameinild on 2021-11-22
It seems zstd is a compression tool related to the compression of initramfs (now the default method in newer releases).  My guess is this happens when you install an updated kernel, and initramfs is generated.

Check which compression is used with the following command:

    ```
cat /etc/initramfs-tools/initramfs.conf | grep COMPRESS
```

Which version of Ubuntu Server are you using? I'm assuming 20.04, but if you upgraded to Impish, then that's probably the cause.

If you're on 20.04: Have you tried with kernel 5.4, which AFAIK does not support zstd, but uses an "older" compression method? Or change the compression method to lz4 (the default in kernel 5.4). Maybe the newer zstd compression kills the Pi for some reason.

And does this change maybe relate to the time where you upgraded system or kernel?

Or maybe you should consider upgrading to a Pi 4. 1 GB of memory is really  pushing it when you want to run containers, and swap isn't enabled on  the Pi by default (because it usually lacks a fast disk device).

EDIT: Related bug reports, confirming that at some point, zstd became the default, and that it uses excessive memory upon initramfs generation.

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1931725](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1931725) 
[*][https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1944082](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1944082) 
[/LIST]

---

### Post by MAFoElffen on 2021-11-23
May be a bit Off-topic ... But in Post #3 you said you were missing some packages to run that script... Since I am the author and maintainer of that UbuntForums 'system-info' script, I need to know what packages prevented you from running that script, so I know if that script needs to be modified/changed in any way... (I wrote it for Server and Desktop Editions, and all flavors of Ubuntu.)

Please help me with that, as it needs to be able help everyone here... It should be a universal tool, and I need feedback/input to keep it that way.

---

### Post by ameinild on 2021-11-24
> **MAFoElffen said:**
> Since I am the author and maintainer of that UbuntForums 'system-info' script, I need to know what packages prevented you from running that script,

I just tried this (good script btw), and I was missing the packages `ubuntu-drivers` and `pastebinit`. However, I could run the script anyway with no issue (on a server).

---

### Post by matlam1001 on 2021-11-24
Hi thanks for the help!
The missing packages are the same as written in the top post I think, because I forgot to write them down.
I solved the problem by creating a swap partition, because as you can see, it was 0.
I tried first disabling swap, and it worked (you can imagine how bad it was working...) and then I created a swap partition in the sd card of the Raspberry.
I also tried splitting the swap between the sd and the usb hard drive I use for various data and that worked very well!
I don't think the swap is evenly split between the two drives, but BTW it worked.


Thanks!

---

### Post by ameinild on 2021-11-25
I would advice against putting the swap partition or file on the SD card - this may lead to your SD card being worn out early. I would isolate swap to an external HDD.

---

### Post by MAFoElffen on 2021-11-26
Even more reason not to use an SD card as Swap is that the read/write speeads of SD cards are "sooo slow"! If I create Swap and have the choice of creating on HHD SSD or NVMe, I'll do it on whatever is the fastest. Imagine that on NVMe is as fast as if you had an Intel Optane Cache...

> **ameinild said:**
> I just tried this (good script btw), and I was  missing the packages `ubuntu-drivers` and `pastebinit`. However, I could  run the script anyway with no issue (on a server).

Yes. Part of the test team tested on Server Editions to ensure it worked okay and was going to be a diagnostics tool for Server Edition,  as well as all flavors of Desktop. Besides, my Ama-Gi Project's Ubuntu Support LiveCD is based on Server Edition. It would be odd and a problem for us if it didn't work somehow.

For the LiveCD, we have more control of what is installed and present for it (less User based variables and combinations... LOL) For instance, having 'fbset' installed to check the screen information of Console and VTTY's... I have that installed there, and in that version of the script,  but is not in the forum's version, because it is not a default app in any version of Ubuntu. But is info that is nice to know for diagnostics.

---

