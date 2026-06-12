---
title: "Apache User's Directory"
date: 2005-02-28
forum: Server Platforms
---

### Post by charlie763 on 2005-02-28
I am running Ubuntu on my 12" Al Powerbook with apache installed and running. When I go to [http://127.0.0.1](http://127.0.0.1) I get shown the directory contents of Apache's root directory. When I go to [http://127.0.0.1/~](http://127.0.0.1/~)[User Name]/ I want Apache to properly handle the contents of /home/[User Name]/public_html/. I have tried to figure the apache2.conf file, but nothing seemes to be working. I also restarted the server each time I saved a change to apache2.conf. Does anyone know how I can go about fixing this. Much thanks...

---

### Post by charlie763 on 2005-02-28
Sorry about putting the post in the wrong catagory. Will you fix this, Mr. Moderator man?

---

### Post by jdonnell on 2005-02-28
You should see something like this in your apache2.conf
```

# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
#       AllowOverride FileInfo AuthConfig Limit
#       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
#</Directory>

```
Change it to this.
```

# UserDir is now a module
UserDir public_html
#UserDir disabled root

<Directory /home/*/public_html>
       AllowOverride FileInfo AuthConfig Limit
       Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

```
Now restart apache and all should be working. You may need to change the permissions of your home folder.

$ chmod 755 /home/username

---

### Post by charlie763 on 2005-03-01
Thanks, jdonnell. I replied in the other forum. I moved the discussion over to the server forum. Here's a link [http://www.ubuntuforums.org/showthread.php?p=81529#post81529](http://www.ubuntuforums.org/showthread.php?p=81529#post81529).

---

