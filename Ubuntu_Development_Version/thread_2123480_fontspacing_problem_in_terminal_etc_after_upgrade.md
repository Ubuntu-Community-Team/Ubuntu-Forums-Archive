---
title: "fontspacing problem in terminal etc after upgrade"
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by Cloud79 on 2013-03-08
After upgrade from 12.10 to 13.04 i get this weird fontproblem, no matter wich font i use (fonts in firefox/chrome looks good tough). Any ideas how to fix? Same problem if I create a new local user with a clean homedirectory

[IMG]http://www.cludden.se/download/screen.png[/IMG]

---

### Post by dino99 on 2013-03-08
from nautilus, you should now only have .fontconfig folder, so i suppose the oldish .fonts.conf (or so, i does not remember how it was) is confusing the system. Simply delete or rename the old "fonts" setting file(s)

---

### Post by Cloud79 on 2013-03-08
No that doesn't seem to be it. I have tried with a new user with (blank slate), same problem. This is OS related not user

---

### Post by ajgreeny on 2013-03-08
You have obviously chosen a custom font as the tick box to use system font is not selected, even though I think it may be what the system normally uses anyway, but have you tried using a different font for the terminal?

---

### Post by Cloud79 on 2013-03-08
Yes i have tried monospace, ubuntu mono etc. It isn't just the terminal font that has problems. Maybe a reinstall is the only solution

---

### Post by schragge on 2013-03-08
Hmm, looks like your terminal uses proportional sans serif font instead of monospaced one. Weird. What does* fc-match Monospace* show?

---

### Post by Cloud79 on 2013-03-08
linus@linux8:~$ fc-match Monospace
DejaVuSansMono.ttf: "DejaVu Sans Mono" "Book"

---

### Post by schragge on 2013-03-08
I presume DejaVu Sans Mono is present on your system. Try
```

dpkg -l ttf-dejavu\*
ls /usr/share/fonts/truetype/ttf-dejavu
sudo fc-cache -r
fc-match Monospace file

```Then re-login.

---

### Post by Cloud79 on 2013-03-08
Sorry, same problem. I have nvidia graphics (proprietary driver) used, could it be this to blame in 13.04?

linus@linux8:~$ dpkg -l ttf-dejavu\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-================================================================
ii  ttf-dejavu                    2.33-3ubuntu2       all                 Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra
ii  ttf-dejavu-core               2.33-3ubuntu2       all                 Vera font family derivate with additional characters
ii  ttf-dejavu-extra              2.33-3ubuntu2       all                 Vera font family derivate with additional characters
linus@linux8:~$ ls /usr/share/fonts/truetype/ttf-dejavu
DejaVuSans-BoldOblique.ttf           DejaVuSans-ExtraLight.ttf       DejaVuSans.ttf                       DejaVuSerifCondensed.ttf
DejaVuSans-Bold.ttf                  DejaVuSansMono-BoldOblique.ttf  DejaVuSerif-BoldItalic.ttf           DejaVuSerif-Italic.ttf
DejaVuSansCondensed-BoldOblique.ttf  DejaVuSansMono-Bold.ttf         DejaVuSerif-Bold.ttf                 DejaVuSerif.ttf
DejaVuSansCondensed-Bold.ttf         DejaVuSansMono-Oblique.ttf      DejaVuSerifCondensed-BoldItalic.ttf
DejaVuSansCondensed-Oblique.ttf      DejaVuSansMono.ttf              DejaVuSerifCondensed-Bold.ttf
DejaVuSansCondensed.ttf              DejaVuSans-Oblique.ttf          DejaVuSerifCondensed-Italic.ttf
linus@linux8:~$ sudo fc-cache -r
linus@linux8:~$ fc-match Monospace file
:file=/usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf

---

### Post by serdotlinecho on 2013-03-08
Do you have gnome-tweak-tool or any similar tool installed? If so, have you tried checking the fonts settings?

---

### Post by Cloud79 on 2013-03-14
I checked wich fonts where used by application (lsof)

I removed the package fonts-sil-padauk and everything is fine. Strange indeed

---

