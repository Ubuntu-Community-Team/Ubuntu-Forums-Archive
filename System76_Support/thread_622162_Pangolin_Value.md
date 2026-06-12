---
title: "Pangolin Value?"
date: 2007-11-24
forum: System76 Support
---

### Post by EmptyCinema on 2007-11-24
Is it just me, or are the Pangolin value specs wrong?  The Pangolin I just received shows a fast ethernet network adapter (NOT gigabit, as advertised) and a different audio chipset than listed on the site.

---

### Post by thomasaaron on 2007-11-26
Regarding the gigabit/fast ethernet connector: send an email to support(at)system76.com with the output of this command: sudo dmidecode >> ~/Desktop/dmidecode.txt

Regarding the sound card, it should be an ALC 268. Double-click your speaker icon. In the resulting window, go to File > Change Device. Does it show an option for: ALC268? You don't want to select it. But it should be there.

---

