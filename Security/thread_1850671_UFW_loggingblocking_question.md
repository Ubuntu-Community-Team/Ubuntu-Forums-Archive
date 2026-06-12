---
title: "UFW logging/blocking question"
date: 2011-09-27
forum: Security
---

### Post by chak2005 on 2011-09-27
Hi, I have a simple question I was hoping for verification and next  steps. I have UFW enabled and set up accordingly. However I am noticing  the log files are being filled all with this one line of blocked  traffic. This is cumbersome as it hinders my ability to discover any  clear issues with my normal network traffic. Am I correct in interpreting this as my   server trying to discover via multicast? Or is it my router? I am new with these logs. If  this is the case, how would I go about stopping this behavior? 

I am running a ubuntu server 11.04. 

```
ubuntuX kernel: [2538931.014884] [UFW BLOCK] IN=eth0  OUT= MAC=(removed but router's address) SRC=192.168.0.1 DST=224.0.0.1  LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=40139 PROTO=2
```

---

### Post by 3rdalbum on 2011-09-27
Just a tip for you: Your router already contains a firewall that will protect all the computers on your network. You actually don't need UFW. At all. Unless you don't trust the fabric of your own network AND you are running server software on your computer that's only intended for that one computer.

**In short:** Use UFW if you are running server software on your computer **AND** it's intended to only be accessed from that computer **AND** you don't trust the other computers or users on your network.

If even ONE of those three things is **not** true, then you don't need any sort of firewall running on any of your network's computers.

That doesn't exactly answer your question, but it might just make your life easier.

---

### Post by Dangertux on 2011-09-27
To answer the original question, this is actually the reason I don't use UFW in favor of just iptables scripts.

If you examine the files /etc/ufw/before.rules and /etc/ufw/after.rules, you will see exactly where the logging policy is applied, unfortunately alot of rules get tossed into one policy. If you want finer grained control over what is logged and what is not you may have to rewrite one or both of those files or opt for creating an iptables script and forgoing ufw alltogether.

---

### Post by SparTacux on 2011-09-27
If you are getting ufw logs showing up in several log files then you can redirect them to just UFW logs by editing 50-default.conf in etc\ryslog.d. using the example below: Put the following line at the top of 50-default.conf.

#  Default rules for rsyslog.
#
#            For more information see rsyslog.conf(5) and /etc/rsyslog.conf

#KEEP UFW DATA TO UFW LOGS ONLY
:msg ,contains, "UFW" /var/log/ufw.log
&~

#
# First some standard log files.  Log by facility.
#



********************************************************************

I suppose you could do some fine tuning here and put something like this instead. It might work.

#TRAP UFW logs to stop  192.168.0.1 broadcasts being printed in logs
:msg, contains, "SRC=192.168.0.1 DST=224.0,0.1"  
&~

---

