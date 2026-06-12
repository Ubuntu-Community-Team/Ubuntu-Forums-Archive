---
title: "Firefox starts up with adverts"
date: 2010-06-06
forum: Security
---

### Post by Ko$ on 2010-06-06
I don`t know how did that happen but now after reboot my firefox starts with pocker and porno web-pages. I don`t play pocker, never did. Yes, a couple of times I did watch... But I didn`t install or change anything (extentions or add-ons) in firefox. I acrually didn`t change anything in system and now firefox starts up with those adverts. In settings of firefox I have "show last opened pages". Of course I didn`t close ever my firefox with a couple of adverts. And it does only after reboot. So, if I close it now and open again it will show the last pages. But after reboot ... Well, if I saw something like that in windows I`d think that there is a virus or something else like adverts-virus but I`m in kubuntu. Kubuntu 10.04.

Anyone can help?

---

### Post by an0dos on 2010-06-06
Try doing the following:

1) In firefox go to "Edit" --> "Preferences". Change "When Firefox starts:" to "Show a blank page".
2) Then click on the privacy tab and click on "clear your recent history" and clear out everything.
3) Reboot your computer and see if it is still having problems.

You may want to consider using the "noscript" add-on for firefox. Browsers are the security soft spot for every home computer whether it runs Windows, OS-X, or Linux.

---

### Post by Rubi1200 on 2010-06-06
> **an0dos said:**
> Browsers are the security soft spot for every home computer whether it runs Windows, OS-X, or Linux.

+1

I suggest you also read the following sticky:

[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by Ko$ on 2010-06-06
thanks a lot !

---

### Post by lovinglinux on 2010-06-08
I would recommend creating a new profile and then installing [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/).

To create a new profile, start it form a terminal with:

```
firefox -P
```

If you want to preserve some things from your current profile, see [this](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

---

