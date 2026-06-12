---
title: "QjackCtl won't start / Kernel won't create Firewire ID"
date: 2016-08-01
forum: Ubuntu Studio
---

### Post by elaterite on 2016-08-01
**Hi -**

Off and on I've been trying to fix a Firewire issue with my machine for many months.

I'm unable to start the JACK Audio Connection Kit (QjackCtl).

I think I've finally diagnosed the problem as having something to do with the kernel given the output I'm seeing in the syslog (see output below).

I don't have a clue of how to fix it though. Any ideas?

**Details:**

I'm running Ubuntu Studio 16.04.1 with kernel 4.4.0-31-lowlatency.

The box is connected to an Onyx-i series Firewire mixer via a PCIe adapter.

This all worked at one time. It was during a box rebuild and/or distro update it all stopped working. I forget which.

**The following log report seems to point to the error:**

```
/var/log/syslog [Same as output from dmesg | grep -E -i "(1394|firewire)"]

Jul 31 15:06:14 elaterite2 kernel: [ 309.319310] firewire_ohci 0000:08:00.0: no self IDs
Jul 31 15:06:14 elaterite2 kernel: [ 309.820118] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:14 elaterite2 kernel: [ 310.091688] firewire_core 0000:08:00.0: PHY ID mismatch in self ID: 0 != 1
Jul 31 15:06:14 elaterite2 kernel: [ 310.091694] firewire_core 0000:08:00.0: topology build failed
Jul 31 15:06:20 elaterite2 kernel: [ 315.540954] firewire_ohci 0000:08:00.0: bad self ID 0/5 (e07fe864 != ~00000000)
[Then the 'firewire_core' lines are repeated three more times.]
Jul 31 15:06:23 elaterite2 kernel: [ 318.634629] firewire_ohci 0000:08:00.0: no self IDs
Jul 31 15:06:24 elaterite2 kernel: [ 319.407269] firewire_ohci 0000:08:00.0: bad self ID 0/7 (e07fe864 != ~00000000)
Jul 31 15:06:24 elaterite2 kernel: [ 319.907889] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:24 elaterite2 kernel: [ 320.179665] firewire_core 0000:08:00.0: PHY ID mismatch in self ID: 0 != 1
Jul 31 15:06:24 elaterite2 kernel: [ 320.179671] firewire_core 0000:08:00.0: topology build failed
Jul 31 15:06:25 elaterite2 kernel: [ 320.679887] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:25 elaterite2 kernel: [ 320.961220] firewire_core 0000:08:00.0: PHY ID mismatch in self ID: 0 != 1
Jul 31 15:06:25 elaterite2 kernel: [ 320.961227] firewire_core 0000:08:00.0: topology build failed
Jul 31 15:06:26 elaterite2 kernel: [ 321.461854] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:26 elaterite2 kernel: [ 321.734822] firewire_ohci 0000:08:00.0: bad self ID 0/5 (00000000 != ~00d117a2)
Jul 31 15:06:26 elaterite2 kernel: [ 322.235878] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:27 elaterite2 kernel: [ 322.503466] firewire_ohci 0000:08:00.0: bad self ID 0/4 (01fe8860 != ~00000000)
Jul 31 15:06:27 elaterite2 kernel: [ 323.003855] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:27 elaterite2 kernel: [ 323.285296] firewire_ohci 0000:08:00.0: no self IDs
Jul 31 15:06:28 elaterite2 kernel: [ 323.785834] firewire_core 0000:08:00.0: rediscovered device fw0
Jul 31 15:06:28 elaterite2 kernel: [ 324.074609] firewire_core 0000:08:00.0: PHY ID mismatch in self ID: 0 != 1
Jul 31 15:06:28 elaterite2 kernel: [ 324.074617] firewire_core 0000:08:00.0: topology build failed
Jul 31 15:06:29 elaterite2 kernel: [ 324.575845] firewire_core 0000:08:00.0: rediscovered device fw0
```

And so on...for over a hundred lines. The kernel seems to keep this process up continuously while the OS is running.

**Here's the JACK Audio Connection Kit log when I try to connect to my mixer (which is turned on) using the Firewire drivers (under the Kit's 'settings' tab).**

```
/home/bob/.log/jack/

Sun Jul 31 17:55:52 2016: ------------------
Sun Jul 31 17:55:52 2016: Controller activated. Version 1.9.11 (unknown) built on Wed Oct 28 16:44:17 2015
Sun Jul 31 17:55:52 2016: Loading settings from "/home/bob/.config/jack/conf.xml" using expat_2.1.0 ...
Sun Jul 31 17:55:52 2016: setting parameter 'engine':'driver':'(null)' to value "firewire"
Sun Jul 31 17:55:52 2016: setting parameter 'engine':'realtime':'(null)' to value "true"
Sun Jul 31 17:55:52 2016: setting parameter 'engine':'verbose':'(null)' to value "false"
Sun Jul 31 17:55:52 2016: setting parameter 'engine':'client-timeout':'(null)' to value "500"
Sun Jul 31 17:55:52 2016: setting parameter 'drivers':'firewire':'period' to value "128"
Sun Jul 31 17:55:52 2016: setting parameter 'drivers':'firewire':'nperiods' to value "3"
Sun Jul 31 17:55:52 2016: setting parameter 'drivers':'firewire':'rate' to value "44100"
Sun Jul 31 17:55:52 2016: Listening for D-Bus messages
Sun Jul 31 17:55:59 2016: Starting jack server...
Sun Jul 31 17:55:59 2016: JACK server starting in realtime mode with priority 10
Sun Jul 31 17:55:59 2016: self-connect-mode is "Don't restrict self connect requests"
Sun Jul 31 17:55:59 2016: [1m[31mERROR: firewire ERR: FFADO: Error creating virtual device[0m
Sun Jul 31 17:55:59 2016: [1m[31mERROR: Cannot attach audio driver[0m
Sun Jul 31 17:55:59 2016: [1m[31mERROR: JackServer::Open failed with -1[0m
Sun Jul 31 17:55:59 2016: [1m[31mERROR: Failed to open server[0m
Sun Jul 31 17:56:00 2016: Saving settings to "/home/bob/.config/jack/conf.xml" ...

```

**Looks like the kernel has loaded the drivers, correct?**

```
lsmod | grep -E -i "(1394|firewire)"

firewire_ohci 40960 0
firewire_core 65536 1 firewire_ohci
crc_itu_t 16384 1 firewire_core
```

**And it looks like the OS see the PCIe Firewire card, correct?**

```
lspci

07:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] (rev 01)
08:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] (rev 01)
```

Any ideas of what my problem is?

Thanks!

---

### Post by CrocoDuck on 2016-08-02
Your firewire card is recognized and the kernel modules are loaded. The kernel logs show that the kernel is attempting working with the device without having any success at it. Are you sure the device is working properly? Check the cables and, if you can, try to see if it works on another computer with another os. By the way, although I think the kernel modules are spawning this, I don't know whether your device is [supported by FFADO]("http://www.ffado.org/?q=devicesupport%2Flist&field_manufacturer_value=&title=onyx&field_support_status_value_op=or&field_support_status_value=All").

---

### Post by wavesound on 2016-08-06
Hi I have the same issue here .

New build of Ubuntu studio 16.6

Here is what I can find so far with my Saffire pro 26 connected By FW.

******

studio@studio-T5500:~$ ls /dev/fw*
/dev/fw0
studio@studio-T5500:~$ ls -l /dev/fw0
crw------- 1 root root 246, 0 Aug  6 19:34 /dev/fw0
studio@studio-T5500:~$ ls -l /dev/fw0
crw------- 1 root root 246, 0 Aug  6 19:34 /dev/fw0
studio@studio-T5500:~$ ls /dev/fw*
/dev/fw0  /dev/fw1
studio@studio-T5500:~$ ls -l /dev/fw1
crw-rw----+ 1 root audio 246, 1 Aug  7 02:42 /dev/fw1
studio@studio-T5500:~$ 
$ 

-----------------------------------
studio@studio-T5500:~$ lsmod | grep fire
snd_firewire_lib       32768  1 snd_bebob
snd_rawmidi            32768  4 snd_firewire_lib,snd_bebob,snd_hdsp,snd_seq_midi
snd_pcm               106496  7 snd_firewire_lib,snd_bebob,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hdsp,snd_hda_core
firewire_ohci          40960  0
firewire_core          65536  3 snd_firewire_lib,snd_bebob,firewire_ohci
crc_itu_t              16384  1 firewire_core
studio@studio-T5500:~$ 

***************************



Am I right in assuming the card is seen and loaded.
I cannot start Jack or FFADO mixer

Cheers Bob

---

### Post by marseille2 on 2016-08-07
Months ago, I was reading through lists and I noticed that with successive upgrades, Firewire support is not as good as it once was. Can't remember where anything is since it's too far back... but searching through kernel and bug lists might shed some light.

---

### Post by wavesound on 2016-08-08
Hi Thank you for the reply.
Indeed it seems the case. I now realise when  Linux audio says the firewire is fully supported I now note it's from years ago.
I then got a copy of win 7 pro 64bit only to be told my RME card willl never have a driver for 64 bit systems £ 400,00 card now unusable).
I thought Firewire would be a no brainer as it's so old.
So Far I can't use the ADATs on win 7 as no driver and can't use FW on Linux 10 years of using and supporting Ardour stopped dead.
Don't we just love upgrades.
Cheers Bob

---

