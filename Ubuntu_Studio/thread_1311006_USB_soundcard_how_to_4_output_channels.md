---
title: "USB soundcard how to: 4 output channels"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by g-raf on 2009-11-02
Linux DJ software Mixxx 1.7.1 is only recognizing 2 output channels on my M-Audio Fast Track Pro. Headphone queing is consequently impossible. I need to have 4 output channels recognized so that I can route the Mixxx headphone output to channels 3-4 which currently aren't available.

Have any ideas on what i need to configure in order to get channels 3-4 recognized by ALSA and Mixxx?

---

### Post by AutoStatic on 2009-11-02
[http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

You need to patch the usbaudio module and recompile it apparently.

---

### Post by g-raf on 2009-11-04
> **AutoStatic said:**
> [http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

You need to patch the usbaudio module and recompile it apparently.

I've known about this patch but don't have a clue how to do it. How does the patch work? Is it a deb file or tar file that i can install? I'd really like to try using the patch.

---

### Post by AutoStatic on 2009-11-04
A patch is a file that contains code that differs from the original code of a program or driver together with information about where the code differs exactly. When you run a patch on source code the patch modifies the source code according to the information in the patch file. So it's not a deb or a tarball. You have to apply the patch to the source code and then compile the modified code.

But I'll check the patch. Which version of Ubuntu are you using? 32 or 64 bit?

---

### Post by japboy on 2009-11-04
hello,
i suppose this thread may help me...

i also have M-Audio Fast Track Pro and wish i could use it with Mixx on Ubuntu.

on Ubuntu 9.04, somehow, I could use 2 stereo outputs and 1 stereo input with 16bit/44.1kHz.

on 9.10, it seems Sound Preferences panel is totally rewritten, looks different from 9.04. and i just use 1 stereo output only. Sound Preferences shows me only 1 output and no inputs.

i was googling about this issue before and know the patch. i wish i could use it though pathing is for me tough. i wonder if someone tried the patch on Ubuntu and may post how it works...

---

### Post by g-raf on 2009-11-05
> **AutoStatic said:**
> Which version of Ubuntu are you using? 32 or 64 bit?

I'm using 32 bit. Thanks so much for helping out with this.

---

### Post by AutoStatic on 2009-11-05
9.04? And which kernel (**uname -a** in a terminal)?

---

### Post by g-raf on 2009-11-05
> **AutoStatic said:**
> 9.04? And which kernel (**uname -a** in a terminal)?

9.04 jaunty, ubuntu studio linux-rt

---

### Post by AutoStatic on 2009-11-05
I've attached the patched modules. I don't have a Fasttrack so I couldn't test anything. This is how to proceed:
- make a copy of your current modules:
[b]sudo cp /lib/modules/2.6.28-3-rt/kernel/sound/usb/usb-snd-audio.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb/usb-snd-audio.ko.orig
sudo cp /lib/modules/2.6.28-3-rt/kernel/sound/usb/usb-snd-lib.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb/usb-snd-lib.ko.orig[/b]
- download the attachement to your desktop and extract the tarball
- copy the modules to the right place:
**sudo cp /home/yourusername/Desktop/*.ko /lib/modules/2.6.28-3-rt/kernel/sound/usb/**
- set the permissions right:
**sudo chown root:root /lib/modules/2.6.28-3-rt/kernel/sound/usb/*.ko**

And then reboot with your fingers crossed. And then hopefully you can use all 4 channels after the reboot. I could have made some typos and keep in mind that with a kernel update all of this has to be done again. And replacing the modules is all at your own risk, chances are you'll have no USB sound after replacing the modules. But then copying the .orig files back to .ko files should reinstate the original configuration.

---

### Post by japboy on 2009-11-05
AutoStatic, you did a brilliant work! Thank you!

Do you think this patch also works on Karmic Koala AMD64? My kernel is 2.6.31-14-generic.

Thanks again.

---

### Post by AutoStatic on 2009-11-06
No, won't work unfortunately. The modules I've attached are compile against the headers of 2.6.28-3-rt 32-bits so Karmic 64-bits will not load them.
And I haven't set up a Karmic chroot yet to build packages/modules, if I have time I'll set it up and patch and compile for Karmic 32-bits.

---

### Post by joegiampaoli on 2009-11-06
Here's a guide I recently did for this device for Pro Audio under ubuntu, might wan't to check it out.

[http://www.joegiampaoli.com/blog/?p=462]("http://www.joegiampaoli.com/blog/?p=462")

Good Luck!

---

### Post by AutoStatic on 2009-11-06
Looks awesome!! I wouldn't compile a complete custom kernel myself though just for some USB sound modules but the rest of the guide is just great! Bookmarking your blog right away :)

---

### Post by japboy on 2009-11-06
wow

joegiampaoli, your article seems so useful! bookmarked!
great job and thank you very much!

---

### Post by g-raf on 2009-11-07
AutoStatic, I've recently found this blog which is a guide to patching the kernel for the Fast Track Pro: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)

What do you think of this? Should i try this or the patch that you've posted?

---

### Post by g-raf on 2009-11-07
> **g-raf said:**
> AutoStatic, I've recently found this blog which is a guide to patching the kernel for the Fast Track Pro: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)

What do you think of this? Should i try this or the patch that you've posted?

Oopsy, someone else already posted it hehe.

---

### Post by g-raf on 2009-11-07
> **AutoStatic said:**
> ...keep in mind that with a kernel update all of this has to be done again.

So far, it hasn't worked for me yet. But there was a small update in the update manager that i just installed. Should i copy the files all over again or just set the permissions right? Also, do i need to name the *.ko file snd-usb-audio or can i use a different name like fast-track-patch?

---

### Post by g-raf on 2009-11-07
Also, do i need to set permissions right for the snd-usb-lib file as well?

---

### Post by AutoStatic on 2009-11-07
g-raf did you follow all the steps I posted? Did you get any warnings or errors? There were no kernel updates so you don't have to do it all again. What does unloading and reloading snd-usb-audio do? Does it output any warnings/errors? You can unload and reload with the following commands:
- Unload: **sudo modprobe -r snd-usb-audio**
- Reload: **sudo modprobe snd-usb-audio**

And you can follow the guide on joegiampaoli.com but then you have to know what you're doing. But I see that you're already compiling yourself so good luck :D

---

### Post by g-raf on 2009-11-07
> **AutoStatic said:**
> And you can follow the guide on joegiampaoli.com but then you have to know what you're doing. But I see that you're already compiling yourself so good luck :D

I followed the guide on joegiampaoli.com, but it's not working. I followed the guide after trying your guide though. How can i get the .orig modules into the new custom kernel in order to see if those modules will be compatible?

---

### Post by AutoStatic on 2009-11-07
Can you boot with the new kernel? What does **uname -a** say? Could you post your */boot/grub/menu.lst* file?

---

### Post by g-raf on 2009-11-08
> **AutoStatic said:**
> - Unload: **sudo modprobe -r snd-usb-audio**
- Reload: **sudo modprobe snd-usb-audio**

I did the *unload* part and got this:

> WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/fast-track-pro, it will be ignored in a future release.

uname -a says this:

> Linux g-rafstudio 2.6.31.4-rt14-custom #1 SMP PREEMPT RT Sat Nov 7 20:24:08 KST 2009 i686 GNU/Linux


---

### Post by g-raf on 2009-11-08
> **AutoStatic said:**
> You can unload and reload with the following commands:
- Unload: **sudo modprobe -r snd-usb-audio**
- Reload: **sudo modprobe snd-usb-audio**

*Reload* gave me this:

> WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/fast-track-pro, it will be ignored in a future release.
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/core/snd-page-alloc.ko): Invalid module format
WARNING: Error inserting snd_timer (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/core/snd-timer.ko): Invalid module format
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/core/snd-pcm.ko): Invalid module format
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/usb/snd-usb-audio.ko): Invalid module format

---

### Post by AutoStatic on 2009-11-08
Hello g-raf, 2.6.31.4-rt14-custom, looks good! But then you don't need the stuff I've uploaded because it's compiled against a different kernel.
```
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/usb/snd-usb-audio.ko): Invalid module format
```Apparently something went wrong with either patching or compiling. I'd suggest you try to do it again. So uninstall your custom kernel (**apt-get remove linux-headers-2.6.31.4-rt14-custom_2.6.31.4-rt14-custom-10.00.Custom_i386 linux-image-2.6.31.4-rt14-custom_2.6.31.4-rt14-custom-10.00.Custom_i386**) and follow the howto again.

And did you ever perform an upgrade on this machine?```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
```With a clean install of 9.04 you shouldn't get those warnings.

---

### Post by g-raf on 2009-11-09
I do have a clean install of 9.04. I've saved both of those files (/etc/modprobe.d/sound & /etc/modprobe.d/fast-track-pro) as .conf files. However, when i try to unload and reload snd-usb-audio, i get this:

FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.31.4-rt14-custom/kernel/sound/usb/snd-usb-audio.ko): Invalid argument

This is my 2nd time patching, compiling and installing the custom kernel.

---

### Post by g-raf on 2009-11-09
As soon as i removed /etc/modprobe.d/fast-track-pro.conf and loaded the linux-rt (ubuntu studio) kernel, my sound is back and fast track pro is working again (but without the 24bit, 4 output channels, etc).

---

### Post by AutoStatic on 2009-11-10
Do you mean 2.6.28-3-rt? Did you try with the modules I uploaded?

---

### Post by g-raf on 2009-11-11
> **AutoStatic said:**
> Do you mean 2.6.28-3-rt? Did you try with the modules I uploaded?

I will try again. Last time, i tested the modules by opening Mixxx and seeing if i could select "Ch 3,4" for the fast track pro headphones output, but that wasn't available, so i assumed it didn't work. Do you have any recommendations for testing it? How can i find out if it's working or not? Also, could these modules allow me to record at 24bit 96000 sample rate that the fast track pro is supposed to?

---

### Post by g-raf on 2009-11-11
I restarted the 2.6.28-3-rt kernel and tried to start qjackctl with 4 output channels and it didn't work. However, it does work with the 96000Hz sample rate. But the sample format for capture is 16bit, not the 24bit I'd like to have. Mixxx (which i use with ALSA since qjackctl is not available in the Sound API preferences) also doesn't give me more than "Ch 1,2" in the sound device preferences for fast track pro. What else should i try? How can i give you more information about what's going wrong?

---

### Post by g-raf on 2009-11-11
> **AutoStatic said:**
> What does unloading and reloading snd-usb-audio do? Does it output any warnings/errors? You can unload and reload with the following commands:
- Unload: **sudo modprobe -r snd-usb-audio**
- Reload: **sudo modprobe snd-usb-audio**

Unloading and reloading the module shows no errors or warnings. The fast track pro is working fine, but without the 24bit sample format and 4 output channels. Seems like the module isn't allowing for that.

---

### Post by AutoStatic on 2009-11-11
But did you copy the modules to the right place? And did you edit your /etc/modprobe.d/alsa-base.conf?

---

### Post by g-raf on 2009-11-12
> **AutoStatic said:**
> But did you copy the modules to the right place? And did you edit your /etc/modprobe.d/alsa-base.conf?

I copied the modules to the right spot, but i haven't edited the /etc/modprobe.d/alsa-base.conf

How should i edit it?

---

### Post by AutoStatic on 2009-11-12
> So we do:
sudo gedit /etc/modprobe.d/fast-track-pro

And we insert the following line:

options    snd_usb_audio    vid=0×763 pid=0×2012 device_setup=0×9 index=5 enable=1

Save and close the file.

Now we configure the alsa-base file, I found out that in newer ubuntu releases the configuration files have been renamed with a .conf extension, so depending on your ubuntu version (you&#8217;ll have to browse yourself), the file we want to edit could be:

/etc/modprobe.d/alsa-base or /etc/modprobe.d/alsa-base.conf

if there is no such file, then it could be

/etc/modprobe.d/sound or   /etc/modprobe.d/sound.conf

It has to be one of those, so open it up with sudo gedit and it should show a bunch of lines with index values. There&#8217;s one we have to look for:

options snd-usb-audio index=-2

change it (comment it out) as:

#options snd-usb-audio index=-2

Save it, and close it

Now reboot&#8230;&#8230;

Source: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)

Remark: keep in mind that your fasttrack Pro will have hardware ID 5 when you perform the above.

---

### Post by g-raf on 2009-11-12
I just tried it, but i have the same problem that i had with the custom kernel: after saving /etc/modprobe.d/fast-track-pro.conf and restarting, ALSA no longer recognizes the fast track pro, leaving me soundless - cat /proc/asound/cards shows only HDA Intel. Very confusing.

---

### Post by AutoStatic on 2009-11-12
Ah! I see a typo:
```
options snd_usb_audio vid=0×763 pid=0×2012 device_setup=0×9 index=5 enable=1
```

This should read:
```
options snd-usb-audio vid=0×763 pid=0×2012 device_setup=0×9 index=5 enable=1
```

So no underscores in the module name but dashes.

---

### Post by g-raf on 2009-11-13
I changed it to this:

```
options snd-usb-audio vid=0×763 pid=0×2012 device_setup=0×9 index=0 enable=1
```

And got the same result. "cat /proc/asound/cards" only shows HDA Intel. In "/etc/modprobe.d/sound.conf" i have the fast track pro set to default, so i set the index=0. 

I really wish someone else got this working so i could find out what they did. I have Pulseaudio disabled...is this dependent on Pulseaudio? What else could i try? Should i give you some info about something?

---

### Post by g-raf on 2009-11-13
In /etc/modprobe.d/sound.conf i have this:

```
options snd-usb-audio index=0
options snd-hda-intel index=1
```

I wonder if it would work if i edit the snd-usb-audio section to this:

```
options snd-usb-audio vid=0×763 pid=0×2012 device_setup=0×9 index=0 enable=1
```

I'll try this.

---

### Post by g-raf on 2009-11-13
That didn't work either. Same results. I really don't want to give up on this. I love ubuntu.

---

### Post by AutoStatic on 2009-11-13
What is in sound.conf? I think it's best in this case to do all configuration in /etc/modprobe.d/alsa-base.conf
And you are now setting the index of snd-usb-audio twice, though I don't think this should cause any issues.
But what is the output of **lsmod | grep snd ** now? Does snd-usb-audio gets loaded? If not, what does manually loading (**sudo modprobe snd-usb-audio**) do? And what does **modinfo snd-usb-audio** say?

---

### Post by g-raf on 2009-11-14
> **AutoStatic said:**
> What is in sound.conf? But what is the output of **lsmod | grep snd ** now? Does snd-usb-audio gets loaded? If not, what does manually loading (**sudo modprobe snd-usb-audio**) do? And what does **modinfo snd-usb-audio** say?

[B]lsmod | grep snd gives me this:

[/B]> snd_hda_intel         435508  0 
snd_pcm_oss            46464  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                82436  2 snd_hda_intel,snd_pcm_oss
snd_usb_lib            24064  0 
snd_hwdep              15236  0 
snd_seq_dummy          10756  0 
snd_seq_oss            38272  0 
snd_seq_midi           14336  0 
snd_rawmidi            29440  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29444  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63140  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15584  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm


[B]sudo modprobe snd-usb-audio gives me this:

[/B]> FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.28-3-rt/kernel/sound/usb/snd-usb-audio.ko): Invalid argument

**modinfo snd-usb-audio** gives me this:

> filename:       /lib/modules/2.6.28-3-rt/kernel/sound/usb/snd-usb-audio.ko
license:        GPL
description:    USB Audio
author:         Takashi Iwai <tiwai@suse.de>
srcversion:     EA5623F784CA0AAC7118B8B
alias:          usb:v*p*d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v*p*d*dc*dsc*dp*ic01isc03ip*
alias:          usb:v7104p2202d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4752p0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13E5p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1235p4661d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v1235p0002d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v1235p0001d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v103Dp0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Dp0100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp0035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CCDp0014d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0CCDp0013d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0CCDp0012d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v086Ap0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v086Ap0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v086Ap0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FDp0001d*dc*dsc02dp*ic*isc*ip*
alias:          usb:v07CFp6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07CFp6801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0763p2019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0763p200Dd*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p2008d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p2003d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p2001d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1041d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1033d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1031d010dc*dsc*dp*ic*isc*ip*
alias:          usb:v0763p1021d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1015d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1011d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0763p1002d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v06F8pB000d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p00E6d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p00DAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p00C2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p00ADd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p00A6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p00A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p009Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0096d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p008Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0080d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p007Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p007Ad*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p0075d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0074d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p006Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p006Ad*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p004Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0044d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p003Bd*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p0037d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p002Bd*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0582p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p001Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p001Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0014d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0582p0000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p7000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p500Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p5000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p2002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p2001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p2000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p104Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p104Ed*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0499p1045d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1044d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1043d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p103Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1038d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1037d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1036d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1034d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p102Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p102Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p102Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p101Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1014d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p100Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p100Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p100Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p100Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p100Ad*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0499p1009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1007d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1005d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1004d*dc*dsc*dp*icFFisc*ip*
alias:          usb:v0499p1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0499p1000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v046Dp0990d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v046Dp08F6d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v046Dp08F5d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v046Dp08F0d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v046Dp08C6d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v046Dp08AEd*dc*dsc*dp*ic01isc01ip*
alias:          usb:v046Dp0850d*dc*dsc*dp*ic01isc01ip*
alias:          usb:v041Ep3F0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v041Ep3F04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v041Ep3F02d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v041Ep3010d*dc*dsc*dp*ic*isc*ip*
depends:        snd-usb-lib,snd-pcm,snd,snd-hwdep
vermagic:       2.6.28-3-rt SMP preempt mod_unload modversions 586 
parm:           index:Index value for the USB audio adapter. (array of int)
parm:           id:ID string for the USB audio adapter. (array of charp)
parm:           enable:Enable USB audio adapter. (array of bool)
parm:           vid:Vendor ID for the USB audio device. (array of int)
parm:           pid:Product ID for the USB audio device. (array of int)
parm:           nrpacks:Max. number of packets per URB. (int)
parm:           async_unlink:Use async unlink mode. (bool)
parm:           device_setup:Specific device setup (if needed). (array of int)
parm:           ignore_ctl_error:Ignore errors from USB controller for mixer interfaces. (bool)

---

### Post by AutoStatic on 2009-11-14
```
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.28-3-rt/kernel/sound/usb/snd-usb-audio.ko): Invalid argument 
```
Ok, I know enough, apparently the module I compiled does not work. I've compiled it in a chrooted Jaunty environment. For applications this is ok, but for modules it doesn't work or I am overseeing something. Probably the last ;)
I I find the time I'll try to post a little howto on compiling the modules yourself. For now it's best to use the original usb audio module otherwise you have no sound at all.

---

### Post by g-raf on 2009-11-15
> **AutoStatic said:**
> ```
FATAL: Error inserting snd_usb_audio (/lib/modules/2.6.28-3-rt/kernel/sound/usb/snd-usb-audio.ko): Invalid argument 
```Ok, I know enough, apparently the module I compiled does not work. I've compiled it in a chrooted Jaunty environment. For applications this is ok, but for modules it doesn't work or I am overseeing something. Probably the last ;)
I I find the time I'll try to post a little howto on compiling the modules yourself. For now it's best to use the original usb audio module otherwise you have no sound at all.

I'm using the modules you've compiled and i get sound. When i save /etc/modprobe.d/fast-track-pro.conf and restart, then i have no sound with the fast track pro. The fast track pro doesn't show up when i cat /proc/asound/cards.

---

### Post by AutoStatic on 2009-11-15
You're right, it says "invalid argument"](*,) And you have sound unless you use the specific fast-track-pro.conf file.
So that means that an argument given is invalid. Could you give the output of **lsusb** ?

---

### Post by g-raf on 2009-11-15
> **AutoStatic said:**
> Could you give the output of **lsusb** ?

lsusb gives me:

> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0763:2012 Midiman 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But i deleted /etc/modprobe.d/fast-track-pro.conf before checking this.

---

### Post by AutoStatic on 2009-11-15
Thanks! I was looking for this:
```
Bus 005 Device 002: ID 0763:2012 Midiman 
```

So found another typo and checked the unofficial Alsa wiki and found even one more typo, the line in fast-track-pro.conf should be:
```
options snd-usb-audio vid=0×0763 pid=0×2012 device_setup=0×09 index=0 enable=1
```

Could you try that one? You could play around with the device_setup option, I think when you put 0x25 there you activate everything.

---

### Post by g-raf on 2009-11-15
It still doesn't work. cat /proc/asound/cards shows no fast track pro and i have no sound. [B]"sudo modprobe snd-usb-audio" also gives me the same result.

C[/B]an i give some more info to help? It seems that /etc/modprobe.d/fast-track-pro.conf is full of typos.

---

### Post by AutoStatic on 2009-11-16
I have to check the patch itself again to verify the values if the device_setup option.
What I find so weird is that on Joe Giampaoli's blog the settings from the unofficial ALSA wiki work apparently. To me this seems impossible:
[LIST=1]
[*]The naming convention for modules changed a while back from snd_usb_audio to snd-usb-audio
[*]The Wiki mentions that you have to add up the device_setup values in order to obtain extra functionality:
>     This will put the FastTrack Pro at device number 5 with 24bit mode, max. 48kHz sampling mode, 2 inputs and 4 outputs. According to the patch, the possible values for the device_setup parameter are the sum of the following numbers:

    * 0×01 : use the device_setup parameter, always needed
    * 0×02 : enable digital output (channels 3,4)
    * 0×04 : use 48kHz-96kHz sampling rate, 8-48 kHz if not used
    * 0×08 : 24bit sampling rate
    * 0×10 : enable digital input (channels 3,4)

    Recording can be done e.g. by using arecord:

    arecord -c2 -t raw -fS24_3BE -d5,0 …
But how do you get a sum of 0x9? Or does 0x01 + 0x02 + 0x04 + 0x08 + 0x10 equal 0x9? No idea :confused:
[/LIST]

What doesn't help either is that I don't own a Fasttrack Pro device so I can't test anything.

---

### Post by AutoStatic on 2009-12-06
Ok, maybe this helps, I've compiled a kernel for Karmic 64-bit that includes the patch:

[http://linux.autostatic.com/ubuntu/linux-headers-2.6.31.4-rt14-fasttrackpro1.deb](http://linux.autostatic.com/ubuntu/linux-headers-2.6.31.4-rt14-fasttrackpro1.deb)
[http://linux.autostatic.com/ubuntu/linux-image-2.6.31.4-rt14-fasttrackpro1.deb](http://linux.autostatic.com/ubuntu/linux-image-2.6.31.4-rt14-fasttrackpro1.deb) 

Please let me know if it works or not. I've also found out that compiling single modules is very likely to work so that was bound to fail anyway. Downloading and double-clicking should install the kernel and the headers.

---

### Post by g-raf on 2009-12-14
> **AutoStatic said:**
> Ok, maybe this helps, I've compiled a kernel for Karmic 64-bit that includes the patch:

[http://linux.autostatic.com/ubuntu/linux-headers-2.6.31.4-rt14-fasttrackpro1.deb](http://linux.autostatic.com/ubuntu/linux-headers-2.6.31.4-rt14-fasttrackpro1.deb)
[http://linux.autostatic.com/ubuntu/linux-image-2.6.31.4-rt14-fasttrackpro1.deb](http://linux.autostatic.com/ubuntu/linux-image-2.6.31.4-rt14-fasttrackpro1.deb) 

Please let me know if it works or not. I've also found out that compiling single modules is very likely to work so that was bound to fail anyway. Downloading and double-clicking should install the kernel and the headers.

I'm using 32-bit Jaunty. Karmic didn't work during the attempted installation.

---

### Post by AutoStatic on 2009-12-14
Ok, I'll try brewing some 32-bits Jaunty kernel then tonight in my cauldron.

---

### Post by swornbrother on 2009-12-23
Hey guys, I've been trying to get the Fast Track Pro working in 24-bit/96000khz on my Karmic64 for some time, and over the past couple days I've been trying the advice provided in this thread, and that of Joe Giampaoli's blog, with limited success.

I first tried compiling the kernels provided by Autostatic, which did allow FTP to run 48000khz for the first time ever (never got it aboved 44000khz before!)  Unfortunately, 24-bit never worked under this kernel even after trying the different suggestions of renaming the values in fast-track-pro.conf, and for some reason my NVIDIA drivers wouldn't load upon boot.

I then tried compiling my own kernel (had to disable staging drivers.)  This kernel flashed two errors during bootup that were so fast I couldn't read them.  NVIDIA worked.  However, I still couldn't get 24-bit going, but could do 48000khz again.  Using the  advice of renaming the values in the fast-track-pro.conf still haven't produced any results, and I'm at a loss of where to go from here.

Any help/suggestions would be appreciated.  Thanks!

---

### Post by swornbrother on 2009-12-23
Ok, so I'm beginning to believe that /etc/modprobe.d/fast-track-pro.conf or /etc/modprobe.d/fast-track-pro DO NOTHING.

Even if I delete the files I can still fire up the FTP, in 48000, but without 24-bit.  You don't need these files to get it up and running, maybe you need them for 24-bit, but I'm not sure, as I don't really know how to test this.

---

### Post by AutoStatic on 2009-12-25
Hello swornbrother, as I don't own a FTP myself it's just too hard to help troubleshooting. But the fast-track-pro.conf file should really do something, if it doesn't then either the patch is not applied properly or there are typo's in the fast-track-pro.conf file.
What is currently in your fast-track-pro.conf file?

---

### Post by g-raf on 2009-12-30
> **AutoStatic said:**
> Ok, I'll try brewing some 32-bits Jaunty kernel then tonight in my cauldron.

Any luck with this?

---

### Post by AutoStatic on 2009-12-30
No, sorry. Next week when I'm back at work I'll have some time to do it.

---

### Post by g-raf on 2010-03-15
> **AutoStatic said:**
> Ok, I'll try brewing some 32-bits Jaunty kernel then tonight in my cauldron.

I'm still trying to get mine to work, so please let me know if you do this. I recently tried to add an audio group to the Users & Groups, but this didn't work.

---

