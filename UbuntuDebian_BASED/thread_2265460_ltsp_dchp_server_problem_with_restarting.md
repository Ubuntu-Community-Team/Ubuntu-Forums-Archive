---
title: "ltsp dchp server problem with restarting"
date: 2015-02-15
forum: Ubuntu/Debian BASED
---

### Post by stevecook on 2015-02-15
I have implemented an LTSP server on ubuntu 14. The problem is with the dhcp server being ready for the ltsp client at client bootup. The is another problem with the tftpd server, but I can resolve that fairly trivially.

Basically, I have outlined the problems below along with how I curerently work around them in a messy kind of way;

(1) the dhcpd server

The dhcpd server must be already running to be able to hand out addresses to an LTSP client. However, since ubuntu 13 onwards, it seems that the dhcpd server can only start once an active connection is already physically established. That is to say, it needs to be already started when an ltsp client is booted up. However, if the ltsp client is the only other computer connected to the ltsp host, then the dhcp server wont be started and ready for it.

If I do a dhcp server restart command (sudo /etc/init.d/isc-dhcp-server restart) on the ltsp host before any physical connection are already established, then it fails. If I try and restart the dhcp server while the ltsp client is booting, then sometimes the restart fails and sometimes it does not. The ONLY WAY I have found to get the dhcp server started and ready for the LTSP client is to have previously connected a PC with the eth card with a full linux installation to the host machine. At which point, if I then do the dhcp server restart command, it will start. At which point, I can then shut down the other PC and boot back on the network. At which point, it will get the necessary addresses from the dhcpd server on the host. Which is where the next problem arises:

2) the tftpd server

I don't know what the server does exactly, but I do know it needs to be ruunning otherwise the clioent will report a tftp timeout error when booting. The tftp server should be already up and running on the host machine as a consequence of starting at boot time. but it isn't. I have resolved this by simply running the server restart command and it loads without error. The command is "sudo service tftpd-hpa restart". I will be sticking this command in a startup script and so this last problem should be trivially resolved.

So, in summary, to get my LTSP system running and clinets logging in unproblematically, I need to do the following:

1) fire up the host

2) restart the tftp server on the host

3) fire up a normal (non LTS) full-fat ubuntu client machine and have it connected to eth0 on the host

4) restart the dhcpd server on the host

5) reboot the client to the network

6), At which point the client will recieve addresses from the dhcpd server on the host and it will also not report a tftp timeout error. In other words, it will boot to LTSP.

Presumably, once there is at least one ltsp client up and running, then all other clients should boot up without any hitches.

The only real problem I now have remaining is getting the dhcpd server up and running and ready for the ltsp client in advance.

Anybody any suggestions?

Edit to add:

I should say, none of the above was ever a problem up to ubuntu 12.04 lts. So, this is definitely a problem with the dchpd server from ubuntu 13 onwards.

---

### Post by stevecook on 2015-02-15
Nobody?

---

