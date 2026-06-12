---
title: "Ubuntu 11.04 DHCP server not starting"
date: 2011-09-11
forum: Server Platforms
---

### Post by talk2montu on 2011-09-11
Hello all,

I am new to Ubuntu (Linux), recently I have been trying to setup a DHCP server for my hotel and I cant seem to understand how to start the services. I have listed my config files and errors below. 

sudo apt-get install dhcp3-server
[sudo] password for montu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  isc-dhcp-server
Suggested packages:
  isc-dhcp-server-ldap
The following NEW packages will be installed:
  dhcp3-server isc-dhcp-server
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/435 kB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package isc-dhcp-server.
(Reading database ... 216713 files and directories currently installed.)
Unpacking isc-dhcp-server (from .../isc-dhcp-server_4.1.1-P1-15ubuntu9.1_amd64.deb) ...
Selecting previously deselected package dhcp3-server.
Unpacking dhcp3-server (from .../dhcp3-server_4.1.1-P1-15ubuntu9.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up isc-dhcp-server (4.1.1-P1-15ubuntu9.1) ...
[B]dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Can't open /etc/dhcp/dhcpd.conf: No such file or directory
invoke-rc.d: initscript isc-dhcp-server, action "start" failed.
Setting up dhcp3-server (4.1.1-P1-15ubuntu9.1) ...

DHCPD.CONF
[/B]# Sample /etc/dhcpd.conf
# Value Inn Motel DHCP server
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.5.69;
option routers 192.168.5.71;
option domain-name-servers Value.Inn.com;
option domain-name "inn.com";

subnet 192.168.5.0 netmask 255.255.255.0 {
range 192.168.5.50 192.168.5.70;
#range 192.168.1.150 192.168.1.200;
}
[B]
INTERFACES
[/B]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.5.69
netmask 255.255.255.0
network 192.168.5.71
broadcast 192.168.5.69
gateway 192.168.5.71[B]

DHCP3-SERVER[/B]
INTERFACES="eth0"
option netbios-name-servers 192.168.5.69[B]

Results when I try to start dhcp services

[/B]chkconfig dhcpd on dhcpd: unknown service
montu@VIRUS:~$ service dhcpd start
dhcpd: unrecognized service[B]

I have uninstalled and installed but no luck

[/B]montu@VIRUS:~$ sudo update-rc.d -f dhcp3-server remove
 Removing any system startup links for /etc/init.d/dhcp3-server ...
montu@VIRUS:~$ sudo update-rc.d dhcp3-server defaultsupdate-rc.d: /etc/init.d/dhcp3-server: file does not exist

---

### Post by hydruid on 2011-09-11
The error told you what was wrong "[B]Can't open /etc/dhcp/dhcpd.conf: No such file or directory"

[/B]Seems like you created/edited /etc/dhcpd.conf instead of /etc/dhcp/dhcpd.conf

---

### Post by talk2montu on 2011-09-11
What would be the best thing to do at this point?  Should I go ahead and un-install the service? How do I start from the scratch and install it correctly.  Previous instructions followed were from [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

---

### Post by Entilza on 2011-09-11
Check if /etc/dhcp.conf exists or /etc/dhcp/dhcpd.conf 

if it's in /etc/dhcp.conf then cp it to /etc/dhcp/dhcp.conf

---

### Post by talk2montu on 2011-09-11
I did check etc/dhcp.conf and in etc/dhcp/dhcpd.conf and none of the files exist.  What should I do next?  Remove the dhcp services?

---

### Post by Entilza on 2011-09-11
Does dhcp require you to create the file manually?

Try apt-get update before doing the install.

so remove it first

sudo apt-get purge dhcp3-server
sudo apt-get update
sudo apt-get install dhcp3-server

---

### Post by talk2montu on 2011-09-11
I am not sure... I have followed so many instructions and nothing seems to work.  I guess I dont understand how the filing system works in Ubuntu yet.  I have removed all of dhcp3 files and restarted the computer and installed it again and I keep missing the file stated above.  Do you think I have a bad install of ubuntu?

This is the latest that I have been encountering

/etc/init.d/dhcp3-server restart
bash: /etc/init.d/dhcp3-server: No such file or directory
montu@VIRUS:~$ sudo /etc/init.d/dhcp3-server restart
[sudo] password for montu: 
sudo: /etc/init.d/dhcp3-server: command not found
montu@VIRUS:~$ /etc/init.d/dhcp3-server restart
bash: /etc/init.d/dhcp3-server: No such file or directory
montu@VIRUS:~$

---

### Post by Entilza on 2011-09-11
Try apt-get update before doing the install.

so remove it first

sudo apt-get purge dhcp3-server
sudo apt-get update
sudo apt-get install dhcp3-server

---

### Post by talk2montu on 2011-09-11
It looks like those steps took care of that error that I kept getting when trying to re-install it.  

montu@VIRUS:~$ sudo apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5,898 B of archives.
After this operation, 69.6 kB of additional disk space will be used.
Selecting previously deselected package dhcp3-server.
(Reading database ... 216726 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_4.1.1-P1-15ubuntu9.1_all.deb) ...
Setting up dhcp3-server (4.1.1-P1-15ubuntu9.1) ...

So should I be able to follow any DHCP setup instructions from here?

---

### Post by Entilza on 2011-09-12
Great you should be good to go with dhcp configurations.

---

### Post by jimerman on 2011-12-15
I have had the same problem on 11.04, tried a purge and reinstall, but the purge apparently did not remove the config file I set up.  It still says dhcp3-service is not recognized.  Help, anyone?

---

