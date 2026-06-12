---
title: "no sound"
date: 2008-11-28
forum: System76 Support
---

### Post by slogger on 2008-11-28
after a security update last night I lost my sound. 
 All volume controls are checked.
playback is on alsa pcm on front
Ran system76 "install drivers" and rebooted

panp4n
ubuntu 8.04
sys 76 driver 2.2.7

---

### Post by thomasaaron on 2008-11-28
Please provide more information about how your sound controls are set up.

Also, make sure PCM, Master, and Front are not muted or turned down too low.

Do you get any error messages if you go to System > Preferences > Sound and press the first Test button.

---

### Post by slogger on 2008-11-28
Nothing is muted and all levels are at max

I get no error messages after running the first test button or sound

I believe all my settings are on default? (autodetect)

---

### Post by swizman on 2008-11-28
Same here. 

No sound after last night's upgrade to kernel 2.6.24-22-generic.

Did a system76 driver restore and a reboot, no sound. 

Nothing is muted and all levels are at max. No error and no sound with any Test buttons. All settings are on Autodetect.  

panp4n
ubuntu 8.04

Booting into the old kernel 2.6.24.-21-generic and the sound works fine.

---

### Post by thomasaaron on 2008-11-28
Sorry, I'm out of the office today, so I don't have access to a PanP4.
I'll be back in the office on Monday, though.

**_Slogger:_**

Please run your System76 Driver...
System > Administration > System76 Driver > Install Tab > Install Button.
...then REBOOT.

Try putting your settings on ALSA instead of auto-detect (in System > Prefs > Sound).

Also, make sure your testing from a fresh reboot and not after resuming from suspend or hibernate.

Also, please post the output of this command...
uname -r

**_Swizman:_**

Is that a proposed kernel? (We're working with Intrepid now, so I'm not really following the progress of Hardy's kernels at the moment... and I'm at home...) In other words, in System > Admin > Software Sources > Updates, do you have the proposed checkbox selected?

If so, try booting into the previous kernel (when you see the grub countdown < grub 3...2...1...> press Esc and select the previous non-recovery-mode kernel and see if sound works there).

---

### Post by swizman on 2008-11-28
I do not have proposed checked. 

Last night was a Hardy security update. Here is the commit log from Synaptic:

Commit Log for Thu Nov 27 20:52:34 2008

Upgraded the following packages:
linux-generic (2.6.24.21.23) to 2.6.24.22.24
linux-headers-generic (2.6.24.21.23) to 2.6.24.22.24
linux-image-generic (2.6.24.21.23) to 2.6.24.22.24
linux-restricted-modules-generic (2.6.24.21.23) to 2.6.24.22.24

Installed the following packages:
linux-headers-2.6.24-22 (2.6.24-22.45)
linux-headers-2.6.24-22-generic (2.6.24-22.45)
linux-image-2.6.24-22-generic (2.6.24-22.45)
linux-restricted-modules-2.6.24-22-generic (2.6.24.14-22.53)
linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35)


I already booted into the previous kernel 2.6.24-21-generic (non-recovery-mode) and sound works fine.

Booting into the new kernel gives no sound and I do not change any sound settings except changing the kernel.

---

### Post by slogger on 2008-11-28
Still no sound after driver install

all audio set to alsa

output of command uname -r

2.6.24-22-generic

---

### Post by Guille Damke on 2008-11-29
Hello people,

Just for sharing my experience, I also updated my system today, with the suggested security packages of the Update Manager, and the new kernel killed my audio (kernel 2.6.24-22). I am running Ubuntu 8.04 on a Pangolin Performance panp4n.
I rebooted using the previous kernel 2.6.24-21 and sound is working fine.
I think we have to wait until Monday to hear news from the guys of system76 about what the new kernel is doing wrong. By now, we can always boot using the previous kernel (press "esc" when grub loads).

Cheers.

---

### Post by earrame on 2008-11-29
I have no sound either. Lost it a couple weeks (or so?) ago and I'm finally getting around to persuing a fix. I can't tie it's loss to a particular update event. I have grown accustom to having no sound coming out of hibernation or suspend. I had just been rebooting when I wanted to hear something. It's a drag but I haven't had time to deal with it. But now all sound is completely gone.

System > Preferences > Sound is the only place I know to adjust sound stuff. Here's the info that I think has been requested so far;

uname -r result is: 2.6.24-21-generic
System: panp4i
System76 driver version: 2.2.7 (just ran an update and rebooted)
Ubuntu 8.04.1
No error messages when pushing test button in the Sound Preferences..
Tried the ALSA setting.
Nothing is muted.

It seems people are having success booting into the kernel I am currently running. I don't have any other kernel options when I esc from the grub load. Only the recovery for this kernel.

---

### Post by formol on 2008-11-30
I got the same problem, no sound.  did the problem with unstable wifi is over with Ubuntu 8.10?  like Tom said, they are working on the last version Ubuntu.

---

### Post by swizman on 2008-11-30
**Earrame**:

I wrote a shell script "sound_check.sh" to collect sound information. 

Extract the 3 files from my attachment file "sound.tar" to your Desktop.

Open a shell and run the commands:
cd ~/Desktop 
sh sound_check.sh

This should create a new text file named "sound_check.txt" on your Desktop.

Compare this file with the one I made called 
"sound_check_sound-ok.txt" 
and maybe it will help you to find the problem.

My other file 
"sound_check_no-sound.txt" 
is made with the new kernel with no sound. 

I cannot see a reason why there is no sound, I think it is a kernel problem. 

**thomasaaron:** Please look at my two text files with my sound information. Thank you.

---

### Post by thomasaaron on 2008-12-01
Imaging a PanPx with Hardy now. I'll test the sound with various updates and see what happens. Stand by...

---

### Post by thomasaaron on 2008-12-01
OK, I imaged a PanPx with Hardy and tested sound. A-OK.
Updated to the current kernel and tested sound. A-OK.
Enabled proposed updates, updated and tested sound. A-OK.

(BTW: I ran the current System76 driver after each update.)

So, I doubt an update is the problem.

Actually, I can't even reproduce the problem on our shop computer, so perhaps there is some other program hosing sound in your cases.

---

### Post by swizman on 2008-12-01
**Thomasaaron:**

Could you please run my script “sound_check.sh” (see attachment to my post # 11) on your machine and post the resulting text file so we can compare your sound settings with ours ?

Thank you.

---

### Post by swizman on 2008-12-01
OK, I have the sound back.

Following the thread
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I determined that I have a Realtek ALC662 rev1 sound card (in my panp4n).

I changed the last line of the file

/etc/modprobe.d/alsa-base 

from 
	options snd-hda-intel model=3stack-6ch-dig

to 
	options snd-hda-intel model=auto

and after a reboot, I have now sound in both my Hardy kernels 2.6.24-21 (old) and 2.6.24-22 (new).


Unfortunately, after closing/opening the lid, the sound does not come back anymore.

Maybe Thomas can help here with a change in the system76 driver?

---

### Post by thomasaaron on 2008-12-02
Are you using a System76 computer?

The System76 driver puts this...
options snd-hda-intel model=3stack-6ch-dig
...in the alsa-base file. That line is necessary for you to have sound after resuming from suspend (which is why you now loose sound after closing and opening your lid).

Please answer these questions:

1. With the above line in your alsa-base file, do you always have sound after a fresh boot? If not, you either have a configuration set incorrectly or there is some other software conflicting with your sound.

2. With the above line in your alsa-base file, do you have sound after closing your lid and opening it (suspending and resuming)? Always? Sometimes?

I'll try the script and post my results back later today.

---

### Post by swizman on 2008-12-02
I am using a system76 panp4n laptop purchased two months ago.



OS is Hardy 8.04.1  64-bit. It is still the original installation from system76 with system76 drivers 2.2.7.


There is NO additional software installed !


All I did was installing the official Hardy security update last week, which replaces the kernel and kills the sound.





kernel 2.6.24-21 (old)



	options snd-hda-intel model=3stack-6ch-dig  

		> sound ok after fresh boot (always)

		> sound ok after suspend/resume (always)



	options snd-hda-intel model=auto

		> sound ok after fresh boot (always)

		> sound ok after suspend/resume (always)





kernel 2.6.24-22 (new):



	options snd-hda-intel model=3stack-6ch-dig  

		> NO sound after fresh boot (always)

		> NO sound after suspend/resume (always)



	options snd-hda-intel model=auto

		> sound ok after fresh boot (always)

		> no sound after suspend/resume (always)
		
		
Besides this option line, nothing else (no sound settings) is changed between reboots. 

As you can see in this thread, there are 2 other system76 customers with the same problem.

---

### Post by thomasaaron on 2008-12-02
Please post the output of...
uname -r

It *should* read: 2.6.24-22-generic -- if it doesn't have the 'generic' part, you are running the wrong kernel.

I'm running 2.6.24-22-generic, and with the model name inserted by the driver, and I have sound both on a fresh start and after suspending from resume.

---

### Post by swizman on 2008-12-02
uname -a 
Linux fifi 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

---

### Post by thomasaaron on 2008-12-02
Hmmm... I'm not sure, then. That looks good.

I'm definitely not able to reproduce the problem in the shop with the same kernel.

We'll look at it some more tomorrow.

---

### Post by kougaru on 2008-12-04
I think I'm having the same problem with my panp4n. Sound just seemed to randomly stop working. I'm not sure if it was directly after an update or not though.

Edit: I forgot to mention I'm running Intrepid.

---

### Post by thomasaaron on 2008-12-04
I'm not sure why you guys are having difficulty with sound in Hardy lately. It works fine on our shop computers.

Have you guys considered just upgrading to Intrepid? It puts in a whole new version of ALSA, and sound seems to be working fine in it.

---

### Post by Derath on 2008-12-04
I would say that it's definitely ALSA related, when I dist-upgraded there was a notice about the ALSA configuration files being different, when I chose to replace with the new config file, the sound worked again.

Basically, my suggestion would be to either: 1) dist-upgrade, or 2) if you don't want to run Intrepid, complete removal of all ALSA packages and reinstall them.

---

### Post by kougaru on 2008-12-04
Ok I think I'm having a different problem then the others. Since I tried changing the setting to auto with zero results.

I did find that changing the sound output to OSS I can hear sound correctly. ALSA and PULSE all I can hear are crackling sounds.

---

### Post by thomasaaron on 2008-12-04
It should be set to Pulse Audio. 
Then turn your PCM slider down.

---

### Post by kougaru on 2008-12-04
The PCM slider is all the way down, but all I continue to hear is crackling.

---

### Post by earrame on 2008-12-04
> **swizman said:**
> **Earrame**:
I wrote a shell script "sound_check.sh" to collect sound information.

Thanks swizman. I ran your shell script and looked at the results. I studied through the file and nothing caught my attention but that doesn't mean anything. Even the results of the diff command with your 'ok' file are beyond my ability to digest. I appreciate your efforts.

I was thinking about running the System76 > Restore. That has a decent probability of fixing what ever the issue is, yes?

What is Intrepid?

---

### Post by thomasaaron on 2008-12-05
Intrepid is Ubuntu 8.10.

Running the Intsall functionality of your System76 driver will do all that should need to be done to fix your sound.

If you're running Ubuntu 8.04 (Hardy), I'd recommend upgrading. That will definitely fix your sound.

---

### Post by kougaru on 2008-12-05
So far I've tried Restore and Install, but no luck. I'm still only getting crackles and pops.

---

### Post by thomasaaron on 2008-12-05
Koagaru, since you are using Intrepid already, please run two tests for me...

1. Plug in a set of speakers or headphones and see if you get crackles and pops there as well.

2. Try booting from a live Ubuntu CD and see if you get the same problem there.

These will confirm whether the problem is hardware or software/configuration.

---

### Post by kougaru on 2008-12-05
I plugged in some headphones but still got the crackling sounds. Then I booted my Ubuntu Live CD and successfully heard the Ubuntu music and test sounds.

I'm guessing it's a software issue then :\

---

### Post by thomasaaron on 2008-12-05
Yes, that's good news. If all else fails, you can just re-install.

Please double-click your speaker icon. In the resulting window, click the preferences button. Then make sure all available checkboxes are selected.

Then, for each tab of your sound control panel (the one with the sliders), take a screenshot and post it.

Also, please take a screenshot of System > Preferences > Sound.

---

### Post by kougaru on 2008-12-05
Here you go.

---

### Post by thomasaaron on 2008-12-05
Un-check IEC958 PCM
Turn your PCM slider up. It is the main amplifier for your system.

---

### Post by kougaru on 2008-12-05
Awesome! Sound works perfectly again! Thank You so much!

---

### Post by swizman on 2008-12-05
**Thomas:**

You recommend Hardy users to upgrade to Intrepid in order to solve the sound problem (see your post #22).

But Hardy is a LTS with a 3 year shelf life. 

It is not acceptable that Ubuntu kills the sound in Hardy with a security update after just 6 months of life.


Also, while I can confirm that upgrading to Intrepid fixes the sound problem, it also kills the following 3 things:

Cheese with Webcam
WiFi with static IP and WEP security
Skype while recording with Audacity

I do not feel that Ubuntu 'Just Works' right now as in the quote from their web page (
[http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)).

---

### Post by earrame on 2008-12-06
> **thomasaaron said:**
> If you're running Ubuntu 8.04 (Hardy), I'd recommend upgrading. That will definitely fix your sound.

Ahhh, Ibis. Intrepid Ibis. The first thing that comes to mind when I see 'Intrepid' is aircraft carriers. :) Sound is back. :) Screen resolution is gone. :(  But that's a topic for a different thread. Another recent thread seems to describe the exact condition I have after the upgrade although he arrived at it via a different route.

---

### Post by thomasaaron on 2008-12-08
> But Hardy is a LTS with a 3 year shelf life.

I understand. However, I'd guess 90 percent of Ubuntu users don't worry too much about that, as they tend to want the latest and greatest. LTS is of the most value, in my opinion, to people who are running several Ubuntu computers in their business, or Ubuntu server users. But if you want to stay with it, that's fine.

> It is not acceptable that Ubuntu kills the sound in Hardy with a security update after just 6 months of life.

I believe this is inaccurate. I've seen two cases so far of Hardy killing sound on System76 machines (to the point where I've not been able to resolve it). From a technical support perspective, this tells me that sound probably wasn't killed by an update, but by some configuration or software problem on your computer. Otherwise, I'd be inundated with these reports of this issue.

> Also, while I can confirm that upgrading to Intrepid fixes the sound problem, it also kills the following 3 things:

Cheese with Webcam
WiFi with static IP and WEP security
Skype while recording with Audacity

Cheese is indeed broken. Hopefully it will be fixed soon. Meanwhile, Skype and Ekiga do work fine.

Your Wifi issue is probably a configuration issue as well -- but, truthfully, I've not heard of this issue and so I've not been asked to investigate it. If you need it fixed, please post another thread on it.

Regarding Skype, you're probably right. There have been bug reports in the past about Skype hogging the sound card. I imagine this too will be resolved as Pulse Audio improves. And it has actually improved quite a bit from Hardy to Intrepid.

---

### Post by melonbug on 2008-12-10
My sound has been gone for a couple weeks now too. *sighs*

Also, I don't want to update to Intrepid yet either for those same reasons just stated. I am always on Skype, my fiance is over 4000 miles away. I cannot and will not lose my ability to see him. He updated to Intrepid and video does not work for him on Skype on it. Therefore he is in Windows all the time. =/

Any more suggestions??

---

### Post by thomasaaron on 2008-12-10
melonbug,

What System76 Model do you have?

Please follow these instructions:

First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.   

Fourth, take a screenshot of each tab of your Sound Control Panel (the one you get when you double-click the speaker icon) and post those screenshots here.

---

### Post by melonbug on 2008-12-10
> **thomasaaron said:**
> melonbug,

What System76 Model do you have?

Pangolin Performance (PAN-P4)

> Please follow these instructions:

First, run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot your computer.

Already done, multiple times since it happened, to no avail.

> Second, double-click on the speaker icon in the upper right corner of your screen. In the resulting Sound Control Panel, go to Edit > Preferences. (If you are using Ubuntu 8.10, you will have to click the Preferences button.) Make sure all available checkboxes have been selected. This will make more sliders available on the sound control panel. On the sound control panel, make sure that PCM, Master and Front (or whatever combination of these you have) are not turned down too low or muted.

Again, this is already done. Nothing is low or muted. 

And I'm using 8.04, like I said, I will not move to 8.10 until I know that the Skype/video issues are resolved.

> Third, go to System > Preferences > Sound. Make sure all drop-down selectors are set to ALSA. (If you are using Ubuntu 8.10, make sure all of them are set to Pulse Audio instead.) Click the first Test button to see if you now have sound.   

No, I don't.

> Fourth, take a screenshot of each tab of your Sound Control Panel (the one you get when you double-click the speaker icon) and post those screenshots here.

Ok...


Also, I've never been able to get my mic (the one in the laptop, or USB one that I also have) working.

---

### Post by thomasaaron on 2008-12-10
OK. Thanks. Those look pretty good.
I'm imaging a machine right now with Hardy to compare.

Please post the output of this command...

```
uname -r
```

Edit >>>> Just got it imaged. Mine looks a bit different than yours. In addition to uname -r, please take a screenshot of System > Preferences > Sound

---

### Post by melonbug on 2008-12-10
uname -r:
2.6.24-22-generic

---

### Post by thomasaaron on 2008-12-11
Hi, Melonbug.

I've got my PanP4 completely updated, with the System76 driver installed and implemented.

Kernel: 2.6.24-22-generic

My sound controls look just like yours with two exception: under switches, I have a checkbox for IEC958 Default PCM (which I suspect you will scroll down and find under Edit > Preferences). However, having that checked or unchecked does not kill sound.

Also, I do not have a 'Digital' slider, but that shouldn't have anything to do with sound OUTPUT.

Setting my controls up just like yours, I have sound.


So... What is the output of...
cat /proc/asound/version
For me it is: 1.0.17

Also, here is my /etc/modprobe/alsa-base file. Please post yours so we can compare:

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack-6ch-dig

---

### Post by thomasaaron on 2008-12-11
Also, are you using Skype or any other sound-card-using program as a start-up program? If so, remove it as a start-up program and reboot to see if your sound works.

---

### Post by melonbug on 2008-12-11
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Nov 25 2008 for kernel 2.6.24-22-generic (SMP).

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack-6ch-dig

Yes, Skype autostarts, however it was doing that since before I lost sound...? I suppose I could try anyway, though...

---

### Post by melonbug on 2008-12-11
Also:
> 
My sound controls look just like yours with two exception: under switches, I have a checkbox for IEC958 Default PCM (which I suspect you will scroll down and find under Edit > Preferences). However, having that checked or unchecked does not kill sound.

I don't have that option. I have everything checked, everything that can be there, is.

---

### Post by Frenziefrenz on 2008-12-11
That's identical, so that doesn't help much. :/

---

### Post by thomasaaron on 2008-12-11
Melonbug,

[SIZE="4"]**BINGO! Perfect!**[/SIZE]

You're running the wrong ALSA version. You have 1.0.16. The System76 Driver loads up 1.0.17.

GO to a terminal and run the System76 driver...

```
system76-driver
```

Press the Install Tab and the Install Button. When it's finished, copy and paste the terminal output, and let's see if it is getting stuck somewhere.

**NOTE: Make sure you are running the latest driver just for good measure. Here are instructions...**

> To install the System76 Driver, navigate to [http://planet76.com/repositories](http://planet76.com/repositories) and download the latest .deb package. It will be the one closest to the bottom of the page. Save the package to your Desktop and, when it has finished downloading, double-click it to launch the Gdebi installer. Then, click the install button.

Once the package has installed, you can open the System76 driver by going to System > Administration > System76 Driver. To install the drivers for your machine, Click the "Install" tab and the "Install" button. 

When the driver has finished running, reboot your computer.

After rebooting, run...

```
cat /proc/asound/version
```

...again and see if you have 1.0.17.

---

### Post by melonbug on 2008-12-11
Woo sound! Awesome awesome awesome thank you!

Now if only I could get my mic to work... >_>

---

### Post by thomasaaron on 2008-12-11
It'll work. Bump this tomorrow morning so I don't forget, and I'll post some screenshots.

---

### Post by melonbug on 2008-12-11
Ok new issue. Seems as though only one thing will utilize sound. Upon reboot, the normal startup noises sounded. Then Pidgin loaded, and the IM sounds worked. Loaded Skype, no noise off the vid on there. Played a youtube vid, that worked, and then the sound disappeared in the IMs on Pidgin...?!

---

### Post by thomasaaron on 2008-12-11
That's why I asked earlier if you were using Skype as a start-up program. There were some bugs a while back saying that Skype was hogging the sound card. That *may* still be going on.

---

### Post by melonbug on 2008-12-11
No see, Pidgin got sound. And then I opened youtube in Fx, and IT got sound. When I closed out Fx, then Pidgin got sound back. It's not Skype taking it, it's only one single app at a time getting use of it. =/

---

### Post by melonbug on 2008-12-12
So, any ideas now? =/

---

### Post by thomasaaron on 2008-12-12
That's probably not one I'm going to be able to solve. You should boot from an Intrepid live CD and see if you get the same problem there. Pulse Audio/ALSA tend to get better with each release.

---

