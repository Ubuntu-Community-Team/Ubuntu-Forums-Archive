---
title: "apache 2.2 and mod_perl"
date: 2008-10-30
forum: Server Platforms
---

### Post by rbblue8 on 2008-10-30
hey all,

im trying to install apache with mod_perl from source and im getting an error when trying to start apache.

the error is 
Cannot load /usr/local/modules/mod_perl.so into server: /usr/local/modules/mod_perl.so: undefined symbol: boot_DynaLoader

when i configured mod_perl like
 perl Makefile.PL MP_APXS=/usr/local/httpd-2.2.10/bin/apxs

that completed as it should with no errors but did give me these messages
```
Writing Makefile for mod_perl2
Note (probably harmless): No library found for -lperl
Note (probably harmless): No library found for -lperl
[warning] mod_perl dso library will be built as mod_perl.so
[warning] You'll need to add the following to httpd.conf:
[warning]
[warning]   LoadModule perl_module modules/mod_perl.so
[warning]
[warning] depending on your build, mod_perl might not live in
[warning] the modules/ directory.

[warning] Check the results of
[warning]
[warning]   $ /usr/local/bin/apxs -q LIBEXECDIR
[warning]
[warning] and adjust the LoadModule directive accordingly.
```


any idea what could be wrong here?

---

### Post by alienprdkt on 2008-10-30
well its not from source but this is what I used to get perl_mod going...
[http://ge.ubuntuforums.com/showthread.php?t=16578](http://ge.ubuntuforums.com/showthread.php?t=16578)

---

### Post by alienprdkt on 2008-10-30
> **alienprdkt said:**
> well its not from source but this is what I used to get perl_mod going...
[http://ge.ubuntuforums.com/showthread.php?t=16578](http://ge.ubuntuforums.com/showthread.php?t=16578)
scratch that just checked link... here is a better one [http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html)

---

### Post by rbblue8 on 2008-10-30
i installed Apache from source, i would hate to install the required files for mod_perl2 (which includes Apache) just to solve this issue...

---

### Post by alienprdkt on 2008-10-30
> **rbblue8 said:**
> 

that completed as it should with no errors but did give me these messages
```
Writing Makefile for mod_perl2
Note (probably harmless): No library found for -lperl
Note (probably harmless): No library found for -lperl
[warning] mod_perl dso library will be built as mod_perl.so
[warning] You'll need to add the following to httpd.conf:
[warning]
[warning]   LoadModule perl_module modules/mod_perl.so
[warning]
[warning] depending on your build, mod_perl might not live in
[warning] the modules/ directory.

[warning] Check the results of
[warning]
[warning]   $ /usr/local/bin/apxs -q LIBEXECDIR
[warning]
[warning] and adjust the LoadModule directive accordingly.
```
any idea what could be wrong here?

actually now that I looked closer theres nothing wrong with it.. says you need to modify your httpd.conf manually.. sorry.. 

**Configure a cgi-bin directory**
 You need to create a cgi-bin directory using the following command
 sudo mkdir /home/www/cgi-bin
 Configuring Apache to allow CGI program execution is pretty easy. Create a directory to be used for CGI programs and add the following to the site configuration file (again between the <VirtualHost> tags).


within your /etc/apache2/httpd.conf file

 [INDENT]ScriptAlias /cgi-bin/ /home/www/cgi-bin/
 <Directory /home/www/cgi-bin/>
Options ExecCGI
AddHandler cgi-script cgi pl
</Directory>
[/INDENT] The first line creates an alias that points to the directory in which CGI scripts are stored. The final line tells Apache that only files that end with the *.cgi and *.pl extensions should be considered CGI programs and executed.
 **Test your Perl Program**
 cd /home/www/cgi-bin
 sudo nano perltest.pl
 Copy and paste the following section save and exit the file.
 [INDENT]###Start###
 #!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
[print]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html#") "Hello there!<br />\nJust testing .<br />\n";
 for ($i=0; $i<10; $i++)
{
print $i."<br />";
}
 ###End###
[/INDENT] make sure you change permissions on it
 sudo chmod a+x perltest.pl
 Now open your web browser open [http://yourserverip/cgi-bin/perltest.pl.It](http://yourserverip/cgi-bin/perltest.pl.It) should be working.

---

### Post by rbblue8 on 2008-10-31
please read the first post.

i get an error when trying to start apache.  apache does not even start b/c of the the error that's in the first post.

I have followed the directions and added the modules/mod_perl.so into the httpd.conf directory.

---

### Post by alienprdkt on 2008-10-31
> **rbblue8 said:**
> please read the first post.

i get an error when trying to start apache.  apache does not even start b/c of the the error that's in the first post.

I have followed the directions and added the modules/mod_perl.so into the httpd.conf directory.
so did it install or not?
if not try 
#sudo aptitude install libapache2-mod-perl2

---

### Post by rbblue8 on 2008-10-31
yes it installs with no errors.

but when i try and start apache it get
Cannot load /usr/local/modules/mod_perl.so into server: /usr/local/modules/mod_perl.so: undefined symbol: boot_DynaLoader

---

### Post by alienprdkt on 2008-10-31
sp apache installed no perl mod...

try this
sudo aptitude install libapache2-mod-perl2

---

### Post by rbblue8 on 2008-10-31
loading that module works fine. 

this is odd that the compiled one does not load though.

---

### Post by alienprdkt on 2008-10-31
well we should be able to get this to work now, if that module just loaded:D

actually now that I looked closer theres nothing wrong with it.. says you need to modify your httpd.conf manually.. sorry.. 

**Configure a cgi-bin directory**
 You need to create a cgi-bin directory using the following command
 sudo mkdir /home/www/cgi-bin
Configuring Apache to allow CGI program execution is pretty easy. Create a directory to be used for CGI programs and add the following to the site configuration file (again between the <VirtualHost> tags).


within your /etc/apache2/httpd.conf file
[INDENT]ScriptAlias /cgi-bin/ /home/www/cgi-bin/
 <Directory /home/www/cgi-bin/>
Options ExecCGI
AddHandler cgi-script cgi pl
</Directory>
[/INDENT]The first line creates an alias that points to the directory in which CGI scripts are stored. The final line tells Apache that only files that end with the *.cgi and *.pl extensions should be considered CGI programs and executed.
 **Test your Perl Program**
 cd /home/www/cgi-bin
 sudo nano perltest.pl
 Copy and paste the following section save and exit the file.[INDENT]###Start###
 #!/usr/bin/perl -w
print "Content-type: text/html\r\n\r\n";
[print]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html#") "Hello there!<br />\nJust testing .<br />\n";
 for ($i=0; $i<10; $i++)
{
print $i."<br />";
}
 ###End###
[/INDENT]make sure you change permissions on it
 sudo chmod a+x perltest.pl
 Now open your web browser open [http://yourserverip/cgi-bin/perltest.pl.It](http://yourserverip/cgi-bin/perltest.pl.It) should be working.

---

### Post by khawasli on 2009-02-12
Hi,
I had the same problem and I just resolved it by installing libperl-dev and libperl-5.10 try it out

---

