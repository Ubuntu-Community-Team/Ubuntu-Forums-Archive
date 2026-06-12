---
title: "Network Monitoring Tool"
date: 2005-08-16
forum: Server Platforms
---

### Post by Puracepa23 on 2005-08-16
I need a network monitoring tool for Ubuntu that will track:

- logons
- print queries
- erros
- other events
- don't need network bandwith...

I need this net monitor tool to log from Windows and Linux servers & clients. Any recommendations are very appreciated.

~Pete

---

### Post by relix42 on 2005-08-16
What software? Samba? NFS? 

Providing mroe information will help us help you.

---

### Post by Puracepa23 on 2005-08-16
I'm not sure if I know how to answer your question, but this is what I know.

I have a LAN with 47 machines (27 Windows 2003 Servers and 20 Linux RedHat). I built 3 Ubuntu machines with the intention of use them as System Management Center:

1 for Network Bandwidth Monitoring
1 for Squid Logs Analizer and
1 for Logons, Events and Alerts Monitoring 

I'm currently using Nagios on RedHat and Squid on Gentoo. I want to replace RedHat and Gentoo with Ubuntu. I've looked on Freshmeat for new applications, but I can't find what I'm looking for. My priority is to be able to get a screen with real-time outputs of every log from the servers:

- when domain users logon and logoff
- when domain users send documents to the printer
- when Sophos detects a virus thread
- etc...

I hope this answered your question. Thanks for your help!

~Pete

---

### Post by thewanderer on 2005-08-16
My immediate thought is to do the additional monitoring you require with syslog (syslog-ng perhaps).

Google for windows event log and syslog. There are a number of ways to implement syslog on windows servers.

Then feed all the events to your ubuntu syslog server where they can be parsed into alerts.

You could setup email alerting or check on freshmeat for some of syslog reporting tools - there may be something that will create a web page summary reporting layout  similar to what you have in mind.

---

