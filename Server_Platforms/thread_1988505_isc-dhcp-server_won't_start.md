---
title: "isc-dhcp-server won't start"
date: 2012-05-27
forum: Server Platforms
---

### Post by atamakosi on 2012-05-27
Hi all,

I was upgrading our ltsp server to 12.04 from 11.10 in prep for installing shibboleth IdP.  ran the upgrade from terminal and everything went ok EXCEPT for isc-dhcp-server.  kept rejecting the upgrade with an error.  I removed the files from cache and got it to upgrade per a recommendation from another site.  however, the isc-dhcp-server service fails to start and remains in a stopped/waiting state.  i've used apt-get remove and install with no change.  purged it, no change.  checked the conf file and that hasn't changed from pre-upgrade.  

what this is causing on our network is our thin clients will not load properly any more.  I had them configured to boot via pxe to rdesktop for using our terminal servers.  it gets as far as the ubuntu loading screen on the thin clients but then just cuts out.  (the screen goes blank and nothing is to be seen. initially after the upgrade it would display 'initramfs' with a message about busybox that i've never seen before.)  also, trying to remote in using xrdp doesn't work correctly now either, only displays partial screen.  this might be related to the thin client rdesktop boot?  So i'll be back with technical info once i get it off the server...

thanks for any help.  we are a tiny school and ltsp really helps us make use of our old decrepit machines.  right now they are all down until this can be resolved.  I'm really afraid I might have to scrap the entire server and reinstall to correct this.

---

### Post by atamakosi on 2012-05-27
ltsp/dhcpd.conf

authoritative;

subnet 172.16.12.0 netmask 255.255.255.0 {
   range 172.16.12.20 172.16.12.250;
   option domain-name "SCHOOLDOMAIN";
   option domain-name-servers 172.16.0.1, 172.16.0.2;
   option broadcast-address 172.16.0.254;
   option routers 172.16.0.1;
   option subnet-mask 255.255.0.0;
   option root-path "/opt/ltsp/i386";

/ltsp/i386/lts.conf

[default]
RDP_OPTIONS = "-f -a 16"
RDP_SERVER = 172.16.0.12
SCREEN_02 = "rdesktop -r"

/etc/network/intefaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.0.13
netmask 255.255.0.0
gateway 172.16.5.1

---

### Post by rabbadabb on 2012-06-18
Hi!

Saw that the option subnetmask is not consistant with the rest of the subnet-masks. Typo?

Hope everything works if you change that.

Cheers
Olle

---

