---
title: "odd SNMPD Problem"
date: 2007-06-06
forum: Server Platforms
---

### Post by neemers on 2007-06-06
Hi all!

I have just installed Ubuntu Feisty on a computer here and am setting it up as a zimbra mailserver.  I went to install snmp on the machine to monitor is performance with Zenoss.  I have about 3 other ubuntu server running 6.0 versions that Zenoss is currently monitoring.  So on this new feisty install I did the same things I normally do to install snmp.  I pretty much did....

apt-get install snmpd
cp /etc/snmp/snmpd.conf  /etc/snmp//snmpd.conf.bak
snmpconf    (configure snmpd agent to allow public read)
cp snmpd.conf  /etc/snmp/
/etc/init.d/snmpd restart
   (if snmpconf fails to start since its not installed, try this first:)
apt-get install libsnmp-base libsnmp-perl libsnmp9 libsnmp9-dev snmp tkmib 

I've followed these steps pretty much to the dot for all my other ubuntu servers.

Now when I try to add the Feisty server device to Zenoss it tells me that snmp can not be found on the device.  I can see the snmpd process running and I have restarted it multiple times.  

Is there currently issues with snmpd and Feisty?  Am I missing a step that is needed for Feisty?

Thank you for your help!

---

### Post by neemers on 2007-06-13
I setup another Ubuntu Feisty Server and am having the same problem with snmp not working.  Any ideas?

Thank you!

---

### Post by neemers on 2007-06-13
I figured it out......thanks to this site.....

[http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti](http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti)

I edited /etc/default/snmpd and took out 127.0.0.1 ....

SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

What that does is it sets up snmp over any network device.

Then I setup com2sec correctly in /etc/snmp/snmpd.conf

All is good now.

thank you all.

---

