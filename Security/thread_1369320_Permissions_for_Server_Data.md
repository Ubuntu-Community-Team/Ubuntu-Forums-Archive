---
title: "Permissions for Server Data"
date: 2009-12-31
forum: Security
---

### Post by humphreybc on 2009-12-31
At the moment I've got my server set up with one 500GB hard drive with two partitions. 5GB for the operating system mounted at / and the rest mounted at /data for the content.

Now at the moment I have the /data permissions set to 777 and the owner set to www-data:www-data - because that's what AjaXplorer requires I think.

I'm not sure about the 777 though, doesn't this mean that if anyone had physical access to my server, they could delete whatever they wanted?

But I have to use sudo to make any changes inside /data, as it's owned by www-data, not me - so does this make it secure?

---

### Post by FuturePilot on 2009-12-31
> **humphreybc said:**
> 
I'm not sure about the 777 though, doesn't this mean that if anyone had physical access to my server, they could delete whatever they wanted?

If someone had access period. Remote or physical.

> But I have to use sudo to make any changes inside /data, as it's owned by www-data, not me - so does this make it secure?

No. Running a web server with permissions set to 777 is not secure at all.

---

### Post by humphreybc on 2009-12-31
Okay... so what should I set the permissions to?

---

### Post by mhanson on 2010-01-01
FuturePilot is correct. Your settings are totally unsecure. To start with, all your regular files should be set to 644, all your directories should be set to 755 regardless of who owns them. Then, depending on the needs of you application (AjaxExplorer) you will customize files and directories permissions as needed.

Cheers

---

### Post by humphreybc on 2010-01-23
So.. in layman's terms and specific to my setup...

Something like:

```

sudo chmod 755 -R /

```

Then what do I set /data and /documents to? (These are the two folders that AjaXplorer sees). Oh and of course /var/www is where AjaXplorer is installed.

Where can I see a list of what the numbers mean?

---

### Post by FuturePilot on 2010-01-23
> **humphreybc said:**
> So.. in layman's terms and specific to my setup...

Something like:

```

sudo chmod 755 -R /

```

Then what do I set /data and /documents to? (These are the two folders that AjaXplorer sees). Oh and of course /var/www is where AjaXplorer is installed.

Where can I see a list of what the numbers mean?

No, **do not** do that. That is very bad and will most likely break some part(s) of your system. Certain programs will not run if the correct permissions are not set on its config files.

More on file permissions [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by humphreybc on 2010-01-23
Hmm so do my /data and /documents folders need to be owned by root or by www-data for AjaXplorer to function?

---

### Post by noway2 on 2010-01-23
I would suggest that you make your files and folders owned by root, but readable by whatever user your web server runs under, such as www-data.  The exception being that you want to have read and executable set for directories.

This way, the web server can access the data, but only root can make changes to it.

---

### Post by bodhi.zazen on 2010-01-24
With such a large hard drive, 5 Gb is a tad scant for your root partition, do you really need 500 Gb for data ?

I would make the root partition 10 Gb

In terms of your data, it depends on if the web server needs to write data.

If not, ownership is root:www-data permissions 750

If so, ownership is www-data:www-data permissions 750

The data itself should have permissions of 640, unless the file is executable, in which case, 750

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by humphreybc on 2010-01-24
Yep I do need that much space for data, I'm actually running out so I'm going to buy another 500GB drive soon.

I ran these commands, tell me if that should suffice:

```

sudo adduser benjamin www-data
sudo chown -R www-data:www-data /data
sudo chown -R www-data:www-data /var/www
sudo chmod 770 /data
sudo chmod 770 /var/www

```

I have some folders on my server bookmarked in Nautilus, and I copy stuff over so I want to have write permissions. Also, I put stuff in /var/www to share to other people (like dropbox).

AjaXplorer seems to work okay still, so that's good.

Why is 5GB too small? I still have 3.1GB free according to my [server stats.]("http://humphreybc.homeip.net/stats.php")

Can I expand the partition?

---

### Post by Lars Noodén on 2010-01-25
> **humphreybc said:**
> Yep I do need that much space for data, I'm actually running out so I'm going to buy another 500GB drive soon.

I ran these commands, tell me if that should suffice:
...
I have some folders on my server bookmarked in Nautilus, and I copy stuff over so I want to have write permissions. Also, I put stuff in /var/www to share to other people (like dropbox).


Close.

Try creating another group, such as **webmasters** or something.  The web server should only have write access when and where it actually needs it, and then only on a case by case basis.  So the group **www-data** should **not** have write access, except where you need the webserver itself to be able to write files.  

You can getting finer control with [find](http://manpages.ubuntu.com/manpages/karmic/en/man1/find.1.html) instead of **chmod -R**.  chmod makes no differentiation between files and directories, though the really do better (safer) with slightly different permission.

```

# create a group for those that are allowed to edit web pages
sudo addgroup webmasters
# add benjamin to that group
sudo adduser benjamin webmasters

# fix group membership and permissions for directories
sudo find  /data -type d -exec chgrp webmasters {} \;
sudo find  /data -type d -exec chmod u=rwx,g=rwxs,o=rx {} \;

sudo find  /var/www -type d -exec chgrp webmasters {} \;
sudo find  /var/www -type d -exec chmod u=rwx,g=rwxs,o=rx {} \;


# fix group membership and permissions for the files
sudo find  /data -type f -exec chgrp webmasters {} \;
sudo find  /data -type f -exec chmod u=rw,g=rw,o=r {} \;

sudo find  /var/www -type f -exec chgrp webmasters {} \;
sudo find  /var/www -type f -exec chmod u=rw,g=rw,o=r {} \;

```

---

### Post by humphreybc on 2010-01-25
Hey, thanks for the reply. Code examples are very useful!

Just one question - won't 

```

sudo find  /var/www -type d -exec chgrp webmasters {} \;
sudo find  /var/www -type f -exec chgrp webmasters {} \;

```

change the ownership to something other than www-data? I'm fairly certain the AjaXplorer files need to be owned by www-data to work..

---

### Post by Lars Noodén on 2010-01-27
> **humphreybc said:**
> Hey, thanks for the reply. Code examples are very useful!

Just one question - won't 

```

sudo find  /var/www -type d -exec chgrp webmasters {} \;
sudo find  /var/www -type f -exec chgrp webmasters {} \;

```

change the ownership to something other than www-data? I'm fairly certain the AjaXplorer files need to be owned by www-data to work..

[chown](http://linux.die.net/man/1/chown) changes the owner of the file or directory, [chgrp](http://linux.die.net/man/1/chgrp) changes the group membership of the file or directory.  If you want the file or directory to be in more than one group, you will have to mount that partition with ACLs enabled, something I wish Ubuntu did by default. 

Whether AjaXplorer needs to own the directories, I do not know.  That should be in the AjaXplorer documentation, if not, then press that project's members to add that information.  

What problem are you trying to solve through use of AjaXplorer?

---

