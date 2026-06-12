---
title: "Web server permission issue"
date: 2011-04-11
forum: Server Platforms
---

### Post by Chamwiz on 2011-04-11
So I've recently decided to make a website for my reenacting unit.  The site is far from completion, however instead of using a hosting company for the site, I thought I would just make my own web server at the house and use that.  Currently I just have the server running on my home network.  I install Ubuntu server edition 10.10.  Installation went well.  I can access the server using it's static ip address.  And use the server via ssh.

Whenever I would open a web browser and type in the computers ip address, it would load the index.html file, but it wouldn't load all the css I wrote for it.  Also, when I tried to use the links to different pages like photos.html.  I got and "Forbidden: You do not have permission to access /photos.html on this server.".

I decide edit the default file in /etc/apache2/sites-available so that the DocumentRoot and Directory pointed to /home/me/www.  The goal of this was hopefully to change the permissions and allow me to view other pages.

Unfortunately now I get "Forbidden: You do not have permission to access / on this server."

I've been using ubuntu desktop for 2ish years now.  Though this is my first time trying to use the server edition.  If anyone has an idea as to my problem with this server, I'd appreciate any help you can offer!

---

### Post by Ryan Dwyer on 2011-04-11
At first glance it looks like the Apache user (www-data) doesn't have access to read your files, but that's strange because everything in /home/yourname/ is world readable unless you changed the permissions.

You should check /var/log/apache2/error.log to see why it's serving up forbidden errors.

---

### Post by Chamwiz on 2011-04-11
Well, after messing with permission for /var/www, I've been able to successfully host the website.  However, I still get the Forbidden error from my home folder.

This is the what has flooded the error.log for apache:
```
[Mon Apr 11 19:25:50 2011] [crit] [client 192.168.1.100] (13)Permission denied: /home/welsh/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

Not 100% sure what this means, although I do know that I do not have a htaccess file in either /var/www or /home/welsh/www.

---

### Post by Doug S on 2011-04-11
If you use all default apache2 configuration files, then if you make a directory at /home/welsh/public_html , it should automatically be available via the relative address "./~welsh/index.html" within your index.html page at /var/www/index.html Or any other page that you can already navegate to. The absolute address [www.yoursite.com/~welsh/]("http://www.yoursite.com/~welsh/") should also work from anywhere.
 
It is on purpose that you should not normally be able to access your home directory. If you made configuration file changes so that you expect to be able to access non standard directories, then we need to check your .htaccess requirements settings (and I have not reminded myself about them yet and for this reply).
 
Edit: The users public_html directory is NOT available by default. The userdir module has to be enabled first with "sudo a2enmod userdir" and, of course, "sudo /etc/init.d/apache2 restart".

---

### Post by Chamwiz on 2011-04-11
Thanks for the reply!  I'll try the html_public folder tomorrow after my classes.

---

### Post by Chamwiz on 2011-04-12
Well, I just figured out my /home/me/www problem.  My friend informed me that it was most likely because I encrypted my home folder :-P

---

### Post by imac_89 on 2011-04-12
That could do it. Still having the permissions issue?

---

### Post by Chamwiz on 2011-04-12
Thankfully no, I was about to set default in sites-available to /home/me/www and it works fine now.  I want to thank everyone for their help.  Now if anyone knows a really easy to follow postfix setup, that'd be awesome! lol.

---

### Post by imac_89 on 2011-04-12
Wow, I see what you mean: [https://help.ubuntu.com/10.10/serverguide/C/postfix.html](https://help.ubuntu.com/10.10/serverguide/C/postfix.html)

It seems rather involved at first glance, but maybe if you broke it down? #-o

---

### Post by Chamwiz on 2011-04-12
Yeah, my main problem is that when I install postfix, it doesn't install correctly, so I can't even perform the following line:
```
sudo dpkg-reconfigure postfix
```
lol, so I'm lost.

---

### Post by imac_89 on 2011-04-13
So the install from apt-get didn't work?

Does your console just spit out that it can't find the command?

---

### Post by Chamwiz on 2011-04-13
It would run through the install and at the end it would tell me that there were errors while installing postfix.  After which I would try the dpkg-reconfigure on it, and it would tell me that postfix was broken or not fully installed.

However, I went through and edit the main.cf file, and when I perform:
```
sudo /etc/init.d/postfix start
```
My terminal told me that it has started correctly.  Unfortunately, I don't know how to test it to see if it is actually working or not.  Any ideas?

---

### Post by imac_89 on 2011-04-13
Although I am not entirely familiar with postfix setup and install, there is a way to test it.

[https://help.ubuntu.com/community/PostfixBasicSetupHowto#Test your default setup]("https://help.ubuntu.com/community/PostfixBasicSetupHowto#Test your default setup")

I hope this is of some help.

---

### Post by Chamwiz on 2011-04-13
Yes, that helped wonders! Thank you.  And it looks as though my postfix is running.

---

