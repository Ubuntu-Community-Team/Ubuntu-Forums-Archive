---
title: "resize + LVM + LUKS"
date: 2015-05-18
forum: Security
---

### Post by aimnano2 on 2015-05-18
Are there any updated guides or tutorials on growing a partition with full disk encryption?  Also, what suggestions for converting from MPT to GPT if growing over 2 TB?  I hosed my VM the first time I tried.  I've got the space to play around with.

---

### Post by aimnano2 on 2015-05-20
Any help here?  I chose to encrypt my filesystem during install and also setup LVM with guided partitioning.  Does Ubuntu use LVM on LUKS or LUKS on LVM?  Is it possible to resize this 600 GB partition to >2TB (will require conversion from MPT/BIOS to GPT) whilst also being an encrypted partition?

---

### Post by HermanAB on 2015-05-22
Hmm, stop right there and back-up all your data first, since the chances of losing it all is about 110%.

---

