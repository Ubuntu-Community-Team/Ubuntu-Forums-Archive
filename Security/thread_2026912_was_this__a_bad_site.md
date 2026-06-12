---
title: "was this  a bad site?"
date: 2012-07-16
forum: Security
---

### Post by boregard on 2012-07-16
hello, i was downloading an iso today for a friend i had talked into trying ubuntu.i cd into the downloads dir. to do a md5sum check on the iso. well when i did, it kept returning a unexpected token error. the file was named, ubuntu desktop-amd 64 (1) iso. i know it was because of the (1). what caused this? was i getting the download from a malicious site? could someone explain? anyways i trashed the file and downloaded again & everything checked out ok. regards

---

### Post by cariboo on 2012-07-16
> **boregard said:**
> hello, i was downloading an iso today for a friend i had talked into trying ubuntu.i cd into the downloads dir. to do a md5sum check on the iso. well when i did, it kept returning a unexpected token error. the file was named, ubuntu desktop-amd 64 (1) iso. i know it was because of the (1). what caused this? was i getting the download from a malicious site? could someone explain? anyways i trashed the file and downloaded again & everything checked out ok. regards

The (1) in the file name, just means that you already have a file named ubuntu desktop-amd 64.iso, in the same directory.

When downloading an Ubuntu iso, it is always better to got to [www.ubuntu.com](www.ubuntu.com), and download the iso directly, or from one of the official mirrors.

---

### Post by boregard on 2012-07-16
thanks, cariboo907. i'll make sure i go to ubuntu.com

---

### Post by samiux on 2012-07-16
> **boregard said:**
> hello, i was downloading an iso today for a friend i had talked into trying ubuntu.i cd into the downloads dir. to do a md5sum check on the iso. well when i did, it kept returning a unexpected token error. the file was named, ubuntu desktop-amd 64 (1) iso. i know it was because of the (1). what caused this? was i getting the download from a malicious site? could someone explain? anyways i trashed the file and downloaded again & everything checked out ok. regards

First of all, how you check and compare with the md5 checksum?  As far as I know, Ubuntu.com does not provide any md5 checksum for users to compare with.

Secondary, I suspected your ISO file is corrupted.  I suggest you to re-download it again.  Before doing so, make sure you deleted all the previous downloaded ISO files in order to prevent you from getting the wrong one by mistake.

Samiux

---

### Post by rookcifer on 2012-07-17
> **samiux said:**
> First of all, how you check and compare with the md5 checksum?  As far as I know, Ubuntu.com does not provide any md5 checksum for users to compare with.

Yes they do. They provide MD5, SHA1 and SHA256[ hashes for each iso]("http://releases.ubuntu.com/12.04/"). They even provide GPG keys for verification if you are paranoid and want to go that route.

OP probably just has a corrupted .iso.  In any case it doesn't really matter where you get the iso as long as you verify its authenticity through SHA1 hashes or PGP sigs.  (Don't use MD5 as it is badly broken).

---

