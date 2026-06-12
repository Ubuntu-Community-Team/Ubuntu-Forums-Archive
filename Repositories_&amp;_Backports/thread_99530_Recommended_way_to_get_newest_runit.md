---
title: "Recommended way to get newest runit?"
date: 2005-12-05
forum: Repositories &amp; Backports
---

### Post by HippoMan on 2005-12-05
I have noticed that the "runit" package is at version 1.2.3 in Ubuntu, but it's at 1.3.1 in Debian sid.  The author of runit is also a Debian maintainer, and he keeps his package up to date over there.

I want to use runit-1.3.1, which has some new features, and I'm wondering what is the recommended Ubuntu way of installing that version.  I know that I can do a non-dpkg install using the author's tar.gz package, but I'd prefer to use a Debian-ized/Ubuntu-ized version, because in this case, the package makes use of proper Debian/Ubuntu installation directories, which the tar.gz package does not.

Am I out of luck until runit-1.3.1 gets ported to Ubuntu, or is there some sort of accepted procedure in Ubuntu for hooking into the Debian repositories for one-off special installs such as this one? ... or what?

Thanks.

---

### Post by m0biu5 on 2005-12-05
You may be able to get it in the backports if it is Debian supported. Go over and check out the request forum.

---

### Post by HippoMan on 2005-12-05
[quote=m0biu5]You may be able to get it in the backports if it is Debian supported. Go over and check out the request forum.[/quote]
Thanks.  I'm new here and until tonight didn't quite get the significance of the backports repository.  I'm on my way over there now ...

---

### Post by m0biu5 on 2005-12-05
Hey, no problem. I don't think you'll have much trouble if it is official debian.

---

### Post by HippoMan on 2005-12-10
* deleted here so I can can create a new thread, instead *

---

