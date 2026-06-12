---
title: "clamav &amp; clamtk"
date: 2017-12-22
forum: Security
---

### Post by anon_private on 2017-12-22
I have installed clamav and clamtk from the kubuntu repository.

The signature files are out of date and I can't seem to update them.

I have tried sudo freshclam. This did not work.

Advice please

UPDATE.

I have managed to update the signature files, but I need to update the GUI. How can I do this?

The scan revealed two possible threats:

.cache/moz/ff: PUA Win.Trojan
.cache/libreoffice: PUA Doc.Tool

What are PUA's?

I have quarantined these two files.

I note that in Quarantine Maintenance, the information does not reveal much. If I wanted to restore a file how would I recognise it?

Thanks

---

### Post by HermanAB on 2017-12-23
Err... Note that the purpose of ClamAV is to scan for Windows viruses.  It is mainly used on mail servers, to protect Windows client computers.

It is not useful on a standalone Linux machine, since there are not any active Linux viruses to scan for.  

The Linux philosophy is to fix the actual problems, thus making any malicious programs ineffective.

---

### Post by SeijiSensei on 2017-12-23
PUAs: [https://www.clamav.net/documents/potentially-unwanted-applications-pua](https://www.clamav.net/documents/potentially-unwanted-applications-pua)

In the cases I've seen, PUAs are generally false positives.  For instance, some features of LibreOffice can be identified as a PUA.

---

### Post by anon_private on 2017-12-24
Thank you for responding.

I don't have any MSWindows applications on my system, only kubuntu utilities.

It looks like i don't need clam, so I can safely remove it.

I quarantined a couple of files on the advice of clam. I assume that I can restore these prior to removal

---

