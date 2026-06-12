---
title: "tiny to invisible fonts on non kde apps."
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by odror on 2012-09-22
OS: ubuntu 12.10

When running KDE in a remote desktop application such as freenx, non native kde applications, such synaptic or gnome-terminal have invisible to very tiny fonts. There is no problem if kde is running on a non-remote session or when using native kde apps. I have adjusted the dpi to 96. It did not help. any help will be appreciated.

Thanks

---

### Post by carl4926 on 2012-09-22
In KDE settings > App Appearance > GTK Styles/Fonts

Check use kde fonts in gtk apps

Might help?

---

### Post by odror on 2012-09-22
> **carl4926 said:**
> In KDE settings > App Appearance > GTK Styles/Fonts

Check use kde fonts in gtk apps

Might help?

Yes that was the default setting. It did not help.
My KDE version is 4.91
The problem is only when using kde remotely.


Thanks

---

### Post by JKyleOKC on 2012-09-30
Try setting the DPI to 125 and see if that helps; the higher the number on this setting, the larger the font will appear.

---

### Post by odror on 2012-09-30
> **JKyleOKC said:**
> Try setting the DPI to 125 and see if that helps; the higher the number on this setting, the larger the font will appear.
I have tried that. the problem is only in KDE running under nxserver. It is some incompatibility of ubuntu12.10 and nxserver3.5

---

### Post by carl4926 on 2012-10-01
As 12.10 is dev
Did you report this as a possible bug

---

### Post by odror on 2012-10-01
> **carl4926 said:**
> As 12.10 is dev
Did you report this as a possible bug
No I have have not. It might be related to a bug where gnome-terminal crash kde.

---

### Post by oldos2er on 2012-10-01
Moved to Ubuntu +1 (Quantal Quetzal)

---

