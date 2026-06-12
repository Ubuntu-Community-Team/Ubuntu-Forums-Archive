---
title: "proftpd permissions"
date: 2009-04-11
forum: Server Platforms
---

### Post by matt91 on 2009-04-11
I have installed proftpd on my server and I'm having a problem with permissions.

I've created a user 'www' (home is /var/www) which I can login with proftpd, I can see all the files in /var/www. The ownership of /var/www is www-data:www-data recursively. I cannot do anything other than read files in the proftpd session even if I have files permissioned 777.

my proftpd.conf is the same as the default config except for IPv6 turned off and DefaultRoot ~

Is their another way other than changing the ownership of /var/www or logging in with www-data?

Thank you.

---

