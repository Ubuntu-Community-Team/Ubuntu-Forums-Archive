---
title: "MIRC and ufw problem"
date: 2010-08-09
forum: Security
---

### Post by syaoran87 on 2010-08-09
Hi, I'm perfectly able to connect to my mirc server, example rizon with my UFW. The problem comes when i have to dcc send or receive. I have checked the ports used for DCC send/receive which is in the range of 1024 to 5000. However, when i configured my ufw to open this ports, my dcc send still doesn't work. My dcc send and receive works perfectly fine when i disable my ufw. However, i still want to use ufw for security reasons and hope someone can help me out here. Thank you so much!

---

### Post by Bachstelze on 2010-08-09
*Never mind.*

---

### Post by syaoran87 on 2010-08-09
i tested the range from 40000-65535 and it can go through...but doing this will enable hackers to exploit so many open ports. I need help. anyone please?

---

### Post by bodhi.zazen on 2010-08-09
Just open the ports when you use dcc

dcc is exploitable if you allow it, how does UFW help ?

If you are not running MIRC, then there are no open ports and nothing to firewall.

If you are running MIRC, you are allowing the traffic, and again there is nothing to firewall.

So you see, UFW does not help you, in this case it does not increase security at all.

Rather then UFW I think you want to lock MIRC down with Apparmor.

---

### Post by syaoran87 on 2010-08-10
ok, makes alot of sense now. But can i ask you another question? What's the purpose of UFW then? and also, if i put my UFW status to inactive, my ports which i earlier configured to be open will be back to default settings(meaning closed/stealth?

---

### Post by bodhi.zazen on 2010-08-10
Firewalls are powerful tools and have many uses.

On Windows, by default, there are several open ports. Most people do not use those ports. Most people who say you need a firewall on Windows are advocating that rather then identifying and closing unused ports you merely install a firewall to block tarffic.

On Linux, bu default, there are no open ports, so there is nothing to firewall.

Now let us imagine you open a port. How does a firewall help you ? It depends on the port.

If the port is say port 22, ssh, you may wish to limit access to a limited set of IP addresses. A firewall will help. You can use iptables to block brute force attempts to log in.

If the port is 80 or 443 , http and https, and you are running a public server, then you may not want to firewall the ports at all.

You can use iptables to block unsavory ip addresses.

You can use iptables to log network traffic.

As I said, in your case, the way you are using the ports in question and iptables you are not adding much, if any, security at all. You are opening ports and allowing all traffic on those ports.

See : 

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by syaoran87 on 2010-08-10
Thanks for the help. I have a better understanding now. If i disable my ufw now, my ports will be back to default right?

---

### Post by bodhi.zazen on 2010-08-10
> **syaoran87 said:**
> Thanks for the help. I have a better understanding now. If i disable my ufw now, my ports will be back to default right?

Yes. You open / close a port by installing or disabling a server, in your case mirc .

You shape or restrict access to the port via a firewall.

---

