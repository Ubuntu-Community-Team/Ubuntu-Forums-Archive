---
title: "LTSP: Migrate to ltsp-pnp"
date: 2015-12-08
forum: Server Platforms
---

### Post by v4169sgr on 2015-12-08
Hello,

I am running 12.04 on a single NIC with ltsp-server-standalone, and am happily running 3 thin clients over it. My configuration has been running well for years, but there are some limitations because I need to run the ltsp version of dhcp on my server, and not on my Netgear N600 router:

* I cannot connect a locked down work laptop that needs dhcp to connect via VPN without disconnecting my clients
* I cannot use my wireless without disconnecting my clients

I've read this

[https://help.ubuntu.com/community/UbuntuLTSP/ltsp-pnp]("https://help.ubuntu.com/community/UbuntuLTSP/ltsp-pnp")

which sounds really attractive, but the problem for me is that the article assumes an otherwise clean install.

How do I go about migrating my ltsp to work with the router's dhcp, without being enormously disruptive to my clients? I'd also ideally like a way back to the previous config if this one doesn't work.

My lts.conf:

```
# This is the default lts.conf file for ltsp 5.
# For more information about valid options please see:
# /usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz
# in the client environment.
#
# Note that things like sound and local device support are
# auto-enabled if the corresponding packages are installed,
# there is no need to manually set these options anymore.
#
# [example]
# key=value
[default]
	LDM_DIRECTX=True
	LDM_SESSION="gnome-session --session=ubuntu-2d"
#	X_MODE_0 = 1024x768
#	XRANDR_DISABLE = True
#	XSERVER = i810
#	XRANDR_MODE_0 = 1024x768

```

My dhcp.conf

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.20 10.0.0.90;
    option domain-name "example.com";
    option domain-name-servers 10.0.0.1;
    option broadcast-address 10.10.0.255;
    option routers 10.0.0.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

Any pointers will be much appreciated - thanks ! :)

---

