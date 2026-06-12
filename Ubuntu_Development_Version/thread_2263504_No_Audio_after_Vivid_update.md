---
title: "No Audio after Vivid update"
date: 2015-02-01
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-02-01
Have been running Vivid sucessfully for several weeks until an update in the last 3 days left the system without an audio device.  Going to Settings and Sound all I have now is the Dummy device.  Use this system to stream radio/music daily so it had been working.  Just as a check I rebuild the system from the 1/31/15 daily build and have the same problem.  Do not see any error in dmesg or syslog to indicate where the problem is.  Have removed/purged alsa-base and pulseaudio but continue to have the problem.  Suggestions on what I should try or what documentation I should gather for a bug report?

---

### Post by zika on 2015-02-01
> **crcarson said:**
> Have been running Vivid sucessfully for several weeks until an update in the last 3 days left the system without an audio device.  Going to Settings and Sound all I have now is the Dummy device.  Use this system to stream radio/music daily so it had been working.  Just as a check I rebuild the system from the 1/31/15 daily build and have the same problem.  Do not see any error in dmesg or syslog to indicate where the problem is.  [SIZE=4][COLOR=#00ffff]Have removed/purged alsa-base and pulseaudio[/COLOR][/SIZE] but continue to have the problem.  Suggestions on what I should try or what documentation I should gather for a bug report?What layer is now supposed to process audio?

---

### Post by crcarson on 2015-02-01
Don't have an answer for "what layer".  Use VLC to stream the audio and on my 14.04 system the audio devices in Settings are Digital Output (S/PIDF) - Build-in Audio and Analog Output - Built-in Audio.  VLC is playing through this.  In the 15.04 system missing both those devices.

---

### Post by zika on 2015-02-01
Re-install at least ALSA so You get back S/PDIF... ;)
Check, once ALSA is back, in AlsaMixer levels...
If I were You I would re-install PulseAudio also, but...
I'm using S/PDIF also so...

---

### Post by crcarson on 2015-02-01
> **zika said:**
> Re-install at least ALSA so You get back S/PDIF... ;)
Check, once ALSA is back, in AlsaMixer levels...
If I were You I would re-install PulseAudio also, but...
I'm using S/PDIF also so...

Removed both Alsa-basic and pulseaudio and re-installed Alsa-basic.  Attemped to start alsamixer but it failed with message "cannot open mixer: No such file or directory".  Checking Settings and Sound I now have no devices listed (even dummy is gone).  
(this is the second attempt to post so you may see this duplicated)

---

### Post by zika on 2015-02-01
Did You try```
[FONT=Ubuntu Mono]sudo alsa force-reload
```...[/FONT]

---

### Post by crcarson on 2015-02-02
> **zika said:**
> Did You try```
[FONT=Ubuntu Mono]sudo alsa force-reload[/FONT]
```[FONT=Ubuntu Mono]...[/FONT]

Yes, tried it, no change.  It's obvious that I'm in over my head here and the only thing I can do is try what's asked and report what I see.  Did bring up 15.04 and apply today Updates (apt-get update and upgrade) and saw no change, no devices at all in my Setting - Sound.  Re-installed pulseaudio and now the Dummy sound device is back.

---

### Post by xc3RnbFO8P on 2015-02-02
Do you dual boot Win8? check this:

[http://askubuntu.com/questions/464388/no-sound-from-laptop-speakers-in-ubuntu-14-04-after-booting-into-windows-8-1]("http://askubuntu.com/questions/464388/no-sound-from-laptop-speakers-in-ubuntu-14-04-after-booting-into-windows-8-1")

---

### Post by crcarson on 2015-02-02
> **Ringi said:**
> Do you dual boot Win8? check this:

[http://askubuntu.com/questions/464388/no-sound-from-laptop-speakers-in-ubuntu-14-04-after-booting-into-windows-8-1](http://askubuntu.com/questions/464388/no-sound-from-laptop-speakers-in-ubuntu-14-04-after-booting-into-windows-8-1)

This problem is resolved by booting with systemd (add init=/lib/systemd/systemd to the boot command).

---

