---
title: "Apache Document Root point to cgi file"
date: 2008-04-24
forum: Server Platforms
---

### Post by Dr Small on 2008-04-24
I am trying to setup a VirtualHost to point to the sqwebmail cgi file, so when I access mail.domain.com, it takes me directly to the webmail, or cgi script.

Anyone know how to do this?

I have in my VirtualHost container, right now:
```
#Mail.mycroftserver.homelinux.org
<VirtualHost *:80>
        ServerAdmin drsmall@mycroftserver.homelinux.org
        DocumentRoot cgi-bin/sqwebmail
        ServerName mail.mycroftserver.homelinux.org
</VirtualHost>

```

I have a symbolic link from /opt/lampp/cgi-bin/sqwebmail to /usr/lib/cgi-bin/sqwebmail and the permission on the latter are:
```
-rwxr-xr-x 1 root root 7432 2007-02-22 22:48 /usr/lib/cgi-bin/sqwebmail
```

Yet, when I access it in the browser (mail.domain.com), it says:
> Forbidden
You don't have permission to access / on this server.

Can anyone tell me where I have made a mistake?

Dr Small

---

### Post by geertn on 2008-04-24
Try specifying the full path to your documentroot.

Furthermore, you have to enable execcgi if it's not already enabled:

<Directory /opt/lampp/cgi-bin/>
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
</Directory>

<Directory /usr/lib/cgi-bin>
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
</Directory>

If it still doesn't work check your /var/log/apache2/error.log

---

### Post by Dr Small on 2008-04-24
Trying what you said, produced this:
```
[error] [client ] File does not exist: /opt/lampp/cgi-bin/sqwebmail/
``` 

The reason the file does not exist, is because the DocumentRoot is apparently trying to read it as a directory.

So, I have been playing around with the settings, trying different things, and came up with this:
```

<Directory "/opt/lampp/cgi-bin">
    AllowOverride None
    Options ExecCGI -MultiViews   
    Order allow,deny
    Allow from all 
</Directory> 
    
    
    
<Directory "/usr/lib/cgi-bin"> 
    AllowOverride None
    Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
</Directory>

```

And then I get this error:
```
[error] [client ] Symbolic link not allowed or link target not accessible: /opt/lampp/cgi-bin/sqwebmail
```

---

### Post by Dr Small on 2008-04-24
Problem Solved.
And here is how I solved it:

In /opt/lampp/cgi-bin/ I created a new directory called "sqwebmail" and moved my Symbolic Link into this directory and called the file index.cgi

Now, in my httpd.conf file, I wrote:
```
<Directory "/opt/lampp/cgi-bin/sqwebmail/">
    AllowOverride None
    Options ExecCGI -MultiViews FollowSymLinks
    Order allow,deny
    Allow from all 
    DirectoryIndex index.cgi 
</Directory>
```

And here was my VirtualHost:
```
#Mail.mycroftserver.homelinux.org
<VirtualHost *:80>
        ServerAdmin drsmall@mycroftserver.homelinux.org
        DocumentRoot /opt/lampp/cgi-bin/sqwebmail
        ServerName mail.mycroftserver.homelinux.org
</VirtualHost>

```

Thank-you for you help. It gave me ideas, and then I fooled with it until I got it complete :)

Dr Small

---

