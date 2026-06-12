---
title: "Apache UserDir module"
date: 2007-06-13
forum: Server Platforms
---

### Post by LebowskiT1000 on 2007-06-13
Major noob to Ubuntu and somewhat of a noob to general server config.

I am trying to get the Apache UserDir module working the way I want it to work.  I have enabled the module using 'a2enmod UserDir' and that worked, added the following to the apache2.conf file:

#UserDir
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
  AllowOverride Fileinfo AuthConfig Limit Indexes
  Options Multiviews Indexes SymLinksIfOwnerMatch IncludesNoExec
  <Limit GET POST OPTIONS>
    Order allow,deny
    Allow from all
  </Limit>
  <LimitExcept GET POST OPTIONS>
    Order deny,allow
    Deny from all
  </LimitExcept>
</Directory>

This all seems to work fine, just as I'd expect it to.  I go to [http://www.domain.com/~user](http://www.domain.com/~user) and it takes me to the appropriate place.  GREAT!

BUT...here's what I want.  I don't want [http://www.domain.com/~user](http://www.domain.com/~user) to go to /home/user/public_html, I want it to go to /home/user/public_html/dir1/dir2.

So I changed the config in the apache2.conf file to read 'UserDir /home/*/public_html/dir1/dir2' and restarted apache, to my surprise nothing changed.  I suspect whatever the root cause to my next problem below may be the same reason for this problem.

And secondly, no matter what I do I can't seem to view dir2 in the browser.  Even if I navigate to that directory in the browser with the first configuration above, it seems to be unreachable (although the permissions on the 'dir2' directory is the same as everything else, so I'm at a loss.

Any help would be most appreciated.  Thanks.

---

### Post by dfreer on 2007-06-13
> **LebowskiT1000 said:**
> Major noob to Ubuntu and somewhat of a noob to general server config.

I am trying to get the Apache UserDir module working the way I want it to work.  I have enabled the module using 'a2enmod UserDir' and that worked, added the following to the apache2.conf file:

#UserDir
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
  AllowOverride Fileinfo AuthConfig Limit Indexes
  Options Multiviews Indexes SymLinksIfOwnerMatch IncludesNoExec
  <Limit GET POST OPTIONS>
    Order allow,deny
    Allow from all
  </Limit>
  <LimitExcept GET POST OPTIONS>
    Order deny,allow
    Deny from all
  </LimitExcept>
</Directory>

This all seems to work fine, just as I'd expect it to.  I go to [http://www.domain.com/~user](http://www.domain.com/~user) and it takes me to the appropriate place.  GREAT!

BUT...here's what I want.  I don't want [http://www.domain.com/~user](http://www.domain.com/~user) to go to /home/user/public_html, I want it to go to /home/user/public_html/dir1/dir2.

So I changed the config in the apache2.conf file to read 'UserDir /home/*/public_html/dir1/dir2' and restarted apache, to my surprise nothing changed.  I suspect whatever the root cause to my next problem below may be the same reason for this problem.

And secondly, no matter what I do I can't seem to view dir2 in the browser.  Even if I navigate to that directory in the browser with the first configuration above, it seems to be unreachable (although the permissions on the 'dir2' directory is the same as everything else, so I'm at a loss.

Any help would be most appreciated.  Thanks.

I'm pretty sure that the options for user directories is located in /etc/apache2/mods-available/userdir.conf, or something similiar (sorry, on a windows machine right now). You should be modifying the home directories there instead of apache2.conf.

---

### Post by LebowskiT1000 on 2007-06-13
lol, I just read that on another post and made the necessary corrections.  Although, the issue still stands as to why I can't see the 'dir2' directory from the browser.

Getting this error now:

Internal Server Error
The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log

UPDATE:

I checked the error log and it appears to not like the .htaccess file I have in the dir2 directory:

"... .htaccess: Options not allowed here"

I am using the symfony php framework and this is just the .htaccess file that is created by default.

Options +FollowSymLinks +ExecCGI

<IfModule mod_rewrite.c>
  RewriteEngine On

  # uncomment the following line, if you are having trouble
  # getting no_script_name to work
  #RewriteBase /

  # we skip all files with .something
  RewriteCond %{REQUEST_URI} \..+$
  RewriteCond %{REQUEST_URI} !\.html$
  RewriteRule .* - [L]

  # we check if the .html version is here (caching)
  RewriteRule ^$ index.html [QSA]
  RewriteRule ^([^.]+)$ $1.html [QSA]
  RewriteCond %{REQUEST_FILENAME} !-f

  # no, so we redirect to our front web controller
  RewriteRule ^(.*)$ index.php [QSA,L]
</IfModule>

# big crash from our front web controller
ErrorDocument 500 "<h2>Application error</h2>symfony application failed to start properly"

Any Thoughts?

---

