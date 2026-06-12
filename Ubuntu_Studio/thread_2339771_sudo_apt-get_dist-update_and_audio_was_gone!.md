---
title: "sudo apt-get dist-update and audio was gone!"
date: 2016-10-12
forum: Ubuntu Studio
---

### Post by jlahtela on 2016-10-12
Hi,

I have strange issue and to be honest I do not exactly know what caused it.
I am inexperienced with Linux audio setup so I am not so sure what bring me in to this situation.

I read instructions from KXStudio page how I can set Reaper to work in Wine.
[http://kxstudio.linuxaudio.org/Documentation:Manual:wineasio_and_reaper](http://kxstudio.linuxaudio.org/Documentation:Manual:wineasio_and_reaper)

Before that everything where good and audio worked in Ubuntu and also in VMWare guest (Windows 10).
I noticed issue with Cadence that if I set any number inputs or outputs on jack it do not start jack server.
It only works if I set those to zero.
Then also Ubuntu issued some "unexepted crash" and on log it pointed out Cadence so I uninstalled it.
It did not resolve the issue.

I tought there is configuration issue so I even reinstalled ALSA if it would help and fix config file(s).

audio do not come out and it do not give any error, not from Spotify, not from Wine Reaper or not from VMWare guest even it identifies soundcard (disconnected from Host).

The thing is that I am not completely sure what caused this and where to look to get it solved.
It might be just some small setting what causes that audio do not come out or something is terribly messed up.

Please, all help is appreciated!

---

### Post by jlahtela on 2016-10-14
I went Windows way and reinstalled it.

---

### Post by jlahtela on 2016-10-25
Hi,

Issue is back... I am think first conclusions was invalid.
Cadence did not cause it.

i run sudo apt-get dist-update and audio was gone!

Pulse volume control shows levels but nothing comes out from from USB audio interface.
Also if I start VMWare player it can not connect to USB device.

lsusb -v shows message 
USB couldn't open device some information will be missing

This is displayed on all USB devices.
At the same time example USB internet modem works.

Any advises where to look problem?

---

### Post by jlahtela on 2016-10-25
Me again on this topic! ;)

I run following commands

sudo apt-get dist-upgrade
sudo apt autoremove 

Then I enabled all additional drivers.
There where some Intel unknown device/driver and Nividia drivers.

Then reboot.

Now Focusrite USB audio interface is regonizied on VMWare and Scarlett MixControl communicates with it!
I have remote TeamViewer session so can not confirm that it actually plays sound, but I confirm this tomorrow and let you guys know!

---

### Post by jlahtela on 2016-10-25
Audio works now on VMWare Windows running on Ubuntu Studio, but no audio from Linux.
Device is claimed by VMWare when it is on and after I switch it off Focusrite comes back to PulseAudio volume panel. It indicates audio signal example from Spotify or browser, but no sound comes out.

I can send pics / logs, if just someone tells me why is needed.
Any suggestion where I should look in to this problem?

---

### Post by jlahtela on 2016-10-26
Okay it was config issue... after dist-upgrade it had muted channel on ALSA mixer.
At least for Scarlet it says Master 1 (Monitor). It wast just muted and dB gaiun set to -128.
Removing mute resolved the "issue", but I set dB gain to zero but did not noticed any changes on volume level.

---

