---
title: "unable to boot."
date: 2013-04-28
forum: Server Platforms
---

### Post by gh0ti on 2013-04-28
Hi  I am unable to boot past after a reboot  of  the system.

stopping set sysctls from /etc/sysctl.conf

any help how to fix this wthout a  complet reinstall

---

### Post by gordintoronto on 2013-04-28
What version of Ubuntu? You select "restart," then what happens?

I have no idea what this means: "stopping set sysctls from /etc/sysctl.conf".

---

### Post by varunendra on 2013-04-29
For the reference, this is my sysctl.conf file (Ubuntu 12.04, 64 bit) :
> #
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


Boot with a live cd/usb, mount your installation partition, browse to the file (/etc/sysctl.conf), open and match it with the contents above. Maybe some critical setting might have messed up. Or, if it looks fine, maybe it is the last thing that finishes successfully and it is actually the next thing in boot process that is messed up.

**EDIT:** It looks the file has all the settings commented out by default, so maybe you 'included' or 'uncommented' some setting that the system doesn't like...

---

### Post by MKSam on 2013-04-29
Hello,
My question is, are you trying Dual boot in your system. If yes then with which operating system, because this error often occur when you try dual boot, and the other operating system doesn't support dual booting. Try to re install it again and then error will be removed accept that there's no way. 
MK Sam

---

