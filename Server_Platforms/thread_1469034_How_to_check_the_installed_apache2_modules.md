---
title: "How to check the installed apache2 modules"
date: 2010-05-01
forum: Server Platforms
---

### Post by RavinderVirk on 2010-05-01
I am trying change the MaxClients parameter for apache2 on ubuntu. I looked in apache2.conf and there are two instances where MaxClients is mentioned.

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

1. How do I know which mpm (multi-processing module) module is currently installed on apache2 so that I can modify the appropriate MaxClient parameter. I believe I installed the apache2 in a pretty standard mode but I don't know what module does apache2 use by default. 
I read apache2 documentation which says to use "-l" from command line to find installed modules  but I keep getting the following error

 /etc/init.d/apache2 -l
 *** Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}**

2. Even if I modify the the MaxClient parameter in both the modules, Do I need to recompile the apache2 or Restarting the apache2 should be sufficient?

There is another directory under apache2 called "mods-enabled", However it does not mention any of the mpm modules. This is the directory listing

 ls -l /etc/apache2/mods-enabled/
total 0
lrwxrwxrwx 1 root root 28 Sep 28  2009 alias.conf -> ../mods-available/alias.conf
lrwxrwxrwx 1 root root 28 Sep 28  2009 alias.load -> ../mods-available/alias.load
lrwxrwxrwx 1 root root 33 Sep 28  2009 auth_basic.load -> ../mods-available/auth_basic.load
lrwxrwxrwx 1 root root 33 Sep 28  2009 authn_file.load -> ../mods-available/authn_file.load
lrwxrwxrwx 1 root root 36 Sep 28  2009 authz_default.load -> ../mods-available/authz_default.load
lrwxrwxrwx 1 root root 38 Sep 28  2009 authz_groupfile.load -> ../mods-available/authz_groupfile.load
lrwxrwxrwx 1 root root 33 Sep 28  2009 authz_host.load -> ../mods-available/authz_host.load
lrwxrwxrwx 1 root root 33 Sep 28  2009 authz_user.load -> ../mods-available/authz_user.load
lrwxrwxrwx 1 root root 32 Sep 28  2009 autoindex.conf -> ../mods-available/autoindex.conf
lrwxrwxrwx 1 root root 32 Sep 28  2009 autoindex.load -> ../mods-available/autoindex.load
lrwxrwxrwx 1 root root 26 Sep 28  2009 cgi.load -> ../mods-available/cgi.load
lrwxrwxrwx 1 root root 30 Sep 28  2009 deflate.conf -> ../mods-available/deflate.conf
lrwxrwxrwx 1 root root 30 Sep 28  2009 deflate.load -> ../mods-available/deflate.load
lrwxrwxrwx 1 root root 26 Sep 28  2009 dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root 26 Sep 28  2009 dir.load -> ../mods-available/dir.load
lrwxrwxrwx 1 root root 26 Sep 28  2009 env.load -> ../mods-available/env.load
lrwxrwxrwx 1 root root 27 Sep 28  2009 mime.conf -> ../mods-available/mime.conf
lrwxrwxrwx 1 root root 27 Sep 28  2009 mime.load -> ../mods-available/mime.load
lrwxrwxrwx 1 root root 34 Sep 28  2009 negotiation.conf -> ../mods-available/negotiation.conf
lrwxrwxrwx 1 root root 34 Sep 28  2009 negotiation.load -> ../mods-available/negotiation.load
lrwxrwxrwx 1 root root 30 Sep 28  2009 rewrite.load -> ../mods-available/rewrite.load
lrwxrwxrwx 1 root root 31 Sep 28  2009 setenvif.conf -> ../mods-available/setenvif.conf
lrwxrwxrwx 1 root root 31 Sep 28  2009 setenvif.load -> ../mods-available/setenvif.load
lrwxrwxrwx 1 root root 29 Sep 28  2009 status.conf -> ../mods-available/status.conf
lrwxrwxrwx 1 root root 29 Sep 28  2009 status.load -> ../mods-available/status.load

I would really appreciate any help in this topic.

Thanks

---

### Post by Ryan Dwyer on 2010-05-01
ls /etc/apache2/mods-enabled/mpm*

Although on my machine I don't have either of them installed. You can install them using apt-get install apache2-mpm-prefork apache2-mpm-worker.

---

### Post by gombadi on 2010-05-02
Try this from the command line

```

[root@server]# dpkg -l | grep mpm
ii  apache2-mpm-worker                    2.2.8-1ubuntu0.15            High speed threaded model for Apache HTTPD

```

It will show you which package you have installed.

---

