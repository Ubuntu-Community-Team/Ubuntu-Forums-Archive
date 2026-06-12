---
title: "need help with apache and multiple websites"
date: 2011-03-16
forum: Server Platforms
---

### Post by untenops on 2011-03-16
Sorry I know there are other posts on this subject but I have not been able to figure this out.  I’ve been beating my head on this one.  I have a box loaded with ubuntu server 10.04 with the LAMP package installed.  I have an account with DynDNS to resolve a domain name to my dynamic IP.  I installed Jinzora 3.0 and it was working great.  I could log on from the internet and stream my music.  All I had to do was type in my domain name from DynDNS with /jinzora-3.0.  ([http://xxxx.xxxxx.net/jinzora-3.0](http://xxxx.xxxxx.net/jinzora-3.0))
  I just installed munin so that I could easily check my servers status.
At first I could not get munin to work at all.  I would goto [http://xxxx.xxxxx.net/munin](http://xxxx.xxxxx.net/munin) and my browser would say 403 forbidden.  So I followed the instructions at ([http://www.debuntu.org/how-to-monitoring-a-server-with-munin-p2](http://www.debuntu.org/how-to-monitoring-a-server-with-munin-p2) )  And this got munin to load on my browser.  But only if I go to [http://xxxx.xxxxx.net](http://xxxx.xxxxx.net) without the /munin.  And now I can not go to jinzora.  When I try jinzora it tells me that its a broken link.  How can I fix this?  What did I do wrong?

---

### Post by wongo888 on 2011-03-16
So what did you put into this file?

/etc/apache2/sites-available/monitoring

Read this

[http://httpd.apache.org/docs/current/mod/core.html#servername](http://httpd.apache.org/docs/current/mod/core.html#servername)

---

### Post by untenops on 2011-03-16
This is my monitoring file.

</VirtualHost>
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName      uxxxx.xxxxxxxx.net
        DocumentRoot /var/www/munin
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
                LogLevel notice
                CustomLog /var/log/apache2/access.log combined
                ErrorLog /var/log/apache2/error.log
                ServerSignature On
</VirtualHost>

---

### Post by jmacgowan on 2011-03-16
Read up a bit on the way that apache2 handles sites and you should be able to find your answer.  The problem that you're having apache answer all requests on port 80 with the directory at /var/www/munin
 
Since your jinzora is at /var/www/jinzora, you won't be able to access it.
 
Basically, when you try:
[http://xxx.xxx.net/jinzora](http://xxx.xxx.net/jinzora), apache is trying to open /var/www/munin/jinzora

---

### Post by untenops on 2011-03-16
Thank you
I did as suggested and changed the 

DocumentRoot /var/www/munin
to
DocumentRoot /var/www/

And I can now get to Jinzora, but when trying xxxxx.net/munin I get a 403 Forbidden again.

---

### Post by untenops on 2011-03-16
Ok this is making no sense.  If I can access one directory in /var/www then why can't I get to another directory there?  I changed DocumentRoot to  /var/www/  and I can now get to Jinzora but it tells me that munin is forbidden.  How can it be forbidden when to comes off the root directory?

---

### Post by wongo888 on 2011-03-16
You might want to check your apache error log to figure out why you are seeing 403 errors

---

### Post by volkswagner on 2011-03-16
I'm not sure it it is a copy paste error, but I see a leading
```
</VirtualHost>
```
At the beginning of your monitor-host file.  Is that from an earlier entry for a different host?

Either way, I prefer to use individual host files (as in the apache2 guide sticky at the top of the server forums) for vhosts, rather than sticking multiple hosts in one file.



What are the current file permissions?

```
ls -alt /var/www/munin
```

```
ls -alt /var/www/
```

---

### Post by untenops on 2011-03-16
latest from the error log

[Wed Mar 16 17:03:22 2011] [error] [client 192.168.1.1] File does not exist: /var/www/favicon.ico
[Wed Mar 16 17:03:23 2011] [error] [client 192.168.1.1] File does not exist: /var/www/favicon.ico
[Wed Mar 16 17:03:30 2011] [error] [client 192.168.1.1] client denied by server configuration: /var/cache/munin/www
[Wed Mar 16 17:03:30 2011] [error] [client 192.168.1.1] File does not exist: /var/www/favicon.ico

---

### Post by untenops on 2011-03-16
the </VirtualHost> in my monitor file was a mistake and does not exist in the current file. 
 
As for the permissions

/var/www
total 20
drwxr-xr-x  3 root root 4096 2011-03-16 14:29 munin
drwxr-xr-x  4 root root 4096 2011-03-15 11:25 .
drwxr-xr-x 17 root root 4096 2011-03-03 20:38 ..
drwxr-xr-x 16 root root 4096 2011-03-02 23:11 jinzora-3.0
-rw-r--r--  1 root root  177 2011-03-01 21:13 index.html

/var/www/munin

total 40
-rw-r--r-- 1 munin munin 2346 2011-03-16 17:20 index.html
drwxr-xr-x 3 root  root  4096 2011-03-16 14:29 .
drwxr-xr-x 3 munin munin 4096 2011-03-15 11:56 localdomain
-rw-r--r-- 1 munin munin 2046 2011-03-15 11:56 favicon.ico
-rw-r--r-- 1 munin munin 2555 2011-03-15 11:56 definitions.html
-rw-r--r-- 1 munin munin 1794 2011-03-15 11:56 logo-h.png
-rw-r--r-- 1 munin munin  473 2011-03-15 11:56 logo.png
-rw-r--r-- 1 munin munin 5351 2011-03-15 11:56 style.css
drwxr-xr-x 4 root  root  4096 2011-03-15 11:25 ..

---

### Post by volkswagner on 2011-03-16
/var/www
total 20
drwxr-xr-x  3 root root 4096 2011-03-16 14:29 munin
drwxr-xr-x 16 root root 4096 2011-03-02 23:11 jinzora-3.0


/var/www/munin

total 40
-rw-r--r-- 1 munin munin 2346 2011-03-16 17:20 index.html
drwxr-xr-x 3 root  root  4096 2011-03-16 14:29 .
drwxr-xr-x 3 munin munin 4096 2011-03-15 11:56 localdomain
-rw-r--r-- 1 munin munin 2046 2011-03-15 11:56 favicon.ico
-rw-r--r-- 1 munin munin 2555 2011-03-15 11:56 definitions.html
-rw-r--r-- 1 munin munin 1794 2011-03-15 11:56 logo-h.png
-rw-r--r-- 1 munin munin  473 2011-03-15 11:56 logo.png
-rw-r--r-- 1 munin munin 5351 2011-03-15 11:56 style.css
drwxr-xr-x 4 root  root  4096 2011-03-15 11:25 ..[/QUOTE]

I'm no expert on file permissions, but Apache2 operates under www-data.

So www-data needs access to the files.  You can change the owner or group. If apache only needs read access to the files, group should be ok.

I would change munin folder to group www-data.

```
sudo chown -R munin:www-data /var/www/munin
```

Or if munin is a group already you could add www-data to the group munin.  More than one way to skin a cat, but I don't know the most secure way.

---

### Post by BkkBonanza on 2011-03-16
Your permissions appear to be ok. They're not ideal but having the other user with read should work.

That error log line with /var/cache/munnin/www looks suspicious though. Are you using some sort of caching? If so, and you changed the doc root it may have a side effect where apache is trying to hit the cache and it's mis-matched to the new root. You may need to reset whatever is going on there. Perhaps deleting files in the cache to force a rebuild.

Normally you don't get lines referencing /var/cache... but I'm not familiar with caching options there.

---

### Post by wongo888 on 2011-03-16
I took a look at that tutorial and it looks dodgy. I have no exp with this app but it is installed as a regular deb package, so it is probably made to run off a subfolder. The nonsense with the name-based virtualhost set up attempts to move the generated html reports to a different folder so that a machine name (ie. monitoring) can access it. That's probably where all your permission issues arise. This mod seems pointless to me since the exact same reports are available under a subfolder.

If I were you, I'd undo the tutorial changes and just run it as a subfolder off the main default webroot. It may not look as cool, but at least it will work.

---

### Post by untenops on 2011-03-17
Ok first I want to thank everyone for all the help.  

I got this thing working.  Here is what I had to do, 
First a lot more googling and reading, :)
then a line in the /etc/apache2/conf.d/munin file needed to be changed.

Alias /munin /var/cache/munin/www
to this:
Alias /munin /var/www/munin

now it all works.

Oh and wongo888 I did do what you said and undid all the goofy tutorial changes.  

Thanks again everybody.   :D

---

