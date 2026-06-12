---
title: "Remote admin of Windows server on Ubuntu"
date: 2009-12-30
forum: Server Platforms
---

### Post by satimis on 2009-12-30
Hi folks,

Ubuntu 9.10
Windows Server 7
Windows Vista

I need setup remote admin of Windows Server 7 and Windows Vista on Ubuntu.  Would VNC is the right road to go?  If YES, will following URL be the right guide/tutorial for me to follow?

Remote Desktop Sharing in Ubuntu
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

VNC How-to
[https://intranet.cs.hku.hk/csintranet/contents/technical/howto/vnc.jsp](https://intranet.cs.hku.hk/csintranet/contents/technical/howto/vnc.jsp)

VNC installation, configuration and use with Linux and Microsoft Windows
[http://www.yolinux.com/TUTORIALS/VNC.html](http://www.yolinux.com/TUTORIALS/VNC.html)

TIA

B.R.
satimis

---

### Post by windependence on 2009-12-30
If all you want to do is access the GUI on the windows machines, VNC is OK for LAN access, but for WAN access I would use simple RDP. It's built in to windows and much more secure than VNC. 

If you want automatic monitoring of server functions, something like Zabbix or Nagios would be better.

-Tim

---

### Post by satimis on 2009-12-30
> **windependence said:**
> If all you want to do is access the GUI on the windows machines, VNC is OK for LAN access, but for WAN access I would use simple RDP. It's built in to windows and much more secure than VNC. 

Hi Tim,

Thanks for your advice.  Whether you mean installing tsclient on Ubuntu?


How To Connect To A Windows Terminal Server From Ubuntu - tsclient
[http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html](http://www.watchingthenet.com/how-to-connect-to-a-windows-terminal-server-from-ubuntu.html)

HOWTO Use Remote Desktop from Linux   - tsclient
[http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux](http://wiki.bath.ac.uk/display/Linux/HOWTO+Use+Remote+Desktop+from+Linux)


What will be the setup on Windows server 7 and Vista?


> 
If you want automatic monitoring of server functions, something like Zabbix or Nagios would be better.


I suppose you meant;

Zabbix
------

Installing Zabbix (Server And Agent) On Debian Etch
[http://www.howtoforge.com/zabbix_network_monitoring_debian_etch](http://www.howtoforge.com/zabbix_network_monitoring_debian_etch)


What is Zabbix
[http://www.debianhelp.co.uk/zabbix.htm](http://www.debianhelp.co.uk/zabbix.htm)


Nagios
------
[http://www.nagios.org/](http://www.nagios.org/)


Nagios Documentation
[http://www.nagios.org/documentation](http://www.nagios.org/documentation)


Which of them will be better and easy to setup?


TIA


B.R.
satimis

---

