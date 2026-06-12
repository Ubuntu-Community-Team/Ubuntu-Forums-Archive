---
title: "[SOLVED] Apache Alias folder returns 403 Forbidden error"
date: 2008-03-17
forum: Server Platforms
---

### Post by pssturges on 2008-03-17
Hi,

I'm trying to use a folder containing thumbnails for my web site. It is located at /storage/Media/Posters. I have tried setting an alias but I keep getting a 403 Forbidden error when I try to access any of the file inside.

The code I'm using is as follows:

Alias /posters /storage/Media/Posters
<Directory "/storage/Media/Posters"> 
	Order allow,deny
	Allow from all
</Directory>

I have tried putting this code in several places including:
/etc/apache2/sites-available/default
/etc/apache2/apache2.conf
/etc/apache2/httpd.conf

As a possible alternate solution I tried creating a symlink to the folder in /var/www, but this gave the same results.

I have also tried changing ownership/permissions without any luck.

I have spent about 4 hours searching for a solution to this. I would really like to get it fixed.

I'm happy to post any config or log files that may help.

Thanks in advance
Phil

---

### Post by penguinpi.com on 2008-03-17
The easiest thing to do really is create a link. I realize you tried a few things already but this is what I would try.

sudo chmod -R 777 /storage/Media/Posters

sudo ln -s /storage/Media/Posters /var/www/posters


also is /storage another drive by any chance?

---

### Post by pssturges on 2008-03-17
Thanks for the reply.

I have tried both chmod -R 777 & creating a symlink, still get 403.

And, yes it is another hdd, here is the relevant fstab entry:

# /dev/sda1
UUID=904b7759-b8f2-4cb1-b177-aa6ca6bbffb2  /storage  ext3  suid,dev,exec  0  2

Thanks again
Phil

---

### Post by pssturges on 2008-03-17
I Don't know if it's relevant, but /storage is shared via samba also.

Thanks

---

### Post by penguinpi.com on 2008-03-18
Make sure you have these settings in your samba conf file

Writable = yes
Map system = yes
Follow symlinks = yes
Wide links = yes

---

### Post by pssturges on 2008-03-18
It had the "writable" line, but not the others. I added them but still no luck.

Thanks again
Phil

---

### Post by penguinpi.com on 2008-03-19
check this out.

[http://ubuntuforums.org/showthread.php?t=352016](http://ubuntuforums.org/showthread.php?t=352016)

---

### Post by pssturges on 2008-03-19
Thanks again for the help.

Unfortunately that didn't work either, but I definitely think we're on the right track. ATM I'm trying to set this up using symlinks, just because it seems easier. Now, when I create a link to a folder within "/storage" (separate HDD & samba shared), I get the forbidden error. However, if I create a link to a folder elsewhere (on system hdd & not shared) it works as it should!

Interestingly, I just tried turning off samba, and I still get the error! I guess this points to the separate hdd issue?

Once again, any help much appreciated,
Phil

---

### Post by pssturges on 2008-03-26
Still no luck, I tried moving the whole server to the /storage. I get forbidden on all pages. Moved it back.

Definitely seems to be because it's a non-sytem HDD.

Thanks for any help.
Phil

---

### Post by pssturges on 2008-03-31
OK, finally figured this one out! Turns out it was nothing to do with Samba, or being a seperate HDD. I found I was able to use some folders within "/storage'. The folders that I couldn't use, for some reason didn't have x permission globally!

So, chmod +x, and all works beautifully.:p

Phil

---

