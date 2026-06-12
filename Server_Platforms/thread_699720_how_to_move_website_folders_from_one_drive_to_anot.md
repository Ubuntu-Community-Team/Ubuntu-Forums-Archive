---
title: "how to move website folders from one drive to another"
date: 2008-02-17
forum: Server Platforms
---

### Post by sandyeggoboy on 2008-02-17
hi All --

I have an apache website that is living currently in a /home dir of one of my users. It has now grown so that my / folder is now 99% used when i do df -H. i have already setup a new drive and partition to hold the site that is big enuff (for now) but need to know how to PROPERLY move the site with out breaking any ownership or group rights, privileges and/or rank. 
I tried this once before by moving the files to another drive and then changing the symbolic link in the /var/www folder to pint to it, seemed to work OK but then started having issues with permissions.
Could someone give me a couple of good ideas?

Thanks,

Deric Stowell

---

### Post by faulkes on 2008-02-17
This is entirely dependent on how the website was configured in /etc/apache2/apache2.conf and /etc/apache2/sites-available/<site-name>.

If the website is that of a user and is accessed via [http://domain.com/~user](http://domain.com/~user) then it is somewhat more complex as the URL could change.  The only solution to that would be to change the users home directory to the newly mounted filesystem and ensure that they have appropriate righs when the data is moved over (via chown user:group dir/ & possibly a global -R chown inside that directory).

If the website has been configured for a domain, the you should only need to change the DocumentRoot in /etc/apache2/sites-available/<site-name> to point to the newly mounted fs (after copying the data over) and directory.  You would still need to configure the appropriate permissions such that the user could access this directory for read/writes.

Finally, df -h will show the total usage of the partitition, not the actual directory, so in fact it may or may not be that particular user.  To determine how much space the user is actually using you want to:

```

cd ~user
du -sh

```

Which should summarize the full size of the users directory.

If you can provide additional details on how your apache2 installation and that user in particular are setup, we can be of further assistance.

Faulkes

---

