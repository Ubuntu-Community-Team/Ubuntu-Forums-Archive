---
title: "Can you downgrade to PHP 5.4?"
date: 2017-08-07
forum: Server Platforms
---

### Post by brooker2 on 2017-08-07
Hi, I am a long time CentOS user thinking about switching to Ubuntu.

One of the requirements of some of the PHP apps on the server is PHP 5.4, is it possible to 'downgrade' to this if I opt for Ubuntu 17.04?[COLOR=#666666][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2017-08-07
First, you don't want to run a server on 17.04.  Ubuntu issues releases with "long-term support" every two years.  The currently active LTS release is 16.04.  The next one comes out in April, 2018.  All other releases are supported for only nine months.

I'd be very surprised if an application that required 5.4 won't run on 5.5.  I'd start with a copy of [Server 14.04]("http://cdimage.ubuntu.com/releases/14.04.5/release/"), which has complete support through April of 2019.  It [defaults to 5.5]("https://launchpad.net/ubuntu/+source/php5"). Ubuntu 16.04 and later all have [PHP7]("https://launchpad.net/ubuntu/+source/php7.0").

I suggest using something like VirtualBox and doing some testing in a virtual machine.  See if the apps will work with 5.5 in the VM.

I still use CentOS on my servers at Linode.  They all run some flavor of CentOS 6.

---

### Post by brooker2 on 2017-08-07
Thanks for the tip about 17.04.

I've just checked, and unfortunately the software only runs in 5.4 and confirmed not working in 5.5.

Is there any way to use 5.5 in 16.04?

---

### Post by SeijiSensei on 2017-08-07
I don't see too many options other than compiling 5.4 from source.  The most recent release is 5.4.45; you can download the source code here: [http://php.net/get/php-5.4.45.tar.gz/from/a/mirror](http://php.net/get/php-5.4.45.tar.gz/from/a/mirror)

I haven't done this in a very long time.  It's a bit tricky because you actually need to compile a module for Apache.  There's a file called INSTALL in the tarball; the instructions you need are in the section on installing to Apache 2.x.

---

### Post by brooker2 on 2017-08-08
Thanks - I'll look into that :)

---

### Post by SeijiSensei on 2017-08-09
Good luck!

---

