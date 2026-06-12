---
title: "Symlink help?"
date: 2011-01-18
forum: Server Platforms
---

### Post by DanHorniblow on 2011-01-18
I am running an ubuntu home web server. I am trying to get my dropbox files to sync to a directory within my web root so I can access them with a PHP file manager.

So far I have got the file manager up and running, I have also got dropbox installed and syncing perfectly.

But dropbox by default syncs to "/home/user/Dropbox". Would it be possible to create a symlink between the bropbox folder and my file manager directory to save the hassle of altering config files file of dropbox?

---

### Post by volkswagner on 2011-01-18
> **DanHorniblow said:**
> I am running an ubuntu home web server. I am trying to get my dropbox files to sync to a directory within my web root so I can access them with a PHP file manager.

So far I have got the file manager up and running, I have also got dropbox installed and syncing perfectly.

But dropbox by default syncs to "/home/user/Dropbox". Would it be possible to create a symlink between the bropbox folder and my file manager directory to save the hassle of altering config files file of dropbox?

I'm pretty sure DropBox works with symlinks.

```
man ln
```

The above will show you the man pages for linking... once you digest that, consider something like this.

```
ln -s /var/www/web1/rootfolder /home/user/Dropbox/webroot
```

---

