---
title: "can't have a local ip adress ubuntu server"
date: 2015-10-15
forum: Server Platforms
---

### Post by marwen-somrani on 2015-10-15
hello, i installed ubuntu server for the first time on virtualbox on my pc running on windows.to test connectivity between the two systems :
windows: 192.168.1.3 (LAN)
ubuntu server: 10.0.2.15

when the ping: ubuntu server ping to windows machine but not vice versa

how to solve this type of problem
thank you

---

### Post by marwen-somrani on 2015-10-15
problem solved with editing the file [COLOR=#333333][FONT=UbuntuMono]/etc/dhcp/dhcpd.conf and writing 
[/FONT][/COLOR]subnet 192.168.1.0 netmask 255.255.255.0 {
[FONT=inherit][/FONT]range 192.168.1.10 192.168.1.100;
[FONT=inherit][/FONT]}

---

