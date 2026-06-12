---
title: "PHP/GD-functions that need bundled GD don't work"
date: 2006-06-25
forum: Server Platforms
---

### Post by Dingen on 2006-06-25
I'm using my Ubuntu 6.06 Dapper-machine as a LAMP-server, with Apache2 and PHP5. It's working great, but I've encountered a little problem.

The GD-functions to output and manipulate images with PHP work fine, except the functions that need the "bundled GD", like [this one]("http://nl2.php.net/manual/en/function.imagefilter.php") or [this one]("http://nl2.php.net/manual/en/function.imageantialias.php").

I've installed php5-gd.

What should I do to install this "bundled GD" so I can use these functions?

---

### Post by Randomskk on 2006-06-25
Basically, the only way to do it is to compile your own PHP5.
I had this a week back, and there is a bug out for it that's closed - the PHP maintainer said that due to security reasons, Ubuntu will NOT use the PHP-bundled version of GD.
I know, it sucks, but not much you can do besides compile your own PHP.

---

### Post by Dingen on 2006-06-25
Hmm... so if I compile my own PHP5 with bundled GD, will that create a security risk on my machine?

---

### Post by Randomskk on 2006-06-25
Not much of a security risk, and it depends if you allow other people to execute PHP code.
The main thing seems to be that some of the bundled GD functions are not very secure, and may get around file limits and things.

I don't believe it will make a big security risk, and if you want/need the extra functions that's the only way to get it.

You could email the maintainer and ask about why Ubuntu don't do it, this is the bug I mentioned:
[https://launchpad.net/distros/ubuntu/+source/php5/+bug/39719](https://launchpad.net/distros/ubuntu/+source/php5/+bug/39719)

---

### Post by Dingen on 2006-06-25
Thanks very much, this makes it very clear.

Now I have to ask myself: do I need the extra bundled-functions? I wanted to use the [imagefilter](http://php.net/imagefilter) and/or [antialias](http://nl2.php.net/imageantialias) functions for some visual prettyness. But I guess it works without them.

*still in doubt* :-k

---

### Post by Randomskk on 2006-06-25
Yea, I faced the same thing: both make the images look nice and pretty, but to get that you have to compile your own PHP, which could mess all sorts of things up :(

I'd like to know exactly why they don't use the bundled version of PHP's GD, there must be a good reason...

---

### Post by Dingen on 2006-06-25
I've e-mailed Adam and asked about the nature of the security issues with PHP's GD. I hope he replies.

---

### Post by Randomskk on 2006-06-25
Cool, let me know if you get a reply

Thanks

---

### Post by xurizaemon on 2006-07-25
worked for me by installing the package php5-gd (i'd been farting around trying to find "php-gd", silly me)

---

### Post by xurizaemon on 2006-07-25
for me, the AUTOMATIC THUMBNAILING in WORDPRESS on my UBUNTU DAPPER 6.06 didn't work until i installed the package PHP5-GD.

once i did that the automatic thumbnails on inline file upload in wordpress 2 (wp2) worked a treat. lovely stuff. thanks again ubuntu :)

---

