---
title: "dns permission problem?"
date: 2015-08-06
forum: Server Platforms
---

### Post by steve214 on 2015-08-06
I just upgraded a dns server to LTS 14.04 I'm seeing syslog entries that look like I have a permissions problem.

Aug  6 14:24:11 NS2 named[1620]: dumping master file: tmp-o7qeIebdR5: open: permission denied
Aug  6 14:24:11 NS2 kernel: [ 6886.346223] type=1400 audit(1438896251.308:443): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/tmp-o7qeIebdR5" pid=1622 comm="named" requested_mask="c" denied_mask="c" fsuid=104 ouid=104


Is this something to be concerned with? 

thanks!

---

### Post by howefield on 2015-08-06
Moved to "*Server Platforms*" forum.

---

### Post by papibe on 2015-08-06
Hi steve214.

Could you post the output of these commands?
```
ls -la /etc/bind

grep -i directory /etc/bind/named.conf.options
```
Regards.

---

### Post by matt_symes on 2015-08-06
Hi

I came across this when using isc bind under 14.04 and it turned out to be apparmor.

You could disable the apparmor bind profile if this is not a production NS server for a quick test.

Remember to teardown as well as restarting apparmor daemon so it does not use cached profiles.

BTW: is the bind apparmor profile set to enforce, complain or disabled on your server ?

Kind regards

---

### Post by steve214 on 2015-08-07
it shows: (file names changed to protect the innocent)
```
-rw-r--r--  1 root bind      3332 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       366 Aug  7 08:59 xxx.xxx.xxx.in-addr-arpa
-rw-r--r--  1 root bind       661 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind      1126 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind       921 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind      1334 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind      1463 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind      1498 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 root bind      1072 Feb 28  2014 xxx.xxx.xxx0.in-addr.arpa
-rw-r--r--  1 root bind      1089 Feb 28  2014 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       725 Aug  7 07:42 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind      2505 Aug  7 09:20 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       369 Aug  7 08:54 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       345 Aug  7 09:36 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       369 Aug  7 09:08 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       370 Aug  7 09:06 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       439 Aug  7 08:57 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       400 Aug  7 10:23 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       370 Aug  7 08:05 xxx.xxx.xxx.in-addr.arpa
-rw-r--r--  1 bind bind       370 Aug  7 10:22 xxx.xxx.xxx.in-addr.arpa
-rw-rw-r--  1 root root      2389 Jul 27 09:53 bind.keys
-rw-------  1 bind bind 291676160 Aug  4 17:03 core
-rw-r--r--  1 bind bind       673 Aug  7 09:28 ctpl.org
-rw-rw-r--  1 root root       237 Feb 21  2014 db.0
-rw-r--r--  1 root bind      3332 Feb 27  2014 db.xxx.xxx.xxx
-rw-r--r--  1 root bind       661 Feb 26  2014 db.xxx.xxx.xxx
-rw-r--r--  1 root bind      1126 Feb 26  2014 db.10.3.102
-rw-r--r--  1 root bind       921 Feb 26  2014 db.10.3.103
-rw-r--r--  1 root bind      1334 Feb 26  2014 db.10.3.104
-rw-r--r--  1 root bind      1463 Feb 26  2014 db.10.3.105
-rw-r--r--  1 root bind      1498 Feb 26  2014 db.10.3.106
-rw-r--r--  1 root bind      1072 Feb 26  2014 db.10.3.107
-rw-r--r--  1 root bind      1089 Feb 26  2014 db.10.3.108
-rw-rw-r--  1 root root       271 Feb 21  2014 db.127
-rw-rw-r--  1 root bind       271 Feb 21  2014 db.127.0.0
-rw-rw-r--  1 root bind       469 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       470 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       761 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind      2668 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       397 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       399 Feb 21  2014 db.xxx.xxx.xxx.save
-rw-rw-r--  1 root bind       366 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       366 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       365 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       403 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       398 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       365 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       365 Feb 21  2014 db.xxx.xxx.xxx
-rw-rw-r--  1 root bind       160 Feb 21  2014 db.xxx.xxx.xxx.in-addr.arpa
-rw-rw-r--  1 root root       237 Feb 21  2014 db.255
-rw-rw-r--  1 root bind      2769 Feb 21  2014 db.cache
-rw-rw-r--  1 root bind       628 Feb 21  2014 db.cache.old
-rw-rw-r--  1 root bind       832 Feb 21  2014 db.ctpl.org
-rw-rw-r--  1 root root       353 Feb 21  2014 db.empty
-rw-rw-r--  1 root root       256 Feb 21  2014 db.local
-rw-rw-r--  1 root bind       785 Feb 21  2014 db.redkelly.info
-rw-rw-r--  1 root bind       801 Feb 21  2014 db.redkelly.net
-rw-rw-r--  1 root bind       779 Feb 21  2014 db.redkelly.org
-rw-rw-r--  1 root bind       815 Feb 21  2014 db.rockthebooks.info
-rw-rw-r--  1 root bind       810 Feb 21  2014 db.rockthebooks.org
-rw-rw-r--  1 root root      1506 Feb 21  2014 db.root
-rw-rw-r--  1 root root      3048 Jul 27 09:53 db.root.dpkg-dist
-rw-rw-r--  1 root bind       835 Feb 21  2014 db.storylabtacoma.com
-rw-rw-r--  1 root bind       833 Feb 21  2014 db.storylabtacoma.org
-rw-rw-r--  1 root bind       890 Feb 21  2014 db.tacomahistory.com
-rw-rw-r--  1 root bind       916 Feb 21  2014 db.tacomahistory.net
-rw-rw-r--  1 root bind       833 Feb 21  2014 db.tacomalibraries.org
-rw-rw-r--  1 root bind       936 Feb 21  2014 db.tacomalibrary.org
-rw-rw-r--  1 root bind       969 Feb 21  2014 db.tacomapubliclibrary.com
-rw-rw-r--  1 root bind       986 Feb 21  2014 db.tacomapubliclibrary.net
-rw-rw-r--  1 root bind      2209 Feb 21  2014 db.tacomapubliclibrary.org
-rw-rw-r--  1 root bind       729 Feb 21  2014 db.talktacoma.com
-rw-rw-r--  1 root bind       717 Feb 21  2014 db.talktacoma.org
-rw-rw-r--  1 root bind      2628 Feb 21  2014 db.tpl
-rw-rw-r--  1 root bind       804 Feb 21  2014 db.tplfoundation.com
-rw-rw-r--  1 root bind       804 Feb 21  2014 db.tplfoundation.net
-rw-rw-r--  1 root bind       781 Feb 21  2014 db.tplfoundation.org
-rw-rw-r--  1 root bind       782 Feb 21  2014 db.tplfriends.com
-rw-rw-r--  1 root bind       759 Feb 21  2014 db.tplfriends.net
-rw-rw-r--  1 root bind       759 Feb 21  2014 db.tplfriends.org
-rw-rw-r--  1 root bind       756 Feb 21  2014 db.tplib.org
-rw-rw-r--  1 root bind      2265 Feb 21  2014 db.tplint.org
-rw-rw-r--  1 root bind      2318 Feb 21  2014 db.tplonline.org
-rw-rw-r--  1 root bind      1073 Feb 21  2014 db.tplrus.org
-rw-rw-r--  1 root bind       948 Feb 21  2014 db.webebooks.org
-rw-rw-r--  1 root bind      5832 Apr  8  2014 named.conf
-rw-rw-r--  1 root bind       490 Jan 10  2014 named.conf.default-zones
-rw-rw-r--  1 root bind       165 Jan 10  2014 named.conf.local
-rw-rw-r--  1 root bind       891 Feb 28  2014 named.conf.options
-rw-r--r--  1 bind bind     14241 Mar  4  2014 named.stats
-rw-r--r--  1 root bind      5317 Feb 26  2014 old-named.conf
-rw-r--r--  1 bind bind       648 Aug  7 08:37 redkelly.info
-rw-r--r--  1 bind bind       642 Aug  7 09:35 redkelly.net
-rw-r--r--  1 bind bind       693 Aug  6 23:39 redkelly.org
-rw-rw-r--  1 bind bind        77 Feb 21  2014 rndc.key
-rw-r--r--  1 bind bind       667 Aug  7 00:25 rockthebooks.info
-rw-r--r--  1 bind bind       666 Aug  7 08:30 rockthebooks.org
-rw-r--r--  1 bind bind       741 Aug  7 00:26 tacomahistory.com
-rw-r--r--  1 bind bind       795 Aug  7 08:55 tacomahistory.net
-rw-r--r--  1 bind bind       790 Aug  7 07:33 tacomalibraries.org
-rw-r--r--  1 bind bind      1410 Aug  7 08:57 tacomalibrary.org
-rw-r--r--  1 bind bind       794 Aug  6 23:14 tacomapubliclibrary.com
-rw-r--r--  1 bind bind       809 Aug  7 09:25 tacomapubliclibrary.net
-rw-r--r--  1 bind bind      1930 Aug  7 09:29 tacomapubliclibrary.org
-rw-r--r--  1 bind bind       657 Aug  6 12:55 talktacoma.com
-rw-r--r--  1 bind bind       647 Aug  6 12:55 talktacoma.org
-rw-r--r--  1 bind bind      2174 Aug  7 09:06 tpl.lib.wa.us
-rw-r--r--  1 bind bind      2206 Aug  7 09:34 tplonline.org
-rw-r--r--  1 bind bind       906 Aug  6 12:55 tplrus.org
-rw-r--r--  1 bind bind       796 Aug  6 12:55 webebooks.org
-rw-rw-r--  1 root root      1310 Feb 28  2014 zones.rfc1918
root@NS2:/home/slh# grep -i directory /etc/bind/named.conf
        # The directory statement defines the name server's working directory
        directory "/etc/bind";
```

thanks!

---

### Post by steve214 on 2015-08-07
Unfortunately, it is a production server. Background info... Someone amused themselves with the DOS exploit for bind 9.8.1 . Apt-get updates (running on 12.04) didn't update bind. So I updated to 14.04 and got 9.9.5. 

I'll poke around apparmor and see if I can figure something out. Thanks for the lead!

> **matt_symes said:**
> Hi

I came across this when using isc bind under 14.04 and it turned out to be apparmor.

You could disable the apparmor bind profile if this is not a production NS server for a quick test.

Remember to teardown as well as restarting apparmor daemon so it does not use cached profiles.

BTW: is the bind apparmor profile set to enforce, complain or disabled on your server ?

Kind regards

---

### Post by papibe on 2015-08-07
Thanks.

You changed the default working and temp directory from '/var/cache/bind' to '/etc/bind'. This may require extra work because (quote from [here]("https://help.ubuntu.com/community/BIND9ServerHowto#Secondary_Master_Server_configuration")):
> The zone file must be in /var/cache/bind/ because, by default, AppArmor only allows write access inside it (this was made specifically for a slave configuration. See AppArmor's configuration in /etc/apparmor.d/usr.sbin.named).

First check that user 'bind' has writing permissions to the directory, and then update your bind's apparmor profile (examples [here]("https://wiki.ubuntu.com/AppArmor") and [here]("http://askubuntu.com/questions/172030/how-to-allow-bind-in-app-armor"))

Alternatively, you could go back to use the default directory and keep the current apparmor's named profile.

Hope it helps. Let us know how it goes.
Regards.

BTW: the 'ls' command was intended to see the permissions of the directory, not the files:
```
$ ls -ld /etc/bind
drwxr-sr-x 2 root bind 4096 Jul 28 15:30 /etc/bind

```

---

### Post by matt_symes on 2015-08-07
Hi

That sounds about right papibe, although I have to say that I cannot remember explicit changing the bind working directory from 12 to 14 lts installs but I did use the same conf files so it must have been a change in the apparmor profile from 12 to 14.

My solution at the time was to edit the apparmor profile. I'll look into reverting those changes on my NS.

Anyway, I hope that helps the OP and I hope you're well papibe :-)

Kind regards

---

