---
title: "getting GD2 installed with PHP5 on Ubuntu 7.04"
date: 2007-06-21
forum: Server Platforms
---

### Post by cards1007 on 2007-06-21
I'm looking for advice on getting GD2 working with PHP5.

I've completed the LAMP server install of Ubuntu 7.04. I've tried doing an apt-get install php5-gd2, but I get a "Couldn't find package php5-gd2" error. I see there is a package for php5-gd, but this seems to be a different version? I installed this package in hopes that it was the same thing.

I'm trying to get this installed to work with CATS ([http://www.catsone.com/]("http://www.catsone.com/")). When I run the CATS installwizard.php, it shows that GD2 is not installed.

I then removed the php5-gd package and retried the CATS installwizard.php, but I get the same error saying GD2 is not installed. It tells me to check the settings in php.ini, but there is no mention of gd2. There IS mention of gd, which reads as follows:
```
[gd]
; Tell the jpeg decode to libjpeg warnings and try to create
; a gd image. The warning will then be displayed as notices
; disabled by default
;gd.jpeg_ignore_warning = 0

```
How do I get gd2 installed and working with PHP5?

Thanks in advance for any suggestions!

---

### Post by cards1007 on 2007-06-21
Nevermind...got it.

I did the apt-get install php5-gd (again, after I had previously removed it...)
Then *restarted apache*...ran the installwizard.php again and everything works. Oops.

---

