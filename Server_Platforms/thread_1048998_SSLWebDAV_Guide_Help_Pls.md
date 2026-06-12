---
title: "SSL/WebDAV Guide: Help Pls"
date: 2009-01-24
forum: Server Platforms
---

### Post by boaz60 on 2009-01-24
I've been searching the forums and the net extensively for a single guide that combines instructions on how to setup Ubuntu LAMP with WebDAV & SSL.

Can anyone please help me find a guide that will show me how to sign my own certificate, configure WebDAV to use SSL and make some users.

Thanks for any help :)

---

### Post by jure1873 on 2009-01-24
you don't need a single guide, install lamp, I think you can do that simply by selecting lamp from the server cd boot menu and then follow a guide on setting up webdav, it's probably the same if it's for ubuntu/rh/suse/... you just have to enable the dav module and set up user permissions

---

### Post by boaz60 on 2009-01-24
Thanks for the reply, however the key here is SSL with WebDAV, which is causing me the problems.

---

### Post by jure1873 on 2009-01-24
what kind of problems? With ssl even the broken xp built in dav support (web folders) work without problems. First you've got to make it work without ssl and then you just enable ssl.

---

### Post by jure1873 on 2009-01-24
I've got something like this and then set the required username in .htaccess for every user.
<IfModule mod_userdir.c>
    UserDir public_html
    UserDir disabled root nimda

    # Make sure to chown www-data:www-data this file
    DAVLockDB /var/lib/apache2/DAVLockDB
    <Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        #Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        Options MultiViews Indexes FollowSymLinks IncludesNoExec
        DAV On

        AuthPAM_Enabled On
        AuthPAM_FallThrough Off
        AuthBasicAuthoritative Off
        AuthUserFile /dev/null

        #ForceType text/plain
        RedirectMatch 404 ^/(MSOffice/|_vti_bin/|_vti_inf.html$)
        Header set MS-Author-Via DAV

        require valid-user
    </Directory>
</IfModule>

---

