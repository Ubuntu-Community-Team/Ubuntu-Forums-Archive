---
title: "For laughs: Accidental decompression bomb with dd and gzip..."
date: 2010-08-24
forum: The Cafe
---

### Post by modmadmike on 2010-08-24
After zero filling 3 hard drives I figured I should backup my root drive (/dev/mapper/Root-root). I was using pigz (parallel implementation of gzip) and dd... I wondered what the hell was taking it so long so I checked with kill -USR1 and received this: ```
4991120257+0 records in
4991120256+0 records out
2555453571072 bytes (2.6 TB) copied, 12330.5 s, 207 MB/s
``` I checked the gzip file and it was only 2.7GB in size... Checked the command and sure enough I typed ```
dd if=/dev/zero | pigz -9 -p 4 > /home/modmadmike/Root-root.img.gz
``` roflmao!!!

---

