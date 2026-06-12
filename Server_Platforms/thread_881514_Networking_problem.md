---
title: "Networking problem"
date: 2008-08-06
forum: Server Platforms
---

### Post by anindya23 on 2008-08-06
hello,
      I have 2 NIC card at my Ubuntu server Machine.
1 is for real ip and another is for local network.
i configured real ip while i install Ubuntu Server 8.04.
now how can configure networking with another nic card to communicate windows machine at network?

---

### Post by linux_tech on 2008-08-06
At the prompt enter the following command to install the SAMBA server applications:

    sudo apt-get install samba

---

### Post by StickyStyle on 2008-08-06
What do you mean by 'real IP'?  An public internet IP address?

Please show us the content of your /etc/network/interfaces file.

---

