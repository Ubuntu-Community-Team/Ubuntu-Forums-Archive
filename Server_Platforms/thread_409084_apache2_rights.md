---
title: "apache2 rights"
date: 2007-04-14
forum: Server Platforms
---

### Post by Petar Marjanovic on 2007-04-14
Aloah

My problem is very old: I want to install Apache2 in (K)Ubuntu. This morning, I reinstalled Kubuntu and installed the packages apache2 (and others, e.g. mod-php). But now, when Konqueror/Nautilus is in /var/www/, can not create any files. And when I am a s.u., I have to set the new created files always execute rights.

What on earth should I do?

// edit:
Now I can create files in /var/www, but I stil have to be in su-mode. I don't have to set rights (yeah!), but kwrite (kate) I should always open in su-mode.

---

### Post by rmemm on 2007-04-14
You should be able to set standard file permissions the way you do on any other set of files and folders.  I think the only thing special about this is that user that runs the apache server has to have read access to these files.

I looked on my laptop and my /var/www directory is owned by root.root and is rx to all users.  I don't know how much  you know about permissions?  Generally to view directories you need rx permission, but to view files you only need r permission.  

If you want to edit files in /var/www without using sudo -- then you need to change permissions and/or ownership to do this.  You can do this with the chmod and chown command with sudo (see man chmod and man chown or example).  You could also assign them to a new or exisiting group that you are a member of and apply the appropriate group permissions.

Rob

---

