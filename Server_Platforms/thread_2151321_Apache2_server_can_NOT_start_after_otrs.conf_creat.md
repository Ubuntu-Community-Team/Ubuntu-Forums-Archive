---
title: "Apache2 server can NOT start after otrs.conf created during OTRS installation"
date: 2013-06-04
forum: Server Platforms
---

### Post by yfdsy on 2013-06-04
Hi Experts:
I am recently installing OTRS(otrs-3.2.7) on my ubuntu server(Ubuntu Server 12.04.2 LTS), by mainly referring to following guides:
[http://vladon.com/installing-otrs-on-ubuntu-server-12-10-x64/](http://vladon.com/installing-otrs-on-ubuntu-server-12-10-x64/)
[http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4)](http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4))

But I met a issue at stage "Web server configuration":
```

cp /opt/otrs/scripts/apache2-httpd.include.conf /etc/apache2/conf.d/otrs.conf service apache2 restart
```After otrs.conf copy done, the apache2 can NOT start any more.
It will prompt below error message:
```
 * Restarting web server apache2... waiting Action 'start' failed.
The Apache error log may have more information.                                            [fail]
```
And apache2 error log as below:
```
[Wed Jun 05 00:08:37 2013] [error] Insecure dependency in require while running with -T switch at /opt/otrs//Kernel/Config/Defaults.pm line 34.
BEGIN failed--compilation aborted at /opt/otrs//Kernel/Config/Defaults.pm line 34.
Compilation failed in require at /opt/otrs//Kernel/Config.pm line 103.
BEGIN failed--compilation aborted at /opt/otrs//Kernel/Config.pm line 103.
Compilation failed in require at /opt/otrs/scripts/apache2-perl-startup.pl line 68.
BEGIN failed--compilation aborted at /opt/otrs/scripts/apache2-perl-startup.pl line 68.
Compilation failed in require at (eval 2) line 1.
[Wed Jun 05 00:08:37 2013] [error] Can't load Perl file: /opt/otrs/scripts/apache2-perl-startup.pl for server localhost:0, exiting...


```

If I delete my coped otrs.conf from /etc/apache2/conf.d, then apache2 can restart correctly.

Can any one give some advice on this issue? 

Waiting for your input and thanks in advance!

Best Regards
Davis

---

### Post by yfdsy on 2013-06-05
Is there anyone who install OTRS on Ubuntu Server 12.04.2 LTS successfully?
If yes, which version OTRS is fine?

Thanks
Davis

---

### Post by Lars Noodén on 2013-06-05
The package  [otrs2](http://packages.ubuntu.com/precise/otrs2) is in the repository.  Maybe it would be easier to start with that.  In general it is best to work with packages from the repository when possible.

---

### Post by WWielbert on 2013-08-07
[http://ownlinuxnotes.wordpress.com/2012/01/22/install-and-configure-otrs-in-ubuntu/](http://ownlinuxnotes.wordpress.com/2012/01/22/install-and-configure-otrs-in-ubuntu/)

These are steps i followed today and otrs works fine for me


wget [ftp://ftp.otrs.org/pub/otrs/otrs-3.2.9.tar.gz](ftp://ftp.otrs.org/pub/otrs/otrs-3.2.9.tar.gz)


cp otrs-3.2.9.tar.gz /opt/


cd /opt


tar -xzvf otrs-3.2.9.tar.gz


ln -s /opt/otrs-3.0.3 /opt/otrs


useradd otrs
passwd otrs
usermod -d /opt/otrs otrs


usermod -g www-data otrs


sudo apt-get install mysql-server apache2


cd /opt/otrs


sudo ./bin/otrs.CheckModules.pl | grep Not


sudo aptitude search libdatetime-perl libnet-dns-perl libwp-useragent-determined-perl


sudo aptitude install libdatetime-perl libnet-dns-perl libwp-useragent-determined-perl


sudo bin/otrs.SetPermissions.pl --otrs-user=otrs &#8211;otrs-group=otrs --web-user=www-data --web-group=www-data /opt/otrs


sudo ln -s /opt/otrs/scripts/apache2-httpd.include.conf /etc/apache2/sites-available/otrs.conf


sudo ls /etc/apache2/sites-available/


sudo /etc/init.d/apache2 reload


sudo a2ensite otrs.conf


sudo /etc/init.d/apache2 reload


[http://local/otrs/installer.pl](http://local/otrs/installer.pl)


It did not work at this moment. Hence, i followed the remaining from [http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4)](http://wiki.otterhub.org/index.php?title=Installation_on_Ubuntu_Lucid_Lynx_(10.4))


cd /opt/otrs/kernel
cp config.pm.dist config.pm
cp config/genericagent.pm.dist config/genericagent.pm


Modify the ENVVARS file


Add # in front of 


#export Apache_run_user=www-data
#export Apache_run_group=www-data


Below that type :


#export Apache_run_user=otrs
#export Apache_run_group=otrs


Restart Apache and you should be able to complete the registration

---

