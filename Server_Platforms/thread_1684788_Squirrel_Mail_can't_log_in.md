---
title: "Squirrel Mail can't log in"
date: 2011-02-09
forum: Server Platforms
---

### Post by Lightning200MPH on 2011-02-09
I'm new to linux and trying to solve this problem. I have followed the perfect server 10.10 setup and I have got a basic page up and running. If I use the IP address of the server /webmail I can log in, if I use the .com/webmail I can't log in and get this error.
 
"Error opening ../config/default_pref
Could not create initial preference file!
/var/lib/squirrelmail/data/ should be writable by user www-data
Please contact your system administrator and report this error."
 
This is my output of ls -la /var/lib/squirrelmail/data/
```
drwxrwx--- 2 root     www-data 4096 2011-02-09 12:36 .
drwxr-xr-x 3 root     root     4096 2011-02-09 12:02 ..
-rwxrwx--- 1 www-data www-data  108 2011-02-09 12:36 postmaster@"website".com.pref

```
 
Any ideas?

---

### Post by Kooothor on 2011-02-09
Hello,
This looks like a permission problem, 
very common on Unix box :)
Try this :
```
sudo chmod 730 /var/lib/squirrelmail/data/
```
[source]("http://squirrelmail.org/docs/admin/admin-3.html") and Ctrl-f : 0730 (

**If** that doesn't work, try to see if 
```
sudo chmod 777 /var/lib/squirrelmail/data/
```
resolves the matter.

---

### Post by Lightning200MPH on 2011-02-10
I've been trying to figure this out and messing around with different chmod settings. I did chmod -R 777 also but it didn't work either.
This is what it is set to now, but I can only log in on the local network address.
```
total 12
drwxrwxrwx 2 root     www-data 4096 2011-02-10 22:18 .
drwxr-xr-x 3 root     root     4096 2011-02-10 21:32 ..
-rw------- 1 www-data www-data  207 2011-02-10 22:18 postmaster@"website".com.pref
```

I wiped out another box and duplicated my setup so I can "try" stuff. I've been reading on the setup link but I haven't figured anything out yet, I've also been searching the web looking for others with the same problem.

---

### Post by elico on 2011-02-11
there is a nice config.pl file and try to setup the settings directory in a related path such as:
/var/www/sqdata and with permissions of  777
just to make sure..
and if you do get it right than enable the use of .htaccess and build one in the settings directory to deny all connections so no one can access the directory info using http.

---

### Post by Lightning200MPH on 2011-02-14
I still have not been able to solve this, I'm not sure what I'm looking for in the config.pl file but in the config.php the $data_dir is /var/lib/squirrelmail/data. I have done chown www-data to the data folder and chmod 777, still not able to log in.
 
I don't really understand the different permissions between using the IP address and the .com address. Wouldn't both be using the same Apache configuration files?
 
This is what the data folder looks like right now. I've also done chmod 777 -R but that didn't work either. 
 
```
total 12
drwxrwxrwx 2 www-data www-data 4096 2011-02-14 13:23 .
drwxr-xr-x 3 root     root     4096 2011-02-09 12:02 ..
-rw------- 1 www-data www-data  108 2011-02-14 13:23 postmaster@'website'.pref
```
 
Could there be something in Apache that is wrong? I did find an old post saying something about a safe mode but I can't find anything in the Apache directory relating to safe mode.
 
I also saw on the squirrel mail [http://squirrelmail.org/wiki/DataPermission](http://squirrelmail.org/wiki/DataPermission) page something about absolute paths, but I couldn't find anything in the config.pl file pointing to /var/lib/squirrelmail/data folder.

---

### Post by Lightning200MPH on 2011-02-17
I have not yet figured out my problem here. But I want to add that I setup my gmail account to get my mail from the server via POP3. So what would the difference be between that and going to my "website".com/webmail and using the pop3? Or I'm just looking in the wrong area.
 
This is what the mail log shows 
 
> Feb 17 15:29:23 server838 imapd: Connection, ip=[::1]
Feb 17 15:29:23 server838 imapd: LOGIN, [EMAIL="user=postmaster@*.com"]user=postmaster@*.com[/EMAIL], ip=[::1], port=[39639], protocol=IMAP
Feb 17 15:29:23 server838 imapd: LOGOUT, [EMAIL="user=postmaster@*.com"]user=postmaster@*.com[/EMAIL], ip=[::1], headers=0, body=0, rcvd=30, sent=238, time=0


---

### Post by elico on 2011-02-18
did you by any chance  tried to use a pop3 client or imap client on your computer?
cause if pop3 works for to gmail then any client can use it.
and you should think about "leave on server" for pop3 cause most of the clients erasing it from the server.

---

### Post by Lightning200MPH on 2011-02-18
I don't have a problem with mail being left on or deleted from the server. I can't log in if I try to do it through mywebsite.com/Squirrel . I was just trying the pop to see if it could log in through something else.

---

### Post by elico on 2011-02-19
and what the results?
in the log it seems fine so use my first advice.

remove the squirrel  mail that on your system.
download the original current version of squirrelmail from here:
[http://squirrelmail.org/countdl.php?fileurl=http%3A%2F%2Fprdownloads.sourceforge.net%2Fsquirrelmail%2Fsquirrelmail-1.4.21.tar.gz](http://squirrelmail.org/countdl.php?fileurl=http%3A%2F%2Fprdownloads.sourceforge.net%2Fsquirrelmail%2Fsquirrelmail-1.4.21.tar.gz)

(src= [http://squirrelmail.org/download.php](http://squirrelmail.org/download.php))

unpack the files in the /var/www directory and if you are using other the use the other directory.

make sure you have installed perl on your system and do the follow:
> cd /var/www/squirrelmail-directory/
mkdir mailinfo
chown -R www-data:www-data *
chmod -R 776 *
then run the file
> /var/www/squirrelmail/config/conf.pl
using the menu setup your settings and change the settings for your server and also change in the 
General Options menu the following:
Data Directory 
to
/var/www/squirrlemail-diretory/mailinfo/
save the settings 
and try to use the squirrel mail system.

the only reason in this case that it wont work is permission misconfigured or bad username.
also you can use the squirrel mail system on other working server to make sure that it's not a problem with your mail system and only php/permissions problem.

---

### Post by Lightning200MPH on 2011-02-22
I couldn't get that to work either, I'm thinking that there is a problem with the path to default_pref. I think the ../config/default_pref isn't pointing to the right directory. Squirrelmail from the "/var/www" directory is working, but from "/var/www/..../web1/web" is not. 
 
Is there a way to change the ../config/default_pref to the /var/lib/squirrelmail/data or to the right folder where it needs to be pointing?

---

