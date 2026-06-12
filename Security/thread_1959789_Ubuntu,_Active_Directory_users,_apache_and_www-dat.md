---
title: "Ubuntu, Active Directory users, apache and www-data!"
date: 2012-04-16
forum: Security
---

### Post by skop on 2012-04-16
Hi to all,

I have a complicate issue that I can't solve.

Scenario:
- Webfarm, with development servers running Ubuntu 8.04 and 10.04;
- Users on Active Directory;
- Users can authenticate to development servers with AD credentials;
- Users writes them development scripts and sites on 
/var/www/project1 etc
- The permissions on these directories are user:domain+group

The problem:
A web application on php, that runs in these servers via apache  (www-data:www-data), must be able to write and delete some files in the developement directory project1 etc etc etc.

Apparently, the solution is to add the local www-data users to the domain. But isn't possibile (as I tried). 

Any other idea? Any other design suggestion? Any help will be appreciated!

Thank you.
JS

---

### Post by skop on 2012-04-17
Hi,
an update:
The only working solution, for now, is to chmod all tree to 777. This is a non solution, but the server is a dev internal server.

If any ideas...

Regards,
JS

---

