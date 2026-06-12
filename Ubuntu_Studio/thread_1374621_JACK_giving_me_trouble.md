---
title: "JACK giving me trouble"
date: 2010-01-07
forum: Ubuntu Studio
---

### Post by TBBucs on 2010-01-07
I'm running Ubuntu 9.10 (not Studio) and am having a heck of a time getting my PreSonus Firepod (connected via firewire) hooked up.  I looked at the other JACK thread on these boards and got some info from there, but I'm still having trouble.  I followed the instructions on these pages:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

...but it's still not working, even though the output of the test bash commands have been spot on with what the guides say they should be.  My JACK Audio Connection Kit settings are identical to the ones at [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) but can be summarized as:

[LIST]
[*]Driver: firewire
[*]Interface: hw:0
[*]Audio: Duplex
[*]Check Realtime
[*]Priority: 70
[*]Frames/Period: 128
[*]Sample Rate: 44100
[*]Periods/Buffer: 2
[/LIST]
But when I run it, I get this:
```
[COLOR=#999999] 01:20:34.656 Startup script...[/COLOR]
 [COLOR=#990099]01:20:34.657 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]01:20:35.059 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]01:20:35.059 JACK is starting...[/COLOR]
 [COLOR=#990099]01:20:35.059 /usr/bin/jackd -R -P70 -dfirewire -dhw:0 -r44100 -p128 -n2 -i8 -o8[/COLOR]
 [COLOR=#999999]01:20:35.061 JACK was started with PID=2252.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216903488, from thread -1216903488] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]01:20:35.073 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]01:20:35.073 Post-shutdown script...[/COLOR]
 [COLOR=#990099]01:20:35.075 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]01:20:35.481 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]01:20:37.227 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

---

### Post by AutoStatic on 2010-01-07
Hello TBBucs,

JACK complains:
```
cannot use real-time scheduling (FIFO at priority 10) [for thread -1216903488, from thread -1216903488] (1: Operation not permitted)
```

So you could either uncheck the Realtime option in QjackCtl or make sure your account is a member of the *audio* and *video* groups on your system and that your */etc/security/limits.conf* is set up properly so that the audio group has extra rights. See the Real-Time Support paragraph of the [UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") help page.

---

### Post by TBBucs on 2010-01-07
Excellent, so now the real-time error is gone.  I was already a member of both audio and video, but the limits.conf file hadn't been set up for audio. However, I now have a new error from JACK:

```

firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire

```

lsmod gave me this output:

```

Module                  Size  Used by
dv1394                 17628  0 
raw1394                25692  0 
nls_utf8                1568  0 
udf                    81060  0 
crc_itu_t               1844  1 udf
snd_hda_codec_idt      60124  1 
snd_hda_intel          26824  2 
snd_hda_codec          76052  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7416  1 snd_hda_codec
snd_pcm_oss            38112  0 
snd_mixer_oss          16564  1 snd_pcm_oss
snd_pcm                75096  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
nls_iso8859_1           3732  3 
snd_seq_dummy           2680  0 
snd_seq_oss            28736  0 
arc4                    1652  2 
snd_seq_midi            6560  0 
ecb                     2516  2 
pcmcia                 35560  0 
snd_rawmidi            22240  1 snd_seq_midi
nls_cp437               5364  3 
snd_seq_midi_event      7092  2 snd_seq_oss,snd_seq_midi
binfmt_misc             8444  1 
snd_seq                50896  9 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                108500  0 
snd_timer              22040  2 snd_pcm,snd_seq
iptable_filter          3092  0 
tpm_infineon            8232  0 
snd_seq_device          6944  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               112340  1 iwlagn
led_class               4088  1 iwlcore
snd                    60740  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              183336  2 iwlagn,iwlcore
yenta_socket           24288  2 
tifm_7xx1               5300  0 
rsrc_nonstatic         11860  1 yenta_socket
psmouse                56460  0 
uvcvideo               59040  0 
tpm                    16128  1 tpm_infineon
videodev               36960  1 uvcvideo
soundcore               7968  1 snd
ppdev                   6712  0 
vfat                   10708  3 
ip_tables              11652  1 iptable_filter
lp                      9604  0 
fat                    51440  1 vfat
x_tables               17176  1 ip_tables
parport                35976  2 ppdev,lp
snd_page_alloc          9244  2 snd_hda_intel,snd_pcm
v4l1_compat            14776  2 uvcvideo,videodev
serio_raw               5432  0 
pcmcia_core            36940  3 pcmcia,yenta_socket,rsrc_nonstatic
sony_laptop            32228  0 
cfg80211               93508  3 iwlagn,iwlcore,mac80211
tifm_core               8080  1 tifm_7xx1
joydev                 10304  0 
tpm_bios                6388  1 tpm
usbhid                 38144  0 
usb_storage            52512  2 
ohci1394               30308  1 dv1394
ieee1394               87284  3 dv1394,raw1394,ohci1394
sky2                   46648  0 
video                  19244  0 
output                  2836  1 video
intel_agp              27516  0 
agpgart                35440  1 intel_agp

```

---

### Post by AutoStatic on 2010-01-07
```
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
```
My guess is that /dev/raw1394 has both user ID and group ID of *root* so the device node can't be used by a normal user.
You can check it with **ls -al /dev/raw1394**. The group ID (GID) should be *audio* or *video*:
```
jeremy@soushi:~$ ls -al /dev/raw1394 
crw-rw---- 1 root video 171, 0 2010-01-07 21:31 /dev/raw1394
```

To set the permissions right: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)
Step 2 and 3.

---

### Post by TBBucs on 2010-01-07
**ls -al /dev/raw1394** gave me this:

```
crw-rw---- 1 root video 171, 0 2010-01-07 13:43 /dev/raw1394
```

Which it seems is correct.  And the command **groups** says I'm in both audio and video (and disk) as I should be.  Any other ideas?

---

### Post by AutoStatic on 2010-01-07
Interface should be (default) in QjackCtl when using Firewire, not hw:0, that's an ALSA designation and the firewire driver in QjackCtl doesn't use ALSA but FFADO.

---

