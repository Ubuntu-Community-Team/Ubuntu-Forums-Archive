---
title: "JACK doesn't work with 2 simultaneous cards"
date: 2009-11-27
forum: Ubuntu Studio
---

### Post by ninjabob7 on 2009-11-27
I'm attempting to set up a machine for recording and live looping of my guitar. I have a cable with USB on one end and 1/4 inch plug on the other which acts as a USB sound card for recording. For playback, I'm using the built-in card. My current machine is a Gateway TA1 laptop, and I am getting frustrated.

I've set up the realtime kernel and all that, and JACK runs fine in duplex mode using either card separately (for both playback and capture). When I try to use them together, I get huge numbers of xruns.

The frustrating thing is I've used this same setup successfully on a 1999 Toshiba laptop. That would seem to rule out any problems related to the USB card or lack of power. I've had the same problem on 2 other machines.

I have no idea about the brand or model of the USB card - lsusb doesn't give a name and Windows just calls it USB Audio Device. The built-in card is an Intel ICH6 chipset.
The output from lshw is here: [http://miscjunk.net/files/lshw.html]("http://miscjunk.net/files/lshw.html")

---

### Post by sgx on 2009-11-28
> **ninjabob7 said:**
> I'm attempting to set up a machine for recording and live looping of my guitar. I have a cable with USB on one end and 1/4 inch plug on the other which acts as a USB sound card for recording. For playback, I'm using the built-in card. My current machine is a Gateway TA1 laptop, and I am getting frustrated.

I've set up the realtime kernel and all that, and JACK runs fine in duplex mode using either card separately (for both playback and capture). When I try to use them together, I get huge numbers of xruns.

The frustrating thing is I've used this same setup successfully on a 1999 Toshiba laptop. That would seem to rule out any problems related to the USB card or lack of power. I've had the same problem on 2 other machines.

I have no idea about the brand or model of the USB card - lsusb doesn't give a name and Windows just calls it USB Audio Device. The built-in card is an Intel ICH6 chipset.
The output from lshw is here: [http://miscjunk.net/files/lshw.html]("http://miscjunk.net/files/lshw.html")

Only cables I know of with usb/guitar ends are the IKMM Stealthplug, and the Lightpipe, known for green LED lights. There may be Lightpipe clones too. As these  are 'more' than just cables, and the Stealthplug is locked to its asio driver, (likely the same for Lightpipe) you won't get far unless there is recent alsa support.  Install rakarrack multi-fx app, and try to connect it in qjackctl to your usb cable setup. 

Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

These will reveal what sound devices are seen by your system. 

If you get those connected, you can turn focus to the onboard soundcard. 

Run the alsaconf command with everything plugged in, and see if it offers to configure more than 1 device.

If you post the output of the lsmod  command, it would help the experts.

Run the lsmod command, and look for an entry for the usb-cable device, these are the usb entries of my system with no usb sound device, you can look for other entries that are unknown, but listed with or near them in various lines.

uhci_hcd               25744  0
ohci_hcd               26640  0
ehci_hcd               38028  0
usbcore               135152  6 usb_storage,cdc_acm,uhci_hcd,ohci_hcd,ehci_hcd

A photo of your cable might help ID it.
Cheers

---

### Post by AutoStatic on 2009-11-28
> **sgx said:**
> A photo of your cable might help ID it.And the output of **lsusb** and **aplay -l**

---

### Post by ninjabob7 on 2009-11-28
```
$ alsaconf
alsaconf: command not found

$ lsmod | grep usb
snd_usb_audio          84320  2 
snd_usb_lib            16340  1 snd_usb_audio
snd_hwdep               7416  1 snd_usb_audio
usbhid                 38144  0 
snd_pcm                75096  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            22240  2 snd_usb_lib,snd_seq_midi
snd                    60740  25 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1940:ac01  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x19400xac01 [USB Device 0x1940:0xac01], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I'm not sure where to find alsaconf - the alsa-utils and alsa-tools packages are both installed already.

Photo: [http://miscjunk.net/files/100_9418.JPG]("http://miscjunk.net/files/100_9418.JPG")
It does have green lights on both ends.

The problem is not with the USB cable, which works fine by itself. The problem is when I try to use it for capture and the onboard card for playback. I assume the 1/4 inch jack on the guitar end is a headphone output, but I haven't been able to get sound out of it before, and even if it worked it would be awkward to connect to speakers.

---

### Post by ninjabob7 on 2009-11-28
I believe I just solved the problem by myself. Google led me to these threads: [http://ubuntuforums.org/showthread.php?t=1128748]("http://ubuntuforums.org/showthread.php?t=1128748") and [http://ubuntuforums.org/showthread.php?t=1198297]("http://ubuntuforums.org/showthread.php?t=1198297")
I got the idea that running jackd using the USB card and then using alsa_out/alsa_in to add the onboard card might work. After some trouble compiling the tools, I found that they didn't work... it complained of requesting 44100Hz sample rate but only 48000 was available.

I changed jackd to 48000 samples, then tried the original setup again, and it worked! I thought 44100 was standard, but apparently not. This explains why the old laptop worked - that card must have been running at 44100, while all the modern machines run at 48000.

I don't know a lot about audio hardware, but I'm wondering if the default for qjackctl should be 48000 instead of 44100? Is it worth filing a bug report?

---

### Post by AutoStatic on 2009-11-29
Great! According to [this thread]("http://forums.fedoraforum.org/showthread.php?t=221446") it's a Lightsnake.
You could try filing a bug, I get the idea that most HDA onboard cards prefer a sample rate of 48Khz.

---

### Post by VertexPusher on 2009-11-29
44100 Hz as a default in QJackCtl makes perfect sense because it's the native sample rate of CDDA. It's true that older AC'97 audio interfaces had a fixed rate of 48000 Hz, but HDA, which replaced AC'97, is perfectly capable of running at 44100, 48000 or 96000 Hz. HDA also supports 32 bit sample width. You can use speaker-test to verify this.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ speaker-test -l 1 -D hw:Intel -F S32_LE -c 8 -r 44100

speaker-test 1.0.20

Playback device is hw:Intel
Stream parameters are 44100Hz, S32_LE, 8 channels
Using 16 octaves of pink noise
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 8 to 2048
Period size range from 4 to 1024
Using max buffer size 2048
Periods = 4
was set period_size = 512
was set buffer_size = 2048
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
Time per period = 23.917873
$ speaker-test -l 1 -D hw:Intel -F S32_LE -c 8 -r 96000

speaker-test 1.0.20

Playback device is hw:Intel
Stream parameters are 96000Hz, S32_LE, 8 channels
Using 16 octaves of pink noise
Rate set to 96000Hz (requested 96000Hz)
Buffer size range from 8 to 2048
Period size range from 4 to 1024
Using max buffer size 2048
Periods = 4
was set period_size = 512
was set buffer_size = 2048
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
Time per period = 23.958757
$
```

ALSA's "hw" plugin performs no sample rate or format conversion, so if you request a sample rate or format that is not natively supported by the card, speaker-test will fail and return an error message. So this is a reliable way to find out the capabilities of your card.

I have not yet seen a HDA interface that couldn't operate at 44100 Hz. However, if yours really doesn't support that sample rate, you can still run Jack at 44100 Hz and use "plughw" instead of "hw". See the difference with speaker-test:

```
$ speaker-test -l 1 -D hw:Intel -F S32_LE -c 8 -r 32000

speaker-test 1.0.20

Playback device is hw:Intel
Stream parameters are 32000Hz, S32_LE, 8 channels
Using 16 octaves of pink noise
Rate 32000Hz not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
$ speaker-test -l 1 -D plughw:Intel -F S32_LE -c 8 -r 32000

speaker-test 1.0.20

Playback device is plughw:Intel
Stream parameters are 32000Hz, S32_LE, 8 channels
Using 16 octaves of pink noise
Rate set to 32000Hz (requested 32000Hz)
Buffer size range from 2 to 682
Period size range from 1 to 342
Using max buffer size 680
Periods = 4
was set period_size = 226
was set buffer_size = 680
 0 - Front Left
 4 - Center
 1 - Front Right
 7 - Side Right
 3 - Rear Right
 2 - Rear Left
 6 - Side Left
 5 - LFE
Time per period = 24.014577
$
```

As you can see, the first test fails because 32000 Hz is not natively supported by the card. The second test succeeds because "plughw" performs rate conversion in software. This way any ALSA client application such as Jack can use its preferred sample rate regardless of the hardware. Latency will not be affected too much because plughw access is exclusive to one client (unlike "dmix" which allows shared access by multiple applications and increases latency quite significantly).

---

