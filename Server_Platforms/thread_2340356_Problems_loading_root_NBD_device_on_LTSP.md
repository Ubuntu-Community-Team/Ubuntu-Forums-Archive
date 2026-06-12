---
title: "Problems loading root NBD device on LTSP"
date: 2016-10-17
forum: Server Platforms
---

### Post by dcroxton on 2016-10-17
I set up my 16.04 Xubuntu computer as an LTSP server.  I have booted a client from it successfully, but under two special circumstances:  (a) using a second NIC and ltsp-server-standalone; (b) using dnsmasq as a dhcp server.  When I set up dnsmasq as a dhcp proxy, the client always fails when it tries to mount the root filesystem with the message "ALERT! /dev/nbd0 does not exist." (Along with some other messages that disappear off the screen too fast to capture, but one of them says something like "unable to create socket, connection refused.)

I actually thought I had dnsmasq set up to run as a proxy dhcp server, but I found out differently when my wife's computer got an IP address from the wifi in the dnsmasq address range and couldn't connect to the internet.  So I adjusted the settings to make it a proxy, and now it doesn't work.  I wish I could remember the exact configuration changes I made.  The only one I know for sure was setting the line "dhcp-range=192.168.0.0,proxy" in ltsp-server-dnsmasq.conf and commenting out a dhcp-range line in dnsmasq.conf.  I can't see why either of those would affect nbd, but what do I know?

NBD does seem to be working in principle, because I can run "nbd-client localhost -N /opt/ltsp/i386 /dev/nbd0" and I get back the size, bs, and sz values.  I don't know what I need to do to let the client connect, or how I could have broken it by changing the dns settings.

Derek

UPDATE: I managed to get Linux up on another computer and tried to run the nbd-client command.  It succeeded.  There is a log message on the server that says "Can't open authorization file /etc/ltsp/nbd-server.allow (No such file or directory)," I don't know if that is relevant.  I assume there must be some problem with my ltsp setup, but I have no idea what I need to do to configure nbd.

---

