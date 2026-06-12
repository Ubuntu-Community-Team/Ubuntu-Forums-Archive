---
title: "sshfs and apache permissions errors"
date: 2009-11-18
forum: Server Platforms
---

### Post by altonbr on 2009-11-18
So I have a server in the house for web and file serving but my web development files are on my desktop, so instead of copying and pasting, or editing off the server all of the time, I decided to try and implement sshfs from the server to the desktop and have the server serve the files through Apache.

Easy enough right? These are the steps I followed on the server:

(1) Install sshfs
```
sudo aptitude install sshfs
```(2) Add myself to FUSE
```
sudo usermod  -a -G fuse brett
```(3) Make new www/ directory on my server
```
mkdir /home/brett/www
```(4) Edit Apache config to reflect change
(changed '/var/www/' to '/home/brett/www/'

(5) Reload Apache
```
sudo /etc/init.d/apache reload
```Test the server and Apache and everything is fine.

(6) Mount my desktop websites folder under /home/brett/www/ on my server
```
sshfs $user@$ip:/home/$user/websites /home/brett/www

```(7) Reload Apache once more...
```
$ sudo /etc/init.d/apache2 reload
```>  * Reloading web server config apache2                                          Warning: DocumentRoot [/home/brett/www/] does not existApparently the directory doesn't exist...

(8) Check if directory exists...

```
ls -lh
```> total 20K
drwxr-xr-x 4 brett brett 4.0K 2009-11-14 19:56 backups
drwxr-xr-x 1 brett brett 4.0K 2009-11-18 14:29 www
Yup... it exists.

(9) Try going to the IP address via Firefox
Apache:
> **Forbidden**

 You don't have permission to access / on this server.
(10) Check Apache error logs...
```
tail -n 4 /var/log/apache2/error.log
```> [Wed Nov 18 14:53:57 2009] [notice] Graceful restart requested, doing restart
Warning: DocumentRoot [/home/brett/www/] does not exist
[Wed Nov 18 14:53:58 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.7 with Suhosin-Patch configured -- resuming normal operations
[Wed Nov 18 14:58:02 2009] [error] [client $IP_address] (13)Permission denied: access to / deniedBut I can traverse to /home/brett/www and view and edit the files...

(11) Test via touch
```
touch /home/brett/www/test.txt
```no error...

(12) Try and change the permissions of the /home/brett/www/ for Apache's user www-data
```
sudo chown brett:www-data www
```> chown: cannot access `www': Permission deniedOkay... something is up. What am I doing wrong?

---

### Post by altonbr on 2009-11-18
I was able to get it running via:

```
sshfs -o allow_other,uid=1000,gid=1000
```as per [http://ubuntuforums.org/showpost.php?p=5424634&postcount=2](http://ubuntuforums.org/showpost.php?p=5424634&postcount=2)

---

### Post by novainvicta on 2011-01-04
add -o workaround=rename if you need to edit the file form apache to the sshfs

---

