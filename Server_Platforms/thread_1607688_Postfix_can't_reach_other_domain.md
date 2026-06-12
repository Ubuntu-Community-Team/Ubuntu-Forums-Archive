---
title: "Postfix can't reach other domain"
date: 2010-10-28
forum: Server Platforms
---

### Post by solidussnake on 2010-10-28
I followed this post
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

But I found that I can only send and receive mails
from the domains in "mydestination"

How can I receive email from outside, like Gmail,
and send to them ?




(p.s. I have already get the domain name from godaddy,
points to the ip of my office,
and port forward 25,110,143 from my router to my ubuntu server)

---

### Post by yesrno on 2010-10-28
Whats does your /etc/postfix/main.cf say at the mydestination part ? Don't have my own configuration at hand but if I look back at the article I followed, I had:
 
mydestination = server1.example.com, example.com, localhost.example.com, localhost

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) was the article btw, might come in handy.

---

### Post by solidussnake on 2010-10-28
> **yesrno said:**
> Whats does your /etc/postfix/main.cf say at the mydestination part ? Don't have my own configuration at hand but if I look back at the article I followed, I had:
 
mydestination = server1.example.com, example.com, localhost.example.com, localhost

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) was the article btw, might come in handy.
what I have input to my Ubuntu are:

dig mx mydomain.com
sudo apt-get install postfix
sudo apt-get install mailutils
sudo postconf -e "home_mailbox = Maildir/"
sudo postconf -e "mydestination = localhost, mydomain.com"
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.0.0/24"
(my router is 192.168.0.1 and my ubuntu is 192.168.0.100)
sudo postconf -e "inet_interfaces = all"
sudo postconf -e "inet_protocols = all"
sudo  /etc/init.d/postfix stop
sudo  /etc/init.d/postfix start


other remains default.


I have tested,
send a email from [email]myname@mydomain.com[/email] to [email]myname@mydomain.com[/email]
at another ip (actually is my 3G phone).
And I can receive the email at my phone.

It means that all the networks is ok.
However I can only send email to mydomain.com
and email incoming can only be mydomain.com.

(p.s. It said "Relay access denied" when I send to other domain and other domain send to the server.)

---

### Post by yesrno on 2010-10-28
Relay access denied could mean a different kind of things, can you post the complete message you get back ?
And:
 
> 
Postfix logs all failed and successful deliveries to a logfile. The file is usually called /var/log/maillog or /var/log/mail; the exact pathname is defined in the /etc/syslog.conf file. 
When Postfix does not receive or deliver mail, the first order of business is to look for errors that prevent Postfix from working properly: 
[INDENT]% **egrep '(warning|error|fatal|panic):' /some/log/file | more**[/INDENT]Note: the most important message is near the BEGINNING of the output. Error messages that come later are less useful. 
The nature of each problem is indicated as follows: 
[LIST]
[*]"**panic**" indicates a problem in the software itself that only a programmer can fix. Postfix cannot proceed until this is fixed. 
[*]"**fatal**" is the result of missing files, incorrect permissions, incorrect configuration file settings that you can fix. Postfix cannot proceed until this is fixed. 
[*]"**error**" reports an error condition. For safety reasons, a Postfix process will terminate when more than 13 of these happen. 
[*]"**warning**" indicates a non-fatal error. These are problems that you may not be able to fix (such as a broken DNS server elsewhere on the network) but may also indicate local configuration errors that could become a problem later. 
[/LIST]

---

### Post by solidussnake on 2010-10-28
> **yesrno said:**
> Relay access denied could mean a different kind of things, can you post the complete message you get back ?
And:

Oct 28 18:23:33 leo pop3d: LOGIN, user=leo, ip=[::ffff:61.93.253.82], port=[2800]
Oct 28 18:23:33 leo pop3d: LOGOUT, user=leo, ip=[::ffff:61.93.253.82], port=[2800], top=0, retr=0, rcvd=12, sent=39, time=0
Oct 28 18:24:58 leo postfix/smtpd[2541]: connect from 061093253082.ctinets.com[61.93.253.82]
Oct 28 18:24:58 leo postfix/smtpd[2541]: NOQUEUE: reject: RCPT from 061093253082.ctinets.com[61.93.253.82]: 554 5.7.1 <leomkl@hotmail.com>: Relay access denied; from=<leo@leo-mui.info> to=<leomkl@hotmail.com> proto=ESMTP helo=<[192.168.1.101]>
Oct 28 18:25:00 leo postfix/smtpd[2541]: disconnect from 061093253082.ctinets.com[61.93.253.82]



[B]the first two lines is an action of get mail,
the others lines are, after I try send a email from the ubuntu mail server to a hotmail account.



And after that, I try sending email from another domain,
to my ubuntu mail server,
it has no output log.
The returned error email is:[/B]



"Subject: Mail System Error - Returned Mail

This Message was undeliverable due to the following reason:

Each of the following recipients was rejected by a remote mail server.
The reasons given by the server are included to help you determine why
each recipient was rejected.

    Recipient: <leo@leo-mui.info>
    Reason:    #5.1.0 Address rejected [email]leo@leo-mui.info[/email]


Please reply to <Postmaster@netvigator.com>
if you feel this message to be in error."

---

### Post by solidussnake on 2010-10-28
I have asked my friend this question.
He said "did you add MX record in godaddy ?"

I have only set these:

@ points to [my ip]
pop points to @
smtp points to @
imap points to @


I know where to set the MX records,
but I don't know what to set...

---

### Post by SeijiSensei on 2010-10-28
An MX server tells remote SMTP senders the IP address(es) of machine(s) configured to receive incoming mail for a domain.

> Oct 28 18:24:58 leo postfix/smtpd[2541]: NOQUEUE: reject: RCPT from 061093253082.ctinets.com[61.93.253.82]: 554 5.7.1 <leomkl@hotmail.com>: Relay access denied; from=<leo@leo-mui.info> to=<leomkl@hotmail.com> proto=ESMTP helo=<[192.168.1.101]>

At least two different things could be wrong here.  First, the server at ctinets.com may not be configured to accept mail from leo-mui.info.  If that's your ISP's server, you need to talk with them about that.  Also Postfix is announcing your server with its internal IP address, not the external address.  Here's a posting from 2003 about the same issue: [http://www.irbs.net/internet/postfix/0303/1005.html](http://www.irbs.net/internet/postfix/0303/1005.html)

---

### Post by solidussnake on 2010-10-28
> **SeijiSensei said:**
> An MX server tells remote SMTP senders the IP address(es) of machine(s) configured to receive incoming mail for a domain.



At least two different things could be wrong here.  First, the server at ctinets.com may not be configured to accept mail from leo-mui.info.  If that's your ISP's server, you need to talk with them about that.  Also Postfix is announcing your server with its internal IP address, not the external address.  Here's a posting from 2003 about the same issue: [http://www.irbs.net/internet/postfix/0303/1005.html](http://www.irbs.net/internet/postfix/0303/1005.html)

[B]Thx a lot ^.^

I have tried another IP (this is from another ISP)/
However, the situation is still the same.[/B]



Oct 29 00:10:16 leo postfix/smtpd[2201]: connect from n219079169029.netvigator.com[219.79.169.29]
Oct 29 00:10:16 leo postfix/smtpd[2201]: NOQUEUE: reject: RCPT from n219079169029.netvigator.com[219.79.169.29]: 554 5.7.1 <leomkl@hotmail.com>: Relay access denied; from=<leo@leo-mui.info> to=<leomkl@hotmail.com> proto=ESMTP helo=<[192.168.2.100]>
Oct 29 00:10:18 leo postfix/smtpd[2201]: disconnect from n219079169029.netvigator.com[219.79.169.29]



[B](p.s. I have also change
smtp_helo_name = leo-mui.info)[/B]

---

### Post by SeijiSensei on 2010-10-28
Change this:

```
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.0.0/24"
```

to 

```
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.0.0/16"
```

The first only allows addresses in the range 192.168.0.0-255; your attempts came from machines with 192.168.1 and 192.168.2 addresses.  Those aren't included in 192.168.0.0/24, but they are contained in 192.168.0.0/16 which matches anything starting with 192.168.

---

### Post by solidussnake on 2010-10-28
> **SeijiSensei said:**
> Change this:

```
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.0.0/24"
```

to 

```
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.0.0/16"
```

The first only allows addresses in the range 192.168.0.0-255; your attempts came from machines with 192.168.1 and 192.168.2 addresses.  Those aren't included in 192.168.0.0/24, but they are contained in 192.168.0.0/16 which matches anything starting with 192.168.

Really thank you for your reply
I have tried,
but no luck that it doesn't change anything.

I think the problem may not be "mynetworks".
Because I can use another IP (my 3G phone)
to send and receive email with [email]leo@leo-mui.info[/email](my ubuntu).
But I still can't send email to other domain
or receive email from other domain.

I am not sure whether my guess is correct or not.
Hope that you can help me~

---

### Post by solidussnake on 2010-10-29
[B]Thank you again

I can now receive e-mail from other domains,
after I have added a MX record in Godaddy DNS panel[/B]

Priority 0
Host @
Goes To mail.leo-mui.info

**and of course I have one more alias**

@ points to [my ip]
pop points to @
smtp points to @
imap points to @
**mail points to @**


[B]However, I still can't send email to other domain
still, "relay access denied"

what's wrong ?[/B]

---

