---
title: "[SOLVED] syslog-ng with Cisco PIX"
date: 2007-12-02
forum: Server Platforms
---

### Post by MatsB on 2007-12-02
Hi,

For some reason I can't get any log information from my Cisco PIX to syslog-ng. Any ideas?

This is what I've added to /etc/syslog-ng/syslog-ng.conf. Everything els is unchanged.
--------------------------------------------------------------------

source network {
        udp();
};

destination df_pix { file("/var/log/pix.log"); };

filter f_local4 { facility(local4); };

log {
        source(network);
        filter(f_local4);
        destination(df_pix);
};


/var/log
-rw-r--r-- 1 root        adm           0 2007-12-02 14:10 pix.log

Cisco PIX
----------------------------------------------------------------------
logging on
logging timestamp
logging monitor debugging
logging buffered debugging
logging host inside 192.168.0.103
logging facility 20 (deafult)

---

### Post by MatsB on 2007-12-03
I've also tried this setup and still nothing in my pix.log file :(

source network {
udp();
};

destination df_pix { file("/var/log/pix.log"); };

log {
source(network);
destination(df_pix);
};


Cisco PIX
----------------------------------------------------------------------
logging on
logging timestamp
logging monitor debugging
logging buffered debugging
logging host inside 192.168.0.103

---

### Post by Maxtorm on 2007-12-03
I guess your next step for troubleshooting is to determine whether the problem is the PIX or the Ubuntu box. You could run ettercap on the Ubuntu box to sniff for traffic and then create a dummy syslog event on the PIX.

---

### Post by MatsB on 2007-12-04
I simply missed this command in the pix.

logging trap informal

---

