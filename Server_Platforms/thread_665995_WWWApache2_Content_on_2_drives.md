---
title: "WWW/Apache2 Content on 2 drives"
date: 2008-01-12
forum: Server Platforms
---

### Post by dunno on 2008-01-12
Hi all,

Would someone help me serve content from 2 drives?

Apache2 is up and running on /media/sda1/, but I keep photos, music, video, etc on /media/sdb1/.

Apache2 serves all the content from /media/sda1 fine, but when it parses the html for the /media/sdb1 it ends up as "/media/sda1/media/sdb1/..." and there is no such path.

How do I keep Apache2 from name-mangling certain paths?

I've tried both relative and direct paths:
"/media/sdb1/photos/..." mangles to "/media/sda1/media/sdb1/photos/..."
"../../sdb1/photos/..." mangles to /media/sda1/photos/..."
This info comes from the error.log.

Thanxmuch.:guitar:

---

### Post by freymann on 2008-01-12
> **dunno said:**
> 
Would someone help me serve content from 2 drives?
Apache2 is up and running on /media/sda1/, but I keep photos, music, video, etc on /media/sdb1/.

 Doesn't the document root define what files are being served by your web browser?

 On ubuntu 7.10 the root directory defaults to /var/www

 You could symlink directories located elsewhere into the root or subdirectories...

 What you're describing doesn't make much sense to me from a web server point of view...

---

### Post by conjur3r on 2008-01-12
Sounds like all you need is to symlink the directory to somewhere within your document root.  Eg, to create a link from /media/sda1/myphotos to /media/sdb1/loc/of/photos:

# cd /media/sda1
# ln -s /media/sdb1/loc/of/photos myphotos

Then to access your photos, point your browser to something like [http://server/myphotos](http://server/myphotos) (or wherever it is in the tree).

---

### Post by dunno on 2008-01-13
The plot thickens...

I considered symlinks, but forgot to mention that both drives are FAT32.  It's my understanding that one cannot create a symlink on or to a FAT drive.

Thanks for the replies

---

### Post by dunno on 2008-01-13
> **freymann said:**
> Doesn't the document root define what files are being served by your web browser?...

 What you're describing doesn't make much sense to me from a web server point of view...

Sorry if i'm not being clear.  Currently, I'm serving /media/sda1/myhtmldocs through apache2 via the document root.  sda1 isn't large enough to hold all my music,photos,etc, so I put it all on another drive, /media/sdb1/Music /Photos /Movies and so on.  I would like the files on sdb1 accessible using the website whose html content is on sda1.

does this clear things a bit?[-o<:confused:

---

### Post by conjur3r on 2008-01-13
Ok no symlinks.  Try the alias directive in apache.  Does a similar thing.  [http://httpd.apache.org/docs/2.2/mod/mod_alias.html](http://httpd.apache.org/docs/2.2/mod/mod_alias.html)

---

### Post by dunno on 2008-01-13
:lolflag:very nice!:guitar:

---

