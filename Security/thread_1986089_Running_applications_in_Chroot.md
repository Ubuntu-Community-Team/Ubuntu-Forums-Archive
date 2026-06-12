---
title: "Running applications in Chroot?"
date: 2012-05-24
forum: Security
---

### Post by Hungry Man on 2012-05-24
I can't find an up to date guide for running an application in a chroot.

If anyone would mind walking me through the steps I'd appreciate that. In this case I'm looking to chroot xchat/pidgin.

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

This page seems out of date. I'm using it with a lot of guess work to fill in some gaps lol

Ok... I've installed debootsrap and I've run it and it gave me a "success" output.

edit: Solved that last issue.

ok, so I actually ended up install Hardy instead of Precise (the wiki guide could really use some clarity) so I guess I have to upgrade in the chroot.

---

### Post by Haneef Mubarak on 2012-05-25
Chroot isn't a secure way to run stuff. Read [LWN: What chroot() is really for]("http://lwn.net/Articles/252794/") and then tell us what you think.

---

### Post by Hungry Man on 2012-05-25
There are no chroot bypasses that work without root. Apparmor + chroot is actually a great way to secure a program because:
1) You can deny root through apparmor
2) You can deny chroot command access through apparmor (bypassing chroot is trivial if you can call chroot, which takes root and capability)
3) You reduce visible attack surface by running a program in what is essentially a separate operating system with only what the program needs

I also use a kernel I compile myself, which directly addresses chroot bypasses.

From your link:
> There are reasonable uses of chroot() for very limited security purposes. Daemons that do not run as root can be placed into their own filesystem subtree &#8211; bind/named and Apache are sometimes run this way &#8211; to prevent any access outside of it. That will work, even if the daemon gets exploited, as long as there is no way to elevate privileges after the exploit. For example, if there are vulnerable setuid() programs accessible from within the chroot(), full filesystem access is possible.
It's pretty simple to address chroot bypasses even without a custom kernel.

---

