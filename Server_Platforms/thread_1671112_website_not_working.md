---
title: "website not working"
date: 2011-01-19
forum: Server Platforms
---

### Post by ZenMasta on 2011-01-19
I just installed the lamp stack and so far my default site is working. 

But a 2nd site I made is not working.
I created the config file in 
/etc/apache2/sites-available

it reads:
> 
<VirtualHost myip:80>
ServerAdmin [email]webmaster@mydomain.com[/email]
ServerName mydomain.com
DocumentRoot /home/robbieb/html/
ErrorLog /home/robbieb/logs/error.log
CustomLog /home/robbieb/logs/access.log combined
</VirtualHost>


I then enabled the site 
sudo a2ensite nameofconfigfile
I reloaded apache 

then I try to view the site, but then I get the generic 403 forbidden no permission to access index.html

If I try to access another file say myspecial.php for example I just get a blank white page.

if I try to view an info.php it will display fine (i just created this via ssh), the other files were uploaded by ftp.


> root@ve:/home/robbieb/html# ls -l
total 12
-rw------- 1 robbieb robbieb   22 Jan 19 11:22 index.html
-rw------- 1 robbieb robbieb 1742 Jan 19 11:22 myspecial.php
-rw-r--r-- 1 root    root      20 Jan 19 13:08 test.php
root@ve:/home/robbieb# ls -l
total 8
drwxr-xr-x 2 robbieb robbieb 4096 Jan 19 13:08 html
drwxr-xr-x 2 robbieb robbieb 4096 Jan 19 12:43 logs


So based on the error and then from this read out its obviously a permission problem. The test file I created with the root user via ssh has a couple of extra read permissions it seems.

Also, I created the folders html and logs with the robbieb user, should I have created them with the root user?

How do I fix this?

---

### Post by James78 on 2011-01-19
If you have your directories as 750 (drwxr-x---) and your files as 640 (-rw-r-----), and have everything owned by robbieb, you can get a really good configuration going. No one else will be able to read your files and whatnot, so you'll have more security. In order to allow Apache to read your files (falling under the group read part), you just add www-data to your users group.
```
sudo adduser www-data robbieb
```

---

### Post by ZenMasta on 2011-01-19
Well I added the www-data to the robbieb group like you suggested but it didn't seem to make any difference. 

I'm not quite following you on the permissions either.

I changed html and logs folder from 755 to 750 and applied recursivly (using ftpzilla) and then when I tried to access either the index.html or the php file it gave me 403 forbidden You don't have permission to access / on this server.
If I change the permission of index.html to 640 I get the same error, regardless of the folder being 755 or 750.

Additionally I find that when I upload via FTP the files are uploaded with 600 permission. 

I installed vsftpd using this guide 
[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html#vsftpd-ftp-server-installation](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html#vsftpd-ftp-server-installation)

---

### Post by wongo888 on 2011-01-19
If you are getting a 403 error then your server has been configured to disallow access. The trick is to figure out what is causing the blocking.

First thing you should do is to check your error logs.

Second thing is to make sure that the apache user (www-data on Ubuntu) can access the file that you are trying to serve.

You might also want to check for any oddball directives in .htaccess files (ie. allow,deny directives).

I've always just left my virtual hosts in /var/www and I've never had a problem. I name them /var/www/example.com/ etc. I usually add a symlink from the user directory for convenience.

---

### Post by ZenMasta on 2011-01-19
I don't have any htaccess files. And I already added the www-data user if you noticed in the previous post. I have checked over and over again /etc/vsftpd.conf and both local_enable=YES
write_enable=YES are uncommented.

If there's more to it then the ubuntu guide definitely needs to be updated.

---

### Post by Jive Turkey on 2011-01-19
Rather than adding www-data to the robbieb group, I would try giving www-data group ownership on the files with "sudo chown -R robbieb:www-data /home/robbieb/html && chmod -R 640 /home/robbieb/html"

I could be really really wrong about this but it seems like adding apache to your user's group is a security risk.

---

### Post by James78 on 2011-01-20
> **Jive Turkey said:**
> Rather than adding www-data to the robbieb group, I would try giving www-data group ownership on the files with "sudo chown -R robbieb:www-data /home/robbieb/html && chmod -R 640 /home/robbieb/html"

_I could be really really wrong about this but it seems like adding apache to your user's group is a security risk._
That is a reasonable conclusion, however I would like to note to you that Webmin does this per default, and if they do it, it must not be a security risk, or they wouldn't do it.

---

### Post by ZenMasta on 2011-01-20
I tried your suggestion > chown -R robbieb:www-data /home/robbieb/html && chmod -R 640 /home/robbieb/html

but this brought the site down again. When you try to view it in a browser its just 403 forbidden/you dont have permission.

And also when I log in with FTP my user couldn't navigate to the html folder anymore, but it could change the permission back to 755.

---

### Post by ZenMasta on 2011-01-20
sorry for the dupe post... forums having that proxy error again.

---

### Post by James78 on 2011-01-20
As wongo said earlier, could you check out your Apache error log?
/var/log/apache2/error.log OR the log file pointed to by the ErrorLog directive in your Virtualhost.

---

### Post by James78 on 2011-01-20
... Proxy error again .. :(

---

### Post by James78 on 2011-01-20
... Proxy error again .. :(

---

### Post by James78 on 2011-01-20
... Proxy error again .. :(

---

### Post by ZenMasta on 2011-01-20
sigh, proxy/time out errors on the forum :(  anyway.

/var/log/apache2/error.log contains only about 16 lines. Mostly from when I was changing configs and reloading. Nothing relevant here.

In /home/robbieb/logs/error.log not much either
> root@ve:~# vi /home/robbieb/logs/error.log
[Wed Jan 19 14:35:00 2011] [error] [client myip] (13)Permission denied: file permissions deny server access: /home/robbieb/html/index.html
[Wed Jan 19 14:35:01 2011] [error] [client myip] (13)Permission denied: file permissions deny server access: /home/robbieb/html/index.html
[Wed Jan 19 14:35:03 2011] [error] [client myip] (13)Permission denied: file permissions deny server access: /home/robbieb/html/index.html
[Wed Jan 19 19:15:38 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:38:16 2011] [error] [client 205.186.134.223] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:38:36 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:38:47 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:39:05 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:39:21 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:40:56 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:41:28 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Wed Jan 19 19:41:33 2011] [error] [client serverip] client denied by server configuration: /home/robbieb/html/magento/app/etc/local.xml
[Thu Jan 20 08:30:28 2011] [crit] [client myip] (13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Thu Jan 20 08:30:31 2011] [crit] [client myip] (13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Thu Jan 20 08:30:32 2011] [crit] [client myip] (13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Thu Jan 20 08:30:34 2011] [crit] [client myip] (13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable


recent vsftpd log info
> 
Thu Jan 20 15:15:10 2011 [pid 5629] CONNECT: Client "myip"
Thu Jan 20 15:15:10 2011 [pid 5508] [robbieb] OK LOGIN: Client "myip"
Thu Jan 20 15:15:17 2011 [pid 9242] CONNECT: Client "myip"
Thu Jan 20 15:15:17 2011 [pid 9241] [robbieb] OK LOGIN: Client "myip"
Thu Jan 20 15:15:17 2011 [pid 9246] [robbieb] FAIL DOWNLOAD: Client "myip", "/home/robbieb/html/vsftpd.log", 0.00Kbyte/sec
Thu Jan 20 15:16:14 2011 [pid 9246] [robbieb] OK UPLOAD: Client "myip", "/home/robbieb/html/indexy.htmlsky", 23 bytes, 0.12Kbyte/sec
Thu Jan 20 15:17:53 2011 [pid 9246] [robbieb] OK UPLOAD: Client "myip", "/home/robbieb/html/thpproducts.ods", 3641323 bytes, 41.14Kbyte/sec
Thu Jan 20 15:18:23 2011 [pid 9246] [robbieb] OK DOWNLOAD: Client "myip", "/home/robbieb/html/thpproducts.ods", 3641323 bytes, 162.60Kbyte/sec
Thu Jan 20 15:19:20 2011 [pid 9246] [robbieb] FAIL DOWNLOAD: Client "myip", "/home/robbieb/html/vsftpd.log", 0.00Kbyte/sec


As you can see, I could not download the vsftpd log for some reason. I was able to upload and download a few files. But the permissions on those were 600

[http://buggyonpurpose.com/random/SS-2011.01.20-15.23.12.jpg](http://buggyonpurpose.com/random/SS-2011.01.20-15.23.12.jpg)

---

### Post by James78 on 2011-01-20
If I remember right, the _"(13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable"_ errors are caused by incorrect file/directory permissions. Maybe we found the problem (and if not, being denied like that is still a problem though)

600 (-rw-------) permissions? That's not group readable, or even world readable at that...  I have my setup like.. I have added www-data to my user group (sudo adduser www-data robbieb), and have 750 directories and 640 files, which is what I have on my setup (no public read! :)). It works really well for me.

---

### Post by wongo888 on 2011-01-20
If "AllowOverride" is "on", Apache will fail safe if it can see an .htaccess file in a web directory, but cannot read it. You can try one of two things:

1) Make the permissions on the .htaccess file readable by apache (and webroot directory must be made executable by apache)

```

$ sudo chmod 644 /home/robbieb/html/.htaccess
$ sudo chmod 755 /home/robbieb/html/

```

2) Temporarily rename the .htaccess file something else until you can debug this setup

```

$ sudo mv /home/robbieb/html/.htaccess /home/robbieb/html/htaccess_TEMP

```

Once again, check the log.

---

### Post by ZenMasta on 2011-01-20
I never had a .htaccess file. But the real problem here anyway seems to be vsftp not apache right?. Yeah apache isn't rendering files because of permissions but isn't that because vsftp or my user isn't given the right permission when it comes to uploading files. Am I missing something?

vsftp conf:
[http://pastie.org/1482998](http://pastie.org/1482998)
apache conf:
[http://pastie.org/1483007](http://pastie.org/1483007)

Even if I create a new users and then try to upload something the permissions are the same... 600

---

### Post by James78 on 2011-01-20
Your vsftp conf looks fine.. Try unchecking the local_umask setting though, and see what that does, if anything.

---

### Post by ZenMasta on 2011-01-20
After uncommenting local_umask=022
I am now succesfully able to upload files and the default permissions look good.:popcorn:

Files:644 
Dir:755

---

### Post by wongo888 on 2011-01-20
Well, it says in your log that you posted that there is an .htaccess file in your webroot that is blocking it from serving your web site. You should check it out if that critical error is still in your log or if you are still getting 403 errors from your server.

```
$ ls -la /home/robbieb/html/
```

---

### Post by ZenMasta on 2011-01-20
Hmm, maybe at one point there was when I was copying backup files and stuff from another dir but there definitely is not one now. 

But I think I'm in business now! Thanks a bunch you guys.

---

### Post by James78 on 2011-01-20
> **ZenMasta said:**
> Hmm, maybe at one point there was when I was copying backup files and stuff from another dir but there definitely is not one now. 

But I think I'm in business now! Thanks a bunch you guys.
No problem. :D
> **wongo888 said:**
> Well, it says in your log that you posted that there is an .htaccess file in your webroot that is blocking it from serving your web site. You should check it out if that critical error is still in your log or if you are still getting 403 errors from your server.

```
$ ls -la /home/robbieb/html/
```
Originally yes, but the _"(13)Permission denied: /home/robbieb/html/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable"_ error is actually commonly caused by incorrect permissions. I've had this problem before, and it's a PAIN to track it down because the error doesn't even point to the correct problem. :|

---

