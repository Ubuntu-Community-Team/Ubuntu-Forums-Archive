---
title: "lan testing"
date: 2013-08-20
forum: Server Platforms
---

### Post by salmendar on 2013-08-20
HI,
      I established a small testing server using Ubuntu 12.04 in my office for web testing and other server services. I also gave it a static ip on my router . i am new so i learn as i go on. now the prblem is that the have a static ip but no domain. when i want to test on lan it first asks for the username and password of the router. being the admin i can provide that but later on i get error 500 whenever i try a mysql based page. others are working fine. is there a way to solve this


:confused::confused::confused::confused::confused:

---

### Post by cartaysm on 2013-08-21
You need to setup your server to run on an internal port for example;
nano /etc/network/interfaces

auto eth0
#iface eth0 inet dhcp
        iface eth0 inet static
                address 192.168.1.110
                netmask 255.255.255.0
                gateway 192.168.1.1
                dns-nameservers 8.8.8.8 192.168.1.1

and then setup your router to point all port 80, 25, etc.. to port 192.168.1.110

Then in your browser if you type in the ip address you were assigned all web traffic will then be directed to port 192.168.1.110 and thus run on your server.

O yes and dont forget to setup apache2 to handle the traffic on that port;
nano /etc/apache2/sites-available

create a file of your hostname and virtualhost

---

### Post by salmendar on 2013-08-26
thank you and sorry for such a late reply

---

