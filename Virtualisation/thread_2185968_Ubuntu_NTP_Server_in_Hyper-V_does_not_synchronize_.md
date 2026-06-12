---
title: "Ubuntu NTP Server in Hyper-V does not synchronize time with external NTP sources"
date: 2013-11-05
forum: Virtualisation
---

### Post by jey2 on 2013-11-05
There is a virtual machine with Ubuntu Server 12.04 LTS x64 that is running inside of Hyper-V Server 2012 hypervisor. NTPD daemon is up and running on Ubuntu, but it does not synchronize with external NTP servers. The required ports are open. NTP traffic on UDP ports 123 are permitted and flows. **Ntpq -p** and **ntptrace** commands consistently show STRATUM 16, ie, server is not synchronized with the external NTP servers.

[FONT=courier new]**# ntpq -p**
      remote           refid      st t when poll reach   delay   offset  jitter
 ==============================================================================
  ns2.odessa.coms .INIT.          16 u    - 1024    0    0.000    0.000   0.000
  nsa.lds.net.ua  .INIT.          16 u    - 1024    0    0.000    0.000   0.000
  magnat.ip-conne .INIT.          16 u    - 1024    0    0.000    0.000   0.000
  ns4.pay-port.ki .INIT.          16 u    - 1024    0    0.000    0.000   0.000

**# ntptrace**
 localhost: stratum 16, offset 0.000000, synch distance 0.000000
[/FONT]

hwclock and date shows different results.

[FONT=Courier New]**# hwclock; date**
Tue 05 Nov 2013 12:44:26 PM EET  -1.145487 seconds
Tue Nov  5 12:37:42 EET 2013[/FONT]

Here is NTPD config

[FONT=Courier New]# /etc/ntp.conf, configuration for ntpd

 driftfile /var/lib/ntp/ntp.drift
 logfile   /var/log/ntp.log

 # Sync witn these servers

 server 0.ua.pool.ntp.org iburst prefer
 server 1.ua.pool.ntp.org iburst
 server 2.ua.pool.ntp.org iburst
 server 3.ua.pool.ntp.org iburst


 # Allow to sync only our net and localhost

 restrict default ignore
 restrict 10.X.0.0 mask 255.255.0.0 notrap nomodify
 restrict 127.0.0.1
 restrict ::1


 # Allow to sync with NTP servers

 restrict 0.ua.pool.ntp.org
 restrict 1.ua.pool.ntp.org
 restrict 2.ua.pool.ntp.org
 restrict 3.ua.pool.ntp.org
[/FONT]

I found this link **[https://www.vpsblocks.com.au/support/Knowledgebase/Article/View/64/9/ubuntu-time-drifting---solved](https://www.vpsblocks.com.au/support/Knowledgebase/Article/View/64/9/ubuntu-time-drifting---solved)**
I've made everything on this article, but it doesn't help for me. In the VM Integration Services Settings I've disabled "Time Synchronization" checkbox, then restart Ubuntu VM, but no success with NTP.

Before Ubuntu there was FreeBSD 9.2 x64 VM inside of Hyper-V Server 2012 hypervisor. There no official Hyper-V Integration Services for FreeBSD. NTP Server was working excellent, the VM successfully was synchronizing with external NTP.

---

### Post by bashiergui on 2013-11-23
What network configuration are you using for the vm? Do you need to forward the ntp port from the vm to the host? Do you have a firewall set on the vm or host and are the ports open if so?

---

