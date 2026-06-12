---
title: "VMware Configuration Issues on 64bit Ubuntu Server"
date: 2010-10-05
forum: Virtualisation
---

### Post by BradleyAtkins on 2010-10-05
Hi All

I am still flailing about trying to bottom out why VMware Server will not let me connect to the UI. Having dug around some more and followed various threads I have a number of question and would be grateful if any could answer any of them: -

1) I came across a post where someone seemed to successfully overcome this problem by issuing the commands: -

```
/etc/init.d/vmware-core start
/etc/init.d/vmware-mgmt  start
/etc/init.d/vmware-autostart start

```

These commands just give me the error: -

```
root@poweredge:~# /etc/init.d/vmware-core start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.
```

Executing config.pl: -

```
/usr/bin/vmware-config.pl
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmci
vmnet
vmmon

I.e. - 'rm /lib/modules/2.6.32-24-server/misc/<ModuleName>.{o,ko}'

Execution aborted.
```

I am prompted to remove these every time I run the vmware-config.pl command. Yet when I am running it I get to a point where it says it was going to delete them but someone (ME!) has already done it. Its as though it cannot recognise at the start that it was the tool that installed them but by the time it reaches the end it does.

2) Another post I was looking at suggested running the chkconfig utility. I am not to sure what this is telling me so any insight  into this output would be appreciated: -

```
chkconfig –list 
vmware                    0:off  1:off  2:on   3:on   4:off  5:on   6:off
vmware-autostart          0:off  1:off  2:off  3:off  4:off  5:off  6:off
vmware-core               0:off  1:off  2:off  3:off  4:off  5:off  6:off
vmware-mgmt               0:off  1:off  2:off  3:off  4:off  5:off  6:off

```

```
chkconfig vmware
vmware  on

```

```
chkconfig -a vmware
insserv: warning: current stop runlevel(s) (0 2 3 5 6) of script `vmware' overwrites defaults (0 6).
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-core: service VMware already provided!
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: script vmware-autostart: service VMware already provided!
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: script vmware-mgmt: service VMware already provided!
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
vmware                    0:off  1:off  2:on   3:on   4:off  5:on   6:off

```

3) Some posts I came across earlier in my struggles suggested commenting out these entries in /etc/hosts. Is this correct? : -

```
# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
```

Any help appreciated 

Cheers

---

