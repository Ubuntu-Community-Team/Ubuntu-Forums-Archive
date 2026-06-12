---
title: "network monitoring"
date: 2012-04-14
forum: Server Platforms
---

### Post by ParrSt on 2012-04-14
I have one physical machine running ubuntu desktop as a KVM virtual host.  On this machine are three virtual machines running ubuntu server.  A web server, file server and email server.  I want to monitor network usage for current bandwidth, historical and cumulative.  I also want to be able to monitor CPU load and HD capacity.  I also want to get email alerts if any of these fall out of specified ranges.

I tried to set up Munin on the web server but never could get it to display a page.  Not sure if that had anything to do with the virtual environment or not.

Any suggestions?  Or should I try Munin again?

Bob

---

### Post by d4m1r on 2012-04-14
I have a Ubuntu server using OpenVZ so not KVM, but it has SolusVM which is free AFAIK it works great.

It also has graphs for network/cpu/ram usage based on times (1 week view, 6 hour view, etc).

Another option is Webmin or DirectAdmin for managing Ubuntu servers but I don't know if they have network monitoring tools specifically.

---

### Post by bradjohnsten on 2012-04-19
Depending on your network setup, Zenoss has some pretty cool stuff using SNMP monitoring. You can monitor you network and devices and get alerts when defined events happen. They have an community supported version. 

[http://community.zenoss.org/index.jspa](http://community.zenoss.org/index.jspa)

---

### Post by SeijiSensei on 2012-04-19
I've run **ntop** on gateway routers; it's pretty easy to set up and provides extensive information via a web interface.  I'd imagine it could be run on a VM host to monitor usage by the guests just as well.

---

### Post by Habitual on 2012-04-19
Bob:

I'd try Munin again.
Maybe we can help you get that up and running easier than learning whole new package?

Network Usage can be monitored in various ways with various tools. Most rely upon snmp or an agent of some kind installed on the target.

---

### Post by mikaelcrocker on 2012-04-19
munin has trends and such and all your listed requirements, you can also create alarms and email notifications.  Also fairly easy to setup

---

