---
title: "public_html permissions multiple users"
date: 2008-02-14
forum: Server Platforms
---

### Post by rendo on 2008-02-14
I have multiple users on my box.  Each user has their own home/user folder that has permissions set so only THEY can access and view the contents of their folder.  Now, when it comes to public_html though, it's blocked.  I want each user to be able to have anyone access their websites, but the only way I've found to do this is to allow access through their home directory, which is not only a security issue, but a privacy issue.  I've tried chmod 755 public_html, but it's still blocked.  

Basically, I'm trying to find a way so that their home folder is protected from non users access, but allow anyone who wants to access their website if they have one.  Much <3 for assistance.

---

### Post by Silby on 2008-02-14
If you setup the www server to use /home/username/public_html as its root folder per user, it should work with chmod 755 /home/username/public_html. You may want to use 711 to disable directory listings.

How are you trying to access the public web folders and what error are you getting ?

---

### Post by rendo on 2008-02-14
Permission denied to the site/folder/whatever you're trying to access

---

### Post by zaynhamdan on 2008-02-14
Sometimes when accessed the folder with no default file on it (ex: index.html or index.php), it will display permission denied page. Please try to create an index.html file on that folder.

---

