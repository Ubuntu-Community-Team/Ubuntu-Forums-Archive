---
title: "Frustrated, somehow I killed PHP... and everything else"
date: 2008-05-22
forum: Server Platforms
---

### Post by kepardue on 2008-05-22
Okay, so I'm a bit of a cli, server novice here.  I was trying to install a mail server into ubuntu, and noticed the tasksel command listed in the ubuntu marketing docs.  I ran tasksel install mail-server, which started the process, which must have failed because it went away and wouldn't return.  So, I then thought the next logical step would be to run tasksel remove mail-server.  Which subsequently removed apache2, php, mysql, proftpd and probably several vaults of records from the library of congress.

So, I've re-added mysql, apache, and php to the system.  Thank GOD my databases didn't seem to be deleted since they show up in Webmin.  But, when trying to access a page it prompts me to try to download the index.php file as application/x-httpd-php, rather than render it.

I've confirmed in webmin that the php5 module is installed, and that application/x-httpd-php is a mimpe type, with php, phtml, and pht as valid extensions.  I've restarted the server more times than I can count.

What am I doing wrong?  And yes, *smack, smack* on me for just running a command without researching it first and jumping in over my head.

---

### Post by windependence on 2008-05-22
It would be much easier for you to install a prepackaged mail server such as Zimbra collaboration suite. Take it from someone who does this for a living and has built mail severs from scratch, I don't do that anymore, it's just too time consuming. Zimbra installs everything at once and just works.

[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

-Tim

---

