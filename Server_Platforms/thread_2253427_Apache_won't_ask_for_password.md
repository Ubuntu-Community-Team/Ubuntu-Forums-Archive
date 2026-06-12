---
title: "Apache won't ask for password"
date: 2014-11-19
forum: Server Platforms
---

### Post by chris137 on 2014-11-19
Hi,
I recently moved a webpage from one server to another.
On my old Server apache 2.2.22 is running and 2.4.7 on my new server.
I copied my password file to the same place with same permissions.
Also I copied the content from default in sites-available to 000-default.conf on my new server which seems to be the default there.
Here are the changes I made on my new server:
- Changed 'ServerName' from my domain to the IP
- Changed all pathes so it would be right

Here is the important part I guess:
```
        <Location />
                AuthType Digest
                AuthName "v87532"
                AuthDigestDomain /var/www/vhosts/default/htdocs/ http://127.0.0.1/vhosts/default/htdocs

                AuthDigestProvider file
                AuthUserFile /etc/apache2/passwords
                Require valid-user
                SetEnv R_ENV "/var/www/vhosts/default/htdocs"
        </Location>
```
It works perfectly on my old server so I'm not sure if there is a version-related problem or my changes were either wrong or incomplete.

---

### Post by chris137 on 2014-12-13
This problem is kinda solved.
For unrelated reasons I changed the listening port and root directory.
Suddenly I got asked for a password.
I'm not sure what the problem was but it definitly had to do with a bad config.

---

