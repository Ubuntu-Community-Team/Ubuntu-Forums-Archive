---
title: "Help: Apache+WebDav+LDAP+OpenSSL"
date: 2010-11-29
forum: Server Platforms
---

### Post by justagangsta on 2010-11-29
Hello. 

I am working with a student organization that hosts its own websites on an Ubuntu server. We have massive storage sharing needs, and DropBox isn't enough. 

We are trying to set up a locally hosted form of DropBox, using Ubuntu 8 LTS, Apache, Webdav and NetDrive. We also want to use LDAP to manage access to WebDav. OpenSSL is also something we'd like to implement. 

However, we have never done something like this before and were wondering if this is really the way to go, or are there better solutions for what we need? 

If it is, we would like som pointers on how to set up Ubuntu+Apache+WebDav+LDAP+OpenSSL. What do we need to know? Are there any books or guides you know of that can be recommended? 


Regards, 

Nadeem Q.

---

### Post by SeijiSensei on 2010-11-29
I'd start simply.  Install apache and make sure you can connect to it.  Then try configuring the DAV share.  The instructions for [mod_dav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") are pretty easy to follow.

If the LDAP server exists already, you can use [mod_authnz_ldap]("http://httpd.apache.org/docs/2.2/mod/mod_authnz_ldap.html").  If it doesn't I'm afraid I have to leave that to others.  I've always found LDAP and OpenLDAP too arcane to force myself to spend time learning.

As for SSL, the easiest solution is to use a self-signed certificate.  There are lots of tutorials around on the net about how to set that up.

Do you intend to place each person's website in a separate directory below the common DAV root?  If so, you'll probably want to limit access to each directory to its specific user for security.  .htpasswd files in each directory is easiest solution, but it's safer to put all the access rules in the global WebDAV configuration in /etc/apache2/sites-enabled.

---

