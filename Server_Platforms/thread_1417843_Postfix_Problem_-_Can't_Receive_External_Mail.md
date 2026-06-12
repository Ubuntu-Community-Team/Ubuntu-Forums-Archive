---
title: "Postfix Problem - Can't Receive External Mail"
date: 2010-02-27
forum: Server Platforms
---

### Post by EagleIdaho on 2010-02-27
Hello Forum Folks,

I recently installed postfix onto my ubuntu 9.10 server.  I can send mail from the command line (using mail).  My problem is that I cannot receive mail from the external internet.  If I send mail from testuser01 (testuser01@mydomain.com) to say [email]john@yahoo.com[/email], John gets the mail.  But. if he tries to reply or send new mail to [email]testuser01@mydomain.com[/email], he receives the following error:

xxx.xx.xxx.xxx does not like recipient
Remote host said: 550 #5.1.0 Address rejected [email]testuser01@mydomain.com[/email] Giving up on xxx.xx.xxx.xx

NOTE (xxx.xx.xxx.xx is the domain ip address.  I substituted xxx.xx.xxx.xx for the real ip address given in the error message).

I appreciate any help or troubleshooting suggestions.  This is my first time at trying to setup postfix.

Thanks

---

### Post by HermanAB on 2010-02-27
For mail to work, you must have A, MX and PTR records in your DNS.  Use 'dig' and verify that before doing anything else.

---

### Post by EagleIdaho on 2010-02-28
Hello Herman,

      Thanks for looking at my question.  Below is the output from the dig command:

; <<>> DiG 9.6.1-P2 <<>> k7qhu.com ANY
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19538
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;k7qhu.com.            IN    ANY

;; ANSWER SECTION:
k7qhu.com.        2614    IN    MX    10 mailstore1.secureserver.net.
k7qhu.com.        2614    IN    MX    0 smtp.secureserver.net.
k7qhu.com.        2058    IN    A    70.58.167.133
k7qhu.com.        2058    IN    NS    ns61.domaincontrol.com.
k7qhu.com.        2058    IN    NS    ns62.domaincontrol.com.

;; Query time: 50 msec
;; SERVER: 205.171.3.65#53(205.171.3.65)
;; WHEN: Sat Feb 27 22:33:53 2010
;; MSG SIZE  rcvd: 159

---

### Post by EagleIdaho on 2010-03-01
Hello Again,

     Here is some additional information that might help in solving this problem.  I noticed that the error is from the mail server that I used to send the mail, not the destination server (k7qhu.com).  Below is the message:

216.69.186.201 Does not like the recipient
Remote host said 550 #5.1.0 Address rejected.

I had originally thought it was my server that was rejecting the mail.  But is seems the mail server I use to send the mail to k7qhu.com doesn't like the address.  Is there a parameter I need to set in the postfix configuration file that enables other mail servers to recognize it?

As you can tell, this is the first time I have set up a mail server, so any suggestions or help appreciated.

---

### Post by noway2 on 2010-03-01
From what I can tell, error 550 is a permanent error, typically indicating that the user to whom the mail is addressed doesn't exit.

There should be some output in your mail.log file that will provide more insight, but it is starting to look like you have a configuration problem.  Locate your mail.log file, which is typically in /var/log, and post a snippet corresponding to the error message so we can see what is happening on your server's end.

---

### Post by EagleIdaho on 2010-03-03
Hello All,

       Good News! The problem has been resolved.  It was a combination of errors.  First, my A record and MX record were incorrect on the DNS server.  Once they were corrected, the errors went away, but still no mail was being received from the external internet.  It looked like port 25 was being blocked by my ISP.  I checked with them and they said port 25 was open.  I tried different settings on the modem/router combination, but nothing worked.  I called the ISP again and asked the support person to try to telnet to port 25.  He tried and agreed it was timing out, but again emphasized that it was not their problem.  I tried troubleshooting again, but everything still pointed to port 25 not being forwarded to my server.  I took a break for the afternoon, and this evening suddenly everything is working!  I have a suspicion that the 2nd call to the ISP triggered them into some kind of action.  Who knows.  

     Anyway, thanks to the forum and hopefully this will help someone in the future.

Steve

---

