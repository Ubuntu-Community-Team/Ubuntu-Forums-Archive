---
title: "Monitoring windows machine services using nagios without nsclient++.."
date: 2012-11-05
forum: Server Platforms
---

### Post by veesyndicate on 2012-11-05
hye guys. I need some help, i want to monitor my windows server 2008 using nagios. i have using NSClient++, and its working as it should be. The problem is, for company windows server, it is best to use standard setting without installing some agent although it is for monitoring purpose. It is to protect their privacy and reduce to rely too much to outside installation software. Can we use ping or snmp to check any windows services we want without installing something on the windows server? Your ideas and suggestion are really needed on this and for other people too. Thanks

---

### Post by Habitual on 2012-11-05
no nsclient++? 
snmp.

This [guide for snmp using Cacti]("https://aaronwalrath.wordpress.com/2010/06/02/monitoring-windows-server-2008-r2-with-snmp-and-cacti/") may be helpful.
and the [Documentation]("http://nagiosplugins.org/man/check_snmp") also.

---

### Post by LHammonds on 2012-11-05
Without adding a client, you are limited in what you can check and to what extent.

You can use ping to see if the server is up or not which is the most basic test...however, if your server is running a firewall, you will need to allow ICMP from your Nagios server IP.

You can also check any port that is open such as web (port 80), SSL (443), mail (25), etc. but will be limited to just knowing if the port is there which may not really help catch problems behind the port.  For example, your Mail server might be running (can see and interact with port 25) but you may not be able to see that the spamfilter or antivirus service is not running...or that drive C: has filled up causing OS instability.

If your company is not going to allow full monitoring of your systems, you might want to scrap the project altogether.  What's the point of maintaining a monitoring system if you cannot monitor everything that is needed?  It is just extra work with no real benefit to you.

LHammonds

---

### Post by veesyndicate on 2012-11-06
> **Habitual said:**
> no nsclient++? 
snmp.

This [guide for snmp using Cacti]("https://aaronwalrath.wordpress.com/2010/06/02/monitoring-windows-server-2008-r2-with-snmp-and-cacti/") may be helpful.
and the [Documentation]("http://nagiosplugins.org/man/check_snmp") also.

Thanks for suggestion Habitual. I will check on it. It is very good alternative way for windows server. Beside, the package is already in the windows. Thanks

---

### Post by veesyndicate on 2012-11-06
> **LHammonds said:**
> Without adding a client, you are limited in what you can check and to what extent.

You can use ping to see if the server is up or not which is the most basic test...however, if your server is running a firewall, you will need to allow ICMP from your Nagios server IP.

You can also check any port that is open such as web (port 80), SSL (443), mail (25), etc. but will be limited to just knowing if the port is there which may not really help catch problems behind the port.  For example, your Mail server might be running (can see and interact with port 25) but you may not be able to see that the spamfilter or antivirus service is not running...or that drive C: has filled up causing OS instability.

If your company is not going to allow full monitoring of your systems, you might want to scrap the project altogether.  What's the point of maintaining a monitoring system if you cannot monitor everything that is needed?  It is just extra work with no real benefit to you.

LHammonds

I will discuss with my supervisor about this. Your comment are very supportive. Guess it can backup me for reason to this. It is good to use NSClient++ because we can monitor many services in windows. Trying my luck. Thanks

---

### Post by koenn on 2012-11-06
couple of additions to what others said

1- snmp - yes you can enable snmp on windows and use that to monitor several aspects of the system's state. It saves you the 'trouble' of installing a 3rd party agent, but even snmp is a feature you'd have to activate, and the security implications are similar (or worse), i.e. your server will expose a lot of internal info to the network. 
You're going to have to read up on snmp and security if you want to go that route. 


2- I've been thinking about monitoring Windows hosts through nagios myself - the solution I arrived at was querying WMI from scripts, and submit the results to nagios by way of nsca. 

Write up of how you could go about it:
[http://users.telenet.be/mydotcom/howto/nagios/nsca-wmi.html](http://users.telenet.be/mydotcom/howto/nagios/nsca-wmi.html)

(My opinion on) remote monitoring and how i decided nsca was best suited to my needs :
[http://users.telenet.be/mydotcom/howto/nagios/remote.html](http://users.telenet.be/mydotcom/howto/nagios/remote.html)

---

### Post by veesyndicate on 2012-11-08
> **koenn said:**
> couple of additions to what others said

1- snmp - yes you can enable snmp on windows and use that to monitor several aspects of the system's state. It saves you the 'trouble' of installing a 3rd party agent, but even snmp is a feature you'd have to activate, and the security implications are similar (or worse), i.e. your server will expose a lot of internal info to the network. 
You're going to have to read up on snmp and security if you want to go that route. 


2- I've been thinking about monitoring Windows hosts through nagios myself - the solution I arrived at was querying WMI from scripts, and submit the results to nagios by way of nsca. 

Write up of how you could go about it:
[http://users.telenet.be/mydotcom/howto/nagios/nsca-wmi.html](http://users.telenet.be/mydotcom/howto/nagios/nsca-wmi.html)

(My opinion on) remote monitoring and how i decided nsca was best suited to my needs :
[http://users.telenet.be/mydotcom/howto/nagios/remote.html](http://users.telenet.be/mydotcom/howto/nagios/remote.html)


Thanks! Very good tutorial. Checking.=)

---

