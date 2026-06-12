---
title: "ssh leaks"
date: 2008-12-05
forum: Security
---

### Post by notgeekenough on 2008-12-05
I just ran a nessus scan on my small WLAN. My laptop is Ubuntu 8.04 and while I got low severity, I have problems about my ssh. Nessus was able to obtain all my installed software, and my MAC addresses via ssh. Is there anyway to stop this? I dont even have the ssh server running.

---

### Post by The Tronyx on 2008-12-06
> **notgeekenough said:**
> I just ran a nessus scan on my small WLAN. My laptop is Ubuntu 8.04 and while I got low severity, I have problems about my ssh. Nessus was able to obtain all my installed software, and my MAC addresses via ssh. Is there anyway to stop this? I dont even have the ssh server running.

Did it actually display a list of installed software or did it just say it was possible?  If you don't have an SSH server running, then it is most likely a false positive but if you give us the exact Nessus message it will be easier to tell.  It is also possible that you do have an SSH server running but you aren't aware of it.  To check, you can run 'ps aux | grep sshd' without the ticks.

On another note obtaining your MAC address isn't that big of a deal and the chances are that any machine on the LAN can pull your MAC address.

---

### Post by notgeekenough on 2008-12-07
did ps aux ... command, no ssh running. Below is the nessus ouput truncated

```

Software Enumeration (via SSH)

Synopsis :

It is possible to enumerate installed software on the remote host, via SSH.

Description :

This plugin lists the software installed on the remote host by calling the
appropriate command (rpm -qa on RPM-based Linux distributions, qpkg, dpkg, etc...)

Solution :

Remove software that is not compliant with your company policy.

Risk factor :

None
Plugin output :

Here is the list of packages installed on the remote Linux system :
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==========================================-====================================================-============================================
ii acl 2.2.45-1 Access control list utilities
ii acpi 0.09-3ubuntu1 displays information on ACPI devices
...
...
Nessus ID : 22869

```

---

