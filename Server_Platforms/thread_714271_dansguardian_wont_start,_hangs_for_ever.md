---
title: "dansguardian wont start, hangs for ever"
date: 2008-03-03
forum: Server Platforms
---

### Post by twistedtwig on 2008-03-03
Hi all,

I have recently installed squid and have this running as a transparent proxy which all works great!!!

I have been following this guide:

[http://ubuntuforums.org/showthread.php?t=320733](http://ubuntuforums.org/showthread.php?t=320733)

```
filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
```

The above were all just like that.

I commented the UNCONFIGURED

The tried to stop and start everything.

squid is find.

Dansguardian will stop but when you try and start it, it will hang for ever.

I can not see anything in the logs to explain it.

I tried googling it but didn't find any logical answers.

I am hoping someone might have some suggestions please?

Thanks

---

### Post by bmathis on 2008-03-04
Hey thats my howto!!!

Is there anything in the syslog relating to the hang? Also, can you paste the output of the restart command that you are using.

---

### Post by twistedtwig on 2008-03-04
Hi Bmathis,

Firstly I would like to say thank you for your howto.  Was very good and helped me though it all.

here is the stop start output:

```
root@betty:/var/log# /etc/init.d/dansguardian stop
 * Stopping DansGuardian dansguardian                                                                                                                 [ OK ] 
root@betty:/var/log# /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                                                                                                        
root@betty:/var/log# 

```

There is nothing in the syslog for it at all.  The last thing in there is my dhcpak from when I logged the computer onto the network. (time it was run at 06:44)

```
root@betty:/var/log# tail -n 50 syslog
Mar  4 06:25:48 betty syslogd 1.4.1#20ubuntu4: restart.
Mar  4 06:26:20 betty dhcpd: DHCPREQUEST for 192.168.10.187 from 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:26:20 betty dhcpd: DHCPACK on 192.168.10.187 to 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:31:21 betty dhcpd: DHCPREQUEST for 192.168.10.187 from 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:31:21 betty dhcpd: DHCPACK on 192.168.10.187 to 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:31:41 betty dhcpd: DHCPDISCOVER from 00:09:5b:06:0f:30 via eth1
Mar  4 06:31:42 betty dhcpd: DHCPOFFER on 192.168.10.186 to 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:31:42 betty named[4023]: client 192.168.10.1#34153: updating zone 'ponywars.local/IN': adding an RR at 'UbuntuWiggly.ponywars.local' A
Mar  4 06:31:42 betty named[4023]: client 192.168.10.1#34153: updating zone 'ponywars.local/IN': adding an RR at 'UbuntuWiggly.ponywars.local' TXT
Mar  4 06:31:42 betty dhcpd: Added new forward map from UbuntuWiggly.ponywars.local to 192.168.10.186
Mar  4 06:31:42 betty named[4023]: client 192.168.10.1#34153: updating zone '10.168.192.in-addr.arpa/IN': deleting rrset at '186.10.168.192.in-addr.arpa' PTR
Mar  4 06:31:42 betty named[4023]: client 192.168.10.1#34153: updating zone '10.168.192.in-addr.arpa/IN': adding an RR at '186.10.168.192.in-addr.arpa' PTR
Mar  4 06:31:42 betty dhcpd: added reverse map from 186.10.168.192.in-addr.arpa. to UbuntuWiggly.ponywars.local
Mar  4 06:31:42 betty dhcpd: DHCPREQUEST for 192.168.10.186 (192.168.10.1) from 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:31:42 betty dhcpd: DHCPACK on 192.168.10.186 to 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:36:11 betty dhcpd: DHCPREQUEST for 192.168.10.186 from 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:36:11 betty dhcpd: DHCPACK on 192.168.10.186 to 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:36:22 betty dhcpd: DHCPREQUEST for 192.168.10.187 from 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:36:22 betty dhcpd: DHCPACK on 192.168.10.187 to 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:39:01 betty /USR/SBIN/CRON[17138]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Mar  4 06:40:14 betty dhcpd: DHCPREQUEST for 192.168.10.186 from 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:40:14 betty dhcpd: DHCPACK on 192.168.10.186 to 00:09:5b:06:0f:30 (UbuntuWiggly) via eth1
Mar  4 06:41:23 betty dhcpd: DHCPREQUEST for 192.168.10.187 from 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1
Mar  4 06:41:23 betty dhcpd: DHCPACK on 192.168.10.187 to 00:d0:e0:90:89:6a (awmgnlbjakq0) via eth1

```

Thanks for the assistance :)

---

### Post by bmathis on 2008-03-04
are you using a third party blacklist? Using one can make dansgaurdian start a little slow because it has to sort and load all the information.

Also, there was a [bug filled for debian]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=432251") that stated clamav was loading slow which was causing the slow load of dansguardian. There was no fix, but a user stated that purging dansguardian and clamav, then reinstalling fixed his issue.

---

### Post by twistedtwig on 2008-03-04
I am using all the defaults.  I have not changed anything apart from editing the config as stated above.

I will try purging it all and reinstalling tomorrow and see if it helps.

Thank you for your advice.. 

Will let you know how I get on.

---

### Post by twistedtwig on 2008-03-05
I purged it and reinstalled.  It no longer hangs but the ps -e | grep dansguardian command does not return any processes.

I have checked in syslog, daemon.log, messages and dansguardian/access.log and there are no entries for it starting at all

---

