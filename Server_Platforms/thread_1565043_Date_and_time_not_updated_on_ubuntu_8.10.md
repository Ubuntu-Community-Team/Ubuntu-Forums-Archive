---
title: "Date and time not updated on ubuntu 8.10"
date: 2010-08-31
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-31
On my virtual machine ubuntu 8.10, the date and time settings are not updated every time when I restart the machine. Any tips plz...

---

### Post by arrrghhh on 2010-08-31
See the [UbuntuTime](https://help.ubuntu.com/community/UbuntuTime) documentation - the NTPD stuff is what you'll want to look at.

---

### Post by ratcheer on 2010-08-31
Quick steps:

1) Run "sudo date time-server", where time-server is some specific time server.
2) Run "sudo apt-get install ntp"
3) Edit /etc/ntp.conf to add some specific time servers.
4) Run "sudo service ntp restart" to pick up the changes you made to ntp.conf

Tim

---

