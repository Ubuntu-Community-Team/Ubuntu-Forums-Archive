---
title: "Recommendations: Network Monitor tool"
date: 2008-06-05
forum: Server Platforms
---

### Post by cocotu on 2008-06-05
We have a mix of Macs, WinXP machines at our LAN. I have being checking these out:

[http://www.nagios.org/about/screenshots.php](http://www.nagios.org/about/screenshots.php)
[http://hobbitmon.sourceforge.net/docs/install.html](http://hobbitmon.sourceforge.net/docs/install.html)
[http://www.zenoss.com/product/screenshots](http://www.zenoss.com/product/screenshots)

Does anyone have experience with these? or can you recommend anything else that is easy to install/configure and will monitor Macs & PCs.  We are running Ubuntu Server on VMware.

Thanks

---

### Post by windependence on 2008-06-05
[http://sectools.org/](http://sectools.org/)


Insecure.org is a great site. There are probably other articles out there on this.

Also don't forget plain old ntop for monitoring quick and dirty.

-Tim

---

### Post by gtdaqua on 2008-06-06
Zenoss. Its an Enterprise Grade Network Monitoring System and have got a pretty active community supporting it.

---

### Post by Titan8990 on 2008-06-06
I tried a few network monitors and the best I found was wireshark. You can get it via apt-get and it also has a MAC OS version.

#apt-get install wireshark

---

### Post by Monicker on 2008-06-06
I've used nagios in the past.  Decent tool, but I hate configuring it.

You might also want to look at Zabbix.  I found it easier than Nagios.  

[http://www.zabbix.com/](http://www.zabbix.com/)

I don't have experience with the other options you mentioned.

---

### Post by cocotu on 2008-06-06
I'm a newbie at this network monitoring stuff.  I'm looking for the simplest way of doing this & would like to see the reports at the browser rather than installing something such as wireshark.  I tried wireshark a while ago(windows version) and didn't like it. thanks..

---

### Post by gtdaqua on 2008-06-07
wireshark is used to sniff the traffic - not monitor an entire network. Try Zenoss. It uses AJAX on its nice web interface and its quite easy to set up. There are several guides to set up. One is on their website itself.

---

