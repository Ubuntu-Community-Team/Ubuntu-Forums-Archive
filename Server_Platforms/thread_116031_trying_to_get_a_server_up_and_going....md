---
title: "trying to get a server up and going..."
date: 2006-01-11
forum: Server Platforms
---

### Post by drosetti on 2006-01-11
Well, I so far have made some progress, but I quickly came to a hault recently. 

Sor far I have, to my knowledge, successfully installed apache and php4. Now what I'm trying to do is setup an FTP server and a media streaming server. I have went to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) to try and see how it's done there, but I have run into some small problems. When I try to run the command "sudo apt-get install proftpd" it starts to install and then ends with errors. The errors would be as follow: 

```
Reading package lists... Done
Building dependency tree... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libapache-mod-php4 (4.3.10-10ubuntu3.6) ...
cp: cannot stat `/usr/share/doc/php4-common/examples/php.ini': No such file or directory
dpkg: error processing libapache-mod-php4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php4-mysql:
 php4-mysql depends on phpapi-20020918; however:
  Package phpapi-20020918 is not installed.
  Package libapache-mod-php4 which provides phpapi-20020918 is not configured yet.
dpkg: error processing php4-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache-mod-php4
 php4-mysql
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think it's just about the same for both programs when trying to install. Now I wish I could read that and tell what is wrong, but I am a newb at ubuntu and don't have that ability as of yet.

Another question I have is that I have files in my /var/www/ and of those files I have an index file. Now when I go to my IP address I thought that if I had a index file that it would just load that, but it doesn't seem to do that. 

Can anyone help a newb?

Thanks.

---

### Post by derelict on 2006-01-11
Start by running ```
apt-get update
``` to get the latest information about all packages. 
After that, there seems to be a dependency problem there: 
> dpkg: dependency problems prevent configuration of php4-mysql:
 php4-mysql depends on phpapi-20020918; however:
  Package phpapi-20020918 is not installed.
So you should first install the package that php4-mysql depends on - if you're still uneasy with apt you can always use synaptic, which is the more user friendly interface to apt (for instance, is would solve this dependency problem in a breeze by telling you you have to install other software before installing what you asked, and automatically doing it)

---

### Post by drosetti on 2006-01-11
I did run apt-get update.

What is this "synaptic" you speak of?

Thanks for the help.

---

### Post by Video Toaster on 2006-01-11
[QUOTE=drosetti]I did run apt-get update.

What is this "synaptic" you speak of?

Thanks for the help.[/QUOTE]

If you have Gnome installed, go to System --> System Setup (I think that's what it's called.. something like that) and then go to Synaptic Package Manager.

---

### Post by drosetti on 2006-01-11
I found out that on the site where ubuntu is trying to get the packages from, there are no files there.  
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/)
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/)
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/)
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/)

So in the etc/apt/source.list that you have to put the links to get the updates I put in:
```

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging 
main universe multiverse

```
Instead of:
```

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse

```


I'm not really sure if that's what I was supposed to do, but I tried running the update on that and it seemed to work. Now when I try to do "apt-get install proftpd" I get:

```

Reading package lists... Done
Building dependency tree... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libapache-mod-php4 (4.3.10-10ubuntu3.6) ...
cp: cannot stat `/usr/share/doc/php4-common/examples/php.ini': No such file or directory
dpkg: error processing libapache-mod-php4 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php4-mysql:
 php4-mysql depends on phpapi-20020918; however:
  Package phpapi-20020918 is not installed.
  Package libapache-mod-php4 which provides phpapi-20020918 is not configured yet.
dpkg: error processing php4-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache-mod-php4
 php4-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by spade_shark on 2006-01-12
Are you using the backports for the streaming media server part?  Becareful what you comment out of the sources list!  Any changes to this file will require you to issue an "apt-get update" command to resync the repos. system.  You must do this first to let the system update its records...then apt-get upgrade / install.

---

### Post by LordHunter317 on 2006-01-12
You don't have php4-common installed, or the version you have installed isn't compatible, and causing the installation of the apache module to fail.  I suspect you've mixed a backports package with an incompatible mainstream package.

---

### Post by drosetti on 2006-01-12
I've been trying to get this thing up. I did install php4 now I dont know what the difference in this and php4-common, I don't know. At this point I'm considering going back and just starting over. But I'm going to try one more thing on here. 

```

Reading package lists... Done
Building dependency tree... Done
php4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libapache-mod-php4 (4.3.10-10ubuntu3.6) ...
cp: cannot stat `/usr/share/doc/php4-common/examples/php.ini': No such file or directory
dpkg: error processing libapache-mod-php4 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache-mod-php4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This code is what I get when I do "apt-get install php4" I'm not sure, but I had a friend look at it and said to post this. 

Let me know if I can do something instead of starting over. 

Thanks for all the help.

---

### Post by imagine on 2006-01-12
[QUOTE=drosetti]I've been trying to get this thing up. I did install php4 now I dont know what the difference in this and php4-common, I don't know. At this point I'm considering going back and just starting over.[/QUOTE]It looks like that by replacing your sources.list with the one from ubuntuguide.org you borked your installation. ubuntuguide.org was made for Ubuntu 5.04 and has not been updated since months. Please don't use it anymore and don't recommend this site to others.
Try the Ubuntu FAQ ([http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)) instead.

---

### Post by Sef on 2006-01-13
Thank you derelict.  I was having a similar problem as drosetti, but by updating, I resolved my problems.

---

