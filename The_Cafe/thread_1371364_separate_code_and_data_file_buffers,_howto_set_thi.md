---
title: "separate code and data file buffers, howto set this up?"
date: 2010-01-03
forum: The Cafe
---

### Post by Cdwijs on 2010-01-03
Hi All,

When I copy a large file on my linux system, the system is no longer responsive. This is due to the following 2 factors:

-One problem is that the complete bandwith of my harddrive is being used for the filetransfer.

-The second factor is that everything that has been cached in the filebuffers, is overwritten by the file that is being copied. This means every program I want to run has to be re-fetched from the busy harddrive.

On my system, I have all data on one partition, and all my programs on another partition. Is there a way to disable file buffering on the data partition? This way all my programs are always buffered, so my system remains responsive.

Maybe the file buffers can be split, one for code, one for data:
[http://brainstorm.ubuntu.com/idea/18219/](http://brainstorm.ubuntu.com/idea/18219/)

Best regards,
Cedric

---

