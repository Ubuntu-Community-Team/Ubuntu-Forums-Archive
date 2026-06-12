---
title: "Help with partition recovery"
date: 2010-03-05
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-05
Since I can't get any [help with ntfsresize]("http://ubuntuforums.org/showthread.php?p=8911234"), could someone please walk me through the best/safest way to recover an ntfs partition deleted with fdisk?

Please keep in mind that

[LIST=1]
[*]This is a server - no X, no GUI.
[*]My server has no CD/DVD drive so I can't use a live CD or other bootable utility discs
[*]The drive containing the deleted partition is an external (USB) drive
[/LIST]
Thank you for your time and consideration.

---

### Post by cdenley on 2010-03-05
Did the partition fill the entire drive? How was it partitioned before and how is it partitioned now?
```

sudo fdisk -l

```

---

### Post by Donny Bahama on 2010-03-05
Thanks for the response!

I was composing a lengthy response when I realize the before and after was identical. I had been doing all this from my laptop (via putty - my server is headless) and was forced to disconnect to take my laptop somewhere. As a result, I never wrote the changed partition table.

Crisis averted!

Thanks for your time and assistance!

---

