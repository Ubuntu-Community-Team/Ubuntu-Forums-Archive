---
title: "htaccess (password protecting)"
date: 2010-03-11
forum: Security
---

### Post by DarkPrinceX on 2010-03-11
hi,

Gonna try to make it simple ^^
i just completed setting up a ubuntu server 9.10, and i installed webalizer, which then can be found in http://www.<hostorsomething>.com/webalizer

and for security reasons i wanted to password protect the page (obviously =) )
and  for that i wanted to use htaccess, and followed these steps:


1. created .htaccess in /www/webalizer

2. pasted this in it

AuthUserFile /var/ht/.htpasswd
AuthGroupFile /dev/null
AuthName webstats     
AuthType Basic
require user bruger


3. created the .htpasswd in the path the htaccess is pointing at with:

htpasswd -c .htpasswd bruger

and entered the password.

that should be it right? but the page is still shown! no asking for password or anything! :(

i also checked the conf file for apache:


#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

i spent time on researching but they all do the same way i do..

---

### Post by cdenley on 2010-03-11
How is your vhost configured? It needs to allow AuthConfig to be overridden.
```

cat /etc/apache2/sites-available/default

```

Also, make sure it isn't a browser caching issue.
```

echo -e "GET /webalizer HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by DarkPrinceX on 2010-03-11
i checked and i was just starring at the "none" part for 10 mins and went doh!
 sat it to "all" now.


Thank you very much cdenley! ^^

---

