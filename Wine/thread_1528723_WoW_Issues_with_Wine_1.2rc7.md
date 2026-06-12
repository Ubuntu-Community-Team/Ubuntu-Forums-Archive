---
title: "WoW Issues with Wine 1.2rc7"
date: 2010-07-11
forum: Wine
---

### Post by EmyrB on 2010-07-11
Since yesterday (when I updated my system after a few days) WoW's sound was borked. I checked the Wine forums and nothing posted and followed the advice there of switching off OSS, then ALSA and finally using PulseAudio but this didn't help. Today I see that an update for Wine came down and now I have no sound in WoW what so ever.

Other games I have got such as Dr Who Adventures and Guild Wars work with sound and I also checked my Arch Linux box and WoW and Wine work fine.

Any ideas?

Edit: Sorry I should have said Ubuntu 10.04 64-bit.

---

### Post by elmaz on 2010-07-11
I have exactly the same issue, but after today's new update (ver 1.2~rc7-0ubuntu2) it was fixed, so maybe you should try it.

---

### Post by EmyrB on 2010-07-12
> **elmaz said:**
> I have exactly the same issue, but after today's new update (ver 1.2~rc7-0ubuntu2) it was fixed, so maybe you should try it.

Yup, that's the same version I am running and now I have no sound as opposed to just noise :(

---

### Post by YokoZar on 2010-07-12
> **EmyrB said:**
> Yup, that's the same version I am running and now I have no sound as opposed to just noise :(

no sound is still typical, unfortunately.

killall -9 pulseaudio before running helps sometimes (as does closing other sources of audio)

---

### Post by hikaricore on 2010-07-13
There's a patch to properly support pulseaudio in wine but for some reason it keeps being ignored.

---

### Post by cburner on 2010-07-13
You can try configuring wine with the command```
padsp winecfg
``` and ticking alsa, if still not working try OSS. Also start WoW with the command ```
padsp wine path/to/WoW/wow.exe
```

---

### Post by search66 on 2010-07-13
The only issue I have with sound is when I'm running Mangler at the same time... Other than that, it's been fine.

---

### Post by dardack on 2010-07-15
> **hikaricore said:**
> There's a patch to properly support pulseaudio in wine but for some reason it keeps being ignored.

If you read his blog he tells why:

 A development branch of Wine aims to implement the new mmdevapi from Vista using OpenAL, which has native pulseaudio support on linux already. Once this is complete winmm and directsound will be implemented on top of mmdevapi. WinePulse will be made redundant by these changes. Thus, this patch shall be maintained only as a stopgap until the new audio system is available. For historical aspects, social commentary and flames see [http://bugs.winehq.org/show_bug.cgi?id=10495](http://bugs.winehq.org/show_bug.cgi?id=10495) .


source for winepulse:

[http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)

---

### Post by dardack on 2010-07-15
> **search66 said:**
> The only issue I have with sound is when I'm running Mangler at the same time... Other than that, it's been fine.

If you feel comfortable compiling your own wine (i do for a faux HW OpenGL cursor patch i wrote for 1.2rc*, and for winepulse) compile in WinePulse, you'll get pulseaudio in wine, which allows both mangler/wow to run together great.

---

