---
title: "GTK apps freeze if non root in kubuntu raring"
date: 2012-12-27
forum: Ubuntu Development Version
---

### Post by Panagiotis Papadakos on 2012-12-27
Hello everybody.

Since I upgraded to raring (from the early days), I notice frequent freezes when I use gtk apps like firefox, chrome, pidgin, darktable in the kde environemt. The only solution I have found is to run them as sudo. I created new users to see if this is a configuration problem but the problem persists.

Initially I thought it was a kwin_gles and I reported it to the kde bugtracker [https://bugs.kde.org/show_bug.cgi?id=310487](https://bugs.kde.org/show_bug.cgi?id=310487).

These applications seem to work ok in fvwm.

So does anybody has any suggestions? Somehow I feel it is a permission problem?

P.S.
Happy new year to everybody.

---

### Post by oldos2er on 2012-12-27
Moved to Ubuntu +1 (Raring Ringtail).

---

### Post by Panagiotis Papadakos on 2012-12-30
Since there is no answer, I guess I am the only one with this problem.
Probably it is related to some misconfiguration of my ubuntu system (I initially installed  7.10 gutsy release and have been updating to each development branch).

So has anybody  any idea about which packages would help by reinstallation or
which files in /etc I should update/change?

Thanks in advance

Papadakos Panagiotis

---

### Post by sonnet on 2012-12-30
> **Panagiotis Papadakos said:**
> Since there is no answer, I guess I am the only one with this problem.
Probably it is related to some misconfiguration of my ubuntu system (I initially installed  7.10 gutsy release and have been updating to each development branch).

So has anybody  any idea about which packages would help by reinstallation or
which files in /etc I should update/change?

Thanks in advance

Papadakos Panagiotis
I have Kubuntu raring, but I'm not experiencing your bug.
On the other side, I've been plagued by random freezes of the system. But they're not related neither to gtk+ or kde.

---

### Post by Panagiotis Papadakos on 2012-12-30
> **sonnet said:**
> I have Kubuntu raring, but I'm not experiencing your bug.
On the other side, I've been plagued by random freezes of the system. But they're not related neither to gtk+ or kde.
I was thinking maybe it is related to [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1075928](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1075928) ?
I am on 64 bits. What about you?

---

### Post by BigCityCat on 2012-12-30
This may be a better place to go for your questions.

[http://www.kubuntuforums.net/forumdisplay.php?178-Pre-Release-Testing](http://www.kubuntuforums.net/forumdisplay.php?178-Pre-Release-Testing)

---

### Post by caryb on 2013-01-01
Am having issues on Kubuntu 64bit with Firefox & Thunderbird, these apps freeze my system until I close them.

Cary

---

### Post by Zomp on 2013-04-23
> Since there is no answer, I guess I am the only one with this problem.

You are not alone - Firefox, Thunderbird and Pidgin freeze to me also... (Newly installed 64bit Kubuntu Daily from 21st April.)

---

### Post by Branimir on 2013-04-23
Perhaps it is related  to oxygen-gtk bug? For example freeciv-gtk3(memory leak) and leafnode(segfaults) have problems when running under those.
Possible other.

---

