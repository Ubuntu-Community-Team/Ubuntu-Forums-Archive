---
title: "Best security software for ubuntu"
date: 2010-02-02
forum: Security
---

### Post by ubudog on 2010-02-02
Hello, what is the best security software for Ubuntu? (preferably open-source)

---

### Post by OrangeCrate on 2010-02-02
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by ubudog on 2010-02-02
Thank you, about to get firestarter running.

---

### Post by bodhi.zazen on 2010-02-02
Uggg ... 

Firestarter is an old application and the default for Ubuntu is UFW.

If you wish, it has a gui front end, GUFW

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Along those lines, please do not blindly install and configure a firewall without at least understanding what you are doing. Assuming you are running a Desktop install behind a router it really does not add much, if anything, to your security.

Please read the security sticky, it is a sticky for a reason.

If you have questions after reading the sticky, feel free to ask.

Otherwise your question is very open ended and is almost certainly answered 

1. Use a router.

2. Use strong passwords.

3. Sit back and enjoy, Linux is not windows and we do not have gaping holes in security you need to worry about.

---

### Post by ubudog on 2010-02-02
Thanks for your help!!

---

### Post by ubudog on 2010-02-02
> **bodhi.zazen said:**
> 
1. Use a router.

2. Use strong passwords.

3. Sit back and enjoy, Linux is not windows and we do not have gaping holes in security you need to worry about.

Would this setup be ok running a very small apache web server on a laptop and remote ssh access?

---

### Post by bodhi.zazen on 2010-02-02
Not if you can access your ssh server from outside your LAN (ie if you forward port 22 from your router and access the ssh server across an internet connection).

In that case, secure ssh by using keys, disable password, and use denyhosts, fail2ban, or iptables to limit failed connection attempts.

Apache is a bit safer, typically problems with Apache occur not due to Apache but rather to holes in cgi, such as php or with the modules rather then the Apache server.

If you use main stream applications, such as wordpress, just keep everything up to date. If you write your own code, be very careful.

Again, if you install Apache for public access look at Apache security. If you are really paranoid, take a look at mod_security.

---

### Post by ubudog on 2010-02-03
> **bodhi.zazen said:**
> 
In that case, secure ssh by using keys, disable password, and use denyhosts, fail2ban, or iptables to limit failed connection attempts.


Ok, I did that.  And I have firestarter which seems to work ok.  I will install fail2ban. Thanks for your help!

---

