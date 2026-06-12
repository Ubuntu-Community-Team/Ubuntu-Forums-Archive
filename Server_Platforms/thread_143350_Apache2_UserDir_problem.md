---
title: "Apache2 UserDir problem"
date: 2006-03-12
forum: Server Platforms
---

### Post by sapo on 2006-03-12
Hi, i used apache2 and had some rules to the public_html user dirs before, but now it seens that i have to use a userdir module, i installed it and tried to enable, but i m getting this error:

```
Invalid command 'UserDir', perhaps mis-spelled or defined by a module not included in the server configuration
```

Anyone could help me? i cant config this stuff and i really need the user dirs :(

---

### Post by claes on 2006-03-13
This is how I usualy add this function to apache:
httpd.conf
<IfModule mod_userdir.c>
    UserDir public_html
</IfModule>
 
And then load the module with:
LoadModule userdir_module /usr/lib/apache/1.3/mod_userdir.so

As you might see this is with apache1.3 but the syntax should be the same with apache 2. Looks like you don't load the module on the error message.

Claes

---

### Post by aimaz on 2006-03-22
I was just suffering from this problem after a fresh install of apache2 with dapper so here's how I enabled user directories.

1) Edited [FONT="Courier New"]/etc/apache2/apache2.conf[/FONT] and uncommented the lines related to UserDir so it looks like this.

[FONT="Courier New"][COLOR="Navy"]#UserDir is now a module[/COLOR]
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>[/FONT]

2) I added linked the UserDir module into apache2's mods-enabled directory. Like this.

[FONT="Courier New"]**:~$** cd /etc/apache2/mods-enabled/
**:/etc/apache2/mods-enabled$** sudo ln -s ../mods-available/userdir.* .
Password: [entered my password]
**:/etc/apache2/mods-enabled$** ls
cgid.conf  cgid.load  userdir.conf  userdir.load[/FONT]

3) I reloaded the apache2 config.

[FONT="Courier New"]**:~$** sudo /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                                                              [ ok ][/FONT]

4) Then you just need to make your [FONT="Courier New"]~/public_html[/FONT] directory and make sure the permissions are ok.

[FONT="Courier New"]**:~$** mkdir ~/public_html/
**:~$** chmod o+rx ~/public_html[/FONT]

Now just go to [http://localhost/~user/](http://localhost/~user/) (replace "user" with your username) in your web browser and you should see an empty directory listing.

---

### Post by agvozden on 2008-04-21
thx

---

