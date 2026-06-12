---
title: "Ubuntu permissions question"
date: 2008-06-05
forum: Security
---

### Post by esullivan on 2008-06-05
I was wondering if there was an easy way to make the entire root (/) permission free (777).  Also any NEW folders that will be created after that.

Or at least inheritable permissions or something like that.

example:

/var/www

I want EVERYTHING under that permission free, writable, 777 whatever.

Thanks in advance.
Evan

---

### Post by Dr Small on 2008-06-05
That is HIGHLY dangerous. I think you better do a little more reading on chmod before you do that.

r = read
w = write
x = execute

777 = rwx-rwx-rwx

In the end, that would be a bad idea... literally.

---

### Post by esullivan on 2008-06-05
> **Dr Small said:**
> That is HIGHLY dangerous. I think you better do a little more reading on chmod before you do that.

r = read
w = write
x = execute

777 = rwx-rwx-rwx

In the end, that would be a bad idea... literally.

Ok, maybe not the entire root, but just one folder.  Where everything under it is 777 then.

---

### Post by Dr Small on 2008-06-05
You can try:
```
chmod 777 /var/www
```

If that is what you want. But www should be set to 755.
If you want to change every directory under /var/www, use:
```
chmod -R 777 /var/www
```

Dr Small

---

### Post by esullivan on 2008-06-05
You guys are quick around here.  Thanks man!

It worked, but will any new folder made under that dir have the same permissions?

---

### Post by Dr Small on 2008-06-05
I'm not really sure. I have never did anything like that. I always thought that permissions automatically defaulted to 755.

---

### Post by tedrogers on 2008-06-05
I'm pretty sure that new folders will default to an non-777 state.

It stands to reason that this is what it is like on most other consumer OS's, so it should he the same here.

You would need some kind of script to change the permissions of any new folders that are created.

Don't ask me about that though.

I would guess it has something to do with CRON jobs though.

Good luck.

---

### Post by The Cog on 2008-06-05
> **esullivan said:**
> 
It worked, but will any new folder made under that dir have the same permissions?

No. The permissions on newly created files/folders is controlled by the umask environment variable.

---

### Post by tedrogers on 2008-06-06
> **The Cog said:**
> No. The permissions on newly created files/folders is controlled by the umask environment variable.

And there we have it! :)

---

### Post by esullivan on 2008-06-06
Thanks all!

---

### Post by HalPomeranz on 2008-06-06
The "right" thing to do here is not to make every directory world-writable, but instead to make everything group writable and add the people who need to access the directory structure to the appropriate group.  For example:

```

sudo groupadd newgroup
sudo chgrp -R newgroup /var/www
sudo chmod -R g+w newgroup /var/www
sudo find /var/www -type d -exec chmod g+s {} \;

```

The last line above will set set-GID on every directory under /var/www.  This will ensure that when new files get created under these directories the new files will end up being group-owned by "newgroup".

When you want to give a user access to /var/www, simply add them to newgroup with the command "usermod -aG newgroup someuser".

---

### Post by esullivan on 2008-06-06
I am not worried about any security, this is the only Linux box we have, just as a web server for Joomla.  The issue I have is when I install a new component for Joomla or upload pictures to a gallery in Joomla they are "locked" with the lock on the file icon.

chmod -R 777 (dir)

Is working GREAT to unlock everything under www root, however any thing new is locked.  I am really not worried about "right" or groups, I just want ALL new files to be open to any user so it's not locked.

The pictures are being uploaded with www-data for user permissions.

I am kind of new to Linux.

---

### Post by esullivan on 2008-06-06
> **HalPomeranz said:**
> 
```

sudo groupadd newgroup
sudo chgrp -R newgroup /var/www
sudo chmod -R g+w newgroup /var/www
sudo find /var/www -type d -exec chmod g+s {} \;

```

This didn't work

sudo chmod -R g+w newgroup /var/www  <--- this line said (newgroup) directory didn't exist

sudo find /var/www -type d -exec chmod g+s {} \;  <-- this line said bash: syntax error near unexpected token `('

---

### Post by HalPomeranz on 2008-06-06
> **esullivan said:**
> I am not worried about any security, this is the only Linux box we have, just as a web server for Joomla.

With respect, this is a dangerous attitude.  If the box gets rooted and somebody replaces all of your web content with malware or defamatory material, how much trouble is that going to be for your organization?  I guarantee you it's going to be a lot of trouble for anybody who visits your site.

> **esullivan said:**
> The issue I have is when I install a new component for Joomla or upload pictures to a gallery in Joomla they are "locked" with the lock on the file icon.

Interesting.  That implies that Joomla is creating the files with permissions that are too restrictive.  The advice I gave in my earlier message will not help with that problem.

I'm not familiar with Joomla, so I can't say if there's a configuration setting that controls what permissions new files get created with.  You might try posting to forum.joomla.org instead, since those folks would be more familiar with Joomla-specific issues.

> 
sudo chmod -R g+w newgroup /var/www <--- this line said (newgroup) directory didn't exist


My bad, I made an error in the commands I gave you earlier:

```

sudo groupadd newgroup
sudo chgrp -R newgroup /var/www
sudo chmod -R g+w /var/www
sudo find /var/www -type d -exec chmod g+s {} \;

```

> sudo find /var/www -type d -exec chmod g+s {} \; <-- this line said bash: syntax error near unexpected token `(' 

Huh.  Interesting.  That would imply to me that you've got some directory names under /var/www that have parentheses in their names.  Well, since the above advice isn't going to help you anyway, I won't give you the more complicated recipe to work around this problem.

---

### Post by esullivan on 2008-06-06
This site is internal only, you can't get to it from the outside.  I understand that you are trying to protect me from myself, but I don't think there will be any issues.

doing chmod -R 777 /var/www works great, it unlocks everything under www folder EXCEPT new stuff.  So if I upload a picture to the gallery, its locked, if I install a new component, the .php files are locked.

Thanks for any help that worked or not.

---

### Post by esullivan on 2008-06-07
I found a solution, using webmin I went to:

-Server
-Apache Webserver
-Global Config
-User and Groups

From there you can set which user\group that Apache uses.

Thanks for you help guys!

---

