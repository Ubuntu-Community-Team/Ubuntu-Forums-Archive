---
title: "Serp4: Hibernate and built-in Mic"
date: 2008-04-09
forum: System76 Support
---

### Post by farruinn on 2008-04-09
Hi,

I've been enjoying my new Serval for a couple months now with the only problems being hibernate and the built-in mic. Are these supposed to work with the System76 driver. If not, does anyone know of other solutions?

Thanks

---

### Post by Gonzell on 2008-04-09
I have a Pangolin and I've been pretty ticked with the Mic quality as well. I've yet to find a solution and Sys76 hasn't provided much help to me in this area besides that they are hoping it might be better in Hardy. I'm currently running the Hardy Beta and the Mic is still horrible (I actually can't even get it to work in Skype since I upgraded). Also, only one program can use my audio device at a time now...that's pretty frustrating as well. I'm not going to be throwing any punches yet though because it is a beta after all. But I'm really hoping these problems will be resolved when Hardy is released.

I also can't Hibernate nor Suspend now. My webcam also runs very slowly in Cheese (but not Skype...). Once again...I am running a beta.

---

### Post by farruinn on 2008-04-09
Ah, well my problem is that the Mic doesn't appear to work at all. With gnome-sound-recorder I've tried every input selection available (front mic boost, mic boost, capture, and digital). The webcam works nicely though.

EDIT: I've also checked the volume control, and everything is enabled and at least 100%

Most important to me is the hibernate. I would really like the ability to hibernate the machine when I'm not using it to reduce battery use while in suspend.

---

### Post by Gonzell on 2008-04-10
Hmm...you might try not putting "Capture" on 100%....I think when I was playing around trying to get better quality on my Mic (unsuccessfully) I would not work at all when I had Capture turn up all the way.....I'm not sure if this is true....memory might just be serving me wrong. Anyway...my suggestion is to just try turning some of your Mic settings a little below 100% and hopefully you hear some progress. :)

---

### Post by thomasaaron on 2008-04-10
gonzell,

Try setting up your Sound Controls, Sound Preferences, and Sound Recorder like these screenshots.

That should get the internal mic working, although the quality will be iffy until ALSA improves.



As for hibernating:
1. Are you having trouble with suspend or hibernate? They are two different things, and you mention both of them.
2. What happens when you try to resume from it?
3. Are you running 32-bit or 64-bit Ubuntu?

---

### Post by Gonzell on 2008-04-10
farruinn is the one with the Mic issue ^_^ (aside from the quality issue...that was mine).

Is it possible that you guys will improve ALSA to fix the quality?

When I try to Hibernate. It goes to the terminal and freezes on a login prompt (if I remember correctly).

Suspend works...It goes to sleep and wakes up. However, my sound does not work at all after a resume and many applications left open crash...such as Pidgin.

I am running 64 Bit and I am using a Pangolin.

---

### Post by thomasaaron on 2008-04-10
OK. We'll be looking at both of those issues on Hardy.

So, Farruinn, please have a look at the configs in my previous post.

---

### Post by farruinn on 2008-04-10
Thomas: Hi, the sound works - I didn't realize there were additional tabs in the sound control program.

Suspend works perfectly, the only problem is with hibernate: when I attempt to send it into hibernate the screen goes black and the hard drive makes some disturbingly loud noises until I get too worried about it and power it down.

This is 64-bit Ubuntu Gutsy, the default configuration.

---

### Post by thomasaaron on 2008-04-11
OK, good job on the sound.

Ummmm, it's not a good idea to power down your computer while the hard drive is working. That's a sure way to irrevocably hose your filesystem.

Try letting hibernate run its course. Does it ever power all the way down? Once it is powered all the way down, press the power button to make it resume. What happens?

BTW: I'm not exactly sure what you mean regarding the sounds your hard drive is making, but when you hibernate, data pertaining to all open programs is being written to your hard drive. If you really think the sound is abnormal, I'd advise you to be keeping good backups. That way, if your drive does go belly up, we can replace it, and you won't loose all your data.

---

### Post by farruinn on 2008-04-11
> **thomasaaron said:**
> Ummmm, it's not a good idea to power down your computer while the hard drive is working. That's a sure way to irrevocably hose your filesystem.

I'm aware of the possible corruption, but I would prefer a hosed filesystem to a dead hard drive. I'll test it later on though and let it go. The longest I've let it go was about 30 seconds I think.

---

### Post by farruinn on 2008-04-12
Tried hibernate again and it appears that as soon as the machine goes into hibernate is resumes. I've attached the dmesg output, this is on battery with the wireless switch set to off.

---

### Post by farruinn on 2008-04-12
New discovery: apparently attempting to hibernate from an earlier time disabled my swap, so in the preceding dmesg log I had no swap. I had to open parted and format /dev/sda6 as swap. I then tried to hibernate (left wireless switch on) and it made that sound I don't like for a little bit then powered off. I thought all was well, but when I hit the power button again it rebooted the computer and again I didn't have any swap. Below is a portion of /var/log/syslog from the event:

```
Apr 12 02:03:43 ubuntu gnome-power-manager: (nathan) GNOME interactive logout because the power button has been pressed
Apr 12 02:03:47 ubuntu dhcdbd: Unrequested down ?:3
Apr 12 02:03:47 ubuntu NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Apr 12 02:03:48 ubuntu avahi-daemon[5872]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 12 02:03:48 ubuntu avahi-daemon[5872]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.151.
Apr 12 02:03:48 ubuntu avahi-daemon[5872]: Withdrawing address record for fe80::21d:e0ff:fe73:89f9 on wlan0.
Apr 12 02:03:48 ubuntu avahi-daemon[5872]: Withdrawing address record for 192.168.0.151 on wlan0.
Apr 12 02:03:48 ubuntu NetworkManager: <debug> [1207980228.587543] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_38_cc_db_35'). 
Apr 12 02:03:48 ubuntu NetworkManager: <info>  Deactivating device eth0. 
Apr 12 02:03:48 ubuntu kernel: [  634.459584] ACPI: PCI interrupt for device 0000:04:00.0 disabled
Apr 12 02:03:50 ubuntu NetworkManager: <debug> [1207980230.750581] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1d_e0_73_89_f9_0'). 
Apr 12 02:03:50 ubuntu NetworkManager: <info>  Deactivating device wlan0. 
Apr 12 02:03:50 ubuntu kernel: [  636.623698] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Apr 12 02:03:51 ubuntu NetworkManager: <WARN>  nm_device_802_11_wireless_get_mode(): error getting card mode on wlan0: No such device 
Apr 12 02:03:51 ubuntu NetworkManager: <debug> [1207980231.118202] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1d_e0_73_89_f9'). 
Apr 12 02:03:55 ubuntu kernel: [  640.088555] PM: suspend-to-disk mode set to 'shutdown'
Apr 12 02:03:55 ubuntu kernel: [  640.089153] swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
Apr 12 02:03:55 ubuntu kernel: [  640.089171] swsusp: Marking nosave pages: 00000000bfed0000 - 0000000100000000
```

---

### Post by thomasaaron on 2008-04-14
Hi, Nathan.

Could you please post the output of: swapon -s

---

### Post by farruinn on 2008-04-14
Ok, so after an unsuccessful hibernate I have no swap and can't turn it on with 'swapon -a'. I open gparted and the swap partition is listed as an "unknown" so I reformat that to linux-swap and now I can enable swap. The output of swap -s is:

```
Filename                                Type            Size    Used    Priority
/dev/sda6                               partition       1044184 0       -1
```

I forgot to mention in my previous post (#12 in this thread) that this is what I did before attempting to hibernate again.

---

### Post by thomasaaron on 2008-04-14
Congratulations! That is one of the top 10 weirdest things I've seen on Ubuntu! :lolflag:

Try the instructions in this thread.
[http://ubuntuforums.org/archive/index.php/t-287096.html](http://ubuntuforums.org/archive/index.php/t-287096.html)

---

### Post by farruinn on 2008-04-14
Thanks for the link - it was informative but unfortunately didn't solve the problem. I have some theories about this problem. It seems that either the RAM image isn't being stored correctly to the swap partition or the image isn't found upon bootup. The swap partition is only ~1GB but that shouldn't matter since the image size was set to 500MB in /sys/power/image_size. I don't know how to interpret the kernel messages from startup to tell if it sees the image in /dev/sda6.

---

### Post by thomasaaron on 2008-04-15
Well, I'm not so sure.

I'll do some more looking around. But, generally, we recommend the swap partition be 2x the installed RAM. I KNOW you've got more that 512MB in a SerP4, right?
Maybe it is overflowing and somehow corrupting the FS when you suspend.

I'd try resizing and reformatting it. Then, if it still doesn't work, try the fix on that link that pertains to the UUID issue.

---

### Post by farruinn on 2008-04-18
Success - the answer was in that thread you posted, Thomas.

Apparently I was skipping step 5: reboot. This meant that even though I put a new uuid in /etc/initramfs-tools/conf.d/resume the old uuid was shown under /dev/disk/by-uuid. It makes me wonder where the memory image was being stored because the hard drive was obviously in use and the swap partition would come back corrupted after reboot.

Thanks for your help on both the issues, problem solved. I'm very excited that I can now hibernate normally!

---

