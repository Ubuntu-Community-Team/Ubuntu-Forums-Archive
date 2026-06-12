---
title: "ProFTPd problems"
date: 2009-06-21
forum: Server Platforms
---

### Post by Radio91 on 2009-06-21
I managed to get the Dns and nameservers set up OK but I have one final issue that I cant see to resolve.

In virtualmin system information ProFTPd FTP Server is not running, when I try to enable it I get the following error:

Failed to start service :

* Starting ftp server proftpd
* warning: unable to determine IP address of 'ns1.mydomain.com_'
* error: no valid servers configured
* Fatal: error processing configuration file '/etc/proftpd/proftpd.conf' ...fail!

I tired to edit the /etc/proftpd/proftpd.conf and remove the _ from the end of ns1.mydomain.com but its not in that file.

There is no typos in /etc/hosts and /etc/hostname

/etc/hosts:

127.0.0.1 localhost.localdomain localhost
94.xx.xxx.xxx ns1.mydomain.com ns1
94.xx.xxx.xxx ns2.mydomain.com ns2

hostname is returing ns1.mydomain.com which is correct but

hostname -f is returning:

hostname: Unknown host

Which makes no sense!

Any idea whats going on here?
Radio91 is online now Report Post   	Edit/Delete Message

---

### Post by Radio91 on 2009-06-24
anybody got any idea about this? or even where ns1.mydomain.com_ might be stored?

---

