---
title: "Apache : Permission questions"
date: 2012-06-07
forum: Server Platforms
---

### Post by Houmie on 2012-06-07
Hi,

I have edited ```
sudo vim /etc/apache2/sites-available/default-ssl
``` and added the following entry:

```
WSGIScriptAlias /hg /var/www/scripts/hgweb.wsgi
        <Directory /var/www/scripts>
                Order allow,deny
                Allow from all
                AuthType Digest
                AuthName "Mercurial repositories"
                AuthDigestProvider file
                AuthUserFile /home/ubuntu/hg/users
                Require valid-user
        </Directory>  
``` 

the idea is if I visit [https://mySite.com/hg](https://mySite.com/hg)  the /var/www/scripts/hgweb.wsgi script will be executed.


The documentation sayd: 
> Make sure the Web server (such as Apache) is configured and can execute the script.

I have done this and it works but I am not sure if its the right way and I haven't exposed too much:

```
sudo chown -R **www-data**:www-data /var/www/scripts
```

So I wonder should I have used rather the username of the server (not root), which is ubuntu. What is the difference?

```
sudo chown -R **ubuntu**:www-data /var/www/scripts
```

Thank you,
Houman

---

### Post by sandyd on 2012-06-07
> **Houmie said:**
> Hi,

I have edited ```
sudo vim /etc/apache2/sites-available/default-ssl
``` and added the following entry:

```
WSGIScriptAlias /hg /var/www/scripts/hgweb.wsgi
        <Directory /var/www/scripts>
                Order allow,deny
                Allow from all
                AuthType Digest
                AuthName "Mercurial repositories"
                AuthDigestProvider file
                AuthUserFile /home/ubuntu/hg/users
                Require valid-user
        </Directory>  
``` 

the idea is if I visit [https://mySite.com/hg](https://mySite.com/hg)  the /var/www/scripts/hgweb.wsgi script will be executed.


The documentation sayd: 


I have done this and it works but I am not sure if its the right way and I haven't exposed too much:

```
sudo chown -R **www-data**:www-data /var/www/scripts
```

So I wonder should I have used rather the username of the server (not root), which is ubuntu. What is the difference?

```
sudo chown -R **ubuntu**:www-data /var/www/scripts
```

Thank you,
Houman

The difference is that the Apache Webserver runs under its own username and group. Just like you cannot write to other username's files, Apache cannot access/execute/write files that do not belong to her.

---

### Post by Houmie on 2012-06-07
I see. So the top approach is then correct?

---

### Post by sandyd on 2012-06-10
> **Houmie said:**
> I see. So the top approach is then correct?

yes.

---

