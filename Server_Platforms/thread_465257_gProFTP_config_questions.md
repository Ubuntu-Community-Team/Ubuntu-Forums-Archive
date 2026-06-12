---
title: "gProFTP config questions"
date: 2007-06-05
forum: Server Platforms
---

### Post by freebeer on 2007-06-05
Hi guys!

I have gproFTP running quite nicely, thanks to help received here.  I want to take my knowledge a little further... I couldn't find documentation on this, so I figured that I'd ask here.

I'm also running Apache 2 (without LAMP).  Just a basic web page for testing 'n stuff.

What I now want to do is to use some of the various webpage creation programs to edit/update said site from a different machine.  (Basically make changes, etc. and push the new pages to the web site.)

Can I configure gproFTP to do this securely?  My current FTP setup points the ftpusers to a folder called /ftp with a few folders below that (the typical /upload /download /your_mama_wears_army_boots setup).  The web folder is /var/www.

Is it as simple as creating a new user (or group) within gproFTP whose ftp home folder is /var/www? (and assuming correct priviledges).  I don't want the regular ftp users to see or have access to the /var/www folder (unless it's through a browswer). 

Is there a better way?  Any and all thoughts or ideas are welcome.

Thanks!

---

### Post by NumberOne on 2007-06-05
In gproftp create a user (I used webftp as a user name) and assign its home directory as /var/www.  its that easy.

---

### Post by freebeer on 2007-06-05
I figured it would be pretty simple.  I'll give it a go... and thanks for the confirmation!  =D>

---

### Post by freebeer on 2007-06-06
Yup.. that worked out well.  I just have to mess with the file-level permissions now so that I can write back the changes.  Thanks again!

---

