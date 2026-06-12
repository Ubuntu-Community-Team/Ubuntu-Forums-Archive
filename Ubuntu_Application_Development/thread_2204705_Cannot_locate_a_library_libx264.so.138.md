---
title: "Cannot locate a library libx264.so.138"
date: 2014-02-09
forum: Ubuntu Application Development
---

### Post by PeterTaps on 2014-02-09
Folks,

I have two machines running Ubuntu 13.10. One is my development box. I compiled a program on the dev box and am trying to run it on my test box. The problem is that the program depends on a library libx264.so.138 that is not available on my test box.

The closest package I have found on the repository is libx264-123. However, I don't understand how I got libx264.so.138 on my dev box. $apt-cache search as well as $apt-file search do not show me libx264.so.138 anywhere

Can someone please tell me where I can obtain the package containing libx264.so.138?

Thank you in advance for your help.

Regards,
Peter

---

### Post by PeterTaps on 2014-02-11
It turns out I had compiled the latest version of ffmpeg. Although I thought I used flags for static libraries, somehow it ended up creating shared libraries.

Regards,
Peter

---

