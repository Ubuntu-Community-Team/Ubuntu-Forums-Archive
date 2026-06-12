---
title: "Help with automatic gallery on webserver"
date: 2007-05-05
forum: Server Platforms
---

### Post by Garyu on 2007-05-05
[http://eric.extremeboredom.net/wiki/doku.php?id=projects:quickthumbs](http://eric.extremeboredom.net/wiki/doku.php?id=projects:quickthumbs)

I found this C# application for apache that I was trying to get to work, but it just won't work out very well.

Some things in the guide are not mentioned. This is basically what I did:

```
sudo aptitude install libmagick9 libexif12 mercurial mono mono-mcs libapache2-mod-mono mono-apache-server2 
hg clone http://bits.extremeboredom.net/quickthumbs--mainline
cd quickthumbs--mainline/src
make
sudo mkdir /var/www/gallery
 sudo cp -a * /var/www/gallery/
sudo chown www-data /var/www/gallery/bin/*
sudo gedit /etc/apache2/mods-enabled/mod_mono.conf  (change to mono-server2)
sudo /etc/init.d/apache2 restart

```

So, now I have a directory listing of [http://localhost/gallery](http://localhost/gallery) with all of the quickthumbs files... But how on earth do I get this to a gallery?

The premises of this gallery application is rather nice. I am supposed to just copy a directory structure of images in separate folders and get an automatic picture gallery. I would very much like to have that. But the installation is far more complex than I need it to be. So, can someone please help me simplify this?

Or, alternatively, can someone give a suggestion of something else I can use which reads a directory structure with images and creates an image gallery automatically? Preferrably PHP. Thanks.

---

