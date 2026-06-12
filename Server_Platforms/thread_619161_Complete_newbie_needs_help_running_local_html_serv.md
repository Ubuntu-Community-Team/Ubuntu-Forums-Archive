---
title: "Complete newbie needs help running local html server"
date: 2007-11-21
forum: Server Platforms
---

### Post by Jimnast on 2007-11-21
I just installed apache2.2.4 on ubuntu gutsy, so that I can test some cgi scripts written in python and html. 

On the computers at my university we had to create a public_html folder and a cgi-bin folder within that, in our home directory, and accessed the scripts via the address [http://localhost/~username/cgi-bin/scriptname.cgi](http://localhost/~username/cgi-bin/scriptname.cgi)

I followed the installation guide on this site for gutsy:
[http://articles.slicehost.com/apache]("http://articles.slicehost.com/apache")

I tried to understand the virtual host configuration guides but they are for creating websites and that's not what I want to do so I don't know how to configure apache to just run a localserver like on the computers at my university. Please help, thank you.

---

### Post by Stemp on 2007-11-21
After installing apache, you'll have to modify your /etc/apache2/apache2.conf file and add :

```
UserDir public_html 
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec ExecCGI
</Directory>
```

then 

```
sudo /etc/init.d/apache2 force-reload 
```

---

### Post by Jimnast on 2007-11-21
I semi solved the problem another way, not exactly desired, but I will test this as well, thank you.

---

### Post by Stemp on 2007-11-21
More infos in the Apache Documentation :
[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)

There's even a part about cgi directory ;)

---

### Post by [censored] on 2007-11-25
> **Stemp said:**
> After installing apache, you'll have to modify your /etc/apache2/apache2.conf file and add :

```
UserDir public_html 
UserDir disabled root

<Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options Indexes SymLinksIfOwnerMatch IncludesNoExec ExecCGI
</Directory>
```

then 

```
sudo /etc/init.d/apache2 force-reload 
```

Tried this exactly.

Apache crashed with this error:

Syntax error on line 297 of /etc/apache2/apache2.conf:
Invalid command 'UserDir', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

---

### Post by Stemp on 2007-11-26
You have to enable userdir module in apache2 :

```
sudo a2enmod userdir
```

then restart apache2 :

```
sudo /etc/init.d/apache2 force-reload
```

---

### Post by [censored] on 2007-11-27
Cheers Stemp. That worked.

---

### Post by Stemp on 2007-11-27
Great ! Champagne !! :popcorn:

---

### Post by golond on 2007-12-18
Stemp, I just wanted to add my "Thank you".  Instructions worked great, and you provided an excellent link to detailed information on Apache.  You're a life saver.

---

### Post by Stemp on 2007-12-20
> **golond said:**
> Stemp, I just wanted to add my "Thank you".  Instructions worked great, and you provided an excellent link to detailed information on Apache.  You're a life saver.

You're welcome. Next time you'll help me (or someone else) ;)

---

