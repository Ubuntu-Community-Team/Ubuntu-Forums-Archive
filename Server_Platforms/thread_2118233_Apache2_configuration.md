---
title: "Apache2 configuration"
date: 2013-02-20
forum: Server Platforms
---

### Post by mr.suchy on 2013-02-20
Hi,

I want to run apache2 on my xubuntu because I do website when I have time and this help me witch this process. I changed default directory from /var/www to my folder in apache2.conf. In official website I red about virtual host but I can't find httpd.conf where I must create this virtual server, virtual website. Is anyone can help me where is this file ?

the official site: [http://httpd.apache.org/docs/2.4/vhosts/name-based.html](http://httpd.apache.org/docs/2.4/vhosts/name-based.html)

Or maybe this section I must add to something another file ? Thanks for help!

---

### Post by Doug S on 2013-02-20
The file /etc/apache2/httpd.conf is either empty or, if your version of Ubuntu is recent enough, non-existent. It has been many versions ago since it was not used anymore, but still required for legacy reasons. As of 12.10 it isn't there anymore.
 
What you want to do is now handled in the /etc/apache2 subdirectores.
 
A good reference, specific to Ubuntu, is the [Ubuntu server guide]("https://help.ubuntu.com/12.10/serverguide/index.html"). (I prefer the [PDF]("https://help.ubuntu.com/12.10/serverguide/serverguide.pdf") version).
 
What I would do in your situation, is leave everything as per the default apache install and use my default directory public_html for my developement work. Of course, user directory use has to be enabled first:```
sudo a2enmod userdir
sudo service apache2 restart
```

---

### Post by mr.suchy on 2013-02-21
Thanks for help but I still have a problem with that.

My apache2.conf
```

#ServerRoot "/etc/apache2"
LockFile ${APACHE_LOCK_DIR}/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On

MaxKeepAliveRequests 100

KeepAliveTimeout 5

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>


<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>


<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType None


HostnameLookups Off

ErrorLog ${APACHE_LOG_DIR}/error.log

LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

Include ports.conf

%{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see the comments above for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

ServerName ubuntu

```My phpmyadmin.local in sites-available
```

<VirtualHost *:80>
        ServerAdmin webmaster@example.com
        ServerName  www.phpmyadmin.local
        ServerAlias phpmyadmin.local

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /home/mrsuchy/Dokumenty/public_html/phpmyadmin

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/mrsuchy/Dokumenty/public_html/phpmyadmin/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog /var/log/apache2/error.log        
</VirtualHost>

```My hosts
```

127.0.0.1    localhost
127.0.1.1    xubuntu-desktop
127.0.0.1    ubuntu
127.0.0.1    phpmyadmin.local
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```When I put ubuntu or phpmyadmin in web browser I see default apache web page I mean "It's works". What I did wrong ?

---

### Post by Doug S on 2013-02-21
I'm not an expert on the virtual hosts stuff, and hope another reader will help.
I wonder if /etc/apache2/sites-enabled/000-default is taking precedence and apache doesn't even get to your files. And/Or if your file got enabled with "sudo a2ensite phpmyadmin.local"

---

### Post by CharlesA on 2013-02-21
> **Doug S said:**
> I'm not an expert on the virtual hosts stuff, and hope another reader will help.
I wonder if /etc/apache2/sites-enabled/000-default is taking precedence and apache doesn't even get to your files. And/Or if your file got enabled with "sudo a2ensite phpmyadmin.local"

Could be.

@OP: You don't do virtualhosts in apache2.conf. You create them in /etc/apache2/sites-available and then enable them like Doug said, with a2ensite sitename.

---

### Post by mr.suchy on 2013-02-22
I dont know what I done but now eveything works fine. Still I have one problem. When I enter phpmyadmin.local the phpmyadmin is work but when I enter wordpress.local nothing happend. I dont know why..

---

### Post by lisati on 2013-02-22
> **CharlesA said:**
> Could be.

@OP: You don't do virtualhosts in apache2.conf. You create them in /etc/apache2/sites-available and then enable them like Doug said, with a2ensite sitename.

+1. Although it might not matter too much with small sites, when you get into hosting multiple sites and/or multiple subdomains, keeping things separate like this can help keep things tidy in your main .conf files.

---

### Post by CharlesA on 2013-02-22
> **mr.suchy said:**
> I dont know what I done but now eveything works fine. Still I have one problem. When I enter phpmyadmin.local the phpmyadmin is work but when I enter wordpress.local nothing happend. I dont know why..

No DNS entry maybe?

> **lisati said:**
> +1. Although it might not matter too much with small sites, when you get into hosting multiple sites and/or multiple subdomains, keeping things separate like this can help keep things tidy in your main .conf files.

True. I tend to create my virtualhosts like this:

```
/etc/apache2/sites-available/url.of.site
```

Helps me know what is what. :D

---

### Post by mr.suchy on 2013-02-22
Hmmm I add wordpress.local to /etc/hosts.

---

