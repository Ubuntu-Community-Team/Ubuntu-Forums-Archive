---
title: "Mail, incoming, problems."
date: 2008-06-24
forum: Server Platforms
---

### Post by WintechAB on 2008-06-24
To make this clear first: I am completele new to Linux command line.

I am trying to start a mailserver, POP3, IMAP & SMTP.
I have followed the guide "PostfixCompleteVirtualMailSystemHowto" here: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)
And everything seems to be up and running.
The problem is, when i try to send a mail to my account(accountname@myhost.se) nothing gets there.
But when i send mails internally from the Ubuntu machine, "Welcome"-mails and so on, the mail reaches the target mailbox.
Ive searched through different log files but i cant find anything from anyone "outside" the Ubuntu machine.

I can connect from outside(the internet) to the mailbox, both through POP3 and IMAP and get the mails in the mailbox, but when someone outside(from the internet) tries to send a mail it doesnt reach the mailbox.

I have no firewalls active, and i cant find any error messages.

What went wrong?

Best regards // Lars

---

### Post by hyper_ch on 2008-06-24
do you have a static or dynamic ip?

Have a read at your /var/log/mail.log 

I assume

(1) your ISP doesn't let you use port 25 to send emails
or
(2) the receiving mail servers don't accept mail from you because you're not on a static ip

---

### Post by WintechAB on 2008-06-24
I have a dynamic IP, but i use a domain name.
My ISP allows port 25

I have had a mailserver(hMailserver) active for more then 2 years using Windows XP and never had any problems, using my domain name and standard ports.
The only thing my ISP wont allow is the default SMTP-port, but that is not so very important, i could use change the SMTP-port or use a relay on the clients.

Edit.
The problem is not sending mails from the server.
The problem is receiving mails from the "outside".

---

### Post by hyper_ch on 2008-06-24
do you forward the port accordingly from the router to the server?

---

### Post by WintechAB on 2008-06-24
Yes.
As i said before, i have no problems connecting to the server from the outside(the internet) and reading the mailbox, the problem is that mails wont reach the mailbox. i.e. the mailbox is empty no matter how many "test" mails i send.

If i send a mail from the server (ie through postfix admin's welcome mail-system) it will find its way to the mailbox, but mails from the "outside" is nowhere to find.

---

### Post by hyper_ch on 2008-06-24
what does the mail.log say?

---

### Post by WintechAB on 2008-06-24
It only shows the logins from my mail client, the SQL-command, and so on.

Jun 24 15:12:10 brasse authdaemond: password matches successfully
Jun 24 15:14:41 brasse pop3d: LOGIN, user=x@x.se, ip=[::ffff:12.12.12.12], port=[54236]
Jun 24 15:14:41 brasse pop3d: LOGOUT, user=x@x.se, ip=[::ffff:12.12.12.12], port=[54236], top=0, retr=559, rcvd=40, sent=749, time=0
Jun 24 15:15:23 brasse authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=x@x.se, fullname=mr x, maildir=x@x.se/, quota=0S, options=<null>
Jun 24 15:15:23 brasse authdaemond: SQL query: SELECT username, password, "", 5000, 5000, '/home/vmail', maildir, concat(quota,'S'), name, "" FROM mailbox WHERE username = "x@x.se"

Things like that, cant find any errors.

---

### Post by hyper_ch on 2008-06-24
did you install firestarter or something like that?

---

### Post by WintechAB on 2008-06-24
Firestarter? No, not that i know of. What is that? afaik i have no firewall, ive stopped shorewall and linux firewall(iptables)
I saw now that "Shorewall" has a "When Stopped"-rule, can that have anything to do with it? I have a webserver installed and that works good.
The "when stopped"-rule looks like this:
eth0 0.0.0.0 routeback
(eth0 is my standard, and only network connection, except loopback)

This it what the log says when i restart the postfix server and send a "welcome message" through postfix admin.
Jun 24 16:13:32 brasse postfix/postfix-script[23118]: stopping the Postfix mail system
Jun 24 16:13:32 brasse postfix/master[22169]: terminating on signal 15
Jun 24 16:13:33 brasse postfix/postqueue[23194]: warning: Mail system is down -- accessing queue directly
Jun 24 16:13:34 brasse postfix/postfix-script[23269]: starting the Postfix mail system
Jun 24 16:13:34 brasse postfix/postqueue[23344]: warning: Mail system is down -- accessing queue directly
Jun 24 16:13:35 brasse postfix/master[23270]: daemon started -- version 2.5.1, configuration /etc/postfix
Jun 24 16:13:46 brasse postfix/smtpd[23351]: connect from localhost[127.0.0.1]
Jun 24 16:13:46 brasse postfix/smtpd[23351]: C8D02310705: client=localhost[127.0.0.1]
Jun 24 16:13:46 brasse postfix/cleanup[23356]: C8D02310705: message-id=<20080624141346.C8D02310705@x.se>
Jun 24 16:13:47 brasse postfix/smtpd[23351]: disconnect from localhost[127.0.0.1]
Jun 24 16:13:47 brasse postfix/qmgr[23349]: C8D02310705: from=<x@x.x>, size=478, nrcpt=1 (queue active)
Jun 24 16:13:47 brasse postfix/virtual[23357]: C8D02310705: to=<x@x.x>, relay=virtual, delay=1.3, delays=0.81/0.26/0/0.23, dsn=2.0.0, status=sent (delivered to maildir)
Jun 24 16:13:47 brasse postfix/qmgr[23349]: C8D02310705: removed

---

### Post by hyper_ch on 2008-06-24
well, send yourself an email from outside and check the shorewall log

---

### Post by WintechAB on 2008-06-24
Hmm.. i dont think that is the problem.
Now i see that the test mails i sent earlier is starting to bounce, with this message:
Diagnostic-Code: X-Postfix; host >myhost<.se[90.228.195.71] said: 550 Unknown
    user (in reply to RCPT TO command)

Seems like postfix dont recognise my mail receiver.
I have an virtual account on the mailserver(postfix) thats called [email]name@mymdomain.se[/email](example), and thats where ive tried to send the test mails.

---

### Post by hyper_ch on 2008-06-24
postfix thinks there is no such user that you try to send the email to.

---

### Post by WintechAB on 2008-06-24
Yeah, figured that out as well.
Why doesent postfix recognise the users i have created then?

---

### Post by windependence on 2008-06-24
You need to set up your MX records on your domain. They need to point to your box in order to get mail.

Also, just for giggles, go to [www.canyouseeme.org](www.canyouseeme.org) and check your port 25 again.

-Tim

---

### Post by hyper_ch on 2008-06-24
> **WintechAB said:**
> Yeah, figured that out as well.
Why doesent postfix recognise the users i have created then?

No clue how you setup postfix ;)

---

### Post by WintechAB on 2008-06-24
Hmm.. i have MX...
subdomain: @
type: MX
data: 10 mydomain.se

And how come i need to edit my domain when everything worked perfectly on my Windows server?

port 25 doesnt work, but as i said before, outgoing mail is not the problem.
POP3 and IMAP ports are open.

---

### Post by WintechAB on 2008-06-24
Sorry double post.

---

