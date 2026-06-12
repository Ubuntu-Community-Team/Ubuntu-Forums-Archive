---
title: "Error on port 80"
date: 2008-06-27
forum: Server Platforms
---

### Post by amai on 2008-06-27
Created 
FTP USERS

aaaaa
bbbbb
ccccc
AND
Websites
1111.com (site directory = 1111)
2222.com (site directory = 2222) 
3333.com (site directory = 3333)


before i was able to do the following on a directly connected PC

http//192.168.1.13/aaaa
http//192.168.1.13/bbbb
http//192.168.1.13/cccc 
Was able to see my uploaded files

ON websites was able to get my sites
[http://192.168.1.13/1111](http://192.168.1.13/1111)
[http://192.168.1.13/2222](http://192.168.1.13/2222)


NOW i am getting on both FTP and website

Not Found

The requested URL /aaaa was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 192.168.1.13 Port 80

****



Troubleshooting I have done so far.

1)FTP with any user works fine.
-->can upload and download from the server

2)[http://192.168.1.13](http://192.168.1.13) works and I get the following

Index of /
[ICO]	Name	Last modified	Size	Description
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 192.168.1.13 Port 80

==>Before if i did [http://192.168.1.13](http://192.168.1.13) was able to see all the directory and file uploaded, but now nothing just
the above.

3)Checked PORT 80 its open.

WHAT should i be looking at or what did I mess up. How to reverse this back to working order

---

### Post by beniwtv on 2008-06-27
Hi amai,

Did you recently update your installation or apply updates?

In that case apache could have been updated and overwritten the configuration. It usually asks you prior to overwriting anything, and if you click 'Install the package maintainer's version' it gets overwritten.

Cheers,

---

### Post by wdaniels on 2008-06-27
Also did you change any of the file ownership/permissions? With a standard setup, the user www-data needs to be able to read the files.

---

### Post by amai on 2008-06-30
Hi Guys,
still unable to fix this...
What file/config I should be looking at.
(Command will be much appreciated, {google but couldnt get anything}).

I still cant access my sites from a directly connected pc to server)
 
JUST thought of posting some logs to see if this might help


root@ubuntu:/home/myname# nmap localhost
Interesting ports on localhost (127.0.0.1):
Not shown: 1691 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
23/tcp    open  telnet
80/tcp    open  http=======>PORT 80 is open
443/tcp   open  https
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap finished: 1 IP address (1 host up) scanned in 0.166 seconds

root@ubuntu:/var/www# ls            ==========================>I can see FTP and Web Users
apache2-default  aaaa  bbbb   cccc    webmin_1.380_all.deb
1111        2222    3333  webalizer  test

root@ubuntu:/var/www/aaaa# ls       ==========================>Can see file and documnets inside a website
about.html    dont worry.html  aaaaclogofooter.jpg
contact.html  index.html       aaaalogo.jpg

root@ubuntu:/etc/apache2/sites-available# ls==================>can see all sites
[www.aaaa.com](www.aaaa.com)    default        
[www.cccc.com](www.cccc.com)    [www.bbbb.com](www.bbbb.com)




root@ubuntu:/var/www# ls -l
total 12744
drwxr-xr-x 2 root       root     4096 2008-04-24 06:44 apache2-default
drwxr-xr-x 2 www-data   root     4096 2008-06-22 02:02 1111
drwxr-xr-x 2      2222  root     4096 2008-06-20 12:15 2222
drwxr-xr-x 2       1003 root     4096 2008-06-20 04:37 aaaa
drwxr-xr-x 2 bbbb       root     4096 2008-06-20 08:56 bbbb
drwxr-xr-x 2 3333       root     4096 2008-06-28 04:23 3333
drwxr-xr-x 2 test       root     4096 2008-06-28 04:08 test
drwxr-xr-x 2 root       root     4096 2008-06-04 00:00 webalizer
-rw-r--r-- 1 root       root 12988458 2007-11-08 13:25 webmin_1.380_all.deb
drwxr-xr-x 2 webuser001 root     4096 2008-06-20 08:52 webuser001
root@ubuntubaba:/var/www# cd cccc
root@ubuntubaba:/var/www/cccc# ls -l
total 140
-rw-r--r-- 1 cccc   cccc  3052 2008-06-20 12:10 about.html
-rw-r--r-- 1 cccc   cccc  2595 2008-06-20 12:12 contact.html
-rw-r--r-- 1 cccc   cccc 67244 2008-06-28 04:24 dont worry.html
-rw-r--r-- 1 cccc   cccc  4986 2008-06-20 12:14 index.html
-rw-r--r-- 1 cccc   cccc 11455 2008-06-20 12:16 3333logofooter.jpg
-rw-r--r-- 1 cccc   cccc  39687 2008-06-20 12:15 3333logo.jpg
******
******

l
root@ubuntu:/etc/apache2/sites-available# ls -l
total 24
-rw-r--r-- 1 root root 1233 2008-06-22 02:00 aaaa.com
-rw-r--r-- 1 root root 1183 2007-10-05 11:54 default
-rw-r--r-- 1 root root 1238 2008-06-20 11:45 bbbb.com
-rw-r--r-- 1 root root 1183 2008-06-27 11:28 [www.aaaa.com](www.aaaa.com)
-rw-r--r-- 1 root root 1183 2008-06-27 11:26 [www.bbbb.com](www.bbbb.com)
-rw-r--r-- 1 root root 1237 2008-06-28 02:51 [www.cccc.com](www.cccc.com)
root@ubuntu:/etc/apache2/sites-available#

---

### Post by beniwtv on 2008-06-30
Hey amai,

If you're using the default apache configuration, the sites should be in 

```
/etc/apache2/sites-enabled
```

not 

```
/etc/apache2/sites-available
```

Cheers,

---

### Post by wdaniels on 2008-06-30
> **beniwtv said:**
> Hey amai,

If you're using the default apache configuration, the sites should be in 

```
/etc/apache2/sites-enabled
```

not 

```
/etc/apache2/sites-available
```

Cheers,

No, they should be in sites-available, but if they are enabled (a2ensite) there should be a symbolic link from sites-available to sites-enabled (i.e. the files will appear in both).

Like I suggested before, your problem looks like the permissions. If you have apache configured normally for Ubuntu then the user www-data needs to be able to access the files you have under /var/www but your output shows different:

```
drwxr-xr-x 2 www-data root 4096 2008-06-22 02:02 1111
drwxr-xr-x 2 2222 root 4096 2008-06-20 12:15 2222
```

Here you can see that www-data can read the directory 1111 (so you should be able to see at least that one) but 2222 is owned by 2222:root (user:group) so www-data will not be able to read it unless you added www-data to the root group, which is not a good idea.

You need to have a proper think about how you want the permissions here to be organised, e.g. does each user need to own his/her files? What I would suggest you do is change these permissions so that the user owns his/her files, but www-data is added as the group with read permissions, for example to reset permissions for user aaaa:

```
sudo chown -R aaaa:www-data /var/www/aaaa
```

Do this for all the users, then set the permissions for /var/www generally:

```
sudo chmod -R 640 /var/www
sudo chmod -R ug+X /var/www
```

The first line gives read/write permission to the user that owns the file, and read permission to the web server. The second line gives permission to list the directory contents (without also giving execute permissions to files, otherwise you could just use 750 in the first line). Use the man pages for chown and chmod (e.g. type "man chmod" in a terminal) to understand what these things do - you have to know this stuff if you intend to administer any kind of web server, for whatever purpose.

If just setting the permissions doesn't do it, the other thing to check is that there is a Directory directive in the relevant apache configs to allow access to the relevant location(s).

Also, why do you have these duplicates in /etc/apache2/sites-available where there is both aaaa.com and [www.aaaa.com?](www.aaaa.com?) Are both of them actually enabled? You should find out which are actually enabled and clean that up.

---

### Post by beniwtv on 2008-06-30
> **wdaniels said:**
> No, they should be in sites-available, but if they are enabled (a2ensite) there should be a symbolic link from sites-available to sites-enabled (i.e. the files will appear in both).

/me makes note to self: *Do the things the debian way next time*. I did not know they were symbolic links, as I normally put my files directly in there. Duh... you learn something new every day!

Cheers,

---

### Post by wdaniels on 2008-06-30
> **beniwtv said:**
> /me makes note to self: *Do the things the debian way next time*. I did not know they were symbolic links, as I normally put my files directly in there. Duh... you learn something new every day!

Cheers,

Lol, don't worry I made the same assumption initially - I thought that the files would just get moved between the two until I actually had cause to set up multiple sites and enable/disable them one time :D I have to admit that I don't tend to read the documentation until something isn't working. Debianization is both a curse and a blessing at times.

---

### Post by beniwtv on 2008-06-30
> **wdaniels said:**
> Debianization is both a curse and a blessing at times.

I agree. On debian, everything seems so "nice" and tidy, but you have to learn new ways also. (Coming from Fedora on my work place).

Cheers,

---

### Post by amai on 2008-07-06
Ummm still an on going issue.
Should I reformat and start again???? OR just delete the ftp users and websites???/

Have changed the permission as mentioned above but now getting the following errors:

Forbidden

You don't have permission to access / on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 192.68.1.13 Port 80

EVEN this one 

2)[http://192.168.1.13](http://192.168.1.13) (WHICH was working before)

You don't have permission to access / on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 mod_ssl/2.2.4 OpenSSL/0.9.8e Server at 192.68.1.13 Port 80



3) QOUTE:If just setting the permissions doesn't do it, the other thing to check is that there is a Directory directive in the relevant apache configs to allow access to the relevant location(s).

WHERE & HOW to check the above

4)LOG File


Tue Jul 08 02:00:36 2008] [error] [client 192.68.1.13] (13)Permission denied: access to /aaaa denied
[Tue Jul 08 02:00:37 2008] [error] [client 192.68.1.13] (13)Permission denied: access to /favicon.ico denied
[Tue Jul 08 02:00:57 2008] [error] [client 192.68.1.13] (13)Permission denied: access to / denied
[Tue Jul 08 02:01:05 2008] [error] [client 192.68.1.13] (13)Permission denied: access to / denied
[Tue Jul 08 02:01:14 2008] [error] [client 192.68.1.13] (13)Permission denied: access to /bbbb denied
[Tue Jul 08 02:02:20 2008] [error] [client 192.68.1.13] (13)Permission denied: access to /1111 denied
[Tue Jul 08 02:02:46 2008] [error] [client 192.68.1.13] (13)Permission denied: access to / denied

*****************


total 12744
drwxr-x--- 2 root       root         4096 2008-04-24 06:44 apache2-default
drwxr-x--- 2 aaaa   www-data      4096 2008-06-22 02:02 aaaa
drwxr-x--- 2 bbbb   www-data      4096 2008-06-20 12:15 bbbb
drwxr-x--- 2       1003 root      4096 2008-06-20 04:37 mhata
drwxr-x--- 2 1111   www-data      4096 2008-06-20 08:56 1111
drwxr-x--- 2 2222   www-data      4096 2008-06-28 04:23 2222
drwxr-x--- 2 test23     root         4096 2008-06-28 04:08 test23
drwxr-x--- 2 root       root         4096 2008-07-01 07:45 webalizer
-rw-r----- 1 root       root     12988458 2007-11-08 13:25 webmin_1.380_all.deb
drwxr-x--- 2 webuser    :root         4096 2008-06-20 08:52 webuser


**************
:confused::confused::

---

