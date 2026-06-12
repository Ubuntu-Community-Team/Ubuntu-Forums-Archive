---
title: "OpenVPN auto start"
date: 2009-03-02
forum: Server Platforms
---

### Post by boondocks on 2009-03-02
This is a Ubuntu 7.10 system.
I need to run OpenVPN with 5 clients using Symmetric Key Encryption.

The configuration files for the OpenVPN server are:
[INDENT]/home/myself/stuff/openVPN_Server_Config_for_Client**1**.conf
/home/myself/stuff/openVPN_Server_Config_for_Client**2**.conf
/home/myself/stuff/openVPN_Server_Config_for_Client**3**.conf
/home/myself/stuff/openVPN_Server_Config_for_Client**4**.conf
/home/myself/stuff/openVPN_Server_Config_for_Client**5**.conf
[/INDENT]
How do I configure OpenVPN to run automatically on system startup with these 5 configuration files?

---

### Post by matey3 on 2009-03-03
I am no ex[pert at all, but I would use either crontab or put all these command lines in one file, chmod it to +x and then run it either at startup or a cron job.
I know there is a better way using init.d or some thing like that but like I said I am new to this.so..
good luck!

---

### Post by koenn on 2009-03-03
the debian openvpn package comes with a startup script (init) that looks in /etc/openvpn and starts any vpn it finds configured there. If the ubuntu packagers didn't change that, it should work as is.

---

### Post by micklock on 2010-07-15
Original question:
##That is right (at least on XUbuntu 10.04), it automatically reads and start VPNs you have a .conf file in /etc/openvpn.
##Is there a way to switch some of them off? 
##Any experience with the update-resolve-conf script?
##Thanks.

OK, I just found it. You can specify which openVPNs autostart in */etc/default/openvpn* file. It is self explanatory, read comments in the file.

---

