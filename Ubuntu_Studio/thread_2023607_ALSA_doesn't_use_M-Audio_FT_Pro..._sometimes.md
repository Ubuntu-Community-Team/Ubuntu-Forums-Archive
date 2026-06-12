---
title: "ALSA doesn't use M-Audio FT Pro... sometimes"
date: 2012-07-12
forum: Ubuntu Studio
---

### Post by dewdrop_world on 2012-07-12
Yes, another thread about USB audio woes...

My M-Audio fast track pro works perfectly, most of the time. But, once in a while, I switch it on and:

- it appears in lsusb,

- qjackctl's "messages" window shows "ALSA connection change" and "ALSA connection graph change" -- this tells me ALSA recognizes something about the sound card and changes its internal state in response to connecting the device,

- but the device doesn't appear in aplay -l, and Jack is not able to connect for playback.

This may or may not be related to logging out and logging back in without a reboot, or waking from sleep.

So far, the only solution I've found is to reboot. That's a waste of time. (I use Linux instead of Windows so that I should *not* have to reboot daily.)

Is there another way to force ALSA to talk to this unit? Maybe "modprobe -r snd_usb_audio; modprobe snd_usb_audio"?

Ubuntu 12.04, Linux dlm-A6200 3.2.0-23-lowlatency #31-Ubuntu SMP PREEMPT Wed Apr 11 02:24:03 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

James

---

### Post by dewdrop_world on 2012-07-12
So, it happened again, immediately after a reboot this time. So I tried

sudo modprobe -r snd_usb_audio
sudo modprobe snd_usb_audio

... and ALSA was back in touch with the device.

Is there an easier way to do this? I now have a laundry list of three or four things I have to check by hand every time I log in. It's starting to get irritating.

James

---

### Post by sgx on 2012-07-13
Hi, try this:

[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-kernel-modules-persistant.html](http://www.centos.org/docs/5/html/Deployment_Guide-en-US/s1-kernel-modules-persistant.html)

Cheers

---

