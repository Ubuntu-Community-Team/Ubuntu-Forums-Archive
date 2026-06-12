---
title: "apache2 cgi issue"
date: 2009-04-11
forum: Server Platforms
---

### Post by test006 on 2009-04-11
Hi,
I am running ubuntu server 8.04. I am trying run a cgi script as part of mrtg software. 
I have installed the router2.cgi script in the following directory:
/usr/lib/cgi-bin
i have created a symbolic link to /var/www/cgi-bin
ln -s /usr/lib/cgi-bin /var/www/cgi-bin

Now when i try to use the web browser to go the following URL:
[http://192.168.1.1/cgi-bin/router2.cgi](http://192.168.1.1/cgi-bin/router2.cgi) i get following error message:
```

Forbidden
You don't have permission to access /cgi-bin/routers2.cgi on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch Server at 192.168.1.1 Port 80

```
Can some please let me know how i can fix this problem...I cannot run any cgi scripts at the moment, i.e. i get same error message....
I am running apache2 web browser. Please help....i need this working urgently.....spent over a week trying different options but still cannot get this to work....

thanks in advance...

---

### Post by volkswagner on 2009-04-11
What are the permissions of the file?

```
ls -alt /var/www/cgi-bin
```

---

### Post by test006 on 2009-04-11
> **volkswagner said:**
> What are the permissions of the file?

```
ls -alt /var/www/cgi-bin
```

Hi here is the information:
```

root@:/var/www# ls -alt /var/www/cgi-bin/
total 8
drwxrwxrwx 2 root root 4096 2009-04-12 01:05 .
lrwxrwxrwx 1 root root   17 2009-04-12 01:05 cgi-bin -> /usr/lib/cgi-bin/
drwxr-xr-x 6 root root 4096 2009-04-12 00:56 ..

```

```

root@:/var/www# ls -alt /usr/lib/cgi-bin/
total 432
-r-xr-xr-x  1 root root 332929 2009-04-12 01:36 routers2.cgi
drw-r--r--  2 root root   4096 2009-04-12 01:35 .
-rwxr-xr-x  1 root root  28284 2009-04-12 00:16 mrtg-rrd.cgi
drwxr-xr-x 64 root root  28672 2009-04-11 22:26 ..
-rwxr-xr-x  1 root root  39699 2001-12-12 22:27 14all-1.0.cgi

```

As you can see i have tried three different cgi scripts and all of them with same error message. 
I did change the owner/group to www-data on all the files and directories and still did not work....my apache2 is running as www-data.

Thanks

---

### Post by apel_2804 on 2009-04-11
I'm note shure if it is correct to only set a symlink.

Have a look in your /etc/apache2/sites-available/default file, there allready should be a directory index for cgi bin:

```
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
```

If not, add this lines and remove the symlink /var/www/cgi-bin/ because there allready exist an alias for cgi's.

And if you changed the config file, reload your apache:

```
/etc/init.d/apache2 restart
```

---

### Post by test006 on 2009-04-11
> **apel_2804 said:**
> I'm note shure if it is correct to only set a symlink.

Have a look in your /etc/apache2/sites-available/default file, there allready should be a directory index for cgi bin:

```
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
```

If not, add this lines and remove the symlink /var/www/cgi-bin/ because there allready exist an alias for cgi's.

And if you changed the config file, reload your apache:

```
/etc/init.d/apache2 restart
```

Hi, yes i have that already on my default file. This is what is configured:
```

 ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

```
So i have removed the symbolic link. The only thing i have now is /var/www/cgi-bin directory. This is empty directory now.
So when i try to go the following URL:
[http://192.168.1.1/cgi-bin/routers2.cgi](http://192.168.1.1/cgi-bin/routers2.cgi)
I still get 403 Forbidden message and You don't have permission to access /cgi-bin/routers2.cgi on this server.

Any thing else you suggest i should look into.....

Thanks

---

### Post by test006 on 2009-04-11
Hi,
Just to confirm i have configured lighttpd server to run on port 8000 and tried using lighttpd to work with cgi script an i get the same error message i.e. 403 Forbidden.
I am running lighttpd and apache2 on the same server....

So it seems some sort of permission issue....how do i fix this....

Thanks

---

### Post by apel_2804 on 2009-04-12
Hm...

I don't think it is an permission problem because have a look on my permissions:

```
thomas@vthomas:/usr/lib/cgi-bin$ ls -al
total 536
drwxr-xr-x  3 root   root    4096 Mar 28 20:49 .
drwxr-xr-x 34 root   root   12288 Apr 12 12:07 ..
drwxr-xr-x  6    500   500   4096 Mar 28 20:49 irc
-rwxr-xr-x  1 thomas users 520986 Dec 25 21:13 nph-proxy.cgi
```

And that works fine!

next steps:

- you have installed your scripts in /usr/lib/cgi-bin/ ?
- remove the directory /var/www/cgi-bin/
- enshure that there is no .htaccess file in your /usr/lib/cgi-bin/
- enshure that the whole path to your script is also readable /usr/lib/

---

### Post by test006 on 2009-04-12
> **apel_2804 said:**
> Hm...

I don't think it is an permission problem because have a look on my permissions:

```
thomas@vthomas:/usr/lib/cgi-bin$ ls -al
total 536
drwxr-xr-x  3 root   root    4096 Mar 28 20:49 .
drwxr-xr-x 34 root   root   12288 Apr 12 12:07 ..
drwxr-xr-x  6    500   500   4096 Mar 28 20:49 irc
-rwxr-xr-x  1 thomas users 520986 Dec 25 21:13 nph-proxy.cgi
```

And that works fine!

next steps:

- you have installed your scripts in /usr/lib/cgi-bin/ ?
- remove the directory /var/www/cgi-bin/
- enshure that there is no .htaccess file in your /usr/lib/cgi-bin/
- enshure that the whole path to your script is also readable /usr/lib/

> 
- you have installed your scripts in /usr/lib/cgi-bin/ ?

Yes
root@:/usr/lib/cgi-bin# ls -lha
total 432K
drw-r--r--  2 root root 4.0K 2009-04-12 01:35 .
drwxr-xr-x 64 root root  28K 2009-04-11 22:26 ..
-rwxr-xr-x  1 root root  39K 2001-12-12 22:27 14all-1.0.cgi
-rwxr-xr-x  1 root root  28K 2009-04-12 00:16 mrtg-rrd.cgi
-rwxrwxrwx  1 root root 326K 2009-04-12 01:36 routers2.cgi

> 
- remove the directory /var/www/cgi-bin/

O.K done.

> 
- enshure that there is no .htaccess file in your /usr/lib/cgi-bin/

The output of ls -lha does not show an .htaccess file in this directory...see above.

> 
- enshure that the whole path to your script is also readable /usr/lib/

Is this what you mean:
root@:/usr/lib# ls -lha | more
drw-r--r--  2 root root 4.0K 2009-04-12 01:35 cgi-bin

Now that i have deleted the /var/www/cgi-bin...How do i access my cgi scripts from a browser?

---

### Post by apel_2804 on 2009-04-13
your cgi scripts are available over [http://your.serv.er/cgi-bin/yourscript.cgi](http://your.serv.er/cgi-bin/yourscript.cgi) because you allready have a virtual site configured in your /etc/apache2/sites-available/default config file! The /cgi-bin/ allready points to -> /usr/lib/cgi-bin/.

---

### Post by test006 on 2009-04-13
> **apel_2804 said:**
> your cgi scripts are available over [http://your.serv.er/cgi-bin/yourscript.cgi](http://your.serv.er/cgi-bin/yourscript.cgi) because you allready have a virtual site configured in your /etc/apache2/sites-available/default config file! The /cgi-bin/ allready points to -> /usr/lib/cgi-bin/.
Hi,
Yes i have checked all this and i still get the same error message....
I am totally stuck and not been able to deploy any cgi based stuff....

---

