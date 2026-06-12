---
title: "Wrong client denied error log entries"
date: 2016-03-07
forum: Server Platforms
---

### Post by andreas53 on 2016-03-07
Hi, I have a strange problem with my Apache error log. A log entry is written on each request, like this:
```
[Mon Mar 07 11:43:00.454450 2016] [access_compat:error] [pid 10486] [client 91.126.16.158:60566] AH01797: client denied by server configuration: /var/www/epc/cgi-bin/perlinfo.pl
```
However, I can correctly access all content!

I've configured my site as follows:
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName intern.epc.local
    
    DocumentRoot /var/www/epc/
    <Directory /var/www/epc/>
        Options -Indexes +FollowSymLinks +MultiViews
        AllowOverride All
        
        AuthType Basic
        AuthName intranet
        AuthUserFile /var/www/epc/.htpasswd
        Require valid-user
        
        Order allow,deny
        Allow from 127.0.0.1     #Server
        Allow from 93.54.126.55  #Server (external)
        Allow from 85.112.14.120 #External IP of companies' network -> those users do not need to login
        Satisfy any
        
    </Directory>

    ScriptAlias /cgi-bin/ /var/www/epc/cgi-bin/
    <Directory "/var/www/epc/cgi-bin">
        AllowOverride All
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        #Order allow,deny
        #Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error-epc.log
    LogLevel warn
    CustomLog /var/log/apache2/access-epc.log combined

</VirtualHost>

```

Ubuntu Server 14.04 LTS
Any idea whats going wrong?
Thanks in advance!

---

### Post by blueridgedog on 2016-03-07
Since you have AllowOverride on, do you have a .htaccess file in /var/www/epc/cgi-bin/?  If not, start with turning off override.

---

### Post by andreas53 on 2016-03-07
Good point, I missed that. Thanks!
However, this does not solve the problem with the error log...

---

### Post by SeijiSensei on 2016-03-07
I don't see a matching entry for 91.126.16.158, the IP reported in the error log.

---

### Post by andreas53 on 2016-03-13
Sure, this is the Basic Auth client

---

### Post by SeijiSensei on 2016-03-13
I have no idea what your response means or if it is a reply to mine.  The log entry refers to an IP address that is not contained in any of the Allow directives in your configuration file, so it should be blocked.

---

### Post by andreas53 on 2016-03-19
The client is correctly authenticated using the basic auth entry. Since "Satisfy any" is added, the other directives should be ignored an no auth error should be written.
Am I wrong with this assumption?
Again, everything works fine, except these wrong entries in the error log.

---

