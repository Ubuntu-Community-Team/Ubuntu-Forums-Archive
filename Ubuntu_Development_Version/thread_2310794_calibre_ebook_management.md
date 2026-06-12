---
title: "calibre ebook management"
date: 2016-01-21
forum: Ubuntu Development Version
---

### Post by krishnan t s on 2016-01-21
I'm trying to get calibre working on ubuntu 16.04. The version in the repositories gave me a broken package, so i downloaded the .tar.gz version from the official site and ran the script to install it. Calibre installed and ran well for maybe 2 times. The third time it got stuck on initializing user interface and the unity desktop hung. None of the keys worked and i had to get my desktop using a hard reboot. How do i get calibre working again? I find it to be the best ebook management software and the only software to render .epub files in ubuntu correctly
Thanks in advance and have a nice day :)

---

### Post by cariboo on 2016-01-22
I'm no help, as Calibre has always worked for me, I update it using the script [here]("http://calibre-ebook.com/download_linux"). Make sure you purge the repository package before installing the version from the web site.

---

### Post by mc4man on 2016-01-22
The repo calibre has an issue with **1st. run** after install. It will try to open the interface from the wizard > Next button with a window that's usually 9-10 times wider than screen. I don't believe the upstream suffers from this but if it does show initializing issues try with this from terminal - 
```
export LIBOVERLAY_SCROLLBAR=0 && calibre
```

---

