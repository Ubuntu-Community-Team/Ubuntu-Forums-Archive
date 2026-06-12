---
title: "Gallium Driver changes to VESA: GF104B Board Post installation"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by blantran on 2013-04-06
I recently did a fresh install of 13.04 Beta 2 release. I installed from a USB stick where everything was displayed at the correct resolution; under details, it showed the graphics driver as Gallium 0.4 on NVCE (I have an nvidia 560 ti card). After the installation, the resolution was wrong and the graphics driver was displayed as VESA: GF104B Board - 1040050. How do I switch it to Gallium again (it seems like a hassle to get the nvidia proprietary drivers to work according to other posts -- I just want to be able to view things at the correct resolution)? Sorry if there is an answer posted somewhere as I could not find it. I'm a little new, so please provide details if possible. Thank you.

---

### Post by cariboo on 2013-04-06
The Nvidia proprietary drivers are in the repositories, you can install them using the Software Centre, just search for Nvidia. You should be able to install the 310 driver with no problems.

---

### Post by blantran on 2013-04-06
That worked perfect, thank you. I should have tried that earlier but was afraid to get caught in a mess trying to get things to display if it didn't work.

---

