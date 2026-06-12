---
title: "APACHE SERVER issue"
date: 2010-12-10
forum: Server Platforms
---

### Post by jdgregson on 2010-12-10
[Ubuntu 9.10 - LAMPP w/ Apache Server (Not sure which version)]

I know this isn't the right place for this kind of question, but I couldn't find any forums like this on any of the Apache pages, and I'd rather not read Apache documentation and FAQ's for hours trying to figure out how to solve this problem. 

Alright, so I chanced the DocumentRoot in httpd.conf (DocumentRoot from /opt/lampp/htdocs to /usr/bin/Archive). It worked like it should, and is serving files normally... almost. 

It loads the index.html like it should, loads images like it should, but it doesn't autoindex directories without an index. Applying new file permissions doesn't help it. If I put an index.html in a directory, it loads the index, but if I go to the same directory without an index.html in it, I get an "Access Forbidden" error. Also, If I type in the URL of a file inside one of these directories, it loads the file like it should. Applying new file permissions doesn't help (I had to say it twice, because I just KNOW someone is going to say "Just type 'chmod 755 "Your Directory'")!  

Okay, so a summary of what I know and think:

- Problem started after I changed the DocumentRoot
- Problem is probably not related to file permissions (I also tried 777 and others with the same results)
- I believe that the problem is with one of the Apache conf files, but I don't know which one/ones.
- Problem is in short "Files are all served normally, except for when you visit a directory without an index.html file, when it should say "Index of Your Directory" it says "Access Forbidden"   

It may be important to note that the new DocumentRoot (/usr/bin/Archive) is also a Samba share!

---

### Post by SeijiSensei on 2010-12-10
> **jdgregson said:**
> Alright, so I chanced the DocumentRoot in httpd.conf (DocumentRoot from /opt/lampp/htdocs to /usr/bin/Archive). It worked like it should, and is serving files normally... almost. 

It loads the index.html like it should, loads images like it should, but it doesn't autoindex directories without an index.

Ubuntu enforces the same strict access rules that Apache does by default.  In /etc/apache2/sites-enabled/000-default we see:

```

<Directory />
     Options FollowSymLinks
     AllowOverride None
</Directory>                                                                
<Directory /var/www>
     Options Indexes FollowSymLinks MultiViews
     AllowOverride None
     Order allow,deny 
     allow from all                                     
</Directory>

```

The default for all directories ("<Directory />") does not include the "Indexes" [Option]("http://httpd.apache.org/docs/current/mod/core.html#options") the same way the definition for /var/www does.  Note, too, that the default configuration of "[AllowOverride]("http://httpd.apache.org/docs/current/mod/core.html#allowoverride") None" doesn't permit the use of a .htaccess file to override the Option, either. If you want to permit indexing of directories, you'll need to include "Options Indexes" in the definition of your virtual host in /etc/apache2/sites-enabled the way it appears for /var/www.

> It may be important to note that the new DocumentRoot (/usr/bin/Archive) is also a Samba share!

That shouldn't matter.  However I will say that placing shares under /usr/bin violates the basic file logic that most Linux distributions share.  Mountable devices are typically in /media, and mounted remote filesystems (Samba and NFS mounts for instance) usually appear under /mnt.  /usr/bin is considered off-limits for much of anything that's not an executable binary.  I'd expect to find web sites in /var/www or /home/username/something. (I use /home/username/web myself.  /home/username/public_html is another common location.)  If you're going to mount a Samba share, put it in /media or /mnt.  Use an Alias directive in Apache if you want to share it via HTTP.

---

### Post by garryconn on 2010-12-10
Hi jdgregson,

I'm sure you're in good hands with getting the support you need. I'm pretty new with Linux so I can't directly help you. But I do have a question for you (mainly to help me learn more). 

Why are you changing the DocumentRoot? I can understand changing it to something like /home/username/public_html but what's the reasoning behind changing it into other directories such as the /opt/lampp/htdocs to /usr/bin/Archive directory?

---

### Post by jdgregson on 2010-12-11
Alright, SeijiSensei, that is very helpful, but I changed the DocumentRoot back to the default now, and it works like it should. I'm not sure why I didn't think of this in the first place, but I placed the Samba share inside the /opt/lampp/htdosc directory. 

garryconn, that's a good question, but I don't really have a reason to recommend it. The reason I had /urs/bin/Archive as a Samba share is because, at the time I made it (I was also really new to Linux) I liked the way the file path sounded. I just liked the way '/usr/bin/Archive' sounded. But why I changed the DocumentRoot to /usr/bin/Archive is a different story. Basically, I wanted laptop/desktop users and iPod users to be able to access the files, but iPods cant access samba shares, they have to use the web browser, or some other app. Instead of having 10gb of music and video in the Samba share for laptops/desktops, and the same 10gb also in /opt/lampp/htdocs for iPods, I wanted to put it all in one place. But instead of moving the samba share to /opt/lampp/htdocs/archive (which I did last night) I changed the document root to /usr/bin/Archive.

Thank you for you time and answers.

---

