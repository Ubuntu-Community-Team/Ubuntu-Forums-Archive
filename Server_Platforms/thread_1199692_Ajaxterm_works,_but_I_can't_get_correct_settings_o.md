---
title: "Ajaxterm works, but I can't get correct settings on apache2 :("
date: 2009-06-29
forum: Server Platforms
---

### Post by mewbie on 2009-06-29
**Thank you for your time and help! :D Please if you could look over my settings and see what's going wrong.. I've read so much and tried soooo many things for 1 month now.**   [FONT=&quot]I'm running: Linux Debian / apache2-mpm-prefork 2.2.9-10+lenny2 [/FONT][FONT=&quot]
Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 [/FONT]
  
  [FONT=&quot]In case you don't know what Ajaxterm is: [/FONT][FONT=&quot]http://antony.lesuisse.org/software/ajaxterm/[/FONT]
  
  [FONT=&quot]I'm sure the problem lies in the configs putting into apache2. As Ajaxterm works on [http://localhost:8022](http://localhost:8022) & I don’t get any errors when loading ajaxterm either. It also works if it reads from one vhost only.[/FONT]
  
  [FONT=&quot]The problem I am having if I make a new vhost file it will:[/FONT]
  [FONT=&quot]1) No matter what URL you enter it will show the AjaxTerm page/window [/FONT]
  [FONT=&quot]I'm sure this is because of this error:[/FONT][FONT=&quot] [warn] _default_ VirtualHost overlap on port 443, the first has precedence. < So it just ignores the other vhost settings.[/FONT]
  
  [FONT=&quot]If I add the configs to ssl file below existing configs[/FONT]
  [FONT=&quot]2) Ajaxterm won't work at all; if I go directly to it's path [/FONT][FONT=&quot]It produces a page with the top strip only of the ajaxterm window that says: Connection error status: 404[/FONT]
  
  [FONT=&quot][B]These are the steps I have done: 
**a2enmod proxy_http **[B]
apt-get install ajaxterm 
/etc/init.d/ajaxterm start[/B] 
It replied: Starting web based terminal: ajaxterm 
**pico /etc/ssh/ssh_config** 
//uncomment: PasswordAuthentication yes 
**cd / **[B]
mkdir /srv/ajaxterm 
cd /srv/ajaxterm 
htpasswd -cm /srv/ajaxterm/.htpasswd MyName 
typed in pass…[/B][/B][/FONT][B]
  
  **[FONT=&quot]1st: the method of making a new file[/FONT]**[/B][FONT=&quot](as per [http://wiki.kartbuilding.net/index.php/Ajaxterm](http://wiki.kartbuilding.net/index.php/Ajaxterm) ) (this makes 'entire' site ajaxterm only):[/FONT]
  [FONT=&quot]**[B]pico /etc/apache2/sites-available/ajaxterm**[/B]*<note this file doesn't exist*[/FONT]
  [FONT=&quot]*In case it matters also note 'my.site' is replacing my actual domain which is in that format of my'.'site'.'org as it's a free dyndns domain*[/FONT]
  
<VirtualHost *:80>
        ServerName ajaxterm.my.site.org
        Redirect 301 / [https://ajaxterm.my.site.org](https://ajaxterm.my.site.org)
        CustomLog /var/log/apache2/access.log combined
        ErrorLog /var/log/apache2/error.log
</VirtualHost>

<VirtualHost *:443>
        ServerName ajaxterm.my.site.org
        HostnameLookups Double
        CustomLog /var/log/apache2/access.log combined env=!dontlog
        SetEnvIf Request_URI "^/u" dontlog
        ErrorLog /var/log/apache2/error.log
        Loglevel warn
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        ProxyRequests Off
        <Proxy *>
                AuthUserFile /srv/ajaxterm/.htpasswd
                AuthName EnterPassword
                AuthType Basic
                require valid-user

                Order Deny,allow
                Allow from all
        </Proxy>
        ProxyPass / [http://localhost:8022/](http://localhost:8022/)
        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)
</VirtualHost>

  [FONT=&quot]Then I:[/FONT]
  [FONT=&quot]**[B]a2ensite ajaxterm**[/B][/FONT][B]
  **[FONT=&quot]/etc/init.d/apache2 reload [/FONT]**[/B]
  [FONT=&quot]reply I get is: Reloading web server config: apache2 [warn] _default_ VirtualHost overlap on port 443, the first has precedence[/FONT]
  [FONT=&quot]and in apache2 error logs:[/FONT]
  [FONT=&quot][warn] Init: SSL server IP/port conflict:ajaxterm.my.site.org:443 (/etc/apache2/sites-enabled/ajaxterm:8) vs. my.site.org:443 (/etc/apache2/sites-enabled/ssl:2)[/FONT]
  line 8 would be: <VirtualHost *:443>  [FONT=&quot]line 2 would be: <VirtualHost *:443>[/FONT]
  
  
  [FONT=&quot]**2nd method after removing the above, adding to my existing ssl file (this makes ajaxterm not work at all):**[/FONT][B]
  **[FONT=&quot]pico /etc/apache2/sites-enabled/ssl[/FONT]**[/B]
  [FONT=&quot]This is my entire file with configs for ajaxterm as the 2nd virtual host configs (as per [http://wiki.kartbuilding.net/index.php/Ajaxterm](http://wiki.kartbuilding.net/index.php/Ajaxterm) ):[/FONT]
  
  [FONT=&quot]NameVirtualHost *:443[/FONT]
  
  [FONT=&quot]<VirtualHost *:443>[/FONT]
  [FONT=&quot]      ServerAdmin webmaster@localhost[/FONT]
  [FONT=&quot]        ServerName my.site.org[/FONT]
  
  [FONT=&quot]      DocumentRoot /var/www/[/FONT]
  [FONT=&quot]        SSLEngine On[/FONT]
  [FONT=&quot]        SSLCertificateFile /etc/apache2/ssl/apache.pem[/FONT]
  
  [FONT=&quot]      <Directory />[/FONT]
  [FONT=&quot]            Options None[/FONT]
  [FONT=&quot]            AllowOverride None[/FONT]
  [FONT=&quot]      </Directory>[/FONT]
  [FONT=&quot]      <Directory /var/www/>[/FONT]
  [FONT=&quot]            Options -Indexes FollowSymLinks MultiViews[/FONT]
  [FONT=&quot]            AllowOverride AuthConfig[/FONT]
  [FONT=&quot]            Order allow,deny[/FONT]
  [FONT=&quot]            allow from all[/FONT]
  [FONT=&quot]                AuthUserFile /etc/apache2/.htpasswd[/FONT]
  [FONT=&quot]                AuthGroupFile /dev/null[/FONT]
  [FONT=&quot]                AuthName  "Authorization Required"[/FONT]
  [FONT=&quot]                AuthType Basic[/FONT]
  [FONT=&quot]                require user myname[/FONT]
  [FONT=&quot]      </Directory>[/FONT]
  
  [FONT=&quot]      ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/[/FONT]
  [FONT=&quot]      <Directory "/usr/lib/cgi-bin">[/FONT]
  [FONT=&quot]            AllowOverride None[/FONT]
  [FONT=&quot]            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch[/FONT]
  [FONT=&quot]            Order allow,deny[/FONT]
  [FONT=&quot]            Allow from all[/FONT]
  [FONT=&quot]      </Directory>[/FONT]
  
  [FONT=&quot]      ErrorLog /var/log/apache2/error.log[/FONT]
  
  [FONT=&quot]      # Possible values include: debug, info, notice, warn, error, crit,[/FONT]
  [FONT=&quot]      # alert, emerg.[/FONT]
  [FONT=&quot]      LogLevel warn[/FONT]
  
  [FONT=&quot]      CustomLog /var/log/apache2/access.log combined[/FONT]
  
  [FONT=&quot]    Alias /doc/ "/usr/share/doc/"[/FONT]
  [FONT=&quot]    <Directory "/usr/share/doc/">[/FONT]
  [FONT=&quot]        Options -Indexes MultiViews FollowSymLinks[/FONT]
  [FONT=&quot]        AllowOverride None[/FONT]
  [FONT=&quot]        Order deny,allow[/FONT]
  [FONT=&quot]        Deny from all[/FONT]
  [FONT=&quot]        Allow from 127.0.0.0/255.0.0.0 ::1/128[/FONT]
  [FONT=&quot]    </Directory>[/FONT]
  
  [FONT=&quot]</VirtualHost>[/FONT]
  
  [FONT=&quot]<VirtualHost *:80>[/FONT]
  [FONT=&quot]        ServerName ajaxterm.my.site.org[/FONT]
  [FONT=&quot]        Redirect 301 / [https://ajaxterm.mysite.org](https://ajaxterm.mysite.org)[/FONT]
  [FONT=&quot]        CustomLog /var/log/apache2/access.log combined[/FONT]
  [FONT=&quot]        ErrorLog /var/log/apache2/error.log[/FONT]
  [FONT=&quot]</VirtualHost>[/FONT]
  
  
  [FONT=&quot]<VirtualHost *:443>[/FONT]
  [FONT=&quot]        ServerName ajaxterm.my.site.org[/FONT]
  [FONT=&quot]        HostnameLookups Double[/FONT]
  [FONT=&quot]        CustomLog /var/log/apache2/access.log combined env=!dontlog[/FONT]
  [FONT=&quot]        SetEnvIf Request_URI "^/u" dontlog[/FONT]
  [FONT=&quot]        ErrorLog /var/log/apache2/error.log[/FONT]
  [FONT=&quot]        Loglevel warn[/FONT]
  [FONT=&quot]        SSLEngine On[/FONT]
  [FONT=&quot]        SSLCertificateFile /etc/apache2/ssl/apache.pem[/FONT]
  
  [FONT=&quot]        ProxyRequests Off[/FONT]
  [FONT=&quot]        <Proxy *>[/FONT]
  [FONT=&quot]                AuthUserFile /srv/ajaxterm/.htpasswd[/FONT]
  [FONT=&quot]                AuthName EnterPassword[/FONT]
  [FONT=&quot]                AuthType Basic[/FONT]
  [FONT=&quot]                require valid-user[/FONT]
  
  [FONT=&quot]                Order Deny,allow[/FONT]
  [FONT=&quot]                Allow from all[/FONT]
  [FONT=&quot]        </Proxy>[/FONT]
  [FONT=&quot]        ProxyPass / [http://localhost:8022/](http://localhost:8022/)[/FONT]
  [FONT=&quot]        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)[/FONT]
  [FONT=&quot]</VirtualHost>[/FONT]
  
  **[FONT=&quot]I have also tried copy over ajaxterm dir to /www/ and with (as per [http://bobcares.com/index.php/blog/?p=120):]("http://bobcares.com/index.php/blog/?p=120%29:")[/FONT]**
  [FONT=&quot]    <virtualhost *:443>[/FONT]
  [FONT=&quot]       ServerName localhost[/FONT]
  [FONT=&quot]       SSLEngine On[/FONT]
  [FONT=&quot]       SSLCertificateKeyFile /etc/apache2/ssl/apache.pem[/FONT]
  [FONT=&quot]       SSLCertificateFile /etc/apache2/ssl/apache.pem[/FONT]
  
  [FONT=&quot]       ProxyRequests Off[/FONT]
  [FONT=&quot]       <proxy *>[/FONT]
  [FONT=&quot]               AuthType Basic[/FONT]
  [FONT=&quot]               AuthName "remote Shell Access"[/FONT]
  [FONT=&quot]               AuthUserFile /etc/apache2/.htpasswd[/FONT]
  [FONT=&quot]               Require user myname[/FONT]
  [FONT=&quot]               Order deny,allow[/FONT]
  [FONT=&quot]               Allow from all[/FONT]
  [FONT=&quot]       </proxy>[/FONT]
  [FONT=&quot]       ProxyPass /ajaxterm/ [http://my.site.org:8022/](http://my.site.org:8022/)[/FONT]
  [FONT=&quot]       ProxyPassReverse /ajaxterm/ [http://my.site.org:8022/](http://my.site.org:8022/)[/FONT]
  [FONT=&quot]    </virtualhost>[/FONT]

---

### Post by MarkoCro on 2011-03-21
Hi. AjaxTerm is slow and ugly. What I use is [Shell In A Box]("http://code.google.com/p/shellinabox/"). Here is my howto for setting it up on Ubuntu with https and HTTP authentication:

[http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/]("http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/")

Cheers!

---

