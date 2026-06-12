---
title: "Working Setups"
date: 2011-07-31
forum: Ubuntu Studio
---

### Post by dawiba on 2011-07-31
Since there are still plenty of posts where people are trying figure out Jack and their setups, I thought it might be useful to have a thread which listed working Jack setups. The idea is that users could browse the list and hopefully find setups that match their own or something else that might help them get up and running.

I'd suggest listing the following;

Computer
Soundcard
Ubuntu Version
Kernel Version
Any changes to default settings
Jack settings &#8211; a screenshot would be good. There are no prizes for lowest latency ;).
Which software you mainly use.
Any problems/workarounds.

Of course, there might be other things worth listing :)


Here's mine to get things started:

1. Computer - Dell Studio XPS 8000
2. Soundcard &#8211; Focusrite Saffire LE (Firewire)
3. Ubuntu Version &#8211; 11.04 (regular Ubuntu)
4. Kernel &#8211; 2.6.38-10-generic-pae (regular kernel)
5. Changes to default installation -
[LIST]Added myself to the Audio and Video Groups
Installed RTIRQ and changed the settings to - RTIRQ_NAME_LIST="rtc firewire snd usb i8042" - [following the instructions on this page]("https://help.ubuntu.com/community/FireWire").
When installing Qjackctl, I enabled the realtime scheduling option
[/LIST]
6. Jack Settings &#8211; see screenshot
7. Problems &#8211; none to speak of. Everything syncs well and I don't get x-runs during recording or playback
8. Main software -
[LIST]Jack - to connect everything together
A2JMidi - to connect QTractor to Jack Midi
Mixbus - for audio recording
LinuxDSP Plugins - compression, eq etc
QTractor - for midi recording
Hydrogen - for drums
Musescore - Notation. (I write out a lot of music :oops:)
FMIT - Tuner
Audacity - For creating MP3's
[/LIST]

If you feel this might be helpful, please add your setup/settings to the list and feel free to offer any other suggestions

---

### Post by sgx on 2011-07-31
Athlon 3800
nvidia MCP51 motherboard chipset
2 gig ram
nvidia 9400GT video
mAudio 24/96 pci soundcard
mAudio fastrack usb interface
Fender Mustang usb guitar interface/amp
Yamaha DGX keyboard midi 5 pin din i/o

this has been wonderfully free of gotchas over the years,
the one trouble area was several iterations of debian installers
would not properly detect/support the motherboard nvidia 6100 chip,
so I had to buy a videocard. This setup works great with Mint 9 audio apps, Ubuntu Studio 8.04, pclinuxos, bodhi linux, puppy studio, macpup, and most live dvds I have tested for booting, like remixOS, AVLinux, and Trinity etc. I use E17 desktop, and minimum gnome/kde dependencies.

the pclinuxos bfs kernels, debian RT kernels,
Puppy Studio kernels, and Ubuntu Studio 8.04 kernel,
all offer great productivity.

I regularly use yoshimi, hydrogen, rakarrack, phasex, calfjackhost,
timemachine, audacity, (qjackctl and jp1 for connections), and use
reaper as a daw in wine, with a couple dozen soft-synths and fx plugins. although I consider the linux environment itself to be the ultimate DAW! If stranded on a desert isle, with only 3 sound apps, and an OS, linux, yoshimi, hydrogen, and rakarrack would win. Commercial software has great and affordable jewels, but that's how I would choose.

Cheers

---

