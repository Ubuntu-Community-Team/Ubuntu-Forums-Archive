---
title: "Weird WINE error showing up when i try to run this program"
date: 2009-03-15
forum: Wine
---

### Post by 133794m3r on 2009-03-15
```

:~$ env WINEPREFIX="/home/mac/.wine" wine "C:\Perfect World Multilanguage Service\patcher\patcher.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  458
  Current serial number in output stream:  458

```
what the hell is this ALSA_CheckSetVolume and this 'PCM Playback Volume'?

---

