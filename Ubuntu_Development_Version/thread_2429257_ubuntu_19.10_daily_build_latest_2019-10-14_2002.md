---
title: "ubuntu 19.10 daily build latest 	2019-10-14 20:02"
date: 2019-10-16
forum: Ubuntu Development Version
---

### Post by jerry47 on 2019-10-16
Under settings. Sound output device not detected. Three selections available. Select manually. Upon reboot wrong output device.

---

### Post by sudodus on 2019-10-16
In order to reach the developers, please create a bug report at Launchpad.

You need a user ID (at Launchpad)

You can start the bug report with the command

```

ubuntu-bug package-name

```

In this case probably

```

ubuntu-bug pavucontrol

```

---

### Post by jerry47 on 2019-10-19
Hi sudodus, 

Sorry for the delayed response. Upon doing some research, I found out that this issue has occurred before in multiple distributions. I just never had the problem with my Asus Z77 motherboard. I have the sound shuddering issue and that's consistent across multiple distros as well. That was patched using the jack retask in the alsa tools gui application. I've been testing Manjaro Gnome latest release as well and it did not have the issue with either 18.0 or 18.1 which has the same kernel and gnome updates I believe. Just last night I found several posts on this topic and how to solve it. I'm using the s/pdif digital output to my soundbar. But on 19.10 the sound setting defaults to hdmi. The solution to inhibit this behavior is simple but finding the correct syntax took some time. The GPU is an Nvidia GTX-1050TI that has two hdmi sound outputs. What I didn't know was that the same intel drivers are used for the onboard sound and the GPU. So, one cannot blacklist it. At least not in the normal way. So I literally stumbled on the solution. The syntax is options snd_hda_intel enable=1,0 written to /etc/modprobe.d/blacklist.conf. The "1" is enabling s/pdif and the "0" is disabling the Nvidia hdmi. Guess its not a solution, but more of a band-aid. I've got two other systems to upgrade after giving 18.10 a thorough testing over the next few weeks on my test pc. You can consider this matter closed. 

Thanks for the response, Gerald

---

### Post by wildmanne39 on 2019-10-19
Since 19.10 is no longer in development and the issue is solved I am closing this thread instead of moving it to an appropriate sub-forum for support. 

Thanks for sharing your solution.

---

