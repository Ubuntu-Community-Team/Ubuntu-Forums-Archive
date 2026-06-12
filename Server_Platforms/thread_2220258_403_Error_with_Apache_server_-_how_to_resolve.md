---
title: "403 Error with Apache server - how to resolve?"
date: 2014-04-27
forum: Server Platforms
---

### Post by Bobby_James on 2014-04-27
Hello,

I have the following 403 error with a VPS that I rent. This happens on all pages including /

[h=1]Forbidden[/h] You don't have permission to access /index.html on this server.

 [HR][/HR] Apache/2.4.9 (Unix) Server at [http://www.whatever.com](http://www.whatever.com) Port 80


Since I rent, I do not have access to any logs. I only have the public_html directory plus the squirrelmail, etc.

I searched around and the main ideas was to edit the .htaccess file. However, I don't have such a file and everything used to work.
[SIZE=2]
Any other ideas?  I've contacted support but they are pretty slow.


[/SIZE]

---

### Post by Lars Noodén on 2014-04-27
If you have access to the configuration file itself you do not need .htaccess.  That would be redundant.

What about obvious things like the file directory permissions?   Check what they are for the document root:

```

ls -ld /var/www

```

Or whatever the right directory is for you. 

It would really help if they could provide you access to the log files.

---

### Post by Bobby_James on 2014-04-27
At the risk of sounding ignorant, by "configuration file", do you mean the html / php / whatever files which I can write and control?

The chmod permissions are 711 for directories. Again, I've not changed anything from when it worked.

When you ask me to ls -ld /var/www, how am I supposed to do that?  I've only accessed the website via logging in and looking at the file manager.  How would you suggest I do it?  Also, as far as I am aware, I don't have access to /var/www. The only directory I see in the file manager is /public_html.

I would be grateful if you could you please explain in more detail. Many thanks!

---

### Post by Lars Noodén on 2014-04-27
I had thought that you had a VPS with proper shell access.  Shell access is about the only way, in the long run, to manage a server.  The configuration file would be for Apache 2 on Ubuntu would be in /etc/apache2/sites-enabled and would tell you where Apache is looking for your files.  In Ubuntu, that defaults to /var/www but it looks like your server is customized a bit so the configuration file would tell where you should look.  

About using ls that would be done via your login account at the VPS.  However, since that is not how you have been accessing your server so far, can I ask what methods do you have available to check on it or configure it?

---

### Post by Lars Noodén on 2014-04-27
711 for the directories should work.  Are the parent directories set similarly? Are the files in the web directories 644 or something like that?

---

### Post by Bobby_James on 2014-04-27
The files are 644.

The only way I have thus far accessed the server (perhaps it is not a VPS - just hosting from a company) is via HTTP - login then use file manager / web mail / check statistics / etc.

When you mention the "login account at the VPS" are we talking about SSH here?

Thanks again!

---

### Post by Lars Noodén on 2014-04-27
Yes, SSH is a great way to access the server.  It also means easy ways to provide help in a forum.  But it sounds like you are using a web-based interface.  

If it's not a VPS maybe you have shared hosting.  What is it called on the product description page?  There might be a way to get error logs, but if not you will probably have to rely on their technical support.  Did any .htaccess files get added by mistake?  Those can override server settings and get in the way.

---

