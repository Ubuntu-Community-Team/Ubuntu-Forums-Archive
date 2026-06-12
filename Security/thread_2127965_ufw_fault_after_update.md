---
title: "ufw fault after update"
date: 2013-03-21
forum: Security
---

### Post by M0pax on 2013-03-21
Hi i have ufw enabled on server 12.10 this list was working ok no access to ssh port 22 and port 10000 from outside my network

443                        ALLOW IN    Anywhere
80/tcp                     ALLOW IN    Anywhere
Anywhere                   ALLOW IN    192.168.1.0/24
22                         ALLOW IN    192.168.1.0/24
10000                      ALLOW IN    192.168.1.0/24
21                         ALLOW IN    192.168.1.0/24
443                        ALLOW IN    Anywhere (v6)
80/tcp                     ALLOW IN    Anywhere (v6)


Did update the other day 3 files now the access is ignored i can log in to ssh and port 22 from outside my network, very strange i have rebooted the ufw and the server as well still the same

---

### Post by Ms. Daisy on 2013-03-23
Is the default set to deny all in?

---

### Post by M0pax on 2013-03-24
Hi thanks for the info I am new to this what do you mean

---

### Post by Ms. Daisy on 2013-03-25
See [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall) for a good guide in setting up a firewall on Ubuntu.

---

### Post by M0pax on 2013-03-25
Hi Ms. Daisy thanks for the help, I have sorted it now ufw reset and re put in ports all working now no access from out side to https and ssh  thanks again

---

