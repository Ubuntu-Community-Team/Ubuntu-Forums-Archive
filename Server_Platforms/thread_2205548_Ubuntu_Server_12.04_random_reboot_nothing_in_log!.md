---
title: "Ubuntu Server 12.04 random reboot? nothing in log!"
date: 2014-02-14
forum: Server Platforms
---

### Post by muhammad.umair on 2014-02-14
Version: Ubuntu 12.04.3 LTS (precise)

uname -a: Linux sysname 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

We have a few Ubuntu servers running in our lab, on some of which we have experienced random reboots. A reboot may happen with a gap of a few days, or may not occur at all. On one machine for example the exact reboot time was "Wed Feb 12 12:56 EST".

I have gone through all the logs I could possibly think of, around the time of reboot (syslog, kernlog, authlog etc), but the reboot seems to be occuring out of the blue. No error/warning/panic messages whatsoever in the log, seems like the system just rebooted during a proper normal working state so to speak. Sample log at the time of reboot (Feb 12 12:56) is as follows:

Feb 12 12:56:55 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.191.130 from 3e:f0:47:96:a9:6a via vmnet8
Feb 12 12:56:57 sysname vmnet-dhcpd: DHCPACK on 192.168.191.130 to 3e:f0:47:96:a9:6a via vmnet8
Feb 12 12:56:57 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.191.141 from 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:08 sysname snmpd[9816]: Connection from UDP: [10.14.44.27]:59568->[10.14.47.114]
Feb 12 12:57:08 sysname vmnet-dhcpd: DHCPACK on 192.168.191.141 to 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:08 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.191.141 from 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:08 sysname snmpd[9816]: Connection from UDP: [10.14.44.27]:59568->[10.14.47.114]
Feb 12 12:57:14 snmpd[9816]: last message repeated 2 times
Feb 12 12:57:14 sysname vmnet-dhcpd: DHCPACK on 192.168.191.141 to 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:14 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.191.141 from 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:18 sysname vmnet-dhcpd: DHCPACK on 192.168.191.141 to 22:9c:0f:78:c1:83 via vmnet8
Feb 12 12:57:38 sysname snmpd[9816]: Connection from UDP: [10.14.44.27]:58736->[10.14.47.114]
Feb 12 12:58:45 sysname kerFeb 12 12:56:12 sysname kernel: imklog 5.8.6, log source = /proc/kmsg started.
Feb 12 12:56:12 sysname rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1269" x-info="http://www.rsyslog.com"] start
Feb 12 12:56:12 sysname rsyslogd: rsyslogd's groupid changed to 103
Feb 12 12:56:12 sysname rsyslogd: rsyslogd's userid changed to 101
Feb 12 12:56:12 sysname rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb 12 12:56:12 sysname kernel: [ 0.000000] Initializing cgroup subsys cpuset
Feb 12 12:56:12 sysname kernel: [ 0.000000] Initializing cgroup subsys cpu
Feb 12 12:56:12 sysname kernel: [ 0.000000] Linux version 3.5.0-23-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 (Ubuntu 3.5.0-23.35~precise1-generic 3.5.7.2)

All I am able to observe from the log is a little time discrepancy where the log time stamps go from 12:56 to 12:57 and then back to 12:56 and on. Other than that I can't seem to identify any sort of a message hinting at the cause of reboot.

Linked below is the syslog file with a few more minutes worth of context:

**dropbox.com/s/g3cx4gwvwuhndpd/syslog.2**

What exactly am I missing here? kindly help me out in identifying the root cause of these reboots!

Note: These Ubuntu servers for the most part are running multiple VMWare Workstation VMs

---

### Post by ian-weisser on 2014-02-14
Ubuntu does not reboot without quite a bit of shutdown activity first, usually over several seconds. That activity is not in the log snippet.
For example, the DHCP lease is not released.

I would start looking at hardware-based causes. Those do happen unexpectedly, and leave no log entries.

---

### Post by muhammad.umair on 2014-02-15
> **ian-weisser said:**
> Ubuntu does not reboot without quite a bit of shutdown activity first, usually over several seconds. That activity is not in the log snippet.
For example, the DHCP lease is not released.

I would start looking at hardware-based causes. Those do happen unexpectedly, and leave no log entries.


I apologize for my ignorance, but what are the most common hardware-related issues that I might look into? I assume one must be temperature, regarding that I tried to install lm-sensors on one of the machines few hours back. Now the machine are running on top of AMD Opteron 6380 (16-core) x2 CPUs. I allowed lm-sensors to scan all possible ranges that it was prompting, despite of that I was unable to get CPU temperature. All it showed was some PCI-Adapter voltages and temperatures. Any suggestions on that?

---

### Post by papibe on 2014-02-15
Hi muhammad.umair.

This should get you started: [How can I check my ram and harddrive for errors]("http://askubuntu.com/questions/14303/how-can-i-check-my-ram-and-harddrive-for-errors").

Hope it helps.
Regards.

---

### Post by tgalati4 on 2014-02-15
It's quite possible that your CPU got hot and caused a rapid, thermal shutdown.  It's possible that lm-sensors cannot detect the temperature diodes for that CPU.  You will have to do some digging to find that.  Other problems are power supply dropouts.  If you have similar servers, try moving them around.  Mark each PSU with a Sharpie and put stickies on the machines to show which PSU is on which machine:  #1, #2, #3, etc.  If one machine drops out more frequently than the others, then keep an eye on that PSU.  See if the problem follows the PSU.

Motherboards can develop intermittent faults.  Reseat all cables and connections.  Clean the machines if they are dusty.  How old are these machines?  Most server hardware with a 5-year warranty will fail in year 6.

---

### Post by muhammad.umair on 2014-02-17
> **tgalati4 said:**
> It's quite possible that your CPU got hot and caused a rapid, thermal shutdown.  It's possible that lm-sensors cannot detect the temperature diodes for that CPU.  You will have to do some digging to find that.  Other problems are power supply dropouts.  If you have similar servers, try moving them around.  Mark each PSU with a Sharpie and put stickies on the machines to show which PSU is on which machine:  #1, #2, #3, etc.  If one machine drops out more frequently than the others, then keep an eye on that PSU.  See if the problem follows the PSU.

Motherboards can develop intermittent faults.  Reseat all cables and connections.  Clean the machines if they are dusty.  How old are these machines?  Most server hardware with a 5-year warranty will fail in year 6.


The machines are brand new! And yea I got the lm-sensors module to work, and i've installed and configured the sensord daemon to dump CPU temperatures every 30 seconds, lets see if it turns up something on the next reboot. Also, I ran 32 instances (as collectively the CPUs have 32 cores) of cpuburn for like 90 minutes, on one of the machines that is experiencing reboots, but despite of the near 100% CPU activity, the temperatures didn't reach critical points. I am hoping the lm-sensors readings aren't THAT unreliable.

---

### Post by tgalati4 on 2014-02-17
Well 32 cores means the chance of a CPU lockup increase.  New machines need a break-in period to weed out the early failures.  Keep an ssh terminal open at all times so you can see the processes and check the log files.  Check your RAM with memtest--take it through 30 complete cycles.

---

### Post by fugu2 on 2014-02-18
I can think of 2 things you might want to check:1) Some BIOS's can keep logs of some hardware failures2) Is your power supply stable? Maybe a loose or bad cable/outlet?

---

### Post by muhammad.umair on 2014-02-18
Here's a log snippet from a more recent machine reboot from our log. This time I had sensord configured to dump CPU temperatures so the log reflects that as well. However assuming that lm-sensors readings are reliable enough, I don't think the temperature has reached critical enough values for the machine to spontaneously reboot, has it?  (I've marked as bold the first message after the reboot occurred)

Feb 18 00:27:50 sysname kernel: [5065491.216053] /dev/vmnet: open called by PID 27122 (vmx-vcpu-0)
Feb 18 00:27:50 sysname kernel: [5065491.216082] /dev/vmnet: port on hub 8 successfully opened
Feb 18 00:27:50 sysname kernel: [5065491.216095] /dev/vmnet: open called by PID 27122 (vmx-vcpu-0)
Feb 18 00:27:50 sysname kernel: [5065491.216102] /dev/vmnet: port on hub 8 successfully opened
Feb 18 00:27:51 sysname vmnet-dhcpd: DHCPDISCOVER from 8a:78:f7:00:68:5d via vmnet8
Feb 18 00:27:51 sysname vmnet-dhcpd: DHCPOFFER on 192.168.120.136 to 8a:78:f7:00:68:5d via vmnet8
Feb 18 00:27:51 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.120.136 from 8a:78:f7:00:68:5d via vmnet8
Feb 18 00:27:51 sysname vmnet-dhcpd: DHCPACK on 192.168.120.136 to 8a:78:f7:00:68:5d via vmnet8
Feb 18 00:27:52 sysname vmnet-dhcpd: DHCPDISCOVER from 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:27:53 sysname vmnet-dhcpd: DHCPOFFER on 192.168.120.129 to 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:27:53 sysname vmnet-dhcpd: DHCPDISCOVER from 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:27:53 sysname vmnet-dhcpd: DHCPOFFER on 192.168.120.129 to 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:27:53 sysname vmnet-dhcpd: DHCPREQUEST for 192.168.120.129 from 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:27:53 sysname vmnet-dhcpd: DHCPACK on 192.168.120.129 to 22:cf:f6:1f:99:cb via vmnet8
Feb 18 00:28:03 sysname sensord: Chip: k10temp-pci-00c3
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
Feb 18 00:28:03 sysname sensord:   temp1: 45.0 C
Feb 18 00:28:03 sysname sensord: Chip: k10temp-pci-00cb
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
Feb 18 00:28:03 sysname sensord:   temp1: 44.6 C
Feb 18 00:28:03 sysname sensord: Chip: k10temp-pci-00d3
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
Feb 18 00:28:03 sysname sensord:   temp1: 36.4 C
Feb 18 00:28:03 sysname sensord: Chip: k10temp-pci-00db
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
Feb 18 00:28:03 sysname sensord:   temp1: 35.8 C
Feb 18 00:28:03 sysname sensord: Chip: fam15h_power-pci-00c4
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
Feb 18 00:28:03 sysname sensord: Chip: fam15h_power-pci-00d4
Feb 18 00:28:03 sysname sensord: Adapter: PCI adapter
**Feb 18 00:26:11 sysname kernel: imklog 5.8.6, log source = /proc/kmsg started.**
Feb 18 00:26:11 sysname rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1227" x-info="http://www.rsyslog.com"] start
Feb 18 00:26:11 sysname rsyslogd: rsyslogd's groupid changed to 103
Feb 18 00:26:11 sysname rsyslogd: rsyslogd's userid changed to 101
Feb 18 00:26:11 sysname rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb 18 00:26:11 sysname kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 18 00:26:11 sysname kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 18 00:26:11 sysname kernel: [    0.000000] Linux version 3.5.0-23-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 (Ubuntu 3.5.0-23.35~precise1-generic 3.5.7.2)

Here is the output of the sensors, while the machine is pretty much in an idle state:

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +16.5°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)

k10temp-pci-00cb
Adapter: PCI adapter
temp1:        +16.5°C  (high = +70.0°C)

k10temp-pci-00d3
Adapter: PCI adapter
temp1:        +16.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)

k10temp-pci-00db
Adapter: PCI adapter
temp1:        +16.0°C  (high = +70.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       43.17 W  (crit = 114.49 W)

fam15h_power-pci-00d4
Adapter: PCI adapter
power1:       40.99 W  (crit = 114.49 W)


Another thing I'd like to mention here is that, all machines in our lab are although running on Ubuntu Server 12.04.3 LTS, but its not stock. This version comes with kernel 3.8, whereas due the nature of our requirements, we had to downgrade the kernel to 3.5 on all machines. Could that be a possible reason?

What confuses me is, if the machine actually is going down due to kernel panic or something like that, why is nothing showing up in the logs? Is it possible that even with a software related failure (such as a kernel panic), the logs could come up with no indication of the failure whatsoever?

---

### Post by tgalati4 on 2014-02-18
Again, that normally points to hardware failure.  A kernel issue usually leaves breadcrumbs.  You will have to research the differences between kernel 3.5 vs 3.8 to determine if any of the changes will affect your machines.  If you have two identical machines, then swap the power supplies.  Otherwise, get an RMA and replace the server.  It obviously doesn't meet your reliability requirements.

Your temperatures look OK, so that only eliminates one theory--thermal shutdown.

The other step I would take is to update the BIOS from the manufacturer.  There may be a bug in the BIOS that causes problems.

---

### Post by brokenhachi on 2014-02-20
Is this a bare-metal install of ubuntu or are you running on top of some hypervisor?

Were you not able to get CPU temp? ([http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature](http://askubuntu.com/questions/15832/how-do-i-get-the-cpu-temperature)) ```
sensors-detect
```

---

