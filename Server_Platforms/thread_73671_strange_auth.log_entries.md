---
title: "strange auth.log entries"
date: 2005-10-09
forum: Server Platforms
---

### Post by Dooglus on 2005-10-09
I'm running ubuntu breezy, and sometimes I see a few entries in /var/log/auth.log like this:

```

Oct  9 07:41:32 localhost su[26759]: + ??? root:chris
Oct  9 07:41:32 localhost su[26759]: (pam_unix) session opened for user chris by (uid=0)
Oct  9 07:41:33 localhost su[26759]: (pam_unix) session closed for user chris
Oct  9 07:41:37 localhost su[26778]: + ??? root:chris
Oct  9 07:41:37 localhost su[26778]: (pam_unix) session opened for user chris by (uid=0)
Oct  9 07:41:38 localhost su[26778]: (pam_unix) session closed for user chris
Oct  9 07:41:38 localhost su[26780]: + ??? root:chris
Oct  9 07:41:38 localhost su[26780]: (pam_unix) session opened for user chris by (uid=0)
Oct  9 07:41:38 localhost su[26780]: (pam_unix) session closed for user chris
Oct  9 07:41:38 localhost su[26782]: + ??? root:chris
Oct  9 07:41:39 localhost su[26782]: (pam_unix) session opened for user chris by (uid=0)
Oct  9 07:41:39 localhost su[26782]: (pam_unix) session closed for user chris

```

It looks like 'root' is su'ing to my account very quickly.  There's less than a second between some su's...

Can that be anything other than a hacker?  Should I be worried?

Also, apt-get keeps breaking.  The files in /var/lib/apt/lists keep disappearing, so I see this:

```

chris@chrislap:~$ sudo apt-get upgrade
Password:
Reading package lists... Done

Building dependency tree... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

Doing an apt-update brings them back, but why are they disappearing?  This has happened twice now, and I'm sure I've not deleted them.

```

chris@chrislap:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release [30.9kB]
Get:3 http://archive.ubuntu.com breezy/main Packages [584kB]
Get:4 http://archive.ubuntu.com breezy/restricted Packages [5041B]
Get:5 http://archive.ubuntu.com breezy/universe Packages [2294kB]
Get:6 http://archive.ubuntu.com breezy/multiverse Packages [91.9kB]
Get:7 http://archive.ubuntu.com breezy/main Sources [231kB]
Get:8 http://archive.ubuntu.com breezy/restricted Sources [1458B]
Get:9 http://archive.ubuntu.com breezy/universe Sources [909kB]
Get:10 http://archive.ubuntu.com breezy/multiverse Sources [46.9kB]
Fetched 4195kB in 26s (158kB/s)
Reading package lists... Done

chris@chrislap:~$ ls /var/lib/apt/lists
archive.ubuntu.com_ubuntu_dists_breezy_Release
archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_multiverse_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_breezy_universe_source_Sources
lock
partial
chris@chrislap:~$ 

```

Any help appreciated!  Thanks.

---

### Post by Wide on 2005-10-09
I have not seen that far as the 'su -' goes on my system
May just be a process trying to run


You 'apt-get install chkrootkit'

Run it to see if you have any root kits.

Open a terminal & run

'sudo tail -f /var/log/auth.log'

This will give you a running tail on the auth.log

open another terminal & do a 'w' this will show all users on the system

Watch these for a while.

You can also see what process's are running with 'ps -ax | more'
This will tell you whats going on



Hope this helps :cool:

---

