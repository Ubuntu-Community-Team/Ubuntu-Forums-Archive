---
title: "using apache to host shared windows directories"
date: 2005-12-11
forum: Server Platforms
---

### Post by bursto22 on 2005-12-11
I would like to make an alieas file with apache where it refrences a shared winodws drive using samba(which works fine already by itself). Does anyone know if this is possible and what i can put into my alias files?

---

### Post by Koybe on 2005-12-12
I'm using this to share some file. I made a link at the DocumentRoot, then just add a location. There is many ways of doing it with Apache.

```
ln -s /mnt/myshare /var/www/share
<Location /share>
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
    Allow from 192.168.1.0/24
</Location>
```

That's it. I didn't made an alias... just come into this directory. It won't appear online for people who can't have access.

---

### Post by bursto22 on 2005-12-12
so im able to mount drives but i dont understand how to get them into mnt or how to access a file location that is somehwere within "/" apposed to a virtual x server access point with a crap path

---

### Post by LordHunter317 on 2005-12-12
[QUOTE=Koybe]That's it. I didn't made an alias... just come into this directory. It won't appear online for people who can't have access.[/QUOTE]Using Alias and <Directory> is generally superior to a symlink+anything.

[quote=bursto22]
so im able to mount drives but i dont understand how to get them into mnt or how to access a file location that is somehwere within "/" apposed to a virtual x server access point with a crap path[/quote]I'm confused.  There's two questions here, but neither are well formed enough to provide any help.

What are you trying to mount?  And how do you have it mounted now?

---

### Post by bursto22 on 2005-12-12
Typically an alias file looks something like this
 
```
Alias /jams /var/

<Directory /var/>
    Options Indexes FollowSymLinks
    AllowOverride All
    Order allow,deny
    Allow from all
</Directory>
```
I would use this file in order to let others view my var files (this particular alias is just an example; not what i am trying to do).
I would like to know if it is possible to Put a windows shared drive in the place of ```
/var/
``` 
(the path location) of the alias file. Something like 

```
Alias /jams /smb://drifter/NDAS%20(G)/

<Directory /smb://drifter/NDAS%20(G)>
    Options Indexes FollowSymLinks
    AllowOverride All
    Order allow,deny
    Allow from all
</Directory>
```

Cannot be used and this is the problem
Thanks and sorry for the ambiguity.

---

