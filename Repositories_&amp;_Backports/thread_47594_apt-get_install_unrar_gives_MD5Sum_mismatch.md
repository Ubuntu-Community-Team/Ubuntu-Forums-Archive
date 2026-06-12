---
title: "apt-get install unrar gives MD5Sum mismatch"
date: 2005-07-09
forum: Repositories &amp; Backports
---

### Post by MWAAAHAAA on 2005-07-09
sudo apt-get --fix-missing install unrar
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.2kB of archives.
After unpacking 90.1kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe unrar 1:0.0.1-1 [17.2kB]
Fetched 17.2kB in 0s (34.8kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/u/unrar/unrar_0.0.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/u/unrar/unrar_0.0.1-1_i386.deb)  MD5Sum mismatch

Does anyone else have this problem? Where should I report this?

---

### Post by adwait on 2005-07-09
Not sure, but you could try using the generic repositories instead of the us one's. Edit /etc/apt/sources.list and remove the us. from the addresses like us.archive.ubuntu.com becomes archive.ubuntu.com

---

### Post by relic411 on 2005-07-09
I just wanted to thank you. I've been working for a while on installing GnuCash and had the MD5 Checksum error. Good advice, it worked perfectly

---

### Post by carlc on 2005-07-10
I just did a clean install of hoary and was having trouble installing some packages. I edited like you said and went back and they all installed fine!  :)

---

### Post by MWAAAHAAA on 2005-07-11
Thanks a lot, as the people above have already said, it works! I tried installing another package today, actually two other ones (libgnet and pan (which depends on libgnet)) and had the same checksum issue, so I guess there seems to be a serious problem with the us repository then.

---

### Post by beko on 2005-07-12
I have the same problem & I thnk that always happend when apt start getting somthing from Us archives mirror like this (Failed to fetch [http://us.archive.ubuntu.com/ubuntu...s/libsndfile/li](http://us.archive.ubuntu.com/ubuntu...s/libsndfile/li) bsndfile1_1.0.10-2_i386.deb MD5Sum mismatch)
That always happend nowadays I don't know why although I just installed a clean installation.

---

