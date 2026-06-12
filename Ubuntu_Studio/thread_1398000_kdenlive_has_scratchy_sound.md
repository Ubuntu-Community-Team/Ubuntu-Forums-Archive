---
title: "kdenlive has scratchy sound"
date: 2010-02-03
forum: Ubuntu Studio
---

### Post by zander1013 on 2010-02-03
hi,

running 9.10 on lenovo t60. i just installed kdenlive and it seems okay except for an unbearable scratchy noise that comes over the audio on a .mov file that otherwise plays fine.

there is another report of this same problem on t60 running 9.10 on the kdenlive forum. no solution has been found yet.

please advise.

---

### Post by LuridCinema on 2010-02-04
Sometimes you get that if you import the audio at 48000 hz and export / render at 41000 hz or vise-versa. Check if your project audio sample rate is high enough. some settings
renders audio at 44100 Hz. If you have audio content that is sampled at
48000 Hz, simply change the project settings to match the highest sample
rate in your project.

---

### Post by zander1013 on 2010-02-04
> **LuridCinema said:**
> Sometimes you get that if you import the audio at 48000 hz and export / render at 41000 hz or vise-versa. Check if your project audio sample rate is high enough. some settings
renders audio at 44100 Hz. If you have audio content that is sampled at
48000 Hz, simply change the project settings to match the highest sample
rate in your project.

the clip audio is recorded at 44.1khz. i can't find the project audio settings you have mentioned.

---

