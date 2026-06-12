---
title: "bind9 restart error"
date: 2010-12-30
forum: Server Platforms
---

### Post by fast_eddie on 2010-12-30
Hi,

First of all I'm new to Ubuntu and Linux, however I'm learning fast but having some issues with getting what shoould be a simple config to work.

All I'm trying to do is use forwarders (using the primary and secondary DNS from my hosting partner) not host the zone files locally at this stage, as I have name servers associated with my domain registrar.

I've used webmin to double check the basic bind9 config files, initially the fault reporting using default rndc.conf config files etc so I manually editted and renamed the associated rndc.conf and rndc.key files. Updated the named.conf and named.conf.options files to be synchronised.
> *Files and locations that have been changed from default:*
/etc/named.conf
/etc/config-file.conf
/etc/bind/named.conf
/etc/bind/config-file.conf
/etc/bind/key-file.key
/var/named/run-root/etc/named.conf
I can start the bind service within webmin or atleast it reports that it has started.
But when I issue the restart command I now see 'permission denied' errors associated with /etc/named.conf

This is the trace when I attempt to start the bind9 service:
> root@crm:~# tail -f /var/log/syslog
Dec 30 21:41:16 crm named[3107]: loading configuration from '/etc/named.conf'
Dec 30 21:41:16 crm named[3107]: [COLOR=Red]none:0: open: /etc/named.conf: permission denie d[/COLOR]
Dec 30 21:41:16 crm named[3107]: [COLOR=Red]loading configuration: permission denied[/COLOR]
Dec 30 21:41:16 crm named[3107]: exiting (due to fatal error)
Dec 30 21:41:16 crm kernel: [ 1544.403140] type=1503 audit(1293745276.074:15): operation="open" pid=3108 parent=3106 profile="/usr/sbin/named" requested_mask=" ::r" denied_mask="::r" fsuid=104 ouid=0 name="/var/named/run-root/etc/named.conf "
Dec 30 21:45:01 crm CRON[3200]: (psaadm) CMD (/usr/local/psa/admin/bin/php /opt/ plesk-billing/admin/sbin/runevents.php > /dev/null 2>&1)
Dec 30 21:50:01 crm CRON[3260]: (psaadm) CMD (/usr/local/psa/admin/bin/php /opt/ plesk-billing/admin/sbin/runevents.php > /dev/null 2>&1)
Dec 30 21:50:01 crm CRON[3261]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache2/access.log ] && /usr/lib /cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Dec 30 21:52:01 crm CRON[3309]: (root) CMD (/opt/psa/admin/sbin/backupmng >/dev/ null 2>&1)
Dec 30 21:55:01 crm CRON[3465]: (psaadm) CMD (/usr/local/psa/admin/bin/php /opt/ plesk-billing/admin/sbin/runevents.php > /dev/null 2>&1)
Dec 30 21:57:38 crm named[3529]: **starting BIND 9.7.0-P1 -t /var/named/run-root -c /etc/named.conf -u bind**
Dec 30 21:57:38 crm named[3529]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
Dec 30 21:57:38 crm named[3529]: adjusted limit on open files from 1024 to 1048576
Dec 30 21:57:38 crm named[3529]: found 1 CPU, using 1 worker thread
Dec 30 21:57:38 crm named[3529]: using up to 4096 sockets
Dec 30 21:57:38 crm named[3529]: [COLOR=Red]loading configuration from '/etc/named.conf'[/COLOR]
Dec 30 21:57:38 crm named[3529]: [COLOR=Red]none:0: open: /etc/named.conf: permission denied[/COLOR]
Dec 30 21:57:38 crm named[3529]: [COLOR=Red]loading configuration: permission denied[/COLOR]
Dec 30 21:57:38 crm named[3529]: exiting (due to fatal error)
Dec 30 21:57:38 crm kernel: [ 2523.894162] type=1503 audit(1293746258.064:16): operation="open" pid=3530 parent=3528 profile="/usr/sbin/named" requested_mask="::r" denied_mask="::r" fsuid=104 ouid=0 name="/var/named/run-root/etc/named.conf" So for some reason the /etc/named.conf file is reporting 'permission denied' when being loaded, yet I have double checked the secret key is synchronised with that of the renamed rndc.conf file...

Where am I going wrong please???

---

### Post by CharlesA on 2010-12-30
Sounds like a permission problem to be honest.

What are the permissions of /etc/named.conf ?

---

### Post by fast_eddie on 2010-12-30
Hi Charles


> 
root@crm:~# ls -l /etc/named.conf
lrwxrwxrwx 1 root root 34 2010-12-24 02:11 /etc/named.conf -> /var/named/run-root/etc/named.conf


---

### Post by CharlesA on 2010-12-30
Hrm, that looks right.

Is it in a chroot?

---

### Post by fast_eddie on 2010-12-30
According to webmin yes, or should I say it is assuming its is under a chroot directory. How would I check manually?

---

### Post by CharlesA on 2010-12-30
I don't know. I haven't really set up BIND.

I found an ancient thread about it [here]("http://ubuntuforums.org/showthread.php?t=110998").

There's a [tutorial]("http://unixwiz.net/techtips/bind9-chroot.html") on how to set it up as a chroot, so maybe that'll give you a place to start.

---

### Post by stmiller on 2010-12-30
```
root@crm:~# ls -l /etc/named.conf
lrwxrwxrwx 1 root root 34 2010-12-24 02:11 /etc/named.conf -> /var/named/run-root/etc/named.conf
```

Yup - this means it is running in a chroot which is good.

Try this:

```

chown root:named /etc/named.conf

```

---

### Post by fast_eddie on 2010-12-30
ok not sure what I'm doing as I would have thought that a caching server wouldn't have required so much effort
- will make the changes suggested in the thread you sent over and see if that fixes it

---

### Post by fast_eddie on 2010-12-30
Hi 

> root@crm:~# chown root:named /etc/named.conf
chown: invalid group: `root:named'


Does that mean anything to you?

---

### Post by fast_eddie on 2010-12-30
Hi

Attached is the screen shot from webmin for BIND.  Shouldn't there be a path for chroot?

Ed

---

### Post by elico on 2010-12-30
hey there..
you have an option in webmin: "check bind config"
that should test your config.

the permission thing leave it for now.
make sure that the basic thing is working and if not webmin wil show you something.

---

### Post by fast_eddie on 2010-12-30
Hi

I have already used that and it isn't reporting any problems ?!

> No errors were found in the BIND configuration file /etc/bind/named.conf or referenced zone files.

But that's why I thought that there must've been inconsistency from looking at the screen dumps I posted. Since webmin wasn't showing up any issues, but there obviously are.

---

### Post by Vegan on 2010-12-30
post all of you config files so I can check the setup, looks like a config problem.

It also looks like you have made several changes from the usual setup.

---

### Post by fast_eddie on 2010-12-30
Charles - 

Well that old thread actually resolved the issue and it is now working!

Very many thanks!

**So for anyone else with a similar problem...** I ended up merging in some instances the additional entries from the thread on 'howtoforge' [ [http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893) ]
I'm running Ubuntu 10.04.1 LTS and so I amended rsyslog instead of syslogd as refered to in the link.

---

### Post by CharlesA on 2010-12-31
Wow, who woulda thunk. Glad you got it sorted out, and please mark the thread as solved from thread tools at the top. ^

:)

---

