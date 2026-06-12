---
title: "Kubuntu Noble ISO"
date: 2024-04-25
forum: Ubuntu Development Version
---

### Post by oldfred on 2024-04-25
renamed noble-desktop-amd64.iso from a day or two ago, in my ISO folder & ran zsync
Had minor update to final.
Note zsync only worked with http not https.

 ```
https://cdimage.ubuntu.com/kubuntu/releases/noble/release/

 zsync http://cdimage.ubuntu.com/kubuntu/releases/noble/release/kubuntu-24.04-desktop-amd64.iso.zsync
#################### 100.0% 252.5 kBps DONE   
Read kubuntu-24.04-desktop-amd64.iso. Target 98.1% complete.      ****************************
downloading from http://cdimage.ubuntu.com/kubuntu/releases/noble/release/kubuntu-24.04-desktop-amd64.iso:
#################### 100.0% 2018.0 kBps DONE      

verifying download...checksum matches OK
used 4043640832 local, fetched 80339893

```

---

### Post by ajgreeny on 2024-04-25
Silly isn't it but zsync has worked only with http, not https, ever since I began to use zsync.

It took me quite a while when I started using it to update my ISO downloads for the last LTS version 22.04, or maybe even before that.
I always went to the download page and right clicked to copy the zsync link, which is https then pasted that into my download command only to have it fail, but with no explanation as to why.
Why don't they change the download link itself to http?

---

### Post by #&amp;thj^% on 2024-04-25
> **ajgreeny said:**
> 
Why don't they change the download link itself to http?

Or Ideally https for zsync....And yes I agree it's very silly.

---

