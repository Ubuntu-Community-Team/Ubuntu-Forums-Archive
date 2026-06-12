---
title: "Can't get apache to listen on port 8000"
date: 2009-06-11
forum: Server Platforms
---

### Post by el.otro on 2009-06-11
I've recently installed Ubuntu Server 9.04 on a Pentium III (447 MHz) to run LAMP, the system runs very stable and makes FTP transfers alright, the only thing is, I want Apache to listen on port 8000, an I can't get it to do so.

Now, at first I thought I had done something wrong because the http.conf file was blank, I googled around to find that I should be using the apache2.conf now, so I changed the following files (all in /etc/apache2) :

*httpd.conf* > added a line ```
Listen 8000
```*ports.conf* > changed ```
Listen 80
``` to ```
Listen 8000
```and

```
NameVirtualHost *:80
``` to ```
NameVirtualHost *:8000
```*./sites-enabled/000-default *> changed ```
<VirtualHost *:80>
```  to  ```
<VirtualHost *:8000>
```I've been trying to restart apache and I get the message:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98 ) Address already in use: make_sock: could not bind to address 0.0.0.0:8000
no listening sockets available, shutting down
Unable to open logs

To check for the port that's in use I type: ```
sudo lsof -i tcp
```and not one process is using that port, I even checked UDP, and there is absolutely no use of port 8000 on my system.

Am I doing something wrong here?  Should I stop apache before configuring? Is there something related to having an static-IP on my LAN? (which I'm doing after I finish writing this thread)  I've only tried dummy connections for now, and only port 80 (when I change those files above) accepts them.  Has anyone had this problem before?  I thought it should be pretty straight forward. :-s

Thanks in advance.

---

### Post by el.otro on 2009-06-11
It seems I used the CODE tag a little too much...sorry. :(

---

### Post by Lars Noodén on 2009-06-11
Try looking in /etc/apache2/ports.conf and making sure that the Listen directive is listed only once.

[http://httpd.apache.org/docs/2.2/mod/mpm_common.html#listen](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#listen)

the error message you have "Address already in use" probably means that you have a problem with the Listen runtime directive.  

make sure that your virtual host has its own separate configuration file in /etc/apache2/sites-available, and that it does *not* contain a duplicate Listen directive

then use 'a2ensite' to enable that site, and /etc/init.d/apache2 reload to load the new configuration

---

### Post by cdenley on 2009-06-11
> **Lars Noodén said:**
> Try looking in /etc/apache2/ports.conf and making sure that the Listen directive is listed only once.
This appears to be the problem. You indicated you have this:
```

Listen 8000

```
in both httpd.conf and ports.conf. If apache sees two Listen directives for the same port, you get this error since it tries to listen on that port twice. You should not have edited httpd.conf, remove that line from it.

---

### Post by el.otro on 2009-06-11
Now I see how obvious my mistake was, I couldn't find a reason for it, and was getting desperate, most of the threads I've seen are about aplications ACTUALLY using those ports.   Clearing the httpd.conf file fixed it.

Thank you both for your help!  I'm really happy I've started using Linux, the amount of learning you go through and the Community is a wonderful thing.   I'm really new to Linux, and much more to servers, and that's exactly what  I like about it, the fact that you feel inspired to do things because its free, and you can find resources...!!  But Again, thanks a lot.

---

