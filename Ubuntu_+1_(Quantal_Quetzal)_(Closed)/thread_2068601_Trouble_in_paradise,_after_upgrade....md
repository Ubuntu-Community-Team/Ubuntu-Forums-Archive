---
title: "Trouble in paradise, after upgrade..."
date: 2012-10-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by zika on 2012-10-09
```
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
(Reading database ... 291217 files and directories currently installed.)
``````
Downloaded 64.4 kilobytes in 0 seconds. (305.93 KB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-contacts gnome-control-center gnome-control-center-data ifupdown
  libgnome-control-center1 python3-gdbm shared-mime-info update-notifier
  update-notifier-common xdg-user-dirs
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,038 kB of archives.
After this operation, 460 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
(Reading database ... 291217 files and directories currently installed.)
Preparing to replace update-notifier 0.122 (using .../update-notifier_0.123_amd64.deb) ...
Unpacking replacement update-notifier ...
Preparing to replace update-notifier-common 0.122 (using .../update-notifier-common_0.123_all.deb) ...
Unpacking replacement update-notifier-common ...
Preparing to replace ifupdown 0.7.2ubuntu1 (using .../ifupdown_0.7.2ubuntu2_amd64.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace python3-gdbm 3.2.3-1build1 (using .../python3-gdbm_3.3.0-1_amd64.deb) ...
Unpacking replacement python3-gdbm ...
Preparing to replace gnome-contacts 3.6.0-0ubuntu1 (using .../gnome-contacts_3.6.0-0ubuntu2_amd64.deb) ...
Unpacking replacement gnome-contacts ...
Preparing to replace libgnome-control-center1 1:3.4.2-0ubuntu18 (using .../libgnome-control-center1_3.4.2-0ubuntu19_amd64.deb) ...
Unpacking replacement libgnome-control-center1 ...
Preparing to replace gnome-control-center-data 1:3.4.2-0ubuntu18 (using .../gnome-control-center-data_3.4.2-0ubuntu19_all.deb) ...
Unpacking replacement gnome-control-center-data ...
Preparing to replace gnome-control-center 1:3.4.2-0ubuntu18 (using .../gnome-control-center_3.4.2-0ubuntu19_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Preparing to replace shared-mime-info 1.0-1ubuntu1 (using .../shared-mime-info_1.0-1ubuntu2_amd64.deb) ...
Unpacking replacement shared-mime-info ...
Preparing to replace xdg-user-dirs 0.14-0ubuntu3 (using .../xdg-user-dirs_0.14-0ubuntu4_amd64.deb) ...
Unpacking replacement xdg-user-dirs ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
-e 
```I've peaked in /usr/share/perl5/Debconf/DbDriver/File.pm but did not see obvious solution in several seconds I had to spare for that. I will look again after other job is done, if there is no solution in the meantime...
Not to mention that &#8222;# This file was preprocessed, do not edit!&#8220; petrified me...

---

### Post by wojox on 2012-10-09
```
sudo apt-get install debconf --reinstall
```

---

### Post by zika on 2012-10-09
> **wojox said:**
> ```
sudo apt-get install debconf --reinstall
```
```
:~$ sudo apt-get install debconf --reinstall
[sudo] password for zika: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 149 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ quantal/main debconf all 1.5.46ubuntu1 [149 kB]
Fetched 149 kB in 0s (485 kB/s) 
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
(Reading database ... 291222 files and directories currently installed.)
Preparing to replace debconf 1.5.46ubuntu1 (using .../debconf_1.5.46ubuntu1_all.deb) ...
Unpacking replacement debconf ...
Setting up debconf (1.5.46ubuntu1) ...
Setting up man-db (2.6.3-1) ...
Building database of manual pages ...
Setting up flashplugin-installer (11.2.202.243ubuntu1) ...
```It worked! You are (obviously) not **breaker** of packages... ;) Thank You...

Update: It surfaced again... I'll try to see what's wrong...
Update: This might be my fault. Putting /var/cache in tmpfs could have caused this. I'll investigate more...
Update: Yes, it seems that putting /var/cache in tmpfs produced this error. Mea culpa...

---

### Post by Paddy Landau on 2012-10-10
zika: How did you make the connection and realise that [FONT=Lucida Console]/var/cache[/FONT] was the problem? I would have been mystified!

BTW, you may want to [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by zika on 2012-10-10
> **Paddy Landau said:**
> zika: How did you make the connection and realise that [FONT=Lucida Console]/var/cache[/FONT] was the problem? I would have been mystified!

BTW, you may want to [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").Good bookkeeping... ;)
I've used tmpfs for year+ and somewhere in 12.04 testing I had to reinstall after too much tweak. At that moment I refrained from using tmpfs in order to be able to find culprit that made me reinstall. After reading aforementioned thread I've turned that „list“ on and problem surfaced. Serendipity...

---

### Post by Paddy Landau on 2012-10-10
> **zika said:**
> Good bookkeeping... [and] Serendipity...
I love good bookkeeping and serendipity! Thanks for the reply.

---

### Post by zika on 2012-10-10
> **Paddy Landau said:**
> I love good bookkeeping and serendipity! Thanks for the reply.OK, a bit of reading of error txt helped me also... ;)
:guitar:

---

