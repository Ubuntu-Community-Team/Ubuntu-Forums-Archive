---
title: "access permission problem in apache/php"
date: 2009-03-13
forum: Server Platforms
---

### Post by fabianus on 2009-03-13
Hello all !

I do not know if this is the right place to post my problem, but I do hope that somebody may help me with this issue. 

I just installed ubuntu server with apache preinstalled. I installed php, mysql etc.

Everything seems to work out well, but when the php application trys to access some image files, it throws a permission error. I suppose that I have to tweak something in the apache settings ... but what :-)

Here is the php code : 


[PHP]<p><?php 

$a = getimagesize("testImage.jpg");

echo $a[1];

?></p>[/PHP]


And the getimagesize function throws the following error : 

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/user/fabianus/www/testImageSize.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Here is the configuraiton file of my apache server : 
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/fabianus/store/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/fabianus/store/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```
Any help would be very wellcome !

Regards, 
Fabianus

---

### Post by BkkBonanza on 2009-03-13
It's not your apache settings - it's the file permission of the images. Check what user your apache is running as - often it's apache or www. Then make sure the images have read permission for that user. Often for public images people just leave them as any user readable. Generally php runs as the same user as apache does.

Some commands, to check images as below in correct directory do,

ls -ls 

you see the owner and group name columns one should be the same as apache user or if not then the permissions column needs to indicate "r" value in the left side triplet (other users). Read up on chgrp, chown commands for more info. Google for a tutorial on file permissions.

And if you are sure your permissions are right then start to look at current working directory for the php script. It will try to access the file from where it runs since you didn't prefix a path for the image. If it cannot even find the file it could give an error like this. So prefix an absolute path to the images.

Hope this helps.

---

### Post by fabianus on 2009-03-13
Hello BkkBonaza, 

thanks a lot for your help !

As you imagine I am a greenhorn in linux/ubuntu. So I have to continue to bother you :-)

How to I check the user that apache is runnings as ? And how to I check if php runs as the same user as apache ...

Questions and questions - hope you could give me some more advice. 

Regards, 
Fabianus

---

### Post by BkkBonanza on 2009-03-13
Look in your httpd.conf file. There is usually a statement like: User www 
That will set the user to run as. PHP is started by apache so it usually runs as the same user. It may be possible to run differently and it would be set in php.ini but most likely you didn't do that so it would be same as the apache user.

You can try changing the image filename in your script. Use one that you know does not exist. If you get the same error then it means that the script is not even finding the file so permissions are not yet your problem (they may still be after you resolve the issue of findign the file). If the image file is located in the same directory as your script then it should be found. If the image is located in another directory then you need to provide a path to the file. So instead of "testImage.jpg" above you would use something like "images/testimage.jpg" (relative to current dir) or "/var/www/mysite/images/testImages.jpg" (absolute).

---

### Post by mcla0203 on 2009-03-13
In my apache2 the user seems to be defined in the file: /etc/apache2/envvars

It sets an environment variable as APACHE_RUN_USER, and you should see the httpd.conf file use this value in the User field.  i.e. User = ${APACHE_RUN_USER}

Check that location as well if you see an environment variable.

---

### Post by fabianus on 2009-03-13
got it !
Yes, the image did not have the right permissions. Now it's done. 
Thanks a lot  !

See you, 
Fabianus

---

### Post by fabianus on 2009-03-13
Hello mcla0203, 

thanks to you, too. 

Regards, 
Fabianus

---

