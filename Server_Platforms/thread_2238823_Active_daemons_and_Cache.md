---
title: "Active daemons and Cache"
date: 2014-08-10
forum: Server Platforms
---

### Post by ibjsb4 on 2014-08-10
I am looking for ways to better use my ram and found this tidbit in an old post.
> Servers like Debian or Ubuntu Server Edition are pre-configured to store active daemons (programs) in cache (RAM)
I use the mini iso to do my installs.  Should I be using the server edition when doing a 'terminal only' install to get this added feature?  Or can it be installed afterwards?

This also sounds similar to preload.  If so, is having preload also installed a good idea?

---

### Post by ian-weisser on 2014-08-10
It's not an added feature.
It's not related to preload.
It has nothing to do with the installer you use.

All active programs, daemons and non-daemons, use some amount of RAM. That's generally how computers work. (but you knew that already)

If you compare the same service (like sshd or httpd) installed using the mini iso vs. using the server iso, they should use exactly the same package and exactly the same amount of RAM.

---

### Post by ibjsb4 on 2014-08-11
Ok, thanks :)

---

