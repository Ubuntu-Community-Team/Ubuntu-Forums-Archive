---
title: "messed up networking interfaces file"
date: 2010-12-25
forum: Server Platforms
---

### Post by -C- on 2010-12-25
For my router I need to change Ubuntu server from DHCP to static IP. So to do this I entered:

```
sudo vi /etc/network/interfaces
```

...and pushed the wrong buttons and exited the session suddenly by mistake. After learning how to use the vi editor I went back but I got a notice that the the last session didn't close properly and that a "swap" file had been created. Anyway, I entered my static IP info, saved the file, and attempted to restart with:

```
sudo /etc/init.d/networking restart
```

Restart failed and I got a notice that I should delete the /etc/network/interfaces.swp file so I did. Tried to restart again and, didn't get the .swp file conflict message this time, but failed again - this time I got the following message:

```
 * Reconfiguring network interfaces...
/etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
```

I'm not sure if it can't be read because I messed up the file format or if the information I entered is wrong. Here's what the file looks like in the vi editor:

```
nterfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.65
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
~
~
~
~
~
~
~
                                                              16,1          All

```

So could someone please tell me what the "misplaced option" is referring to by looking at the above? Is there anything I can do?

Thanks in advance.

---

### Post by aceofspades686 on 2010-12-25
This looks the same as my interfaces file except this:
```

nterfaces

```
on the first line.  Maybe try removing that?

---

### Post by -C- on 2010-12-25
For some reason I thought that bit was there before I started pushing buttons...apparently not because it works after removing it.

Thank you!

---

### Post by not12listen on 2011-11-30
i am having the exact same problem.

here is what my 'interfaces' file looks like:

-----

# This file describes the network interfaces available on your system
and how to activate them. For more information, see Interfaces(5).

# The Loopback network interface
auto lo
iface lo loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.x.x
netmask 255.255.255.0
gateway 10.10.x.x

auto eth1
iface eth1 inet static
address 10.10.x.x
netmask 255.255.255.0

-----

in the above, i have replaced the last 2 octet numbers with x's for the address and gateway.  i am 100% certain that they do not conflict.

any help is appreciated.

thanks!

---

### Post by spynappels on 2011-12-01
You should really start your own thread for this, but....

What error messages are you getting?

There is little or no point putting XXs in instead of the actual numbers because this is on your LAN and there is nothing to identify you to the wider world, including detail may help to diagnose the issue.

---

### Post by kums3570 on 2012-01-04
> **not12listen said:**
> i am having the exact same problem.

here is what my 'interfaces' file looks like:

-----

# This file describes the network interfaces available on your system
and how to activate them. For more information, see Interfaces(5).

# The Loopback network interface
auto lo
iface lo loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.x.x
netmask 255.255.255.0
gateway 10.10.x.x

auto eth1
iface eth1 inet static
address 10.10.x.x
netmask 255.255.255.0

-----

in the above, i have replaced the last 2 octet numbers with x's for the address and gateway.  i am 100% certain that they do not conflict.

any help is appreciated.

thanks!

Please Put a '#'  at second line
Your Problem gets resolve

---

