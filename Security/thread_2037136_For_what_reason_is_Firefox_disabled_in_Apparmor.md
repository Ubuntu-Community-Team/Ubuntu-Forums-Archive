---
title: "For what reason is Firefox disabled in Apparmor"
date: 2012-08-03
forum: Security
---

### Post by houseworkshy on 2012-08-03
This is my first proper attempt to get my head round apparmor,   it was
too much for me before and my yet be again, so please forgive what may be a very obvious question.  I noticed that firefox was being skipped, searched and found

"Since Ubuntu 9.10 (Karmic), AppArmor ships with a profile for Firefox which is disabled by default. 
You can enable it using the following command: 
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox"

So before doing that, I'd like to know why as there is bound to be
a good reason.

I've read that addon's can be affected ( that's logical )
So the one's I like to use are; no-script, better privacy, 
downthemall, and add to search bar.

The Firefox version is 14.0.1 Mozilla Firefox for Ubuntu canonical - 1.0
I'm using Ubuntu 10.04 64bit ( the Gnome2 version )

---

### Post by Hungry Man on 2012-08-03
Mostly for ease of use.

One example is if I download a text file from Firefox and double click it from the download manager Apparmor would block Firefox from being able to execute the program that reads text files.

---

### Post by vasa1 on 2012-08-03
Historical but "official" reason:
>  Users must opt-in to using the profile and therefore should know that AppArmor confinement could cause firefox to behave unexpectedly.
Source: [https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile](https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile)

---

