---
title: "dns-nameservers line in /etc/network/interfaces not being used?"
date: 2011-08-30
forum: Server Platforms
---

### Post by romandas on 2011-08-30
I put my DNS server IP in /etc/network/interfaces as:
dns-nameservers 10.0.0.200

restarted networking, as well as rebooting, and yet name resolution does not work. Any reason why the dns-nameservers line isn't being honored?

I'm using Ubuntu Server 10.04 LTS.

---

### Post by romandas on 2011-08-30
It appears you need to install the resolvconf package to use the dns-* values in /etc/network/interfaces.  Did not realize that..

---

### Post by cconstantine on 2011-08-30
Check the open bugs for the resolvconf package. In my opinion, it doesn't work. There are issues with the startup sequencing that mean sometimes (as in, always, but only on some systems), you'll boot up with an empty /etc/resolv.conf file.

---

### Post by ningji on 2012-01-13
1. installed resolvconf

2. cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 1.5.182.182
netmask 255.255.252.0
gateway 1.50.183.254
dns-nameservers 1.5.5.5

auto eth0
iface eth0 inet dhcp

3. reboot
but not seeing 1.5.5.5 in /etc/resolv.conf,
neither in /var/run/resolvconf

Anyone tried this before ?

---

### Post by shulegaa on 2012-02-21
I'm having the same problem.  Has this been this solved?    

I have given up on editing /etc/resolv.conf.  I've put the  Ubuntu mandated dns-nameservers line into the appropriate  /etc/network/interfaces stanza for eth0.  

Lucky for me, I did  have the Ubuntu resolvconf package installed.    

Now, following works for me as root:  

ifdown eth0; ifup eth0 

This puts all the right contents into /etc/resolv.conf (which is now a symoblic link).

But a reboot smashes me back to having a blank /etc/resolv.conf file (as pointed to by this symbolic link).  DARN!   

It sure would be nice to configure Ubuntu once ... rather than upon each reboot.  

I'd be amused to hear the rationale behind this "break-user-specified-configuration-on-each-reboot" (by ignoring configuration file contents) approach.  DARN!  

I'm soooo bummed.
:-(

---

### Post by hawkmage on 2012-02-21
Are you using Network Manager?  This has a tenancy of thinking that it knows better than the config files and updateing the resolv.conf file with what it wants.  Normally if I am using static addressing I remove Network Manager to avoid issues.

You can update a file dhclient.conf.  Depending on what is installed you may have both a /etc/dhcp and /etc/dhcp3 directory both of which will have a dhclient.conf file in it.  I am not sure what version of dhcpd Ubuntu 10 has but I would assume that you are likely using the /etc/dhcp/dhclient.conf file.

In the dhclient.conf file add a line like this to override what Node Manger/DHCP is getting:
```
supersede domain-name-servers 1.5.5.5
```

Or if you want to add you DNS server to the beginning of what Node Manger/DHCP is getting:
```
prepend domain-name-servers 1.5.5.5
```

---

### Post by jymbob on 2013-02-20
I've just come across this issue on upgrading my server to 12.04.2

There was a conflict with /etc/resolv.conf not being a symlink which meant nothing was getting generated from my (correct) /etc/resolvconf/ files.

The solution:
```
sudo rm /etc/resolv.conf
sudo dpkg-reconfigure resolvconf

```

Hope this helps.

---

### Post by jdthood on 2013-02-20
> **jymbob said:**
> I've just come across this issue on upgrading my server to 12.04.2

Well, the symptoms may be the same, but the cause probably is not the same.

Prior to Ubuntu 12.04 the resolvconf package was only in the "universe" component and furthermore had not worked properly since Ubuntu transitioned to Upstart. The people who participated in this thread earlier (in 2011 and early 2012) either didn't have the resolvconf package installed, or were hitting the aforementioned Upstart-related bug, or both.

Anyone running Ubuntu prior to 12.04 is advised not to run resolvconf unless they have a special need for it. Anyone running Ubuntu 12.04 or later is advised to keep resolvconf installed under all circumstances (even if a static /etc/resolv.conf file is desired).

> 
There was a conflict with /etc/resolv.conf not being a symlink which meant nothing was getting generated from my (correct) /etc/resolvconf/ files.

The solution:
```
sudo rm /etc/resolv.conf
sudo dpkg-reconfigure resolvconf

```

Hope this helps.

Yes, that is a good way to restore the symbolic link at /etc/resolv.conf.

See bug #1000244 ([https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)) especially comment #82 ([https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244/comments/82)) for a summary of reasons why /etc/resolv.conf may have disappeared.

---

