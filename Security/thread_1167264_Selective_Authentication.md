---
title: "Selective Authentication"
date: 2009-05-22
forum: Security
---

### Post by davehahn on 2009-05-22
I have a server running Apache/1.3.41.
I have an application that uses Apache, and all the configuration for this
application is done through the browser when you login as the user
application-admin.

The application uses Apache to do authentication - I had to add the
following to httpd.conf:
<Directory "/path/to/application">
AllowOverride None
AuthType Basic
AuthName "WebApp"
require valid-user
AuthUserFile /path/to/application/apache.userfile
Options None
</Directory>

My question is can I use Apache to limit logging in as user
"application-admin" to an internal subnet, so that you can't login as
"application-admin" from outside our building. For that matter, several
other internally used user accounts would be nice to limit to internal IPs
as well. Aside from just a few accounts, all the users are external users -
but these few accounts would be nice to be internal only.

What I'm wanting is:
AllowFrom 10.1.0.0/16 any user
AllowFrom everywhere else, anyuser except "applicaiton-admin"

I could have 2 separate auth files if I needed to - one that has "application-admin" and one that doesn't (cron job every minute to copy auth.1 to auth.2 and echo "application-admin" >> auth.2)

Could I then do something more like:

Any IP - require valid-user from /auth.1
10.*.*.* - require valid-user from /auth.2

Thanks!

Dave

---

