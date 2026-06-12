---
title: "MAudio Delta 2496 Envy24 Mix Issue"
date: 2013-03-02
forum: Ubuntu Studio
---

### Post by abhayadevs on 2013-03-02
Hi,

Ubuntu Studio 12.04
Versions: Envy Control 24 Utility: 1.0.4.0 (Mudita24)
QJack - 0.3.8-1/ Jackd: 5

I have installed a new Delta2496 card and i am able to see the mix control output in JACK as CAPTURE_1 and CAPTURE_2. Also able to connect to Ardour for recording. Now issue is that, the mix control software is not working or Ardour is getting input only from the analog input (HW Input 1&2) but not from SPDIF. I tried Muting the inputs from the Envy24 mix control software but seems to be not working. However the levels in the mix control is ok with the 2 inputs (Analog and SPDIF). If i mute one only the another is shown in the "Digitzal Mixer".

Any fix for getting the SPDIF signal also in to Ardour?

appreciate your support...

Regards,
abhayadevs

---

### Post by abhayadevs on 2013-03-04
> **abhayadevs said:**
> Hi,

Ubuntu Studio 12.04
Versions: Envy Control 24 Utility: 1.0.4.0 (Mudita24)
QJack - 0.3.8-1/ Jackd: 5

I have installed a new Delta2496 card and i am able to see the mix control output in JACK as CAPTURE_1 and CAPTURE_2. Also able to connect to Ardour for recording. Now issue is that, the mix control software is not working or Ardour is getting input only from the analog input (HW Input 1&2) but not from SPDIF. I tried Muting the inputs from the Envy24 mix control software but seems to be not working. However the levels in the mix control is ok with the 2 inputs (Analog and SPDIF). If i mute one only the another is shown in the "Digitzal Mixer".

Any fix for getting the SPDIF signal also in to Ardour?

appreciate your support...

Regards,
abhayadevs

When i chnaged the input device the PCI hardware i could have more inputs in the "Jack" and the 9,10 are the SPDIF L and R.

nice isn't it? more later

---

