---
title: "Secure, http-based (port 443) replacement for ftp?"
date: 2014-01-02
forum: Server Platforms
---

### Post by 1clue on 2014-01-02
Hi,

I have a server on the Internet.  I'm looking for some sort of replacement for FTP and would like recommendations.  It needs to have strong security, multiple users, groups with different authorities and be strictly http.  I have customers who allow http and https only, they won't open ftp or ssh or any of that.

I do NOT want a multi-protocol NAS-type answer.  I want the functionality of a good, secure ftp server but using https.

This is for file transfers, usually database backups containing confidential information.  I want two groups at least:

Employee/admin:  Have read/write access to everything: Common area, employee-only space, customer-specific areas.
Customer:  Has read-only access to a common area, and read/write to their own directory.  Note that each customer gets a separate directory which is invisible to any other customer, but not to employees.

All access must be authenticated, the common area is not for just anyone.

I thought maybe WebDAV on apache, but I can't seem to find any sophisticated access controls.  I don't know enough about how to set it up to really tell.

This could be something free-standing, or on apache2, or maybe Tomcat.  Again, needs to be secure.

Thanks.

---

### Post by SeijiSensei on 2014-01-02
[WebDAV on Apache]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") uses the same [authorization schemes]("http://httpd.apache.org/docs/2.2/howto/auth.html") as ordinary web sites.  Ordinarily I just use "basic" authentication with a [password file]("http://httpd.apache.org/docs/2.2/howto/auth.html#gettingitworking"), but other alternatives like dbm databases and LDAP are also an option.  You can grant permissions by user and group.  

To make it an SSL-secured connection, you would need a certficate.  You can either buy one or distribute a self-signed one to your customers.  Following the example from the Apache site, you would put the <Location> container inside a <VirtualHost *:443> container that includes the [necessary code]("https://help.ubuntu.com/12.04/serverguide/httpd.html#https-configuration") to implement SSL.

---

### Post by 1clue on 2014-01-02
This is good news, it didn't look all that promising from the intro documentation I found.

I haven't decided where to put this yet, I have a couple boxes with ssl certificates already.  Or I might want to put it on something separate and avoid unnecessary risk, in which case I'll just use a self-signed certificate.

Thanks a bunch for the input.

---

