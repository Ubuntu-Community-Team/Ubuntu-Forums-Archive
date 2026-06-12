---
title: "Upgrading multiple servers in one go"
date: 2009-02-18
forum: Server Platforms
---

### Post by MeneM on 2009-02-18
Im trying to update and upgrade multiple servers in one go.

To do this, I was thinking to send my public key to remote root accounts, and then use the following "for loop" to do a lot of servers in one fell swoop:

```
for host in dms vpn misc www mysql nzb mail dns proxy asterisk samba bacula dhcp terminal adito cunico-ams; do echo $host; ssh root@$host '(aptitude update; aptitude dist-upgrade)'; done
```

But sometimes I'm getting the following error messages when debconf wants my attention:
```
misc
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages will be upgraded:
  libpq5 sudo 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 463kB of archives. After unpacking 4096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information...
Get:1 http://10.0.0.18 hardy-updates/main libpq5 8.3.6-0ubuntu8.04 [287kB]
Get:2 http://10.0.0.18 hardy-updates/main sudo 1.6.9p10-1ubuntu3.4 [176kB]
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
Fetched 463kB in 9s (46.7kB/s)
(Reading database ... 11323 files and directories currently installed.)
Preparing to replace libpq5 8.3.5-0ubuntu0.8.04 (using .../libpq5_8.3.6-0ubuntu8.04_i386.deb) ...
Unpacking replacement libpq5 ...
Preparing to replace sudo 1.6.9p10-1ubuntu3.3 (using .../sudo_1.6.9p10-1ubuntu3.4_i386.deb) ...
Unpacking replacement sudo ...
Setting up libpq5 (8.3.6-0ubuntu8.04) ...

Setting up sudo (1.6.9p10-1ubuntu3.4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...

```

See where it tries to get a terminal? well.. it cant ;)

Anyway to enhance this for loop a bit, or perhaps someone has a better way of doing this?

Thanks!

---

### Post by shizzy-t on 2009-02-18
I think if you ran it with 

rsh root@$host aptitude update; aptitude dist-upgrade

it would work.

---

### Post by MeneM on 2009-02-20
Excellent! that works like a charm.

Thanks!

---

### Post by HermanAB on 2009-02-20
There are versions of ssh that will log into multiple machines at once and execute the commands on all of them in parallel, for example pssh:
[http://www.theether.org/pssh/](http://www.theether.org/pssh/)

Of course, this works best when all machines are *exactly* the same, like in a high performance cluster.

Cheers,

Herman

---

### Post by ravedog on 2011-02-15
Hi!

Can anyone explain why the solution that shizzy-t mentions works and the $ssh user@host "CMD ; CDM" or $ssh user@host 'CMD ; CMD' dont work?

Thanks for solution btw, it helped me too :)

br,

Ravee

---

### Post by Vegan on 2011-02-15
I am lazy, I have all my machines on automatic updates

This way I can simply go back to sleep until something breaks.

---

### Post by zeugmatis on 2012-12-04
> **Vegan said:**
> I am lazy, I have all my machines on automatic updates

This way I can simply go back to sleep until something breaks.
Auto update has silently stopped working for me in the past, leaving systems vulnerable and wide open to security holes... hopefully it will work out better for you than it did me.

---

### Post by zeugmatis on 2012-12-04
The error message means what it says - there is no $TERM variable set.  To get rid of that message, you simply set that variable in your SSH commandline: 

ssh example.com "export TERM=xterm-256color; apt-get update; apt-get -y dist-upgrade; etc."

---

