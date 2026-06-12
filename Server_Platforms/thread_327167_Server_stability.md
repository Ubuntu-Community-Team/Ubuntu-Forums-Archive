---
title: "Server stability"
date: 2006-12-28
forum: Server Platforms
---

### Post by lubod on 2006-12-28
Hello, I'm currently using Dapper (6.06 LTS) Server with two network interfaces, for external WAN access and internal LAN access, and in most respects it is doing precisely what is required, which at the moment is DHCP (ISC dhcpd), NAT (IPTables), Web serving (Apache), and a couple of other server functions.

Some questions come to mind:

Recently, after running just short of 20 days non-stop, the NAT seemed to malfunction.
DHCP addresses kept being handed out on the LAN side, and standing at the console I could verify that the external WAN interface could ping [www.google.com](www.google.com) for example, but the forwarding was not happening at all.

A reboot cured it, but that is what I call a "Microsoft" fix. I'd appreciate suggestions where I can track down what went wrong (perhaps /var/log/messages, kern.log, or syslog?)

Also, if it is a bug that someone else experienced before, or something more specific about my configuration. Is there a quick way to dump information of the sort various Mac OS X or windows system profiler utilities do?

I can do uname -a:
Linux mercury 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux

/proc/cpuinfo shows what appear to be two Pentium(D) 2.8 Ghz
quantity of RAM is not supposed to be a problem, unless somehow 2 Gb is not enough
(of course I have no idea about its condition so taking the system offline and running the built in memory test might be a good idea)

top output:

top - 15:33:38 up 2 days,  2:12,  2 users,  load average: 0.04, 0.02, 0.00
Tasks:  82 total,   1 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0% us,  0.0% sy,  0.0% ni, 100.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   2074604k total,   380328k used,  1694276k free,   136108k buffers
Swap:  3196892k total,        0k used,  3196892k free,   146160k cached

Maybe some output from dpkg or apt-get to indicate what packages are installed would help, since essentially everything from the Server CD to Webmin 1.300 was installed either from a .deb or directly through apt-get, so there should be a complete record, if only I knew the syntax.

I saw several similar threads where the problem seemed to be ACPI or APIC, so I'm considering turning those off, but would like to know what I'd lose by doing so (presumably performance?)

---

