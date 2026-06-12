---
title: "Easy server questions"
date: 2009-11-24
forum: Server Platforms
---

### Post by Iker Etxebarria on 2009-11-24
Hi all!

I have installed the Ubuntu 9.10 server edition with a LAMP and VSFTPD.

The goal of my installation was to configure the LAMP and access to the /var/www folder via FTP to upload the content of my apps.

I configured vsftpd but when I try to put files on it and run php files,  I couldn't so I changed the www permissions and owner, and now, I don't know how should be the permissions on the www folder.

Here are my questions:
-Wich permissions should the www folder have to can access with a ftp user to it, store php files and can run them?
-Wich are the default permission of the www folder?
-When I upload a php file it doesn't have the +x permissions. So I have to change it. How could I set that each time I upload a php file it has automatically the execution permission enabled?

Thanks

---

### Post by Lars Noodén on 2009-11-24
make a group for "webmasters" and add those allowed to edit the web site to it

```

# set the group for the web folders
sudo find /var/www -type d -exec chown webmasters {}  \;

# then set the directory permissions so that the group
# can write and that items in the directory stay in that group
sudo find /var/www -type d -exec chmod u=rwx,g=rwxs,o=rx {}  \;

```

If you want to have several groups, then ACLs would be the way to go for the /var/www partition, assuming it's a separate partition.

Regarding FTP, unless you have pressing reason to use FTP and specifically FTP, you might want to consider using SFTP.  It's a lot easier to set up and will give an encrypted connection.

---

