---
title: "Ubuntu One seems to upload multiple files in parallel"
date: 2011-08-31
forum: Ubuntu One (CLOSED)
---

### Post by nsk7even on 2011-08-31
Hello,

I am sitting here on a fresh install of natty with all updates.

But U1 behaves weird:
It seems to upload all files simultaneously instead of queueing.
Today the upload generally works better, so it at least finished some uploads.
But yesterday it started over and over again - I checked with "u1sdtool --current-transfers" and it tried to upload more than 25 mp3 files in parallel but never succeeded. Instead at some point the "bytes written" were reset to zero and it started again...

Can I limit the number of concurrent uploads?

Thanks in advance,
7even

---

