---
title: "Request: rtorrent"
date: 2005-11-23
forum: Ubuntu Backports
---

### Post by DanyX on 2005-11-23
Hi all,

could anyone please backport this very promising looking bittorrent client from dapper to breezy-backports? It does not yet exist in breezy at all...

TIA,
Daniel

---

### Post by jdong on 2005-11-23
looks good.... This is a multi-step backport, due to the new library libtorrent... Gonna make notes as I go along:


(1) backport libtorrent

---

### Post by DanyX on 2005-11-23
Many thanks for your trouble! Much appreciated!

Daniel

---

### Post by jdong on 2005-11-23
Cannot be built; rtorrent requires libcurl3-openssl-dev, which requires a curl backport, which breaks the "no library backport" rule.

---

### Post by DanyX on 2005-11-23
Too bad. Thanks for trying tough!

---

