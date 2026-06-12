---
title: "Apache2 and Mod-Perl"
date: 2005-10-17
forum: Server Platforms
---

### Post by Meerkat on 2005-10-17
Hello all!

I'm quite new to Ubuntu, but thus far I'm liking it... except for how difficult it seems to be to install apache2 with mod_perl.

I installed libapach2-mod-perl2 via the package manager, and apache was working after that, but when I tried to get a perl script, it tries to download instead of being displayed,

After reading the forums here I added to following to the apache2.conf file:

AddHandler cgi-handler .pl

# If the perl module is installed, this will be enabled.
<IfModule mod_perl.c>
  <Location /var/www>
    SetHandler perl-script
    PerlHandler Apache::Registry
    Options +ExecCGI
  </Location>
</IfModule>

<Files ~ "\.pl$">
  SetHandler perl-script
  PerlHandler ModPerl::Registry
  Options +ExecCGI
</Files>

and still I have the same problem. I've seen that many out there have had the same problem. Has anyone out there solved it? Does anyone have any suggestions?

Thanks

---

### Post by herrpoon on 2005-10-18
Hi there!  I did have problems installing and getting to work the perl mod, there was a point where I had the same problems as you, and the only thing I can think of is that either you haven't installed it properly (unlikey if done through synaptic) or that you haven't restarted apache.  I can't remember 100% but you need to be placing your scripts in the cgi-bin (usr/lib/cgi-bin) unless you have edited your apache2.conf to allow them to exectue outside there of course.  This probably isn't it but also make sure that you've set the permissions correctly so your scripts will execute, i.e. 755.

---

### Post by Meerkat on 2005-10-18
Thanks for your reply. 

Permissions are correct, and Apache had been reloaded and restarted after the apache2.conf file was edited. 

As far as the cgi-bin goes, does:

<IfModule mod_perl.c>
<Location /var/www>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>

tell it to execute scripts from anywhere in /var/www ?

Thanks

---

### Post by LordHunter317 on 2005-10-18
Is the module actually being loaded in listed in /etc/apache2/mods-enabled?

---

### Post by Meerkat on 2005-10-18
I believe so:


marilyn@felix:~$ ls -al /etc/apache2/mods-enabled/
total 8
drwxr-xr-x  2 root root 4096 2005-10-17 18:35 .
drwxr-xr-x  8 root root 4096 2005-10-17 15:40 ..
lrwxrwxrwx  1 root root   37 2005-10-17 18:35 cgid.conf -> /etc/apache2/mods-available/cgid.conf
lrwxrwxrwx  1 root root   37 2005-10-17 18:35 cgid.load -> /etc/apache2/mods-available/cgid.load
lrwxrwxrwx  1 root root   37 2005-10-17 18:35 perl.conf -> /etc/apache2/mods-available/perl.conf
lrwxrwxrwx  1 root root   37 2005-10-17 18:35 perl.load -> /etc/apache2/mods-available/perl.load
lrwxrwxrwx  1 root root   40 2005-10-17 15:40 userdir.conf -> /etc/apache2/mods-available/userdir.conf
lrwxrwxrwx  1 root root   40 2005-10-17 15:40 userdir.load -> /etc/apache2/mods-available/userdir.load

with perl.conf, and perl.load being there... I'm assuming that it is loaded. And when I was playing around I got an internal server error, which displayed the version of apache and mod_perl that I am running.

Am I missing something else here?

---

### Post by Meerkat on 2005-10-19
Hello... I'm still having problems with this.. but now it's a different problem... I'm hoping that this means progress :P

I've changed my apache2.conf file to have:

# If the perl module is installed, this will be enabled.
<IfModule mod_perl.c>
<IfModule mod_alias.c>
Alias /perl/ /var/www/perl/
</IfModule>
<Location /perl>
SetHandler perl-script
PerlHandler Apache::Registry
Options +ExecCGI
</Location>
</IfModule>

<Files ~ "\.pl$">
Options +ExecCGI
</Files>

and I added +ExecCGI to the options line in /sites-enabled/000-default

and now I'm getting the error:

[Wed Oct 19 13:06:50 2005] [notice] Apache/2.0.54 (Ubuntu) mod_perl/2.0.1 Perl/v5.8.7 configured -- resuming normal operations
[Wed Oct 19 13:08:03 2005] [error] [client 207.216.243.73] failed to resolve handler `Apache::Registry': Can't locate Apache/Registry.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at (eval 2) line 3.\n
[Wed Oct 19 13:08:03 2005] [error] [client 207.216.243.73] File does not exist: /var/www/favicon.ico

when I try to run: /var/www/perl/test.pl

Has anyone encounted this? Any suggestions?

Thanks

---

### Post by pksings on 2005-10-20
Doesn't +ExecCGI turn it off?

I thought the correct syntax is just plain ExecCGI

---

### Post by Meerkat on 2005-10-20
I'm not sure which is the correct syntax... I've tried both now, and they both have the same effect... still not working.

---

### Post by i_am_socket on 2005-10-20
I was having the same problem, but I fixed it (just this morning actually)

Here's the directory section of /sites-available/default

Alias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin/">
     AllowOverride None
     Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
     AddHandler cgi-script .pl
     Order allow,deny
     allow from all
</Directory>

I also have
AddHandler cgi-script .cgi .pl
in apache2.conf

Hope this helps.

---

### Post by Meerkat on 2005-10-20
I'm not sure if that's actually using mod-perl... or if that's just cgi... can you run perl modules with that?

---

### Post by i_am_socket on 2005-10-20
I'm running the YaBB 2.0 bulletin board on it just fine, so maybe?

Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1 mod_perl/2.0.1 Perl/v5.8.7 Server at 192.9.200.163 Port 80

mod_perl's in there, and so's Perl.... can't hurt to have both right?  It works...

---

### Post by kzimmerm on 2005-11-09
[QUOTE=i_am_socket]I was having the same problem, but I fixed it (just this morning actually)

Here's the directory section of /sites-available/default

Alias /cgi-bin/ /var/www/cgi-bin/
<Directory "/var/www/cgi-bin/">
     AllowOverride None
     Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
     AddHandler cgi-script .pl
     Order allow,deny
     allow from all
</Directory>

I also have
AddHandler cgi-script .cgi .pl
in apache2.conf

Hope this helps.[/QUOTE]


The AddHandler is what fixed my version of Apache.  It took a bit of time to locate all of the issues to be resolved.  At least now I have everything working.    IF one was going to use PHP as a cgi-script would it need to be placed at the end of the AddHandler?

Thanks.
Kurt

---

### Post by Flannel on 2005-12-19
that's not using mod_perl, that's simply using the cgi handler.

To use mod perl, the only thing you need to do is (in your site file apache2/sites-enabled) include this:
```
	<Files ~ "\.(pl|cgi)$">
		SetHandler perl-script
		PerlResponseHandler ModPerl::PerlRun
		Options +ExecCGI
		PerlSendHeader On
	</Files>
```
You can remove everything else you've added.

This will allow .pl or .cgi programs (that are +x) to be run in any of your site directories.  If you want to further narrow it down, you are free to do so (<Directory> tags, etc).

---

### Post by hqmq on 2008-07-07
Using:
```
<Files ~ "\.(pl|cgi)$">
	SetHandler perl-script
	PerlResponseHandler ModPerl::PerlRun
	Options +ExecCGI
	PerlSendHeader On
</Files>
```

Will still only use part of the power of ModPerl -- if you want to see real speed increases try changing the PerlResponseHandler to ModPerl::Registry.

My benchmarks showed that I could run a sample script 12.8 times/sec with normal CGI, 82 times/sec with ModPerl::PerlRun and 533+ times/sec with ModPerl::Registry.

---

