---
title: "Web Server Help"
date: 2008-06-21
forum: Server Platforms
---

### Post by johnswb on 2008-06-21
Hello all,

I've just got my Ubuntu WebServer up and running on Apache.  I've copied over my web site from a Windows server and successfully got it to up.  My problem now is I can't edit my index.htm file from an XP box using Dreamweaver.  I've successfully connected to the web server via FTP from within the application and see the files.  When I make any changes and hit F12 to view the changes in a browser I get the following message after saving it.


> Started: 6/21/2008 10:04 AM

index.htm - error occurred - An FTP error occurred - cannot put index.htm.  Access denied.  The file may not exist, or there could be a permission problem.   Make sure you have proper authorization on the server and the server is properly configured.

File activity incomplete. 1 file(s) or folder(s) were not completed.

Files with errors: 1
index.htm

Finished: 6/21/2008 10:04 AM
This is what I've done so far to try and fix the problem myself.

```
chown webuser.yourgroup -R /path_to_document_root
```
and
```
chmod g+w -R /path_to_document_root
```

After doing chmod 777 to every file in the web folder.  

Also, I'm using WebMin for most of the configuration of the webserver.

I am at a lost please help.

---

### Post by Sef on 2008-06-23
Moved to Server Platforms.

---

### Post by windependence on 2008-06-23
Can you post the output of :

```
ls -la /path_to_doc_root
```


-Tim

---

### Post by molotov00 on 2008-06-23
Agree with windependence.

I assume you're getting this error outside of Deamweaver as well? If you just try uploading/overwriting files via FTP?

Looks like a file permission issue on the ftp server... should be easy once we see ls.

Oh, what user are you logging in as, via FTP? webuser.yourgroup (or did you just make that up for this post?)

---

### Post by cariboo on 2008-06-24
Why not create a directory in your home directory for all your data then create a symlink from /var/www to that directory for example in /var/www type:

```
sudo ln -s /home/user/web web_data
```

This way the linked directory in /var/www/web is owned by root and you still have access to the directory in /home/user.

Jim

---

