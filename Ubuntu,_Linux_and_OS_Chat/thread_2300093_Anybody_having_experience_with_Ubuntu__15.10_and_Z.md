---
title: "Anybody having experience with Ubuntu  15.10 and Z170 ?"
date: 2015-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by MrHobbit on 2015-10-23
Hi,

I'm in for a hardware upgrade and I'm thinking about ASUS MAXIMUS VIII HERO or even ASUS Z170 deluxe + 7i 6700.
Just wondering if these run Ubuntu 15.10 properly.
Is there somebody out there who already tried this ?

Thanks.

---

### Post by mail-kariver on 2015-10-23
Assuming that they are EFI-compatible computers, you can probably boot from a pendrive. The most universal distros I recommend (sadly not sure if 15.10-based) are:

[LIST]
[*]elementary OS Freya, Ubuntu 14.04 LTS
[*]Kubuntu, Ubuntu (mine is 14.04 LTS)
[/LIST]

Please use Rufus and make sure your pendrive is GPT, if your original PC is under Windows.

---

### Post by trentggg on 2016-01-05
15.10 mostly works with Z170 Deluxe. The only issue I had was with WiFi. I was able to use a USB tether with my phone and install bcmwl-kernel-source which immediately made WiFi work without even a reboot.

I could not get audio to work in 14.04 and that's why I installed 15.10.

---

### Post by Bucky Ball on 2016-01-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by fjgaude on 2016-01-06
I'm using 16.04 with a Z170 ASRock MB... it is okay but last I checked audio didn't work but WIFi did. It's a work in progress. By release time most things should be there.

---

### Post by rdeknijf on 2016-02-23
I just got the audio to work by upgrading the kernel from 3.19 to 4.4.2. for Ubuntu 15.10.
All other efforts failed. I tried many different alsa drivers in 14.04 and 15.10.

I don't use wifi on this board, so I wouldn't know.

I also had a hell of a time setting up video. I had to unplug and replug monitors to get to a shell to install the nvidia drivers. I expect this has something to do with the internal video-card, even though no image was being sent from those ports as well.

And, the kicker, nothing to do with Ubuntu, but this gave me so much grief: until I enabled the TPU1 switch on the motherboard I had constant Code 55 errors ("no memory installed", or really just "invalid memory") even though I use supported RAM.

But for now it's running like a charm.

---

### Post by fjgaude on 2016-02-23
After the last update of 16.04 my Z170 ASRock ITX/ac board is working fine, audio, video, wifi, and most other things. VirtualBox hasn't worked and needs to be upgraded but that will come likely just as 16.04 gets released in April.

---

### Post by Bucky Ball on 2016-02-24
> **fjgaude said:**
> After the last update of 16.04 my Z170 ASRock ITX/ac board is working fine, audio, video, wifi, and most other things. VirtualBox hasn't worked and needs to be upgraded but that will come likely just as 16.04 gets released in April.

This is your second post regarding 16.04 LTS. It is not released yet, as you accurately state, and as such all posts/threads about it go in 'Ubuntu Development Version' forum, not here or anywhere else.

If you have something to add in relation to a supported, released version of Ubuntu, feel free to input. Your progress with 16.04 LTS does not belong on this thread and may be considered thread drifting as this thread is specifically about 15.10 and the Z170. 

If you are encouraging a brand new user to install an unreleased, testing version of Ubuntu, not a good plan. While your install is working great now, it may not be after the next update/upgrade or in a week, as is the nature of a development release. Thanks. :)

---

### Post by gordintoronto on 2016-02-24
It's usually a bad idea to try a Linux kernel which is older than the motherboard.

> **mail-kariver said:**
> Assuming that they are EFI-compatible computers, you can probably boot from a pendrive. The most universal distros I recommend (sadly not sure if 15.10-based) are:

[LIST]
[*]elementary OS Freya, Ubuntu 14.04 LTS
[*]Kubuntu, Ubuntu (mine is 14.04 LTS)
[/LIST]

Please use Rufus and make sure your pendrive is GPT, if your original PC is under Windows.

---

### Post by fjgaude on 2016-02-24
Thanks, Bucky Ball, for your comments. Okay!

---

### Post by fjgaude on 2016-02-27
> **fjgaude said:**
> Thanks, Bucky Ball, for your comments. Okay!

I went and put 15.10 on a flash drive and am running its on a Z170 box.

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

ubuntu@ubuntu:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   18998 MB in  2.00 seconds = 9505.63 MB/sec
 Timing buffered disk reads: 1332 MB in  3.00 seconds = 443.59 MB/sec

```

My CPU is a i3-6100 at 3.7GHz with Intel video: Skylake DT GT2 running.

Looks like everything that I tested works.... audio, video, browser, so I would say that 15.10 is good for Z170 chip sets.

---

