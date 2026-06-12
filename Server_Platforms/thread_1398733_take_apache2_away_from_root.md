---
title: "take apache2 away from root?"
date: 2010-02-04
forum: Server Platforms
---

### Post by Mykle87 on 2010-02-04
I think my apache2 is owned and running as root. I don't know if I installed it like a noob a while ago but I would like to secure it now especially since I just figured out how setup virtual hosts and I may want to eventually let people host sites on my server and I obviously don't want to have to give them root access. How can I confirm that apache2 is running as root and how do I take it away from the root user?

---

### Post by tr333 on 2010-02-04
Run the following in a terminal:
```
$ ps aux | grep apache
```

You should get output similar to the following:
```
root      2169  0.0  0.4  33076  9544 ?        Ss   Jan30   0:18 /usr/sbin/apache2 -k start
ubuntu       9679  0.0  0.0   3040   796 pts/0    R+   15:53   0:00 grep --color=auto apache
www-data 10793  0.0  0.3  33724  6508 ?        S    Feb02   0:00 /usr/sbin/apache2 -k start
www-data 19734  0.0  0.3  33732  6664 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 19736  0.0  0.3  33720  6592 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 19737  0.0  0.3  33352  6324 ?        S    Feb01   0:01 /usr/sbin/apache2 -k start
www-data 19738  0.0  0.3  33780  6772 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 20087  0.0  0.3  33736  6676 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 20088  0.0  0.3  33728  6628 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 22355  0.0  0.3  33736  6592 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 22356  0.0  0.3  33736  6640 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start
www-data 22447  0.0  0.3  33872  6676 ?        S    Feb01   0:00 /usr/sbin/apache2 -k start

```

What should be happening with apache on Ubuntu (and is shown above in the output) is that there is one process owned by root which starts all the child worker processes which do the actual web-server work.  These child processes are run under the www-data account (which has the home directory of /var/www as shown in /etc/passwd).  If it's working as intended, there should be no security issues as the root process is not handling any of the apache work.

---

### Post by Mykle87 on 2010-02-05
Ok awesome so one process is running as root and I see www-data for the others. If I wanted to allow people say sftp to edit a website, do I have to create new users and add them to the www-data group? The other thing that confuses me is that /var/www is owned by the root. Is that ok?

---

### Post by tr333 on 2010-02-05
I have my /var/www and subfolders owned by my user with group ownership of www-data.  This allows me to edit files in there as my user while allowing apache access to the files through the group permissions of www-data.

SFTP is basically just FTP over SSH, so if all users will be editing files in /var/www/ then you could add them all to www-data as long as www-data has group-write permissions for /var/www (which it should do if /var/www is chmod 775, instead of the normal 755).  You would probably want these new user accounts to be limited users (no Sudo access).

If the users will be running websites out of personal home directories (eg. /home/username/public_html for [http://url/~username](http://url/~username)) then you don't need to worry about /var/www as SFTP will give them access to their own home directories by default.

---

### Post by Lars Noodén on 2010-02-05
> **Mykle87 said:**
> Ok awesome so one process is running as root and I see www-data for the others. If I wanted to allow people say sftp to edit a website, do I have to create new users and add them to the www-data group? The other thing that confuses me is that /var/www is owned by the root. Is that ok?

Ownership by root is fine.  What you would like to avoid is the web-server (the group **www-data**) with write permissions.  As tr333 describes, set the group permissions for /var/www as read-write.

You may wish to set the guid bit, so that the files in the directories retain the same membership. 

You will need some other group than www-data to add users to. 
It is for the web server, not users.  

```

sudo chgrp -R webmeisters /var/www

# set permissions for dierctories
sudo find /var/www -type d -exec chmod u=rwx,g=rwx**s**,o=rx {} \;

# set permissions for files
sudo find /var/www -type d -exec chmod u=rw,g=rw,o=r {} \;


``` 

If you need different sets of permissions for more than one group per directory, then you should enable ACLs in the file system.  

If you can, have /var/www mounted as a separate file system.  That way if it fills up, it won't choke /tmp and /var/log to bring your system down.

If you have a really special or risky script, such as one that must *write* to, you can even run it as yet another user and group using [SUexecUserGroup](http://httpd.apache.org/docs/2.2/mod/mod_suexec.html#suexecusergroup)

I wish there were a practical way to contribute to the documentation and guides because this needs to be in there.  I'd kind of like to see the user wwww-data and group www-data renamed to _www-data and _www-data respectively so that users are less likely to use them for other than scripting.  At least the LAMP-server meta package should create a webmasters groups of some sort.

---

### Post by Lars Noodén on 2010-02-05
> **tr333 said:**
> SFTP is basically just FTP over SSH

Behaviorally, yes.  Using it is the same.  
But in truth it is a completely new, separate protocol not related to FTP.

The legacy work-around, FTPS, in contrast is actually FTP tunneled over SSL/TLS.  With SFTP, FTPS is not needed anymore and is far more difficult to set up.

---

### Post by Mykle87 on 2010-02-05
Thank you for all your help tr333 and Lars Nooden. If I do in fact want to set up new users to access their website files independently so I don't have to do everything for them, I will create new user accounts and put them in the www-data group and let them work out of their home directories.

---

