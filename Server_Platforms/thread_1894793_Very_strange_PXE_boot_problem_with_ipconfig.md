---
title: "Very strange PXE boot problem with ipconfig"
date: 2011-12-13
forum: Server Platforms
---

### Post by Jonathan L on 2011-12-13
Dear All

I'm stuck on a building site in the snow and need some help!

I'm having some trouble with debugging a very strange PXE booting problem: all comes down to the behaviour of "ipconfig" inside the Live CD boot initrd filesystem.  Anybody know documentation or source for the file /bin/ipconfig inside initrd.lz on the Live CD? 

It's failing (silent hanging) when we have some UDP broadcasts on the network: when we disconnect the broadcasting item, it boots fine.  Terribly confusing.

The file is /bin/ipconfig inside /casper/initrd.lz on 10.04.3 Desktop LiveCD ISO.

29f52987aad59fbb6c31838695913f73  bin/ipconfig
d169011c359121f3a75085f47ea0e90b  /exports/ubuntu-10.04.3-desktop-i386/casper/initrd.lz
f63028da38308d917cd1460e14fb8540  /cdroms/ubuntu-10.04.3-desktop-i386.iso

Thanks for any help or pointers or workarounds.  I'm suspecting something to do with DHCP or similar, but am not sure at all.

Jonathan

---

### Post by Jonathan L on 2011-12-13
Hi

It appears this is the klibc utils version of ipconfig.

Not sure of the versions, but the main page appears to be: [http://packages.debian.org//klibc-utils](http://packages.debian.org//klibc-utils)

Inside the source for that page, there is a README:

```
BOOTP/DHCP client for klibc
---------------------------

Usage:

ipconfig [-c proto] [-d interface] [-i identifier]
     [-n] [-p port] [-t timeout] [interface ...]

-c proto    Use PROTO as the configuration protocol for all
        interfaces, unless overridden by specific interfaces.
-d interface    Either the name of an interface, or a long spec.
-i identifier    DHCP vendor class identifier.  The default is
        "Linux ipconfig".
-n        Do nothing - just print the configuration that would
        be performed.
-p port        Send bootp/dhcp broadcasts from PORT, to PORT - 1.
-t timeout    Give up on all unconfigured interfaces after TIMEOUT secs.

You can configure multiple interfaces by passing multiple interface
specs on the command line, or by using the special interface name
"all".  If you're autoconfiguring any interfaces, ipconfig will wait
until either all such interfaces have been configured, or the timeout
passes.

PROTO can be one of the following, which selects the autoconfiguration
protocol to use:

not specified    use all protocols (the default)
dhcp        use bootp and dhcp
bootp        use bootp only
rarp        use rarp (not currently supported)
none        no autoconfiguration - either static config, or none at all

An interface spec can be either short form, which is just the name of
an interface (eth0 or whatever), or long form.  The long form consists
of up to seven elements, separated by colons:

<client-ip>:<server-ip>:<gw-ip>:<netmask>:<hostname>:<device>:<autoconf>

  <client-ip>    IP address of the client. If empty, the address will
                either be determined by RARP/BOOTP/DHCP. What protocol
                is used de- pends on the <autoconf> parameter. If this
                parameter is not empty, autoconf will be used.

  <server-ip>   IP address of the NFS server. If RARP is used to
                determine the client address and this parameter is NOT
                empty only replies from the specified server are
                accepted. To use different RARP and NFS server,
                specify your RARP server here (or leave it blank), and
                specify your NFS server in the `nfsroot' parameter
                (see above). If this entry is blank the address of the
                server is used which answered the RARP/BOOTP/DHCP
                request.

  <gw-ip>       IP address of a gateway if the server is on a different
                subnet. If this entry is empty no gateway is used and the
                server is assumed to be on the local network, unless a
                value has been received by BOOTP/DHCP.

  <netmask>     Netmask for local network interface. If this is empty,
                the netmask is derived from the client IP address assuming
                classful addressing, unless overridden in BOOTP/DHCP reply.

  <hostname>    Name of the client. If empty, the client IP address is
                used in ASCII notation, or the value received by
                BOOTP/DHCP.

  <device>      Name of network device to use. If this is empty, all
                devices are used for RARP/BOOTP/DHCP requests, and the
                first one we receive a reply on is configured. If you
                have only one device, you can safely leave this blank.

  <autoconf>    Method to use for autoconfiguration. If this is either
                'rarp', 'bootp', or 'dhcp' the specified protocol is
                used.  If the value is 'both', 'all' or empty, all
                protocols are used.  'off', 'static' or 'none' means
                no autoconfiguration.

IP addresses and netmasks must be either absent (defaulting to zero)
or presented in dotted-quad notation.

An interface spec can be prefixed with either "ip=", "nfsaddrs=", both
of which are ignored.  These (along with the ugliness of the long
form) are present for compatibility with the in-kernel ipconfig code
from 2.4 and earlier kernels.

Here are a few examples of valid ipconfig command lines.

Enable the loopback interface:
    ipconfig 127.0.0.1:::::lo:none

Try to configure eth0 using bootp for up to 30 seconds:
    ipconfig -t 30 -c bootp eth0

Configure eth0 and eth1 using dhcp or bootp, and eth2 statically:
    ipconfig -c any eth0 eth1 192.168.1.1:::::eth2:none

--

From Russell's original README, and still true:

The code in main.c is yucky imho.  Needs cleaning.

--
Russell King (2002/10/22)
Bryan O'Sullivan (2003/04/29)
```


I did some experiments and it's definitely the dhcp or bootp failing.

I've worked around it horribly for the moment by using static configuration
    ```
#ipconfig -c bootp ${DEVICE} /tmp/net-${DEVICE}.conf | tee /netboot.config
    ipconfig -c bootp 192.168.1.64:192.168.1.32:255.255.255.0:::${DEVICE}:none /tmp/net-${DEVICE}.conf | tee /netboot.config
```

More later when I can find a good solutions.

Kind regards,
Jonathan

---

