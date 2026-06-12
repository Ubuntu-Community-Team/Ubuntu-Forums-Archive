---
title: "avast?"
date: 2009-04-08
forum: Security
---

### Post by JakeHinojosa on 2009-04-08
i ran a scan with avast and when it completed it showed the linux mint iso file (im using ubuntu, not linux mint) and it said the file was a "decompression bomb" whats that mean?

---

### Post by EXCiD3 on 2009-04-08
"A decompression bomb is a file that unpacks to an enormous amount of data - thus "flooding" the unpacking engine. It's quite hard to detect such files reliably, so it's possible that it gives some false alarms ocassionally."

Source: [http://forum.avast.com/index.php?topic=8943](http://forum.avast.com/index.php?topic=8943)

I really doubt Linux Mint's iso has anything to worry about, it is most likely a false positive with avast. Many things with compression get flagged as false positives because it is something hard to detect. Lots of the PortableApps.com applications are flagged as such and are never an issue. You should be fine. :)

---

