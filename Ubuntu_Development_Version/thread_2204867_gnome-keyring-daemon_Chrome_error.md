---
title: "gnome-keyring-daemon Chrome error"
date: 2014-02-10
forum: Ubuntu Development Version
---

### Post by VMC on 2014-02-10
This has always work before in the past, but not anymore. Yesterday and today's gnome ISO has resulted in a strange keyring error.

My normal procedure is to install the latest ISO, then install Chrome. After which, the gnome-keyring-daemon would first appear. All I had to do was blank the password options. Now that causes some sort of error. The screen blanks and then comes back missing windows decorations. If tweak was activated, then there all gone.

The Password & Keys (Seahorse), is missing the default Certificate. If I do give it a a password, then default is created but is always locked. Deleting it results in the previous behavior.

I have searched and found nothing that works. I've check the "/etc/xdg/autostart". There's three keyring files there, but they are the same as Xubuntu, and it works.

I want to know if anyone else has seen this problem. I don't think just doing updates will suffice. To reproduce my problem, one needs to install today's ISO, and then install Chrome. After which when you launch Chrome is when this all starts.

---

