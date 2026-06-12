---
title: "sendmail not relaying from localhost"
date: 2009-02-05
forum: Server Platforms
---

### Post by sullam on 2009-02-05
Ubuntu server 8.04
I uninstalled the default MTA postfix and installed sendmail 8.14 because I am more used to sendmail. Mail is being recieved from outside hosts. The problem is that  system messages are not coming through such as mail from logwatch. What follows are the details,any help would be appreciated:

I can telnet at the console to port 25 using localhost or 127.0.0.1 or the ip address on the ethernet or my domainname.
I have added and commented out the following lines in the sendmail.cf and restarted sendmail and it makes no difference:

#O DaemonPortOptions=Port=smtp,Addr=127.0.0.1, Name=MTA
#O DaemonPortOptions=Port=smtp,Addr=192.168.1.10, Name=MTA

More info:

netstat -an | grep 25
**gets:**
tcp        0      0 0.0.0.0:25     0.0.0.0:*               LISTEN

tail -f /var/log/mail.log

**gets:**

Feb  5 08:40:03 ubuntu sm-msp-queue[29112]: n0VNK1ju003912: to=root, ctladdr=root (1000/1000), delay=4+15:20:02, xdelay=00:00:00, mailer=relay, pri=31080286, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]

Thanks for your ideas in advance.

---

