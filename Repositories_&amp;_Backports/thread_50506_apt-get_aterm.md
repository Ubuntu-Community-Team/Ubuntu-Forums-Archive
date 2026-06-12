---
title: "apt-get aterm"
date: 2005-07-20
forum: Repositories &amp; Backports
---

### Post by Valenj3 on 2005-07-20
Trying to apt-get aterm on my laptop and keep getting this:

root@Area51:/ # sudo apt-get install aterm
Reading package lists... Done
Building dependency tree... Done
Package aterm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package aterm has no installation candidate
root@Area51:/ #


Is there some other package out there that replaced this?  I keep finding posts from people saying there installs went fine.

Also, is Eterm any better for transparant backgrounds and such?

---

### Post by varunus on 2005-07-20
aterm is in universe.  Make sure you enable extra repositories as described at [www.ubuntuguide.org](www.ubuntuguide.org) before you try to install it, and it should work.

I've used Eterm, and it works very nicely for transparent borderless stuff.  There's a howto in the "hoary tips and tricks" section of the forums on howto use a transparent borderless terminal with eterm.

---

