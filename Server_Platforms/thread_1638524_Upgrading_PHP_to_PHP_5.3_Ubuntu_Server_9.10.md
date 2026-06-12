---
title: "Upgrading PHP to PHP 5.3 Ubuntu Server 9.10"
date: 2010-12-05
forum: Server Platforms
---

### Post by IkeLewis on 2010-12-05
Hi there,

I have been looking around for [options to install]("http://www.howtoforge.com/installing-php-5.3-nginx-and-php-fpm-on-ubuntu-debian") php 5.3 on a Karmic server.

If php 5.3 is in the Lucid repos, then is there a way to upgrade from them? I was looking at [Dot Deb]("http://www.dotdeb.org/"), but I was wondering if there was a more seamless way to upgrade from Ubuntu's repos.

Thanks,

Ike, alias MeltingK33board.

---

### Post by chrislynch8 on 2010-12-06
try adding the lucid repos to your lists

---

### Post by IkeLewis on 2010-12-06
Yeah, I tried that, and then it still held back the php packages from upgrade... if I then did an "aptitude dist-upgrade" then it would upgrade all the packages, but at that point it seems like upgrading to Lucid would be better. So that is what I am doing.. just doing a network upgrade to Lucid.

---

