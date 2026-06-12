---
title: "UserDir mod for Apache2"
date: 2011-03-14
forum: Server Platforms
---

### Post by cosine_omerta on 2011-03-14
I am trying to set it up so that my users each have their own webpages, [www.mydomain.com/userbob/index.html](www.mydomain.com/userbob/index.html).

I've used a2enmod userdir, and it supposedly has enabled that, then I reloaded and restarted apache.

When I try to use the userdir command, i get an error message:
userdir: command not found

What am I missing? It seems straightforward enough to get this to work.  Anybody have a great tutorial or walkthru to getting this to work?

Thanks.

---

### Post by cosine_omerta on 2011-03-15
Ubuntu server 10.10 64 bit. If I try to enable it, it will say already enabled. I have disable and re-enabled it.  I still get userdir: command not found. Anybody?

---

### Post by cosine_omerta on 2011-03-15
Ok, so let's approach this differently. 

If I wanted to set up my webserver to allow each user to have their own web pages, and have it set like [www.myserver.net/userbob/index.html](www.myserver.net/userbob/index.html) and [www.myserver.net/userjanet/index.html](www.myserver.net/userjanet/index.html), how would I do that?

Ubuntu Server 64 10.10, apache2.

---

### Post by Lars Noodén on 2011-03-16
> **cosine_omerta said:**
> I am trying to set it up so that my users each have their own webpages, [www.mydomain.com/userbob/index.html](www.mydomain.com/userbob/index.html).

I've used a2enmod userdir, and it supposedly has enabled that, then I reloaded and restarted apache.

When I try to use the userdir command, i get an error message:
userdir: command not found

What am I missing? It seems straightforward enough to get this to work.  Anybody have a great tutorial or walkthru to getting this to work?

Thanks.

usedir is a module for Apache to work with, not a program that you run from the shell.

userdir will let you have URLs like the following which point to a directory within the users' own home directories:
```
http://example.com/~*cosine_omerta*/
```

You might need to create the directory for Apache to find in the users home directory.

---

### Post by cosine_omerta on 2011-03-16
From what I read the userdir command allows me to enabled and disabled which users I wanted to have the mod work with.

And when I activate the mod, all of my users are just in the [www.myserver.net/index.html](www.myserver.net/index.html), overlapping each other.

---

### Post by Lars Noodén on 2011-03-16
[Apache's userdir module](http://httpd.apache.org/docs/2.2/mod/mod_userdir.htmlhttp://httpd.apache.org/docs/2.2/mod/mod_userdir.html) maps urls to a subdirectory within the user's home directory.  There is a [tutorial](http://httpd.apache.org/docs/2.2/howto/public_html.html), but it's quite easy once you figure it out.

Externally, the URLs are something like this:

[http://www.example.com/~foobar](http://www.example.com/~foobar)

Internally the folder is something like this:

/home/foobar/public_html

The exact path is in your Apache configuration file and set by the directive [UserDir](http://httpd.apache.org/docs/2.2/howto/public_html.html#userdir), so look in your Apache configuration file(s) to see what you have.

---

### Post by Lars Noodén on 2011-03-16
> **cosine_omerta said:**
> From what I read the userdir command allows me to enabled and disabled which users I wanted to have the mod work with.


Again, that would be done inside your Apache configuration file, not in the shell.  Inside the web server configuration, you can [set which users are allowed to use UserDir](http://httpd.apache.org/docs/2.2/howto/public_html.html#enable)

---

### Post by cosine_omerta on 2011-03-16
I'm an idiot. Thanks for clearing that up.  The syntax was so simple it made me think it was a command not a line in the conf file.

I do have another question though.  I have 2 users, myself and janet, and I have userdir configured and working, with 2 virtual hosts for my webpages and one for janet. I don't want my webpages to need /~myname/ on the url, but I want janet's to require it.

When I put my user name in the disabled, and janet in the enabled, if you leave off the /~janet/ part, it will still find her pages. [www.myserver.net/janetsindex.html](www.myserver.net/janetsindex.html) will pop up just as will [www.myserver.net/~janet/janetsindex.html](www.myserver.net/~janet/janetsindex.html).

Is this how it's supposed to work? Or am I doing something wrong again? Is there a way to make it require the /~janet/ to get to her pages?

Thanks again.

---

### Post by dominic007 on 2011-04-26
Hello,

I have set up an Ubuntu server on an old pc. It’s a school excersise. I have on it installed: apache2, vsftpd, php5, ssh, vim. We should make a webserver where students can put there website on by ftp and then could launch it local. I got it working, so if you go to [http://80.101.134.200/~testuser](http://80.101.134.200/~testuser) you get the testuser his own directory. In that directory is a file and you should be able to read that file (You can try the link, I opened one port). You shouldn’t have to login or something like that, but when I go to that html file is says the following:
Forbidden
You don't have permission to access /~testuser/steph en daan jael2.html on this server.

Apache/2.2.16 (Ubuntu) Server at 192.168.178.8 Port 80

Please help me. How can a user login or how can I give everyone the readpowers. 
Im very sorry for my bad english.
Greetz,

Dominic

---

### Post by dominic007 on 2011-04-26
I found out that i have to give the directory some right, so everyone can read it. DOes anybody know how to do that?

---

