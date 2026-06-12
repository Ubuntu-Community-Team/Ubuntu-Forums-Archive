---
title: "Apache2 woes, from Permission problems to Custom Directory issues"
date: 2015-01-30
forum: Server Platforms
---

### Post by reydempto on 2015-01-30
After a solid week digging through the forums here and a hundred of other places on the net trying solution after solution and coming up empty. I want to be as detailed as possible in order to hopefully, finally come to a conclusion so I can move on with my project!

I have a Dell Poweredge 1950 server from work that I inherited and I am playing around with it and planning to host some content from home. It has some pretty beefy specs so I didn't mind installing Ubuntu Server 14.04 with an xfce desktop environment. I have a 3TB raid5 setup. I have a 100GB partition for the Ubuntu install, 8GB swap area, and a 2.9TB ext4 partition intended for all of my web based adventures (I know it is a lot but I am doing something online that requires the space)

I have a Virtual Box set up running windows7 just for seeding my (legal!) torrents from etree, and that is working beautifully. I have PS3 Media Server set up and serving all of my movies etc to my PS3 via a USB ntfs drive connected to the server. Again, working beautifully. Mazbe these details aren't necessary but I do not want to leave anything out -- I am absolutely stumped on this one.

I installed LAMP with the intention of building a site locally (and eventually deploying it online, upgrading to fiberoptic and a static ip). Outta the box my apache server works perfectly, showing me the apache welcome page when I browse to localhost or my local ip. Even works on other machines, like if I go to my windows laptop and browse to my apache install, I get the same welcome page from apache. HOWEVER! As I mentioned before, I have a separate 2.9TB partition that I would like to use as document root for my web server.

So I edited my config at /etc/apache2/sites-available/000-default.conf, to the Document Root I desire:

```
DocumentRoot /media/psilo/Tofu/lastrewind/var/www/html
```

And yes, I copied the default index.html from the original document root to the new one.

I also edited my config at /etc/apache2/apache2.conf to point to the same directory:

```
<Directory /media/psilo/Tofu/lastrewind/var/www/html>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>
```

After this, I browse to my localhost page and get the dreaded 403 FORBIDDEN error. Oh no! I broke my apache server! I figure not all is lost, so I tail it (tail -f /var/log/apache2/error.log), and the error report i get is:

```
[Fri Jan 30 22:19:54.323921 2015] [core:error] [pid 10859] (13)Permission denied: [client 192.168.0.30:42955] AH00035: access to /index.html denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Fri Jan 30 23:06:18.015778 2015] [mpm_prefork:notice] [pid 10855] AH00169: caught SIGTERM, shutting down
[Fri Jan 30 23:06:19.156959 2015] [mpm_prefork:notice] [pid 11298] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Fri Jan 30 23:06:19.157114 2015] [core:notice] [pid 11298] AH00094: Command line: '/usr/sbin/apache2'

```

So I have a couple of problems apparently, one I can identify and two that are beyond my knowledge. Let's address the one I know a bit about:

```
[Fri Jan 30 22:19:54.323921 2015] [core:error] [pid 10859] (13)Permission denied: [client 192.168.0.30:42955] AH00035: access to /index.html denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
```

This means, to me, maybe I am wrong, there is a permission issue somewhere within /media, /media/psilo/ or /media/psilo/Tofu. So I entered the command 'sudo ls -ld /media/ /media/psilo/ /media/psilo/Tofu/' and the output is:

```
drwxr-xr-x  6 root  root     4096 Jan 30 17:05 /media/
drw-r----x+ 4 psilo www-data 4096 Jan 30 18:29 /media/psilo/
drw-r--r-x  4 psilo www-data 4096 Jan 29 20:21 /media/psilo/Tofu/

```

...problem is I have no idea how to clean up that mess and get things in order, and maybe things are more out of order than that although I didn't change much in terms of permissions. I tried to chown and chmod these to 644 AND 755 with the user and group psilo:www-data but nothign has worked so far.

Those other two tail'd errors are a mystery to me, and I have tried reading so many guides and forum discussions to get this solved but nothing works whatsoever. At the moment I am working with a fresh install of LAMP with only those document roots changed, I have made no further modifications to any configuration files. If anyone can help me get apache to work on this custom directory, I would greatly appreciate it.

---

### Post by Doug S on 2015-01-30
For your first issue, just make make the permissions of the entire chain of directories 755:```
/media 755
/media/psilo 755
/media/psilo/Tofu 755
/media/psilo/Tofu/lastrewind 755
/media/psilo/Tofu/lastrewind/var 755
/media/psilo/Tofu/lastrewind/var/www 755
/media/psilo/Tofu/lastrewind/var/www/html 755
```Your second issue isn't an issue at all. Those are normal log entries for a restart. Example (from my computer):```
[Tue Jan 27 08:30:03.469185 2015] [core:info] [pid 9563] AH00096: removed PID file /var/run/apache2/apache2.pid (pid=9563)
[Tue Jan 27 08:30:03.469223 2015] [mpm_prefork:notice] [pid 9563] AH00169: caught SIGTERM, shutting down
[Tue Jan 27 08:30:04.585205 2015] [mpm_prefork:notice] [pid 9708] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 OpenSSL/1.0.1f configured -- resuming normal operations
[Tue Jan 27 08:30:04.585257 2015] [core:notice] [pid 9708] AH00094: Command line: '/usr/sbin/apache2'
```

---

### Post by reydempto on 2015-01-30
> **Doug S said:**
> For your first issue, just make make the permissions of the entire chain of directories 755:```
/media 755
/media/psilo 755
/media/psilo/Tofu 755
/media/psilo/Tofu/lastrewind 755
/media/psilo/Tofu/lastrewind/var 755
/media/psilo/Tofu/lastrewind/var/www 755
/media/psilo/Tofu/lastrewind/var/www/html 755
```Your second issue isn't an issue at all. Those are normal log entries for a restart. Example (from my computer):```
[Tue Jan 27 08:30:03.469185 2015] [core:info] [pid 9563] AH00096: removed PID file /var/run/apache2/apache2.pid (pid=9563)
[Tue Jan 27 08:30:03.469223 2015] [mpm_prefork:notice] [pid 9563] AH00169: caught SIGTERM, shutting down
[Tue Jan 27 08:30:04.585205 2015] [mpm_prefork:notice] [pid 9708] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 OpenSSL/1.0.1f configured -- resuming normal operations
[Tue Jan 27 08:30:04.585257 2015] [core:notice] [pid 9708] AH00094: Command line: '/usr/sbin/apache2'
```

Thanks for your reply! 

As per your instructions, I changed the permissions of everything to 755 using the command

```
sudo chmod 755 /media
```
...and repeated for every directory in question.

But when I restart the apache2 service I still get the 403 forbidden error and tail still reports this:

```
[Sat Jan 31 00:09:24.657262 2015] [core:error] [pid 11870] (13)Permission denied: [client 192.168.0.30:54175] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path

```

was that chmod incorrect? A quick ls check reveals this:

```
drwxr-xr-x  6 root  root     4096 Jan 30 17:05 /media/
drwxr-xr-x+ 4 psilo www-data 4096 Jan 30 18:29 /media/psilo/
drwxr-xr-x  4 psilo www-data 4096 Jan 29 20:21 /media/psilo/Tofu/
drwxr-xr-x  3 psilo www-data 4096 Jan 30 20:18 /media/psilo/Tofu/lastrewind/
drwxr-xr-x  3 psilo www-data 4096 Jan 29 20:21 /media/psilo/Tofu/lastrewind/var/
drwxr-xr-x  3 psilo www-data 4096 Jan 29 20:21 /media/psilo/Tofu/lastrewind/var/www/
drwxr-xr-x  2 psilo www-data 4096 Jan 30 21:29 /media/psilo/Tofu/lastrewind/var/www/html/

```

Seems good (except /media says root:root and not psilo:www-data)

It appears as though I cannot get /media to have permissions for anyone but root...maybe I am wrong but if I am not..is there any way around this?

Still getting a 403 Forbidden error :(

---

### Post by Doug S on 2015-01-30
For unknown reasons, I got a different error message than you:```
[Fri Jan 30 16:31:37.879239 2015] [authz_core:error] [pid 2900] [client 192.168.111.101:56597] AH01630: client denied by server configuration: /media/newhd/test_web/
```However, and in my opinion, the error message was more meaningful. I had to edit /etc/apache2/apache2.conf and change this:```
# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>

<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

[COLOR=#ff0000]<Directory /media/newhd/test_web/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>[/COLOR]

#<Directory /srv/>
#       Options Indexes FollowSymLinks
#       AllowOverride None
#       Require all granted
#</Directory>
```Then it worked O.K. for me. Here are my permissions:```
drwsrwsrwt 8 root root 4096 Nov 28 19:55 /media
drwxr-xr-x 5 root root 4096 Jan 30 16:24 /media/newhd
drwxr-xr-x 2 root root 4096 Jan 30 16:26 /media/newhd/test_web
-rw-r--r-- 1 root root 1422 Jan 30 16:26 /media/newhd/test_web/index.html
```

---

### Post by reydempto on 2015-01-31
Thanks again Doug. I just tried what you have done there and I still get the same result. What a head-scratcher!
Here is the section of my apache2.conf file in question:

```
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>

<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>

<Directory /var/www>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

<Directory /media/psilo/Tofu/lastrewind/var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

#<Directory /srv/>
#	Options Indexes FollowSymLinks
#	AllowOverride None
#	Require all granted
#</Directory>

```

As for your error, that is one my machine hasn't produced yet :/

---

### Post by volkswagner on 2015-01-31
Is the USB drive formatted NTFS? With the little + sign in permissions, I suspect it is.
```
drwxr-xr-x+ 4 psilo www-data 4096 Jan 30 18:29 /media/psilo/
```

You may not have much joy with NTFS.
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1464912&page=2").

Also with XFCE installed the drive is likely getting automounted. It may be helpful if you could
control the mount in /etc/fstab by adding uid/gid.

---

### Post by reydempto on 2015-02-01
> **volkswagner said:**
> Is the USB drive formatted NTFS? With the little + sign in permissions, I suspect it is.
```
drwxr-xr-x+ 4 psilo www-data 4096 Jan 30 18:29 /media/psilo/
```

You may not have much joy with NTFS.
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1464912&page=2").

Also with XFCE installed the drive is likely getting automounted. It may be helpful if you could
control the mount in /etc/fstab by adding uid/gid.

Nope, /media/psilo/Tofu is an ext4 formatted partition of a 3TB raid5 config. I have an external USB ntfs drive but it is not being used for this at all. What does the + sign signify there?

And even though I am using xfce, I did put my drives in fstab myself, and here is my fstab output for you to check:

```
UUID=7f5f9f33-2c30-4550-9950-1c5d1689cf52	/media/psilo/Tofu	ext4	user	0	0
```
Well, that's the only line that relates to the filepath in question ;)

---

### Post by volkswagner on 2015-02-01
The + sign indicates extended attributes or permissions.  I'm curious why you are mounting at /media/psilo/Tofu?
How did you create the directory /media/psilo?  Do you have any other mounts inside /media/psilo?
Can you post your entire /etc/fstab?
Take a look at this [Apache2 doc]("https://wiki.apache.org/httpd/13PermissionDenied").

Do you need to have the webroot so deep in the file structure (not that it won't work but it make diagnosis a bit more cumbersome)?

/media is no where I'd recommend mounting a permanent disk. May I suggest /mnt or create you're own root dir like /Tofu and mount there.

One test I may suggest... copy your index.html to each directory starting with /media and change the document root respectively to see where the
break occurs.

---

### Post by reydempto on 2015-02-02
I'll just answer those in chronological order :)

Why am I mounting there? I had some strange permission issues for with all of my drives when trying to mount them using fstab...it was crazy, but then as soon as I set the options (in gnome-disks) to 'auto mount' the drives mounted fine with no permission errors, but Tofu mounted itself at /media/psilo/Tofu. At the time I figured well at least I got it to mount properly, and didn't want to mess with it further so I left it at that directory. So basically, /media/psilo/Tofu was made automatically when xubuntu automounted the drive for the first time.

Do I have any other mounts within /media/psilo? Only sometimes, I have a USB memory stick in from time to time, and when it is plugged in, it mounts to /media/psilo.

Here's my complete fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=82c7da9a-e7e5-4c83-9aa4-8898f657d715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=6a7be234-a59c-4f7f-a976-43cfc293b734 none            swap    sw              0       0

UUID=50D49F67D49F4DDA /media/Bertha ntfs default 0 0
UUID=7f5f9f33-2c30-4550-9950-1c5d1689cf52	/media/psilo/Tofu	ext4	user	0	0
```

Oh oh, and I have been to that link before, with the Apache2 error faq about my permission problem. This is actually one of the first things I found when googling the error, but following it didn't produce a solution unfortunately.

I will do the index.html test and see if I can get a result out of it..and I will await a reply on the fstab output I posted, maybe there's something wrong with that!

EDIT: I pasted the default index.html file into every folder along the directory structure (/media/psilo/Tofu/lastrewind/var/www/html) and tested each part of the directory as the document root, restarted the server each time, and every single one still gave me my 403 Forbidden error!

I wanted to wait until your reply on the other stuff and my fstab info before I try your suggestion of changing Tofu's mount point to /mnt, incase I would accidentally further complicate matters

---

### Post by volkswagner on 2015-02-02
I suggest creating a new mount point and editing /etc/fstab. First we'll create the mountpoint, then temporarily mount it, after unmounting existing mount.

create new mount point:
```
sudo mkdir /tofu
sudo chown psilo:www-data /tofu
sudo chmod 755 /tofu
```

Unmount existing... make sure you don't have any open files nor have any terminal sessions with current working directory pointed inside /media/psilo/Tofu:
```
sudo umount /media/psilo/Tofu
 
```
Edit /etc/fstab by commenting out existing mount and make a new one. Create a backup as well.
```
sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab
 
```

NOTE: I'm not familiar with XFCE automount, you may need to edit or undo settings previously set on mounting this partition.

Edit as follows, comment out existing then, create new line with new mount point.
```
#UUID=7f5f9f33-2c30-4550-9950-1c5d1689cf52	/media/psilo/Tofu	ext4	user	0	0
UUID=7f5f9f33-2c30-4550-9950-1c5d1689cf52	/tofu	ext4	defaults	0	2
```

Lets see if we can mount and test function:
```
sudo mount -a
 
```

Fix permissions:
To recursively set permissions only on directories!
```
sudo find /tofu -type d -print0 | xargs -0 chmod 755
```

Edit your apache config to point to new document root. Does it work? If not check permissions.

```
ls -al /tofu/lastrewind/var/www/html
```

Hopefully you don't have any errors along the way. If you encounter errors, please don't reboot without reverting your /etc/fstab.
Also, if there are issues, post the fdisk output here, and any relevant apache errors.
```
sudo fdisk -l
```

---

### Post by reydempto on 2015-02-02
volkswagner--THAT DID IT! Apparently trying to run this from the /media folder was the problem. As soon as I followed your exact directions (remounting everything at /tofu) it started working properly!

You are a lifesaver, and I REALLY appreciate your and Doug S' help. Thanks for taking the time to help me out. I always know that whenever I am truly stumped on a problem, this community has the knowledge to get to the solution.

---

### Post by Doug S on 2015-02-02
Glad you got it working.

Yes, thanks to volkswagner for chiming in on this one. /media worked for me, but oh well.

---

### Post by reydempto on 2015-02-03
I marked this thread as unsolved so as to not make a separate post, This is related to this problem we have been working on this whole time.

Now that apache works and I can get my localhost directory to display fine, I started messing with a wordpress install, but I keep getting a 'Error: PHP is not running' message from wordpress when I try to install. When I go to install PHP5, it says it is installed, but when I create a php.info file to test in the root directory, I get a blank page. Is this something to do with my customised www directory? Is there somewhere where I can point PHP towards my custom apache root? Or am I thinking about it wrong?

---

### Post by Doug S on 2015-02-03
> **reydempto said:**
> Is this something to do with my customised www directory?I re-created the test scenario I had the other day (see previous posts) on my test server. I added a php test file. It worked fine. So, I am thinking, no.

However, I suggest a test: Go back to everything being default. i.e. documentroot as /var/www/html and put your php file there. Does it work then?> **reydempto said:**
> Is there somewhere where I can point PHP towards my custom apache root? Or am I thinking about it wrong?I made no other change on my system and it worked. However, I do know that php was already working.

---

### Post by reydempto on 2015-02-03
Hey Doug, good to see you are still in this :)

I did what you said, reverted my webroot to /var/www/html, created an info.php file in the root.

The code I used for info.php is:

```
<?php phpinfo(); ?>
```

But when I browse to info.php it produces a blank white page. Seems like there's something not right with my PHP installation.

---

### Post by SeijiSensei on 2015-02-03
Try "sudo apt-get install libapache2-mod-php5" and see if that fixes the problem.  

Also, what do you see in /var/log/apache2/error.log when you get the blank page?

---

### Post by reydempto on 2015-02-03
> **SeijiSensei said:**
> Try "sudo apt-get install libapache2-mod-php5" and see if that fixes the problem.  

Also, what do you see in /var/log/apache2/error.log when you get the blank page?

"libapache2-mod-php5 is already the newest version." --so that is for sure installed, I already knew that but I ran the command just to be triple-sure.

I tail'd my error.log file for you, here it is:

```
[Tue Feb 03 16:33:26.175678 2015] [suexec:notice] [pid 26585] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Tue Feb 03 16:33:26.245150 2015] [mpm_prefork:notice] [pid 26586] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:33:26.245253 2015] [core:notice] [pid 26586] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:33:30.621266 2015] [mpm_prefork:notice] [pid 26586] AH00171: Graceful restart requested, doing restart
[Tue Feb 03 16:33:30.705204 2015] [mpm_prefork:notice] [pid 26586] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:33:30.705234 2015] [core:notice] [pid 26586] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:36:13.152352 2015] [mpm_prefork:notice] [pid 26586] AH00169: caught SIGTERM, shutting down
[Tue Feb 03 16:36:14.200209 2015] [suexec:notice] [pid 26695] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Tue Feb 03 16:36:14.271239 2015] [mpm_prefork:notice] [pid 26696] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:36:14.271331 2015] [core:notice] [pid 26696] AH00094: Command line: '/usr/sbin/apache2'

```

Not sure if there is anything really revealing there though.

Here's the complete log file just in case:

```
[Sun Feb 01 08:05:49.062510 2015] [mpm_prefork:notice] [pid 15011] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Sun Feb 01 08:05:49.062567 2015] [core:notice] [pid 15011] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:41:37.496425 2015] [core:error] [pid 19548] (13)Permission denied: [client 192.168.0.30:45130] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:41:37.672605 2015] [core:error] [pid 19548] (13)Permission denied: [client 192.168.0.30:45130] AH00035: access to /favicon.ico denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:43:41.576758 2015] [mpm_prefork:notice] [pid 15011] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 11:43:42.431095 2015] [mpm_prefork:notice] [pid 30402] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 11:43:42.431226 2015] [core:notice] [pid 30402] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:43:46.049697 2015] [core:error] [pid 30406] (13)Permission denied: [client 192.168.0.30:45281] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:44:35.614607 2015] [mpm_prefork:notice] [pid 30402] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 11:44:36.719071 2015] [mpm_prefork:notice] [pid 30484] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 11:44:36.719204 2015] [core:notice] [pid 30484] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:44:38.787039 2015] [core:error] [pid 30488] (13)Permission denied: [client 192.168.0.30:45342] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:44:39.554027 2015] [core:error] [pid 30488] (13)Permission denied: [client 192.168.0.30:45342] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:45:12.612268 2015] [mpm_prefork:notice] [pid 30484] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 11:45:13.717259 2015] [mpm_prefork:notice] [pid 30559] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 11:45:13.717387 2015] [core:notice] [pid 30559] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:45:16.005464 2015] [core:error] [pid 30563] (13)Permission denied: [client 192.168.0.30:45376] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:46:13.585450 2015] [mpm_prefork:notice] [pid 30559] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 11:46:14.690602 2015] [mpm_prefork:notice] [pid 30652] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 11:46:14.690732 2015] [core:notice] [pid 30652] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:46:17.066933 2015] [core:error] [pid 30656] (13)Permission denied: [client 192.168.0.30:45456] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:46:18.013794 2015] [core:error] [pid 30656] (13)Permission denied: [client 192.168.0.30:45456] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:46:18.390078 2015] [core:error] [pid 30656] (13)Permission denied: [client 192.168.0.30:45456] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:46:18.423691 2015] [core:error] [pid 30656] (13)Permission denied: [client 192.168.0.30:45456] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:57:03.354235 2015] [core:error] [pid 30657] (13)Permission denied: [client 192.168.0.30:46283] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 11:58:11.946370 2015] [mpm_prefork:notice] [pid 30652] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 11:58:13.050153 2015] [mpm_prefork:notice] [pid 30783] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 11:58:13.050284 2015] [core:notice] [pid 30783] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 11:58:19.663864 2015] [core:error] [pid 30787] (13)Permission denied: [client 192.168.0.30:46451] AH00035: access to / denied (filesystem path '/media/psilo/Tofu') because search permissions are missing on a component of the path
[Mon Feb 02 16:59:24.739158 2015] [mpm_prefork:notice] [pid 30783] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 16:59:25.849301 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 16:59:25.849429 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:14:08.382291 2015] [:error] [pid 13106] [client 192.168.0.30:39697] script '/tofu/lastrewind/var/www/html/info.php' not found or unable to stat
[Mon Feb 02 17:14:58.967071 2015] [mpm_prefork:notice] [pid 13098] AH00171: Graceful restart requested, doing restart
[Mon Feb 02 17:14:59.091151 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:14:59.091189 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:15:32.480741 2015] [mpm_prefork:notice] [pid 13098] AH00171: Graceful restart requested, doing restart
[Mon Feb 02 17:15:32.595889 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:15:32.595920 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:15:32.699943 2015] [mpm_prefork:notice] [pid 13098] AH00171: Graceful restart requested, doing restart
[Mon Feb 02 17:15:32.789393 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:15:32.789422 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:34:57.382945 2015] [mpm_prefork:notice] [pid 13098] AH00171: Graceful restart requested, doing restart
[Mon Feb 02 17:34:57.479221 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:34:57.479253 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:39:22.511911 2015] [mpm_prefork:notice] [pid 13098] AH00173: SIGHUP received.  Attempting to restart
[Mon Feb 02 17:39:22.588612 2015] [mpm_prefork:notice] [pid 13098] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:39:22.588694 2015] [core:notice] [pid 13098] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:43:40.848292 2015] [mpm_prefork:notice] [pid 13098] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 17:43:41.940728 2015] [suexec:notice] [pid 22756] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Feb 02 17:43:42.010668 2015] [mpm_prefork:notice] [pid 22757] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:43:42.010791 2015] [core:notice] [pid 22757] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:51:44.265754 2015] [mpm_prefork:notice] [pid 22757] AH00173: SIGHUP received.  Attempting to restart
[Mon Feb 02 17:51:44.344268 2015] [mpm_prefork:notice] [pid 22757] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:51:44.344380 2015] [core:notice] [pid 22757] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:52:42.717689 2015] [mpm_prefork:notice] [pid 22757] AH00173: SIGHUP received.  Attempting to restart
[Mon Feb 02 17:52:42.795796 2015] [mpm_prefork:notice] [pid 22757] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:52:42.795888 2015] [core:notice] [pid 22757] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 17:53:39.173899 2015] [mpm_prefork:notice] [pid 22757] AH00173: SIGHUP received.  Attempting to restart
[Mon Feb 02 17:53:39.252123 2015] [mpm_prefork:notice] [pid 22757] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 17:53:39.252216 2015] [core:notice] [pid 22757] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 19:03:01.759833 2015] [mpm_prefork:notice] [pid 22757] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 19:04:34.661682 2015] [suexec:notice] [pid 25177] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Feb 02 19:04:34.729883 2015] [mpm_prefork:notice] [pid 25178] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 19:04:34.729984 2015] [core:notice] [pid 25178] AH00094: Command line: '/usr/sbin/apache2'
[Mon Feb 02 19:06:45.227370 2015] [mpm_prefork:notice] [pid 25178] AH00169: caught SIGTERM, shutting down
[Mon Feb 02 19:06:46.273932 2015] [suexec:notice] [pid 25306] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Mon Feb 02 19:06:46.343444 2015] [mpm_prefork:notice] [pid 25307] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Mon Feb 02 19:06:46.343545 2015] [core:notice] [pid 25307] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:32:51.761340 2015] [mpm_prefork:notice] [pid 25307] AH00169: caught SIGTERM, shutting down
[Tue Feb 03 16:32:52.799996 2015] [suexec:notice] [pid 26441] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Tue Feb 03 16:32:52.869748 2015] [mpm_prefork:notice] [pid 26442] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:32:52.869847 2015] [core:notice] [pid 26442] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:33:25.130750 2015] [mpm_prefork:notice] [pid 26442] AH00169: caught SIGTERM, shutting down
[Tue Feb 03 16:33:26.175678 2015] [suexec:notice] [pid 26585] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Tue Feb 03 16:33:26.245150 2015] [mpm_prefork:notice] [pid 26586] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:33:26.245253 2015] [core:notice] [pid 26586] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:33:30.621266 2015] [mpm_prefork:notice] [pid 26586] AH00171: Graceful restart requested, doing restart
[Tue Feb 03 16:33:30.705204 2015] [mpm_prefork:notice] [pid 26586] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:33:30.705234 2015] [core:notice] [pid 26586] AH00094: Command line: '/usr/sbin/apache2'
[Tue Feb 03 16:36:13.152352 2015] [mpm_prefork:notice] [pid 26586] AH00169: caught SIGTERM, shutting down
[Tue Feb 03 16:36:14.200209 2015] [suexec:notice] [pid 26695] AH01232: suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec)
[Tue Feb 03 16:36:14.271239 2015] [mpm_prefork:notice] [pid 26696] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 configured -- resuming normal operations
[Tue Feb 03 16:36:14.271331 2015] [core:notice] [pid 26696] AH00094: Command line: '/usr/sbin/apache2'
```

---

### Post by Doug S on 2015-02-03
I was always watching this thread. I just couldn't add any value with the fstab stuff that volkswagner was helping with.

O.K. so we know the issue is just that php isn't working, and not (at least not yet) related to your doc root location. The following suggestion is cut and pasted from [the Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/php5.html"):> By default, the Apache 2 Web server is configured to run PHP5           scripts. In other words, the PHP5 module is enabled in Apache2           Web server automatically when you install the module. Please           verify if the files           /etc/apache2/mods-enabled/php5.conf and           /etc/apache2/mods-enabled/php5.load           exist. If they do not exists, you can enable the module using           a2enmod command.Edit: I had not seen the previous two posts when I replied.

---

### Post by reydempto on 2015-02-03
> **Doug S said:**
> I was always watching this thread. I just couldn't add any value with the fstab stuff that volkswagner was helping with.

O.K. so we know the issue is just that php isn't working, and not (at least not yet) related to your doc root location. The following suggestion is cut and pasted from [the Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/php5.html"):

Always watching, great now I feel much safer :) heheheh Thank you man.

I checked and both files are indeed present in the directory the serverguide specified. Is there something within them that I can edit to fix this? Didn't really see anything in the conf file.

EDIT: Here are the contents of my php5.conf file:

```
<FilesMatch ".+\.ph(p[345]?|t|tml)$">
</FilesMatch>
<FilesMatch ".+\.phps$">
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Order Deny,Allow
    Deny from all
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
    Order Deny,Allow
    Deny from all
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```

---

### Post by Doug S on 2015-02-03
> **reydempto said:**
> I started messing with a wordpress install, ...I wonder if that messed things up. What reference did you use for your wordpress install? I would recommend [the Ubuntu server guide]("https://help.ubuntu.com/lts/serverguide/wordpress.html"). The wordpress section was only recently added, and I know it works, as I was the proof reader and used only the one reference to successfully install it, and make it functional.

---

### Post by volkswagner on 2015-02-03
I go a little hog wild with php5 packages. Here's what I install prior to installing Wordpress via SVN.

```
apt-get install mysql-server mysql-client
apt-get install php5 libapache2-mod-php5
apt-get install php-pear php5 php5-cli php5-common php5-curl php5-dev php5-gd php5-idn php5-imagick php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl phpmyadmin
```

Of course I'd like to know what each package does and if it's required or a security hole, but there's only so much time in a day ;)

I know most of those are not needed, but I also know Wordpress works flawlessly after following the [Subversion how-to.]("http://codex.wordpress.org/Installing/Updating_WordPress_with_Subversion")

---

### Post by reydempto on 2015-02-04
> **Doug S said:**
> I wonder if that messed things up. What reference did you use for your wordpress install? I would recommend [the Ubuntu server guide]("https://help.ubuntu.com/lts/serverguide/wordpress.html"). The wordpress section was only recently added, and I know it works, as I was the proof reader and used only the one reference to successfully install it, and make it functional.

The only thing I did was place the wordpress files in my webroot directory and tried to browse to wp-admin/install.php, made no real changes whatsoever. I don't really see how just placing the wordpress files in my webroot could stop PHP from working.

I will look through the wordpress section of the guide today, but it looks like PHP is not working properly either way (remember I made a phpinfo.php file to test and it came up blank)

> **volkswagner said:**
> I go a little hog wild with php5 packages. Here's what I install prior to installing Wordpress via SVN.

```
apt-get install mysql-server mysql-client
apt-get install php5 libapache2-mod-php5
apt-get install php-pear php5 php5-cli php5-common php5-curl php5-dev php5-gd php5-idn php5-imagick php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl phpmyadmin
```

Of course I'd like to know what each package does and if it's required or a security hole, but there's only so much time in a day ;)

I know most of those are not needed, but I also know Wordpress works flawlessly after following the [Subversion how-to.]("http://codex.wordpress.org/Installing/Updating_WordPress_with_Subversion")


Thanks guys, I will go through both of these today and report what happens :) honestly I am only using wordpress as a test environment and to build a temporary site while I build a new version of my project from the ground up using django, but I will still need php.

---

### Post by SeijiSensei on 2015-02-04
> **volkswagner said:**
> Of course I'd like to know what each package does and if it's required or a security hole, but there's only so much time in a day ;)

All those php5-something packages add modules to support specific functionality within PHP.  The php5-imagick module adds [ImageMagick]("http://php.net/manual/en/book.imagick.php") support; php5-mcrypt enables the use of the [mcrypt]("http://php.net/manual/en/book.mcrypt.php") encryption functions; and so forth.  The phpinfo() command will show which additional modules are loaded.

---

### Post by reydempto on 2015-02-10
I started over from scratch on the whole wordpress install, and started over using the Ubuntu Server Guide that Doug gave..I still get no response from PHP.

I also installed all those extra packages, I had 90% of them already, but the ones that installed made no difference. What a headache!!!

I am considering starting over from scratch and repartitioning my hard drive back to one piece so that I can leave my lamp settings at pretty much default..I had this all working before I upgraded the size of my raid. Does anyone else agree that this is the best course of action?

EDIT: I decided to cut and run and just start developing on python instead of using PHP. It's about time I moved on to it anyway, this seems like as good a time as any. What is better, I already have a virtual instance of django running on apache snoothly right now, so I'll probably just remove all the php packages and go on from here.

Thank you to everyone who helped me come to this conclusion. Sometimes the path of least resistance is the best one, and this time it will lead me to understanding another scripting language :)

---

