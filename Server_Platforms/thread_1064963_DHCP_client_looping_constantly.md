---
title: "DHCP client looping constantly"
date: 2009-02-09
forum: Server Platforms
---

### Post by redmage123 on 2009-02-09
Hello all,

i've got two laptops, one running Intrepid that will serve as 
a DHCP/PXEboot server.  I have another laptop running as the boot client. 

For some reason, when the client powers up and does a net boot via PXE, 
it constantly requests and then release a DHCP address from the server. 

The syslog file looks like:


Feb  9 16:33:33 xvarix dhcpd: DHCPDISCOVER from 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:34 xvarix dhcpd: DHCPOFFER on 192.9.200.10 to 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:38 xvarix dhcpd: DHCPREQUEST for 192.9.200.10 (192.9.200.1) from 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:38 xvarix dhcpd: DHCPACK on 192.9.200.10 to 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:40 xvarix dhcpd: DHCPRELEASE of 0.0.0.0 from 00:22:64:67:e7:c0 via eth0 (not found)
Feb  9 16:33:40 xvarix dhcpd: DHCPDISCOVER from 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:40 xvarix dhcpd: DHCPOFFER on 192.9.200.10 to 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:44 xvarix dhcpd: DHCPREQUEST for 192.9.200.10 (192.9.200.1) from 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:44 xvarix dhcpd: DHCPACK on 192.9.200.10 to 00:22:64:67:e7:c0 via eth0
Feb  9 16:33:50 xvarix dhcpd: DHCPRELEASE of 0.0.0.0 from 00:22:64:67:e7:c0 via eth0 (not found)


over, and over, and over, etc. 

The dhcpd.conf file is dirt simple: 

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#
    option routers 192.9.200.254;

subnet 192.9.200.0 netmask 255.255.255.0 {
    ping-check = 1;
    filename = "pxelinux.0";
    range 192.9.200.10 192.9.200.253;
    next-server 192.9.200.1;
}


Why is the client releasing the address constantly?  The dhcpd.leases
file shows: 

# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-V3.1.1

lease 192.9.200.10 {
  starts 1 2009/02/09 16:58:47;
  ends 2 2009/02/10 04:58:47;
  tstp 2 2009/02/10 04:58:47;
  cltt 1 2009/02/09 16:58:47;
  binding state active;
  next binding state free;
  hardware ethernet 00:22:64:67:e7:c0;
}

So I know that the server is giving the lease to the client, but for some
reason the client is rejecting it.  

This is driving me nuts.  I don't know what else to do to debug this problem.  Any assistance gratefully accepted. 

Thanks,

Braun Brelin

---

### Post by koenn on 2009-02-09
technically, the dhcp client isn't rejecting the lease, it accepts it (re the REQUEST and ACK exchange in the log), but then seems to release it although it hasn't expired. 

given that you're trying to do a PXE boot, and the "next server" is the same as the dhcp server (your dhcp server is 192.9.200.1, right ?), one would expect syslog to show some tftp activity after the dhcp lease has been given out - something like "TFTP: request from 192.9.200.10; TFTP serving file pxelinux.0 to 192.9.200.10". So either your syslog snippet is incomplete, or you should configure tftp to log more debug info, or you don't have tftp working at all. 

Assuming the latter, its conceivable that the pxe boot client fails to retrieve the pxe boot file, decides it's not going to run anything anyway, and thus gives up its address lease. I don't know if that's the expected behaviour, but it may be worth a closer look.


that, or there is something (else) in your dhcp server or client config that makes the lease invalid almost the instant it has been acquired. I don't see anything that points in that direction, except maybe the presence of the tstp and cltt properties in the lease : I don't know if they're expected if you don't have a dhcp fail-over set up; your dhcpd.conf doesn't show that you have.
I don't have a ISC dhcpd close by to check this, so you might want to look in to it yourself (or someone else could check this).

Lastly, your IP addresses are unusual, but I doubt that that could be the source of your problem.

---

### Post by redroad55 on 2009-02-09
Is there something in bios that needs to be set .. What alptops are we talking about ? Post back

---

### Post by HermanAB on 2009-02-09
You need to add "authoritative" to your DHCP Server configuration.

Cheers,

Herman

---

