---
title: "Setting aliases with apache2 ?"
date: 2007-05-02
forum: Server Platforms
---

### Post by punkdanne on 2007-05-02
Hi ! 

Today i set up my first apache-server, and i want to set "aliases", where apache should look for files. How should i do this in ubuntu ?

---

### Post by TennTux on 2007-05-02
The quick answer is to edit the */etc/apache2/apache2.conf* and near the bottom of the file add an entry similar to the following.

```
Alias /virtualname/ "/home/me/html/realdirectory/"
<Directory "/home/me/html/realdirectory/">
    Options Indexes
    AllowOverride None
    Order allow,deny
</Directory>
```

You will want to change the *virtualname* and */home/me/html/realdirectory/* entries as required. Also check out the Apache documentation for Alias, ScriptAlias and Options.

Good Luck.

---

### Post by punkdanne on 2007-05-03
Thx for your answer, but my roomie helped me solve this by just doing a softlink (im still a newbie in linux :P) in var/www.

---

