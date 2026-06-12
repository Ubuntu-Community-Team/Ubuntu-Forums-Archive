---
title: "Unique server/samba configuration"
date: 2007-09-09
forum: Server Platforms
---

### Post by galeron on 2007-09-09
Hey guys,

I'll be moving into my new house in 3 months time and I'll be running Ubuntu with Samba as my fileserver.

I'd like to have a configuration similar to the following:
- Each user has their own home directory, for example /home/james
But,
- Inside the /home/james folder, I'd like to have the following folders:
     - public (similar to Mac OS X's public dropbox)
     - private (which should have been the original /home/james protected folder
     - www (where all files put in this folder will be accessible from the web)

My question is, how do I configure Samba for such folder permissions?
Secondly, is it possible to have Apache automatically use the /home/james/web folder as a web directory, such that [http://localhost/~james/](http://localhost/~james/) points to /home/james/www?

If it helps, none of the users will need to access the fileserver locally or through SSH, only through Samba.

Thanks!

---

### Post by HermanAB on 2007-09-09
You are pretty much describing the default configuation of Samba.

---

### Post by galeron on 2007-09-10
Hm...really? 

I was under the impression that the special [homes] directive in the Samba configuration provides for private folders only, not web-accessible (which I do admit might be more Apache than Samba) and public dropboxes, similar to what Mac OS X has?

---

### Post by koenn on 2007-09-10
- public (similar to Mac OS X's public dropbox)

can't you just do that by making a 'public' directory in your home dir and  chmod it so that its writable by everyone ? You may have to look into modes (fs permissions) and samba permissions to let others reach that subdirectory through the share / parent directory but  it's probably doable

- private (which should have been the original /home/james protected folder

likewise, make a 'private' subdir,give ownership to james (chown james:james /home/james/private ) and take away all permissions from 'others' (or chmod 770 /home/james/private )

- www (where all files put in this folder will be accessible from the web)

I don't think samba offers web access, you'll need a web server (apache, lighttpd, ....) and point its doc root to /home/james/www


... or something along those lines. Haven't tried it, never done anything like it, use at own risk, no warranty.

---

### Post by galeron on 2007-09-11
Hey,

Based on my understanding, the [homes] configuration would look something like this:
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750

So the way I see it, I could have a private folder, but not the public dropbox, because I can't make Samba automatically recognise that the public folder is meant to be world-writable.

Or am i mistaken?

---

### Post by lolocaust on 2007-09-11
You could make /www/ in each users' home symlink to /www/~user/ then in a web browser if you type /~user/ after the url apache should load the corresponding user's pages, without having to mess with apache's config.

---

