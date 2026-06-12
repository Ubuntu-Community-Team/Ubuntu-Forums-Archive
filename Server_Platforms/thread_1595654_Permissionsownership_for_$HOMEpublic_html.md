---
title: "Permissions/ownership for $HOME/public_html"
date: 2010-10-13
forum: Server Platforms
---

### Post by memilanuk on 2010-10-13
Hello,

Basic server install of Ubuntu 10.04.1 LTS on an older PC.  Setup LAMP and webmin, can get to default web page, webmin & phpadmin control pages, but having a little trouble with user web pages under /home/*/public_html.  Right now, for my default user (i.e. the one who can by default use sudo for sysadmin work) their home directory ownership is user:admin, and the least permissions that I can get away with and still browse web pages inside /home/user/public_html is 0751.  Is there a way, by either adding the user to another group (say, www-data) or another combination of permissions that would allow me to have things a little more locked down?  What is considered a 'correct' or normal setup as far as which group the directories (both /home/user and /home/user/public_html) should belong to, which group(s) the user should be apart of, and what the permissions on both directories should be?

TIA,

Monte

---

### Post by memilanuk on 2010-10-16
btt

---

### Post by James78 on 2010-10-16
Webmin's normal permissions for /home/user are 0750. Webmin also automatically adds www-data user to users group, this giving Apache read only access to your files (enough in most cases, but permissions can be increased to allow group writing if needed)

You can modify how Webmin sets the servers up however in the Server Templates (in Virtualmin)

---

