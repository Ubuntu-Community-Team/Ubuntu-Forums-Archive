---
title: "DHCP not working"
date: 2012-09-05
forum: Server Platforms
---

### Post by carlo bolzonello on 2012-09-05
Hi All,

Its been a long time. I have downloaded and installed the latest relase for server.

It all works great, When finnished installing, I installed webmin, but now I cannot get DHCP to work at all. Webmin says its not enabled/installed.

I have followed the DHCP install guide from [https://help.ubuntu.com/12.04/serverguide/dhcp.html](https://help.ubuntu.com/12.04/serverguide/dhcp.html)
But still webmin shows no DHCP

anything would help, I am busy trying to build a cloneziller box and only have tommorow

again thank you in advance

---

### Post by SeijiSensei on 2012-09-05
Is dhcpd running?  What does "ps ax | grep dhcp | grep -v grep" show?  If it's empty, you need to start the dhcpd server with "sudo /etc/init.d/isc-dhcp-server restart" as the Server Guide says.

---

### Post by carlo bolzonello on 2012-09-05
Thanks, Yip tried all that, still nothing works. I have removed the DHCP pakage and reinstalled, still same issue,

Says not running - and if i try to start the services, I get errors all over. I never had this issue before

---

### Post by carlo bolzonello on 2012-09-05
I assume that its installing verion 2 or 3 right?

---

