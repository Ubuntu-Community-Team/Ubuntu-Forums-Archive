---
title: "Setup Subversion with Apache2 on Ubuntu"
date: 2006-11-06
forum: Server Platforms
---

### Post by satimis on 2006-11-06
Hi folks,

Ubuntu-6.06-LAMP-server-amd64

I followed following guide;
"Setup Subversion with Apache2 on Ubuntu"
[http://www.jessejcollins.com/blog/index.php?/archives/32-How-To-Setup-Subversion-with-Apache2-on-Ubuntu.html](http://www.jessejcollins.com/blog/index.php?/archives/32-How-To-Setup-Subversion-with-Apache2-on-Ubuntu.html)
to setup Subversion.

Encountered following problems.


1)
To restart Apache2

$ sudo /etc/init.d/apache2 restart```

* Forcing reload of apache 2.0 web server...     
[Mon Nov 06 11:50:49 2006] [crit] Apache is running a threaded MPM, 
but your PHP Module is not compiled to be threadsafe.  
You need to recompile PHP.
Pre-configuration failed                                           [fail]

```


2)
point 8) Now let's create a project........

$ svn import /home/bigbambo/myproject [http://localhost/svn/projectname](http://localhost/svn/projectname) \
> -m "creating repository" --username bigbambo --password bigbambo```

svn: PROPFIND request failed on '/svn/projectname'
svn: PROPFIND of '/svn/projectname': could not connect to server (http://localhost)

```


Could you please shed me some light where to check.  What name will be more appropriate to replace "myproject"

TIA


B.R.
satimis

---

