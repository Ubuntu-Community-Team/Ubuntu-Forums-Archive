---
title: "Squid3 + webmin guide?"
date: 2012-03-26
forum: Server Platforms
---

### Post by Sternfan on 2012-03-26
Hi all,

I have set up numerous squid boxes before (that actually worked) but for whatever reason it is just not working this time.  **What I am looking for is a guide for SQUID3 using webmin.**  I used the guide from the webmin page but it is so old that the screenshots are from squid 2.4...  I have the webmin book - but it is from 2003...

What is driving me nuts is that I have two functional squid3 servers running - I copy the very same settings to the new server and squid simply won't start.

Any help greatly appreciated.

Rob

---

### Post by Sternfan on 2012-03-26
Hi all,

I am starting over from scratch using 11.10.  After doing the basic install & updates - when I get to initializing the cache - what user should I use?

Under "administrative options" - what user & group should I use?

Thanks,
Rob

---

### Post by AnvarIT on 2012-04-20
> **Sternfan said:**
> Hi all,

I have set up numerous squid boxes before (that actually worked) but for whatever reason it is just not working this time.  **What I am looking for is a guide for SQUID3 using webmin.**  I used the guide from the webmin page but it is so old that the screenshots are from squid 2.4...  I have the webmin book - but it is from 2003...

What is driving me nuts is that I have two functional squid3 servers running - I copy the very same settings to the new server and squid simply won't start.

Any help greatly appreciated.

Rob
Couldn't get webmin to work either with Squid3, so I reverted back the 2.7Stable who has no problem at all with webmin

---

### Post by SeijiSensei on 2012-04-20
I'm running Squid 3.1.10 and Webmin 1.570 on a CentOS 6 system.  It works very well.  I'm pretty sure Webmin is better tuned for RedHat-flavored systems than Debian ones.

---

### Post by jaimerosario on 2012-04-20
Install all Squid3 packages:

```

sudo apt-get install squid3^

```

Next, edit /etc/webmin/squid/config and match the following settings:

```

squidclient=squidclient
cache_dir=/var/spool/squid3
log_dir=/var/log/squid3
pid_file=/var/run/squid3.pid
squid_path=squid3
squid_conf=/etc/squid3/squid.conf
cachemgr_path=/usr/lib/cgi-bin/cachemgr3.cgi
squid_restart=squid3 -k reconfigure
squid_start=service squid3 start
squid_stop=service squid3 stop
```

Then check the Webmin module by refreshing all modules in the Webmin Configuration menu.

---

### Post by fulllefty on 2012-05-03
Thank you jaimerosario :)

This is what I'm looking for, [COLOR="Lime"]get squid3.1 detected on webmin ( mine 1.5.8 )[/COLOR]

I've changed my /etc/webmin/squid/config from

this

```
sort_conf=0
squidclient=squidclient
cache_dir=/var/spool/squid
sync_create=0
log_dir=/var/log/squid
pid_file=/var/run/squid.pid
cal_max=50000
sync_modify=1
cal_fmt=w
cal_all=1
squid_path=squid
calamaris=calamaris
squid_conf=/etc/squid/squid.conf
sync_delete=0
cal_args=-aw
cachemgr_path=/usr/lib/cgi-bin/cachemgr.cgi
crypt_conf=0
restart_pos=0
```

to this

```
sort_conf=0
squidclient=squidclient
cache_dir=/var/spool/**[COLOR="Lime"]squid3[/COLOR]**
sync_create=0
log_dir=/var/log/**[COLOR="Lime"]squid3[/COLOR]**
pid_file=/var/run/**[COLOR="Lime"]squid3[/COLOR]**.pid
cal_max=50000
sync_modify=1
cal_fmt=w
cal_all=1
squid_path=**[COLOR="Lime"]squid3[/COLOR]**
calamaris=calamaris
squid_conf=/etc/**[COLOR="Lime"]squid3[/COLOR]**/squid.conf
sync_delete=0
cal_args=-aw
cachemgr_path=/usr/lib/cgi-bin/cachemgr.cgi
crypt_conf=0
restart_pos=0
[B][COLOR="Lime"]squid_restart=squid3 -k reconfigure
squid_start=service squid3 start
squid_stop=service squid3 stop[/COLOR][/B]

```

then refreshing the module from webmin config menu
voila, Squid Proxy Server listed on Webmin Servers dropdown list

I confirmed this way works.

---

