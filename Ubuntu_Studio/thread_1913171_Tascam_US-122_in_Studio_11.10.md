---
title: "Tascam US-122 in Studio 11.10"
date: 2012-01-22
forum: Ubuntu Studio
---

### Post by fabio sela on 2012-01-22
Dear ubuntu-studio forum,

I am using Ubuntu 11.10 32 bit and I tried to install my Tascam US-122 here. I followed the instructions on [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122) for 'newer releases'. 

After installation, the lights of my US-122 turn on and it seems to be running, at least according to the following output:

```
cat /proc/asound/cards
...
2 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 002/006)
```However, trying to use US-122 fails with every attempt. E.g. in Audacity I can choose the device from the dropdown-menu, but as soon as I start e.g. a playback of a sound-file, Audacity gives me the following error-message:

[I]"Error while opening sound device. Please check the output device settings and the project sample rate."
[/I]
Similar problems occur when I try to start Jack (QjackCtl):
```
13:05:58.134 D-BUS: JACK server could not be started. Sorry
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: driver "alsa" selected
...
Sun Jan 22 13:05:57 2012: Saving settings to "/home/stefan/.config/jack/conf.xml" ...
Sun Jan 22 13:05:57 2012: Starting jack server...
Sun Jan 22 13:05:57 2012: JACK server starting in realtime mode with priority 89
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sun Jan 22 13:05:58 2012: control device hw:2
Sun Jan 22 13:05:58 2012: control device hw:2
Sun Jan 22 13:05:58 2012: [1m[31mERROR: Failed to acquire device name : Audio2 error : Input/output error[0m
Sun Jan 22 13:05:58 2012: [1m[31mERROR: Audio device hw:2 cannot be acquired, trying to open it anyway...[0m
Sun Jan 22 13:05:58 2012: creating alsa driver ... hw:2|hw:2|1024|2|48000|0|0|nomon|swmeter|-|32bit
Sun Jan 22 13:05:58 2012: control device hw:2
Sun Jan 22 13:05:58 2012: configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
Sun Jan 22 13:05:58 2012: ALSA: final selected sample format for capture: 24bit little-endian
Sun Jan 22 13:05:58 2012: ALSA: use 2 periods for capture
Sun Jan 22 13:05:58 2012: ALSA: final selected sample format for playback: 24bit little-endian
Sun Jan 22 13:05:58 2012: ALSA: use 2 periods for playback
Sun Jan 22 13:05:58 2012: [1m[31mERROR: ALSA: cannot set hardware parameters for playback[0m
Sun Jan 22 13:05:58 2012: [1m[31mERROR: ALSA: cannot configure playback channel[0m
Sun Jan 22 13:05:58 2012: [1m[31mERROR: Cannot initialize driver[0m
Sun Jan 22 13:05:58 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sun Jan 22 13:05:58 2012: [1m[31mERROR: Failed to open server[0m
13:06:01.998 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```I tried things out up- and down, but I permanently fail to get my US-122 running on Ubuntu 11.10. I have never had this problem before on previous releases of Ubuntu.

Another thing that strucks me is that when going to ">System Settings >Sound", I can chosse the US-122 as input, but it does not appear in the output list. If I choose it as input there, I can use the US-122 in audacity as input device, but recording only works for around 1 second, after that the signal becomes a steady cracking sound.

I'd be happy for any help.

Sela

---

### Post by fabio sela on 2012-01-23
I still cannot find any solution for my problem from above. Jack will not start and it is not possible to do any playback/capturing with the US-122 even though the lights are on, the direct monitor is running and ubuntu gives me the information that the soundcard is properly recognized.

Maybe this information can give some more insight into my problem:

```
arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Is it possible that my problem is somehow related to the fact that 'device 0' is given several times, for 'card 0' and 'card 2' under capture devices, and the same for the playback devices? Shouldn't the 'US-X2Y Audio' have a different device-no than the 'STAC92xx Analog'?

Sela

---

