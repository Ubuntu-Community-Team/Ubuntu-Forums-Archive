---
title: "apache and access level"
date: 2009-04-27
forum: Server Platforms
---

### Post by cacavolante on 2009-04-27
Hi everyone

I have an web-form accessed by a customer of mine. Its just a php site that lists the contents of a folder (pdfs) and has a delete button next to every file  so it can be deleted. It is protected as following

AuthType Basic
AuthName "User Authentication"
AuthUserFile /etc/apache2/passes
AuthGroupFile /etc/apache2/groupcarr
Require valid-user

My problem is that customer now wants half of the users that allready have access to be able to delete files but the other wont be able to delete. 

I dont want to rewrite the code to use mysql for access level. Is there a way to be done via htaccess or file system level access. I want to use the same form but delete button will fail for some users.

Thanks in advanced

---

### Post by cacavolante on 2009-04-27
Ok thanks everyone for looking in to my post. Problems solved via a <File> section in .htaccess with diferent group/pass files.

Thanks again everyone who took a look in my post (and think about just a little)

---

