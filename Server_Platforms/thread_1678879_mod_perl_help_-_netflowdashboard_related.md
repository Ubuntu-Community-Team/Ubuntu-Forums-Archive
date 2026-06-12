---
title: "mod_perl help - netflowdashboard related"
date: 2011-01-31
forum: Server Platforms
---

### Post by iclebyte on 2011-01-31
Morning,

I'm desperately trying to get Netflowdashboard working properly [http://www.netflowdashboard.com]("http://www.netflowdashboard.com")

The bit I'm stuck on is creating an Apache 2 compliant vhost.

The website [http://trac.netflowdashboard.com/netflowdashboard/wiki/InstallNotes]("http://trac.netflowdashboard.com/netflowdashboard/wiki/InstallNotes") suggests the following vhost

```
<VirtualHost *:80>
    ServerName nfdb.localhost.com
    DocumentRoot /var/www/netflowdashboard/cgi
    PerlModule Apache::PerlRun
    <Location />
        SetHandler perl-script
        PerlHandler Apache::PerlRun
        PerlRequire /var/www/netflowdashboard/cgi/startup.pl
        Options ExecCGI
        PerlSendHeader On
        DirectoryIndex index.cgi
        Order deny,allow
        Allow from all
    </Location>
    <Location /images/>
        SetHandler default-handler
    </Location>
    <Location /css/>
        SetHandler default-handler
    </Location>
    <Location /js/>
        SetHandler default-handler
    </Location>
</VirtualHost>

```

However it produces this error under ubuntu 10.04 LTS 

```
Syntax error on line 8 of /etc/apache2/sites-enabled/nfdb:
PerlRequire directive not allowed in a <Location> block
   ...fail!

```

So I moved the PerlRequire outside of the initial location directive and apache would then start however, the application still won't run. I have obviously created an entry for nfdb.localhost.com in /etc/hosts and it's resolving correctly.

Any help with this would be great.

Thanks.

---

