---
title: "Nautilus drag &amp; drop no longer works"
date: 2024-03-16
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-03-16
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2058101](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/2058101)

---

### Post by jbicha on 2024-03-16
I uploaded nautilus 46 RC to the [Ubuntu Desktop PPA]("https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa") . Do you still have the same issue there?

The PPA also includes GNOME Shell 46. The biggest annoyance is that the Yaru theme has not been updated yet so there are some major styling issues in the Ubuntu session, particularly with the Ubuntu Dock. It works a bit better with the GNOME session. There are some other bugs too.

---

### Post by corradoventu on 2024-03-16
After installing Your PPA problem disappeared
Thanks

---

### Post by corradoventu on 2024-03-16
After installing PPA system no longer boots. 
GNOME Shell 46 NOT installed

---

### Post by jbicha on 2024-03-16
yikes

But that might be unrelated to the PPA?

Did you only update nautilus or how did you avoid getting GNOME Shell 46?

---

### Post by corradoventu on 2024-03-16
I have done update+upgrade, nautilus has been installed but GNOME shell was kept back.
I have logs and crash file if needed.
I think this is related to the PPA because on a different partition Noble at the same level still works fine.
I have another partition i can sacrifice to redo the test and save the messages from apt upgrade

---

### Post by jbicha on 2024-03-16
My guess is that it was because gnome-session didn't build yesterday. There is a new build now but it may take an hour to be published.

[https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa/+build/27932150](https://launchpad.net/~ubuntu-desktop/+archive/ubuntu/ppa/+build/27932150)

Or it could be because you ought to do a dist-upgrade and update GNOME Shell too.

As long as you can get to a virtual terminal, you can run ppa-purge to undo adding a PPA.

---

### Post by corradoventu on 2024-03-16
Ok, done dist-upgrade, system boot ok Thanks
```
corrado@corrado-n4-nn-0310:~$ apt policy gnome-shell
gnome-shell:
  Installed: 46~rc-0ubuntu1~bpo24.04.1
  Candidate: 46~rc-0ubuntu1~bpo24.04.1
  Version table:
 *** 46~rc-0ubuntu1~bpo24.04.1 500
        500 https://ppa.launchpadcontent.net/ubuntu-desktop/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     45.3-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
corrado@corrado-n4-nn-0310:~$ apt policy nautilus
nautilus:
  Installed: 1:46~rc-0ubuntu2~bpo24.04.1
  Candidate: 1:46~rc-0ubuntu2~bpo24.04.1
  Version table:
 *** 1:46~rc-0ubuntu2~bpo24.04.1 500
        500 https://ppa.launchpadcontent.net/ubuntu-desktop/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     1:46~beta-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
corrado@corrado-n4-nn-0310:~$ 
```

---

