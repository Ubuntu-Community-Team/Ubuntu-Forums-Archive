---
title: "ldd reports not found, but library installed"
date: 2009-05-19
forum: Server Platforms
---

### Post by fantata on 2009-05-19
Hi all,

I'm really tearing my hair out on this.
I installed fine on a debian system, but ubuntu fails to see a shared library.

When I run ldd I get...
	libnspr4.so => not found
	libplc4.so => not found
	libplds4.so => not found

BUT, they are all there in /usr/lib/

ldconfig -v shows 
	libnspr4.so.0d -> libnspr4.so.0d
etc. for all of them, but it's not linking them. Other libraries are linked fine.

Any ideas?

---

### Post by fantata on 2009-05-19
Well, I'm nearly bald, but I sorted the problem.

If anyone else has this problem, it was because I am running a 64 bit OS and was trying to install a 32 bit version of Flash Media Server and linking to 64 bit libraries.

In the end, I set up a IA32-chroot and it worked like a charm.
See here -> [http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292205](http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id292205) if you need to do the same.

---

