---
title: "SSL not requiring authentication"
date: 2009-02-02
forum: Server Platforms
---

### Post by jdunham on 2009-02-02
I am trying to set up my own server, and trying to stick to the ubuntu documentation with the help of HOWTOs that I can find. I am trying to set up Subversion with https:// access.  For now I am using a self-signed certificate since I am the only one using the server at this time.

After following the instructions at
[https://help.ubuntu.com/8.10/serverguide/C/httpd.html](https://help.ubuntu.com/8.10/serverguide/C/httpd.html)
and 
[https://help.ubuntu.com/8.10/serverguide/C/subversion.html](https://help.ubuntu.com/8.10/serverguide/C/subversion.html)

to that effect, I added this to the end of /etc/apache2/apache2.conf
<Location /svn>
  DAV svn
  SVNParentPath /srv/svn
  AuthType Basic
  AuthName "My Repository"
  AuthUserFile /etc/subversion/passwd
  <LimitExcept GET PROPFIND OPTIONS REPORT>
    Require valid-user
  </LimitExcept>
</Location>

Just about everything is working, but I can access the repository  without any password even though I am using an [https://.](https://.).. URL. I can also get the "It Works!" test page in apache  without being asked for a password. 

I guess it's obviously an apache ssl config problem but I have no idea how to debug it. I don't seem to be getting any errors.

---

### Post by spiderbatdad on 2009-02-02
Generally the above would go into a directory file in the enbled site. /etc/apache2/sites-available/default```
  DocumentRoot /var/www/
                 SSLEngine On
        <Directory />
                AuthType Basic
                AuthName "Restricted Files"
                AuthUserFile /home/some_user/.htpasswords
                Require valid-user
                Options FollowSymLinks
                AllowOverride None
        </Directory>
```

---

### Post by jdunham on 2009-02-03
[QUOTE=spiderbatdad;6666341]Generally the above would go into a directory file in the enbled site. /etc/apache2/sites-available/default

Thanks so much for the reply.

The ubuntu docs for Subversion did say to put it in apache.conf, but... they didn't say I should put a typo in when I named the passwd file.  I guess that's what testing is for.

Subversion is now fine, but I can't get apache to serve secure ssl pages ([https://)](https://))

Trying to change the ubuntu configuration as little as possible, I have in 
/etc/apache2/sites-available/default-ssl:
```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin webmaster@localhost
        

        DocumentRoot /srv/www/mysecurefiles/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /srv/www/mysecurefiles/>
                #next 4 lines to ubuntu config by me
                AuthType Basic
                AuthType "My Restricted Files"
                AuthUserFile /etc/httpd/.htpasswords
                Require valid-user

                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>

```
[followed by lots more stuff, but no changes except for certificate and keys, which seem to be working]

when I browse to [https://mysite.com/](https://mysite.com/) [not the real name]

I get error 500, and the apache error log shows
...configuration error:  couldn't check user.  No user file?: /

the file /etc/httpd/.htpasswords exists and seems correct and I gave it universal rw access, to no avail.  Any ideas would be appreciated.
Based on the apache documentation, I'm trying to avoid using .htaccess files in the directories in favor of a central configuration.

---

### Post by spiderbatdad on 2009-02-03
```
	#this I have in httpd.conf:
<Directory /srv/www/mysecurefiles>
<IfModule mod_rewrite.c>
	<IfModule mod_ssl.c>
		RewriteEngine on
		RewriteCond %{HTTPS} !^on$ [NC]
		RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
	</IfModule>
        <IfModule>
SSLOptions +StrictRequire
</Directory>
SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM
SSLCertificateFile /path/to/ssl.crt/server.crt
SSLCertificateKeyFile /path/to/ssl.key/server.key


#this in /sites-available/mysite
      <VirtualHost **DOMAIN.com**:443>
        ServerAdmin actual@email.net
        

        DocumentRoot /srv/www/mysecurefiles/
                 SSLEngine On
        <Directory />
                  #next 4 lines to ubuntu config by me
                AuthType Basic
                AuthType "My Restricted Files"
                AuthUserFile /etc/httpd/.htpasswords
                Require valid-user
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /srv/www/mysecurefiles/>
               
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>

```
Where DOMAIN.com is your FQDN, or at least ip address.
Of course you have forwarded port 443 from your router to your server?

---

### Post by jdunham on 2009-02-03
> **spiderbatdad said:**
> 
Where DOMAIN.com is your FQDN, or at least ip address.
Of course you have forwarded port 443 from your router to your server?

Well that didn't work.  I specified the host FQDN and restarted apache, but the behavior did not change.

Truthfully I didn't change the router, but subversion over https is working fine, so I am sure that means port 443 traffic is reaching the host.

Thanks again for the response, and feel free to suggest something else. I'll keep thinking about it too.](*,)]

---

### Post by spiderbatdad on 2009-02-03
subversion over https is not the same as your domain over https. If you haven't open 443 on your router, requests from outside cannot get through on that port to your server. Additionally if you have enabled ufw or another firewall on the server...that needs to allow 443
Edit: i think i see you are only trying to use subversion repos, you are not actually hosting on your machine?

---

### Post by jdunham on 2009-02-03
> **spiderbatdad said:**
> subversion over https is not the same as your domain over https. 

I don't think that's true.  The whole point of subversion over https is that apache serves it up securely with ssl.  Also I can telnet to the host on port 443 and the connection is made, so the router is definitely doing its job.

Maybe I'm a limited by this:
[http://wiki.apache.org/httpd/NameBasedSSLVHosts](http://wiki.apache.org/httpd/NameBasedSSLVHosts)

Thanks for your attention!

---

