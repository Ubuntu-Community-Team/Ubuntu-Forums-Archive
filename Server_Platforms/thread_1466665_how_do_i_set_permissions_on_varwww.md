---
title: "how do i set permissions on var/www ???"
date: 2010-04-30
forum: Server Platforms
---

### Post by whitetimer on 2010-04-30
Hi All

Just setting up flash-builder 4 in xubuntu and when i try to set up a test project on the server /var/www i receive a write permissions not allowed ...

How do i set read & write on this folder to my user-name please ?

:guitar:

---

### Post by ghost_ryder35 on 2010-04-30
> **whitetimer said:**
> Hi All

Just setting up flash-builder 4 in xubuntu and when i try to set up a test project on the server /var/www i receive a write permissions not allowed ...

How do i set read & write on this folder to my user-name please ?

:guitar:

use sudo.  the permissions are correct for the folder, but your user does not have access to write into the directory.  

```

sudo vi /var/www/magic.html

```

---

### Post by whitetimer on 2010-04-30
> **whitetimer said:**
> Hi All

Just setting up flash-builder 4 in xubuntu and when i try to set up a test project on the server /var/www i receive a write permissions not allowed ...

How do i set read & write on this folder to my user-name please ?

:guitar:

Sorted ... I did this sudo chmod -R 777 /var/www


:lolflag:

---

### Post by ghost_ryder35 on 2010-04-30
> **whitetimer said:**
> Sorted ... I did this sudo chmod -R 777 /var/www


:lolflag:

that is a horrible idea

---

### Post by sisco311 on 2010-04-30
> **whitetimer said:**
> Sorted ... I did this sudo chmod -R 777 /var/www


:lolflag:

Hmmm, not the best solution. 

Check out:

[uhelp]community/ApacheMySQLPHP#Virtual%20Hosts[/uhelp]
and
[uhelp]community/FilePermissions[/uhelp]

---

### Post by whitetimer on 2010-04-30
Hi 

Its just a development pc at home, thats why i did it that way for now.

:(

---

### Post by arrrghhh on 2010-04-30
Just curious, what should the permissions look like for /var/www?  Obviously owned by www-data user&group, but what about read & write permissions?

---

### Post by ghost_ryder35 on 2010-04-30
> **arrrghhh said:**
> Just curious, what should the permissions look like for /var/www?  Obviously owned by www-data user&group, but what about read & write permissions?

```

foo@ubuntu:~$ ls -hal /var/
drwxr-xr-x.  6 root root 4.0K 2009-12-03 09:26 www
foo@ubuntu:~$

```

---

### Post by arrrghhh on 2010-04-30
Owned by root:root?  I have my owned by www-data:www-data...

---

### Post by ghost_ryder35 on 2010-04-30
> **arrrghhh said:**
> Owned by root:root?  I have my owned by www-data:www-data...

hmm that is weird it should be owned by www-data:www-data.  I didnt even look when I copy and pasted... now I am wondering what happend to my little ubuntu. :)

---

### Post by cdenley on 2010-04-30
Why would you want it owned by www-data? You don't what apache to be able to modify the files it is serving. A compromise in apache or a web application could then compromise your content, spreading malware to your website visitors.

---

### Post by ghost_ryder35 on 2010-04-30
> **cdenley said:**
> Why would you want it owned by www-data? You don't what apache to be able to modify the files it is serving. A compromise in apache or a web application could then compromise your content, spreading malware to your website visitors.
on the same note though, if your visitors are say uploading photos and your storage for those is /var/www/photos apache would need to be able to write there.

---

### Post by arrrghhh on 2010-04-30
So www-data should own stuff that users need to upload to, but if they're just downloading and not needing any write permissions whatsoever, owning by root:root is expected?

Also, back to chmod permissions... do I chmod to 766 to achieve the correct rights?

---

### Post by cdenley on 2010-04-30
> **ghost_ryder35 said:**
> on the same note though, if your visitors are say uploading photos and your storage for those is /var/www/photos apache would need to be able to write there.

Allowing visitors to upload files to /var/www is another horrible idea. I hope you don't allow any malicious PHP scripts to be uploaded. If you need to allow uploads, it is best to place uploaded files somewhere else. If you're trusting and want to allow uploads to /var/www/photos, then give write permission for that directory, not all of /var/www.

---

### Post by ghost_ryder35 on 2010-04-30
> **cdenley said:**
> Allowing visitors to upload files to /var/www is another horrible idea. I hope you don't allow any malicious PHP scripts to be uploaded. If you need to allow uploads, it is best to place uploaded files somewhere else. If you're trusting and want to allow uploads to /var/www/photos, then give write permission for that directory, not all of /var/www.
touché

---

### Post by cdenley on 2010-04-30
> **arrrghhh said:**
> So www-data should own stuff that users need to upload to, but if they're just downloading and not needing any write permissions whatsoever, owning by root:root is expected?

Also, back to chmod permissions... do I chmod to 766 to achieve the correct rights?

Pretty much. I usually just give all users write-permission if apache needs to write to a directory.

755 for directories like /var/www, 644 for files, assuming it is owned by root.

---

### Post by arrrghhh on 2010-05-03
> **cdenley said:**
> Pretty much. I usually just give all users write-permission if apache needs to write to a directory.

755 for directories like /var/www, 644 for files, assuming it is owned by root.

Excellent, thank you.  I just adjusted all my permissions, so only the upload directory is owned by www-data/chmodd'd to 777 :D

---

