---
title: "Snort newbie"
date: 2011-10-26
forum: Security
---

### Post by vishnu.reddy@datumsoftwar on 2011-10-26
Hi All, 
 
Basically i am new to Ubuntu 8.04 and Snort 2.6.8. I have installed Snort, Base, Mysql. I am able to get to the url for base. I started snort using the command "snort -u snort -c /etc/snort/snort.conf" I am doing scans accross this system using nmap. But I am not able to see any listing in the BASE. Please correct me if i am doing something wrong? Are do i need to mention some rules in the snort.conf in order to capture some data? 
Thanks,
Vishnu

---

### Post by Dangertux on 2011-10-26
> **vishnu.reddy@datumsoftwar said:**
> Hi All, 
 
Basically i am new to Ubuntu 8.04 and Snort 2.6.8. I have installed Snort, Base, Mysql. I am able to get to the url for base. I started snort using the command "snort -u snort -c /etc/snort/snort.conf" I am doing scans accross this system using nmap. But I am not able to see any listing in the BASE. Please correct me if i am doing something wrong? Are do i need to mention some rules in the snort.conf in order to capture some data? 
Thanks,
Vishnu

You need to make sure your database is configured properly, this is the most common reason base doesn't show anything. You may wish to read this documentation.

[https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)

---

