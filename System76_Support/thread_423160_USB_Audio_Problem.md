---
title: "USB Audio Problem"
date: 2007-04-25
forum: System76 Support
---

### Post by aay on 2007-04-25
I'm using a Gazalle Pro and I'm having problems with my Plantronics USB headset.

The headest works out of the box on an Edgy desktop I have, but it is not detected at all on my new install of Feisty onto this Gazzelle.

I know that this headset uses the generic usb audio driver, but what's strange is that it doesn't seem to be available.

When I run "cat /proc/asound/modules" I get:

 0 snd_hda_intel

Likewise when I run: "lsmod |grep snd" there is no entry for "snd_usb_audio"

If I try and do, "modprobe snd_usb_audio"

I get "FATAL: Module snd_usb_audio not found."

Why the heck would snd_usb_audio not be available?  I'm not sure if this is a Feisty problem or somethings specific to the Gazelle.  Does the System76 driver do anything to enable the onboard Intel sound card which would cause problems for this device?  

I've googled around a bit, and I've found a few people having problems with USB audio devices under Feisty, but not the number or problems I'd expect if it was a Feisty problem in general.

Anyone know about this or has anyone else gotten usb audio devices to work on a Gazelle using Feisty?

Thanks,

Adam York

---

### Post by aay on 2007-04-26
It truly did baffle me when I couldn't modprobe snd-usb-audio, but now I think I see what the problem is.  I believe this is a problem with the System76 driver.  I didn't realize that the System76 driver downloads its own version of ALSA, but I now see that it does.

There is no usb audio module in /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc2/modules

System76, I believe this needs to be fixed in the driver.  USB sound devices (esp headsets) are pretty common and for things like Skype and Gizmo a usb headset is all but essential.

Please correct me if I've missed something here.  It looks like you guys included modules only for the Intel sound card, but I think USB audio is really quite essential too.

Adam York

---

### Post by thomasaaron on 2007-04-26
Could you please file a bug report on this one?
[https://launchpad.net/system76](https://launchpad.net/system76)

---

### Post by aay on 2007-04-26
> **thomasaaron said:**
> Could you please file a bug report on this one?
[https://launchpad.net/system76](https://launchpad.net/system76)

Is the link you give specific to System76 or is it going to get filed with Ubuntu?  

I'm happy to file a bug report, but I need someone at System76 to verify whether I've diagnosed the problem correctly.  I don't want to submit a bug to Ubuntu that is System76 specific.

Looking at /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc2/modules, it appears to me as if the System76 driver is installing its own version of ALSA.  Normally this would be a good thing since by doing this you are getting the Intel Hda card (which is on the Gazelle) to work whereas with a stock Ubuntu install it does not work.    In this case it isn't good because it appears that when the System76 driver installs it's own version of ALSA it leaves out the snd_usb_audio driver which is needed for devices like my Plantronics headset.  I can understand why System76 would do this out of simplicity's sake for the default sound card on the Gazelle, but this policy overlooks the possibility of someone using a USB audio device.

I am just guessing about all this but it looks reasonable from what I can see.  Can you please confirm?  If the above is correct, then this is a System76 issue not an Ubuntu issue.

It seems to me like the best solution here is to include the usb audio driver in the System76 driver's version of ALSA so that when USB audio devices are plugged in HAL can do it's thing and load the proper module and offer to enable the devices as a sound card.

Adam York

---

### Post by aay on 2007-04-26
Ok looks like the link you are sending me to is System76 specific.  

I'll file a bug there.

Adam

---

### Post by thomasaaron on 2007-04-26
It is for System76.

---

### Post by aay on 2007-04-30
I did create a bug report last week which can be found here:

[https://bugs.launchpad.net/system76/+bug/110321](https://bugs.launchpad.net/system76/+bug/110321)

Right now I'd welcome any of the following from System76 or the community.

1.   A temporary work around until the bug is fixed.
2.   A permanent fix.
2.  Corroboration from someone else that I have correctly diagnosed this problem.  Any other System76 customers having similar USB Audio problems running Feisty with the latest System76 driver?  This is on a Gazelle Pro, but perhaps people have experienced this on other models as well.

Thanks

---

### Post by thomasaaron on 2007-05-01
Verified that snd_usb_audio is not present on a standard Feisty install.
Looking for a work-around.

Here is an interesting bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/33736](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/33736)

---

### Post by aay on 2007-05-01
> **thomasaaron said:**
> Verified that snd_usb_audio is not present on a standard Feisty install.
Looking for a work-around.

Here is an interesting bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/33736](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/33736)

Thanks for looking into this issue.  However, from what you posted in reply the the bug report in Launchpad, I don't see that you've verified that snd_usb_audio isn't present in a Feisty install.  I listed my reasons for saying this on that bug report.  I believe if Feisty didn't include the usb audio driver we would be seeing much more of a howl on the forums than I have seen.

This seems to be a System76 issue.  The reason is quite simple.  System76 installs it's own version of ALSA in /opt.  The problem is that the  snd_usb_audio driver is not present in /opt/system76/system76-driver/src/sys76-alsa-1.0.14rc2/.  The version of ALSA installed by the System76 driver does not seem to include it.

The other bug report you list is interesting, but not relevant to this issue.  That bug doesn't relate to whether or not snd_usb_audio is or is not loaded, but rather it has to do with a dmix problem.  These are two different issues.

I really appreciate you're looking into this issue.  Please post any further info about it here or on the bug report and I'll try to respond.  Thanks also for looking into work arounds.

Adam

---

### Post by thomasaaron on 2007-05-02
True. I did not plug in a USB sound device before doing lsmod | grep sound.
I do not currently have a USB sound device (and probably won't for at least two weeks, since everyone is abroad right now). If anyone with a usb sound device could do a fresh install, plug in the device, do lsmod | grep snd and post the results, that would go a long way towards helping us isolate the cause of the problem.

Best,
Tom

---

### Post by emurphy on 2007-05-03
I've got a homebuilt desktop machine and a system76 Gazelle Performance 2, both running Fiesty. When I plug in my Logitech USB headphones to the desktop machine, they work fine, and I see snd_usb_audio loaded. When I plug in those headphones to my Gazelle laptop, running version 2.01 of the System76 driver installer, I do not see snd_usb_audio loaded.

Here is the output of lsmod | grep snd on my desktop:
```

emurphy@scared@:~>lsmod | grep snd
snd_intel8x0           38952  1 
snd_ac97_codec        117720  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_usb_audio          94336  0 
snd_pcm_oss            49536  0 
snd_seq_dummy           5380  0 
snd_mixer_oss          19840  2 snd_pcm_oss
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_pcm                92808  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_usb_lib            19584  1 snd_usb_audio
snd_timer              26632  2 snd_pcm,snd_seq
snd_rawmidi            29696  2 snd_seq_midi,snd_usb_lib
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_hwdep              12168  1 snd_usb_audio
snd                    68904  12 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore              10272  2 snd
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
usbcore               154416  8 snd_usb_audio,usblp,xpad,snd_usb_lib,usbhid,ohci_hcd,ehci_hcd

```

Here is the output of the same command on my Gazelle laptop after plugging my USB headset:
```

emurphy@wander:/opt/system76/system76-driver/src$ lsmod | grep snd 
snd_hda_intel          22424  1 
snd_hda_codec         200448  1 snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80900  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35328  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56580  11 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

```

This headset used to work on the laptop, not sure exactly when it broke but I'm becoming suspicious of the system76 driver installer. Is there a way I can remove the stuff installed by the System76 driver to test out if it works with plain Feisty?

---

### Post by emurphy on 2007-05-03
> **aay said:**
> I did create a bug report last week which can be found here:

[https://bugs.launchpad.net/system76/+bug/110321](https://bugs.launchpad.net/system76/+bug/110321)

Right now I'd welcome any of the following from System76 or the community.

1.   A temporary work around until the bug is fixed.
2.   A permanent fix.
2.  Corroboration from someone else that I have correctly diagnosed this problem.  Any other System76 customers having similar USB Audio problems running Feisty with the latest System76 driver?  This is on a Gazelle Pro, but perhaps people have experienced this on other models as well.

Thanks

You diagnosed correctly, in my opinion. I've attached a patch to your bug report that fixes the problem on my Gazelle Performance running fiesty (it fixes it by telling the system76-provided version of ALSA to include the usb audio driver).

---

### Post by crichell on 2007-05-04
Fix committed to system76-driver version 2.0.3

---

