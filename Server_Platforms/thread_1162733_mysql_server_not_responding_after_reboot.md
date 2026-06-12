---
title: "mysql server not responding after reboot"
date: 2009-05-18
forum: Server Platforms
---

### Post by harmony on 2009-05-18
Hi all, I have my wordpress blog setup on local server, It works great until I reboot then I get the data base not found error when I try to visit my site. When I try to log in to mysql with mysql -u root -p it fails, unless I go into my.cnf and change the bind address back to localhost, from the ip address from the computer. So basically mysql won't start unless I have the bind address set to localhost in /etc/mysql/my.cnf. Is there a work around for this? Im sure there is, but I don't know what it is. Anyone got any suggestions? Thanks):P

---

### Post by justatemptest on 2009-05-18
Are you using DHCP on the other interface? Is that interface up before MySQL is loaded?

---

### Post by harmony on 2009-05-18
> **justatemptest said:**
> Are you using DHCP on the other interface? Is that interface up before MySQL is loaded?
Yes I have the darn dhcp on, so if I set a static ip address that might fix the problem. Should I set the ip address in /etc/hosts, or where?

---

### Post by harmony on 2009-05-18
So I have my wordpress blog working now by setting a static ip address, and I also added my computer ip address into /etc/hosts, so all seems good now.

---

