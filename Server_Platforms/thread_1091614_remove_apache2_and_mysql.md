---
title: "remove apache2 and mysql"
date: 2009-03-09
forum: Server Platforms
---

### Post by funkyali on 2009-03-09
Hi

I wonder if someone here could help me with this question?

[http://ubuntuforums.org/showthread.php?t=1091367](http://ubuntuforums.org/showthread.php?t=1091367)

---

### Post by bluefrog on 2009-03-09
dpkg -l apache* mysql* | grep ii | awk '{ print $2 }' | xargs sudo apt-get remove --purge

sudo tasksel and unchecking LAMP should do the trick as well.

---

### Post by funkyali on 2009-03-09
I tried the first line of code and it just aborted.

```
user-laptop:~$ dpkg -l apache* mysql* | grep ii | awk '{ print $2 }' | xargs sudo apt-get remove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl linux-headers-2.6.27-7 libdbi-perl
  linux-headers-2.6.27-7-generic libapr1 libplrpc-perl libpq5 php5-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache2* apache2-mpm-prefork* apache2-utils* apache2.2-common*
  dovecot-common* dovecot-imapd* dovecot-pop3d* libapache2-mod-php5*
  libaprutil1* libdbd-mysql-perl* libmysqlclient15off* libqt4-sql-mysql*
  mysql-client-5.0* mysql-common* mysql-server* mysql-server-5.0* php5-mysql*
0 upgraded, 0 newly installed, 17 to remove and 14 not upgraded.
After this operation, 132MB disk space will be freed.
Do you want to continue [Y/n]? Abort.
user-laptop:~$ 

```

---

### Post by funkyali on 2009-03-09
when i try sudo tasksel it just gives me a blinking cursor

---

### Post by cdenley on 2009-03-09
Tasksel isn't very good with long tasks. Assuming you already deselected what you wanted to remove, it's probably doing it, just not printing any progress. As far as using apt-get, that command is a little over-complicated.
```

sudo apt-get remove --purge ^apache.* ^libapache.* ^mysql-server.*

```

---

### Post by funkyali on 2009-03-09
> **cdenley said:**
> Tasksel isn't very good with long tasks. Assuming you already deselected what you wanted to remove, it's probably doing it, just not printing any progress. As far as using apt-get, that command is a little over-complicated.
```

sudo apt-get remove --purge ^apache.* ^libapache.* ^mysql-server.*

```

I tried your code and still got the blinking cursor

```
user-laptop:~$ sudo apt-get remove --purge ^apache.* ^libapache.* ^mysql-server.*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting apache2-suexec-custom for regex ‘^apache.*’
Note, selecting apache2-utils for regex ‘^apache.*’
Note, selecting apache2-mpm-itk for regex ‘^apache.*’
Note, selecting apache-ssl for regex ‘^apache.*’
Note, selecting apache-common for regex ‘^apache.*’
Note, selecting apache for regex ‘^apache.*’
Note, selecting apache-utils for regex ‘^apache.*’
Note, selecting apache2-common for regex ‘^apache.*’
Note, selecting apache-perl for regex ‘^apache.*’
Note, selecting apache2-mpm-perchild for regex ‘^apache.*’
Note, selecting apache2-mpm-prefork for regex ‘^apache.*’
Note, selecting apache2 for regex ‘^apache.*’
Note, selecting apache2-threaded-dev for regex ‘^apache.*’
Note, selecting apache2.2-common for regex ‘^apache.*’
Note, selecting apache2-suexec for regex ‘^apache.*’
Note, selecting apache2-mpm-threadpool for regex ‘^apache.*’
Note, selecting apachetop for regex ‘^apache.*’
Note, selecting apache2-dev for regex ‘^apache.*’
Note, selecting apache2-threaded-dev for regex ‘apache2-dev’
Note, selecting apache2-doc for regex ‘^apache.*’
Note, selecting apache2-mpm-worker for regex ‘^apache.*’
Note, selecting apache2-mpm-event for regex ‘^apache.*’
Note, selecting apache2-mpm for regex ‘^apache.*’
Note, selecting apache-doc for regex ‘^apache.*’
Note, selecting apache2-src for regex ‘^apache.*’
Note, selecting apache2-prefork-dev for regex ‘^apache.*’
Note, selecting libapache-session-perl for regex ‘^libapache.*’
Note, selecting libapache-mod-ruby for regex ‘^libapache.*’
Note, selecting libapache2-mod-scgi for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-sys-group for regex ‘^libapache.*’
Note, selecting libapache2-mod-php5filter for regex ‘^libapache.*’
Note, selecting libapache-authenhook-perl for regex ‘^libapache.*’
Note, selecting libapache-dbilogger-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-shib for regex ‘^libapache.*’
Note, selecting libapache2-mod-python2.2 for regex ‘^libapache.*’
Note, selecting libapache2-mod-python2.3 for regex ‘^libapache.*’
Note, selecting libapache2-mod-python2.4 for regex ‘^libapache.*’
Note, selecting libapache2-mod-python2.5 for regex ‘^libapache.*’
Note, selecting libapache2-mod-python for regex ‘libapache2-mod-python2.5’
Note, selecting libapache2-mod-rpaf for regex ‘^libapache.*’
Note, selecting libapache2-mod-proxy-html for regex ‘^libapache.*’
Note, selecting libapache2-mod-evasive for regex ‘^libapache.*’
Note, selecting libapache2-svn for regex ‘^libapache.*’
Note, selecting libapache-mod-python2.1 for regex ‘^libapache.*’
Note, selecting libapache-mod-python2.2 for regex ‘^libapache.*’
Note, selecting libapache-configfile-perl for regex ‘^libapache.*’
Note, selecting libapache-mod-python2.3 for regex ‘^libapache.*’
Note, selecting libapache-asp-perl for regex ‘^libapache.*’
Note, selecting libapache-mod-fastcgi for regex ‘^libapache.*’
Note, selecting libapache2-mod-python for regex ‘^libapache.*’
Note, selecting libapache2-mod-ruby for regex ‘^libapache.*’
Note, selecting libapache-admin-config-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-log-sql-mysql for regex ‘^libapache.*’
Note, selecting libapache2-authcassimple-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-ocamlnet for regex ‘^libapache.*’
Note, selecting libapache-db-perl for regex ‘^libapache.*’
Note, selecting libapache-session-wrapper-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-musicindex for regex ‘^libapache.*’
Note, selecting libapache2-mod-bt for regex ‘^libapache.*’
Note, selecting libapache2-reload-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-bw for regex ‘^libapache.*’
Note, selecting libapache2-mod-jk for regex ‘^libapache.*’
Note, selecting libapache-gallery-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-vhost-hash-alias for regex ‘^libapache.*’
Note, selecting libapache-mod-ssl for regex ‘^libapache.*’
Note, selecting libapache-mod-jk for regex ‘^libapache.*’
Note, selecting libapache-mod-python for regex ‘^libapache.*’
Note, selecting libapache2-mod-passenger for regex ‘^libapache.*’
Note, selecting libapache2-webauth for regex ‘^libapache.*’
Note, selecting libapache2-modbt-perl for regex ‘^libapache.*’
Note, selecting libapache2-redirtoservname for regex ‘^libapache.*’
Note, selecting libapache-authcookie-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-radius for regex ‘^libapache.*’
Note, selecting libapache2-mod-macro for regex ‘^libapache.*’
Note, selecting libapache-singleton-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-perl2-dev for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-pgsql for regex ‘^libapache.*’
Note, selecting libapache2-mod-perl2-doc for regex ‘^libapache.*’
Note, selecting libapache2-authenntlm-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-fcgid for regex ‘^libapache.*’
Note, selecting libapache-sessionx-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-openid for regex ‘^libapache.*’
Note, selecting libapache-ruby1.8 for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-kerb for regex ‘^libapache.*’
Note, selecting libapache2-mod-apparmor for regex ‘^libapache.*’
Note, selecting libapache2-mod-layout for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-plain for regex ‘^libapache.*’
Note, selecting libapache2-mod-wsgi for regex ‘^libapache.*’
Note, selecting libapache-mod-log-sql-mysql for regex ‘^libapache.*’
Note, selecting libapache-htpasswd-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-suphp for regex ‘^libapache.*’
Note, selecting libapache-mod-auth-kerb for regex ‘^libapache.*’
Note, selecting libapache2-mod-bt-dev for regex ‘^libapache.*’
Note, selecting libapache2-mod-encoding for regex ‘^libapache.*’
Note, selecting libapache2-mod-python-doc for regex ‘^libapache.*’
Note, selecting libapache2-mod-defensible for regex ‘^libapache.*’
Note, selecting libapache2-mod-authnz-external for regex ‘^libapache.*’
Note, selecting libapache2-mod-log-sql-dbi for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-mysql for regex ‘^libapache.*’
Note, selecting libapache2-mod-speedycgi for regex ‘^libapache.*’
Note, selecting libapache2-mod-random for regex ‘^libapache.*’
Note, selecting libapache2-mod-fastcgi for regex ‘^libapache.*’
Note, selecting libapache2-modxslt for regex ‘^libapache.*’
Note, selecting libapache2-mod-log-sql for regex ‘^libapache.*’
Note, selecting libapache2-mod-line-edit for regex ‘^libapache.*’
Note, selecting libapache2-mod-perl2 for regex ‘^libapache.*’
Note, selecting libapache-ssi-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-dnssd for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-pam for regex ‘^libapache.*’
Note, selecting libapache2-mod-auth-shadow for regex ‘^libapache.*’
Note, selecting libapache2-mod-gnutls for regex ‘^libapache.*’
Note, selecting libapache2-mod-chroot for regex ‘^libapache.*’
Note, selecting libapache-mod-musicindex for regex ‘^libapache.*’
Note, selecting libapache2-mod-lisp for regex ‘^libapache.*’
Note, selecting libapache-mod-perl for regex ‘^libapache.*’
Note, selecting libapache-mod-php4 for regex ‘^libapache.*’
Note, selecting libapache-mod-php5 for regex ‘^libapache.*’
Note, selecting libapache2-mod-vhost-ldap for regex ‘^libapache.*’
Note, selecting libapache2-mod-neko for regex ‘^libapache.*’
Note, selecting libapache2-mod-mime-xattr for regex ‘^libapache.*’
Note, selecting libapache2-webkdc for regex ‘^libapache.*’
Note, selecting libapache2-mod-log-sql-ssl for regex ‘^libapache.*’
Note, selecting libapache2-redirtoservername for regex ‘^libapache.*’
Note, selecting libapache-dbi-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-mono for regex ‘^libapache.*’
Note, selecting libapache-mod-jk-doc for regex ‘^libapache.*’
Note, selecting libapache-request-perl for regex ‘^libapache.*’
Note, selecting libapache2-mod-php4 for regex ‘^libapache.*’
Note, selecting libapache2-mod-php5 for regex ‘^libapache.*’
Note, selecting libapache2-mod-removeip for regex ‘^libapache.*’
Note, selecting libapache2-mod-geoip for regex ‘^libapache.*’
Note, selecting libapache2-mod-apreq2 for regex ‘^libapache.*’
Note, selecting libapache2-mod-ldap-userdir for regex ‘^libapache.*’
Note, selecting libapache2-mod-jk2 for regex ‘^libapache.*’
Note, selecting libapache2-request-perl for regex ‘^libapache.*’
Note, selecting mysql-server-4.1 for regex ‘^mysql-server.*’
Note, selecting mysql-server-5.0 for regex ‘^mysql-server.*’
Note, selecting mysql-server for regex ‘^mysql-server.*’
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic libapr1 libaprutil1
  php5-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache2* apache2-mpm-prefork* apache2-utils* apache2.2-common*
  libapache2-mod-php5* mysql-server* mysql-server-5.0* php5-mysql*
0 upgraded, 0 newly installed, 8 to remove and 14 not upgraded.
After this operation, 98.2MB disk space will be freed.
Do you want to continue [Y/n]? Y

```

If I press ctrl + C then it seems to give me the command line back.
I tried unticking the LAMP server under Synaptic Package Manageing but it is greyed out and when I tick it it darkens but does not untick it.

---

### Post by cdenley on 2009-03-09
Once again, the "blinking cursor" probably just means it is in the middle of removing your packages. I don't remember there being a very long lag, but don't really feel like removing it for myself to find out. Just give the command a few minutes to work, and see if it finishes. If nothing happens, are you sure your hardware is working?
```

dmesg|tail

```

---

### Post by funkyali on 2009-03-09
somethign really strange. I noticed the update icon in the taskbar. So I tried to update the 14 recommended updates and it just gave me a blinking cursor as well.

---

### Post by funkyali on 2009-03-09
> **cdenley said:**
> Once again, the "blinking cursor" probably just means it is in the middle of removing your packages. I don't remember there being a very long lag, but don't really feel like removing it for myself to find out. Just give the command a few minutes to work, and see if it finishes. If nothing happens, are you sure your hardware is working?
```

dmesg|tail

```
I tried your command and it gave me this
```

user-laptop:~$ dmesg|tail
[ 4572.518085] Restarting tasks ... <6>ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 4572.628150] done.
[ 4574.426594] r8169: eth0: link down
[ 4574.426951] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4574.440894] ADDRCONF(NETDEV_UP): ath0: link is not ready
[ 4582.295623] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 4587.170564] type=1503 audit(1236629855.449:20): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=113 name="/proc/4778/net/if_inet6" pid=4779 profile="/usr/sbin/named"
[ 4587.187635] type=1503 audit(1236629855.465:21): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=113 name="/proc/4778/net/if_inet6" pid=4779 profile="/usr/sbin/named"
[ 4587.204646] type=1503 audit(1236629855.485:22): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=113 name="/proc/4778/net/if_inet6" pid=4779 profile="/usr/sbin/named"
[ 4592.588043] ath0: no IPv6 routers present

```

---

### Post by cdenley on 2009-03-09
> If I press ctrl + C then it seems to give me the command line back
How long exactly did you wait until you decided to kill the process?

---

### Post by funkyali on 2009-03-09
10 minutes

---

### Post by funkyali on 2009-03-09
still "running" after 20mins.

---

