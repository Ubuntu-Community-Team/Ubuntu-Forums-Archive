---
title: "Ubuntu Server Permissions for /var/www"
date: 2008-03-22
forum: Server Platforms
---

### Post by vatonerd on 2008-03-22
I don't know how to set the permissions for files and directories on Ubuntu Server so that I can publish files under Dreamweaver and so that the files are visible to visitors.

I installed Ubuntu LAMP successully on a home machine but I could not publish to /var/www using Dreamweaver. So, I chown from root to my username using chown username /var/www. 

I was able to publish to /var/www with dreamweaver, but now I cannot see the files with a browser. 

So I started tinkering with chmod and I can't untangle myself...very confusing. The latest thing I did was chmod 755 /var/www -R.

Can anyone help with with permissions for the directories and the files?

---

### Post by Bachstelze on 2008-03-22
Moved to Server Platforms.

It should be

```
chmod -R 755 /var/www
```

---

### Post by zujik on 2008-03-22
You need to add yourself to the www-data group, change username and usergroup to your username and usergroup (they are usually the same thing but just in case) and foldername to the required folder:

```

sudo usermod -a -G www-data username

```

Check that your listed with the www-data group via:

```
groups
```

The folder "should" be owned by the www-data group but just in case change it:

```
sudo chgrp -R www-data foldername
```

Ensure all new folders created are owned by the www-data group:

```
sudo chmod -R 2750 foldername
```

If Apache needs write access:

```
sudo chmod -R 2770 foldername
```

If I'm wrong, feel free to correct me but that works for me.

---

### Post by vatonerd on 2008-03-23
Thanks for the suggestion. I already did the chown the folder to 755 although my syntax was a bit different. Changed the syntax to your recommendation and still no browser access. Any other ideas?

---

### Post by chuckthorne on 2008-03-24
When I tried to do this I now get the following error
sudo: /var/run/sudo writable by non-owner (040720), should be mode 0700

what should I do?

---

