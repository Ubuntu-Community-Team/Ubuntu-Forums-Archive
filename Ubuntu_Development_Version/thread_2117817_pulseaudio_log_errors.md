---
title: "pulseaudio log errors"
date: 2013-02-19
forum: Ubuntu Development Version
---

### Post by anca-emanuel on 2013-02-19
pulseaudio[1721]: [pulseaudio] authkey.c: Failed to load authorization key '/var/lib/lightdm/.config/pulse/cookie': Invalid argument
That is after I manually created the path and the file with "" content.

Second error:
pulseaudio[1726]: [pulseaudio] core-util.c: Failed to create secure directory (/run/user/lightdm/pulse): No such file or directory


You can see this from "System Log"

---

### Post by lucazade on 2013-02-23
same here:
pulseaudio[1700]: [pulseaudio] authkey.c: Failed to open cookie file '/home/luca/.config/pulse/cookie': File o directory non esistente

---

### Post by VinDSL on 2013-02-23
> **anca-emanuel said:**
> pulseaudio[1721]: [pulseaudio] authkey.c: Failed to load authorization key '/var/lib/lightdm/.config/pulse/cookie': Invalid argument
That is after I manually created the path and the file with "" content.

Second error:
pulseaudio[1726]: [pulseaudio] core-util.c: Failed to create secure directory (/run/user/lightdm/pulse): No such file or directory


You can see this from "System Log"
Nothing concerning "core-util.c", but...

Yes, I use GDM (not LightDM) and I'm seeing...

```
pulseaudio[2580]: [pulseaudio] authkey.c: Failed to open cookie file '/var/lib/gdm/.config/pulse/cookie': No such file or directory
pulseaudio[2580]: [pulseaudio] authkey.c: Failed to load authorization key '/var/lib/gdm/.config/pulse/cookie': No such file or directory
```

Also...

```

pulseaudio[2583]: [pulseaudio] sink.c: Default and alternate sample rates are the same.
```

```
pulseaudio[4649]: [alsa-sink] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
pulseaudio[4649]: [alsa-sink] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
pulseaudio[4649]: [alsa-sink] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

---

### Post by lucazade on 2013-02-23
I get choppy sound when pulseaudio is running, it eats all the cpu.
Killing it I have a normal sound playback..

so pulseaudio seems a bit buggy at the moment!

---

### Post by edkmho on 2013-03-18
I have exactly the same error, also the skype notification sound cracking.
pulseaudio[2138]: [pulseaudio] core-util.c: Failed to create secure directory (/run/user/gdm/pulse): No such file or directory

Any help will be grateful.

---

### Post by azurkin on 2013-05-03
Have same problem with lightdm:
```
[pulseaudio] authkey.c: Failed to open cookie file '/var/lib/lightdm/.config/pulse/cookie': No such file or directory
[pulseaudio] authkey.c: Failed to load authorization key '/var/lib/lightdm/.config/pulse/cookie': No such file or directory
```
Sometimes sound doesn't work after restart. Problems appeared after upgrade to 13.04.
> **edkmho said:**
> I have exactly the same error, also the skype notification sound cracking.
I have that problems too. This answer [http://askubuntu.com/a/201747/132931](http://askubuntu.com/a/201747/132931) solved skype problem.

---

### Post by cordes-ben on 2013-10-14
I seem to have fixed the "failed to load authorization file" error by copying .config/pulse/cookie out of my primary user's homedir and into /var/lib/lightdm/.config/pulse/cookie, then chown'ing the directory and the file to lightdm:lightdm, then restarting lightdm. That made the errors go away in my log, although it didn't fix the (apparently unrelated) login problem I'm having :)

---

