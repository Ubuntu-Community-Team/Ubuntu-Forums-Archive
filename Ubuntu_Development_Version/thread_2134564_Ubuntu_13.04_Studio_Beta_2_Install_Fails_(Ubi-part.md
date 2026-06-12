---
title: "Ubuntu 13.04 Studio Beta 2 Install Fails (Ubi-partman, Time Zone, Nouveau)"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by fowlslegs on 2013-04-11
System: Timeline Ultra M5-481TG, recently updated BIOS.  Install Options: Clean install onto completely unallocated HDD, using Logical Volume Management, download updates, and install proprietary software.  Partitions: sda1--491.5GB, primary, ext4, /; sda2--GB, primary, swap area.  Notes: Previously had 12.10 Ubuntu Studio Running, tried daily build of Ubuntu 13.04 Studio with a similar error, tried using Startup Disk Creator and UNetbootin.  Errors: If installing directly from menu install will go fine until it crashes at "time zone configuration," (not when you first select your time zone yourself, but during the actual installation process), bug report fails. If installing from within "Try Ubuntu" crashes at point you select your time zone yourself with "ubi-partman error code 10."  var/log/syslog contents:     ```
Apr 11 17:38:11 ubuntu-studio kernel: imklog 5.8.11, log source = /proc/kmsg started. Apr 11 17:38:11 ubuntu-studio rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="1449" x-info="http://www.rsyslog.com"] start Apr 11 17:38:11 ubuntu-studio rsyslogd: rsyslogd's groupid changed to 103 Apr 11 17:38:11 ubuntu-studio rsyslogd: rsyslogd's userid changed to 101 Apr 11 17:38:11 ubuntu-studio rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ] Apr 11 17:38:11 ubuntu-studio kernel: [   38.941727] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941751] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941773] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941795] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000
```  The nouveau error will repeat indefinitely.

---

### Post by fowlslegs on 2013-04-11
Sorry, I had everything nicely spaced including the code. Preview displayed it nicely, but when I posted it came out like this.

---

### Post by smartboyhw on 2013-04-12
> **fowlslegs said:**
> System: Timeline Ultra M5-481TG, recently updated BIOS.  Install Options: Clean install onto completely unallocated HDD, using Logical Volume Management, download updates, and install proprietary software.  Partitions: sda1--491.5GB, primary, ext4, /; sda2--GB, primary, swap area.  Notes: Previously had 12.10 Ubuntu Studio Running, tried daily build of Ubuntu 13.04 Studio with a similar error, tried using Startup Disk Creator and UNetbootin.  Errors: If installing directly from menu install will go fine until it crashes at "time zone configuration," (not when you first select your time zone yourself, but during the actual installation process), bug report fails. If installing from within "Try Ubuntu" crashes at point you select your time zone yourself with "ubi-partman error code 10."  var/log/syslog contents:     ```
Apr 11 17:38:11 ubuntu-studio kernel: imklog 5.8.11, log source = /proc/kmsg started. Apr 11 17:38:11 ubuntu-studio rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="1449" x-info="http://www.rsyslog.com"] start Apr 11 17:38:11 ubuntu-studio rsyslogd: rsyslogd's groupid changed to 103 Apr 11 17:38:11 ubuntu-studio rsyslogd: rsyslogd's userid changed to 101 Apr 11 17:38:11 ubuntu-studio rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ] Apr 11 17:38:11 ubuntu-studio kernel: [   38.941727] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941751] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941773] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000 Apr 11 17:38:11 ubuntu-studio kernel: [   38.941795] nouveau E[     PMC][0000:01:00.0] unknown intr 0x00040000
```  The nouveau error will repeat indefinitely.


Would you like to report a bug on Launchpad? Target the bug against nouveau (Ubuntu).

---

### Post by fowlslegs on 2013-04-13
I did thank you.

---

