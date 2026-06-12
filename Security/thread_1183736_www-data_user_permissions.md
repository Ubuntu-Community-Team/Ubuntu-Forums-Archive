---
title: "www-data user permissions"
date: 2009-06-10
forum: Security
---

### Post by ene_dene on 2009-06-10
I'm playing with configuration of my web page. I'm not really sure that permissions should I give to www-data user.
I put my pages to /var/www. First of all, who should be the owner of web pages? www-data user, or some normal user?
As I understand www-data user is the one surfing on my site, but if I make him the owner he should, in theory, be able to do anything with that site. But how can he do that in practice by using http protocol? For example, I made a php script that makes thumbnails of pictures in site directory. Data needs to be saved in some directory (for example /var/www/site/thumbnails), for that I need to give ownership/readwrite permissions to www-data user of that directory. But I'm afraid that there exists a way that someone could use that directory how ever he wants since www-data user has all the rights.

How is that done in practice? I know that enabling the users read/write permissions has negative repercussions no security, but I just want to make script that read/writes in some directory when www-data users connects to my site.

To give a even more simple example let's say that my site is in directory:
/var/www/site
I just have a simple index.html inside that directory. The owner of directory and file is www-data user.
Is this example a security risk, is there a way for other users to write/delete this directory, since they are connecting to my site as www-data users (that is apache is using that user to do its work)?

---

### Post by cdenley on 2009-06-10
Visitors to your site shouldn't be able to modify anything regardless of permissions unless you install a script for that purpose. Security with permissions becomes a concern with the possibility that one of your scripts has a vulnerability which can be used by a malicious user to modify files or directories in ways that you did not intend, then run malicious scripts created by himself or simply deface, destroy, or infect your site.

It also becomes a concern with the more unlikely possibility that an attacker discovers an unpatched vulnerabilitiy in apache itself which allows the attacker to modify your files. In this hypothetical scenario, these malicious file operations would be done with the permissions of the www-data user.

Having /var/www owned by root is the safest, since it is the most protected user account. Of course, you might have to make exceptions if you need scripts to write to directories. If your user account is compromised and you own /var/www, your entire site can be compromised.

---

### Post by ene_dene on 2009-06-10
> **cdenley said:**
> Visitors to your site shouldn't be able to modify anything regardless of permissions unless you install a script for that purpose. Security with permissions becomes a concern with the possibility that one of your scripts has a vulnerability which can be used by a malicious user to modify files or directories in ways that you did not intend, then run malicious scripts created by himself or simply deface, destroy, or infect your site.

It also becomes a concern with the more unlikely possibility that an attacker discovers an unpatched vulnerabilitiy in apache itself which allows the attacker to modify your files. In this hypothetical scenario, these malicious file operations would be done with the permissions of the www-data user.

Having /var/www owned by root is the safest, since it is the most protected user account. Of course, you might have to make exceptions if you need scripts to write to directories. If your user account is compromised and you own /var/www, your entire site can be compromised.
Thank you very much, this is exactly the answer I hoped to get.

---

