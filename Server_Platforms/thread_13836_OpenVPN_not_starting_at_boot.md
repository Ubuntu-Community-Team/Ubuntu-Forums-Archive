---
title: "OpenVPN not starting at boot"
date: 2005-02-03
forum: Server Platforms
---

### Post by cultpenguin on 2005-02-03
Hi 
I use OpenVPN (has been extremely relaible VPN connection for me for years), but I cannot make it start at boot time in Ubuntu

I notice ubuntu start in runlevel 2, so I create a link to tge openvpn init script :

 ln -s /etc/init.d/openvpn /etc/rc2.d/S19openvpn

However openvpn never starts. I need it to mount some NFS drive.

/etc/init.d/openvpn start works fine.

What do I do wrong ?

- Thomas

---

### Post by alastair on 2005-02-03
NFS drive? Seems an odd requirement. I guess this might mean using the right "S" level to come after NFS/portmap mounts remote filesystems?

---

### Post by cultpenguin on 2005-02-04
It is really not that odd to mount andNFS drive :) But, mounting NFS is not part of the problem. 

The problem is that the INIT script for openvpn does not start at boot time even though it is specified in /etc/rc2.d with a linkt to /etc/init.d/openvpn.

running from the commandline :
/etc/init.d/openvp stop
/etc/init.d/openvp start
/etc/init.d/openvp restart

works just fine....

Is there any log file I could check for errors ?

Thanx - Thomas

---

### Post by alastair on 2005-02-05
Firstly - I should say that I have not yet installed or properly used Ubutu. I have also never used Debian.

But - log files can be found in /var/log/

Look for - syslog , messages , dmesg and, perhaps, any boot.log.

I would try removing the link you make and remake it - starting it later in the boot cycle e.g.

 ln -s /etc/init.d/openvpn /etc/rc2.d/S99openvpn

---

### Post by cultpenguin on 2005-02-05
Hi. I looked through the log files, and I found that openvpn fails because the tun module is not properly loaded..

I do have a line in /etc/modules.conf :
-
alias char-major-10-200 tun
-
which should enable tun to be loaded, but in /var/log/syslog i get the following messaged from OpenVPN
-
Feb  5 22:14:14 localhost ovpn-home_server[4641]: OpenVPN 1.6.0 i386-pc-linux-gnu [SSL] [LZO] [PTHREAD] built on Aug 13 2004
Feb  5 22:14:14 localhost ovpn-home_server[4641]: LZO compression initialized
Feb  5 22:14:14 localhost ovpn-home_server[4641]: Note: Cannot open TUN/TAP dev /dev/net/tun: No such file or directory (errno=2)
Feb  5 22:14:14 localhost ovpn-home_server[4641]: Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Feb  5 22:14:14 localhost ovpn-home_server[4641]: Cannot open TUN/TAP dev /dev/tun1: No such file or directory (errno=2)
-

I do have 'modprobe tun' in my openvpn initscript.

Also, When I run the initscript as root when the computer comes up, OpenVPN starts without fuss..


Anybody know how to make sure that tun/tap devices can be created and avaiable at boot time ?

---

### Post by alastair on 2005-02-05
This is a shot in the dark - I use OpenVPN as well but have no "alias" line in /etc/modules.conf (I'm using Fedora Core 2 anyway).

Maybe this is "udev" related?

What I would try :

a) make sure OpenVPN starts near the end of the boto cycle (i.e. S99)
b) add the "tun" module to the list of modules loaded at boot (I think there's a file to list these on Debian - /etc/modules?) 
c) perhaps put a "sleep 3" (or something) after the "modprobe tun" in the init script?

Worth a try.

---

### Post by cultpenguin on 2005-02-06
sleep 3 
did the trick :D  
Thanx a lot for the help  =D> 
- Thomas

---

