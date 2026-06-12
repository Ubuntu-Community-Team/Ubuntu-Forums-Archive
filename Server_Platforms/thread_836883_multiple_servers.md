---
title: "multiple servers"
date: 2008-06-21
forum: Server Platforms
---

### Post by jamzwebdesign on 2008-06-21
Hi, I am currently using one server running ubuntu server edition to host my website, I am considering running multiple servers e.g: 1 for the mysql database, 1 for apache, how would I go about setting this up? thanks

---

### Post by mbeach on 2008-06-22
build the other server, then run mysql on it, backup your data, then restore on the new server.  Turn off mysql on the first server with something like "sudo /etc/init.d/mysql stop".  

your webapps will continue to run on the first server, but in your apps configuration files, you'll likely be changing 'localhost' to the ip address of the new server.  

In mysql, you'll also need to make sure your users can come from the ip which is running apache instead of just user@localhost (see: [http://dev.mysql.com/doc/refman/5.0/en/privileges.html](http://dev.mysql.com/doc/refman/5.0/en/privileges.html)).  You'll also likely need to edit the /etc/mysql/my.cnf file to listen to requests from the server with apache [probably by commenting out the bind-address line, or setting it to only listen to the apache server depending on your needs].

---

