---
title: "Simple DHCP"
date: 2024-11-01
forum: Server Platforms
---

### Post by hlad05 on 2024-11-01
Hello
I plan to install a new DHCP server.
On old server CentOS (LSB Version: core-3.1) running DHCP client "Internet Systems Consortium DHCP Client V3.0.5-RedHat".
New DHCP server is "ubuntu-24.04.1-live-server".

We use DHCP only for static IP defined in file.
Old DHCP is very simply:
-----
...
dhcp    on
100.1.0.100     0       e       hinet           D8:5D:64:45:F6:61 #server 1
100.1.0.101     0       e       hinet           D8:5D:64:45:F2:39
100.1.0.102     0       e       hinet           53:EA:F6:BA:1A:49 #test PC 1
-----
Just write the IP address and MAC in the file, thats all. 
Can the DHCP on the new server be set up this way as well? I think the device name must be set (can't do without it?).

Thank You.

---

