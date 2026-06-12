---
title: "gtk-recordMyDesktop error with Jack"
date: 2009-07-05
forum: Ubuntu Studio
---

### Post by Rytron on 2009-07-05
Hi.
I set up Jack recently. I read that it is far better than Pulse. I followed [this guide]("http://ubuntuforums.org/showthread.php?t=806730") to set it up. I set the option in gtk-recordMy Desktop error to use jack but I now get this error [picture attached].
I also notice that I cant record properly in Audacity with Jack. I must have the wrong settings for Jack.

---

### Post by lucianodato on 2010-09-13
I have the same problem.

---

### Post by Pablo_F on 2010-09-15
I had the same problem with gtk-recordmydesktop. Then I switched to plain recordmydesktop (CLI). I launch it with:

recordmydesktop -x 47 -y 84 -width 1600 -height 900 -fps 15 **--use-jack system:capture_1 system:capture_2**

With this command recordmydesktop will have two inputs, by default connected to the system: captures. You can change these connections in qjackctl or patchage. Of course, you can specify other ports but these ones are always there and recordmydesktop will never miss them. 

A nice trick is "follow mouse":

recordmydesktop --follow-mouse --width 300 -height 180 -fps 15 --use-jack system:capture_1 system:capture_2

Once you have decided the command you like (see "man recordmydesktop" for all the options) you can add a launcher on the panel. Add another one to stop recording with the command: "killall recordmydesktop" and you are done.

Cheers! Pablo

---

### Post by AutoStatic on 2010-09-16
JACK is not far better than PulseAudio. They're both sound daemons with different purposes. JACK for low-latency, real-time audio and PulseAudio for less critical desktop applications. To quote the developer of PulseAudio, JACK is for pro audio and PulseAudio for consumer audio.
Concerning JACK and gtk-recordMyDesktop: [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/621188)

I switched to ffmpeg + jack_capture myself, this allows me to record lossless screencasts.

---

