---
title: "Managing Router Firewall Syslog data"
date: 2015-03-28
forum: Security
---

### Post by Spartanxxx on 2015-03-28
I've just bought a new router and set up the Firewal logs to be forwarded on Syslog UDP port 514.

I've edited 50-default.conf in /etc/rsyslog.d/ to pick up the router firewall logs as they happen in real time and output them to a file called modem.log using the lines

:fromhost-ip, is equal, "192.168.0.1" /var/log/modem.log
&~

This works but the router is forwarding quite a bit of log data to the modem.log file. 

I view the modem.log file in real time with log file viewer so that I can see all firewall activity and traffic in and out of my home network. The only problem is that the router forwards a lot more data that what I need. See below.

Mar 28 10:16:27 router06ae35 kernal: #warn<4> Connection Accepted: IN=eth0 OUT-eth1 SRC 192.168.1.102 DST 204.79.197.200 LEN-40 TOS=0x00 PREC=0x00 ID=19850 DF PROTO=TCP SPT=49600 DPT=443 WINDOW=1024 RES=0x00 ACK URGP=0

What I want to do is only write the Source IP, Destination IP and ports being used to the modem.log file so that I can easily view them in real time using log file viewer:

Mar 28 10:16:27 Connection Accepted SRC 192.168.1.102 49600 DST 204.79.197.200 443 


Does anyone know how to mainupulate the router firewall log data so that only the necessary info I reqire is written to the modem.log file?

---

### Post by SeijiSensei on 2015-03-28
Use awk and sed:
```
tail -f /var/log/modem.log | awk '{print $1 " " $2 " " $3 " Connection Accepted SRC " $12 " " $21 " DST " $14 " " $22}' | sed 's/SPT=//g' | sed 's/DPT=//g' >> /var/log/massaged-modem.log
```
Awk tokenizes the line using space as the default delimiter. (You can specify a different delimiter with the -F parameter.)  The items are numbered sequentially starting from one.  The two sed commands delete the "SPT=" and "DPT=" strings.

---

### Post by Spartanxxx on 2015-04-02
Thanks for taking the time to answer my question SeijiSensei

I put that command line in the 50-default.conf file in /var/log/ but it didn't create a new modem output file with the shortened output. I presume that's the file were you meant me to put the command line with awk and sed?

---

### Post by SeijiSensei on 2015-04-02
No, I meant you could run it from the command prompt with sudo.  The 50-default.conf file has settings that are passed to rsyslogd.  I don't know if you can configure it to pipe output to a script.  

I'd first make sure the command does what you want by running it from the command prompt.  Leave off the ">> /var/log/massaged-modem.log" so it will write the output to the screen. If it works properly, you could try adding the complete command to /etc/rc.local which runs with root privileges at startup and see if that works for you.

---

