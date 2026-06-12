---
title: "Apache Mime Support broke with Ubuntu by default"
date: 2006-01-26
forum: Server Platforms
---

### Post by metapunk on 2006-01-26
Hello. I've posted about this once before but got no response.
I've been having numerous problems with Apache2 and Php5 with Ubuntu.
By default it appears that the Ubuntu packages don't include mod.mime and mime.magic doesn't work.

This has mostly been happening with Drupal 4.6, and it is definently an aspect of the Ubuntu install. Everything I upload has .txt attached to it because Mime.Magic doesn't appear to be working. 

I did install it as an available module and restarted Apache2 but I can't get it to work otherwise. I had thought that this problem was isolated to Apache2 + Php5, but now I'm having similar problems with a server running Apache1 and Php 4.4.

Both of these are Breezy systems. I am just hoping someone has had similar problems or can provide me with some sort of troubleshooting procedures or tips/hints.

---

### Post by LordHunter317 on 2006-01-26
Yes, they do.  I'm sure mod_mime is builtin to the Apache binary, and cannot be disabled.

[quote=metapunk]This has mostly been happening with Drupal 4.6, and it is definently an aspect of the Ubuntu install. Everything I upload has .txt attached to it because Mime.Magic doesn't appear to be working.[/quote]mod_mime_magic has generally given me more trouble than it's worth in my experience.  And it sounds more like a drupal issue to me.

---

### Post by MJN on 2006-01-26
As LordHunter says, **mod_mime**is part of the default core.

As you've enabled **mime_magic**, try putting **MIMEMagicFile magic** inside the **<VirtualHost>** container of your **sites-available/default** config and restart Apache...

Does it work now...?

Incidentally, what do you mean by *'every file has .txt attached to it'*? Mime types only influence how the server declares the file *type and encoding *etc and does not actually change the file *name* (which .txt is simply a part of - leave the Windows reliance on extensions in the past ;)). Or do you mean it *appears* as if the files are being changed to text (.txt) files..? Or perhaps this is something Drupal messes with (I have no experience of it).

You mentioned PHP, is it these files that are not working properly? If so, try adding **AddType application/x-httpd-php .php** and **AddType application/x-httpd-php-source .phps **to mods-available/php5.conf (_not_ inside the <Files *.php> container) and comment out **SetOutputFilter PHP **and **SetInputFilter PH** (these _are_ inside <Files *.php>).

Mathew

---

### Post by metapunk on 2006-01-27
Ok, well I'm still having this problem. I tried what you said to no avail.

I don't know what the cause of this is, but basically what drupal is doing is uploading a file to /tmp and then trying to determin it's type with mod_mime and then for some reason it can't figure it out and decideds by default it's a .txt file and then it doesn't work properly in the program.

As far as I know this problem isn't widespread and very few other people are reporting it but it happens to both of my drupal servers, both breezy. One running whatever the latest Apache 1.3 and Php 4.4 modules and the other one the latest Apache2 and php 5 modules.

It probably is something related to Drupal but I can't figure out why I'm only being affected by it with Ubuntu servers whereas it works fine on other servers.

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=metapunk]I don't know what the cause of this is, but basically what drupal is doing is uploading a file to /tmp and then trying to determin it's type with mod_mime and then for some reason it can't figure it out and decideds by default it's a .txt file and then it doesn't work properly in the program.[/quote]What are you uploading?

---

### Post by MJN on 2006-01-28
...and can you also confirm that you've got **mime_magic** working within Apache for files (without 'known' extension) that you've *manually* uploaded (i.e. take Drupal out of the loop for the time being)? By 'working', I mean Apache is correctly identifying the mime type for files based on content (i.e. mime_magic matching expressions within the file) and correctly informing the client the mime type?

My mime_magic is working perfectly so I know it in itself is likely not 'broke' (however I don't use Drupal so, as LH says, it sounds more like a problem with that).

Mathew

---

### Post by can3p on 2006-02-05
I've found solution to this problem at [http://drupal.org/node/43568](http://drupal.org/node/43568)

All you need is to set mime_magic.magicfile=/etc/apache2/magic in /etc/php5/apache2/php.ini where /etc/apache2/magic is a magic file from apache package, php.ini is php configuration file. Then just restart apache and everything will work

---

### Post by DrakeGuan on 2006-02-08
it works!

but /etc/apache2/magic supports very few file types. for example, png & flash files are not included. 

I just tried to copy matching expressions for png from /usr/share/misc/file/magic.mime to /etc/apache2/magic and make sure the delimiter is tab. but php function 'mime_content_type' seems not recognize it or match it into wrong mime type @@ it returns 

httpd/unix-directory

why?

I'm using 5.04 hoary.

---

### Post by MJN on 2006-02-08
Check out [http://uk2.php.net/mime_magic]("http://uk2.php.net/mime_magic").
 
It states:
 
> You must compile PHP with the configure switch --with-mime-magic to get support for mime-type functions. The extension needs a copy of the simplified magic file that is distributed with the Apache httpd.
 
Note: The configure option has been changed from --enable-mime-magic to --with-mime-magic since PHP 4.3.2
 
Note: This extension is not capable of handling the fully decorated magic file that generally comes with standard Linux distro's and is supposed to be used with recent versions of file command

 
..thus it would appear you can't just add in entries from the more-comprehensive 'standard' magic file - if an entry has been removed then it's for a reason.
 
Mathew

---

### Post by can3p on 2006-02-09
[QUOTE=DrakeGuan]
I just tried to copy matching expressions for png from /usr/share/misc/file/magic.mime to /etc/apache2/magic and make sure the delimiter is tab..[/QUOTE]

magic.mime has different format than magic file.
Try To use /usr/share/mimelnk/magic. It's much bigger and is used by gnome, kde etc, as I understand. It works great for me

---

### Post by MJN on 2006-02-09
It's exactly the same format.

As stated in the above URL, the PHP extension works with a cut down version of the 'standard' file. This is cut down as in number of enttries, not format.

When you say it works great for you, are you talking about with Drupal?

Mathew

---

### Post by can3p on 2006-02-10
[QUOTE=MJN]It's exactly the same format.

As stated in the above URL, the PHP extension works with a cut down version of the 'standard' file. This is cut down as in number of enttries, not format.
[/QUOTE]

I was wrong, this file really has the same format, but look:
```

$ ls -l /usr/share/misc/file/magic.mime
-rw-r--r--  1 root root 30429 2005-09-16 17:08 /usr/share/misc/file/magic.mime
$ ls -l /usr/share/mimelnk/magic
-rw-r--r--  1 root root 40669 2005-11-19 11:56 /usr/share/mimelnk/magic
$ ls -l /etc/apache2/magic
-rw-r--r--  1 root root 12441 2005-10-04 10:52 /etc/apache2/magic

```

As you can see, /usr/share/mimelnk/magic is the biggest file and supports more mime-types. Just try to use it(set mime_magic.magicfile=/usr/share/mimelnk/magic in php.ini)

[QUOTE=MJN]
When you say it works great for you, are you talking about with Drupal?
[/QUOTE]

No, I'm talking about result from the mime_content_type() php function. I'm sure that Drupal engine uses it, because it's the only way to determine file type in php

---

