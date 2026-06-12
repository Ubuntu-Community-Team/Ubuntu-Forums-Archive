---
title: "Apache 403 forbidden"
date: 2011-06-28
forum: Server Platforms
---

### Post by ryanrobinson on 2011-06-28
Hi guys,

I have installed Apache many times and then shared the /var/www folder using Samba. I have always been able to view the files in a web browser via my servers IP.

On my latest install however, it won't let me browse the folders in the web browser but I am allowed to make changes to the files via the samba share.

This is my samba config:

[www]
        comment = Apache root
        path = /var/www
        public = yes
        writable = yes
        valid users = dev
        create mask = 0771
        directory mask = 0771
        force user = dev
        force group = www-users


And I ran the commands:

[HTML]sudo chown -R root:www-users /var/www
sudo chmod -R 771 /var/www[/HTML]

To give samba user permissions.

Any suggestions as to why it's doing this?

---

### Post by dapperdanny77 on 2011-06-28
Please post your apache config - maybe the DirectoryIndex option is not set. Have a look at your apache error log (/var/log/apache2)

---

### Post by ryanrobinson on 2011-06-28
I got it working.

I changed the permissions in the Samba config and the chown commands to use 755 permissions.

---

### Post by Lars Noodén on 2011-06-29
Glad you spotted the permissions error.  You can refine it even further by not granting execute permission to regular files:

```

find /var/www -type d -exec chmod u=rwx,g=rwxs,o=rx

find /var/www -type f -exec chmod u=rw,g=rw,o=r

```

---

