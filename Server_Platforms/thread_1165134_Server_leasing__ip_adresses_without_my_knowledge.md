---
title: "Server leasing  ip adresses without my knowledge??"
date: 2009-05-20
forum: Server Platforms
---

### Post by aldav on 2009-05-20
Hello, I'm relatively newbie in Linux, but my company wants to migrate in some future to open source platforms. In order to do so, I installed VMWare ESXi 3.5 Server, so I can manage a Linux distro in a virtual machine, learning all I can, while the Windows Server is still running in another virtual. That way, I can begin to learn and the old services may still run. Anyway, I decided to install Ubuntu Server 8.10 (in the virtual machine). During the install process, the setup prompted me to select which servers I wanted to install. I decided to install them all, except the Virtual Machine Server. There was no DHCP server available. After I finished installing Ubuntu Server, everything went OK, but after a few hours, some people started complaining about connection issues. As it appears to be, someone is acting as a DHCP server in my network and the most likely suspect is my new Ubuntu Server. During the installation process I recall I selected DNS Server. Is it possible that my installation is acting as a rogue dhcp server? How can I detect it? If so, how can I remove that behavior without reinstalling the whole system again? Thanks in advance.

---

### Post by Cheesemill on 2009-05-20
You can tell if there is a DHCP server running on your Ubuntu box by doing
```
ps ax | grep dhcpd
```

This will tell you if there are any DHCP server processes running.

Cheesemill

---

### Post by beckols on 2009-05-20
snip

---

### Post by aldav on 2009-05-20
yes "ps ax | grep dhcpd" returned the following:

4616 tty1   S+    0:00  grep dhcp

If I'm correct that refers to the command I just execute, right?
Nothing else came up.

---

### Post by aldav on 2009-05-21
Well, it turned out it wasn't my server the one leasing IP Addresses, thank god :). Any way, I still want to know if it is possible that by installing a DNS server, a DHCP server is installed also. And I still want to know how to uninstall the DNS server. Anyone?

---

### Post by Vegan on 2009-05-21
You do not generally need a DNS service unless you are running a large shop.

If you are then bind9 is the current favorite tool.

DHCP is the default for Ubuntu, static addresses are manually setup.

---

### Post by aldav on 2009-05-21
Yes, I'm aware of the needs of a DNS Server. The first post of the thread explains what happened to me and what I needed, but I'll repeat it anyway.

I installed Ubuntu Server 8.10 32 bits. During the installation process, I selected all the available servers except the virtual machine server. That included DNS server. (I know I shouldn't have done that, but I did it, I also mentioned I was a newbie in linux). Now, all I want to do is uninstall the DNS server. In windows server it is extremely simple, but in linux I'm just lost. So the question still remains the same:
How to uninstall DNS server from Ubuntu Server Edition 8.10?

---

### Post by bab1 on 2009-05-21
> **aldav said:**
> ... So the question still remains the same:
How to uninstall DNS server from Ubuntu Server Edition 8.10?

From the terminal -- ```
sudo apt-get purge bind9
```

This assumes that it is BIND9 that you have installed.

---

### Post by aldav on 2009-05-21
After executing "sudo apt-get purge bind9" this came up:


```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  bind9*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 37423 files and directories currently installed.)
Removing bind9 ...
Purging configuration files for bind9 ...
dpkg - warning: while removing bind9, directory `/var/run/bind/run' not empty so not removed.
dpkg - warning: while removing bind9, directory `/var/run/bind' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for ufw ...
```

Does it mean DNS server was succesfully removed or not? How do I check it?

---

### Post by bab1 on 2009-05-21
It has been removed.  I use a utility called ***locate*** to look for relevant```

``` files.  You have to install it as it is not in the base setup.  The 2 lines ```
dpkg - warning: while removing bind9, directory `/var/run/bind/run' not empty so not removed.
dpkg - warning: while removing bind9, directory `/var/run/bind' not empty so not removed.

```

are just directories and could be addressed if you are really picky.  If you leave them no harm will come from them being there.

---

### Post by aldav on 2009-05-21
Ok, thanks then. I'm assuming now that DNS server is uninstalled. Thanks for all the help

---

