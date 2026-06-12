---
title: "Changing /var/www to /media/hda5/www"
date: 2006-07-02
forum: Server Platforms
---

### Post by Isoss on 2006-07-02
Is it possible to change the localhost directory to a folder in a storage media hard disk?

If yes, can u please explain how can I configuer apache so I can get it working?

Thanks for your time.

---

### Post by Randomskk on 2006-07-02
In /etc/apache2/sites-available/default
change DocumentRoot /var/www to DocumentRoot /media/hda5/www
then run this:
apache2ctl restart

and it should all work.

---

### Post by Isoss on 2006-07-02
I did so, I edited the file and then *sudo apache2ctl restart* and it outputted the following:
```
apache2: Could not determine the server's fully qualified domain name, using 192.168.0.1 for ServerName
```
dunno what's wrong!

I also need to know if it's possible to change the "mysql" database directory /var/lib/mysql to /media/hda5/www/mysql/data/

Thanks.

---

### Post by Randomskk on 2006-07-02
For that error message in the logs, I wouldn't worry, but if you want to get rid of it, you have three options (listed in order of ease):
1) Add this line to the /etc/apache2/sites-available/default file:
ServerName <your domain name>

2) run this command:
sudo hostname <your domain name>

3) edit /etc/hosts as root, change / add the line that starts 192.168.0.1 so that it looks like:
192.168.0.1 <possibly other names> <your domain name>

Any option should work, if not go to the next on the list.
Apache should work anyway, though.

As far as moving the MySQL database, I've got less experience, but I'd look into the config file at /etc/mysql/my.cnf , the paths for MySQL can be changed there (remember to do "sudo /etc/init.d/mysql restart" after editing the file).

---

### Post by Isoss on 2006-07-02
Alright it worked and apache was started but I can't access the /media/sda5/server/www through the browser! I am using putty to access the server. I used [http://192.168.0.1](http://192.168.0.1) to access the /var/www of the server PC from my laptop through the browser over my LAN. Now when I go to this address it says:

**Forbidden**

You don't have permission to access / on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
--------------------------------------------------------------
Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 Server at 192.168.0.1 Port 80

How can I view the localhost folder? 

As for option 3, the /etc/hosts file outputs:
```

127.0.0.1         localhost
192.168.0.1      server
.
.
.
.
etc

```
Now I am not sure what to do here ... would I just add anything like: 192.168.0.1 server <anything>

Let me tell you what I am doing. I need to move my www folder to the media hard disk so when I am in windows, I can use phpdev, which is a little software for windows that installs apache, php and mysql in a one folder specified by me, (i.e /harddisk/server/ ) which has the www inside the server folder and mysql database files in /server/mysql/data/, so I can have both windows and linux server for the same web root folder. dunno if this is possible, but I am trying. That's why I want to move both /var/www and /var/lib/mysql/

So I hope I can get more help on this based on my need.

So now I need to be able to read [http://192.168.0.1](http://192.168.0.1) which opens the localhost from /media/sda5/server/www

Thanks.

---

### Post by mssever on 2006-07-02
It appears that your DocumentRoot isn't readable by Apache. Make sure that all files in DocumentRoot are world readable (or otherwise readable by Apache) and that DocumentRoot itself and all of its parent directories are world executable.

As to the hosts file, I did the following (I have a similar setup to you):
```
127.0.0.1       localhost
192.168.1.50    scott-desktop scott-desktop.local
```
This made Apache quit complaning about being unable to find a fully-qualified domain name. Also, by doing this, I don't have to access the server by IP number anymore. I use [http://scott-desktop.local](http://scott-desktop.local) instead. I also added that line to the hosts file of my Windows laptop (C:\windows\system32\drivers\etc\hosts). Now, I can use the domain name I set up anywhere in my network.

---

### Post by Randomskk on 2006-07-02
Sorry, was playing UT04 >:D

Anyway, for the Apache you basically need to do this:
chmod 666 -R /media/hda5/www
chmod a+X -R /media/hda5/www

That should fix the 403 error, and for the /etc/hosts file just make it so the line reads:
192.168.0.1 server <domain name>

As mssever said, you could put anything in domain name really, just so long as it's a domain name (something . something).

---

### Post by Isoss on 2006-07-03
Thanks. I'll try all that and report to you the results. Thanks guys.

---

### Post by Isoss on 2006-07-05
didn't work! same problem!!

Are u sure this works? cuz I remember a couple of months ago i read something about this somewhere and it was more complicated but I can't remember where I read that.

I guess it's not hard for ppl in this forum since this is a normal server problem.

Thanks.

---

### Post by Randomskk on 2006-07-05
If you type:
sudo su www-data
you should get a shell, this is as the user apache runs as.
Then, try going to /media/hda5/www and see if you have permission to, you can try to keep changing permissions until you get it.
The problem may be related to the fact that it's an external hard disk, although this seems a little unlikely, none the less you may need to set permissions higher up the filesystem:
sudo chmod a+rw -R /media/hda5

---

### Post by mssever on 2006-07-05
Here's something I just thought of. If Randomskk's instructions don't work, it may be because of the filesystem type. Since you're planning on using Windows to view the files, there's a good chance that its format is either vfat (Win calls it FAT32) or NTFS. If it's NTFS, you need to know that NTFS support in Linux is experimental, and if you write to the partition, you could lose all data on that partition. That said, I've never had any trouble with NTFS on Linux. To find out what kind of filesystem it is, type [FONT="Courier New"]mount[/FONT] (assuming that the partition is already mounted).

Windows filesystems don't support *nix permissions. So, try this:
```
#find the uid and gid that www-data runs as
cat /etc/passwd|grep www-data
#fields are separated by ":"; uid is the third field and gid the fourth
sudo mount -o remount,uid=<www-data's uid>,gid=<www-data's gid> /media/hda5
```

If Apache works now, than you probably won't be able to access the files as your normal user. There will be no secure option, AFAIK. You can tell Apache to run as your user (insecure), or you can edit your /etc/fstab and include [FONT="Courier New"]umask=000[/FONT] as an option for that partition. This makes the partition fully-writable by anyone (insecure).

*Edit: I hope I gave the proper umask; if that doesn't work, try 777. I don't know umasks as well as I should.*

---

### Post by Randomskk on 2006-07-05
Yea, this seems like a good idea.
You did give the right umask, 000 = 777 permissions (you take the umask away from 777 to get the permissions).

---

