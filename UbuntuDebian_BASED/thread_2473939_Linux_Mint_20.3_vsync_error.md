---
title: "Linux Mint 20.3 vsync error"
date: 2022-04-18
forum: Ubuntu/Debian BASED
---

### Post by f23948 on 2022-04-18
I am using Cinnamon edition, not Cinnamon (Edge), not MATE, not XFCE, not LMDE 5. My BIOS did sets to secure boot off and did sets to TPM off, still no luck
I went that site: [URL="https://learnubuntumate.weebly.com/screen-tearing-on-intel-graphics.html"]https://learnubuntumate.weebly.com/screen-tearing-on-intel-graphics.html
[/URL]```
Section "Device"
 Identifier "Intel Graphics"
 Driver "intel"
 Option "TearFree" "true"
EndSection
```
After I login, it gives me error.
[https://www.youtube.com/watch?v=kUhgxx24TUg](https://www.youtube.com/watch?v=kUhgxx24TUg)

---

### Post by f23948 on 2022-04-18
I did installed Linux Mint without compatibility mode

---

### Post by f23948 on 2022-04-18
admin/moderator
please move to:[https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453)

---

### Post by f23948 on 2022-04-26
Update: I did clean installed xfce edition and showing no error```
Section "Device"
 Identifier "Intel Graphics"
 Driver "i915"
 Option "TearFree" "true"
EndSection
```

---

### Post by f23948 on 2022-04-26
marked as solved

---

