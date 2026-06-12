---
title: "Apache Forbidden 403 Easy Fix?"
date: 2010-06-14
forum: Server Platforms
---

### Post by ChrisEiffel on 2010-06-14
I am using the Desktop Version of Ubuntu Lucid Lynx, but I am posting here because I think all of you server guru's can help me. I am setting up my desktop as a mobile development server. I am hoping to eventually have it work with an intranet. Anyways I am trying to configure this and I hit a snag.  

I have a 403 forbidden error. I've read around and I thought it might have something to do with SELinux

Here is my Virtualhost file 

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName starace
        DocumentRoot /home/chris/public_html
        DirectoryIndex index.html index.php
        <Directory "/">
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory "/home/chris/public_html/">
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /home/chris/cgi-bin/
        <Directory "/home/chris/cgi-bin/">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /home/chris/logs/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /home/chris/logs/access.log combined

</VirtualHost>

```I was wondering if everything is set up correctly in the configuration file to allow access to the starace document directory?

I have added this to the sites enabled using the a2ensite command. The logs appear to be working just fine. 

I have an index.html in the /home/chris/public_html/

I added starace to the /etc/hosts/

Both the public_html and index.html have read permission
ls -l:  -rwxr-xr-x 1 chris chris 6 2010-06-08 15:30 index.html
and
drwxr-xr-x 2 chris chris 4096 2010-06-14 02:04 public_html


I go to [http://starace/index.html](http://starace/index.html) and I get 
**Forbidden**

 You don't have permission to access /index.html on this server.
  Apache/2.2.14 (Ubuntu) Server at starace Port 80


The error log tells me 
[Mon Jun 14 02:43:03 2010] [error] [client 127.0.1.1] (13)Permission denied: access to /index.html denied

Why am I getting a 403? How can I set the permissions to allow the content to be shown?

Thanks

---

### Post by Bachstelze on 2010-06-14
Make sure /home/chris also has read and search permission.

---

### Post by ChrisEiffel on 2010-06-14
Wow, it was as easy as chmod o+x /home/chris

I guess apache not only needs the Document Root but all parent directories to have execute permission as well. I knew it was an easy fix! Thanks!

---

### Post by Ryan Dwyer on 2010-06-14
For future reference, you can usually figure out what's wrong with Apache by checking /var/log/apache2/error.log.

---

### Post by Bachstelze on 2010-06-14
> **ChrisEiffel said:**
> Wow, it was as easy as chmod o+x /home/chris

I guess apache not only needs the Document Root but all parent directories to have execute permission as well. I knew it was an easy fix! Thanks!

Not only Apache but any process. ;) Otherwise, it's like saying "You can go in my kitchen but not in my house."

---

### Post by robsoles on 2010-09-20
<snip>LOL, first snip in ages and it is because I have posted to the wrong thread - this thread is referenced from where I was trying to post - [http://ubuntuforums.org/showthread.php?t=1578209](http://ubuntuforums.org/showthread.php?t=1578209)</snip>

---

