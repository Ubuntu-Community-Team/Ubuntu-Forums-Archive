---
title: "No sounds mixer controls in Unity"
date: 2013-01-18
forum: Ubuntu Development Version
---

### Post by MadNachos on 2013-01-18
Since I installed 13.04 I have not had a working sound mixer in Unity, the mixer exists but it does not see a sound device so the controls don't work. I have been having to use AlsaMixer. Is this a common issue (search didn't find anything)? Can anyone point me in the right direction to fix it?

Thanks much.

---

### Post by anca-emanuel on 2013-01-19
Try:
sudo apt-get install --reinstall pulseaudio
sudo reboot

---

### Post by zika on 2013-01-19
> **MadNachos said:**
> Since I installed 13.04 I have not had a working sound mixer in Unity, the mixer exists but it does not see a sound device so the controls don't work. I have been having to use AlsaMixer. Is this a common issue (search didn't find anything)? Can anyone point me in the right direction to fix it?

Thanks much.Did You try using pavucontrol to configure PulseAudio...?
> **anca-emanuel said:**
> Try:
sudo apt-get install --reinstall pulseaudio
sudo rebootBig hammer approach...
Reboot is not necessary, PA can be restarted nicely... But even reinstall, I think is not necessary... Just tuning...

---

### Post by MadNachos on 2013-01-20
> **anca-emanuel said:**
> Try:
sudo apt-get install --reinstall pulseaudio
sudo reboot

No dice.

---

### Post by MadNachos on 2013-01-20
> **zika said:**
> Did You try using pavucontrol to configure PulseAudio...?
Big hammer approach...
Reboot is not necessary, PA can be restarted nicely... But even reinstall, I think is not necessary... Just tuning...

I have never used pavucontrol but I installed it and just ran it and it says 'connection to pulseaudio failed'. So I checked to see if pulse was running and it was not. Running 'pulseaddio' from bash gives me:

```
W: [pulseaudio] source.c: Default and alternate sample rates are the same.
E: [pulseaudio] module.c: Failed to open module "module-esound-protocol-unix": file not found
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

```

So at least I have an idea of where to go next.

ETA: Looks like installing pulseaudio-esound-compat solved the issue. Others have also had this issue as noted here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1078543")

---

