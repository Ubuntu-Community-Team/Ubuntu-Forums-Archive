---
title: "DHCP [fail]"
date: 2005-12-23
forum: Server Platforms
---

### Post by JeffLeBoeuf on 2005-12-23
I just attempted to follow the instructions to set up a 5.10 server machine to serve as an ltsp (thin client server) but here's where I am stuck:

```

root@ubuntu-ltsp:~# invoke-rc.d dhcp3-server restart
 * Stopping DHCP server...                                               [fail]
 * Starting DHCP server...                                               [fail]
root@ubuntu-ltsp:~#

```

Not real hardcore at linux just yet, any ideas where I should begin?

---

### Post by afhp on 2005-12-23
Check /var/log/messages, /var/log/syslog etc and see if it says anything about why it fails (or whether it even actually tries to start). 

Try starting it manually (/etc/init.d/dhcpd or something similar) and see what it says. Look inside the script for the actual commands.

Chances are, if it doesn't start, there's a configuration snafu somewhere.

---

### Post by JeffLeBoeuf on 2005-12-27
Both of those log files didn't return any information at all on a failing dhcp service. :\

---

### Post by fordfan753 on 2005-12-27
Is there anything wrong with your dhcp config file?

---

### Post by JeffLeBoeuf on 2005-12-27
Could be, any idea what I should be checking for?  I personally have not altered it in any way.

This is a fresh Ubuntu install and I went straight through the ltsp guide.

I'm certainly willing to take a peek though. :)

---

### Post by fordfan753 on 2005-12-27
Post it here, I'll see if I can find anything wrong (probably not right now, I need sleep before I can tackle config files), you will have to customise it to suit your network.

---

