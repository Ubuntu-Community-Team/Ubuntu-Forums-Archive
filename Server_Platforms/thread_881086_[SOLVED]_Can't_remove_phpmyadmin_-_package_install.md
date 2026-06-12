---
title: "[SOLVED] Can't remove phpmyadmin - package install"
date: 2008-08-05
forum: Server Platforms
---

### Post by a.thomas on 2008-08-05
Hey all,

I have been working little by little to get a LAMP server up and running. I have Apache 2 working fine, PHP working fine and MySQL working fine. I wanted to use phpmyadmin. 
So I ran
```
sudo apt-get install phpmyadmin
```

Did not work. Then I read that there has to be an include in the apache.conf file:
Include /etc/phpmyadmin/apache.conf

so I added that and it still did not work.

So I decided to uninstall and reinstall thinking it might have been the package I got.

Here is what I get:
```
sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 10.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 95670 files and directories currently installed.)
Removing phpmyadmin ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So I did a lot of looking on the web and found some things to try such as looking at the phpmyadmin.prerm and phpmyadmin.postrm scripts. The phpmyadmin.postrm was blank and still is. The phpmyadmin.prerm script is blank also.
I didn't think this was correct but couldn't find anything about them.

I have tried:
```
sudo dpkg --remove --force-remove-reinstreq phpmyadmin
(Reading database ... 95670 files and directories currently installed.)
Removing phpmyadmin ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 phpmyadmin
```

Also tried:
```
 sudo dpkg-reconfigure phpmyadmin
apache2: Syntax error on line 300 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
   ...fail!
invoke-rc.d: initscript apache2, action "reload" failed.
```

This is line 300 of /etc/apache2/apache2.conf:
Include /etc/apache2/conf.d/

I am really out of ideas. I really just want it to truly go away so I can reinstall it.

Any ideas/suggestions will be greatly appreciated!

Thanks AT

---

### Post by a.thomas on 2008-08-06
Anybody?

I am really stuck... someone has to have an idea.

---

### Post by a.thomas on 2008-08-06
Solved my own problem...

---

### Post by Kolipoki on 2008-08-07
> **a.thomas said:**
> Solved my own problem...
I wish I could have helped, but honestly didn't know the answer. Nonetheless, would be great for the community if your solution is posted here. Could help someone -including myself- in the future. :)

---

### Post by a.thomas on 2008-08-07
Well, after extension searching and finding things I already tried, I went to where the phpmyadmin.prerm, phpmyadmin.postrm, etc scripts where and deleted them manually.

```
cd /var/lib/dpkg/info/
```
```
 ls -l phpmyadmin.*
-rw-r--r-- 1 root root   165 2008-03-05 21:42 phpmyadmin.conffiles
-rwxr-xr-x 1 root root   287 2008-03-05 21:42 phpmyadmin.config
-rw-r--r-- 1 root root 33524 2008-08-06 11:31 phpmyadmin.list
-rw-r--r-- 1 root root 51996 2008-03-05 21:42 phpmyadmin.md5sums
-rwxr-xr-x 1 root root  3286 2008-03-05 21:42 phpmyadmin.postinst
-rwxr-xr-x 1 root root  1762 2008-03-05 21:42 phpmyadmin.postrm
-rwxr-xr-x 1 root root  1762 2008-08-06 09:12 phpmyadmin.postrm.orig
-rwxr-xr-x 1 root root   339 2008-03-05 21:42 phpmyadmin.preinst
-rw-r--r-- 1 root root 22441 2008-03-05 21:42 phpmyadmin.templates
```

then I deleted those files
```
sudo rm -r phpmyadmin.*
```

then I ran
```
sudo apt-get clean
```
```
sudo apt-get update
```

I wanted to see if the package was still around, so I ran
```
sudo apt-get remove phpmyadmin
```

I got the response that the package was not installed so it couldn't not be removed.

FINALLY!

So from there I just ran
```
sudo apt-get install phpmyadmin
```

and voila! Back to normal.

I hope this does help someone, because I look to Ubuntu forums for a lot of answers.

Thanks,
AT

---

### Post by Kolipoki on 2008-08-07
Well thx, I wish I had those lines some weeks ago.

---

### Post by a.thomas on 2008-08-07
Nobody had any suggestions, so I just made it happen...

---

### Post by paulochf on 2010-07-13
Wow! Thank you!

Yes, it helped someone! =)

---

### Post by icd* on 2010-08-11
add me to that list ofpeople it helped ;D thanks.

---

### Post by HerixFromParis on 2010-09-16
I had a similar problem (though not exactly the same). Bottom line : stuck with a half-baked install of phpmyadmin, couldn't remove it, got bunches of the likes of 
```
/var/lib/dpkg/info/phpmyadmin.postinst: 42: dbc_go: not found
```

and though I don't perfectly understand the hows and whys of what you did it inspired me and I also removed all the phpmyadmin.* in 
```
/var/lib/dpkg/info/
```
and thus was able to remove phpmyadmin.

Thanxxxxxxxxxxxxxxx ! :p

---

### Post by t1m3 on 2010-12-13
post #5 works like a charm, now, when I got to this step:
matt$ sudo apt-get remove phpmyadmin

It was still there so I read what it said and it suggests typing:
matt$ sudo apt-get autoremove

then typed:
matt$ sudo apt-get remove phpmyadmin

and it was finally worked!! thank you sooo much, looked all afternoon and this is the first good solution I've found.  THis should be stickied.

---

### Post by willow315 on 2011-03-13
I have followed all these steps, and there are still files in /etc/phpmyadmin

The real issue, here, is that I've installed and uninstalled phpMyAdmin about 6 times now, and cannot access it via [http://localhost/phpmyadmin](http://localhost/phpmyadmin). 

I'm running Ubuntu 10.04 in VirtualBox on a MAC. 

I have installed the LAMP stack using apt-get....everything else works fine. 

I just can't get phpMyAdmin to work. I've gotten it to work on a number of different platforms and situations, and am totally frustrated. 

Can anyone think of anything else to do? I don't know if I should delete the files that remain in /etc/phpmyadmin, and try a different way of installing this? 

Thanks for any help you can give. WCW

---

### Post by bloodhacker2 on 2011-03-21
ok i am having the same problem and i followed all of your steps. 

after following your steps i tried to remove my phpadmin and got the same error.

```
bla-desktop:~$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package phpmyadmin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libdc1394-22 python-renderpm libftgl2 libopenjpeg2 python-lxml
  python-reportlab-accel libavformat52 wwwconfig-common libalut0 gettext
  python-numpy libjs-mootools cvs libwmf-bin libmagick++2 python-uniconvertor
  blender javascript-common perlmagick inkscape python-reportlab libavdevice52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up dkimproxy (1.2-3) ...
addgroup: The group `dkimproxy' already exists as a system group. Exiting.
The system user `dkimproxy' already exists. Exiting.
 * Starting inbound DomainKeys-filter dkimproxy.in                              Unknown option: hostname
Usage:
      dkimproxy.in [options] LISTENADDR:PORT RELAYADDR:PORT
        smtp options:
          --conf_file=FILENAME
          --listen=LISTENADDR:PORT
          --relay=RELAYADDR:PORT
          --reject-error

        verification options:
          --reject-fail
          --hostname=HOSTNAME

        daemon options:
          --daemonize
          --user=USER
          --group=GROUP
          --pidfile=PIDFILE

      dkimproxy.in --help
        to see a full description of the various options

                                                                         [fail]
invoke-rc.d: initscript dkimproxy, action "start" failed.
dpkg: error processing dkimproxy (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 dkimproxy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so then i thought, well im going to try to install phpmyadmin again and see what happens.

everything seemed to be going fine, it asked my for a admin password to use for the mysql and theni get this. 

```
bla-desktop:~$ sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdc1394-22 python-renderpm libftgl2 libopenjpeg2 python-lxml
  python-reportlab-accel libavformat52 libalut0 gettext python-numpy cvs
  libwmf-bin libmagick++2 python-uniconvertor blender perlmagick inkscape
  python-reportlab libavdevice52
Use 'apt-get autoremove' to remove them.
Recommended packages:
  php5-gd
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 4,285kB of archives.
After this operation, 17.4MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe phpmyadmin 4:3.3.2-1 [4,285kB]
Fetched 4,285kB in 37s (116kB/s)                                               
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 224868 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a3.3.2-1_all.deb) ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up dkimproxy (1.2-3) ...
addgroup: The group `dkimproxy' already exists as a system group. Exiting.
The system user `dkimproxy' already exists. Exiting.
 * Starting inbound DomainKeys-filter dkimproxy.in                              Unknown option: hostname
Usage:
      dkimproxy.in [options] LISTENADDR:PORT RELAYADDR:PORT
        smtp options:
          --conf_file=FILENAME
          --listen=LISTENADDR:PORT
          --relay=RELAYADDR:PORT
          --reject-error

        verification options:
          --reject-fail
          --hostname=HOSTNAME

        daemon options:
          --daemonize
          --user=USER
          --group=GROUP
          --pidfile=PIDFILE

      dkimproxy.in --help
        to see a full description of the various options

                                                                         [fail]
invoke-rc.d: initscript dkimproxy, action "start" failed.
dpkg: error processing dkimproxy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up phpmyadmin (4:3.3.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]

Errors were encountered while processing:
 dkimproxy
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i have installed severs servers on ubuntu and have never had this problem.

the error seems to be with the dkimproxy...

what do you think?

---

### Post by geniegl on 2012-02-01
> **a.thomas said:**
> Nobody had any suggestions, so I just made it happen...

haha good answer to nobody :lolflag:

but it remove all phpmyadmin, thx

---

