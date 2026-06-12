---
title: "audio port sharing"
date: 2008-07-17
forum: Ubuntu Studio
---

### Post by vivichrist on 2008-07-17
Is there any way I can get apps to all share the audio port? .... this is very frustrating and annoying problem in GNU/linux.

---

### Post by thorgal on 2008-07-18
what do you mean by port ? do you mean "apps sharing the same device at the same time" ?
looks like you're using old and deprecated OSS because ALSA comes with the dmix plugin which is the default. And the newer pulseaudio server is meant to make the device sharing even more transparent and extend it to LAN contexts. And finally, you have the pro audio server JACK which provides amazing routing capabilities between applications themselves and your underlying hardware.

I suggest you describe your setup before complaining about linux ;)

---

### Post by vivichrist on 2008-07-18
yes I know but some apps Qsampler for instance hoggs the port where as other apps i.e totem and nautilus can simultaneously use the audio port. how can you tell whether an app is using ALSA, OSS or other? my setup is not special.

---

