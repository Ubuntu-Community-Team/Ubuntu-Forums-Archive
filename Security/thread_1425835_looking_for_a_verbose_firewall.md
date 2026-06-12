---
title: "looking for a verbose firewall"
date: 2010-03-09
forum: Security
---

### Post by v1nsai on 2010-03-09
I'm trying to find a firewall manager that will display alerts whenever a packet with no rules associated with it is detected, and give me the option to allow or deny.  Firewall seems to be the most popular iptables gui, but will it be this verbose?

---

### Post by bodhi.zazen on 2010-03-09
Why would you want something like that ? Do you really want to examine each packet ?

If so, wireshark is a good start.

---

### Post by mapltux on 2010-03-09
I guess you can give this a try [UFW]("https://help.ubuntu.com/community/UFW")

"The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw  provides a user friendly way to create an IPv4 or IPv6 host-based firewall"

And here's a blog post 'bout this [UFW]("http://beginlinux.com/blog/2009/10/ubuntu-9-10-ufw-firewall/")

---

### Post by v1nsai on 2010-03-10
Wireshark is a sniffer, I'm talking about a firewall that gives a popup window you when a new program tries to contact out of the network, or a remote host tries to connect to my system.  

Most firewalls I've seen in Windows do this, but firestarter is completely quiet.  UFW is just a frontend for IPtables, right?  That means that it still won't ask if I want to block or allow unknown connections.

---

### Post by bodhi.zazen on 2010-03-10
> **v1nsai said:**
> Wireshark is a sniffer, I'm talking about a firewall that gives a popup window you when a new program tries to contact out of the network, or a remote host tries to connect to my system.  

Most firewalls I've seen in Windows do this, but firestarter is completely quiet.  UFW is just a frontend for IPtables, right?  That means that it still won't ask if I want to block or allow unknown connections.

I am not aware of any such graphical firewall function in Linux. In general people configure their firewall to deny all traffic but default and allow only desired traffic.

To be honest, depending on your network and configuration, you will see tens to hundreds to thousands of such requests and it would be impossible to review such activity in real time.

For example, if you install apache, and forward port 80, at first you will get very few connection requests. You will next see the spiders, you will then see a steady increase in the number of hits.

On one public server I have dropped 15,000 packets in the last week. This amounts to 90 pop up alerts every hour (and this server is not *that* busy). 

If you open VNC or ssh you will see hundreds of attempts to connect in short time.

---

### Post by Sir Jasper on 2010-03-10
Hi,

My Windows firewall has alternative modes:
Block Most - block everything not specifically allowed
Allow Most - allow everything not specifically blocked
Rules Mode - ask when something is not specifically allowed

I do not think iptables is that flexible and I do not know of another ´buntu firewall.

My regards

---

### Post by bodhi.zazen on 2010-03-10
> **Sir Jasper said:**
> Hi,

My Windows firewall has alternative modes:
Block Most - block everything not specifically allowed
Allow Most - allow everything not specifically blocked
Rules Mode - ask when something is not specifically allowed

I do not think iptables is that flexible and I do not know of another ´buntu firewall.

My regards

iptables is both flexible and powerful, it has a steep learning curve is all.

I believe you would get the same function with iptables -P

"Block most" would be a default policy of DROP, with rules to allow or white list certain traffic.

"Allow most" would be a default policy of ACCEPT, with rules to drop or blacklist certain traffic.

There is no Linux equivalent of "Rules Mode" where a user is asked for input, which is what I thing the OP is wanting. One would need to log dropped traffic and review the logs.

---

### Post by rookcifer on 2010-03-11
There is a perl script in the repos called "psad" which is a port scan detector.  I haven't really used it, but it might be worth a try if you just have to know each time some bot is scanning your ports (I think it's hardly worth the trouble, but different strokes..).  I don't know if it alerts in real time, or just logs everything and alerts you in /var/spool/mail.  Either way, it will be the closest thing to what you are asking.

BTW, the features of many Windows firewalls (like ZoneAlarm) are really only useful on Windows.  Why?  Because the only reason you need outbound filtering is if you are concerned you might have malware that is phoning home (and malware is obviously a huge problem on Windows).  There is no other reason for it.  With Linux, since there is no malware, you do not need this type of alert each time something tries to establish an outbound connection to the Internet.

If you are on a desktop machine, just set UFW to default deny every incoming connection.  Or if you have a router, do the same with it and turn off UFW.

---

