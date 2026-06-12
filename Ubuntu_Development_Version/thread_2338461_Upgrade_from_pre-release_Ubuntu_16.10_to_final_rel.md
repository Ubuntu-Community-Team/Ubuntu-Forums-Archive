---
title: "Upgrade from pre-release Ubuntu 16.10 to final release"
date: 2016-09-28
forum: Ubuntu Development Version
---

### Post by 1j4fj67 on 2016-09-28
If I install Ubuntu 16.10 from the daily list in the next couple of days, I assume I would receive updates as they work towards final release on Oct 13. Am I correct in assuming that as Ubuntu 16.10 final is released, my system will automatically update to that release without my having to reinstall a fresh copy? Or perhaps it would be a good idea to install a fresh copy anyway? The live CD images on that daily list - are they .iso files that I can transfer to a USB stick using Startup Disk Creator or something similar? Thanks.

---

### Post by howefield on 2016-09-28
> **1j4fj67 said:**
> If I install Ubuntu 16.10 from the daily list in the next couple of days, I assume I would receive updates as they work towards final release on Oct 13. Am I correct in assuming that as Ubuntu 16.10 final is released, my system will automatically update to that release without my having to reinstall a fresh copy?

Yes that is the way it works, no need to install fresh after release date unless you really wanted to.

> The live CD images on that daily list - are they .iso files that I can transfer to a USB stick using Startup Disk Creator or something similar? Thanks.

Yes, they are iso files, eg..

```
                                     -   
MD5SUMS                         28-Sep-2016 08:07  119   
MD5SUMS-metalink                28-Sep-2016 08:07  129   
MD5SUMS-metalink.gpg            28-Sep-2016 08:07  933   
MD5SUMS.gpg                     28-Sep-2016 08:07  933   
SHA1SUMS                        28-Sep-2016 08:07  135   
SHA1SUMS.gpg                    28-Sep-2016 08:07  933   
SHA256SUMS                      28-Sep-2016 08:07  183   
SHA256SUMS.gpg                  28-Sep-2016 08:07  933   
yakkety-desktop-amd64.iso       28-Sep-2016 08:03  1.6G  Desktop image for 64-bit PC (AMD64) computers (standard download)
yakkety-desktop-amd64.iso.zsync 28-Sep-2016 08:06  3.2M  Desktop image for 64-bit PC (AMD64) computers (zsync metafile)
yakkety-desktop-amd64.list      28-Sep-2016 08:03  4.5K  Desktop image for 64-bit PC (AMD64) computers (file listing)
yakkety-desktop-amd64.manifest  28-Sep-2016 07:58   63K  Desktop image for 64-bit PC (AMD64) computers (contents of live filesystem)
yakkety-desktop-amd64.metalink  28-Sep-2016 13:57  1.0K  
yakkety-desktop-i386.iso        28-Sep-2016 08:05  1.6G  Desktop image for 32-bit PC (i386) computers (standard download)
yakkety-desktop-i386.iso.zsync  28-Sep-2016 08:06  3.2M  Desktop image for 32-bit PC (i386) computers (zsync metafile)
yakkety-desktop-i386.list       28-Sep-2016 08:05  3.9K  Desktop image for 32-bit PC (i386) computers (file listing)
yakkety-desktop-i386.manifest   28-Sep-2016 07:57   62K  Desktop image for 32-bit PC (i386) computers (contents of live filesystem)
yakkety-desktop-i386.metalink   28-Sep-2016 13:57  1.0K  
```

---

### Post by 1j4fj67 on 2016-09-28
Thank you Howefield. Much appreciated as I learn my way around Ubuntu and Linux.

---

### Post by howefield on 2016-09-28
Very welcome, something you may like to know is that you can zsync from one image to the next. In other words, zsync will download only the difference between two images, can be a decent saving in time and bandwidth. 

I generally use zsync to keep daily images current and also to bring an image up to date with the final release (for keeps), and then use a copy as the base for the next development cycle. Not well explained but just sayin' :) Worth a look if you are likely to download more than a single daily.

---

