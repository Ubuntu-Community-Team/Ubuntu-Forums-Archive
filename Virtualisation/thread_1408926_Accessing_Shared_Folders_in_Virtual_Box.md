---
title: "Accessing Shared Folders in Virtual Box"
date: 2010-02-17
forum: Virtualisation
---

### Post by BionicGear83 on 2010-02-17
There is a function in Virtual Box that lets the guest OS access a shared folder on the host OS, but I can't get it to work.
I am running ubuntu 9.10 as a guest on the windows 7 host.

---

### Post by kiranmurari on 2010-02-17
Hi,

You need to install Guest Additions first, before sharing folders between the guest and the host.

Please see the following links from VirtualBox manual on installing guest additions for Linux Guest and sharing folders between Windows host and Linux guest [URL="http://forums.virtualbox.org/viewtopic.php?f=3&t=15868"]
[/URL][http://www.virtualbox.org/manual/ch04.html#id2522652]("http://forums.virtualbox.org/viewtopic.php?f=3&t=15868")
[http://www.virtualbox.org/manual/ch03.html#id2520443]("http://forums.virtualbox.org/viewtopic.php?f=3&t=15868")
[URL="http://forums.virtualbox.org/viewtopic.php?f=3&t=15868"]http://forums.virtualbox.org/viewtopic.php?f=3&t=15868
[/URL]
Hope this helps.

---

