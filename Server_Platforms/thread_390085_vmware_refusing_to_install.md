---
title: "vmware refusing to install"
date: 2007-03-21
forum: Server Platforms
---

### Post by jms1989 on 2007-03-21
Hi, I have been trying to install the vmware on my system and I keep getting errors.

This what I get when I try to install it;

```

root@amber-1989:/home/jms1989# apt-get install vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vmware-player is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.169.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.143.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

/etc/init.d/functions: 227: Syntax error: Bad substitution
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please Help,
jms1989

---

### Post by DoLoop on 2007-03-21
The vmware-player package has been broken for a while.  See [this thread]("http://ubuntuforums.org/showthread.php?t=382113") for more info.

---

### Post by conjur3r on 2007-03-22
> **jms1989 said:**
> 
/etc/init.d/functions: 227: Syntax error: Bad substitution


Looks very similar to a bash/dash issue.  Try changing the default to bash rather than dash:
# sudo dpkg-reconfigure dash

If it doesn't work, no worries, you can change it back to dash.

---

### Post by jms1989 on 2007-03-23
It works thanks.

---

