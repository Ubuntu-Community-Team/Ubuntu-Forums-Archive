---
title: "man pages for posix timers"
date: 2008-12-06
forum: Ubuntu Dev Link Forum
---

### Post by stardust496 on 2008-12-06
Hi,

I am new to ubuntu and am using ubuntu 8.04 .

I see that the posix timer related functions like timer_create() etc are available .. (i can compile a program that uses it)

But, I do not seem to have the manpages for the same, (man timer_create fails)

Which package should I download to get these? I have downloaded the glibc-doc , manpages and manpages-dev packages but none of these have the man page for timer_create.

Thanks a lot for any advice!

---

### Post by WW on 2008-12-07
Get the packages **manpages-posix** and **manpages-posix-dev**.  The -dev package is the one you want for timer_create(), etc.

---

