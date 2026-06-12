---
title: "Brainstorm installation problem"
date: 2008-05-08
forum: The Cafe
---

### Post by melat0nin on 2008-05-08
Hi all

I'm installing Brainstorm (actually the qapoll and qawebsite modules for Drupal) on a web server, but I keep getting the following sql errors:

```


    * user warning: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'SIMILAR TO subdomain' at line 1 query: SELECT * FROM qawebsite_site WHERE 'melat0nin.virtual.vps-host.net' SIMILAR TO subdomain in /home/webadmin/melat0nin.virtual.vps-host.net/html/drupal/includes/database.mysql.inc on line 172.
    * user warning: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'SIMILAR TO subdomain' at line 1 query: SELECT * FROM qawebsite_site WHERE 'melat0nin.virtual.vps-host.net' SIMILAR TO subdomain in /home/webadmin/melat0nin.virtual.vps-host.net/html/drupal/includes/database.mysql.inc on line 172.


```

I have installed it mostly using the instructions on this page ([https://wiki.ubuntu.com/Brainstorm/Installation](https://wiki.ubuntu.com/Brainstorm/Installation)) along with some changes because it's not a local machine I am installing on.

Alas there is no instruction there to link the installation with the postgresql database.  I have created the database and a user/pass, but in the absence of any reference to them in the module I can't see how it can 'know' where to get the data from.

Anyone got any ideas?

---

### Post by nand on 2008-05-09
Hi!

No need to specify a password, Brainstorm will use the Drupal database connection. So once you have installed Drupal, you don't have to worry about the database (as long as you follow the requirement, i.e. postgresql 8.2).

Concerning the SQL errors here, it seems the changes you have made on the SQL script have somehow broken them.

For further infos and troubleshooting, I recommend you to pass on IRC at #ubuntu-testing!

---

