---
title: "ifconfig statistics reset"
date: 2011-04-19
forum: Server Platforms
---

### Post by ethernaly on 2011-04-19
hello, is there an easy way to reset ifconfig statistics?
I've a server, and I need to send via email bandwidth usage. (with a script in cronjob)

but at the end of the script, I need a way to reset:

RX bytes:12373569355 (12.3 GB)  TX bytes:4598971089 (4.5 GB)
RX bytes:3793248996 (3.7 GB)  TX bytes:3793248996 (3.7 GB)

can you help me? I tried to search with google and search form, but nothing results.



edit:
/etc/init.d/networking restart (or reload) doesn't work

edit 2:
I tried:
#!/bin/bash
ifconfig eth0 down
ifconfig eth0 up

but this have stuck my server.

---

### Post by ethernaly on 2011-04-19
solved by myself:

ethtool -i eth0 (to find driver used by eth0)

than script:
```
#!/bin/bash
/etc/init.d/networking stop
modprobe -r DRIVER
modprobe DRIVER
/etc/init.d/networking start
```


So my script:

```
#!/bin/bash

#### Print network usage ####
echo "Report $(date)" > report.txt
echo "Network USAGE" >> report.txt
ifconfig eth0 | grep "TX bytes" >> report.txt

#### eset network usage ####
#### pcnet32 is the name of diver used by vmware esxi ####
/etc/init.d/networking stop
modprobe -r pcnet32
modprobe pcnet32
/etc/init.d/networking start


cat report.txt | mail -s "REPORT $(date)" myemail@domain.com
```

THIS script is working only if your kernel support "load modules function". (modprobe / modprobe -r)

---

