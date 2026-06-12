---
title: "Apache Setup Questions"
date: 2015-02-23
forum: Server Platforms
---

### Post by RavenLX on 2015-02-23
I'm having a hard time getting aquainted with the Apache Documentation. It is hard to understand it all and so much to look through. I have to get a server going soon and really don't have time to look through everything. (Even then I tend to miss a lot of info.) So I thought I'd ask here.

The server is a virtual host system, hosting several domain names.

1. Can apache run as different users (ie. run as several domain names)? Or is it best to add each domain to an apache group? (Reason I ask this is sometimes webmasters want to remove files that a php script created and find they can't because they don't have the permission).

2. How can I make sure an .htaccess file is usable even if it's in a sub direcectory of the domain's main directory?

3. Which takes precedence, the main apache.config (or is it apache2.conf?) file or the domain's configuration file in sites-enabled? Can I override a setting from apache.conf by setting it differently in sites-enabled? Reason I ask this is I would like to have a default setup and then further enable or limit those settings per-domain.

4. Is adding libapache2-mod-defensible a good idea or will fail2ban be better? (I don't know too much about these and I'm trying to keep things efficient and not too redundant unless it's necessary).

Thanks for any help that anyone can give me.

---

### Post by Lars Noodén on 2015-02-23
> **RavenLX said:**
> 1. Can apache run as different users (ie. run as several domain names)? Or is it best to add each domain to an apache group? (Reason I ask this is sometimes webmasters want to remove files that a php script created and find they can't because they don't have the permission).

Apache runs as the user www-data in the group www-data.  That can be changed for specific virtual hosts using [SuExecUserGroup](http://httpd.apache.org/docs/2.4/mod/mod_suexec.html#suexecusergroup).  But be careful that Apache cannot write to any files or directories containing scripts.  If you want various web masters to be able to write to their DocumentRoot to edit files, then that is done in the file system instead.  


If you are going to be the only user of the directory, then you can simply take ownership of it and that will be that:


```

sudo chown -R ravenlx /var/www/vhost1/

```

If you are going to be sharing access to the folder with a bunch of people, then you can set up group access.

```

sudo addgroup webhost2
sudo chgrp -R webhost2 /var/www/vhost2/

sudo find /var/www/vhost2/ -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www/vhost2/ -type f -exec chmod g=rws "{}" \;

# repeat for each user:
sudo gpasswd --add ravenlx webhost2

```

That will allow any user in the group 'webhost2' to edit the website found in /var/www/vhost2/

---

### Post by RavenLX on 2015-02-23
Please forgive me if I'm rather confused.

(NOTE: I'm re-editing my post so that I hopefully am more clear.)

I've got a hosting system I'm setting up where each domain will have it's own directory in /var/html (ie. /var/html/thisdomain.com, /var/html/thatdomain.net, etc.) Each owner of the domain can ***only*** upload/download/delete/modify the files via FTP (proftpd server).

Problem:

1. I want to make sure that the scripts can write to the domain's root directory (ie. /var/html/thisdomain.com) and sub-directories but not be able to touch another's (ie. scripts in /var/html/thisdomain.com should not be able to write in /var/html/thatdomain.net's root or sub directories).

2. As mentioned, scripts will need to write but the domain owners need to be able to remove those files that scripts write and be able to do so via FTP.

That is what I'm facing with Question #1 in my OP. Would also like answers to the other questions as well, if anyone knows how to solve those problems too.

---

### Post by Lars Noodén on 2015-02-23
1. I would use the method described in #2 above and create a separate group for each web site and then add users to each group as appropriate.  It will then be the write permissions at the group level that determine who can write to any given directory.  

2.  I can't help with [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  If it were my machine and I did not want shell access, I would set up SFTP-only accounts instead can chroot them to a specific vhost's directory.  In that way they cannot get shell access but can use SFTP but only in their website's directories.  Unless you are setting up virtual users there are few to no other use cases for FTP in 2015.

---

### Post by RavenLX on 2015-02-24
Thank for the information. Not sure if I understand fully, but it does give me some ideas on permissions. Not exactly what I was looking for though.

I still do have unanswered questions from my first post.

---

### Post by RavenLX on 2015-02-24
Looking at it again, #2 won't work. Because scripts will still be writing as group www-data when I would want them to be domain.com for example.

---

### Post by Lars Noodén on 2015-02-24
> **RavenLX said:**
> Looking at it again, #2 won't work. Because scripts will still be writing as group www-data when I would want them to be domain.com for example.

Only web-based scripts would run as group www-data, but even that is avoidable.  You can use [SuExecUserGroup](http://httpd.apache.org/docs/2.4/mod/mod_suexec.html#suexecusergroup) in each vhost to run the web-based script as whichever user or group you like.

---

### Post by Lars Noodén on 2015-02-24
> **RavenLX said:**
> 2. How can I make sure an .htaccess file is usable even if it's in a sub direcectory of the domain's main directory?

Make sure that the directory and .htaccess are readable, but not writeable, by the web server.  Then make sure that the specific directory has or has inherited the [overrides](http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride) that you want users to be able to choose, from among the subset allowed by .htaccess.  If there's a way to avoid .htaccess, then that way is better.

---

### Post by Lars Noodén on 2015-02-24
> **RavenLX said:**
> 3. Which takes precedence, the main apache.config (or is it apache2.conf?) file or the domain's configuration file in sites-enabled? Can I override a setting from apache.conf by setting it differently in sites-enabled? Reason I ask this is I would like to have a default setup and then further enable or limit those settings per-domain.

As far as I know, the vhosts take precedence if they have different settings than the default.  Any particular settings in mind?

---

### Post by RavenLX on 2015-02-25
Thank you for all your help. Very good information and answered all my questions. I think I have an idea now how I will go about things. The .htaccess thing is a little more confusing but will try and figure it out (I learn best by watching things work). If not I'll post my findings in the forum. But everything else was answered. I think I'll go with the [SuExecUserGroup]("http://httpd.apache.org/docs/2.4/mod/mod_suexec.html#suexecusergroup") idea after all as that looks like the only way to do what I'm trying to accomplish.

---

