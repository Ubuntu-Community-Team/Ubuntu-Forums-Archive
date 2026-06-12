---
title: "htaccess and https problems"
date: 2009-05-19
forum: Server Platforms
---

### Post by hellarough on 2009-05-19
Okay, so, recently I built a small home LAMP server. So far I have done the following:

ssh server   #for remote administration

Torrentflux (dir is at /home/user/share1)   #torrents 24/7

samba file share no. 1 (/home/user/share1)  #for local home users to store files and DL torrents to

samba file share no. 2 (/var/www/share2)   #for local and www access

My problem is that I am not sure how to restrict access to my site. Here is my .htaccess file (sanitized) and it is located in /var/www/ 

```
#-----Authentication--------
AuthName "Web Server"
AuthUserFile /path_to_my/.htpasswd
AuthType basic
Require valid-user
Order deny,allow
Deny from all
Allow from xxx.xxx.x.x #allows a local connection w/o user/pass prompt?
Satisfy Any

#-----Security---------------

RewriteEngine On 
RewriteCond %{SERVER_PORT} 80  
RewriteRule ^(.*)$ https://mywebsite.com/$1 [R,L] #redirects to secure page

#I read somewhere that this is how to force secure access only (ideal)
#SSLOptions +StrictRequire
#SSLRequireSSL
#SSLRequire %{HTTP_HOST} eq "mywebsite.com"
#ErrorDocument 403 https://mywebsite.com
```

1. Do I have to forward another port to my server for https requests?

2. What do I have to put in my apache configuration files (httpd.conf, access.conf, etc.) to make this work?  


I have tried reading [this apache tutorial about htaccess]("http://www.askapache.com/htaccess/apache-htaccess.html#httpd-config-examples") files and I am still kinda confused. Really what I want is to make sure that usernames and passwords are not sent in plain text and that once someone has gained access to the site they are limited to downloading files (right-click save as from the default apache index page). In the future I would like the capability to upload files through a web browser so my family would be able to use it. I originally tried using vsftpd but couldn't configure it correctly (port issue) but then I realized that my family would never be able to use ftp client software.

I am open to any suggestions, comments, idea and help

thanks

---

### Post by hellarough on 2009-05-21
Since I am at a stand still I have decided to put this project on hold. There will be no web access, share #2 is getting removed, and I plan to use FTP for the file transfers. If anyone has any other ideas as to what other service I can add to my home server I am open to ideas.

---

### Post by albinootje on 2009-05-21
> **hellarough said:**
> share #2 is getting removed, and I plan to use FTP for the file transfers. 

Ftp and ssh over internet ? 

You do know that ftp by default uses plain text of username and password,  right ? Because in that case anyone who can sniff that, can also log in with ssh, and probably use sudo to gain full control.

It is better to use "virtual users" in ftp to start with.

---

### Post by hellarough on 2009-05-22
> **albinootje said:**
> Ftp and ssh over internet ? 

You do know that ftp by default uses plain text of username and password,  right ? Because in that case anyone who can sniff that, can also log in with ssh, and probably use sudo to gain full control.

It is better to use "virtual servers" in ftp to start with.

No, didnt really know, I am still a pretty big noob. I thought that ssh and sftp were encrypted but if I understand you correctly then the username and password are sent plain text and everything else is encrypted? 

So I am guessing that by virtual server you mean using something like vsftpd where I can jail users to a specific directory? I tried using that at first but I couldn't really configure it to work just like that htaccess.

---

### Post by albinootje on 2009-05-22
> **hellarough said:**
> I thought that ssh and sftp were encrypted but if I understand you correctly then the username and password are sent plain text and everything else is encrypted? 

ssh/sftp/scp is all encrypted. 
But ftp is, by default, completely unencrypted.
> 
So I am guessing that by virtual server you mean using something like vsftpd where I can jail users to a specific directory? I tried using that at first but I couldn't really configure it to work just like that htaccess.
I meant with "virtual users" in ftp that those users are created within the ftp server environment, those users are only ftp users, and not "normal" users in your Ubuntu system.

Here's a howto to try :
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293)
and another short one :
[http://linuxforfun.net/2008/04/15/vsftpd-virtual-users-another-approach/](http://linuxforfun.net/2008/04/15/vsftpd-virtual-users-another-approach/)

---

### Post by apel_2804 on 2009-05-22
To run apache with SSL (HTTPS):

[http://www.tbaumi.de/blog/?p=60](http://www.tbaumi.de/blog/?p=60)

And a howto for htaccess:

[http://www.tbaumi.de/blog/?p=72](http://www.tbaumi.de/blog/?p=72)

---

### Post by hellarough on 2009-05-23
> **albinootje said:**
> ssh/sftp/scp is all encrypted. 
But ftp is, by default, completely unencrypted.

I meant with "virtual users" in ftp that those users are created within the ftp server environment, those users are only ftp users, and not "normal" users in your Ubuntu system.

Here's a howto to try :
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=518293)
and another short one :
[http://linuxforfun.net/2008/04/15/vsftpd-virtual-users-another-approach/](http://linuxforfun.net/2008/04/15/vsftpd-virtual-users-another-approach/)

Sweet. Thanks for the help. 

> **apel_2804 said:**
> To run apache with SSL (HTTPS):

[http://www.tbaumi.de/blog/?p=60](http://www.tbaumi.de/blog/?p=60)

And a howto for htaccess:

[http://www.tbaumi.de/blog/?p=72](http://www.tbaumi.de/blog/?p=72)

Thanks for the links, I'll have to try them out when I get home.

---

