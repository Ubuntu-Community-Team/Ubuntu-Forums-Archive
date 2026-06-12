---
title: "www-data security permissions"
date: 2010-03-17
forum: Security
---

### Post by wavesailor on 2010-03-17
Hi,

I'm running Apache2 under uBuntu 9.10. My problem is that I use my own user "wavesailor" to work on my websites. I kept all my sites under /var/www and I set up the security of the directory after following the guidelines.
```
sudo chown -R root:root /var/www
sudo chown -R www-data:www-data /var/www/*
sudo chmod -R 755 /var/www/*
```
I added the user to the www-data group
```
sudo usermod -a -G www-data wavesailor
```
Which strangely does not show up when you type the command ???```
groups
```
But does show up when you 
```
cat /etc/group | grep www-data
``` as ```
www-data:x:33:wavesailor
```

All good so far I think ... except if I try and copy a file from my Desktop (home directory) or if I try to make a new directory under /var/www/Site1
**What am I missing????**
I want to be able to work as my user (wavesailor) under the /var/www directory without having to sudo all the time.

Regards,
JJ

PS. I know I can create a public_html folder under my home directory and get Apache to use it but I would rather work under /var/www

---

### Post by cdenley on 2010-03-17
First of all, new group memberships do not take effect until you log out and log back in. Secondly, if a directory has 755 permissions, you must be the owner of the directory to create new directories or files within it. I think you want to change that to 775, so member of the www-data group can write to it. I think it would be better to keep it owned by root, but change the group ownership to "admin" if you want your admin users to be able to edit your website without privilege elevation. You don't want to give apache permission to modify your website.

---

### Post by wavesailor on 2010-03-19
Thanks for reply.
> **cdenley said:**
> First of all, new group memberships do not take effect until you log out and log back in. Secondly, if a directory has 755 permissions, you must be the owner of the directory to create new directories or files within it. I think you want to change that to 775, so member of the www-data group can write to it. 
Ok, as I read it, it all makes perfect sense to me (*embarrassed*) - Thanks


> **cdenley said:**
> I think it would be better to keep it owned by root, but change the group ownership to "admin" if you want your admin users to be able to edit your website without privilege elevation. You don't want to give apache permission to modify your website.
I'm keen to know what the "Best Practices" are and use them. Are there any documents out there like that?
I like your suggestion to keep it owned by root and the idea to change the group ownership to I gather a new group called "admin". But if I do that how will Apache which runs as www-data access the files then? Would Apache access them as the public on the 775 then?

---

### Post by cdenley on 2010-03-19
> **wavesailor said:**
> I'm keen to know what the "Best Practices" are and use them. Are there any documents out there like that?
I like your suggestion to keep it owned by root and the idea to change the group ownership to I gather a new group called "admin". But if I do that how will Apache which runs as www-data access the files then? Would Apache access them as the public on the 775 then?

I've never come across a comprehensive list of "best practices". I just follow the principle that you don't want to grant any more permission than is necessary. You don't typically need apache to modify your web scripts/content, so why allow the possibility that an attacker can exploit apache to install malicious code on your site?

775 means the owner (root) and the group owner (admin) has full access to the directory, while everyone else (including www-data, the user apache runs as) can ONLY read, which is all apache should need to do.

In ubuntu, members of the group "admin" are allowed to execute commands as root after providing their password. By default, only the initial user you created at install is a member. If you want to allow admin users to modify files without escalating privileges first, make "admin" the group owner, and allow write permissions for the group owner.

---

### Post by wavesailor on 2010-03-19
Ok - It makes sense. I'm going to implement your suggestions.

Thanks again for the help.

---

