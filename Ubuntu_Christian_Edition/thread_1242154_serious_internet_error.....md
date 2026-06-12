---
title: "serious internet error...."
date: 2009-08-16
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2009-08-16
hey my acer aspire 5610z cannot use the wireless card once its updated on any ubuntu install...so in used CE and now i cannt update some things...even tho i get internet there are a whole lot of updates that i cannot get: heres the list of them...hey dk can you help my find a solution to this issue:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.11+build2+nobinonly-0ubuntu0.9.04.1_all.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-11ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-11ubuntu0.9.04.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.28.13.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.28.13.17_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.28.13.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.28.13.17_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.28.13.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.28.13.17_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.13.17_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.13.17_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-13.45_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-13.45_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.28-13.17_all.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.28-13.17_all.deb)
  404 Not Found

---

### Post by david_kt on 2009-08-16
> **stlsaint said:**
> hey my acer aspire 5610z cannot use the wireless card once its updated on any ubuntu install...so in used CE and now i cannt update some things...even tho i get internet there are a whole lot of updates that i cannot get: heres the list of them...hey dk can you help my find a solution to this issue:


```

sudo apt-get update
sudo apt-get upgrade
```

would be able to solve that problem. The files are really non existence.

DK

---

### Post by stlsaint on 2009-08-16
DK i cant begin to express my gratitude towards you and UCE...i have tried 4 different distros of ubuntu on this other system i am working on and none of them have been able to keep up my wireless card! on my main system i run ubuntu ultimate and UCE and on this system just UCE because its the only distro that took!!! thank you once again! i have one last question for the moment...i would  like to know if the following programs will be compatible with UCE with no issues....
1. Virtual box
2. pidgin( the newer one)
3. microsoft 2007
4. sims 3
5. frostwire
6. amarok
7. a few choice games from repos(minesweeper, solitaire, tc)

thanks again DK!!

---

### Post by david_kt on 2009-08-17
> **stlsaint said:**
> 
1. Virtual box
2. pidgin( the newer one)
3. microsoft 2007
4. sims 3
5. frostwire
6. amarok
7. a few choice games from repos(minesweeper, solitaire, tc)

thanks again DK!!

1. Virtual box and pidgin should not be an issue.
2. Microsoft 2007 should depend on wine version and how you install it. I
t might need some tweak but that should be generic (i.e. the same as any other distros).
3. The latest version of amarok has some issue, its better to isntall the old version.
4. games should ok
5. Not sure about sims 3 and frostwire. But as general guidelines, as long as it work in normal ubuntu, it would work on ubuntu ce.

DK

---

