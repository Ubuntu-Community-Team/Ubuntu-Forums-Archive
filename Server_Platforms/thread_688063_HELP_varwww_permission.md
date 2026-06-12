---
title: "HELP: /var/www permission"
date: 2008-02-05
forum: Server Platforms
---

### Post by cjtjamandra on 2008-02-05
I have a website (apache2) and iam uploading files to it, iam getting a permission denied error everytime i try to upload so i have set my /var/www floder to chmod 777 to allow uploading and iam not getting the error anymore. my problem is that i think setting chmod 777 means allowing everyone to modify that folder and its contents and its a risk in security if iam right...

is there any solution or other security option that i can set so that my web pages are the only one that can access and upload to my folder.. thx in advance...

---

### Post by soulresin on 2008-02-05
> **cjtjamandra said:**
> I have a website (apache2) and iam uploading files to it, iam getting a permission denied error everytime i try to upload so i have set my /var/www floder to chmod 777 to allow uploading and iam not getting the error anymore. my problem is that i think setting chmod 777 means allowing everyone to modify that folder and its contents and its a risk in security if iam right...

is there any solution or other security option that i can set so that my web pages are the only one that can access and upload to my folder.. thx in advance...

Hi.  777 permissions are world writable.  Not really recommended.

What I recommend is running your site in a virtual host with the document root set to some arbitrary home folder.  Then use the id of the user that owns the home folder to ftp in and upload files.

---

### Post by cjtjamandra on 2008-02-05
Thx for the suggestion. Can i have virtual host even if i dont have a DNS server? Can you show me a tutorial on accomplishing this? Thx.

---

