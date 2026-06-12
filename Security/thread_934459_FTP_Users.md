---
title: "FTP Users"
date: 2008-09-30
forum: Security
---

### Post by RavenSensei on 2008-09-30
We have a need for our Marketing dept to be able to ftp files up and down from our 8.04 ubuntu server.  All of our directories are live on the web.

I would like to create a user that will allow it access to a directory within /var/www.  We have 3 sites, and I'd like to create a different user for each site that only allows them access to that specific site.  It'll allow us to track who is doing what out there.

I don't know anything about groups or why /var/www exists as the bane of my existence, but for some reason, every user I create and try to push a file to /var/www/site1, it tells me it can't (553 Could not create file)

Any ideas?  I think I need to create a group that has access to those dirs and then put the people in it, but I don't know how.

---

### Post by lemming465 on 2008-09-30
FTP is pretty much only good for intranet use and anonymous downloads.  For uploads I'd strongly recommend using SSH file copies ("scp") instead.

/var/www is simply the default document root for Apache httpd.  If you don't like having your web documents there, change it.  See e.g. */etc/apache2/sites-enabled/000-default*.

The "could not create file" error would be a group permissions problem; you are going to have to learn about groups, alas.

Assuming you have users fred, joe, and mary, the kind of thing you need is along the lines of:
```
sudo -i
groupadd marketing
mkdir -p /var/www/upload/marketing
chgrp marketing /var/www/upload/marketing
chmod 2775 /var/www/upload/marketing
for muser in fred joe mary; do
  usermod -G marketing -a $muser
done
```

---

