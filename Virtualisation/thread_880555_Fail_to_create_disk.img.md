---
title: "Fail to create disk.img"
date: 2008-08-05
forum: Virtualisation
---

### Post by satimis on 2008-08-05
Hi folks,


Ubuntu 8.04 server amd64 - host - headless (w/o X packages)
Ubuntu 6.06 server amd64 - guest - headless (w/o X packages)
KVM


Previously I ran;


# qemu-img create -f qcow2 disk.img 10G

then

# kvm -hda disk.img -cdrom /dev/scd0 -m 512 -boot d

to create a working disk.img.  It works on the VM.


But I couldn't create direct on running;

# kvm -hda disk.img -cdrom /dev/scd0 -m 512 -boot d


must be in 2 steps.



Now I tried creating another disk.img but the above steps did not work.


# qemu-img create -f qcow2 ubuntu6.06_080805.img 10G```

Formatting 'ubuntu6.06_080805.img', fmt=qcow2, size=10485760 kB

```


# kvm -hdb ubuntu6.06_080805.img -cdrom /dev/scd0 -m 512 -boot d -smp 2```

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15) 
(*) Direct/Memcpy: Using libc memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Could not initialize SDL - exiting

```


without "-smp 2" still the same.


I don't know what mistake I have committed.  I didn't done anything on the host except running apt-get update/upgrade.  Please advise.


TIA


Edit:-

I found the cause.  It was iptables.  After flushing all rules, the problem gone.


Xterm-1
# kvm -hdb ubuntu6.06_080805.img -cdrom /dev/scd0 -m 512 -boot d -smp 2 -vnc :9
(starting)


Xterm-2
$ vncviewer 192.168.0.110:9

viewer popup and installation began.  After finish it reboots.


However on Xterm-1
it popup ;-```


kvm_run: failed entry, reason 65535
kvm_run returned -8

```


Xterm-1
Ran
# kvm ubuntu6.06_080805.img -vnc :0


Xterm-2
$ vncviewer 192.168.0.110:0

viewer starts displaying;```

.....
Booting the kernel
.....
Alert! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
#

```

Any mistake committed?  Please advice.  TIA

Remark:  AMD dual core CPU


$ cat /etc/rc.local```

# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# allow all VMware MUI HTTP connections in from anywhere
iptables -A INPUT -p tcp --dport 8222 -j ACCEPT

# allow all VMware MUI HTTPS connections in from anywhere
iptables -A INPUT -p tcp --dport 8333 -j ACCEPT

# allow all VMware Authorization Daemon connections in from anywhere
iptables -A INPUT -p tcp --dport 902 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 25 -j ACCEPT 
iptables -A INPUT -p tcp --dport 110 -j ACCEPT


# Allow ssh from workstation public IP
iptables -A INPUT -s 192.168.0.36 -p tcp --dport 22 -j ACCEPT


# Allow ssh from workstation public IP
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG



# OUTPUT

# Set the default policy to drop
#iptables -P OUTPUT DROP
iptables -P OUTPUT ACCEPT

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```


What rule shall I add allowing X forwarding?  Shall I do anything on hosts.allow and hosts.deny?  TIA



B.R.
satimis

---

### Post by PCessna on 2008-08-05
Queme(or whatever it is) is a mess, May I recommend trying VirtualBox, or Virtual PC for Windows, Two real, free, virtual machine that will do what you want without all that stupid trouble

---

### Post by satimis on 2008-08-05
> **PCessna said:**
> Queme(or whatever it is) is a mess, May I recommend trying VirtualBox, or Virtual PC for Windows, Two real, free, virtual machine that will do what you want without all that stupid trouble
Hi PCessna,


Thanks for your advice.


I have tried VMWare and KVM both encountering trouble on networking.  On VMWare guest can connect Internet but Internet can't get into guest/VMWare.  On KVM/QEMU I also encounter problem on networking.  On guest I can run update and upgrade on REPO but I can't ping Internet there.  I found tons of document on googling.  Seemingly none of them can help me out.  The server is headless.  Lastly disregarding the problem on ping I'll install Zimbra on the guest to see what will happen to finish my test on KVM.  It is a nice project easily creating disk.img.


I'm learning Virtualization.  Virtural box/VServer are also included on my program.  


B.R.
satimis

---

