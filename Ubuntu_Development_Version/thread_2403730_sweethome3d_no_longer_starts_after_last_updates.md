---
title: "sweethome3d no longer starts after last updates"
date: 2018-10-15
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-10-15
corrado@corrado-HP-p5-cc-0927:~$ sweethome3d
Inconsistency detected by ld.so: dl-lookup.c: 112: check_match: Assertion `version->filename == NULL || ! _dl_name_match_p (version->filename, map)' failed!

Problem seems due to some recent update. sweethome start ok before updates, then i run apt update+upgrade and after upgrades sweethome does not start.

[https://bugs.launchpad.net/ubuntu/+source/sweethome3d/+bug/1797920](https://bugs.launchpad.net/ubuntu/+source/sweethome3d/+bug/1797920)

---

### Post by dino99 on 2018-10-15
Possibly a glibc issue  [https://stackoverflow.com/questions/22564780/debugging-ld-inconsistency-detected-by-ld-so](https://stackoverflow.com/questions/22564780/debugging-ld-inconsistency-detected-by-ld-so)

---

### Post by Hreinsi on 2018-10-18
Same here you can try this works for me. [https://snapcraft.io/sweethome3d-homedesign](https://snapcraft.io/sweethome3d-homedesign)

---

### Post by corradoventu on 2018-10-19
Also the snap version works fine, but if you have the same problem please subscribe my bug.

---

### Post by dino99 on 2018-10-19
Latest Cosmic version has been updated on  Sun, 14 Oct 2018 ; so your report needs to be commented too if that version is still not working for you.
Can you grab something related via journalctl ?

---

### Post by mc4man on 2018-10-19
The segfault was caused by the upgrade of openjdk-lts from 10.0.2+13-1ubuntu1 to 11~28-3ubuntu2. Maybe sweet.. needs just a rebuild or maybe it needs to be modified/patched for newer openjdk.. There are numerous undefined symbol errors

(- if desired you could downgrade to these 2 packages
openjdk-11-jre_10.0.2+13-1ubuntu1_amd64.deb
openjdk-11-jre-headless_10.0.2+13-1ubuntu1_amd64.deb

---

