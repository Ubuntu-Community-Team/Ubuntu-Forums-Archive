---
title: "Problem installing Mysql server with /tmp mounted noexec"
date: 2006-04-24
forum: Server Platforms
---

### Post by quackking on 2006-04-24
Hi. I am trying to install a mysql/postfix/cyrus package called web-cyradm under Ubuntu. I have done this several times successfully on Mandrake, no problem - it's a great package. Anyway, I obviously need MySql-server in order to make this work. I've got a new install of Dapper 6.06, which seems stable and is already running Apache just fine; I also installed Webmin, etc. The default Dapper install seemed to install MySql-server 5, but Webmin won't start it, and actually the only binaries there were mysql-ndb. 

I figured I would remove all MySql 5 stuff and go back to 4.x, which I am familiar with. Using Synaptic (yes, I know I *should* use only CLI to be a real admin, but I am lazy) I did remove the 5.x server, client, etc. 

I then went to install 4.x and it failed with these messages:

The following problems were found on your system:

E: /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb: subprocess pre-installation script returned error exit status 1


The detailed terminal contains this:

Preconfiguring packages ...
Can't exec "/tmp/mysql-server-4.1.config.10091": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/mysql-server-4.1.config.10091 configure  failed at /usr/share/perl5/Debconf/ConfModule.pm line 57
mysql-server-4.1 failed to preconfigure, with exit status 2
Selecting previously deselected package mysql-client-4.1.
(Reading database ... 111837 files and directories currently installed.)
Unpacking mysql-client-4.1 (from .../mysql-client-4.1_4.1.15-1ubuntu5_i386.deb) ...
Unpacking mysql-server-4.1 (from .../mysql-server-4.1_4.1.15-1ubuntu5_i386.deb) ...
Aborting downgrade from (at least) 5.0 to 4.1.
dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-client-4.1 (4.1.15-1ubuntu5) ...

------------

I have mounted /tmp as nouser and noexec - since I have seen various rootkit exploits use /tmp and /var/tmp to upload and then execute different exploits. 

Of course I can modify fstab and remount /tmp without those restrictions temporarily for this install, but it seems that is pretty klugy. Also, other apt-get tasks seem to work fine with the restrictions on /tmp.

Is there a workaround for this? Why should I have to mount a world-writable filesystem witn exec privileges? Ubuntu development team please feel free to weigh in here, even to flame. I don't get it.

Thanks in advance, and thanks for building what I think is the best distro out there.

/'quackking'

---

### Post by quackking on 2006-04-25
More info about this problem. I remounted /tmp as completely unrestricted, rebooted, tried all sorts of apt-get -f install mysql-server-4.1 commands - same result. Always ended up with Sub-process /usr/bin/dpkg returned an error code 1.

Interestingly, if I apt-get -f install mysql-server-5.0, it works. No problem.

Is there actually an issue with the mysql-server-4.1 deb file?

/'quackking'

---

### Post by da_g_bomb on 2007-02-18
No problem with the deb file, I found this, which sorted my problem

[http://nattster.blogspot.com/2006/07/downgrade-mysql-50-to-41.html]("http://nattster.blogspot.com/2006/07/downgrade-mysql-50-to-41.html")

Its to do with mysql5 files existing in /var/lib/mysql/

Like it says in the blog, a quick rm and you can install mysql-server-4.1 without any issues

---

