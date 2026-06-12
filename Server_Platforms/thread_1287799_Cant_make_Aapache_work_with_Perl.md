---
title: "Cant make Aapache work with Perl"
date: 2009-10-10
forum: Server Platforms
---

### Post by CrAzYoNi on 2009-10-10
Hi all,

Introduction:

I'm using:
- Ubuntu Jaunty (9.04) 32 bit.
- Apache 2.2.11
- Perl 5.10.0

* I'm searching for distro updates everyday, so my system should be updated.

- I've got Apache to work for several months now without any problems (I'm running my web site which is based on PHP5.

- I've got Perl working for several months as well, I'm running some monitor scripts, based on Cron, to check my system status.
--------------------------------------------------------------------------

Now I wanted to run some Perl script on my Apache, I've wrote a simple Perl script, "hello world" kind, and name it "hello.pl".
I checked its syntax and it works.

I've installed: sudo apt-get install libapache2-mod-perl2
I've verified that Apache recognize the module: sudo apache2ctl -M

When trying to browse to that page I've got an error, below is the output as it shown in /var/log/apache2/error.log:

```

[Sat Oct 10 21:20:57 2009] [error] [client 127.0.0.1] failed to resolve handler `Apache::Registry': Can't locate loadable object for module Apache::Constants in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /var/www) at /usr/local/lib/perl/5.10.0/mod_perl.pm line 14\nCompilation failed in require at /usr/local/lib/perl/5.10.0/Apache.pm line 6.\nBEGIN failed--compilation aborted at /usr/local/lib/perl/5.10.0/Apache.pm line 6.\nCompilation failed in require at /usr/local/lib/perl/5.10.0/Apache/Registry.pm line 2.\nBEGIN failed--compilation aborted at /usr/local/lib/perl/5.10.0/Apache/Registry.pm line 2.\nCompilation failed in require at (eval 2) line 3.\n

```

Any ideas how can I solve this issue?

Thanks in advance.

Yours,
Yoni D.

---

### Post by superc0w on 2009-10-10
Hi!

Could you please post your apache configs?

Thanks

---

### Post by CrAzYoNi on 2009-10-10
Apache2 config:

> 
ServerSignature On
ServerName Server.Every1.Kicks-***.net
ServerRoot "/var/www"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>
DefaultType text/plain
HostnameLookups On
ErrorLog /var/log/apache2/error.log
LogLevel debug
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-agent}i\" %I %O" combined
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/


000-default:

> 
AddDefaultCharset UTF-8

ServerTokens ProductOnly
ServerSignature Off
ErrorDocument 404 "/404.php"
LogLevel debug
ErrorLog /var/log/apache2/error.log
CustomLog /var/log/apache2/access.log combined

<VirtualHost *:80>
	ServerAdmin [email]Yoni@Every1.Kicks-***.net[/email]
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	<Directory "/var/www/cgi-bin/">
		PerlHandler Apache::Registry
		AddHandler perl-script .pl
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>


Apache2ctl -M output:

> 
$ apache2ctl -M
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 perl_module (shared)
 php5_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK


---

### Post by wojox on 2009-10-10
Here I just posted this the other day: [http://ubuntuforums.org/showthread.php?t=1285019](http://ubuntuforums.org/showthread.php?t=1285019)

May help.

---

### Post by CrAzYoNi on 2009-10-10
Thanks Wojox!! your tut really solved the issue I was having!

---

