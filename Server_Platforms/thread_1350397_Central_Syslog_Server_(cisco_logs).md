---
title: "Central Syslog Server (cisco logs)"
date: 2009-12-09
forum: Server Platforms
---

### Post by -lodogg- on 2009-12-09
I’m trying to setup a simple remote syslog server but seem to be running into some issues.  I searched the /etc/ directory for a syslog.conf file with no luck.  Can anyone point me to a link or a forum post showing how you can create a remote syslog server?  I need to point a firewall and two routers to a central syslog server in order to capture events.

I followed this article but I could not find the syslog service there is only an rsyslog service.
[http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml](http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml)

------
# ps -Af | grep "syslog"
root      1557     1  0 09:15 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog    1559     1  0 09:15 ?        00:00:00 rsyslogd -c4
------
Linux ubuntu-server 2.6.31-16-generic-pae #52-Ubuntu SMP
------
-lo

---

### Post by de0xyrib0se on 2009-12-09
[http://ubuntuforums.org/showthread.php?t=1349753]("http://ubuntuforums.org/showthread.php?t=1349753")

---

### Post by -lodogg- on 2009-12-09
ahh great!  Can you post how to write it to a separate log file?  /var/log/cisco-logs?

Are there any add on applications that I can use to send alerts out from the system?  So if a certain event hits the log file an e-mail is triggered.

-lo

---

### Post by Lars Noodén on 2009-12-09
You'll be sure to want /var/log in a separate partition of its own.  With log servers, there is a risk of DOS by filling up the partition if it is on the same partition as /tmp.

As for how the service reports to the log server, that is a matter of setting the program being logged to report as a specific Syslog Facility and Log Level:

The possible values for Syslog Facility are DAEMON, USER, AUTH, LOCAL0, LOCAL1, LOCAL2, LOCAL3, LOCAL4, LOCAL5, LOCAL6, and LOCAL7.  It is possible to have more than one.  So you can leave the default logging and then add LOCAL1 for that service.  

Possible values for LogLevel can vary but are usually at least QUIET, FATAL, ERROR, INFO, VERBOSE, and DEBUG.

I'm looking now at the 'documentation' for rsyslog.conf and the manual page is far from useful or clear. :(  But that's what you'll have to change to forward from the machine with the service you wish to log to the log server.  The manual page mostly just points to the web site, but that's not much clearer to me either, but maybe it's a start in the right direction.  
[http://www.rsyslog.com/doc](http://www.rsyslog.com/doc)

---

### Post by -lodogg- on 2009-12-09
I'm having issues with logs showing up on the Ubuntu server.  Are there any ways to troubleshoot my rsyslog setup?

-----------
Here are the entries I added to the rsyslog.conf file:

$InputTCPServerRun 514
$AllowedSender TCP, 127.0.0.1, 192.168.1.0/24

$UDPServerRun 514
$AllowedSender UDP, 127.0.0.1, 192.168.1.0/24
-----------

The firewall is sourcing from a 192.168.1.0/24 network and I have my logging set to debug with the Ubuntu server as my destination log repository.  I ran through a packet trace on the firewall and UDP/514 is making it to the Ubuntu server.  I ran the following commands trying to see if the logs were going anywhere.

cat /var/log/* | grep "deny"
cat /var/log/* | grep "IKE"
sudo /etc/init.d/rsyslog restart
sudo /etc/init.d/networking restart

All basic network connectivity seems to be up:\  IPTables is not enabled at this time.

-lo

---

### Post by -lodogg- on 2009-12-09
I was missing two lines in my config:\  But it looks like the data is dropping into the /var/log/messages log.  It would be nice to drop it in my own log directory /var/log/cisco..?


rsyslog lines that actually work

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

# provides TCP syslog reception
$ModLoad imtcp
$InputTCPServerRun 514

-lo

---

### Post by -lodogg- on 2009-12-09
It's still dumping the syslog data into my /var/log/messages file.  I tried the following in my rsyslog.conf file:

%PIX.* /var/log/cisco.log

and

local7.* /var/log/cisco.log

--------------

Here is a snippet of what I'm seeing from my PIX:

Dec  9 19:31:35 192.168.1.1 %PIX-6-302020: Built outbound ICMP connection for faddr 192.168.1.40/0 gaddr 10.22.1.101/1 laddr 10.22.1.101/1
Dec  9 19:31:40 192.168.1.1 %PIX-6-302020: Built outbound ICMP connection for faddr 192.168.1.20/0 gaddr 10.22.1.102/1 laddr 10.22.1.102/1
Dec  9 19:31:41 192.168.1.1 %PIX-4-713903: IP = 192.168.30.62, Error: Unable to remove PeerTblEntry

---

### Post by -lodogg- on 2009-12-10
I had to finish this thread:-)

---------------------
I needed the following in the rsyslog.conf:
local*.* /var/log/cisco.log

#local4.* /var/log/cisco.log
#local7.debug /var/log/cisco.log
#local7.warn /var/log/cisco.log
---------------------

That's right I'm sending all logs to one location for now.

---------------------
I also needed the following on my pix config:
logging facility 20 (local4)
logging trap critical
----------------------

The following was a real help.  
[http://www.cisco.com/en/US/products/hw/vpndevc/ps2030/products_tech_note09186a0080094030.shtml](http://www.cisco.com/en/US/products/hw/vpndevc/ps2030/products_tech_note09186a0080094030.shtml)

It's hard understanding how to trigger the syslog filter and write it to a separate log file.

-lo

---

### Post by Lars Noodén on 2009-12-11
> **-lodogg- said:**
> 
---------------------
I also needed the following on my pix config:
logging facility 20 (local4)
logging trap critical
----------------------


Collecting system logs always has two parts, the configuration of the application making the log messages, the remote or local syslog daemon.

---

