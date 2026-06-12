---
title: "Basic Mail Server setup problems - failed test 1."
date: 2013-07-07
forum: Server Platforms
---

### Post by NuxNik on 2013-07-07
Hello,

I am trying to set up a basic mail server using the guide 
 ----[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

The test he guide did not work
The test is to send a mail from root@localhost to  a user defined on the server
 I was able to do all of the steps but when I entered the "mail" command,  my result was:
  "no mail for fmaster"

I did not get any error message during the creation of the test mail

Any clues ?

------------------------------------------

Addendum:
I just noticed something with the telnet command

I an supposed to get a response which has
  "Connected to  mymailservername.mydomain.com"
Instead I got
  "Connected to localhost"
Is this meaningful ?
 
My /etc/hostame file contains
 mymailservername
My /etc/Hosts file contains
  127.0.0.1	localhost  127.0.1.1	mymailservername


  # The following lines are desirable for IPv6 capable hosts
  ::1     ip6-localhost ip6-loopback
  fe00::0 ip6-localnet
  ff00::0 ip6-mcastprefix
  ff02::1 ip6-allnodes
  ff02::2 ip6-allrouters

---

### Post by Doug S on 2013-07-07
> **NuxNik said:**
> I just noticed something with the telnet command

I an supposed to get a response which has
  "Connected to  mymailservername.mydomain.com"
Instead I got
  "Connected to localhost"
Is this meaningful ?I do not think so. I get the same on my system, and e-mail is working fine.```
doug@doug-64:~/tcpdump/061$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
...
```Have a look in /var/log/mail.log and mail.err to see if there is useful information there. Here are my log entries when I did the telnet stuff from your reference (I have IPV6 disabled):```
Jul  7 14:16:01 doug-64 postfix/smtpd[16598]: connect from localhost[127.0.0.1]
Jul  7 14:17:34 doug-64 postfix/trivial-rewrite[16607]: warning: inet_protocols: disabling IPv6 name/address support: Address family not supported by protocol
Jul  7 14:17:55 doug-64 postfix/cleanup[16610]: warning: inet_protocols: disabling IPv6 name/address support: Address family not supported by protocol
Jul  7 14:17:55 doug-64 postfix/smtpd[16598]: 71AAF1B8023C: client=localhost[127.0.0.1]
Jul  7 14:19:01 doug-64 postfix/cleanup[16610]: 71AAF1B8023C: message-id=<20130707211755.71AAF1B8023C@zzzz.zzzzzzz.com>
Jul  7 14:19:01 doug-64 postfix/qmgr[5745]: 71AAF1B8023C: from=<doug@localhost>, size=363, nrcpt=1 (queue active)
Jul  7 14:19:01 doug-64 postfix/local[16614]: warning: inet_protocols: disabling IPv6 name/address support: Address family not supported by protocol
Jul  7 14:19:01 doug-64 postfix/local[16614]: 71AAF1B8023C: to=<doug@localhost>, relay=local, delay=87, delays=87/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jul  7 14:19:01 doug-64 postfix/qmgr[5745]: 71AAF1B8023C: removed
Jul  7 14:19:09 doug-64 postfix/smtpd[16598]: disconnect from localhost[127.0.0.1]
```

---

### Post by NuxNik on 2013-07-08
Thanks for the response Doug,

Sadly the Mail,log and Mail.err are basically empty
[COLOR=#000000][INDENT]Last few lines of Mail.log

Jul  7 12:15:01 posta postfix/master[28895]: daemon started -- version 2.10.0, configuration /etc/postfix
Jul  7 12:15:04 posta dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul  7 12:15:04 posta dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
Jul  7 12:15:04 posta dovecot: master: Dovecot v2.1.7 starting up (core dumps disabled)
Jul  7 12:15:58 posta postfix/master[28895]: terminating on signal 15
Jul  7 12:15:58 posta postfix/master[29060]: daemon started -- version 2.10.0, configuration /etc/postfiix

[/INDENT]
[/COLOR]

---

### Post by SeijiSensei on 2013-07-09
Did you run the telnet test after Jul 7 12:15:58 when mail.log reports the Postfix daemon is running?

Open another terminal window and run the command "sudo tail -f /var/log/mail.log".  Now in the original window, type "sudo service postfix restart".  You should see entries appear in the log.  Now connect with "telnet localhost 25" as the documentation proscribes but only enter "ehlo localhost" and hit return.  You should see a log entry appear in the other window like the one at the top of Doug's log above that reads "connect from localhost".  The telnet session should display:
```

250-hostname
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

where "hostname" is the name returned by the "hostname" command.

---

### Post by NuxNik on 2013-07-12
Sorry for the delay, 
This has been pushed way down my activity list.
Not to mention that a few other outside elements were dumped

---

