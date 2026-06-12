---
title: "Need your opinion!"
date: 2010-10-29
forum: Server Platforms
---

### Post by gm112 on 2010-10-29
Hello! I've recently been debating my choice of HTTP server software. Lighty(LightTPD) has always been my favorite, and it's done its job quite well(sans the rewrite issues I have had with some software). However, a friend of mine recently suggested that Apache was better due to it having .htaccess. I haven't been able to really.. well, come to a conclusion regarding this. You see, I am teaching myself how to deploy and manage fully chrooted servers, and I just wanted your opinion on this.

Which do you think would be easier to maintain in a chroot jail? 
Is Lighty or Apache more "suited" for this sort of thing? I personally believe that it's equally as difficult, but I am still curious nevertheless.

Would Apache be more secure in chroots?


In the long-run, which is more resource friendly? Lighty or Apache?

I have yet to experience a memory leak with Lighty, even though people seem to complain about one. Apache-worker, and Apache-prefork seem to both eat more CPU and RAM, but still curious.


Just so you know, my test setup is running Apache-Worker with mod-fcgi allowing me to use PHP5. Lighty, I've used FastCGI to spawn PHP5 processes. I've had problems with getting drupal to run properly on Lighttpd, so this begin to make me wonder...

---

### Post by hantechbl on 2010-10-30
I'd choose apache it's more widely used, but that could also pose more security risks...

---

