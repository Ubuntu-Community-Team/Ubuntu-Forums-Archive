---
title: "[SOLVED] Conky transparent background?"
date: 2020-08-30
forum: The Cafe
---

### Post by RallyDarkstrike on 2020-08-30
Hey all!

Years ago, I had a netbook with Conky and I had a very  nice semi-transparent background with non-transparent foreground text,  etc.

I cannot remember for the life of me how to get a semi-transparent background behind my current conky display? It's fully transparent except for the text, symbols, graphs, etc....but I want a semi-transparent black/gray background behind the conky window to make the text more legible on light-colored or white wallpapers...?
[ATTACH=CONFIG]286838[/ATTACH]

Any help in doing so would be appreciated! :D

Please find my .conkyrc file attached if anybody has any ideas: [ATTACH]286837[/ATTACH]

---

### Post by drpjkurian on 2020-08-31
Hi
I'm not sure, but you may try changing the lines 44 and 46 in the conky file to get the desired effect. You may type 'no' for the transparent window. Colour I'm not sure, please google it find the appropriate color code. Please backup your original conky file it goes haywire.

---

### Post by RallyDarkstrike on 2020-08-31
Those two lines seem to already be set to the correct settings for transparency...?

own_window_transparent is set to yet and (line 44) and own_window_color is 000000 which should be black, but is completely transparent in my case. Adjusting own_window_color does give me transparency with colors or white, but I cannot get black?

---

### Post by deadflowr on 2020-08-31
See if this solution found here work:
[https://ubuntuforums.org/showthread.php?t=2441576]("https://ubuntuforums.org/showthread.php?t=2441576")

---

### Post by RallyDarkstrike on 2020-08-31
I figured it out! I had to turn own_window_transparent to 'no' and then use own_window_argb_visual set to 'yes' and use own_window_argb_value to adjust the transparency amount. :)

---

### Post by drpjkurian on 2020-08-31
Good, you resolved the issue. Please mark the thread solved.

---

