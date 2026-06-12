---
title: "Syslog-ng and iptables"
date: 2011-07-14
forum: Security
---

### Post by pacifiste95 on 2011-07-14
Hello,

i've a problem with syslog-ng filter and iptables.

So, this is an example of my iptables log : 

```
Jul 13 08:27:01 davis kernel: [2447090.462486] iptables RULE -16 -- ACCEPT IN= OUT=eth4 SRC=10.100.40.2 DST=224.0.0.18 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=25462 PROTO=112 
Jul 13 08:27:01 davis kernel: [2447090.462773] iptables RULE -16 -- ACCEPT IN= OUT=eth1 SRC=10.100.10.2 DST=224.0.0.18 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=25462 PROTO=112 
Jul 13 08:27:01 davis CRON[24335]: (root) CMD (cp /var/log/iptables.log /opt/log/iptables/davis/iptables.log       # exports log iptable every min)
Jul 13 08:27:02 davis kernel: [2447091.460677] iptables RULE -16 -- ACCEPT IN= OUT=eth3 SRC=10.100.30.2 DST=224.0.0.18 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=25462 PROTO=112 
Jul 13 08:27:02 davis kernel: [2447091.460866] iptables RULE -16 -- ACCEPT IN= OUT=eth2 SRC=10.100.20.2 DST=224.0.0.18 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=25462 PROTO=112 
```

And this is my configuration in syslog-ng.conf file : 

```
destination iptables_fw {
                        file("/var/log/archive/$R_YEAR-$R_MONTH-$R_DAY/firewall"
                        template("$HOUR:$MIN:$SEC $HOST <$FACILITY.$PRIORITY> $MSG\n")
                        template_escape(no)
                        );
};

filter f_iptables { match("RULE") 
or match("iptables"); }; 

log {
        source(local);
        filter(f_iptables);
        destination(iptables_fw);
};
```

I get a "firewall" file, but in this file i only get this lines : 

```
14:50:01 davis <cron.info> CRON[28985]: (root) CMD (cp /var/log/iptables.log /opt/log/iptables/davis/iptables.log       # exports log iptable every min)
14:51:01 davis <cron.info> CRON[29018]: (root) CMD (cp /var/log/iptables.log /opt/log/iptables/davis/iptables.log       # exports log iptable every min)
14:52:01 davis <cron.info> CRON[29022]: (root) CMD (cp /var/log/iptables.log /opt/log/iptables/davis/iptables.log       # exports log iptable every min)
14:53:01 davis <cron.info> CRON[29026]: (root) CMD (cp /var/log/iptables.log /opt/log/iptables/davis/iptables.log       # exports log iptable every min)
```

But i don't want this, i want this type of line :

**"Jul 13 08:27:01 davis kernel: [2447090.462486] iptables RULE -16 -- ACCEPT IN= OUT=eth4 SRC=10.100.40.2 DST=224.0.0.18 LEN=40 TOS=0x00 PREC=0x00 TTL=255 ID=25462 PROTO=112"**

What is the problem in my syslog-ng configuration?

Thanks :) :)

---

