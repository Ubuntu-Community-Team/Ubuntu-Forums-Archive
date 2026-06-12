---
title: "Stop isc-dhcp-server from automatically starting after reboot"
date: 2019-12-15
forum: Server Platforms
---

### Post by diktio on 2019-12-15
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]Running a Ubuntu server version 14.04 with isc-dhcp-server automatically starting after a reboot. My question is how can I stop isc-dhcp-server from starting automatically to manually? [/COLOR]
[COLOR=#000000]I can control the server via ssh without GUI. [/COLOR]


[COLOR=#000000]Regards,[/COLOR]

[COLOR=#000000]Rob[/COLOR]

---

### Post by howefield on 2019-12-15
Thread moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2019-12-16
14.04 uses traditional init.d files.  See the [manual page for chkconfig]("https://manpages.ubuntu.com/manpages/precise/man8/chkconfig.8.html").

```
sudo chkconfig isc-dhcp-server off
```

should do the trick.

---

### Post by diktio on 2019-12-17
Thanks but chkconfig is not available on this host ( Ubuntu 14.0.4) 
Also systemctl is not available 

Regards,

Rob

---

### Post by SeijiSensei on 2019-12-17
Well, you can disable it by brute force by removing the symbolic links to /etc/init.d/isc-dhcp-server from the directories in /etc/rc[1-6].d/.  The entries beginning with "S" start a service; those with a "K" stop the service.

14.04 doesn't used systemd, so systemctl will not be present.

---

### Post by diktio on 2019-12-26
Hi thanks,

Does the following command do the same : [COLOR=#242729][FONT=Consolas]sudo update-rc.d -f isc-dhcp-server remove ? 

Regards,

Rob 

[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-12-26
I don't know, but it wouldn't hurt to try.  Worst case is nothing changes.

---

### Post by diktio on 2020-01-06
Thanks 

Regards,

Rob

---

