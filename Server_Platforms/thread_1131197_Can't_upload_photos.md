---
title: "Can't upload photos"
date: 2009-04-20
forum: Server Platforms
---

### Post by kaj on 2009-04-20
I made a big mistake when i upgraded my server from Unubntu 6.06 LTS to Ubuntu 8.04 LTS.
On my old server I had a variety of cms systems installed for testing, and some of them I have also installed on the new server, but there are a common fault in all of them: I cannot upload pictures.

Some of them uploads the file name, but the files are empty.

The cms system Flatpress told me, that i had to enable the Php GD2 extension. After some search I found the package phpgd and some dependensies and the error message disappeared, but I was still not able to upload any files.

Wordpress tells me, that the file is empty, please upload something with a content. Or uploads are not enabled in your php.ini.

I have searched my system for php.ini, and I found three:
/etc/php5/apache2/php.ini
/usr/share/php5/php.ini-dist
/usr/share/php5/php.ini-dist.cli

I guess it's the first one that counts, but there's the same thing in all of them:

;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not
; specified).
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
upload_max_filesize = 2M

I hope that someone has a solution to my problem.

Kaj Rasmussen

---

### Post by cdenley on 2009-04-20
Did you also recently upgrade the computer you are uploading from? I know firefox 3 broke some upload utilities since the javascript value of a file input no longer contains the full path to the file. I would try a simple PHP upload script.

---

### Post by kaj on 2009-04-20
I can't programme php, but such a script aught to be included in the various content management systems, I am using.

On my old server witch was working until about 10 days ago, upload went perfectly well, both from localhost (I have the Gnome desktop installed) and from two other computers, with Firefox 3 and IE 7.
It had been working right from the start, so I don't know exactly, what did make it work.

I have searched in Synaptic and installed some packages that I thought could have just the slightest influence, but nothing works.

---

### Post by cariboo on 2009-04-20
I don't have a server running php at the moment, but I seem to rememberr having to enable gd in a php.ini file. Check /etc/php5/php.ini.

Jim

---

### Post by kaj on 2009-04-21
I am copying the gd section from phpinfo() in below, and I think, that it is allright. 

gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.3.5
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled

I have found out, that I can upload pictures from my other computers, but I can't resize them and I can't make thumbnails.
But I can't upload from localhost itself. 

My old server could do all these things without me having to any configuring at all.

---

