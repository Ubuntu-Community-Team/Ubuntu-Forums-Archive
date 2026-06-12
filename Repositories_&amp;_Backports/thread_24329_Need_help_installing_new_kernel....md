---
title: "Need help installing new kernel..."
date: 2005-04-06
forum: Repositories &amp; Backports
---

### Post by vinoloco on 2005-04-06
Hi all,  this should be a pretty basic question so please bear with me...

I'm currently working on my first intall of Ubuntu (Hoary) onto a laptop and need some help updating the kernel.  

I connect to the net using a Prism2 USB adapter (MA111) and can't get it to work on the base install (2.6.10-5) but read a note here on the forums that there was a bug fix on a more recent kernel so I'm attempting to update.  I've tranferred  the linux-image-2.6.11-1-386_2.6.11-0.2_i386.deb file via CD to the laptop but have no idea how to install it.  Does anybody have a pointer to a FAQ to describe the process?

Also, I'd like to be able to make and intall the most current linux-wlan-ng software but have noticed that the appropriate development tools are missing from the base install.  What do I need to install to get those?  I'm assuming that once I get my internet connection going thing should get easier....  Any help would be appreciated.

   -- vino

---

### Post by taygan on 2005-04-06
to install a local deb you can try:
```
dpkg -i linux-image-2.6.11-1-386_2.6.11-0.2_i386.deb 
```

for more info check out the dpkg manual page ```
man dpkg
```
press q to get out of the manual pages.  Maybe this is a little basic, but heck, I'm still learning too.

to get the essentials for compiling try:
```
apt-get build-essential
```
I don't know if you need the internet to get these, though.

---

