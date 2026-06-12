---
title: "Ubuntu 13.04 locale error"
date: 2013-04-18
forum: Ubuntu Development Version
---

### Post by Waddle on 2013-04-18
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_TIME = "ko_KR",
    LC_MONETARY = "ko_KR",
    LC_ADDRESS = "ko_KR",
    LC_TELEPHONE = "ko_KR",
    LC_NAME = "ko_KR",
    LC_MEASUREMENT = "ko_KR",
    LC_IDENTIFICATION = "ko_KR",
    LC_NUMERIC = "ko_KR",
    LC_PAPER = "ko_KR",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory





locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=ko_KR
LC_TIME=ko_KR
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=ko_KR
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=ko_KRw this can be fixed. 
LC_NAME=ko_KR
LC_ADDRESS=ko_KR
LC_TELEPHONE=ko_KR
LC_MEASUREMENT=ko_KR
LC_IDENTIFICATION=ko_KR
LC_ALL=
 are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory



Anyone know how this can be fixed. I am located in Korea but want my OS in English. When I installed the ATI video drivers CCC comes up in Korean.

Thank you!

---

### Post by dino99 on 2013-04-18
reset your locales, then set them back
[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

if the problem persist, then report against libencode-locale-perl

note: be sure that non genuine packages (from ppas) conflict the config

---

### Post by Waddle on 2013-04-18
Solved..."Most users want a single locale to be used for all aspects of their session. In this case, the GUI provided by **System Settings -> Language Support** does the right thing."

---

