---
title: "Does system logs show you about your system is compromised?"
date: 2012-12-28
forum: Security
---

### Post by samiux on 2012-12-28
I am writing to comfirm you all that the Ubuntu wiki namely ["DidIJustGetOwned"](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned) contains some incorrect information.

I would like to response the thread at [here](http://ubuntuforums.org/showthread.php?t=2097567) but unfortunately that it is closed by Forums Admin.

**syslog**

This [video](http://www.youtube.com/watch?v=BwCfx9Syg5U) is to confirm that the syslog will not help you to identify if your system is compromised or not.  Please take some of your valuable time to watch.

**auth.log and firewall log**

Meanwhile, the auth.log will not show you something as you get the shell without login and authentication.  The firewall log will also not show you any valuable information as the shell is connected to the attacker by reverse connection.

In addition, the port that attackers used may not be the one stated in the wiki.  They may not be 1337, 4141, 4444, 6666, 7777, 9999, 13337, 31337, and 44444.  It can be anything.

**rkhunter and chkrootkit**

rkhunter and chkrootkit will produce a lot of false postitive alerts when your system is just updated.  This will waste a lot of your time to figure them out.

**Additional Users**

If the attackers create a new user account in your system, the uid will not be greater than 1000.  Be keep in mind about that.

Thank you for reading.

Samiux

---

### Post by Elfy on 2012-12-28
Closed.

Edit the wiki.

---

