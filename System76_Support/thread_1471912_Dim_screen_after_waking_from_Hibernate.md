---
title: "Dim screen after waking from Hibernate"
date: 2010-05-03
forum: System76 Support
---

### Post by bakelitedoorbell on 2010-05-03
I put a fresh install of Ubuntu 10.04 on my Serp5 this past weekend. I have my Nvidia driver v173, the S76 driver, restricted extras, and 64-bit Flash installed okay.

One problem I'm having is that when I Hibernate, and then turn it back on, the screen is very dim.  Brightness is all the way down.  I can manually increase it by using Fn-F9.  In fact it seems to reset to less than zero because I have to push Fn-F9 three times before the brightness level starts to increase.  It's not happening with Suspend, only hibernate.

I remember this also happened when Karmic first came out, and was one of the reasons I decided to skip that release and stay with Jaunty.

Is there a setting I change to fix this?  Or what can I do to help troubleshoot why this is happening?

-----
Note - it also happens with suspend, just not every time!  I'm experimenting to see what triggers it.

Could this be bug# 451282?

---

### Post by isantop on 2010-05-04
Enable the backports and proposed updates (System > Administration > Software Sources, then click on the Updates tab and check the options there.) and run an update. 

If this still doesn't work, give me a holler.

---

### Post by bakelitedoorbell on 2010-05-05
isantop - thanks for the reply.  I did as you suggested, enabling those sources and running all the updates.

Unfortunately it had no effect on my problem, still have zero screen brightness after resuming from hibernation.

Also my wireless connection is a little flaky now, it's losing the connection and asking for my wep password now when it never did that before.  This is my main computer, so I'd prefer not to be at the bleeding edge.  Maybe I should put Jaunty back on it for now?

---

### Post by thomasaaron on 2010-05-05
Well, it's good that you have a workaround, anyway.

We'll have a look at the System76 Driver for Jaunty and see if we did something to fix this. If so, it should be easy to port the fix over. If not, we'll do some testing. Thanks for reporting this.

---

### Post by isantop on 2010-05-06
I don't think it's that bug, since that only seems to happen between boots.

Try removing the 173 version of the Nvidia driver, and installing the Version Current one. It might help your problem, and should do better off all around.

To do this, got to System > Administration > Hardware Drivers and wait for it to detect drivers. Then, click on version 173 of the driver and click "Remove." When that has finished, click on the Current version of the driver and click "Activate."

---

### Post by neu5eeCh on 2010-05-09
> **bakelitedoorbell said:**
> I put a fresh install of Ubuntu 10.04 on my Serp5 this past weekend. I have my Nvidia driver v173, the S76 driver, restricted extras, and 64-bit Flash installed okay.

One problem I'm having is that when I Hibernate, and then turn it back on, the screen is very dim.  Brightness is all the way down.  I can manually increase it by using Fn-F9.  In fact it seems to reset to less than zero because I have to push Fn-F9 three times before the brightness level starts to increase.  It's not happening with Suspend, only hibernate.

I remember this also happened when Karmic first came out, and was one of the reasons I decided to skip that release and stay with Jaunty.

Is there a setting I change to fix this?  Or what can I do to help troubleshoot why this is happening?

-----
Note - it also happens with suspend, just not every time!  I'm experimenting to see what triggers it.

Could this be bug# 451282?

Had the same problem. Here's a solution I found elsewhere. Seems to be a well-known bug that Canonical hasn't fixed yet.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by bakelitedoorbell on 2010-05-10
Hello Vermont Poet

The link you provided seems to be about a different problem, that of the Ubuntu logo being the wrong resolution during booting.  I have that as well, but I boot so rarely that it doesn't bother me.

My post here was about the screen brightness control being reset to zero when I resume from hibernate or suspend, with my new Lucid install.  For the time being I am just turning the brightness back up after resuming.  It makes me nervous though because I fear it could be a symptom of a greater problem with the nVidia driver.

---

### Post by isantop on 2010-05-11
Hey bakelitedoorbell,

Just checking in. Did using the current Nvidia Driver fix your problem?

---

### Post by bakelitedoorbell on 2010-05-13
> **isantop said:**
> Hey bakelitedoorbell,

Just checking in. Did using the current Nvidia Driver fix your problem?

Afraid not, I have the current version of the Nvidia driver and this is still happening.  My workaround is to just turn the brightness back up after resuming.  This never happened to me with Jaunty, so I'm pretty sure its not a hardware issue.

---

### Post by isantop on 2010-05-13
Can you please run ```
apt-cache policy system76-driver
``` from a terminal (Applications > Accessories > Terminal) and post the output?

---

### Post by bakelitedoorbell on 2010-05-13
OK, here it is

```
system76-driver:
  Installed: 2.4.8
  Candidate: 2.4.8
  Version table:
 *** 2.4.8 0
        500 http://planet76.com/repositories/ ./ Packages
        100 /var/lib/dpkg/status
     2.4.4 0
        500 http://planet76.com/repositories/ ./ Packages
     2.4.0 0
        500 http://planet76.com/repositories/ ./ Packages
     2.3.9 0
        500 http://planet76.com/repositories/ ./ Packages
     2.3.7 0
        500 http://planet76.com/repositories/ ./ Packages
     2.3.5 0
        500 http://planet76.com/repositories/ ./ Packages
     2.3.3 0
        500 http://planet76.com/repositories/ ./ Packages
     2.3.0 0
        500 http://planet76.com/repositories/ ./ Packages
     2.2.7 0
        500 http://planet76.com/repositories/ ./ Packages
     2.2.6 0
        500 http://planet76.com/repositories/ ./ Packages
     2.2.2 0
        500 http://planet76.com/repositories/ ./ Packages
     2.2.1 0
        500 http://planet76.com/repositories/ ./ Packages
     2.2.0 0
        500 http://planet76.com/repositories/ ./ Packages
     2.1.8 0
        500 http://planet76.com/repositories/ ./ Packages
     2.1.7 0
        500 http://planet76.com/repositories/ ./ Packages
     2.1.3 0
        500 http://planet76.com/repositories/ ./ Packages
     2.1.1 0
        500 http://planet76.com/repositories/ ./ Packages
     2.1.0 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.9 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.8 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.5 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.4 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.3 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.2 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.1 0
        500 http://planet76.com/repositories/ ./ Packages
     2.0.0 0
        500 http://planet76.com/repositories/ ./ Packages
     1.9.95 0
        500 http://planet76.com/repositories/ ./ Packages
     1.9.8 0
        500 http://planet76.com/repositories/ ./ Packages
     1.9.7 0
        500 http://planet76.com/repositories/ ./ Packages
     1.9.3 0
        500 http://planet76.com/repositories/ ./ Packages
     1.5.4 0
        500 http://planet76.com/repositories/ ./ Packages
     1.5 0
        500 http://planet76.com/repositories/ ./ Packages
     1.4 0
        500 http://planet76.com/repositories/ ./ Packages
     1.3 0
        500 http://planet76.com/repositories/ ./ Packages
     1.2.1.1 0
        500 http://planet76.com/repositories/ ./ Packages
     1.2.1 0
        500 http://planet76.com/repositories/ ./ Packages
     1.2 0
        500 http://planet76.com/repositories/ ./ Packages

```

---

### Post by bgreenaway on 2010-05-15
> **bakelitedoorbell said:**
> I put a fresh install of Ubuntu 10.04 on my Serp5 this past weekend. I have my Nvidia driver v173, the S76 driver, restricted extras, and 64-bit Flash installed okay.

One problem I'm having is that when I Hibernate, and then turn it back on, the screen is very dim.  Brightness is all the way down.  I can manually increase it by using Fn-F9.  In fact it seems to reset to less than zero because I have to push Fn-F9 three times before the brightness level starts to increase.  It's not happening with Suspend, only hibernate.

I remember this also happened when Karmic first came out, and was one of the reasons I decided to skip that release and stay with Jaunty.

Is there a setting I change to fix this?  Or what can I do to help troubleshoot why this is happening?

-----
Note - it also happens with suspend, just not every time!  I'm experimenting to see what triggers it.

Could this be bug# 451282?

I have the same problem with dim screen when coming out of hibernate.

---

### Post by kellywashere on 2010-05-16
I have the same problem. I found a related bug report here, you might find interesting:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451282](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451282)

Look for msg #26 and higher. I used the work-around described there. However, it still happens to me sometimes.
Could you please report the content of the following two files after having this problem (leave the brightness low when checking...):

/sys/devices/virtual/backlight/acpi_video0/brightness
/sys/devices/virtual/backlight/acpi_video0/actual_brightness
(the path may be slightly different on your system)

For me, these are BOTH reset to 0 after (long?) suspends. The suggested script in /etc/rc.local does set these files both to the maximum value on boot, but still the problem appears sometimes (the problem not being the files being out of sync, but BOTH of them being 0)

Kelly

---

### Post by kellywashere on 2010-05-16
Okay, forget what I said before about me still having the problem after the work around. I did some simple tests: turns out that for some reason my system does not run /etc/rc.local !

By the way, anybody a clue as to how that is possible? Properties are:
-rwxr-xr-x 1 root root 1406 2010-05-16 09:21 rc.local
so I guess it is still executable...
Its first line is
echo test > /home/kellywashere/test.txt
but the file is not created. Also, the brightness file is still 0 after startup, while actual_brightness is 10.
Maybe I should file a separate question about not running rc.local though...

---

### Post by jdb on 2010-05-16
> **kellywashere said:**
> Okay, forget what I said before about me still having the problem after the work around. I did some simple tests: turns out that for some reason my system does not run /etc/rc.local !

By the way, anybody a clue as to how that is possible? Properties are:
-rwxr-xr-x 1 root root 1406 2010-05-16 09:21 rc.local
so I guess it is still executable...
Its first line is
echo test > /home/kellywashere/test.txt
but the file is not created. Also, the brightness file is still 0 after startup, while actual_brightness is 10.
Maybe I should file a separate question about not running rc.local though...

Are you running the test after a reboot are after a hibernate/suspend?
rc.local is not invoked after a hibernate/suspend.

jdb

---

### Post by isantop on 2010-05-17
For the people who are having this problem:

Please run ```
lsmod
``` from a terminal (Applications > Accessories > Terminal), suspend, then run it again. Post the output here for both times.

---

### Post by bakelitedoorbell on 2010-05-17
After a fresh reboot:
/sys/devices/virtual/backlight/acpi_video0/brightness
/sys/devices/virtual/backlight/acpi_video0/actual_brightness
Both are equal to 7, which is all the way up.

lsmod gives me this:
```
ubob@ubob-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11072  0 
snd_hda_codec_si3054     4236  1 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  4 
snd_hda_codec          85727  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
arc4                    1473  2 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
jmb38x_ms               8643  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                121577  0 
snd                    70978  20 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlcore               124955  1 iwlagn
mac80211              238128  2 iwlagn,iwlcore
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
psmouse                64608  0 
serio_raw               4918  0 
memstick               10121  1 jmb38x_ms
cfg80211              148386  3 iwlagn,iwlcore,mac80211
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  2 iwlcore,sdhci
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  0 
nvidia              10799466  40 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
r8169                  39554  0 
mii                     5237  1 r8169
ieee1394               94675  1 ohci1394
ahci                   37646  3 
```

Then I clicked the power icon in the upper right corner and selected Hibernate from the menu.  Waited for it to go all the way to sleep.  Then pushed the physical power button to wake it up, typed my password.  Screen is now dim.

/sys/devices/virtual/backlight/acpi_video0/brightness
/sys/devices/virtual/backlight/acpi_video0/actual_brightness
Both are now equal to 0.

lsmod now says:
```
ubob@ubob-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11072  0 
snd_hda_codec_si3054     4236  1 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  4 
snd_hda_codec          85727  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
arc4                    1473  2 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
jmb38x_ms               8643  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlagn                121577  0 
snd                    70978  20 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlcore               124955  1 iwlagn
mac80211              238128  2 iwlagn,iwlcore
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
psmouse                64608  0 
serio_raw               4918  0 
memstick               10121  1 jmb38x_ms
cfg80211              148386  3 iwlagn,iwlcore,mac80211
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
led_class               3732  2 iwlcore,sdhci
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  0 
nvidia              10799466  44 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
r8169                  39554  0 
mii                     5237  1 r8169
ieee1394               94675  1 ohci1394
ahci                   37646  3 
```

After this I pushed Function-F9 to turn it up so I can see what I'm doing.  What I said before about it being reset to less than zero was wrong, it just seemed that way because I was pushing the button faster than the brightness bar was moving.  Each Function-F9 does actually increase it by one eighth of the max like it should.

Thank you System76 for helping with this issue.  Do you have a Serp5 in the workshop that has this same issue?  By the way, I do feel fortunate that this is my only problem with 10.04 LTS!

---

### Post by Syphar on 2010-05-31
This isn't really a bug; more of an annoying feature. To fix it, go to Power Management Preferences, make sure the brightness is at the level you'd like it to stay at, then just click on "Make Default". It'll ask you for your password and what have you, then when it's done, it'll never go back down to zero brightness after waking up from sleep/hibernation.

---

### Post by PGScooter on 2010-05-31
only tested it once, but Syphar's solution worked for me. Thank you for posting! I have not tested with hibernate, only suspend.

---

### Post by bakelitedoorbell on 2010-06-05
> **Syphar said:**
> This isn't really a bug; more of an annoying feature. To fix it, go to Power Management Preferences, make sure the brightness is at the level you'd like it to stay at, then just click on "Make Default". It'll ask you for your password and what have you, then when it's done, it'll never go back down to zero brightness after waking up from sleep/hibernation.

Syphar - thanks for the suggestion.  I did this and unfortunately it did nothing for this problem on my computer.  The brightness is still reset to zero after resuming.

Some further information - the dim screen always happens the FIRST time I suspend after booting.  The second, third and so on suspend/resumes it is much less likely to happen, probably only 5-10% of the time.  So it is a minor bug but yes it's annoying.

In the "lsmod"s that I did earlier the only difference I see is the "nvidia" line changed from  40 to 44.  What do these numbers mean?

---

### Post by Flyers2391 on 2010-06-17
> **Syphar said:**
> This isn't really a bug; more of an annoying feature. To fix it, go to Power Management Preferences, make sure the brightness is at the level you'd like it to stay at, then just click on "Make Default". It'll ask you for your password and what have you, then when it's done, it'll never go back down to zero brightness after waking up from sleep/hibernation.

I thought the same thing but never bothered to look into how to change it.  I just updated my settings, thanks to your suggestion, and it works great!

---

### Post by nelliott71 on 2010-07-04
> **bakelitedoorbell said:**
> Syphar - thanks for the suggestion.  I did this and unfortunately it did nothing for this problem on my computer.  The brightness is still reset to zero after resuming.

I spent a few hours chasing a similar problem until I found [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1484156") explaining that the scripts in /etc/pm/sleep.d/ are called during both sleep and wake, they are passed different flags depending on the event.  I used the same method described there to set my screen to 100% brightness on resume.

The command I used to set my panel to 100% brightness: [FONT="Courier New"]**echo 100 > /proc/acpi/video/VGA/LCD/brightness**[/FONT]  (I understand from reading that the syntax may vary from one platform to another?)

So the complete fix for me was to create a script in /etc/init.d which I called 'fullbright'.  This script is simply:
```
#!/bin/sh
echo 100 > /proc/acpi/video/VGA/LCD/brightness

```

I created a second script in /etc/pm/sleep.d/, which I called 99-fullbright:
```
#!/bin/bash
case "$1" in
    thaw|resume)
        /etc/init.d/fullbright 2>/dev/null
        ;;
    *)
        ;;
esac
exit $?

```

This has fixed my problem, I hope it is useful to someone else as well.  :D

---

### Post by Scribble86 on 2011-11-02
the above post doesn't appear to work for me, running an nc4200 hp laptop on ubuntu 11.10 but I may have missed a step. Seems like putting a couple scripts in place also needs something to run them?

---

### Post by isantop on 2011-11-03
I'm not very familiar with HP's hardware. Perhaps your question would be better served in the General support section.

---

