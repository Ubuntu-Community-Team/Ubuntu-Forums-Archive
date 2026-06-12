---
title: "[SOLVED] Apache2 + SVN + [SSL] +  403 Forbidden"
date: 2008-05-20
forum: Server Platforms
---

### Post by ntalamai on 2008-05-20
Hello,

I have googled hard enough to find a solution to my problem but no luck. Ok, I am not a Ubuntu expert, but I have already spent 1.5 days (and nights) on the problem. Any help will be much appreciated.

I recently upgraded from 7.10 to 8.04 hardy - 64 bit. In the upgraded system, I tried to install apache2 + svn, but unfortunately it does not seem to work.

Initially I tried to use SSL as well, so I followed the instructions on: 
[http://linuxhappy.wordpress.com/2008/01/21/sucess-subversion-apache2-ssl-ubuntu-710-with-users/]("http://linuxhappy.wordpress.com/2008/01/21/sucess-subversion-apache2-ssl-ubuntu-710-with-users/")
and
[http://ubuntuforums.org/showthread.php?t=51753]("http://ubuntuforums.org/showthread.php?t=51753")

Later on I gave up (because of a persistent 403 Forbidden error), so I tried the basic configuration steps (without SSL):
[https://help.ubuntu.com/8.04/serverguide/C/subversion.html]("https://help.ubuntu.com/8.04/serverguide/C/subversion.html")

Before trying, I uninstalled apache2, subversion and libapache2-svn doing:
sudo apt-get autoremove packages

I know this does not remove apache2 configuration files, so I tried to restore them into their original status by using copy-paste file contents from a fresh-install of Hardy on another machine. Btw is there a better approach to get a clean apache2 install? If I manually move /etc/apache2/ and /var/www/, when I try to reinstall apache2 I get error messages (some files are not found).

After following the steps on [http://help.ubuntu.com/8.04/serverguide/C/subversion.html]("http://help.ubuntu.com/8.04/serverguide/C/subversion.html"), I can create-checkout-commit-import to/from the repository when I access them locally, i.e. using the file:///... protocol.

When I try through http, I get 403 Forbidden error:
```
svn co http://localhost/svn Docs
Authentication realm: <http://localhost:80> Your repository name
Username: user1
Password for 'user1': ******
svn: PROPFIND request failed on '/svn'
svn: PROPFIND of '/svn': 403 Forbidden (http://localhost)
```

Btw, in firefox I can access [http://localhost](http://localhost) which shows "It works", but not [http://localhost/svn](http://localhost/svn) (again 403 message):
```

Forbidden

You don't have permission to access /svn on this server.
Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 Server at localhost Port 80
``` 
I get the 403 message after I authenticate using a username/password that I provided during the initial setup. This is shown a few steps below when I list the contents of apache2.conf. 


Apache2 error log: 
```
cat /var/log/apache2/error.log
....
[Tue May 20 14:57:30 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue May 20 14:57:40 2008] [notice] Apache/2.2.8 (Ubuntu) DAV/2 SVN/1.4.6 configured -- resuming normal operations
[Tue May 20 14:59:49 2008] [error] [client 127.0.0.1] (13)Permission denied: cannot read directory for multi: /var/www/
```

dav_svn.conf contents
```
cat /etc/apache2/mods-enabled/dav_svn.conf
# Everything in comments like this
```
Everything is in comments, because the official ubuntu instructions do not require to change this file. Instead, I changed apache2.conf:
```
cat /etc/apache2/apache2.conf
#Default apache configuration here.
#...
<Location /svn>
  DAV svn
  SVNPath /home/user1/svn
  AuthType Basic
  AuthName "Your repository name"
  AuthUserFile /etc/subversion/passwd
  #<LimitExcept GET PROPFIND OPTIONS REPORT>
  Require valid-user
  #</LimitExcept>
  </Location> 

```
Note that I have set it up so that I authenticate even when reading the repository. My tests above revealed that I need to authenticate, but after successful authentication I get the 403 message!

Finally the permissions for my svn repository are:
```
user1@ubuntuDesktop:~$ ls -ld /home/user1/svn
drwxr-xr-x 7 www-data www-data 4096 2008-05-20 14:48 /home/user1/svn

```

Do you have any ideas on how to troubleshoot this? That would be match appreciated. Does the "multi" keyword in apache2 play any role in that?

The funny this is that, the official ubuntu guidelines work on a fresh install of Hardy on an Intel-32 machine. The last thing I want is to format my current machine (AMD-64) and install Hardy fresh.

---

### Post by ntalamai on 2008-05-20
I wanted to add how I checkout my repository:

```
svn co file:///home/user1/svn Docs
A    Docs/a.txt
A    Docs/CPU.Benchmarks.txt

```

This apparently works without requesting a username/password.

---

### Post by ntalamai on 2008-05-21
The "solution" is to do:
sudo mkdir /var/www/svn/

Then everything works "almost" fine. I don't know why this is the case. I thought that the svn community is more related to the problem, so I posted in the SVN forums:
[http://www.svnforum.org/2017/viewtopic.php?t=6169](http://www.svnforum.org/2017/viewtopic.php?t=6169)

Hopefully they will provide a reason there.

---

### Post by ntalamai on 2008-05-22
Ok, after 3.5 days of hard work, I eventually figured that out. I had to do with multiviews, so I needed to disable multiviews in the default website. In other words change in
/etc/apache2/sites-available/default the lines:
<Directory /var/www/>
		Options Indexes FollowSymLinks Multiviews
to
<Directory /var/www/>
		Options Indexes FollowSymLinks

Then everything works like a charm. 

Can someone provide a sane explanation as to why this is the case?

Cheers.

---

