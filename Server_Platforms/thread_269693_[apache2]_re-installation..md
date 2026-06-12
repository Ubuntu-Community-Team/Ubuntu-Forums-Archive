---
title: "[apache2]: re-installation."
date: 2006-10-02
forum: Server Platforms
---

### Post by chlag on 2006-10-02
Hello,
I had installed, first, Ubuntu 6.06 LTS(and other packatages), by using 3DVDs those come with a magazine....I had installed apache2, php5, mysql-server, java.....whithout problem.
After a problem, I was obliged to formate all and to reinstall that OS......I have succesed to re-install it, but the problem now is that, I can not install apache2(by using both, synaptic and command line).
My question is: What kind of configuration must I do to re-install apache2?
Thanks in advence for the help.

---

### Post by az on 2006-10-02
> **chlag said:**
>  I can not install apache2(by using both, synaptic and command line).

What do you mean?  You cannot find the package. the package will not install or it installs but does not work?  Please be more specific.


> **chlag said:**
> 
My question is: What kind of configuration must I do to re-install apache2?
Thanks in advence for the help.


Other that enabling the repositories that contain the apache2 packages, you should not have to configure anything - apache2 does not conflict with anything on a default Ubuntu system.


See here about repositories.  You need the main repository enabled:
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

see also:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by chlag on 2006-10-03
Hello, 
In fact, apache2 is well installed(I've verified it), but the problem is when I do:
```
$sudo /etc/init.d/apache2 reload
```
I get the following message:
> *Reloading apache2.0 configuration....
apache2 : Could not determine the server's fully qualified domaine name, using 127.0.1.1 for ServerName
httpd not running, trying to start
( 98 )Address already in use : make_sock : could not bind to adresse [::]:80
no listening sockets available, shutting down
Unable to open logs                          [[COLOR="Red"]fail[/COLOR]]

What must I do in this case, to start apache2?
Thanks in advance for the help.

---

### Post by sonic2000gr on 2006-10-03
Actually it should read 127.0.0.1 and not 127.0.1.1

Please edit your /etc/hosts file and verify the following line exists:

```
127.0.0.1  localhost.localdomain localhost
```

The message from apache means it cannot bind to port 80. This is either because a) You mispelled 127.0.0.1 like noted above or b) There is another server type program listening on port 80 (unlikely). Please confirm the file /etc/apache2/ports.conf contains the following:

```
 Listen 80 
```

If you want apache to function on the server only and not serve pages anywhere on the local net or the internet, you may change it to:

```
 Listen 127.0.0.1:80 
``` 

otherwise just leave it as before.
You may also edit the /etc/apache2/apache2.conf file and add the line:

```
 ServerName localhost 
```

Also

---

### Post by chlag on 2006-10-04
apache/1.3.34 was installed with apache2 => so the problem.
I have desinstalled and rm totaly all about apache1.3.34 and then, in the ```
/etc/apache2/apache2.conf 
```
I have added the line:
> ServerName localhost
Then it(apache2) works now.
Thanks.

---

