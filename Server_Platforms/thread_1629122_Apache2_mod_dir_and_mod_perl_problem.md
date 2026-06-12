---
title: "Apache2 mod_dir and mod_perl problem"
date: 2010-11-23
forum: Server Platforms
---

### Post by sgardne on 2010-11-23
I'm trying to make my server recognize that index.cgi and index.pl should be loaded automatically with mod_dir. It looks like mod_dir is already configured to work that way, here's the config in /etc/apache2/mods-enabled/dir.conf:

```
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>
```

The problem is when I enable perl execution in the directory, it no longer works. If I don't enable perl execution, I can go to [http://localhost/hostman/](http://localhost/hostman/) and get a download prompt for index.cgi. If I go there after enabling perl execution, it gives me a 404 until I explicitly go to [http://localhost/hostman/index.cgi](http://localhost/hostman/index.cgi). Here's my httpd.conf:

```
Alias /hostman/ /var/www/perl/hostman/
<Location /hostman/>
        SetHandler perl-script
        PerlResponseHandler ModPerl::Registry
        PerlOptions +ParseHeaders
        Options +ExecCGI
        Order allow,deny
        Allow from all
</Location>
```

When I try to access the page, I get the following error in my log:

> Attempt to serve directory: /var/www/perl/hostman/

Can anyone tell me what I'm doing wrong?

Thanks,
Scott

---

### Post by sgardne on 2010-11-24
No one? I'm booting up a CentOS VM right now to see if it's distro specific. I think I read one time during the many hours of investigation on this that this was a Debian issue, but I can't find the link now.

---

### Post by sgardne on 2010-11-25
The following config is the way to make this work:
```
Alias /hostman/ /home/sgardne/httpd/hostman/
<Directory /home/sgardne/httpd/hostman/>
    AddHandler perl-script .pl .cgi
    PerlResponseHandler ModPerl::Registry
    PerlOptions +ParseHeaders
    Options +ExecCGI
    Order allow,deny
    Allow from all
</Directory>
```

---

### Post by martis on 2012-06-19
Today just made my first steps into "mod_perl".

Because most of the examples I saw suggested to use:
```
SetHandler perl-script
```
rather than:
```
AddHandler perl-script .pl .cgi
```

I was stuck for several hours unless found this post witch saved my day!

By the way, while I was lurking [http://perl.apache.org/docs](http://perl.apache.org/docs) on how to make **index.pl **act as index file I found a notice saying that is possible but not advisable for main HTTP root directory where regular and/or static html files may be served because it's a way to troubles.

---

