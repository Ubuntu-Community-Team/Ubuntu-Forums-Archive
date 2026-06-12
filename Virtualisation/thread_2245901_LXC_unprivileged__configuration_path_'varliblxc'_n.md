---
title: "LXC unprivileged?  configuration path '/var/lib/lxc' not found"
date: 2014-09-26
forum: Virtualisation
---

### Post by Jack Waugh on 2014-09-26
Is it possible to run LXC from the package as an unprivileged user, as it says in [https://help.ubuntu.com/lts/serverguide/lxc.html#lxc-unpriv](https://help.ubuntu.com/lts/serverguide/lxc.html#lxc-unpriv)?  When I try the instructions there (only changing the architecture spec to i386), I get "configuration path '/var/lib/lxc' not found".  Does it make sense for the tool to be looking in a global configuration area when it is being run unprivileged?  By the way, the directory there is empty and belongs to root and is in mode 0700.  Is the package maintainer in the house here?  I am trying this on server Ubuntu 12.04.5 LTS (precise) (on a Digital Ocean node).

---

### Post by Doug S on 2014-09-27
I tried creating an unprivileged LXC container on my 14.04 test server, using only the instructions from the Ubuntu serverguide link you provided. It worked fine.
There have been a great many changes to LXC, and virtualization in general, since 12.04. The Ubuntu Serverguide LXC section was completely re-written, by a subject matter expert, for 14.04. You might want to try [the 12.04 version of the serverguide]("https://help.ubuntu.com/12.04/serverguide/lxc.html") as a reference.

---

