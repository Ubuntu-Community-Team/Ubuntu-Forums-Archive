---
title: "Online Banking - Can't get the Java running"
date: 2008-11-10
forum: Security
---

### Post by flameproof on 2008-11-10
I can't get the Java running to get into my bank account. Any help is highly appreciated!

Ubuntu 8.10
Firefox 3.03 (User Agent Switcher installed - site allows only IE)


You can try it yourself if you get up to the login screen to put in username and password. Please try "Corporate Internet Banking"


[https://ibusiness.shacombank.com.hk](https://ibusiness.shacombank.com.hk)

---

### Post by Rhubarb on 2008-11-10
You need to install java, Applications --> Accessories --> Terminal:
```
sudo aptitude install sun-java6-plugin
```
Then enter in your password when prompted.
Once installed, you will need to restart firefox for the changes to make effect.

The URL comes up for me with a java prompt to accept a certificate.
Unfortunately a dialogue box comes up that reads:
> CIB services are now only supported under Windows platform.
This may possibly pose a problem for you.

---

### Post by kevdog on 2008-11-10
What about the Firefox User-Agent-Switcher extension?  Set it to IE -- sometimes that works!

---

