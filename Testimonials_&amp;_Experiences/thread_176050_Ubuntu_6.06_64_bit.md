---
title: "Ubuntu 6.06 64 bit"
date: 2006-05-14
forum: Testimonials &amp; Experiences
---

### Post by nikosft on 2006-05-14
The ubuntu 5.10 64 bit had a big disadvantage over Suse linux 9.3 64 bit. In suse the 32 bit programs could run smoothly without any trick. On the other hand in ubuntu you had to make variuos tricks in order to make them running. Has this issue beem solved in the upcoming version of Ubuntu or will the 64bit procrssor owners will have to use the 32bit version? I have read noting about it and I am quite concerned.

---

### Post by bonzodog on 2006-05-14
As far as I am aware, this is planned but will not really be implemented for another 2 or 3 releases, due to the way debian works. Unlike Suse, debian puts all its 64 bit libs in /usr/lib64 then symlinks to /usr/lib. All 32 bit libs are in /usr/lib32 and stay there. this creates problems when installing 32 bit programs, as they have to be told to go to /usr/lib32. Suse does things the other way around, with 32 bit libs in /usr/lib and 64 bit libs in /usr/lib64

---

