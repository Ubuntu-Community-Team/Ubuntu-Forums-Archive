---
title: "32 ch rme raydat soundcard with linux ?"
date: 2012-07-07
forum: Ubuntu Studio
---

### Post by Gusss on 2012-07-07
I need to use all 32 adat channels of my RME raydat soundcard with ubuntu studio or other distro - will it work ?

---

### Post by sgx on 2012-07-08
If the card will work in stereo, you might get lucky,
and have reaper in a wineasio setup, see the 32 multichannels.
I would ask at the ardour forum instead, because high-end
audio cards are much more likely to be considered by
studio engineers, who would hang out there, if anywhere.

cat /proc/asound/cards
arecord -l
aconnect -i
lspci
lsmod

those commands should have common phrases in their output,
if your card is supported by your kernel/alsa version.
Cheers

---

