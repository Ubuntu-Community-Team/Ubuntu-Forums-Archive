---
title: "syslog-ng and Nortel Baystack"
date: 2008-02-01
forum: Server Platforms
---

### Post by MatsB on 2008-02-01
Hi,

I'm not getting anything in my net.log file. If I run tcpdump I can see that the switch is sending syslog traffic on udp/514. Any ideas?

I've configured a Nortel Baystack 470 with these settings:

Event Logging: Enabled
Volatile Logging Option: Latch
Event Types To Log: Critical, Serious, Informational
Event Types To Log To NV Storage: Critical, Serious
Remote Logging: Enabled
Remote Logging Address: 10.100.100.15
Event Types To Log Remotely: Critical, Serious, Informational

My syslog-ng.conf looks like this:

destination df_net { file("var/log/net.log"); };

filter f_local0 { facility(local0); };
filter f_local1 { facility(local1); };
filter f_local2 { facility(local2); };
filter f_local3 { facility(local3); };
filter f_local4 { facility(local4); };
filter f_local5 { facility(local5); };
filter f_local6 { facility(local6); };
filter f_local7 { facility(local7); };

log {
        source(network);
        filter(f_local0);
        destination(df_net);
};

log {
        source(network);
        filter(f_local1);
        destination(df_net);
};

log {
        source(network);
        filter(f_local2);
        destination(df_net);
};

log {
        source(network);
        filter(f_local3);
        destination(df_net);
};

log {
        source(network);
        filter(f_local4);
        destination(df_net);
};

log {
        source(network);
        filter(f_local5);
        destination(df_net);
};

log {
        source(network);
        filter(f_local6);
        destination(df_net);
};

log {
        source(network);
        filter(f_local7);
        destination(df_net);
};

---

