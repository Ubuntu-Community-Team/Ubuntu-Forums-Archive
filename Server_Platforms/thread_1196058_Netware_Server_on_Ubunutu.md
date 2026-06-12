---
title: "Netware Server on Ubunutu"
date: 2009-06-24
forum: Server Platforms
---

### Post by dummzeuch on 2009-06-24
Hi,

I am looking for a way to have some computers running DOS connect to an ubuntu file server. These are currently connecting to a Novell Netware 3.12 server and that works fine.

I cannot update these boxes to anyting but DOS because they access some proprietary hardware for which there aren't any Windows drivers available.

There is the ancient Microsoft requester for DOS which uses lots and lots and lots of memory (if I remember correctly) and is therefore not an option. And even if it were, I don't have it any more.

I remember reading about Mars-NWE a few years ago but cannot find anything recent on the internet. Is there a package for ubuntu? If not, is there another way to use the Novell DOS client to access an ubuntu fileserver? If not, are there any other options for a computer running DOS to access an ubuntu file server?

So far the only possible way seems to install vmware and run a novell server in a virtual machine. Not quite what I would like to do...

twm

---

### Post by zharmad on 2009-06-24
You need MARS-NWE, you can get .deb packages for it from: [http://people.debian.org/~pm/pool/main/mars-nwe/](http://people.debian.org/~pm/pool/main/mars-nwe/).
Its home page, with some documentation is [http://www.compu-art.de/mars_nwe/](http://www.compu-art.de/mars_nwe/) - but it is in German. Novell's website has some limited english documentation. [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch17s03.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch17s03.html)

---

### Post by dummzeuch on 2009-06-24
> **zharmad said:**
> You need MARS-NWE, you can get .deb packages for it from: [http://people.debian.org/~pm/pool/main/mars-nwe/](http://people.debian.org/~pm/pool/main/mars-nwe/).
Its home page, with some documentation is [http://www.compu-art.de/mars_nwe/](http://www.compu-art.de/mars_nwe/) - but it is in German. Novell's website has some limited english documentation. [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch17s03.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch17s03.html)

That's what I was looking for. Thanks. German docs are fine with me, I happen to speak some German, have been living there for about 40 years. ;-)

twm

---

