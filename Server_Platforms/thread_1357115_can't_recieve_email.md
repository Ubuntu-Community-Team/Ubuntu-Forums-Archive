---
title: "can't recieve email"
date: 2009-12-16
forum: Server Platforms
---

### Post by menaice on 2009-12-16
ok so i got a ubuntu server running in my shop, i installed webmin which is working perfectly. I also want to run my own in house mail server. I installed postfix and i can send out without a problem no errors. But i can NOT receive emails. Is there something else i need to install besides postfix? This is the tutorial that i used here step for step
[http://postfixmail.com/blog/index.php/using-webmin-to-set-up-postfix/](http://postfixmail.com/blog/index.php/using-webmin-to-set-up-postfix/)
 
I know for a fact that its not my ISP blocking... because i have a sbs2008 server running exchange which works perfect.
 
Any help will be appericated
 
Here is an error message that got kicked back when i tried to reply to a test message
"Reporting-MTA: dns;blu0-omc3-s17.blu0.hotmail.com
Received-From-MTA: dns;BLU0-SMTP65
Arrival-Date: Wed, 16 Dec 2009 16:37:35 -0800
Final-Recipient: rfc822;mike@xxxxxxxxxxx Action: failed
Status: 5.5.0
Diagnostic-Code: smtp;550 <[EMAIL="mike@xxxxxxxxxxxx"]mike@xxxxxxxxxxxx[/EMAIL]> No such user here"

---

### Post by uniden9 on 2009-12-16
I'm not a postfix user.  But some general tips.

Make sure postfix is listening on port 25
$sudo netstat -tln
0.0.0.0:25
or
External Ip:25

Make sure you have a hole in the firewall to allow email in.
Open tcp port 25 in the firewall.

$sudo iptables-save
Will list your iptable rules.

From another machine, telnet to your external ip on port 25 and see what it says. 

Finally, check you log in /var/log

---

### Post by HermanAB on 2009-12-17
Howdy,

First test your DNS and ensure that you have both a MX and PTR record and that it actually resolves properly.

---

### Post by menaice on 2009-12-17
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
 
 
Thats what comes up on port 25 with netstat
 
Also i did the iptables command you suggested search the computer and found the file but have no idea how to open it. Kinda new to linux but have learned alot over the past month. 
 
I tried to telnet to it from another computer it connects then says "press any key to continue..."  so i press a key and it does nothing else.
 
Also just to add if it didn't say to do it in the tutorial i have not done it. Since i followed exactly what that tutorial said. I seen something about virutal domains in postfix on the webmin side. Don't really know what thats all about yet. THe other day deleted all the content in my mail.log file..... which now i think about it was dumb. And it doesn't seem to be loging anything anymore.

---

### Post by menaice on 2009-12-19
ok so i can now reply to my test messages but i have no idea where they go to.... Can't find them on the mail server.  Also iam getting these entries in the var/log/mail.log file
 
Dec 19 13:46:48 NIXServer postfix/smtpd[29991]: fatal: dict_open: unsupported dictionary type: pcre:  Is the postfix-pcre package installed?
Dec 19 13:46:50 NIXServer postfix/master[27125]: warning: process /usr/lib/postfix/smtpd pid 29991 exit status 1
Dec 19 13:46:50 NIXServer postfix/master[27125]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
 
Anyone know what this means or how to fix this?

---

### Post by linuxfrance on 2009-12-19
I would advice you with the following links

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

then this for optimisation 

[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

---

