---
title: "Disable the OOM Killer"
date: 2014-01-01
forum: Server Platforms
---

### Post by PsionicArchon on 2014-01-01
As the title suggests, regardless of the repercussions, how do you disable this "feature". 

Please do not provide alternate suggestions such as "get more ram" or "tell the program to use less memory". 

I'm running a Minecraft server that has its heap space and permgen configured to use nearly all of the available memory on the vps where it resides. I have a highly specific reason for doing this and no, it has never caused me any problems in the past.

Yes the OOM Killer is killing the process see: OOM killed process 659 (java) vm:4973220kB, rss:2066504kB, swap:0kB

Who ever thought killing processes that are consuming beyond a specific amount of memory was a good idea, you have caused me and, the users of my server immeasurable levels of frustration. I am no Linux guru, so any help would be appreciated so long as that help reads "To disable  the oom-killer do X". 

Thank you in advance.

---

### Post by Iowan on 2014-01-01
[http://thetechnick.blogspot.com/2010/12/steps-to-disable-oom-on-linux.html](http://thetechnick.blogspot.com/2010/12/steps-to-disable-oom-on-linux.html)
[http://www.oracle.com/technetwork/articles/servers-storage-dev/oom-killer-1911807.html](http://www.oracle.com/technetwork/articles/servers-storage-dev/oom-killer-1911807.html)
> The OOM killer can be completely disabled with the following command. This is not recommended for production environments, because if an out-of-memory condition does present itself, there could be unexpected behavior depending on the available system resources and configuration. This unexpected behavior could be anything from a kernel panic to a hang depending on the resources available to the kernel at the time of the OOM condition.

sysctl vm.overcommit_memory=2
echo "vm.overcommit_memory=2" >> /etc/sysctl.conf

---

### Post by PsionicArchon on 2014-01-01
This is my sysctl.conf with those settings added and, after a system reboot.

```
-----

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

vm.oom-kill = 0
vm.overcommit_memory = 2 

-----
```

The oom killer is still killing the java process.

Edit: I have a bit of an update, if anyone is still willing to help. 

When attempting to force the sysctl file to reload I get this:  permission denied on key 'vm.overcommit_memory'

How can I be denied permission to use a command as root... This is all rather headache inducing and, it's starting to look like I'll be terminating my vps account as it's no longer viable.

---

### Post by Jonathan L on 2014-05-25
Hi Psionic

I was having the same difficulties.  You report that the oom-killer is still killing your process, I suggest either properly fully disabling the oom-killer or lowering the overcommit ratio, as follows:

_** Disabling OOM Killer**_

According to: [https://www.kernel.org/doc/Documentation/cgroups/memory.txt](https://www.kernel.org/doc/Documentation/cgroups/memory.txt)
```
You can disable the OOM-killer by writing "1" to memory.oom_control file, as:
    #echo 1 > memory.oom_control
```

_** Reducing Overcommit Ratio**_

According to [https://www.kernel.org/doc/Documentation/vm/overcommit-accounting](https://www.kernel.org/doc/Documentation/vm/overcommit-accounting)
 ```
2    -    Don't overcommit. The total address space commit
        for the system is not permitted to exceed swap + a
        configurable amount (default is 50%) of physical RAM.
        Depending on the amount you use, in most situations
        this means a process will not be killed while accessing
        pages but will receive errors on memory allocation as
        appropriate.

        Useful for applications that want to guarantee their
        memory allocations will be available in the future
        without having to initialize every page.

  The overcommit policy is set via the sysctl `vm.overcommit_memory'.

  The overcommit amount can be set via `vm.overcommit_ratio' (percentage)
  or `vm.overcommit_kbytes' (absolute value).

```

There's a rather good article on this topic [http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html?page=1)

Of course, in general if you're getting processes killed it means there's a problem with using more memory than the system can cope with, and the symptoms are very likely to come out somewhere else.  In my case the oom-killer was definitely picking the right process, even though it was the primary purpose of the whole computer: the program had a data-dependent bug and was allocating memory out of control.

I hope that helps.

Kind regards,
Jonathan.

---

