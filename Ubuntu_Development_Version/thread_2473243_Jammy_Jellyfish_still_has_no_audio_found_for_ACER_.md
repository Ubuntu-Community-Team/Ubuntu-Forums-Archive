---
title: "Jammy Jellyfish still has no audio found for ACER 317 Chromebook"
date: 2022-03-29
forum: Ubuntu Development Version
---

### Post by maxmcgrath on 2022-03-29
Hello all,

22.04 still isn't able to find the audio speakers on my ACER 317 Chromebook. It says that "dummy output" is found. All older versions of Linux distros also have the same issue, I am wondering if the "tech" is to "new" or "odd", but its not that new... ACER calls them upward facing speakers... As expected the speakers work find with the chrome OS that it came with... But I want off that OS.

Any one have any ideas on what I should do.

Thanks!

---

### Post by Frogs Hair on 2022-03-29
Chrome books aren't intended to host other operating systems so I'm not sure there is an officially supported solution. The 22.04 Beta release is due in two days and I wouldn't expect sweeping changes before the final release. I don't know that filing a bug for that hardware would promt any urgency to solve the problem. You may have wait for feedback from someone with the same system.

---

### Post by maxmcgrath on 2022-03-30
Well that is a bummer, I was really hoping to get this Chromebook off of ChromeOS.

Does any one have any ideas?

---

### Post by Frogs Hair on 2022-03-31
> **maxmcgrath said:**
> Well that is a bummer, I was really hoping to get this Chromebook off of ChromeOS.

Does any one have any ideas?

I would search for methods for troubleshooting no sound in Ubuntu. The Ubuntu wiki and other sources have procedures for this. Off the top of my head the following command will verify if your sound card is detected.```
 lspci 
```

---

