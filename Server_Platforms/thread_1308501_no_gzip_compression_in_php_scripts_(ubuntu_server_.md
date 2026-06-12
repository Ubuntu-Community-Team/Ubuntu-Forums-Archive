---
title: "no gzip compression in php scripts (ubuntu server karmic)"
date: 2009-10-31
forum: Server Platforms
---

### Post by agamum on 2009-10-31
Hi!

I just installed from scratch an ubuntu server (karmic) for LAMP use, and I noticed that php applications (i.e. phpmyadmin, or some worpress plugins) that usually have an option to compress an export file or backup files using 'gzip', are not showing that option now.

For example, phpmyadmin only gives the option to compress using zip and bzip2, but no gzip...

The phpinfo() is showing:

Registered PHP Streams 	https, ftps, compress.zlib, compress.bzip2, php, file, data, http, ftp, zip 

So I wonder why I cant use gzip from any php script...

What is wrong with PHP package from ubuntu repository?

I'll need to recompile php on my onw? :(

Any help would be appreciated.

---

### Post by Vegan on 2009-10-31
I use phpBB and it is working fine. The settings mention gzip and it seems to be working fine.

Did you install the fill LAMP stack?

if not:

```
sudo tasksel
```

and select LAMP, and install it all

---

### Post by agamum on 2009-10-31
> **Vegan said:**
> 
Did you install the fill LAMP stack?

if not:

```
sudo tasksel
```

and select LAMP, and install it all

Thanks for your fast reply Vegan ;)

Well, I'm on a VPS from a hosting company, so the initial deploy is automatically made by the VPS panel...

I installed some packages manually, but anyway when I run "tasksel" I have already marked the lamp stack.

---

### Post by agamum on 2009-10-31
More info:

I tried to run a simple code to compress and descompress a file using gzip from php, the code is from here: [http://www.whenpenguinsattack.com/2006/12/14/compressing-files-in-php/](http://www.whenpenguinsattack.com/2006/12/14/compressing-files-in-php/)
```

<?php

function uncompress($srcName, $dstName) {
  $string = implode("", gzfile($srcName));
  $fp = fopen($dstName, "w");
  fwrite($fp, $string, strlen($string));
  fclose($fp);
} 

function compress($srcName, $dstName)
{
  $fp = fopen($srcName, "r");
  $data = fread ($fp, filesize($srcName));
  fclose($fp);

  $zp = gzopen($dstName, "w9");
  gzwrite($zp, $data);
  gzclose($zp);
}

//change to the names of your files
compress("test.php","test.gz");
uncompress("test.gz","test2.php");
?>
```

And when I tried to run the script, I get this error:

> PHP Fatal error:  Call to undefined function gzopen() in /var/www/gzip-test.php on line 16

It seems like if PHP in ubuntu repositories was compiled without '--with-zlib' but I found this in my phpinfo() page, so I think that zlib support is fully enabled:

> zlib
ZLib Support 	enabled
Stream Wrapper support 	compress.zlib://
Stream Filter support 	zlib.inflate, zlib.deflate
Compiled Version 	1.2.3.3
Linked Version 	1.2.3.3 

But I cant gzip any file from PHP scripts :(

---

### Post by agamum on 2009-10-31
Finally I found the solution! :)

The problem is caused by a bug in the php package for ubuntu karmic.

You can find the bug report and [solution for zlib problem here]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/451405"). 

Basically adding the proposed repo and reinstall php.

---

### Post by Vegan on 2009-10-31
Good to see, I was looking at you code and it seems OK, but I see that gzip is not bound so I am expecting an update.

Come to my site and lets see if there are any other PHP bugs, my site is all PHP.

---

