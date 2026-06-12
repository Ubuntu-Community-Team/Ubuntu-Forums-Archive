---
title: "sound stops working, have to reboot to fix it"
date: 2014-02-18
forum: System76 Support
---

### Post by superjoe30 on 2014-02-18
Model Name: Bonobo Extreme
Model Number: bonx7
Ubuntu Version: 13.10
Driver Version: 13.10.6


After about 2-3 suspends, usually my audio stops working. With the PulseAudio Volume Control I can verify that sound should be coming out, but no sound comes out. Here is a screenshot:

[IMG]http://i.imgur.com/7AD40pH.png[/IMG]

In this screenshot you can see that sound should be coming out. I hear nothing in my headphones, and when I unplug my headphones nothing changes; it looks like it still thinks my headphones are plugged in.

Rebooting fixes the problem (until it happens again after 2-3 resumes from suspend.)

---

### Post by ddraper2 on 2014-02-20
This is a known issue in 13.10, the workaround is to restart the audio systems. If you perform a search you will find a few threads on the subject. What is happening is that when you suspend a pulseaudio does not correctly release the audio device so when the resume occurs alsa does not initialize correctly because the device was not released.

You need to create a file in ~/.pulse named pulse.conf.xxx
It should contain the following line:

autospawn = no

Then create a shell script that contains the following:

#!/bin/bash
set -x
mv ~/.pulse/client.conf.xxx ~/.pulse/client.conf
pulseaudio --kill
lsof /dev/snd*
sudo alsa force-reload
pulseaudio --start
mv ~/.pulse/client.conf ~/.pulse/client.conf.xxx

Execute the shell script and when you are done the audio should be working again.

---

