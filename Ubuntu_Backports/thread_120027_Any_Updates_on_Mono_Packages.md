---
title: "Any Updates on Mono Packages?"
date: 2006-01-20
forum: Ubuntu Backports
---

### Post by jaboo on 2006-01-20
I have searched the Backports forum and understand that the Backports team is working with Ubuntu's Mono team for backports of current Mono packages. I was just curious if there were any updates on this process? If there is a publicly accessible forum for checking on the progress of Mono packages in Ubuntu, where should I look? Thanks for any enlightenment.

---

### Post by arpunk on 2006-01-20
[QUOTE=jaboo]I have searched the Backports forum and understand that the Backports team is working with Ubuntu's Mono team for backports of current Mono packages. I was just curious if there were any updates on this process? If there is a publicly accessible forum for checking on the progress of Mono packages in Ubuntu, where should I look? Thanks for any enlightenment.[/QUOTE]
Yes, theres been posts about the mono backports months ago, they are being tested and such but i havent seen any word of progress (which would be nice).

---

### Post by P.-A. on 2006-01-21
I was looking for newer Mono package too. First I've tested debian packages from [http://debian.meebey.net](http://debian.meebey.net). They work fine but libgdiplus didn't want to be installed.

And yesterday I found another repository (via Banshee website). It is made for breezy and no problem with this one until now. Just work fine :). Monodevelop stops finally to crash!

[http://apt.filefind.net/](http://apt.filefind.net/)

---

### Post by arpunk on 2006-01-23
[QUOTE=P.-A.]I was looking for newer Mono package too. First I've tested debian packages from [http://debian.meebey.net](http://debian.meebey.net). They work fine but libgdiplus didn't want to be installed.

And yesterday I found another repository (via Banshee website). It is made for breezy and no problem with this one until now. Just work fine :). Monodevelop stops finally to crash!

[http://apt.filefind.net/](http://apt.filefind.net/)[/QUOTE]

Yea im using that one too, too bad banshee doesnt come with the DAAP plugin, but monodevelop works perfect, also the mono libraries :p

---

### Post by vaskark on 2006-01-26
I also started using the apt.filefind.net mono repository, but now I can't reinstall beagle. This is the error i get:

beagle:
  Depends: libgconf2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libglade2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libglib2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libgnome2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed
  Depends: libgtk2.0-cil (<2.5.0) but 2.7.90-0filefind.net-breezy0 is to be installed

Any ideas?

---

### Post by FuzzySkat on 2006-01-26
> Any ideas?
To address here ([http://ubuntuforums.org/showthread.php?t=106883](http://ubuntuforums.org/showthread.php?t=106883)) and to wait, while will make a package for beagle 0.2.0

---

### Post by binarymelon on 2006-02-08
Does anyone have any idea when banshee 0.10.5 will be released to the apt.filefind.net repository?

---

