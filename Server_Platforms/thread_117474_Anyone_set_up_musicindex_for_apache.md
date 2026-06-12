---
title: "Anyone set up musicindex for apache ?"
date: 2006-01-15
forum: Server Platforms
---

### Post by dbee on 2006-01-15
Has anyone setup the musicindex mod for apache ???

I'm back on apache with ubuntu and once again I'm finding things completely indecipherable. :(

The musicindex folder is in my document root, but I can't see it from my localhost. I have a feeling that this is something to do with the great enigma that is 'sites-enabled'. There is nothing about any of this in the wiki btw ? 

Also, where have my virtual directory configs in apache2.conf gone ? apache2.conf seems to be split up into parts and then scattered to the wind ?

---

### Post by drogoh on 2006-01-15
mod_musicindex is a pain to fool with; try gnump3d out for size instead.  It does essentially what mod_musicindex does but with the magic and love that is Perl.

---

### Post by dbee on 2006-01-15
Thanks drogoh I'll give it a try

---

### Post by duffydack on 2006-01-15
ive set it up ok,  pretty simple.
make a link to the module
sudo ln -s /etc/apache2/mods-available/musicindex.load /etc/apache2/mods-enabled/
add something like this to the sites-enabled file you have
ive mounted my mp3`s in var/www/ as "music".  Its on a windows hd.

<Directory "/var/www/music/">
Options Indexes MultiViews FollowSymlinks
AllowOverride None
Order allow,deny
Allow from all
MusicLister On
MusicSortOrder album disc track artist filename title length bitrate filetype uri
MusicFields title artist length bitrate
MusicAllowDownload Off
MusicAllowStream On
MusicAllowSearch On
MusicPageTitle Mp3 Collection
MusicCssDefault musicindex.css
MusicCachePath /tmp/musicindex
#MusicIceServer idontuseone:8000
MusicCookieLife 300
</Directory>

ive actually added it as part of main <directory> config.   i also tried to make it my default root page but doesnt show up properly, love to know how if anyone knows.

[http://server : port/music](http://server : port/music) and voila

---

### Post by duffydack on 2006-01-15
There is also this page to look at if you need some help

[http://www.ubuntuforums.org/showthread.php?t=34359](http://www.ubuntuforums.org/showthread.php?t=34359)

---

