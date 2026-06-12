---
title: "Wine Lagging Computer a little."
date: 2009-09-26
forum: Wine
---

### Post by zaduma on 2009-09-26
Wine version is 1.0.1, I installed it from the repositories.

As my title says it lags my computer.

When I start it these errors appear (this is when I run winecfg)

fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ce059e8, overlapped 0x7ce059cc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/zaduma/.wine' has been updated.
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer


when i run wine notepad it is reponsive, but sometimes on larger applications it takes a while for the application to start up and when it does, my computer is very slow.

Computer specs:
Intel Core 2 Duo E8400 @ 3.6 GHz
ATI Radeon HD 4850 (with binary drivers installed.)

My main audio device is HDA Intel, I do not need HDA ATI HDMI, because I do not connect my monitor through HDMI.

Thanks for your help. I'll provide additional information as needed within 3 minutes of you asking me. (blackberry + email updates).

---

### Post by hikaricore on 2009-09-26
None of what you posted is an error of any kind..
Are you saying that your whole system crawls or that it just starts slowly?
Sometimes things just start slowly in WINE, tis a common issue.
How much ram do you have?

---

### Post by Meow27 on 2009-09-26
from what i understand, when wine is run for the first time, or once in a while, (first time as in after a boot) wine shotguns the wine server files as fast as it can to get everything loaded.

try running a small program first then your bigger ones that you are having trouble with. see if its still slow

---

