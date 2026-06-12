---
title: "Your favourite monitoring solutions?"
date: 2010-02-16
forum: Server Platforms
---

### Post by minaev on 2010-02-16
What do you use to monitor your servers? I use Munin and think about integrating it with Nagios. Munin "just works" and is a good simple solution. I'm beginning to think, though, that this simplicity could be a minus, rather than an advantage...

---

### Post by Grenage on 2010-02-16
We use Nagios here, I get on with it very well.

---

### Post by minaev on 2010-02-16
Do you think you don't need the dynamic picture, as presented by graphs a la Munin?

---

### Post by Grenage on 2010-02-16
PNP4Nagios add-on gives graphing support, if you want/need it; I don't have a need for them at the moment.

---

### Post by minaev on 2010-02-16
Thank you.

---

### Post by mimor on 2010-02-16
I would recommend as well.
It is quite expandable and there are a lot of people out there using it, making support on IRC more probable.

---

### Post by dnvikram on 2010-02-16
1) OSSEC - Host Based Intrusion Detection (HIDS)

2)Logwatch - For logs monitoring & reports

3)Tiger - For intrusion detection signatures,rootkits,vulnerabilities on host level

4)SPLUNK - For central syslogging of all the linux machines on the network

5)NMON(IBM's Nigel Monitor)- For system resource(s) reports generation

6)Denyhosts - For monitoring SSH brute force logins & blacklisting the culprit IPs on the host level

7)Shell scripts to monitor and alert(email) me any filesystem(s) full (or) out of space issues.

These are the ones I am currently running on my Ubuntu 9.04 server and it works perfectly without any issues,like a well oiled machine.All the above work in tandem with each other.

Monitoring,performance tuning & hardening are things which need to be done on a regular basis and one has to update/upgrade/tune the methods regularly inorder to keep the server secure and efficient.

Let me know what you are interested in and trying to achieve.Would be glad to assist you.

---

### Post by fang0654 on 2010-02-16
We use nagios in my environment.

Originally we had Zabbix up and running.  I liked it, but I ran into difficulty monitoring non-standard things, such as different raid controllers, etc.  Not that it can't be done, I just gave up on it :)

Next, I had ZenOSS.  Pretty much the same situation, I got *most* of the monitoring working great, but would run into trouble trying to sift through the dozens of Compaq SNMP templates.

Finally, recently, I switched over to nagios, and was able to get everything up and running very quickly.  It is extremely flexible, and it was pretty easy to monitor all of the different types of raids I have in production.

---

### Post by minaev on 2010-02-17
Thanks. I considered Zabbix, but it seems to be pretty heavy.

---

### Post by fcefan00 on 2010-05-18
OSSIM could be very interesting for you. It's a bit more complex, because it combines Nagios, Snort, Nessus, Arpwatch and a lot more for monitoring your network. It belongs to so called SIM solutions-> [http://en.wikipedia.org/wiki/Security_information_management](http://en.wikipedia.org/wiki/Security_information_management)

---

