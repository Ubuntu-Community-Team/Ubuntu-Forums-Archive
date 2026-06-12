---
title: "Redmine svn integration"
date: 2010-06-03
forum: Server Platforms
---

### Post by jeka.km on 2010-06-03
I've been faced with such a problem:
       Installed Redmine, configured automatic repository svn creation for  new
projects.
Users of redmine and svn must be created and matched  automaticly. Found a
manual [http://www.redmine.org/wiki/1/Repositories_access_control_with_apache_mod_dav_svn_and_mod_perl](http://www.redmine.org/wiki/1/Repositories_access_control_with_apache_mod_dav_svn_and_mod_perl)
But,  whle adding necessary options in config of virtual host, apache showed
me  an error message: "Invalid command
'RedmineDSN', perhaps misspelled  or defined by a module not included in the
server configuration". As i  understand such a problem shows up when symlink
for Redmine.pm is  not created, but i did it
(/usr/lib/perl5/Apache/Redmine.pm)
       If anyone knows how to solve this problem - i'd be very thankful.
OS:  Ubuntu 10.04 Server

---

### Post by L0neRanger on 2010-10-30
Looking for similar help. Anyone out there has this setup?

---

### Post by khairil on 2010-12-25
I resolved mine by adding
```
PerlLoadModule Apache::Redmine
```
before
```
<Location /svn>
...

```

---

