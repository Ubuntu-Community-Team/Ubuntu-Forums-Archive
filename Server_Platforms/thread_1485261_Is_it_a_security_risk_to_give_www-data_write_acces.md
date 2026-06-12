---
title: "Is it a security risk to give www-data write access to /var/www?"
date: 2010-05-16
forum: Server Platforms
---

### Post by allspiritseve on 2010-05-16
I am trying to set up a php script that can automatically run svn update on a subversion working copy on our development server. I have been able to get this to work if www-data owns the working copy files, but not if www-data is member of a group which owns the working copy files. 

My question is, is it a security risk to allow www-data write access to /var/www? If so, what alternatives do I have to allow updates to be triggered by a php script?

---

### Post by allspiritseve on 2010-05-20
I would really appreciate an answer here.

---

### Post by mobilediesel on 2010-05-20
I don't know that there's a security risk but you could also set the web server's document root to $HOME/public_html or another location in your home directory.

---

### Post by allspiritseve on 2010-05-20
> **mobilediesel said:**
> I don't know that there's a security risk but you could also set the web server's document root to $HOME/public_html or another location in your home directory.
I'm not sure how that would change anything. I need to execute svn commands through PHP which means the commands are being executed by user www-data. If I give www-data permissions to write to the document root, no matter where that is, that means any php file could overwrite any file on the server, which seems like a bad idea but I can't figure out how to do it any differently.

---

### Post by tgalati4 on 2010-05-20
Well it's a compromise between security and convenience.  Sugarcrm needs www-data ownership so that the database administrator can update php code through the web browser.  This is convenient but does it does introduce an avenue for exploits.

So in a way, you have answered your own question.  If you want to perform svn actions within a web browser using PHP then apache needs www-data ownership of all files (with the exception of .htaccess) in the web page tree.  I don't know of an alternative way to do it.  And yes, it's possible for a malicious script to mangle the web page.  I'm not sure if the entire server would be at risk.  Normally only files/directories below /var/www need to owned by www-data:www-data.

When I get some time, I will research this issue at sugarcrm.com and the sugar forums to see what others think.

To summarize:  This www-data ownership method is widely used by production software for these types of self-updating actions.  I don't know how risky these methods are.  In sugar's case, the database is only as secure as the administrator's password.  So any web-facing application has to deal with this basic security premise first.

---

### Post by allspiritseve on 2010-05-20
> **tgalati4 said:**
> When I get some time, I will research this issue at sugarcrm.com and the sugar forums to see what others think.
Thanks, I appreciate that. I will do my own research as well and write back here if I find anything.

---

### Post by mobilediesel on 2010-05-20
> **allspiritseve said:**
> I'm not sure how that would change anything. I need to execute svn commands through PHP which means the commands are being executed by user www-data. If I give www-data permissions to write to the document root, no matter where that is, that means any php file could overwrite any file on the server, which seems like a bad idea but I can't figure out how to do it any differently.

Ah, I didn't read your post as clearly as I thought. I'm only running stuff accessible from the internal network so I haven't needed to worry about that kind of security for php. I totally didn't help!

Hopefully tgalati4 can help more than I have. I guess any help at all would accomplish that. :-|

---

### Post by Bachstelze on 2010-05-20
> **allspiritseve said:**
> I am trying to set up a php script that can automatically run svn update on a subversion working copy on our development server.

Why not just do it in a cron job?

---

### Post by allspiritseve on 2010-05-20
> **Bachstelze said:**
> Why not just do it in a cron job?
It needs to be triggered manually. 

[QUOTE=mobilediesel]Ah, I didn't read your post as clearly as I thought.[/QUOTE]
No worries.

---

### Post by tgalati4 on 2010-05-20
Well, there is some debate in the sugar forums about this matter.

The general consensus is www-data:www-data for all files in the sugarcrm mainpage and below otherwise major breakage.  Sugarcrm is entirely PHP-driven.

755 permission for all files except config.php which should be 644.  Don't use 777 as that is a major security risk.

Here's a wiki:

[http://www.sugarcrm.com/wiki/index.php?title=Required_file_system_permissions_on_Linux](http://www.sugarcrm.com/wiki/index.php?title=Required_file_system_permissions_on_Linux)

Your issue is similar in that you need to perform system updates within a PHP-driven webpage.  Normally I would perform such updates by logging in remotely with ssh without using a password but shared encryption keys.  Once inside the ssh session, then you can run your svn scripts.  Of course this is all console-based, but it's more secure then using PHP.  Again it's a balance between security vs convenience.

---

