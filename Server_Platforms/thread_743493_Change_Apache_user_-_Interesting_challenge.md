---
title: "Change Apache user - Interesting challenge"
date: 2008-04-02
forum: Server Platforms
---

### Post by sleepkreep on 2008-04-02
Hello all.  I have an interesting challenge.  I would like to provide access for my users to their home directories through WebDAV.  I want to completely stop supporting FTP.  I DO NOT want to switch to SFTP.  WebDAV is supported out of the box on every major OS so it is the obvious choice.  However, since apache runs as the www-data user, it cannot write to the user's home directory.  And here's the challenge.  I need apache to fork a process and change it to run with the permissions of the user logged in.  Special cases, I CANNOT write a rule for every user in the config file because we are constantly adding and removing users from the system.  We have on average 1000 users at any given moment.  Here's my config so far, and don't ask about the directory structure.  It's left over from the guy before me:

```

Alias /dav /usr/local/home/accts/

<Directory /usr/local/home/accts/>
        Order deny,allow
        Deny from all 
</Directory>

<Directory /usr/local/home/accts/*>
        RewriteEngine on
                RewriteCond %{SERVER_PORT} !=443
                RewriteRule ^.*/(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [R] 
        DAV on
        AuthBasicAuthoritative Off 
        AuthPAM_Enabled on
        AuthName "Home Directory Access"
        AuthType Basic
        Require valid-user
        Order allow,deny
        Allow from all 
</Directory>
```

Any suggestions?

---

