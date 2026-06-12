---
title: "[SOLVED] Apache2 ExecCGI directory directive"
date: 2008-03-06
forum: Server Platforms
---

### Post by slafochmed on 2008-03-06
I have a strange problem concerning the ExecCGI directive in the apache2.conf.

I have only one directory directive which looks like:

```
<Directory "/var/www/test">
    Options FollowSymLinks ExecCGI Indexes 
    AllowOverride All
</Directory>
```

My *.cgi files in directory test and in its subdirectories are working.

But, when I change the directory line just to

```
<Directory "/var/www">
    Options FollowSymLinks ExecCGI Indexes 
    AllowOverride All
</Directory>
```

it just simply does not work anymore. No cgi script in test or below. The only thing I could think of is a .htaccess denial in www but there is no file there (I looked with mc and it shows hidden files). I have been looking to solve this problem for hours but I still have no clue. I hope someone can help me out.

I did not forget to restart apache2, and the error log says that Execcgi is off in test.

---

### Post by Bliepo32 on 2008-03-06
Could it be that you have another <Directory "/var/www/test">? Because it might be you accidently have it two times. The first one could then overide the second.

---

### Post by slafochmed on 2008-03-06
I checked that, but there is no second directory entry for /var or /var/www. But your suggestion gave me another idea. Perhaps I was running apache several times? But I checked that, too. It is only running once but uses 6 process IDs.

---

### Post by MJN on 2008-03-07
Can you quote the exact error message? Presumably CGI files in /var/www/ execute okay? If not, then try setting the appropriate execute flag for the /var/www folder.
 
Mathew

---

### Post by slafochmed on 2008-03-07
```
Options ExecCGI is off in this directory: /var/www/hello.cgi
```

This is the error entry I get from apache2 error log.

My directory directive was set like this, and restart of apache2:

```
# To use CGI scripts outside /cgi-bin/:
#
AddHandler cgi-script .cgi

<Directory "/var/www">
      Options ExecCGI Indexes FollowSymLinks MultiViews
      AllowOverride None
      Order allow,deny
      allow from all

</Directory>

```

The same cgi is working when the path is "/var/www/somefolder". I only do changes in the apache2.conf. Is there another possibility to do changes like a .htaccess file in www?

---

### Post by MJN on 2008-03-07
Ensure you don't have a <Directory "/var/www"> statement in /etc/apache2/sites-available/default - this will effectively override what you've set in apache2.conf (which is read earlier).

Mathew

---

### Post by slafochmed on 2008-03-07
Yeyeyeyeyeeeeeehhhhhh!!! That's it! \\:D/\\:D/\\:D/\\:D/
Great! You are my apache2 King, Mathew. Thanks alot! \\:D/

Since /var/www was my document root the
```
Options ExecCGI
``` was not entered there.

Ah, my weekend is saved, hehehehehe.

---

### Post by MJN on 2008-03-07
Excellent!

---

