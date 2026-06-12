---
title: "Cisco router config software"
date: 2010-12-03
forum: Server Platforms
---

### Post by DanHorniblow on 2010-12-03
Hi, I want to able to configure my cisco router with my ubuntu server machine via the serial port it has, are there any programs out there for ubuntu server similar to putty?

---

### Post by arrrghhh on 2010-12-03
ssh comes built-into the system.  As does telnet ;)

---

### Post by DanHorniblow on 2010-12-03
I need to use the COM port on the server and im not sure what protocol that uses ? the router has no configuration on it yet so it doesn't have an ip address

---

### Post by arrrghhh on 2010-12-03
> **DanHorniblow said:**
> I need to use the COM port on the server and im not sure what protocol that uses ? the router has no configuration on it yet so it doesn't have an ip address

Ah, I didn't realize that...

Found the solution (hopefully).  Install minicom :D  [Source](http://ubuntuforums.org/showthread.php?t=1208562)

---

### Post by endotherm on 2010-12-03
I think you are asking for a hyperterm equivalent app.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1249652](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1249652)
seems gtkterm and minicom are the most recommended.

---

### Post by DanHorniblow on 2010-12-04
Thanks for your replies how do I start gtkterm or minicom once incstalled?

---

### Post by endotherm on 2010-12-04
this is likely where we should have started:
[https://help.ubuntu.com/community/CiscoConsole](https://help.ubuntu.com/community/CiscoConsole)

---

### Post by arrrghhh on 2010-12-05
> **endotherm said:**
> this is likely where we should have started:
[https://help.ubuntu.com/community/CiscoConsole](https://help.ubuntu.com/community/CiscoConsole)

Ah-ha!  I was hoping for a community page like that, but my google-fu didn't turn it up.  Nice find!

---

