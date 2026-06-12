---
title: "Dell Openmanage with Nagios"
date: 2010-11-22
forum: Server Platforms
---

### Post by nosebreaker on 2010-11-22
So I am trying to monitor OpenManage (hardware monitoring) on Ubuntu 10.04 Server with Nagios, and I can't get it to work due to smux.

I got Dell OpenManage 6.3 installed by following this:
[http://linux.dell.com/repo/community/deb/](http://linux.dell.com/repo/community/deb/)

And it appears to work fine (I installed snmp first).  I can login to the web interface and see the hardware without issue.

To get Nagios to monitor OpenManage, there is a nice little plugin for it called check_openmanage:
[http://folk.uio.no/trondham/software/check_openmanage.html](http://folk.uio.no/trondham/software/check_openmanage.html)

I install that fine as well, it did something funky by installing to /usr/lib64 instead of /usr/lib, so I just moved the files.

But then when I try to monitor it, the plugin just returns:
ERROR: (SNMP) OpenManage is not installed or is not working correctly 

Which seems to indicate it can't find the snmp item at:
1.3.6.1.4.1.674.10892.1.300.10.1.9.1

So I try to snmpwalk to that MIB, and there is nothing there!  I can snmpwalk other items without issue.

So then I check /var/log/syslog, and I see:
snmpd[2617]: /etc/snmp/snmpd.conf: line 20: Warning: Unknown token: smuxpeer.

I just installed net-snmp with apt-get, I didn't do anything to exclude smux from it, so how do I get it to load?

---

### Post by nosebreaker on 2010-11-22
I found it!  Another mailing list:
You have to remove '-I -smux' from /etc/default/snmpd and restart your snmpd service.

Now it works!

---

