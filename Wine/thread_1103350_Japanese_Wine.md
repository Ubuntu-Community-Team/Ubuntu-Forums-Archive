---
title: "Japanese Wine"
date: 2009-03-22
forum: Wine
---

### Post by considerable on 2009-03-22
About a week ago I got some programs to teach myself Japanese, and I wanted to install them under Wine. I do that, but, to my surprise, the interface is in Japanese, which is weird, seeing that I installed them under WindowsXP and the interface was in English. I gave up.
Today I downloaded another unrelated application. I installed it under Wine, and to my surprise, it opened a windows terminal (to run the GUI from it, you know what I mean), but the contents of the terminal were in Japanese (what!). I think that something happened to my imaginary Windows settings, would anyone help me to restore the language to English?
Thanks in advance.

---

### Post by cogadh on 2009-03-23
Do you have anything else installed with Wine that you need to keep? If not, you can just delete the .wine directory from your home directory, which will wipe out all of your current Wine settings and any apps that are installed. Then the next time you use or configure Wine, that directory will be recreated with the default settings, including language.

---

### Post by MYGRA1N on 2009-03-23
> **considerable said:**
> About a week ago I got some programs to teach myself Japanese, and I wanted to install them under Wine. I do that, but, to my surprise, the interface is in Japanese, which is weird, seeing that I installed them under WindowsXP and the interface was in English. I gave up.
Today I downloaded another unrelated application. I installed it under Wine, and to my surprise, it opened a windows terminal (to run the GUI from it, you know what I mean), but the contents of the terminal were in Japanese (what!). I think that something happened to my imaginary Windows settings, would anyone help me to restore the language to English?
Thanks in advance.

Teaching yourself Japanese is a nightmare! You may wanna try a more managed approach.:popcorn:

---

### Post by considerable on 2009-03-23
Well, thanks for the help, but I did as you suggested, and I installed the program again, ran it once, everything was cool and English, ran it a second time, and, surprise, everything turned Japanese again.
Does anyone know where, in particular, is the wine language setting stored?

---

### Post by MYGRA1N on 2009-03-23
where did my comment go?? =O

---

### Post by NightMKoder on 2009-03-23
What's the output of locale? I don't think wine has its own locale setting, or if it does, it should be in the registry (which you successfully nuke when you do rm -Rf .wine).

If you get this problem resolved, I think the fix to your first problem may be @ [http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628) .

---

### Post by considerable on 2009-03-24
locale:
```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```
> **NightMKoder said:**
> What's the output of locale? I don't think wine has its own locale setting, or if it does, it should be in the registry (which you successfully nuke when you do rm -Rf .wine).
Been there, done that (many times). There's no use.

> **NightMKoder said:**
> If you get this problem resolved, I think the fix to your first problem may be @ [http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628) .
Which part would be relevant to my problem? I don't see anything there.


EDIT: Resigned, I did everything in the thread you provided, and now the splash screen of the program and some windows are in English. Weird.

---

### Post by MYGRA1N on 2009-03-24
heyyyy. out of curiousity have you downloaded/enabled japanese language support for UBUNTU from system/administaration/language support ?

---

### Post by considerable on 2009-03-25
> **MYGRA1N said:**
> heyyyy. out of curiousity have you downloaded/enabled japanese language support for UBUNTU from system/administaration/language support ?

Yep.

---

