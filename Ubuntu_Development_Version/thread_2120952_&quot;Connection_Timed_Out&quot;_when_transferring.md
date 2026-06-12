---
title: "&quot;Connection Timed Out&quot; when transferring about 2GB+ of data over network?"
date: 2013-02-28
forum: Ubuntu Development Version
---

### Post by Roasted on 2013-02-28
I just installed 13.04 64 bit on my desktop and laptop using the 2/27 daily image. I have Ubuntu Server 12.04.2 running on my server here. On both my laptop and desktop, I tried to copy a folder several GB in size over to my server. I tried to copy this file through Samba in Nautilus as well as with rsync over SSH. In both instances, it locked up right around the 2.0 to 2.3 GB area. Each system lost connection at this point, forcing a reboot. In one case with my laptop, I left it sit for about 10 minutes and came back to it. At this time pings were working again.

Any of you guys out there available to give this a shot? All I did was try to copy something over 2.3 GB in size to my server. Like I said, Samba and Rsync both exhibited the same behavior, along with wired desktop vs wireless laptop.


EDIT - dmesg output from desktop when the problem hit. I was spamming dmesg over and over. Once the issue turned up is when the DMA lines appeared:

```
[    3.918858] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[    3.918944] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[    3.919017] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    3.919073] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    3.947169] init: udev-fallback-graphics main process (946) terminated with status 1
[    4.968540] init: failsafe main process (987) killed by TERM signal
[    4.981107] Bluetooth: Core ver 2.16
[    4.981129] NET: Registered protocol family 31
[    4.981130] Bluetooth: HCI device and connection manager initialized
[    4.981184] Bluetooth: HCI socket layer initialized
[    4.981187] Bluetooth: L2CAP socket layer initialized
[    4.981192] Bluetooth: SCO socket layer initialized
[    4.986657] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.986661] Bluetooth: BNEP filters: protocol multicast
[    4.986668] Bluetooth: BNEP socket layer initialized
[    4.987832] Bluetooth: RFCOMM TTY layer initialized
[    4.987843] Bluetooth: RFCOMM socket layer initialized
[    4.987844] Bluetooth: RFCOMM ver 1.11
[    4.999846] type=1400 audit(1362030386.924:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1079 comm="apparmor_parser"
[    5.000839] type=1400 audit(1362030386.924:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1079 comm="apparmor_parser"
[    5.017141] type=1400 audit(1362030386.940:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1110 comm="apparmor_parser"
[    5.017152] type=1400 audit(1362030386.940:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1111 comm="apparmor_parser"
[    5.017347] type=1400 audit(1362030386.940:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1112 comm="apparmor_parser"
[    5.017399] type=1400 audit(1362030386.940:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1111 comm="apparmor_parser"
[    5.036613] atl1c 0000:05:00.0: irq 54 for MSI/MSI-X
[    5.037121] atl1c 0000:05:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[    9.898041] input: Logitech Unifying Device. Wireless PID:1024 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/input/input11
[    9.898799] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1024] on usb-0000:00:1d.0-1.6:1
[    9.900091] input: Logitech Unifying Device. Wireless PID:2011 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/input/input12
[    9.900212] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2011] on usb-0000:00:1d.0-1.6:2
[ 1022.072341] DMA: Out of SW-IOMMU space for 30968 bytes at device 0000:05:00.0
[ 1022.076694] DMA: Out of SW-IOMMU space for 30968 bytes at device 0000:05:00.0
[ 1022.080899] DMA: Out of SW-IOMMU space for 13592 bytes at device 0000:05:00.0
[ 1022.536781] DMA: Out of SW-IOMMU space for 7240 bytes at device 0000:05:00.0
[ 1022.783313] DMA: Out of SW-IOMMU space for 7240 bytes at device 0000:05:00.0
[ 1023.031361] DMA: Out of SW-IOMMU space for 7240 bytes at device 0000:05:00.0
[ 1023.280154] DMA: Out of SW-IOMMU space for 7240 bytes at device 0000:05:00.0
[ 1023.526582] DMA: Out of SW-IOMMU space for 6680 bytes at device 0000:05:00.0
[ 1023.776287] DMA: Out of SW-IOMMU space for 7240 bytes at device 0000:05:00.0
[ 1024.023317] DMA: Out of SW-IOMMU space for 6352 bytes at device 0000:05:00.0
[ 1024.267164] DMA: Out of SW-IOMMU space for 5792 bytes at device 0000:05:00.0
[ 1024.475257] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1024.684636] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1024.926598] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1025.135775] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1025.339428] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1025.543224] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1025.747944] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1025.990350] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1026.201231] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1026.405181] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
[ 1026.646002] DMA: Out of SW-IOMMU space for 1522 bytes at device 0000:05:00.0
[ 1026.648540] DMA: Out of SW-IOMMU space for 4344 bytes at device 0000:05:00.0
```



EDIT - For what it's worth, I just used my same problematic 13.04 laptop to push 40GB of data to a 12.04 system I have here via Samba/Nautilus. No issues at all. I wonder why on earth I ran in to any issues last night then with my laptop AND desktop pushing data to my server...

EDIT II - Some additional reading has suggested this is a kernel issue of some sort. I read about several bugs and also bumped up a recent one (actually it was posted in 2009, but continually bumped up over the years.... nice.....). Hopefully we'll see a fix soon.

---

### Post by Roasted on 2013-03-01
Nobody is seeing this? Granted, I've only been able to duplicate it at home versus an Ubuntu Server 12.04.2 box, but I tried a 5GB Samba push to a 12.04 desktop machine in a different environment without issue.

Currently I'm pushing an 8GB ISO to my server via my problematic laptop, but this time on my 12.04 partition. 90% done, no issues, whereas on 13.04... 2GB and it tanks. :(

---

### Post by papibe on 2013-03-02
Hi Roasted.

This kernel [bug]("https://bugzilla.kernel.org/show_bug.cgi?id=9468") says you can get around the problem by disabling IOMMU.

It looks like you can do that by adding a grub option: "intel_iommu=off" (reference [here]("http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk")).

I hope you can solve your problem. Let us know how it goes.
Regards.

---

### Post by fdrake on 2013-03-02
check your quotas:
```
smbcquotas -v -L  //server1/share1

```

---

### Post by Roasted on 2013-03-02
> **papibe said:**
> Hi Roasted.

This kernel [bug]("https://bugzilla.kernel.org/show_bug.cgi?id=9468") says you can get around the problem by disabling IOMMU.

It looks like you can do that by adding a grub option: "intel_iommu=off" (reference [here]("http://www.phoronix.com/scan.php?page=news_item&px=MTAzNzk")).

I hope you can solve your problem. Let us know how it goes.
Regards.

Sounds good. I appreciate the link. What I'm more interested in is learning a bit more as to what exactly the system is doing. Do you have any idea as to what is happening that the system drops off like that, causing those dmesg errors?

I also find it a little disheartening that this bug report was from the 2.6 days, supposedly fixed, and I'm seeing it now in whatever kernel I'm using in 13.04 (I think 3.7). I've bumped up a couple other Ubuntu-specific bugs that I found regarding this issue in hopes of it getting a re-visit, but so far have heard nothing else about it. If I don't hear anything it soon it may be time to put in a new bug report. A lot of people were swearing by 13.04's stability, but if I can't even push 2GB to my server, this is flat out unusable the way it currently stands. But hey, it's a beta - I get that. ;)

Is nobody else out there with 13.04 seeing this?

---

### Post by cwsnyder on 2013-03-02
Current Raring Ringtail is kernel 3.8.0-7, upgraded today from 3.7.0-7.  I had seen this reported in Mint 14 and Ubuntu 12.10 using Caja and Nautilus.  Yours is the first report of problems using command line utilities that I have seen, also the first report of Raring Ringtail having a problem, although I don't get on the forums every day.

---

### Post by cariboo on 2013-03-02
[COLOR=#000000]&#8203;@Roasted, do you see the same thing using sftp, or is that the same as using rsync+ssh?[/COLOR]**[COLOR=#000000] [/COLOR]**[COLOR=#000000][/COLOR]

---

### Post by Roasted on 2013-03-02
I can't answer that with certainty, but I do believe sftp is the same as rsync/ssh. Today I upgraded my laptop as much as I could, which took it from kernel 3.8.0-7 to 3.8.0-9. I don't know what differences exist but I upgraded and tested again. What's funny is, on -9 my laptop worked fine to push 8GB. So I booted to -7 and did the same thing, and it worked too... but I expected it to fail since it failed the other day...

On the flip side, I did the same thing to my desktop. I hopped on 3.8.0-9 and pushed 8GB of data, both by rsync/ssh and Samba in Nautilus. Both failed with the error again. Arg....

EDIT - I got this email notification this morning. The user (I assume a developer) dhewg responded with:

> 
Fixed upstream with:

commit 7cb08d7f3a5ea6131f4f243c2080530ac41cb293
atl1c: restore buffer state

Queued for stable, but doesn't look like it made it for 3.8.2.
Please include said patch


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132477](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132477)

If I recall, atl1c is a driver. I wonder if this issue resides with specific network drivers?

Also, speaking of the fact it didn't make it for 3.8.2, that makes me wonder - what kernel is 13.04 supposed to ship with?

---

### Post by lorenzfx on 2013-03-03
I'm having the same problem, running Linux 3.8.0-9-generic
I see the same problem while copying via scp or nfs but haven't tried disabling IOMMU yet.

---

### Post by Roasted on 2013-03-03
> **fdrake said:**
> check your quotas:
```
smbcquotas -v -L  //server1/share1

```

I apologize - I didn't see your post earlier. In regard to quotas, I have no quotas. This is my own file server on my LAN.

> **lorenzfx said:**
> I'm having the same problem, running Linux 3.8.0-9-generic
I see the same problem while copying via scp or nfs but haven't tried disabling IOMMU yet.

I have not tried disabling IOMMU either. I do have to ask, what *exactly* is IOMMU? I haven't heard of it until this issue, but I'm still not entirely sure I understand what it is. I also upgraded to 3.8.0-9 and still saw the problem.

---

### Post by lorenzfx on 2013-03-03
what system information could be helpful to debug this problem?

---

### Post by ArchangeGabriel on 2013-03-08
Nothing, it is already fixed upstream as said before. You just have to wait for kernel 3.8.3 or 3.9, you may also add iommu=off to your boot options as a workaround while waiting for those new kernel. Current Raring kernel is 3.8.0-11 based on upstream 3.8.2. 3.8.3 should be released this WE, and will hit Raring this week normally.

---

