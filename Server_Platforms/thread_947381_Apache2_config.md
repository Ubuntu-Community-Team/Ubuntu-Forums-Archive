---
title: "Apache2 config"
date: 2008-10-14
forum: Server Platforms
---

### Post by sipickles on 2008-10-14
Hi,

I am a server noob, but its going fairly well.

I've set up apache to use my own php site by modifying /etc/apache2/sites-enabled/000-default

However I have a problem:

How can I specify other folders on the server to be accessible? even subfolders of the document root are Forbidden. Eg:

[http://mysite.com](http://mysite.com) - accesses mysite.com/index.html
[http://mysite.com/downloads/test.php](http://mysite.com/downloads/test.php) - Forbidden

thanks

Si

---

### Post by comandrei on 2008-10-14
Check the filsystem permissions. They must be at least readable for www-data

---

### Post by shredder12 on 2008-10-14
Even i am a noob in this field..but i have successfully ran apache on my laptop..
I don't have much idea what exactly the following script means but this is what i hve in my config file..
so i think you should check it with yours..
```
 <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On
        </Directory>

```
/var/www is my default..[http://localhost/](http://localhost/) directory and all the sub-directories in it are accessible..
so may be this script could help..
and yes as comandrei says the files and sub directories in the /var/www/ folder should be at least readable..

---

### Post by sipickles on 2008-10-14
Thanks comandrei, indeed it was a pemissions thing again.

I'd added the files remotely via ftp. Is there a way I can make apache have permission to use new files by default, rather than setting the file permissions on new files by hand?

---

### Post by cdenley on 2008-10-14
> **sipickles said:**
> Thanks comandrei, indeed it was a pemissions thing again.

I'd added the files remotely via ftp. Is there a way I can make apache have permission to use new files by default, rather than setting the file permissions on new files by hand?

What ftp server are you using?

---

### Post by sipickles on 2008-10-15
vsftpd

---

### Post by cdenley on 2008-10-15
You probably want to add options like this in your vsftpd config
```

local_umask=0022
file_open_mode=0755

```

---

