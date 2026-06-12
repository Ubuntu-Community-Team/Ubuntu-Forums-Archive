---
title: "Apache Confusion"
date: 2006-07-22
forum: Server Platforms
---

### Post by uncleclinto on 2006-07-22
Hey peeps,

I'm the new proud owner of an Ubuntu computer complete with LAMP stack server installed.  I have Samba up and running, and I can see my Ubuntu Compy from my Windows boxes.  I'm all ready to begin the migration of website files from my WAMP server to my new LAMP server, but I have a problem.  

How do I configure Apache?  I need to tell it where to look for my Web Site files etc.  On my WAMP server, I acomplished this by editing httpd.conf.  That file is largely empty on my Ubuntu machine and says something about etc/apache2/mods {available,enabled}.  Do I need to find something in those folders to tell apache where to point for my web files etc.?  Is there a Linux-specific (or better yet Ubuntu-specific) tutorial out there with an explanation of how to do this (preferably with lots of screenshots)?](*,)

---

### Post by jordilin on 2006-07-22
take a look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by uncleclinto on 2006-07-22
Yes, I've had that thing open on my screen all day.  I've determined that apache's default webroot folder on Linux is var/www.  So I moved all of my files there, typed 127.0.0.1 in my browser window and got that index of my files.  I can even see my page named "index.htm" in the list!  Why o why did it default to an "index" instead of index.htm?  I don't think I'm a complete moron when it comes to serving up websites.  I've been doing it on a windows box for years.  What am I missing here?](*,)

---

### Post by scxtt on 2006-07-22
there are certain definitions in your apache2.conf that reference which extensions are used ... .htm might not be defined by default - but i think .php is, for example ... i'd get you better info (the line in the file), but i have apache2 installed on a VM and can't start it up right now :p

and remember to restart apache2 anytime you make changes to the config [ sudo /etc/init.d/apache2 restart ]

---

### Post by uncleclinto on 2006-07-22
Good call.  My apache.conf file does not recognize index.htm.  Unfortunately (though I am logged in as the administrator) I can't save changes to that file.  Do I have to use some tricky command line covert linux way in instead of just clicking on the darn file in the etc folder in order to have admin privileges??;)

---

### Post by scxtt on 2006-07-22
you can do either:
[indent]**sudo vi /etc/apache2/apache2.conf**[/indent]
- or -
[indent]**gksudo gedit /etc/apache2/apache2.conf**[/indent]

to gain admin priv. to edit the file ...

there's also a KDE version, if you need it - and i'm only 75% sure that's where apache2.conf is, but looks like you know where it is already :p

---

