---
title: "ntptrace timed out"
date: 2011-01-03
forum: Server Platforms
---

### Post by damateem on 2011-01-03
I decided to add time synchronization to my Ubuntu 10.04LTS. I followed the command line configuration instruction given at [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) and added the following servers.

server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org

The install and configuration went fine, but I wanted to gain some confidence that it was working correctly, so I performed the tests near the bottom of the page.

host seems to be working fine:

```

david@server1:~/temp/config_file_backup/final_files$ host 3.us.pool.ntp.org
3.us.pool.ntp.org has address 204.9.136.253
3.us.pool.ntp.org has address 173.9.142.98
3.us.pool.ntp.org has address 173.203.202.87

```

ntpq seems to be working fine:

```

david@server1:~/temp/config_file_backup/final_files$ ntpq --numeric --peers
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
-216.129.104.26  164.67.62.194    2 u   16   64  377   84.497   -3.351   5.507
-38.117.195.101  38.96.163.131    3 u   11   64  377   45.913    4.159   6.096
+207.171.7.152   164.67.62.212    2 u    9   64  377   81.066    3.437   3.174
*173.255.211.195 216.218.192.202  2 u    1  128  377   80.020    0.333  11.945
+91.189.94.4     193.79.237.14    2 u    2   64  377  112.439    1.752   8.828

```

But, I get varying results from ntptrace:

```

david@server1:~/temp/config_file_backup/final_files$ ntptrace 0.us.pool.ntp.org
0.us.pool.ntp.org: stratum 2, offset 0.000876, synch distance 0.039538
stallman.cse.ohio-state.edu: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace 0.us.pool.ntp.org
packman-ha.isc.org: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace ntp.ubuntu.com
europium.canonical.com: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace 1.us.pool.ntp.org
1.us.pool.ntp.org: stratum 2, offset 0.000031, synch distance 0.049715
***Association ID 24827 unknown to server
david@server1:~/temp/config_file_backup/final_files$ ntptrace 2.us.pool.ntp.org
selenium.tilderoot.com: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace 3.us.pool.ntp.org
morose.quex.org: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace 0.us.pool.ntp.org
node1.mainframe.cx: timed out, nothing received
***Request timed out
david@server1:~/temp/config_file_backup/final_files$ ntptrace ntp.ubuntu.com
europium.canonical.com: timed out, nothing received
***Request timed out

```

The "timed out" text makes me nervous. Do these ntptrace results look typical?

Thanks,
David

---

### Post by samosamo on 2011-01-04
i don't know much about ntptrace but maybe it helps you to know that i have the same result

```
$ ntptrace 0.us.pool.ntp.org
0.us.pool.ntp.org: stratum 2, offset 0.000002, synch distance 0.016440
172.16.65.22: timed out, nothing received
***Request timed out
$
```

---

