---
title: "VirtualBox Update won't install"
date: 2013-12-20
forum: Virtualisation
---

### Post by foberle on 2013-12-20
I'm been using VirtualBox for quite some time on 64-bit Ubuntu 12.04, and have successfully updated it at least three times; currently I'm using 4.2.18 r88780.

When I run VirtualBox now, it tells me that a new update is available, but when I download the deb package update, the Ubuntu software Center gives me the following error message and won't install it.

"Breaks existing package 'virtualbox-4.2' that conflict: 'virtualbox'. But the '/home/myusername/Downloads/virtualbox-4.3_4.3.6-91046-Ubuntu-precise_amd64.deb' provides it via: 'virtualbox'"

I don't have any issues with VirtualBox now aside from the "guilt by association" that comes with having it run Windows, so this isn't probably a big deal, but does anyone have any ideas why this should happen?

---

### Post by memilanuk on 2013-12-20
Did you install your existing VirtualBox 4.2.nn via the upstream vendor (i.e. Oracle) repos?

If so, try running 'sudo apt-get install virtualbox<tab><tab>' to get a list of all the packages beginning with 'virtualbox'.  One of those should be 'virtualbox-4.2', and another should be 'virtualbox-4.3'.  Install the latter and it should automagically remove the old version (4.2.nn) and install the new one (4.3.6 at this point in time), including unloading and reloading the kernel modules, etc.

As it happens, I just went thru this process earlier today on Ubuntu 13.10, so I'm somewhat confident it should work for you ;)

HTH,

Monte

---

