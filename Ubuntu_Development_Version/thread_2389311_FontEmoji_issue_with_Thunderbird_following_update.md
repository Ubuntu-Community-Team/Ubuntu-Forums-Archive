---
title: "Font/Emoji issue with Thunderbird following update"
date: 2018-04-15
forum: Ubuntu Development Version
---

### Post by Psychobudgie on 2018-04-15
Since updating to the current Beta the following glitch has manifested in Thunderbird. It would seem that any email with an emoji attached is rendering with incorrect dimensions. I have tried reinstalling Thunderbird, nvidia drivers and reinstalling/regenerating fonts to no avail. Hopefully a simple fix but it escapes me. This only seems to affect Thunderbird and didn't occur with the same version running in 17.10 or on other OS.

[ATTACH=CONFIG]279302[/ATTACH]

---

### Post by jbicha on 2018-04-15
I believe this issue is fixed in the Thunderbird Beta. Thunderbird 60 should be released soon (maybe June?).

---

### Post by Psychobudgie on 2018-04-15
Thanks, that fixes the issue.

---

### Post by billstei on 2018-05-08
Assuming the problem to be over-sized emojis in the Subject and From lines, this issue remains (as of this post on 5/8/2018) in Bionic 18.04 and Thunderbird 52.7.0, and can be worked around by uninstalling package fonts-noto-color-emoji (Version 0~20180424-0ubuntu1) and installing package fonts-symbola.

---

### Post by cariboo on 2018-05-09
> **billstei said:**
> Assuming the problem to be over-sized emojis in the Subject and From lines, this issue remains (as of this post on 5/8/2018) in Bionic 18.04 and Thunderbird 52.7.0, and can be worked around by uninstalling package fonts-noto-color-emoji (Version 0~20180424-0ubuntu1) and installing package fonts-symbola.

Bionic has been released, Thread closed. Start a thread in [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331").

---

