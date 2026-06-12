---
title: "VSFTP - Permissions for a single user"
date: 2008-04-13
forum: Server Platforms
---

### Post by flip79 on 2008-04-13
Hello, I recently bought a VPS with CentOS (sorry to ask here, but I'm usually an Ubuntu user, and Ubuntu Forums are my second home :P )

I have a little problem: I'm currently running some sites that I directly manage, but I have also a site that should be updated by an external person via FTP.

I installed VSFTP, configured it to allow FTP local user login, then I added an user (let's say his user name is "foo"), and I disabled SSH access for him in /etc/passwd:

```
foo:x:500:500::/home/foo:/sbin/nologin
```

then I set VSFTP to CHROOT users:
chroot_local_user=YES

now user foo can login with any FTP client, and he is automatically CHROOTed to his home directory, but he can only operate in this directory.

So, I also mounted the directory with the site I want him to manage to his home dir:

mount --bind /var/www/sites/foo-site.com/htdocs /home/foo/htdocs/

so he can browse to this dir too, but he has no write permissions.

How I can add this permission for my "foo" user?

actually, permissions for the foo-site.com directory are:
```
drwxrwxr-x 3 ricky apache 4096 Apr 2 10:53 htdocs
```

(ricky is me :) )

---

### Post by andguent on 2008-04-13
It looks like you have everything done right so far. How clean does it look like when you do:

ls -lah /home/foo/htdocs/

Is the group 'apache' a custom made one? The group membership of my apache daemon is usually 'www-data'. Is it worth adding yourself into that group? Just an idea, not a definitive/secure solution. :)

adduser ricky www-data

---

### Post by flip79 on 2008-04-13
Hello, thank you very much for your answer!

"apache" group is one of the default system groups I found on my VPS, if I'm right it should be the group under user "apache" (the apache deamon) runs to serve sites.

CentOS names Apache service "httpd", while Ubuntu names it "apache2", so I think it should be only a difference in titles...

I added my "foo" user to "apache" group, and now he can write files with FTP also for the directory of the site I mounted in his root... fantastic! :)

The only doubt I still have is if my procedure (both when I assign the user to apache's group and when I mount a subdirectory from /var/www to the user's home with fstap) is correct or... am I opening some security breach in my server?

---

### Post by andguent on 2008-04-13
Honestly, I wish I knew. I approach nearly all of my security issues with aggressive firewalling/VPN setups. It is definetly possible to set it up securely (vs = very secure). Maybe someone else will have more in depth tips, or Google may already have the answers you are looking for. Let us know how it goes.

---

