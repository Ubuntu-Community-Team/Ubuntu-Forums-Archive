---
title: "Configure Subversion on Subdomain"
date: 2011-10-25
forum: Server Platforms
---

### Post by zowo on 2011-10-25
Hy yesterday i tried to setup a subversion on my vServer.

I've read several Tutorials and finally i've done the basic-configruation ... i hope so ;-)

Therefore i did the following tasks

- install libapache2-svn and subversion
- create a new Folder in /var/www/subdomain for my project
- created an and enabled a config file (default and SSL) for the project in etc/apache2/sites-available/
- enabmled a2enmod ssl
- also created the ssl-certificate
- created a repository in /var/local/subversion/subdomain
- added a user to subversion.passwd
- changed ownershiop of /var/www/subdomain and /var/local/subversion/subdomain to www-data

I'm not sure if everything went well, i'm new to ubuntu, but i tried my best :-)

Here are the site-files

etc/apache2/sites-available/svn.domain.com

```
    <virtualhost *:80>

      # Admin email, Server Name (domain name) and any aliases
      ServerAdmin hello@domain.com
      ServerName  svn.domain.com

      # Index file and Document Root (where the public files are located)
      DirectoryIndex index.html
      DocumentRoot /var/www/svn.domain.com/

        <Location /domain>
        DAV svn
        AuthType Basic
        AuthName "Repos"
        AuthUserFile /etc/apache2/subversion.passwd
        SVNPath /var/local/subversion/domain
        Require valid-user
        </Location>

        # Log-Files
        CustomLog /var/log/apache2/svn-access.log combined
        ErrorLog /var/log/apache2/svn-error.log

    </virtualhost>

```

etc/apache2/sites-available/svn.domain.com-ssl

```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin hello@domain.com
        ServerName svn.domain.com
        DocumentRoot /var/www/svn.domain.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/svn.domain.com/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on
        SSLCertificateFile    /etc/apache2/ssl/apache.pem

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

        # added by zowo 241011

        <Location /domain>
        DAV svn
        AuthType Basic
        AuthName "Repos"
        AuthUserFile /etc/apache2/subversion.passwd
        SVNPath /var/local/subversion/domain
        Require valid-user
        </Location>


</VirtualHost>
</IfModule>


```

The first problem is that i cannt connect to [http://svn.project.com](http://svn.project.com) via Browser

What could be the problem? Maybe the top-domain? For the top-domain i also have a config-file in the sites-available which is linked to /var/www/domain and which is available via Browser

Now i want also to connect to the repository via Netbeans, put this doesn't work i alwayse that an error message within Netbeans:

[[IMG]http://s14.directupload.net/images/111025/fqjlootd.jpg[/IMG]](http://www.directupload.net)

Can somebody give me a hint? I suppose there is a problem with the subdomain :-/

---

