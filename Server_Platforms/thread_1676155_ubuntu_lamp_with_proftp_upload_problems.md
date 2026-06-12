---
title: "ubuntu lamp with proftp upload problems"
date: 2011-01-26
forum: Server Platforms
---

### Post by cinikal on 2011-01-26
Hello all.  
 
Ive looked up and down but i cant seem to find an answer to my question. Why cant i upload to my ftp site. I am running a lamp server and i installed proftp. i created users and groups. i tested my server and its working fine. but now when im working on dreamweaver to connect to my ftp... It connects fine i can download my files from the site but when i edit them and try to "put" them back. i get an error:
 
index.html - error occurred - An FTP error occurred - cannot put index.html.  Access denied.  The file may not exist, or there could be a permission problem.   Make sure you have proper authorization on the server and the server is properly configured.
File activity incomplete. 1 file(s) or folder(s) were not completed.
Files with errors: 1
index.html
Finished: 1/26/2011 6:20 PM
 
 i think everything was setup properly. 
as for permissions problem ow can i change that. 
also im using webmin. can i do this from webmin?
Is there supposed to be a port open on the firewall for uploads or does it use the standard 21 port
any and all help would be appreciated because everything went smooth until this.

---

### Post by gordintoronto on 2011-01-26
Is your site in /var/www? Can you move it to home/www?

---

### Post by cinikal on 2011-01-27
Thank you so much for trying o help gordintoronto but i figured out my problem. It was all about chown. once i did this to my directory it worked perfecly. 
 
Apparently you need to do this to give that user rights or something to that effect. I'm still learning:
 
*sudo chown -R username:group /var/www *
 
that solved the problem and now i can upload.
 
Thank you to "bmathis" here on ubuntu forums for that post. 
Here is the link to that post:
 
[http://ubuntuforums.org/showthread.php?t=519428](http://ubuntuforums.org/showthread.php?t=519428)
 
:popcorn:

---

