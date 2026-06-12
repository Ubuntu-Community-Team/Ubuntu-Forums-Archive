---
title: "Can LibreOffice 5.0.4.2 be used with gtk3?"
date: 2015-12-23
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-12-23
Can LibreOffice 5.0.4.2 be used with gtk3? If yes, will it be possible with 14.04 LTS?

---

### Post by ajgreeny on 2015-12-23
Not sure about 5.4.0.2 but 5.3.0.2 certainly works well with 14.04 and I have it on my Xubuntu trusty machine.

I use the LO ppa at [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) to install new versions as they appear, but so far no 5.4.0.2 has shown in the ppa.

---

### Post by vasa1 on 2015-12-23
Thanks for replying. Did you have to do anything special to get it to work with gtk3? Or is gtk3 the default?

---

### Post by ajgreeny on 2015-12-23
> **vasa1 said:**
> Thanks for replying. Did you have to do anything special to get it to work with gtk3? Or is gtk3 the default?
I haven't the faintest idea about that.  I simply updated the default version of LO when I enabled the ppa and have allowed it to update automatically ever since.

I see that I have the package  **libreoffice-gtk3** installed, which from its description appears to be needed for gtk3 integration of the suite, and that was not installed automatically when I first used the ppa.  I can not find any specific reason why it was added when it was as it was not part of another LO upgrade, but was a standalone installation of that package alone in June 2015, so I presume I must have read somewhere that it would be helpful with the newer OSs that use gtk3.

It was back in early August 2015 that the ppa updated libreoffice from 1:4.4.5~rc2-0ubuntu1~trusty1 to 1:5.0.0~rc5-0ubuntu1~trusty1 and it has not presented any problems or difficulties to me.

---

### Post by vasa1 on 2016-02-11
Well, I took the plunge and now have 5.0.4.2 (Build ID: 1:5.0.4~rc2-0ubuntu1~trusty1) running. All is well, but, in *~/.config/libreoffice* I have a folder named "4" and not "5" (as I'd expect). Is this just me?

---

### Post by Bucky Ball on 2016-02-11
Have you installed libreoffice-gtk3? Not sure if that's there by default. On the 14.04 LTS I'm running (and Libreoffice comes as default with Ubuntu) I installed Libreoffice manually and only writer, presentation and calc, so that would probably make a difference.

---

### Post by vasa1 on 2016-02-12
> **Bucky Ball said:**
> Have you installed libreoffice-gtk3? Not sure if that's there by default. On the 14.04 LTS I'm running (and Libreoffice comes as default with Ubuntu) I installed Libreoffice manually and only writer, presentation and calc, so that would probably make a difference.
Yes, I installed *libreoffice-gtk3*. But it seems, for LibO to use gtk3, the gtk3 version must be newer than 3.10 and I have 3.10 according to ```
apt-cache policy libgtk-3.0
libgtk-3-0:
  Installed: 3.10.8-0ubuntu1.6
  Candidate: 3.10.8-0ubuntu1.6
  Version table:
 *** 3.10.8-0ubuntu1.6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.10.8-0ubuntu1.4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     3.10.8-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
10:30 AM ~ $ 

```

---

### Post by vasa1 on 2016-03-12
Well, I tried a live USB of Lubuntu 16.04. Just installing *libreoffice-calc* (and whatever dependencies and recommends are default) resulted in an "unthemed" appearance (before.png). Adding *libreoffice-gtk3* fixed that (after.png).

---

