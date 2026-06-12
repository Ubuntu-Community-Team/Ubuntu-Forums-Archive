---
title: "behringer guitar link + ubuntu studio"
date: 2012-04-13
forum: Ubuntu Studio
---

### Post by jmakepeace on 2012-04-13
Hi there fellows.

A disclaimer: I am an absolute noob at this ubuntu story - and to DAW's and audio recording and production, so please try to be patient ):P.

I have been trying for days to get this to work. I have worked out the basics of JACK, and I am using patchage. I am able to record with my laptops onboard mic, so all is well on that front.

As I understand it, when I plug in my behringer usb interface I it should come up in patchage and that I should be able to connect the in and out (headphones out and guitar in) to other components. Unfortunately this is not the case, I can't see it in patchage. I can however see it in the JACK interface drop down, and aplay, arecord and lsusb shows this:

jono@jono:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jono@jono:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jono@jono:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 002: ID 08bb:2902 Texas Instruments Japan PCM2902 Audio Codec

I have absolutely no idea what to do to get it to work. Anyone have any ideas?

Thanks in advance,

Jono

---

### Post by sgx on 2012-04-13
Hi, look in the rakarrack topic below, things I mention there
apply in your case, just change the names. Patchage sometimes draws
items far off the viewable area, so you may need to scroll around,
to see what's there, and then scoot icons within useful range
of each other.
Cheers

---

### Post by jmakepeace on 2012-04-14
Thanks for your reply! Its still not showing up in patchage, no matter what I with the JACK settings. It also doens't show up in the JACK connection kit. .

---

### Post by sgx on 2012-04-14
does it show up in the output of

arecord -l
or  cat /proc/asound/cards
?
Its proper name may be in brackets, and can be used
in qjackctl in place of hw:0,0  hw:1  or whatever is shown
in the qjackctl setup page

Input Device >
Output Device >  fields

I know others are using these in linux with good results.
Cheers

---

### Post by jmakepeace on 2012-04-14
As in my 1st post, it does show up in arecord -l as:

card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
Subdevices: 1/1
Subdevice #0: subdevice #0

So you're suggestion is that I take the [USB Audio CODEC] or [USB Audio] (which one?) and replace the (default) in the input device?

I'm not worried about the output, because I want that to come from my PC and not from the interface.

Thanks!

---

### Post by jmakepeace on 2012-04-14
Also, I'm not 100% sure whether the real-time box should be checked. I'm pretty sure I said yes to real-time kernel when I installed the OS, is there a way to check?

---

### Post by jejeman on 2012-04-14
You can check running kernel with
```
uname -a
```

---

### Post by jmakepeace on 2012-04-14
Thanks!

Get this out:

Linux jono 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Not particularly sure what it means as its 13:41 here..

---

### Post by jejeman on 2012-04-14
You are not running realtime kernel, but that should not worry you. Jack needs to work anyway. You maybe can't get low latnecies, but it should work.

---

### Post by jmakepeace on 2012-04-14
Oh I get it, that's when it was installed. How do I know from that command if real time kernel is enabled?

---

### Post by jejeman on 2012-04-14
Instead of generic in 3.0.0-17-generic, it should write realtime, rt or preempt.
Also you could have lowlatency kernel.
I'm guessing that you use ubuntu 11.10. There are no realtime kernels for that version, all you maybe can get is lowlatency kernel from PPA-s, but that ship has also probably sailed too.

---

### Post by jmakepeace on 2012-04-14
Still haven't managed to get this to work, however with JACK turned off and just listening to some music via Rhythmbox, I found the slider for the line out of the guitarlink interface. I can now get music to play out of the PC's line out OR the guitarlink's out OR both.

Something funny that may contribute:

When I'm listening to music through Rhythmbox and I open JACK, the song pauses and I can't hear anything. My JACK log also looks horrible..:

> 15:59:44.708 Patchbay deactivated.
15:59:44.806 Statistics reset.
15:59:44.818 ALSA connection change.
15:59:44.838 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
15:59:45.229 D-BUS: JACK server is starting...
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
15:59:45.235 ALSA connection graph change.
15:59:45.426 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: driver "alsa" selected
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Saving settings to "/home/jono/.config/jack/conf.xml" ...
Sat Apr 14 15:59:44 2012: Starting jack server...
Sat Apr 14 15:59:44 2012: JACK server starting in realtime mode with priority 10
Sat Apr 14 15:59:45 2012: control device hw:0
Sat Apr 14 15:59:45 2012: control device hw:0
Sat Apr 14 15:59:45 2012: Acquired audio card Audio0
Sat Apr 14 15:59:45 2012: creating alsa driver ... hw:0|hw:0|1024|4|48000|0|0|nomon|swmeter|-|32bit
Sat Apr 14 15:59:45 2012: control device hw:0
Sat Apr 14 15:59:45 2012: configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 4 periods
Sat Apr 14 15:59:45 2012: ALSA: final selected sample format for capture: 32bit integer little-endian
Sat Apr 14 15:59:45 2012: ALSA: use 4 periods for capture
Sat Apr 14 15:59:45 2012: ALSA: final selected sample format for playback: 32bit integer little-endian
Sat Apr 14 15:59:45 2012: ALSA: use 4 periods for playback
Sat Apr 14 15:59:45 2012: graph reorder: new port 'system:capture_1'
Sat Apr 14 15:59:45 2012: New client 'system' with PID 0
Sat Apr 14 15:59:45 2012: graph reorder: new port 'system:capture_2'
Sat Apr 14 15:59:45 2012: graph reorder: new port 'system:playback_1'
Sat Apr 14 15:59:45 2012: graph reorder: new port 'system:playback_2'
Sat Apr 14 15:59:45 2012: New client 'PulseAudio JACK Sink' with PID 1851
Sat Apr 14 15:59:45 2012: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Sat Apr 14 15:59:45 2012: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Sat Apr 14 15:59:45 2012: New client 'PulseAudio JACK Source' with PID 1851
Sat Apr 14 15:59:45 2012: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Sat Apr 14 15:59:45 2012: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
15:59:47.722 JACK connection change.
15:59:47.727 Server configuration saved to "/home/jono/.jackdrc".
15:59:47.732 Statistics reset.
15:59:47.758 Client activated.
15:59:47.771 JACK connection graph change.
Sat Apr 14 15:59:47 2012: New client 'qjackctl' with PID 3277
16:00:02.996 XRUN callback (1).
Sat Apr 14 16:00:02 2012: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 2[0m
Sat Apr 14 16:00:02 2012: [1m[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 2[0m
Sat Apr 14 16:00:02 2012: [1m[31mERROR: JackAudioDriver::ProcessGraphAsync: Process error[0m
16:00:04.216 XRUN callback (1 skipped).

---

### Post by sgx on 2012-04-15
I would leave the box ticked, as there are many elements of RT
behavior, that are now in the mainstream kernels.
Main thing is Periods/Buffer in qjackctl is 3, don't use a usb hub.

Try all the usb ports, with no other usb device in use.
Repeat the process by starting the computer without the behringer,
run the commands, plug it in, run the commands again, and look at whats different in the output.

When you see the device name in brackets from arecord -l
or cat /proc/asound/cards

replace the existing term used in qjackctl setp page

Input Device >
Output Device >

with the text found within brackets, and restart qjackctl.

(you need not use the behringer as the output device, but I
have read that you can. Otherwise, choose the motherboard sound
as the output device, in case 100% support for duplex i/o is lacking in this case.
Cheers

---

