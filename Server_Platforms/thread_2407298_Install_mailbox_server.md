---
title: "Install mailbox server"
date: 2018-12-02
forum: Server Platforms
---

### Post by programercek on 2018-12-02
Hi,

I tried to install mailbox server but I got wrong password after wants login to my mailbox.

I think mailbox is not created correctly but I'm not sure.

I installed port: 25,587, 993,995 and with Thunderbird I got correct settings.

Only problem is because username or password was wrong.

I used **postfix-mysql **

nano /etc/postfix/mysql-virtual-mailbox-domains.cf
		
user = usermail
password = mailpassword
hosts = 127.0.0.1
dbname = servermail
query = SELECT 1 FROM virtual_domains WHERE name='%s'


...


With this postmap -q example.com mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf

find 1 rows, so this works.

I want manual without cpanel or others programs create mailbox with terminal,...

What can be problem here?

Thanks.

---

### Post by TheFu on 2018-12-02
Postfix is an MTA. It is meant for sending and receiving SMTP communication.
It is not for reading email.  For that you'll want either a POP3 or IMAP server to integrate.

Thunderbird would use either POP3 or IMAP to point at an appropriate service, say, dovecot for IMAP-based message reading.
Thunderbird would use SMTP to send authenticated email over port 465/tcp or 587/tcp, your choice. This would go directly to postfix or some other compatible SMTP server (exim, sendmail, etc).  Only 1 MTA should be enabled on a server.

All of this ignores all the extra set required to have an email server on the internet. The SMTP is very simple, but to combat spammers, we've added on layer after layer after layer of other things as required.

Before we try to do anything else, 
* do you have a real domain registered?  example.com cannot be used since that is reserved.
* do you have DNS records setup for MX, A, CNAME, and 2 text records for SPF and DKIM requirements?
* is the server in a data center?  Running email from a residential location/home, is generally blocked. Nobody else will ever accept your emails.

The output from **postconf -n** would be helpful.  Other config files are probably necessary too, but not until you answer the above questions.

If you just want a local email server, the setup is different.  Being on the internet is a hassle thank to all the spammers in the world.

BTW, I have no clue what a "mailbox server" is, but I've only been running corporate email servers for 23 yrs.

---

### Post by programercek on 2018-12-02
Hello,

Before we try to do anything else, 
* do you have a real domain registered? example.com cannot be used since that is reserved.

Yes of course. I added my domain name.


* do you have DNS records setup for MX, A, CNAME, and 2 text records for SPF and DKIM requirements?

Yes of course. This all works.


* is the server in a data center? Running email from a residential location/home, is generally blocked. Nobody else will ever accept your emails.

Dedicated server and do not blocked any ports. 

I have all set-up and now I need to know how I can set-up mailbox like [EMAIL="test1@domain.com"]test1@domain.com[/EMAIL], [EMAIL="test2@domain.com"]test2@domain.com[/EMAIL] with password and then I can use this on Gmail, Outlook, Thuderbird...

---

### Post by TheFu on 2018-12-03
I asked the first questions because almost all email server posts here are for home users trying to accomplish things that aren't usually practical. Thanks for answering them.

Do the system and mail log files show any errors related to any of the tools involved?
 
There are about 20 steps to setting up something like this.  Showing 1 step makes it hard to figure out any issue.
[https://www.linode.com/docs/email/postfix/email-with-postfix-dovecot-and-mysql/](https://www.linode.com/docs/email/postfix/email-with-postfix-dovecot-and-mysql/) appears to be fairly complete instruction set, so can you check your work with it.  Anything missing?  Without posting all the related config files and showing the DB schema, 

I don't use google mail, so I'd have doubts they'd work with outside mail servers as clients, but all the other clients should work fine once everything is setup correctly. OTOH, I know that many enterprise email servers can connect as clients into gmail or yahoomail or hotmail or ... whatever mail via POP3 or IMAP and provide a centralized mailbox view for end-users.  Maybe gmail does the same? IDK.

POP3, IMAP and authenticated SMTP are standardized protocols and well supported.  A client that doesn't work with these standards is useless.  I use thunderbird and have helped others use android and Windows and Mac email clients to connect into our corporate email server(s) over the years.  They all work without any magic, just need to configure the correct ports, allow access through any firewalls, and have the correct login method picked.  We don't store login data in mysql, we use ldap, but pretty much everything else is the same.

Anyway, hope that step-by-step guide in the link is helpful.

---

### Post by programercek on 2018-12-03
Hello,


I tried now and if used this code:  sudo useradd -d /home/vmail/domain.com/username -m username mailbox exists. Then I used sudo passwd username and work but after send i cannot found my mails. 
I have checked in /home/vmail/domain.com/username but here not exists any file. In which folder need to check where mail exists?


Also I checked with thunderbird and is the same. wrong username or password...

---

### Post by TheFu on 2018-12-03
Again .... 

> Do the system and mail log files show any errors related to any of the tools involved?

There are about 20 steps to setting up something like this. Showing 1 step makes it hard to figure out any issue.
[https://www.linode.com/docs/email/po...cot-and-mysql/](https://www.linode.com/docs/email/po...cot-and-mysql/) appears to be fairly complete instruction set, so can you check your work with it. Anything missing? 

Why would system userids have **anything** to do with email users stored in mysql?  Hint: they do not.

---

### Post by programercek on 2018-12-03
Hello,


ok I used this link: [https://www.linode.com/docs/email/po...cot-and-mysql/](https://www.linode.com/docs/email/po...cot-and-mysql/) and send is ok. Now I have only problem after send from gmail to server not received and i got from this comand:  sudo mail -f /var/mail/vhosts/domain.com/dejan00, /var/mail/vhosts/domain.com/dejan00: 0 messages

Maybe is problem with PORT.

telnet localhost 25


220 domain.com ESMTP Postfix (Ubuntu)

telnet localhost 587


220 domain.com ESMTP Postfix (Ubuntu)

For 993
root@vmi223765:~# telnet localhost 993
Trying ::1...
Connected to localhost.
Escape character is '^]'.





root@vmi223765:~# telnet localhost 995
Trying ::1...
Connected to localhost.
Escape character is '^]'.



root@vmi223765:~# telnet localhost 143
Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
root@vmi223765:~#


I checked online and ports: 25, 587, 993,995 are open, only 143 is closed




Let me know if I have problem with any Port and thanks for your help.

---

### Post by TheFu on 2018-12-04
I only allow 25, 465 and 993 from the internet.  Checking access from localhost only shows that a service is running, it doesn't test any firewalls, since most won't block localhost by design.

25/tcp - non-authenticated SMTP and SMTPS using STARTTLS.
465/tcp - authenticated SMTPS from clients
993/tcp - IMAPS from authenticated clients.

I do not support pop3/pop3s or unencrypted imap.

465/tcp and 587/tcp have the same purpose.  Pick one to allow or both. Doesn't matter.

---

### Post by programercek on 2018-12-04
Thanks working.

Now I checked and I have email in Held 2 messages in /var/mail/dejan1985root@vmi223765:~# sudo mail -f **/var/mail/dejan1985**
"/var/mail/dejan1985": 2 messages 2 unread
>U   1 xxx xxx    Tue Dec  4 12:48  55/2672  da
 U   2 xxx xxx    Tue Dec  4 13:11  54/2653  test
?


I want to receive mail in /var/mail/vhosts/domainname/dejan1985/

Currently I have : 

mail_location = maildir:/var/mail/vhosts/%d/%n
mail_privileged_group = mail



From your help tutorial: [https://www.linode.com/docs/security/securing-your-server/#configure-a-firewall](https://www.linode.com/docs/security/securing-your-server/#configure-a-firewall)

Thanks.

---

