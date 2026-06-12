---
title: "QJackCtl - Failed to acquire device name"
date: 2012-10-26
forum: Ubuntu Studio
---

### Post by layolayo on 2012-10-26
Just installed Ubuntu Studio on my PC - been running stock Ubuntu 12.04 (12.10) fine and running QTractor/RoseGarden with Jack (fine but with some teething problems).

Now with UbuntuStudio Jack will not start at all - I get the message:

 ```
Fri Oct 26 19:17:45 2012: Starting jack server...
 Fri Oct 26 19:17:45 2012: JACK server starting in realtime mode with priority 10
 Fri Oct 26 19:17:45 2012: control device hw:0
 Fri Oct 26 19:17:45 2012: control device hw:0
 Fri Oct 26 19:17:45 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Cannot allocate memory[0m
 Fri Oct 26 19:17:45 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
 Fri Oct 26 19:17:45 2012: [1m[31mERROR: Cannot initialize driver[0m
 Fri Oct 26 19:17:45 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Fri Oct 26 19:17:45 2012: [1m[31mERROR: Failed to open server[0m
 Fri Oct 26 19:17:46 2012: Saving settings to "/home/midi/.config/jack/conf.xml" ...
 19:17:54.327 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```Running aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 2: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Running arecord - l

```
**** List of CAPTURE Hardware Devices ****
card 2: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```And running cat /proc/asound/cards

```
 0 [USBMIDI        ]: USB-Audio - CASIO USB-MIDI
                      CASIO CASIO USB-MIDI at usb-0000:00:1d.7-5.4, full speed
 1 [UMONE          ]: USB-Audio - UM-ONE
                      Roland UM-ONE at usb-0000:00:1d.7-5.3, full speed
 2 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 44
```I have checked the two Jack conf files and they are different - Note this is the same PC dual-booting.

Stock Ubuntu Conf:

```
<!-- Tue Oct 23 17:43:15 2012 --><jack><engine><option name="driver">alsa</option><option name="realtime">true</option><option name="verbose">false</option><option name="client-timeout">500</option></engine><drivers><driver name="loopback">
  </driver><driver name="alsarawmidi">
  </driver><driver name="firewire">
  </driver><driver name="netone">
  </driver><driver name="alsa"><option name="capture">hw:0</option><option name="playback">hw:0</option><option name="device">hw:0</option><option name="rate">44100</option><option name="period">1024</option><option name="nperiods">2</option><option name="hwmon">false</option><option name="hwmeter">false</option><option name="duplex">true</option><option name="softmode">false</option><option name="monitor">false</option><option name="dither">n</option><option name="shorts">false</option></driver><driver name="dummy">
  </driver><driver name="net">
  </driver></drivers><internals><internal name="netmanager">
  </internal><internal name="audioadapter">
  </internal><internal name="profiler">
  </internal><internal name="netadapter">
  </internal></internals></jack>
```Ubuntu Studio Conf:

```
<!-- Fri Oct 26 18:42:53 2012 --><jack><engine><option name="driver">alsa</option><option name="realtime">true</option><option name="verbose">false</option><option name="client-timeout">2000</option></engine><drivers><driver name="alsa"><option name="device">hw:0</option><option name="rate">44100</option><option name="period">256</option><option name="nperiods">3</option><option name="hwmon">false</option><option name="hwmeter">false</option><option name="duplex">true</option><option name="softmode">false</option><option name="monitor">false</option><option name="dither">n</option><option name="shorts">false</option></driver><driver name="firewire">
  </driver><driver name="dummy">
  </driver><driver name="net">
  </driver><driver name="netone">
  </driver><driver name="loopback">
  </driver></drivers><internals><internal name="audioadapter">
  </internal><internal name="netmanager">
  </internal><internal name="profiler">
  </internal><internal name="netadapter">
  </internal></internals></jack>
```Hoping there is a simple answer to this.

Cheers!

---

### Post by layolayo on 2012-10-27
Just checked aplay, arecord and cat /proc/asound/cards for the working Stock Ubuntu.

aplay:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


arecord:

```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


cat /proc/asound/cards:

```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 44
 1 [UMONE          ]: USB-Audio - UM-ONE
                      Roland UM-ONE at usb-0000:00:1d.7-5.3, full speed
 2 [USBMIDI        ]: USB-Audio - CASIO USB-MIDI
                      CASIO CASIO USB-MIDI at usb-0000:00:1d.7-5.4, full speed
```

Is having the internal Intel soundcard as Card 0, making all the difference here? If so, how I can reconfigure this on Ubuntu Studio?

---

### Post by layolayo on 2012-10-27
OK - I take all the above back, now I have loaded 12.10 Ubuntu back up and run the aplay commands etc for the above post - I have attempted to restart Jack and I get the same error.

Everything worked yesterday just fine, before installing Studio as a dual-boot...?

EDIT: So, Jack works again on 12.10 after a reboot and plugging in my PC Speakers - rebooted back into U-Studio and still get the error?

---

