---
title: "SOLVED What makes torrent downloads of .iso inherently safer?"
date: 2016-02-21
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-02-21
I have read that torrent downloading of .iso's of buntu's and other distro's is inherently safer than downloading directly from Web-pages. 

Downloading from a web-page one should always check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM").

I don't know why but, I have read that the torrent files found for .iso will always be correct. How is this so?

---

### Post by sammiev on 2016-02-21
Came across a post at [ask ubuntu]("https://askubuntu.com/questions/519354/what-is-the-recommended-way-to-download-ubuntu-new-releases-iso-torrent-or-offi") and followed a link from one thread to [another]("https://askubuntu.com/questions/65715/is-the-ubuntu-direct-download-exactly-the-same-as-the-torrent").

Hope it helps.

---

### Post by deadflowr on 2016-02-21
Because torrents are usually pulled from multiple sources, they need to be checked constantly.
so every packet downloaded is automatically checked as it is downloaded.
torrents do this by adding a hash to every piece or packet in the file being sent.

That is the basic concept.

Direct downloads can not check the hash until the whole image/file is downloaded.

---

### Post by mikodo on 2016-02-21
> **deadflowr said:**
>  - What you said. - 

Thank you.

---

### Post by goofprog on 2016-02-22
Torrent files have this hash functionality in it and every one on the torrent shares the same data.

---

### Post by Geoffrey_Arndt on 2016-02-22
hmm,  deju-vu anyone?

---

### Post by coldraven on 2016-02-23
It should be mentioned that it is important to get the torrent link from the distros web-page and **not** from untrustworthy sources.
Go here, click on a version and scroll down the page to find the torrent download options:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

