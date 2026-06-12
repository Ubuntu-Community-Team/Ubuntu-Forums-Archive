---
title: "not able to start apache2 in ubuntu server"
date: 2012-02-17
forum: Server Platforms
---

### Post by mahi_nix on 2012-02-17
Hi Friends,
 
I have a Ubuntu server installed on my environment i have installed apache2, php5, mysql and perl in my server i am going to migrate one website which is already hosted on one live server. i have done all things but while i am restarting the apache2 server it shows me below error message.
 
```

* Restarting web server apache2 Syntax error on line 9 of /etc/apache2/sites-enabled/dnsadmin:
Can't locate Catalyst/Plugin/Cache/FastMmap.pm in @INC (@INC contains: /srv/www/dnsadmin/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/apache2). at /usr/lib/perl5/Class/MOP.pm line 116\n\tClass::MOP::load_first_existing_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/lib/perl5/Class/MOP.pm line 121\n\tClass::MOP::load_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/share/perl5/Catalyst.pm line 2813\n\tCatalyst::setup_plugins('DNS', 'ARRAY(0x7fd1a2d1afa0)') called at /usr/share/perl5/Catalyst.pm line 1079\n\tCatalyst::setup('DNS') called at /srv/www/dnsadmin/lib/DNS.pm line 45\n\trequire DNS.pm called at /etc/apache2/sites-enabled/dnsadmin line 10\n\tApache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9::BEGIN() called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval {...} called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval 'package Apache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9;\n#line 9 /etc/apache2/sites-enabled/dnsadmin\nuse lib \\'/srv/www/dnsadmin/lib\\';\nuse DNS;\n\n;' called at /srv/www/dnsadmin/lib/DNS.pm line 0\nCompilation failed in require at /etc/apache2/sites-enabled/dnsadmin line 10.\nBEGIN failed--compilation aborted\t(in cleanup) Can't locate Catalyst/Plugin/Cache/FastMmap.pm in @INC (@INC contains: /srv/www/dnsadmin/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/apache2). at /usr/lib/perl5/Class/MOP.pm line 116\n\tClass::MOP::load_first_existing_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/lib/perl5/Class/MOP.pm line 121\n\tClass::MOP::load_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/share/perl5/Catalyst.pm line 2813\n\tCatalyst::setup_plugins('DNS', 'ARRAY(0x7fd1a2d1afa0)') called at /usr/share/perl5/Catalyst.pm line 1079\n\tCatalyst::setup('DNS') called at /srv/www/dnsadmin/lib/DNS.pm line 45\n\trequire DNS.pm called at /etc/apache2/sites-enabled/dnsadmin line 10\n\tApache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9::BEGIN() called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval {...} called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval 'package Apache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9;\n#line 9 /etc/apache2/sites-enabled/dnsadmin\nuse lib \\'/srv/www/dnsadmin/lib\\';\nuse DNS;\n\n;' called at /srv/www/dnsadmin/lib/DNS.pm line 0\nCompilation failed in require at /etc/apache2/sites-enabled/dnsadmin line 10.\nBEGIN failed--compilation aborted at /etc/apache2/sites-enabled/dnsadmin line 10.\n 

```
 
I dont know what to do. i have done googling but no results. please help me to sorted out the issue.
 
Thank you,

---

### Post by Lars Noodén on 2012-02-17
It helps if you wrap the output in [ code ] [/code] tags so that the lines don't get wrapped so.  Slow down and read the output carefully.

To begin with it looks like you have a syntax error in your configuration file "dnsadmin" in line 9.  

You can test your configuration like this
```

sudo /usr/sbin/apache2ctl configtest

```

---

### Post by mahi_nix on 2012-02-17
HI Lars Noodén,
 
I run the command "/usr/sbin/apache2ctl configtest" on my ubuntu and it shows me the same error message. please check below.
 
```
Syntax error on line 9 of /etc/apache2/sites-enabled/dnsadmin:
Can't locate Catalyst/Plugin/Cache/FastMmap.pm in @INC (@INC contains: /srv/www/dnsadmin/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/apache2). at /usr/lib/perl5/Class/MOP.pm line 116\n\tClass::MOP::load_first_existing_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/lib/perl5/Class/MOP.pm line 121\n\tClass::MOP::load_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/share/perl5/Catalyst.pm line 2813\n\tCatalyst::setup_plugins('DNS', 'ARRAY(0x7f867811a7d0)') called at /usr/share/perl5/Catalyst.pm line 1079\n\tCatalyst::setup('DNS') called at /srv/www/dnsadmin/lib/DNS.pm line 45\n\trequire DNS.pm called at /etc/apache2/sites-enabled/dnsadmin line 10\n\tApache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9::BEGIN() called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval {...} called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval 'package Apache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9;\n#line 9 /etc/apache2/sites-enabled/dnsadmin\nuse lib [\\'/srv/www/dnsadmin/lib\\';\nuse]("file://\\'/srv/www/dnsadmin/lib\\';\nuse") DNS;\n\n;' called at /srv/www/dnsadmin/lib/DNS.pm line 0\nCompilation failed in require at /etc/apache2/sites-enabled/dnsadmin line 10.\nBEGIN failed--compilation aborted\t(in cleanup) Can't locate Catalyst/Plugin/Cache/FastMmap.pm in @INC (@INC contains: /srv/www/dnsadmin/lib /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/apache2). at /usr/lib/perl5/Class/MOP.pm line 116\n\tClass::MOP::load_first_existing_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/lib/perl5/Class/MOP.pm line 121\n\tClass::MOP::load_class('Catalyst::Plugin::Cache::FastMmap') called at /usr/share/perl5/Catalyst.pm line 2813\n\tCatalyst::setup_plugins('DNS', 'ARRAY(0x7f867811a7d0)') called at /usr/share/perl5/Catalyst.pm line 1079\n\tCatalyst::setup('DNS') called at /srv/www/dnsadmin/lib/DNS.pm line 45\n\trequire DNS.pm called at /etc/apache2/sites-enabled/dnsadmin line 10\n\tApache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9::BEGIN() called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval {...} called at /srv/www/dnsadmin/lib/DNS.pm line 0\n\teval 'package Apache2::ReadConfig::etc::apache2::sites_enabled::dnsadmin::line_9;\n#line 9 /etc/apache2/sites-enabled/dnsadmin\nuse lib [\\'/srv/www/dnsadmin/lib\\';\nuse]("file://\\'/srv/www/dnsadmin/lib\\';\nuse") DNS;\n\n;' called at /srv/www/dnsadmin/lib/DNS.pm line 0\nCompilation failed in require at /etc/apache2/sites-enabled/dnsadmin line 10.\nBEGIN failed--compilation aborted at /etc/apache2/sites-enabled/dnsadmin line 10.\n

```

---

### Post by Lars Noodén on 2012-02-17
Yes, it will tell you your errors. You then need to read through them and address them one by one.  For example, you see that you are probably missing the perl module package libcache-fastmmap-perl  Install that and go on to the next error.

---

### Post by mahi_nix on 2012-02-17
Hi Lars Noodén,
 
The below package is already installed on the server.
 
>  
libcache-fastmmap-perl

 
i have checked the @INC path in the server which is as below.
```
@INC:
    /etc/perl
    /usr/local/lib/perl/5.10.1       ---- not available
    /usr/local/share/perl/5.10.1  ---- not available
    /usr/lib/perl5
    /usr/share/perl5
    /usr/lib/perl/5.10
    /usr/share/perl/5.10
    /usr/local/lib/site_perl           ---- not available

```
 
if i am disabling that perticular site that the apache2 starts.
 
Plese find the configuration of linu 8,9 & 10 below.
```

<Perl>
use lib '/srv/www/dnsadmin/lib';
use DNS;
</Perl>

```
 
Please suggest me if you can able to find the issue.

---

