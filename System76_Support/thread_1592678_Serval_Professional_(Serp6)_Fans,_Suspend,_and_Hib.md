---
title: "Serval Professional (Serp6): Fans, Suspend, and Hibernate"
date: 2010-10-10
forum: System76 Support
---

### Post by gbutler69 on 2010-10-10
I just recently purchase the Serval Professional (Serp6) laptop from System76. For the most part, everything has been smooth (aside from the issue with the 64-bit ATI drivers that was a problem with a change in the upstream kernel that the ATI PPA developers made a fix recently for). I am having a few issues I'd hope could be addressed:

    1. The fans run constantly, even though the I'm running the CPU Freq Scaling applets on the panel and have it set to "On Demand" which clocks down the CPU's to 933 MHz (53% of full speed). Is there a way to get the fans to run less? On my previous System 76 Model (PanV3) the Fan would only run full on (where I could really hear it), when the CPU's were running full-out.

    2. Suspend and Hibernate don't seem to work. There is some sort of error about disconnecting from USB and it never fully hibernates. Any ideas what the problem might be?

    3. The touch-pad is kinda hokey. I looked into it and the model that is installed does not support side/bottom vertical/horizontal scrolling. Instead, it has some kind of weird tap the corners thing to scroll vertically. Is there any way to improve this situation to have better functionality out of the touch-pad?

Any help on these issues would be greatly appreciated.


****** SOLVED THE HIBERNATE ISSUE / Touch Pad issue was misunderstanding how the Syntellic Touchpad worked, Fan issue solved (see responses in this thread *******

I've manged to solve my Hibernate problem finally. I did not follow your advice as I did not have time that I could afford to fiddling with it and the specific advice you were giving didn't seem to make sense to me (sorry).

That being said, I finaly got some time to spend on it and started googling around. I felt that the problem was somehow related to the size of my swap partition. I was thinking that maybe it needed to be block aligned or something like that (it was confirmed to be significantly large than RAM, so should have been sufficient for hibernate to work properly).

Googling around led me to this article (referencing Ubuntu 8.04) that seemed relevant[http://kerneltrap.org/node/22793]("http://kerneltrap.org/node/22793"),

This seemed to make sense and so I did the following:

** 1. edited /etc/initramfs-tools/conf.d/resume to have the same UUID as the UUID for my swap partition from /etc/fstab
** 2. ran the following command (as described in the above article):*sudo update-initramfs -u

I then clicked the "Hibernate" option and waited for the system to hibernate and power off. I then booted up and everything came back correctly from hibernate. Problem solved, YAY!

Now, this happened because I resized the hibernate partition (made it bigger) by booting with live CD and resizing partitions because I thought that was why hibernate wasn't working originally (when I first bought this laptop from you); however, going back and reviewing the forums and my e-mails to you, I can see that at around the same time, you fixed an issue with the System76 drivers that fixed the hibernate issue. Unfortunately, because I had resized the swap partition myself trying to fix the issue, once your driver was fixed I was still broken (because the partition resize changed the UUID of the swap partition). I knew to update the UUID in /etc/fstab, but, I had never heard of this /etc/initramfs-tools/conf.d/resume configuration.

Well, so that is the whole story. Hope this helps other customers you may have that may be experiencing a similar issue. If nothing else, it might be something worth adding to the knowledge base.

YAY! :D:D:D YAY! :KS:KS:KS :popcorn::popcorn:
[http://kerneltrap.org/node/22793](http://kerneltrap.org/node/22793)

---

### Post by isantop on 2010-10-12
Hi.

1. That's actually a know BIOS issue. We're working on getting it fixed up. For now, touching the "M" light above the keyboard should scale the ran back.

2. This is the second issue we've seen with suspend / hibernate on the SerP6. I think this is becoming a known issue as well.

3. The touchpad is actually not a synaptic model like those found in most other laptops. It's a sentellic model. I'm not sure if what you wanted is possible with the hardware, but you can install a configuration utility by following the instructions here: [http://knowledge76.com/index.php/Serp6](http://knowledge76.com/index.php/Serp6). Look under "Touchpad Configuration".

---

### Post by thomasaaron on 2010-10-14
On #2, did you do a fresh install of 10.10? If so, there is a known issue with Ubuntu not creating a large enough swap partition to accommodate hibernate.

---

### Post by gbutler69 on 2010-10-15
> **thomasaaron said:**
> On #2, did you do a fresh install of 10.10? If so, there is a known issue with Ubuntu not creating a large enough swap partition to accommodate hibernate.

No, I have not yet upgraded to 10.10 or done a fresh install. I'm still running the 10.04 it came with. Any other ideas?

---

### Post by gbutler69 on 2010-10-15
> **isantop said:**
> Hi.

1. That's actually a know BIOS issue. We're working on getting it fixed up. For now, touching the "M" light above the keyboard should scale the ran back.

2. This is the second issue we've seen with suspend / hibernate on the SerP6. I think this is becoming a known issue as well.

3. The touchpad is actually not a synaptic model like those found in most other laptops. It's a sentellic model. I'm not sure if what you wanted is possible with the hardware, but you can install a configuration utility by following the instructions here: [http://knowledge76.com/index.php/Serp6](http://knowledge76.com/index.php/Serp6). Look under "Touchpad Configuration".

Thanks for the answers. For clarification:

   1. What is the "M" and "W" buttons/lights at the top of the keyboard. I see them on my keyboard, I just had no idea what they are for.

   2. Does the suspend/hibernate have anything to do with USB3 perhaps? Thought I read something about that somewhere.

   3. Will the 10.10 upgrade perhaps make this situation better (i.e. the new Gesture support etc.)?

---

### Post by toddpedlar on 2010-10-29
> **gbutler69 said:**
> I just recently purchase the Serval Professional (Serp6) laptop from System76.

    2. Suspend and Hibernate don't seem to work. There is some sort of error about disconnecting from USB and it never fully hibernates. Any ideas what the problem might be?


I have also just purchased a Serval Pro, delivered last week with 10.10 installed.  The Suspend and Hibernate on my computer also don't seem to work.  I assumed (wrongly) that I was going to be able simply to close the lid on the machine and bring it home (I have it set to suspend on closure), but it rode home still powered on.  

This wouldn't be so bad, but when I open the lid after closing it, the machine is hung, and I have to "hard reset" by holding the power button down.  Don't like to do that, of course.

I also tried Hibernate and Suspend from the power menu - both had the same effect of freezing the machine. 

Help?! Is there any hope of this being fixed?  I really don't want to have to actually go the route of shutdown every time I want to move my machine from home to work and back.

---

### Post by pilbender on 2010-10-29
I'm with you here.  I have started a similar thread but have been unsuccessful.  You might want to check out what I've done as well although no one, including System 76 support, seems to have a solution.

[http://fostergrant.ubuntuforums.org/showthread.php?t=1578722](http://fostergrant.ubuntuforums.org/showthread.php?t=1578722)

---

### Post by PabloH on 2010-10-30
I have one with the Nvidia card on Lucid and it seems to work. Am I correct in assuming this is caused by 10.10 or does it have something to do with the ATI card?

I am looking to upgrade to get trim support for my SSD drive, but if I am going to loose hibernate, I will wait.

---

### Post by scottjspencer on 2010-10-31
I just got my new Serval last week, and I can say it's not exclusive to those with an ATI video card.  I have the new one with the Nvidia GeForce GTX 460M, and I can't get hibernate and suspend to work either.

It's not a huge deal for me, but I would be interested if anyone finds a solution.

---

### Post by pilbender on 2010-11-01
I'm not feeling so bad about immediately removing the default install since suspend doesn't seem to work for anyone else either.

I wish we could just get some hardware specs on this and we could just fix it ourselves.  What are the "quirks" settings or extra modules we need to compile into the kernel?  I'm willing to do it (and I have tried quite a few options already) but I have no idea which ones to use because I can't seem to identify the hardware itself.  

I already have to compile and install the wireless card modules separately.  If I knew which ones I needed for suspend to work, I could do those too :mad:

If anyone else has a made recent purchase of a Serval Professional and suspend is not working, they all should post that here because it needs to be fixed.  The System 76 guys are on this forum and they will see it.  It seems to be a fairly widespread problem.

I also have the Nvidia GeForce GTX 460M and I am running Ubuntu and Slackware on my Serval Pro.

---

### Post by cgerber on 2010-11-04
I just got mine yesterday. I closed the lid a few minutes ago. Now it's just a black screen. I figured there must be some sort of key combination to resume. No luck yet. I guess I'll just have to power it off.

---

### Post by pilbender on 2010-11-04
I don't know if anyone cares but I did an update of the wireless driver and it seems to work a lot better.  A new driver was released on 10-25-2010 from Realtek.  Here is the download link:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I was getting a lot of drops and intermittent connections before and I've had no problems now.

I still don't have suspend working.  I wish we had an update for that.

---

### Post by dayer4b on 2010-11-04
I'm having problems with suspend & hibernate as well.  I got a Serval Professional (serp6) 2 weeks ago.

I'm running Ubuntu 10.10.

I'm hoping this can get fixed soon, it kinda bothers me.

---

### Post by toddpedlar on 2010-11-09
> **dayer4b said:**
> I'm having problems with suspend & hibernate as well.  I got a Serval Professional (serp6) 2 weeks ago.

I'm running Ubuntu 10.10.

I'm hoping this can get fixed soon, it kinda bothers me.


Is anyone working on this at system76?  I'm starting to really be frustrated with this computer given that I have to manually shutdown every time I take the computer anywhere.  Granted it's fast shutting down and restarting - but I'd much rather just be able to close the lid and have it sleep, and wake up upon reopening.

---

### Post by pilbender on 2010-11-09
I don't see any movement on it, but that does not mean it is not happening.  I'm not sure where one would look to find out.

The wireless has been better but I still have to unload and load the wireless module periodically.  It's a frustrating thing too.  I'd settle for anything to fix this.  I'd even be willing to install new hardware.  

The laptop is great except for suspend not working and wireless dropping once in a while.

---

### Post by isantop on 2010-11-09
The suspend problems are a known issue, and we are working on fixing them. The issue is that it affects many different systems, and each computer seems to have its own severity on this. 

If anyone can make this occur, it would help out if they could cause it, then upon rebooting, open a terminal and run these commands: 
```
date
cat /var/log/pm-suspend.log
```

That would help in pinpointing the cause of this, especially on the Servals.

---

### Post by val67 on 2010-11-10
> **isantop said:**
> The suspend problems are a known issue, and we are working on fixing them. The issue is that it affects many different systems, and each computer seems to have its own severity on this. 

If anyone can make this occur, it would help out if they could cause it, then upon rebooting, open a terminal and run these commands: 
```
date
cat /var/log/pm-suspend.log
```

That would help in pinpointing the cause of this, especially on the Servals.

Hi isantop,
This is a step forward. At least you don't claim that suspend works "nearly flawless" on s76 anymore.

val.

---

### Post by pilbender on 2010-11-10
I'll be more than happy to help where ever I can.  I'll do this tonight as soon as I get home:

> date
cat /var/log/pm-suspend.logIs it best to post these things here or should we also be checking out another location or bug tracker?  I just want to make sure we are helping put the right information in the right place.

scott

---

### Post by isantop on 2010-11-10
Right here is fine, though we may be setting up a bug report in the future.

---

### Post by pilbender on 2010-11-10
As promised, the output of 

> 
date
cat /var/log/pm-suspend.log:


> 
scott@andromeda:~$ date
Wed Nov 10 19:31:43 MST 2010
scott@andromeda:~$ cat /var/log/pm-suspend.log
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Sat Nov  6 16:26:33 MST 2010: Running hooks for suspend.
/usr/lib64/pm-utils/sleep.d/00logging suspend suspend:Linux andromeda 2.6.35.7 #3 SMP Mon Oct 11 01:34:00 CDT 2010 x86_64 Intel(R) Core(TM) i7 CPU       Q 840  @ 1.87GHz GenuineIntel GNU/Linux
Module                  Size  Used by
r8192se_pci           504606  0 
joydev                  9959  0 
usbhid                 37684  0 
hid                    75900  1 usbhid
vboxnetadp              5073  0 
vboxnetflt             14811  0 
vboxdrv              1746089  2 vboxnetadp,vboxnetflt
snd_seq_dummy           1479  0 
snd_seq_oss            29892  0 
snd_seq_midi_event      5708  1 snd_seq_oss
snd_seq                52326  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          5441  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            39897  0 
snd_mixer_oss          16770  1 snd_pcm_oss
ipv6                  274380  77 
pcmcia                 36586  0 
pcmcia_core            13216  1 pcmcia
cpufreq_ondemand        8871  8 
acpi_cpufreq            6079  1 
freq_table              2467  2 cpufreq_ondemand,acpi_cpufreq
mperf                   1195  1 acpi_cpufreq
lp                      9877  0 
ppdev                   6149  0 
parport_pc             21182  0 
parport                29799  3 lp,ppdev,parport_pc
fuse                   64328  1 
snd_hda_codec_nvhdmi    14345  4 
nvidia              10024694  83 
snd_hda_codec_si3054     3902  1 
snd_hda_codec_realtek   267201  1 
snd_hda_intel          22107  5 
snd_hda_codec          74500  4 snd_hda_codec_nvhdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6254  1 snd_hda_codec
uvcvideo               60955  0 
snd_pcm                73094  5 snd_pcm_oss,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
cfg80211              146747  1 r8192se_pci
snd_timer              19575  3 snd_seq,snd_pcm
videodev               43734  1 uvcvideo
sdhci_pci               7234  0 
r8169                  39551  0 
ohci1394               29252  0 
snd                    57854  20 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
v4l1_compat            15434  2 uvcvideo,videodev
rtc_cmos                9342  0 
sdhci                  16463  1 sdhci_pci
jmb38x_ms               8086  0 
thermal                12841  0 
video                  19963  0 
processor              29923  9 acpi_cpufreq
i2c_i801                9110  0 
soundcore               5745  1 snd
mmc_core               56400  1 sdhci
thermal_sys            14278  3 thermal,video,processor
agpgart                29706  1 nvidia
v4l2_compat_ioctl32    11748  1 videodev
rfkill                 16442  1 cfg80211
snd_page_alloc          7233  2 snd_hda_intel,snd_pcm
psmouse                47969  0 
ieee1394               74842  1 ohci1394
sg                     26405  0 
led_class               2507  1 sdhci
mii                     3906  1 r8169
memstick                6910  1 jmb38x_ms
wmi                     7286  0 
output                  2020  1 video
hwmon                   1505  1 thermal_sys
evdev                   9067  14 
serio_raw               4502  0 
rtc_core               14663  1 rtc_cmos
button                  5013  0 
rtc_lib                 1946  1 rtc_core
battery                10407  0 
ac                      3185  0 
i2c_core               19698  3 nvidia,videodev,i2c_i801
ext4                  311099  0 
             total       used       free     shared    buffers     cached
Mem:       8164608    7904372     260236          0     633392    4560632
-/+ buffers/cache:    2710348    5454260
Swap:      8388604          0    8388604
success.
/usr/lib64/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/01grub suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/91wicd suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
Sat Nov  6 16:26:37 MST 2010: performing suspend
/usr/lib64/pm-utils/pm-functions: line 295: echo: write error: No such file or directory
Sat Nov  6 16:26:41 MST 2010: Awake.
Sat Nov  6 16:26:41 MST 2010: Running hooks for resume
/usr/lib64/pm-utils/sleep.d/99video resume suspend:Couldn't get a file descriptor referring to the console
Couldn't get a file descriptor referring to the console
Returned exit code 1.
/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib64/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib64/pm-utils/sleep.d/91wicd resume suspend:success.
/usr/lib64/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib64/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib64/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/01grub resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib64/pm-utils/sleep.d/00logging resume suspend:success.


---

### Post by isantop on 2010-11-12
Good news! We have this fixed! It was an issue related to USB 3 in newer Servals. The fix will be coming down in the System76 Driver in a few days. When it comes, simply update to and run the latest driver to enable the fix.

---

### Post by pilbender on 2010-11-14
I'm absolutely elated about this.  Is it possible to gain access to the original source for this driver?  I can break apart the driver from the .deb file, but I'd rather not have to if the original source is made available.  Then we can use it outside the .deb packaging.  Is the driver available as a new module loaded into the kernel for USB 3 or was it some other tweak that had to be made?  Is it something that will end up upstream in the kernel from kernel.org?

I think there are a lot of people who would be interested in the Serval if they knew they didn't have to run Ubuntu to make this work.  I count myself as one of them.  I have a Ubuntu installed on a separate partition now just to test these things, but my primary system will always be Slackware.  General hardware compatibility is the reason I bought mine in the first place.

Please let us know as soon as this is available.  I will be happy to test, offer feedback and/or troubleshoot as needed to make this work.

Thanks for working on this for us.

scott

---

### Post by isantop on 2010-11-15
I can make an archive of the files it installs (which are all in python), that you can use to extract the original driver. It might be easier and faster to install the latest driver on your Ubuntu Partition and copy over the contents of /opt/system76.

I'll be sure and post an update when that driver comes down.

---

### Post by pilbender on 2010-11-15
Thanks, it's very much appreciated.  I'll see what I can do to extract things myself.  If I need some assistance, I'll post back here.

If I'm successful, I'll let others know how I did it.

---

### Post by pilbender on 2010-11-28
I'm dying for some updates on this :biggrin:

I also had some other bad behavior but I think it's upstream with the X server.  Don't really know.  It could also be the Nvidia driver or the BIOS... 

Once in a while (like once every few days) my display freezes.  I've seen this before with other systems, that is other distros and other hardware.  The mouse stops moving the display freezes but whatever was showing still shows, the keyboard no longer works, and only a hard reset will fix it.

The other weirdness is on boot up, sometimes the keyboard will not work.  So I can't enter my password to unlock Luks.  Again, a hard reset is the only way out.  The next time is usually okay, although occasionally it happens twice in a row.

I don't think this is necessarily an System 76 issue.  Some of this is likely attributed to needing some updates on the BIOS and some if it may be upstream in other packages.

Generally, Linux serves me well, but some of these issues are embarrassing and downright irritating.  A BIOS update and many other updates eventually fixed my old Dell Latitude D630 when it was doing this.  I haven't had trouble with that system in almost 2 years now.

---

### Post by gbutler69 on 2010-11-28
> **isantop said:**
> Good news! We have this fixed! It was an issue related to USB 3 in newer Servals. The fix will be coming down in the System76 Driver in a few days. When it comes, simply update to and run the latest driver to enable the fix.

I just updated to the latest System76 Driver. It is NOT fixed. It does shut-down when I select Hibernate now, as opposed to complaining about USB3 being unable to freeze, but, when I turn it back on, it boots up to a normal login rather than to by session.

I have to say, at this point I'm pretty upset. I've purchased 4 laptops from System76 in as many years and have been fairly happy with my purchases up to this point. I have to say though, that this Serval Professional is turning out to be a lemon. I purchase from System76 believing I am getting hardware that has been properly tested with Ubuntu Linux and is 100% compatible. I even pay extra for the support.

As it stands, I'm hearing a not of "well, Ubuntu really isn't compatible with this hardware....". I'm having issues with the Suspend/Hibernate, the touchpad, the Fans, and I had issues with the ATI video when I first received it.

If I could return it I would. I'm reall fairly disappointed with the entire experience. For the $2,200.00+ I paid, I'd expect to have a much better and smoother experience than this.

If I wanted these kinds of difficulties, I would use random hardware and run Gentoo on it.

If my tone seems angry or upset, well, that's because I am. Consider me an UNHAPPY CUSTOMER! :mad::mad::mad::mad: :(:(:(

---

### Post by gbutler69 on 2010-11-28
> **pilbender said:**
> 
...

I don't think this is necessarily an System 76 issue.  Some of this is likely attributed to needing some updates on the BIOS and some if it may be upstream in other packages.

...


In what way exactly are either the need for a BIOS update or hardware incompatibility not a System76 issue? I purchased from System76 with the understanding that the hardware would run Ubuntu without any issues. If I wanted to figure things out and rely on upstream to fix it, I would buy random hardware, not from a company selling laptops with Ubuntu pre-installed.

---

### Post by pilbender on 2010-11-29
> In what way exactly are either the need for a BIOS update or hardware incompatibility not a System76 issue? I purchased from System76 with the understanding that the hardware would run Ubuntu without any issues. If I wanted to figure things out and rely on upstream to fix it, I would buy random hardware, not from a company selling laptops with Ubuntu pre-installed.

I can't disagree with your statement here.  I too paid over $2,000 for my laptop and I too bought it for the same reasons.  I too have been enormously disappointed because I was looking for a better experience.  I really wanted to just do my work on my laptop and not have to mess around like this.  I'd be lying if I said I wasn't angry about it.  As my first laptop purchase from System 76, I'd be hesitant to buy another one because the experience has not been better than other laptops and in many ways the experience has been much worse.  I feel like I was taken.  My Dell D630 works perfectly (like a Mac) but it just wasn't powerful enough for the work I was doing.  So I bought this thinking I was doing a good thing.

On the other hand, I have it now.  I need this machine for my work and I'm not going to return it.  If it was just a consumer device I would have returned it already.  It took 2 weeks to get here and I can't afford to not have a powerful machine right now.  Also, I spent all my money on it so I can't afford to upgrade my desktop adequately at the moment.  Believe me, if I could go back, I would just have upgraded my desktop and done something else on my laptop later.

The reason I mentioned upstream is because most resellers of laptops or other hardware go through common suppliers.  So this is more than likely System 76 branded hardware purchased through another vendor which sells to lots of companies like System 76.  So there is an upstream (more than likely) for the hardware.  Also, the BIOS is a common component shared and purchased amongst many vendors.  The X server and NVidia drivers also have upstream responsibilities, obviously.

So I'm all in on this and I really want it to work.  And I'll do anything I have to do to make it work.  Including not getting mad about it because that doesn't solve the problems.  But that doesn't mean I'm happy about it.  And it certainly doesn't mean I like it.

---

### Post by isantop on 2010-11-30
gbutler69's issues actually are not related to the issue fixed in the new System76 Driver, which was related to suspend. The machine now suspends and resumes perfectly.

Our in-shop testing machine hibernates and wakes up fine. Can anyone else replicate the hibernate issue in Ubuntu 10.10?

---

### Post by pilbender on 2010-12-01
> I just updated to the latest System76 Driver. It is NOT fixed. It does shut-down when I select Hibernate now, as opposed to complaining about USB3 being unable to freeze, but, when I turn it back on, it boots up to a normal login rather than to by session.

> gbutler69's issues actually are not related to the issue fixed in the new System76 Driver, which was related to suspend. The machine now suspends and resumes perfectly.

So the driver for fixing suspend did come out?  I checked last weekend and I didn't see any fixes that worked for me.  Shall I update again?

Personally, I'd be okay with only suspend working (I think, depends on how long the battery would last with it).  I don't use Hibernate myself.  I'm mainly looking at being able to shut my lid and throw it in my bag without having to restart all my stuff, which takes at least 10 minutes even on this fast machine.  The shutdown and start up is miserable for someone like me.  I never shut down my stupid Dell.  Thank God.  It would be almost useless if I had to shut down a slow machine.  Since it suspends, it's actually quite convenient for some things.

---

### Post by isantop on 2010-12-01
That's right. As of System76 Driver v. 2.5.9, the suspend issues on the Serval are fixed, and updating/running the new driver should get suspend working for you.

---

### Post by pilbender on 2010-12-02
> **isantop said:**
> That's right. As of System76 Driver v. 2.5.9, the suspend issues on the Serval are fixed, and updating/running the new driver should get suspend working for you.

I was able to get this to work on Ubuntu.  But not without some headache first.  I did the update and it did not work.  Then I did a reset to factory and it sort of worked but I lost the display.  Finally, I downloaded the NVidia driver from their site, dropped down to runlevel 2 and ran it despite warnings about running the installer at that runlevel.  Then I rebooted since I couldn't figure out how to get things back to normal (which is why I hate Ubuntu).

After doing all this, suspend finally worked.  That Beta Nvidia driver I got from the Ubuntu software updates was no good, I had to force the NVidia driver I downloaded directly from them.  Also had to do the "reset" for the System 76 driver.

That's step one.  Step two is to make it work in Slackware.  I read through a bunch of the python scripts and I was unable to see what was happening to make suspend work.  I'll do some more digging later, but I would appreciate a hint on what was changed.  I tried some of the kernel parameters in the python file and didn't get anywhere.

Is it possible to ping a developer and find out exactly what made suspend work?

---

### Post by scottjspencer on 2010-12-03
I can confirm that the update allows me to use suspend.  (Hibernate always worked, I think.  I don't really use it much, but I haven't had a problem with it.)

Suspend now works near flawlessly.  Occasionally, it will fail to resume after I open the lid, but that has only happened twice since the update (so, around once a week).

---

### Post by pilbender on 2010-12-03
From what I can gather the only change was kernel boot parameters. The rest of the changes I saw were to other models and hardware.  I added this to my lilo.conf file:
append=" acpi_os_name=Linux,acpi_osi=Linux,vt.default_utf8=0"

I also tried this:
append=" acpi_osi=\"!Windows 2006\" vt.default_utf8=0"

Originally it was this:
append=" vt.default_utf8=0"

Doesn't seem to make a difference though.  Is there something else I'm missing here?

scott

---

### Post by isantop on 2010-12-03
The different system patches are in driverscontrol.py. In there is a complete list of every System76 model the driver supports, and what needs to be done. For the SerP6:

```
    elif modelname == ('serp6'):
        ...
        elif version == ('10.10'):
            acpi.xhcihcdModule()
```

So, you'll want to check the file called acpi, and in that file, the xhcidhcdModule function:

```
def xhcihcdModule():
    """Unload the NEC USB 3.0 module prior to suspend"""
    os.system('sudo rm /etc/pm/config.d/suspend_modules')
    os.system('echo "SUSPEND_MODULES=\"xhci-hcd\"" | sudo tee -a /etc/pm/config.d/suspend_modules')
    os.system('sudo chmod +x /etc/pm/config.d/suspend_modules')
```

So, to fix suspend on the SerP6, open a terminal and run:

```
sudo rm /etc/pm/config.d/suspend_modules
echo "SUSPEND_MODULES=\"xhci-hcd\"" | sudo tee -a /etc/pm/config.d/suspend_modules
sudo chmod +x /etc/pm/config.d/suspend_modules
```

Note that your directories may be different, since these are for Ubuntu, but they should be pretty close.

---

### Post by pilbender on 2010-12-03
Thank you for posting this.  Your extra detail was certainly adequate.  I was able to make the modification which really just boils down to creating the file, "suspend_modules" and adding:

SUSPEND_MODULES=xhci-hcd

I put this file in /etc/pm/config.d on Slackware, but the problem is I don't have that module loaded in Slackware so it's not the issue in my case.

Perhaps there is some other module that won't unload, I don't know.  I will likely study the list of loaded modules when each is booted up to try and narrow down the possibilities.

But still no suspend for Slackware ](*,)

---

### Post by pilbender on 2010-12-05
So I've gone through many of the modules and done some experiments with no real results.  I'm learning though.

I perused the logs when I was putting the system into suspend and it appears to be pretty verbose and helpful.  Here's what I have so far:

```

Initial commandline parameters: 
Sun Dec  5 12:40:51 MST 2010: Running hooks for suspend.
/usr/lib64/pm-utils/sleep.d/00logging suspend suspend:Linux andromeda 2.6.35.7 #3 SMP Mon Oct 11 01:34:00 CDT 2010 x86_64 Intel(R) Core(TM) i7 CPU       Q 840  @ 1.87GHz GenuineIntel GNU/Linux
Module                  Size  Used by
hidp                   13700  1 
hid                    75900  1 hidp
vboxnetadp              5073  0 
vboxnetflt             14759  0 
vboxdrv              1746203  2 vboxnetadp,vboxnetflt
snd_seq_dummy           1479  0 
snd_seq_oss            29892  0 
snd_seq_midi_event      5708  1 snd_seq_oss
snd_seq                52326  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          5441  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            39897  0 
snd_mixer_oss          16770  1 snd_pcm_oss
rfcomm                 37416  4 
sco                     8940  2 
bridge                 73257  0 
stp                     1624  1 bridge
llc                     3816  2 bridge,stp
bnep                   10538  2 
l2cap                  40360  21 hidp,rfcomm,bnep
btusb                  11433  4 
bluetooth              50703  10 hidp,rfcomm,sco,bnep,l2cap,btusb
ipv6                  274380  44 
pcmcia                 36586  0 
pcmcia_core            13216  1 pcmcia
cpufreq_ondemand        8871  8 
acpi_cpufreq            6079  1 
freq_table              2467  2 cpufreq_ondemand,acpi_cpufreq
mperf                   1195  1 acpi_cpufreq
lp                      9877  0 
ppdev                   6149  0 
parport_pc             21182  0 
parport                29799  3 lp,ppdev,parport_pc
fuse                   64328  1 
nvidia              10024694  83 
snd_hda_codec_nvhdmi    14345  4 
snd_hda_codec_si3054     3902  1 
snd_hda_codec_realtek   267201  1 
snd_hda_intel          22107  2 
r8192se_pci           504606  0 
snd_hda_codec          74500  4 snd_hda_codec_nvhdmi,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
thermal                12841  0 
uvcvideo               60955  0 
sdhci_pci               7234  0 
sdhci                  16463  1 sdhci_pci
snd_hwdep               6254  1 snd_hda_codec
cfg80211              146747  1 r8192se_pci
snd_pcm                73094  4 snd_pcm_oss,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
videodev               43734  1 uvcvideo
snd_timer              19575  2 snd_seq,snd_pcm
v4l1_compat            15434  2 uvcvideo,videodev
mmc_core               56400  1 sdhci
psmouse                47969  0 
snd                    57854  16 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
ohci1394               29252  0 
v4l2_compat_ioctl32    11748  1 videodev
processor              29923  9 acpi_cpufreq
video                  19963  0 
rtc_cmos                9342  0 
serio_raw               4502  0 
evdev                   9067  17 
led_class               2507  1 sdhci
soundcore               5745  1 snd
jmb38x_ms               8086  0 
button                  5013  0 
i2c_i801                9110  0 
ieee1394               74842  1 ohci1394
thermal_sys            14278  3 thermal,video,processor
r8169                  39551  0 
agpgart                29706  1 nvidia
rfkill                 16442  3 bluetooth,cfg80211
output                  2020  1 video
snd_page_alloc          7233  2 snd_hda_intel,snd_pcm
rtc_core               14663  1 rtc_cmos
battery                10407  0 
ac                      3185  0 
rtc_lib                 1946  1 rtc_core
wmi                     7286  0 
mii                     3906  1 r8169
i2c_core               19698  3 nvidia,videodev,i2c_i801
memstick                6910  1 jmb38x_ms
hwmon                   1505  1 thermal_sys
sg                     26405  0 
ext4                  311099  0 
             total       used       free     shared    buffers     cached
Mem:       8164608    1175320    6989288          0      32228     243748
-/+ buffers/cache:     899344    7265264
Swap:      8388604     144616    8243988
success.
/usr/lib64/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/01grub suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/91wicd suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib64/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
Sun Dec  5 12:40:54 MST 2010: performing suspend
/usr/lib64/pm-utils/pm-functions: line 295: echo: write error: No such file or directory
Sun Dec  5 12:40:55 MST 2010: Awake.
Sun Dec  5 12:40:55 MST 2010: Running hooks for resume
/usr/lib64/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib64/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib64/pm-utils/sleep.d/91wicd resume suspend:success.
/usr/lib64/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib64/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib64/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/01grub resume suspend:not applicable.
/usr/lib64/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib64/pm-utils/sleep.d/00logging resume suspend:success.
Sun Dec  5 12:40:58 MST 2010: Finished.

```

I'm making a total guess here as I'm pretty far from an expert in this, but it seems there is a timing issue of some kind because this location exists.

---

### Post by jamiekrug on 2010-12-17
I can confirm that the System76 Driver v. 2.5.9 did NOT resolve my SerP6 resume problems. I've confirmed that I do have SUSPEND_MODULES=xhci-hcd in my /etc/pm/config.d/suspend_modules file. I suspend/resume at least twice per day, and I've gone as much as 2 or 3 weeks without issue, but last week resume failed two days in a row.

It's intermittent, but it's painfully annoying when it happens. I've reviewed tons of logs, and basically, I can find NOTHING logged at the time of failed resumes. It's as if the hardware knows to light the lights and spin the fan, but the kernel knows nothing of an intended resume. The display remains completely black on failed resumes--no flicker or anything. No key combinations do anything. I've waited for 15+ minutes with no change. I see no hard drive activity whatsoever.

I'm no expert in this area, but I'm eager to help, if I can. Any advice would be most welcome! Just [like pilbender]("http://ubuntuforums.org/showpost.php?p=10177477&postcount=28"), I'm highly disappointed in my very expensive Serval Pro 6 purchase, but I'm all in, and I want it to get better. I have a Dell Vostro that's had none of the X and suspend/resume problems I've had with my System76 SerP6 (with both Ubuntu 10.04 and 10.10). I purchased it, because I thought I'd be able to avoid all of these issues. My Vostro is not powerful enough for most of my work, so I'm sticking this out too!

I also have a friend that made a nearly identical purchase around the same time as me, and he's experiencing the same issues. This is clearly a fairly widespread problem, so hopefully the System76 team will stick on this issue.

My laptop specs:
System76 Serval Pro (SerP6)
Ubuntu 10.10 (Maverick) 64-bit (clean install)
Core i7-840QM Processor ( 45nm, 8MB L3 Cache, 1.86GHz )
Memory 8 GB - DDR3 1333 MHz
Nvidia GeForce GTX 285M Graphics with 1GB GDDR3 Video Memory
160 GB Intel X25-M Solid State Drive
802.11 B+G+N Wireless LAN Module

Thanks,
Jamie

---

### Post by hpng on 2010-12-18
I installed Ubuntu 10.10 on an older Shuttle motherboard.
It can SUSPEND but the fan still runs, unfortunately.

---

### Post by pilbender on 2010-12-18
Suspend seems to be working for me on my Ubuntu partition but I only have that for testing and debugging suspend.  I don't really use it for work.  One thing about it is you always have to turn bluetooth back on manually after suspend.  There's no way to tweak this in the BIOS.  I have to do this when I turn the machine on as well.

I've been having other problems that are not hardware related. I had a corrupted update and I've finally recovered from that.  That was not necessarily System 76's fault.  But there is some blame to go around on the wireless.  Doing any sort of updates on the system with wireless is precarious because it is so unreliable.

There are 2 major things that are still messing with me regularly.  

I've mentioned this before, but I install the wireless driver manually using the manufacturer's driver.  That driver still drops the wireless periodically and the have to unload and reload the module.  It's really bad.  It just falls on its face and if I catch it soon enough, I can usually reload the module before whatever I was doing times out.  This can happen several times a day.

Second thing is, of course, the suspend.  I haven't done anymore debugging due to the system being down for a few days.  I just set it aside and worked on another computer.  I had to get that work done and I was willing to work on a slow system to do it.  I upgraded my desktop RAM as a stop gap until I can afford to upgrade the rest of it for the work I'm doing.  Builds take 3 times as long compared to this laptop, but it works and that's better than nothing.

I'll remind everyone that I am primarily using Slackware.  That way I don't have to unnecessarily defame System 76 because *my* suspend is not working.  I wish the hardware itself was better vetted so standard Linux distros could be swapped out.  As I've said before, my Dell D630 works perfectly.

I also wish Ubuntu wasn't such a miserable distribution to use.  I would just switch to it.  But I'm developing a Web Application that uses MySQL, Tomcat load balanced with Apache, Sendmail, Bind, Memcached, Maven, Git and a few other things that come standard and unaltered with Slackware.  I actually need something standard like Slackware to stay out of my way.  The development tools are essential and Ubuntu makes all these things a pain because it is not a server oriented system.  Consumer oriented users might be satisfied with Ubuntu but I hate it with a passion.

I hope to get this working and if I figure out what is holding me up,  I'll be sure and let people know so they can benefit as well.

scott

---

### Post by pilbender on 2010-12-29
Okay boys and girls.... are you ready?  Suspend is working in Slackware!  Finally.  Shut the damn lid and go!  That's where we are at.  That's what I wanted so badly.

I referenced this thread to make it work:
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/getting-lenovo-w510-to-go-to-sleep-suspend-to-ram-812694/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/getting-lenovo-w510-to-go-to-sleep-suspend-to-ram-812694/)

Summary:
As root create a file called "unload_module" in /etc/pm/config.d and this is what goes in it:
```

SUSPEND_MODULES="xhci"

```

That's it.  If you have the rest of your settings configured properly just shut the lid or manually put it into suspend.  Remember, in Slackware the user doing the suspending must be in the "power" group.

I still have to manually turn Bluetooth back on, but that's minor compared to not having to boot the machine anymore.  In fact, I'm starting to wonder why I have Ubuntu installed ;-)  That might be wiped from this machine pretty soon.  It sucks anyway and it's buggy too.

So that about does it.  I think this machine is in pretty good shape.  I do need an auxiliary power supply though.  This one hour battery life is terrible for flying on trips.  It's a trade off though and I'd rather have a powerful machine than a long battery life (which is why I didn't buy a Mac among other reasons).

Something else interesting I discovered while traveling... someone had palm phone that could act as a wireless access point.  Long story short, we lost the Internet on Christmas Day and I had stuff I needed to do for work.  I was able to get on it and that palm phone saved me.  When I got home, I immediately rooted my Android to enable the same functionality.  It worked well but not on Slackware.

Turns out I was using Wicd to connect and it doesn't do Ad-Hoc, which is the mode the Android needs for this.  The Network Manager and its corresponding Applet did the trick.  So take out wicd and put in Network Manager for all the other Slackers that need to do this.  Network Manager is available as a Slackbuild on [http://slackbuilds.org](http://slackbuilds.org).

It was painful as hell these last couple of months but I think I've finally got this machine completely meeting my needs.

---

### Post by isantop on 2010-12-29
Looks like it was simply a matter of differences in driver nomenclature. Good to hear you're up and running.

---

### Post by pilbender on 2010-12-29
> **isantop said:**
> Looks like it was simply a matter of differences in driver nomenclature. Good to hear you're up and running.

Exactly.  But my errors in the logs were not pointing me towards *that* as being the problem.  So it was a little harder to find and figure out.  Maybe not for someone who knows what they are doing but for me it was tough.

---

### Post by pilbender on 2011-01-02
Just a little update for those that might be curious as to how well this is working.

So far things have been perfect.  I've had no issues whatsoever.  I shut the lid and go.  With Network Manager, I have to hook into the network manually by selecting it which is one nicer thing about Wicd.  (This has nothing to do with suspend, see my previous post) Also I have to turn on Bluetooth manually, but it is is a function key so this is pretty easy.  

In a way, having to switch on bluetooth manually is nice because you might not want it draining power if you are just checking something quick.

This is a really big deal for me.  I now leave Netbeans running, my app server running, Windows XP in a Virtual Machine running, Chromium, Thunderbird, IM, etc.  Everything just keeps on working.  No restarts are necessary on any process.  This is a huge savings on time and it increases flexibility.  I no longer hesitate to pick up my stuff and go because I don't have restart everything.  I just pick up where I left off as soon as I open the lid.

I guess the only other thing to keep in mind is I use Fluxbox for my window manager in case someone else uses KDE or Xfce and has issues.  I don't think there will be any issues but it's something to note.  I would also like to remind people that I use Luks encryption with Logical Volume Management.  There are docs in Slackware's distribution to help with this configuration.  But it means that all my stuff is safe and encrypted with AES 256, including my swap space.

Because the battery life is only 1 hour, I was looking into auxiliary external battery packs.  I don't really need one but it would be nice to have.  It appears difficult to find one that has enough juice to run this machine.  I have put in a couple of inquiries into different sites so we'll see what they come back and tell me.

Right now, this pack seems to be a good contender but the Wattage is slightly inadequate: [http://www.bixnet.com/bp170.html](http://www.bixnet.com/bp170.html)

The Serval power supply is 6.3 Amps at 19 Volts which means 119.7 Watts.  That bixnet battery automatically shuts off if the draw is more than 90 Watts.  So I'm guessing it won't be enough.  It would be nice to get at least 4 or 5 hours out of a battery for travel.  When I'm coding, 1 hour is just enough to really get rolling on something and then the battery is dead.  I don't travel much now, but I expect to in the future with the type of work I am starting to do.

I would even consider a custom made battery pack.  I will also look into this possibility.  Something thin about the size of the bottom of the laptop would work nicely but something commodity and external would probably be most economical and practical.

I'll post another update in a few weeks, but I expect it will be like my old Dell D630 where it stays up for months back and forth between offices.  Like I said, it has been working really well for 4 and half days already.

scott

---

### Post by pilbender on 2011-01-03
I think I jinxed it.  About 12 hours after I wrote yesterday's post, the wireless fell into oblivion.  Suspend still works fine and I tested that even after the wireless went down.

Normally, I can just reload the driver module but this time I couldn't get it back without a reboot.  It seems that this wireless driver/hardware has had issues for a year and this is not due to System 76:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585938](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585938)
You'll notice one of the developers from Realtek is also involved.

This thread talks about kernel panics but there are more issues with the wireless driver than just that.  Posts to this thread started last May and the most recent is December 31st, a few days ago.

I was up for over 5 days before this issue forced me to reboot.  I hope this continues to only be sporadic at worst.  I think it will get better if people continue to work on it.

---

### Post by pilbender on 2011-01-08
I was up for 4 days again, suspending and working happily.  Then I got a hard freeze.  No real reason why.  Only thing to do was a hard reset.  I suppose if the laptop is going to hard freeze, once every few days, this is acceptable.  

I'll update if this seems to be a chronic problem or not.  I'm a pretty hard user, I'm on my laptop 12 hours a day.  So I guess if there are issues, I'm going to find them :P

I'd say, in general, I'm quite pleased with things.  I'd like a longer battery life but I don't want a Mac.  

The only other thing I've had was some weirdness with the Microphone having really bad sound pick up.  This wasn't an issue before and I still haven't gotten down to the root of the problem.  I use Skype a lot so it's possible that it's giving me grief and not the hardware.

scott

---

### Post by toddpedlar on 2011-01-08
> **isantop said:**
> That's right. As of System76 Driver v. 2.5.9, the suspend issues on the Serval are fixed, and updating/running the new driver should get suspend working for you.

I have version 2.5.9 running, and suspend really doesn't do much of anything other than temporarily turn off the monitor.  

When I choose "Suspend" from the pulldown menu, the monitor turns off briefly and then the login box comes back up (same login box as if I had left the machine idle for a while and the screensaver came on)


When I hit the suspend button "Fn-F4", same thing as "suspend" from the pulldown menu.


When I close the lid, nothing happens to the blue power lights or anything - the monitor just seems to turn off, but the fans keep running.

The log file at /var/log/pm-suspend.log indicates something very strange - in the middle of the text, I find this:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jan  8 08:06:18 CST 2011: performing suspend
Sat Jan  8 08:06:20 CST 2011: Awake.
Sat Jan  8 08:06:20 CST 2011: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

Mind you I did NOTHING except hit the suspend button in this case.   The thing wakes immediately, having suspended for, oh, something like 2 seconds.

So this is what happens when suspend is "working"?

---

### Post by pilbender on 2011-01-08
You are on the right track.  Suspend does turn off those blue lights on either end, above the keyboard, below the monitor.

You can also configure those buttons, even the sleep button, to have different behavior.  Maybe you already did, but make sure those are configured to actually put it into sleep.

Check to make sure this file, /etc/pm/config.d/suspend_modules has this inside it:
```

SUSPEND_MODULES=xhci-hcd

```

That really ought to fix it on Ubuntu.  I'm attaching my Ubuntu log file so you can compare.  The earlier suspends in the log file did not work.  Those around December 25th (while I was gone on vacation) were working suspend actions.

Hope it helps.  Good luck!

scott

PS:  I forgot to mention, I had another hard freeze when I was doing my usual loading and unloading of the wireless drivers.  The freeze actually happened on the "modprobe" of the wireless driver.  We'll see if there is any correlation on the next one.

---

### Post by toddpedlar on 2011-01-08
> **pilbender said:**
> You are on the right track.  Suspend does turn off those blue lights on either end, above the keyboard, below the monitor.

You can also configure those buttons, even the sleep button, to have different behavior.  Maybe you already did, but make sure those are configured to actually put it into sleep.

Check to make sure this file, /etc/pm/config.d/suspend_modules has this inside it:
```

SUSPEND_MODULES=xhci-hcd

```

That really ought to fix it on Ubuntu.  I'm attaching my Ubuntu log file so you can compare.  The earlier suspends in the log file did not work.  Those around December 25th (while I was gone on vacation) were working suspend actions.

Hope it helps.  Good luck!

scott

PS:  I forgot to mention, I had another hard freeze when I was doing my usual loading and unloading of the wireless drivers.  The freeze actually happened on the "modprobe" of the wireless driver.  We'll see if there is any correlation on the next one.

Ah... I never noticed that was needed.  

Why in the world is this file not standard?

Thanks for the pointer.  I just suspended and it worked fine, and came back happily.  You don't know how much you've just positively impacted my work life :)  (well, yes, you do)

---

### Post by jamiekrug on 2011-01-08
> **pilbender said:**
> I was up for 4 days again, suspending and working happily.  Then I got a hard freeze.  No real reason why.  Only thing to do was a hard reset.  I suppose if the laptop is going to hard freeze, once every few days, this is acceptable. 

Scott: This is basically where I'm at with Ubuntu 10.10 64-bit on my Serval Pro. My laptop runs 10+ hours per day and sees an average of 2 suspend/resume cycles per day. Resume fails roughly once per week--but I've gone 2-3 weeks without issue, and I've also had multiple failed resumes in one day. I'm not sure "acceptable" is the word I'd choose, but I'm getting by without too much frustration ;-)

---

### Post by pilbender on 2011-01-09
> Ah... I never noticed that was needed. 

Why in the world is this file not standard?

Thanks for the pointer. I just suspended and it worked fine, and came back happily. You don't know how much you've just positively impacted my work life  (well, yes, you do)
Of course I do!  I'm so glad it helped because I know how you feel!  I don't know if it makes you feel any better but the file was not standard in Slackware either.  In fact it was missing for other people using other hardware and distributions as well.  That's how I stumbled across it in the first place.  It was truly a stumble because I was at a point where I was willing to try anything to make it work.

> Scott: This is basically where I'm at with Ubuntu 10.10 64-bit on my Serval Pro. My laptop runs 10+ hours per day and sees an average of 2 suspend/resume cycles per day. Resume fails roughly once per week--but I've gone 2-3 weeks without issue, and I've also had multiple failed resumes in one day. I'm not sure "acceptable" is the word I'd choose, but I'm getting by without too much frustration ;-)
I hear you!  That's why I posted about it.  I had a similar problem with my old Dell D630.  What finally ended up fixing it was a combination of flashing the BIOS and upgrading the kernel. It was over a year of putting up with it though.  I hope we don't have a similar experience with this model.  For the last year and a half that Dell would stay up for months at a time with twice daily suspend and resumes.  I personally think the BIOS update was the more critical fix because that model went through 15 BIOS updates that I know about.

Perhaps "livable" is a more appropriate term rather than "acceptable" ;-)

I still cannot seem to pin down what causes these random freezes.  The wireless module loading and unloading does not cause it, at least not by itself.  Again, I was seeing similar, weird wireless and suspend behavior on that old Dell until the BIOS flashing seemed to fix it permanently.  I'm very suspicious that the Serval could use the same thing.

---

### Post by jamiekrug on 2011-01-09
> **pilbender said:**
> I still cannot seem to pin down what causes these random freezes.  The wireless module loading and unloading does not cause it, at least not by itself.  Again, I was seeing similar, weird wireless and suspend behavior on that old Dell until the BIOS flashing seemed to fix it permanently.  I'm very suspicious that the Serval could use the same thing.

Since you mention "random freezes," I wonder which type you mean. My main problem is that my Serval fails to resume after a suspend, intermittently (again, once per week, at most). But I did recently have my first random freeze right after a successful resume. That's only happened once, so I'm calling it a fluke for now. The failure to resume is what's a drag, when that does occur. And when it does, there's absolutely NOTHING logged in any log file at that time, so seems difficult to troubleshoot???

---

### Post by pilbender on 2011-01-09
> Since you mention "random freezes," I wonder which type you mean. My main problem is that my Serval fails to resume after a suspend, intermittently (again, once per week, at most). But I did recently have my first random freeze right after a successful resume. That's only happened once, so I'm calling it a fluke for now. The failure to resume is what's a drag, when that does occur. And when it does, there's absolutely NOTHING logged in any log file at that time, so seems difficult to troubleshoot???

At this point they seem totally random.  There does not appear to be in correlation between the suspend operation and the freezes in my case.  So far, suspend/resume has not caused it.

Right now the wireless unloading and loading does not appear to be a correlation either, only a coincidence.  

I've only had 3 freezes since getting the suspend/resume working properly.  I consider the ones that happened before to no have value because there were other mitigating issues.  To be sure, I've had a couple dozen freezes or more, but I'm only keeping track now since the suspend/resume is working properly.

The other 2 freezes, were during normal work and I was not doing anything out of the ordinary when they happened.  This is the same behavior I saw with that old Dell D630.  I never did find exactly what would reproduce the condition.  But, eventually, all issues with it went away.  Possibly from kernel updates, but more likely, at least in my mind, from the BIOS updates.

---

### Post by pilbender on 2011-01-13
2 more random freezes, each requiring a hard reset.

First one was after 2 days, the second after only 1 day.  Both of these happened while I was away from the computer.  It was just sitting there with everything open as usual, but completely frozen.

This is trending in the wrong direction.  For me the frequency seems to be increasing.

---

### Post by pilbender on 2011-01-18
Another update...

Still getting totally random freezes.  I was speculating I might have had a file system corruption as a possible cause.  Just to be thorough, I reinstalled the core system and restored data from backup.  I also tried a couple of different kernels and the result was the same: Random freezes after about 2 to 4 days of use on average.

When the freeze happens the Caps Lock and the Scroll Lock indicators blink together and the display stays exactly as it was when the freeze started.  The computer requires a hard reset because the keyboard and mouse do not respond.

Still livable but sometimes this can happen at the worst possible times.

---

### Post by jamiekrug on 2011-01-18
> **pilbender said:**
> When the freeze happens the Caps Lock and the Scroll Lock indicators blink together and the display stays exactly as it was when the freeze started.  The computer requires a hard reset because the keyboard and mouse do not respond.

I'm no expert, but I was led to believe that the blinking caps/scroll lock indicators is a sign of a kernel panic, no? I recall reading some tricky things you could do to better log/debug something when that happens, but I was either too lazy or incapable of following through at the time ;-)

I had a freeze like this, with the blinking caps/scroll lock lights, just a couple weeks ago--however, this was the first and only time I've seen that in the 4-5 months that I've owned my Serval Pro.

---

### Post by pilbender on 2011-01-18
That's exactly why I posted this.  I really wanted to post some of the symptoms in case someone with knowledge and experience wanted to chime in.

When I had this issue in the past it seemed on only be fixed with a BIOS update.  I did think of the kernel panic idea and tried a few different kernels to see if there was a change.

There is also the Alt-SysReq R-E-I-S-U-B key combination: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

That didn't seem to make any difference though.  It did not work in this case.  Sometimes that used to work when I saw this issue in the past.

---

### Post by pilbender on 2011-01-18
That's exactly why I posted this.  I really wanted to post some of the symptoms in case someone with knowledge and experience wanted to chime in.

When I had this issue in the past it seemed on only be fixed with a BIOS update.  I did think of the kernel panic idea and tried a few different kernels to see if there was a change.

There is also the Alt-SysReq R-E-I-S-U-B key combination: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

That didn't seem to make any difference though.  It did not work in this case.  Sometimes that used to work when I saw this issue in the past.

---

### Post by pilbender on 2011-01-18
Hmm.  Double posted it.  More wireless fun!  You have to laugh about it a little.  Although I am getting sick of some of these things.

---

### Post by jamiekrug on 2011-01-19
> **pilbender said:**
> That's exactly why I posted this.  I really wanted to post some of the symptoms in case someone with knowledge and experience wanted to chime in.

When I had this issue in the past it seemed on only be fixed with a BIOS update.  I did think of the kernel panic idea and tried a few different kernels to see if there was a change.

There is also the Alt-SysReq R-E-I-S-U-B key combination: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

That didn't seem to make any difference though.  It did not work in this case.  Sometimes that used to work when I saw this issue in the past.

Well, I have some experience, but little knowledge concerning kernel panics :P I just recall that the two blinking indicator lights (Caps Lock and either Num or Scroll Lock) are a tell-tale sign of a kernel panic. I also recall reading a little about the Magic SysRq key combos, but I'm not sure they're expected to be effective in the case of a kernel panic (or maybe it depends on the type of panic?).

FWIW, I do remember now that my recent kernel panic coincided with me leaving an rsync command running to archive some files from my home directory to an external drive, via the eSATA port. I remember having a similar problem with my Dell Vostro 1510 when I left a backup job running--I'd often return from lunch to a kernel panic. I eventually narrowed it down to the Broadcom wireless module--when I turned off the wifi switch on my Dell, I never saw a kernel panic. So, this may be that same issue (probably not related to this thread?) back again, or something completely unrelated???

---

### Post by pilbender on 2011-01-19
> **jamiekrug said:**
> Well, I have some experience, but little knowledge concerning kernel panics :P I just recall that the two blinking indicator lights (Caps Lock and either Num or Scroll Lock) are a tell-tale sign of a kernel panic. I also recall reading a little about the Magic SysRq key combos, but I'm not sure they're expected to be effective in the case of a kernel panic (or maybe it depends on the type of panic?).

FWIW, I do remember now that my recent kernel panic coincided with me leaving an rsync command running to archive some files from my home directory to an external drive, via the eSATA port. I remember having a similar problem with my Dell Vostro 1510 when I left a backup job running--I'd often return from lunch to a kernel panic. I eventually narrowed it down to the Broadcom wireless module--when I turned off the wifi switch on my Dell, I never saw a kernel panic. So, this may be that same issue (probably not related to this thread?) back again, or something completely unrelated???

My old Dell D630 was the same.  It had wireless problems and freezes like this.  The wireless was fixed along with the freezes by BIOS updates.  On the freezes, it could have been the kernel as well, but I went down this path, that is trying different kernel versions, and things were not fixed until BIOS revision number 15 and I started on 2!

---

### Post by isantop on 2011-01-19
> **pilbender said:**
> Hmm.  Double posted it.  More wireless fun!  You have to laugh about it a little.  Although I am getting sick of some of these things.

Actually, I don't think that's wireless. There's been performance issues on the forums for a while now, and recently it's gotten so bad that they closed the non-support areas to help reduce the load on the servers. They're getting new hardware, which should be in soon.

About the freezes, the Alt+SysRq keys had no response? That's almost always a software issue. It's odd that it's persisting across kernel versions though.

---

### Post by pilbender on 2011-01-19
> **isantop said:**
> Actually, I don't think that's wireless. There's been performance issues on the forums for a while now, and recently it's gotten so bad that they closed the non-support areas to help reduce the load on the servers. They're getting new hardware, which should be in soon.

About the freezes, the Alt+SysRq keys had no response? That's almost always a software issue. It's odd that it's persisting across kernel versions though.

You could be right about the wireless.  Although it will just drop without notice and usually pick back up after a minute or so, forum or not.  I hit the submit button twice and it finally came back after 5 minutes.  My posts showed 5 minutes apart even though I hit the button in rapid succession.

I will continue to try the Alt-SysReq keys when this comes up and post back the results.  Freezes seem to be 2 to 4 days apart right now with similar symptoms I've seen on the Dell D630 in the past.

---

### Post by pilbender on 2011-01-30
Posting my obligatory update.  Hope no one is tired of hearing from me.  Too bad if you are, really :-)

I'm still getting random freezes averaging every other day.  I go though multiple suspend/resume cycles without issues.  I also switch from wireless to wired ethernet connections several times before it happens.

During each freeze, it seems I'm doing something different.  Sometimes during email, sometimes while editing source code (I'm learning to save my work constantly now), sometimes while using a browser, sometimes while I'm away from the computer.  In short, there is no pattern.

Also worth noting:  Some of the freezes happen with the Caps Lock and the Scroll Lock indicators blinking, sometimes not.  But the display always stays exactly as it was, totally frozen with no way to remote into the machine or use the keyboard or mouse.  A hard reset is *always* required.

I have to say, I'm really frustrated.  I hate this computer.  I like all the features, the keyboard, the mouse, the display, the processor and RAM, but, in general, I hate this machine.  The wireless sucks and the random freezes are almost intolerable.  The shore battery life is not so good either but I bought it knowing that.

If I had some money, I'd sell this thing and buy another computer.  The new Macs are out with the same processors as this thing now.  I wish I had one.  I'd wipe it and install Slackware with Fluxbox.  I hate the Mac interface, but I'd really like to have a *reliable* computer.  Even Windows machines have better uptime than this thing!  And that's pathetic.

Great hardware with some serious flaws.

---

### Post by isantop on 2011-01-31
Can you try it with Ubuntu? It could simply be that Slackware is not cooperating with the hardware.

---

### Post by pilbender on 2011-01-31
That could be, but I doubt it.  Others are reporting the same problems with Ubuntu.  If I have time, I'll test it, but I use this machine every day so I probably won't see it happen before I have to do work on it.

I'll do my best to help out with it though.

---

### Post by toddpedlar on 2011-02-03
> **isantop said:**
> Can you try it with Ubuntu? It could simply be that Slackware is not cooperating with the hardware.

Of late, my Serp6 running 10.10 has had the worst wireless ability I can remember.  If the signal isn't booming hot (i.e. if I'm not right next to the wirless hub, as I am in my lab, but not in my office) then I get intermittent to zero connection.   I do not recall this laptop being this bad when I first bought it (mid-November) but the last couple weeks (I haven't tracked upgrades so perhaps there was a bad one) suddenly it acts as though its got no wireless card at all.

---

### Post by isantop on 2011-02-03
> **toddpedlar said:**
> Of late, my Serp6 running 10.10 has had the worst wireless ability I can remember.  If the signal isn't booming hot (i.e. if I'm not right next to the wirless hub, as I am in my lab, but not in my office) then I get intermittent to zero connection.   I do not recall this laptop being this bad when I first bought it (mid-November) but the last couple weeks (I haven't tracked upgrades so perhaps there was a bad one) suddenly it acts as though its got no wireless card at all.

I think you may have a support issue. Please contact us at support...at...system76...dot...com

---

### Post by pilbender on 2011-02-04
I have to agree with Todd Pedlar.  My wireless is notoriously unreliable.  I don't do anything on wireless that matters.  I always find a place to plug in when I have to do a deployment from my laptop.  The wireless is pretty much guaranteed to fall on its *** several times a day.  Then I manually rmmod and modprobe the driver to bring it back up and sometimes that doesn't work either.

This is a small issue compared with the hard freezes every 2 days or so, give or take a day.

I see this laptop model was pulled from the site.  I have to applaud that action.  This laptop should *not* be sold to anyone.

I would even be interested in a trade in with some credit, but I'm not shelling out another $2,000 on the chance that the wireless and hard freezes are fixed on the new model.  There's no way I'm making another purchase this big without some guarantees.

Scott Smith

---

### Post by isantop on 2011-02-04
pillbender, would it be possible to try running a memory tester like MemTest86? It could simply be that one of your cards are bad, as this isn't an issue we're seeing with our SerP6 in the shop. You also might try reseating the memory cards, as they may have been bumped loose at some point.

---

### Post by pilbender on 2011-02-05
> **isantop said:**
> pillbender, would it be possible to try running a memory tester like MemTest86? It could simply be that one of your cards are bad, as this isn't an issue we're seeing with our SerP6 in the shop. You also might try reseating the memory cards, as they may have been bumped loose at some point.

I went ahead and installed MemTest86 to the boot loader and ran it.  It reliably freezes at "Test" 4%, "Pass" 0%.  

So, what should be my next course of action?  Should I try and open the laptop to re-seat the memory cards?  I really don't want to take it apart but if that will make it work, I'm willing to try it.  At this point, with the amount of time I've wasted on this machine, I'd rather dump it in the ocean.

By the way, I appreciate the added direction to getting some of this resolved.  I'm still totally disgusted, but at least there appears to be a reason for some of the behavior I'm seeing.

---

### Post by isantop on 2011-02-07
I'd go ahead and try that out, but if it doesn't work, then I think you probably have a bad card or two, and we can send you some new ones. Go ahead and contact us at support...at...system76...dot...com and we'll take care of it there.

---

### Post by pilbender on 2011-02-09
> **isantop said:**
> I'd go ahead and try that out, but if it doesn't work, then I think you probably have a bad card or two, and we can send you some new ones. Go ahead and contact us at support...at...system76...dot...com and we'll take care of it there.

Okay.  Sounds good.  I'll try it in a few days.  I'm travelling at the moment so I can't do anything with until I get home.

---

### Post by pilbender on 2011-02-12
I tried taking out the RAM and putting it back in and the results are the same.  I even switched the cards so each was in the other's slot.  Memtest freezes at 4%.

I'm emailing support now for new cards.

scott

---

### Post by babanner on 2011-02-13
I am willing to buy the newest Serval Professional this summer (what is its codename?) and I see so many problems people deal with this laptop. However, I see they have the old serval, not the new one with 2nd genration intel cpus and so on. These new servals, do they also have all these sorts of problems with suspend, hibernation, etc?

I would rather hear from a system76 representative. Thanks!

---

### Post by isantop on 2011-02-14
We haven't seen any issue with the new Serval/Gazelle in regards to Suspend/Hibernate issues. However, the models we're testing with do have the Chipset bug that's affected the Sandy Bridge units. We'll have to wait for the revised version before we can know for sure that the systems are okay.

---

### Post by pilbender on 2011-02-15
Just another update for those that might be curious and/or have the same issue....

I went ahead and did memtest86 tests on each RAM card individually in each of the memory slots and all tests fail.  I've already contacted support about it, but I suspect I'll be sending the laptop back because there appears to be a problem with the memory slots themselves.  I'm sure this would account for the random freezing with no consistent symptoms.

Others may want to test their memory as well if you are having random, unexplainable freezes.

---

### Post by gbutler69 on 2011-02-21
**** EDIT/UPDATE ****

I've manged to solve my Hibernate problem finally. I did not follow your advice as I did not have time that I could afford to fiddling with it and the specific advice you were giving didn't seem to make sense to me (sorry).

That being said, I finaly got some time to spend on it and started googling around. I felt that the problem was somehow related to the size of my swap partition. I was thinking that maybe it needed to be block aligned or something like that (it was confirmed to be significantly large than RAM, so should have been sufficient for hibernate to work properly).

Googling around led me to this article (referencing Ubuntu 8.04) that seemed relevant,

This seemed to make sense and so I did the following:

** 1. edited /etc/initramfs-tools/conf.d/resume to have the same UUID as the UUID for my swap partition from /etc/fstab
** 2. ran the following command (as described in the above article):*sudo update-initramfs -u

I then clicked the "Hibernate" option and waited for the system to hibernate and power off. I then booted up and everything came back correctly from hibernate. Problem solved, YAY!

Now, this happened because I resized the hibernate partition (made it bigger) by booting with live CD and resizing partitions because I thought that was why hibernate wasn't working originally (when I first bought this laptop from you); however, going back and reviewing the forums and my e-mails to you, I can see that at around the same time, you fixed an issue with the System76 drivers that fixed the hibernate issue. Unfortunately, because I had resized the swap partition myself trying to fix the issue, once your driver was fixed I was still broken (because the partition resize changed the UUID of the swap partition). I knew to update the UUID in /etc/fstab, but, I had never heard of this /etc/initramfs-tools/conf.d/resume configuration.

Well, so that is the whole story. Hope this helps other customers you may have that may be experiencing a similar issue. If nothing else, it might be something worth adding to the knowledge base.

---

### Post by gbutler69 on 2011-02-21
> **gbutler69 said:**
> I just updated to the latest System76 Driver. It is NOT fixed. It does shut-down when I select Hibernate now, as opposed to complaining about USB3 being unable to freeze, but, when I turn it back on, it boots up to a normal login rather than to by session.

I have to say, at this point I'm pretty upset. I've purchased 4 laptops from System76 in as many years and have been fairly happy with my purchases up to this point. I have to say though, that this Serval Professional is turning out to be a lemon. I purchase from System76 believing I am getting hardware that has been properly tested with Ubuntu Linux and is 100% compatible. I even pay extra for the support.

As it stands, I'm hearing a not of "well, Ubuntu really isn't compatible with this hardware....". I'm having issues with the Suspend/Hibernate, the touchpad, the Fans, and I had issues with the ATI video when I first received it.

If I could return it I would. I'm reall fairly disappointed with the entire experience. For the $2,200.00+ I paid, I'd expect to have a much better and smoother experience than this.

If I wanted these kinds of difficulties, I would use random hardware and run Gentoo on it.

If my tone seems angry or upset, well, that's because I am. Consider me an UNHAPPY CUSTOMER! :mad::mad: :(:(


**** EDIT/UPATE --- PROBLEM SOLVED!!! ****

I've manged to solve my Hibernate problem finally. I did not follow your advice as I did not have time that I could afford to fiddling with it and the specific advice you were giving didn't seem to make sense to me (sorry).

That being said, I finaly got some time to spend on it and started googling around. I felt that the problem was somehow related to the size of my swap partition. I was thinking that maybe it needed to be block aligned or something like that (it was confirmed to be significantly large than RAM, so should have been sufficient for hibernate to work properly).

Googling around led me to this article (referencing Ubuntu 8.04) that seemed relevant,

This seemed to make sense and so I did the following:

** 1. edited /etc/initramfs-tools/conf.d/resume to have the same UUID as the UUID for my swap partition from /etc/fstab
** 2. ran the following command (as described in the above article):*sudo update-initramfs -u

I then clicked the "Hibernate" option and waited for the system to hibernate and power off. I then booted up and everything came back correctly from hibernate. Problem solved, YAY!

Now, this happened because I resized the hibernate partition (made it bigger) by booting with live CD and resizing partitions because I thought that was why hibernate wasn't working originally (when I first bought this laptop from you); however, going back and reviewing the forums and my e-mails to you, I can see that at around the same time, you fixed an issue with the System76 drivers that fixed the hibernate issue. Unfortunately, because I had resized the swap partition myself trying to fix the issue, once your driver was fixed I was still broken (because the partition resize changed the UUID of the swap partition). I knew to update the UUID in /etc/fstab, but, I had never heard of this /etc/initramfs-tools/conf.d/resume configuration.

Well, so that is the whole story. Hope this helps other customers you may have that may be experiencing a similar issue. If nothing else, it might be something worth adding to the knowledge base.
:p:p:p

---

### Post by gbutler69 on 2011-02-21
Ooops, I forgot to include the URL for the Article I mentioned. The URL Is: [http://kerneltrap.org/node/22793](http://kerneltrap.org/node/22793)

This is where I found the stuff about /etc/initramfs-tools/conf.d/resume and the UUID of the swap partition etc.

---

### Post by gbutler69 on 2011-02-21
Ooops, I forgot to include the URL for the Article I mentioned. The URL Is: [http://kerneltrap.org/node/22793](http://kerneltrap.org/node/22793)

This is where I found the stuff about /etc/initramfs-tools/conf.d/resume and the UUID of the swap partition etc.

---

### Post by pilbender on 2011-02-28
I've had a couple of people send me personal inquiries as to the status of my Serp 6 and wanting to know what actually was happening.  I'm sorry to have checked out on people.  I'm working on a startup and I have 4 weeks left to implement an entire social media appplication... by myself minus the UI.  I'm very busy to say the least.

System 76 sent me a couple of RAM chips on the off chance that I might have 2 bad RAM cards.  It was a long shot but they were trying to be helpful in my situation by not making me send in the laptop to get it repaired.  It turns out that the issue is probably some place on the motherboard and I am going to have to send it in.  System 76 is even going to pay the postage.  Really good, friendly service.

But for me, in my current situation, I can't go without a computer. So I'm in the process of ordering another system.  After I get it and set it up to do my work, I will be sending in my Serp 6, along with all the extra RAM, for repairs.  I have decided to keep the hard disk because of confidentiality reasons and because I don't believe there are any issues with it.  I will then reinstall the hard disk after I get my laptop back.  I also don't want to go through the hassle of setting it up again and System 76 was fine with this proposition.

So, I'm waiting on the next system, which is a desktop I'm building from my chosen components.  I have pretty intense hardware requirements and building is much more economical than buying this caliber of hardware.  The system I'm building would be at least $3,000 to buy from a vendor and I absolutely need a lot of speed.  The parts are about $1,200 instead.  I can put this system together in an evening and be up and running before I go to bed that same night.  Hardware is easy, but setting up my development environment takes a lot of time.

So, I'll be sending in my Serp 6 in about a week after all my parts arrive.  I'm also throwing a thank you to System 76 for working with me and trying to get it all resolved in as short a time as possible.

---

### Post by pilbender on 2011-07-14
I'll try to keep things on topic because I've had a lot of other computer problems unrelated to the Serval.  A couple of hard drive failures in other systems, a power supply failure... in short, really poor luck lately.  I've actually had 4 hardware related failures in the last 2 months if you include the Serval: 2 at home, and one in a data center.

My Serval finally became totally unusable. I was limping along with it for 3 months.  So I built another system and sent the Serval in for repair.  Got it back in a little over 2 weeks.  It seems to work perfectly.  I'm still setting it up so I'm not using it regularly yet.

Thanks to System 76 for fixing it.  It was sorely missed.

I've also had a couple of inquiries on running Slackware on it.  Slackware runs perfectly.  Feel free to ping me if you have any questions about it.  I wiped out Ubuntu on mine.  I'm 100% Slackware.

---

