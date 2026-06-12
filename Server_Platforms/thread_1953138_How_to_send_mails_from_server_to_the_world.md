---
title: "How to send mails from server to the world?"
date: 2012-04-05
forum: Server Platforms
---

### Post by deepakdeshp on 2012-04-05
I am using Ubuntu server 10.04 which has got a dynamic ip. I am using noip and using a domainame but I can not send mails outside. When I send mails to google address it lands in spam and to other addresses lile yahoo etc they do not reach at all.

What will help me send mails from my mail server?

[LIST=1]
[*]Is it  having a fixed ip ?
[*]Or do I have to book a domain name , get a fixed ip and tie the domain name to the fixed ip?
[/LIST]

---

### Post by Cheesemill on 2012-04-05
You need three things to run a mail server successfully.

A fixed IP
A domain name.
Forward and reverse DNS entries.

The IP, domain name, and forward DNS entries are easy to get hold of, however residential ISP's usually won't let you change your reverse DNS entry.

So check with your ISP and see if they allow you to set up a Reverse DNS entry linking your domain name to your fixed IP address.

[http://www.simpledns.com/kb.aspx?kbid=1052](http://www.simpledns.com/kb.aspx?kbid=1052)

---

### Post by kevdog on 2012-04-05
I used to have Comcast and would forward my outgoing mail from my server (with dynamic IP and IP name) through their SMTP server without any problem.  It wasn't an open relay since I needed a username and password, but beyond this, it was pretty dang close.

---

### Post by deepakdeshp on 2012-04-08
When I send mail from my system it  reaches gmail but gmail does not accept the mail. The message from gmail is

*host [gmail-smtp-in.l.google.com]("http://gmail-smtp-in.l.google.com/")[*[I]173.194.79.27] said:
    550-5.7.1 [117.219.113.30] The IP you're using to send mail is not
    authorized to 550-5.7.1 send email directly to our servers. Please use the
    SMTP relay at your 550-5.7.1 service provider instead. Learn more at 550
    5.7.1 [http://support.google.com/mail/bin/answer.py?answer=10336](http://support.google.com/mail/bin/answer.py?answer=10336)
    ky3si2006548pbc.127 (in reply to end of DATA command)
[/I]

---

### Post by deepakdeshp on 2012-04-08
> **kevdog said:**
> I used to have Comcast and would forward my outgoing mail from my server (with dynamic IP and IP name) through their SMTP server without any problem.  It wasn't an open relay since I needed a username and password, but beyond this, it was pretty dang close.


How do I send mails through the SMTP server . I have a broad band connection and also I have booked a domain name so the later should also have an smtp server. It should be possible to forward the mails through the smtp server of my domain . But how t do it. I want to send mails from my Ubuntu system through command mode to google yahoo etc

---

### Post by lisati on 2012-04-08
It could be that Google is rejecting your IP address because it is listed on some DNSBLs as a dynamic IP address that shouldn't be sending emails. There may also be reverse DNS issues.

See [http://www.nszones.com/dyn.ip?117.219.113.30](http://www.nszones.com/dyn.ip?117.219.113.30) and [http://www.spamhaus.org/query/bl?ip=117.219.113.30](http://www.spamhaus.org/query/bl?ip=117.219.113.30) for more information.

As an aside: word has it that nszones isn't the most reliable DNSBL around, It's probably better to look at the spamhaus listing, paying attention to the information on the PBL list for your IP address. I've got a web page set up to help check DSNBLs, at [http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist) - please be patient, it can take a little while before it shows useful information if no-one has checked a particular IP address in the last few minutes.

---

### Post by deepakdeshp on 2012-04-08
I did the configuration as per the following link and now my mails arent going to  the users @localhost too.

**[http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid](http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid)**

```
 sudo tail /var/log/mail.log

```Apr  8 01:28:05 ubuntu postfix/qmgr[20204]: 964BD7F4D4: from=<>, size=2199, nrcpt=1 (queue active)
Apr  8 01:28:05 ubuntu postfix/bounce[20219]: 653857F4D2: sender non-delivery notification: 964BD7F4D4
Apr  8 01:28:05 ubuntu postfix/qmgr[20204]: 653857F4D2: removed
Apr  8 01:28:05 ubuntu postfix/smtp[20217]: 964BD7F4D4: to=<tejas@ubuntu.tejas>, relay=none, delay=0.14, delays=0.05/0/0.09/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=ubuntu.tejas type=A: Host not found)
Apr  8 01:28:05 ubuntu postfix/qmgr[20204]: 964BD7F4D4: removed
Apr  8 01:32:57 ubuntu postfix/pickup[20203]: DADEA7F4D4: uid=1000 from=<tejas>
Apr  8 01:32:57 ubuntu postfix/cleanup[20355]: DADEA7F4D4: message-id=<20120408053257.DADEA7F4D4@ubuntu.tejas.com>
Apr  8 01:32:57 ubuntu postfix/qmgr[20204]: DADEA7F4D4: from=<tejas@ubuntu.tejas>, size=333, nrcpt=1 (queue active)
Apr  8 01:33:00 ubuntu postfix/smtp[20359]: DADEA7F4D4: to=<deepakdeshp@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.79.26]:25, delay=2.7, delays=0.12/0.01/1.2/1.4, dsn=2.0.0, status=sent (250 2.0.0 OK 1333863180 mk2si11549528pbc.167)
Apr  8 01:33:00 ubuntu postfix/qmgr[20204]: DADEA7F4D4: removed

---

### Post by deepakdeshp on 2012-04-08
> **lisati said:**
> It could be that Google is rejecting your IP address because it is listed on some DNSBLs as a dynamic IP address that shouldn't be sending emails. There may also be reverse DNS issues. 

My ip is a dynamic ip , not static.

---

### Post by deepakdeshp on 2012-04-08
1

---

### Post by deepakdeshp on 2012-04-08
> **deepakdeshp said:**
> I've got a web page set up to help check DSNBLs, at [http://lisati.homelinux.com/blacklist](http://lisati.homelinux.com/blacklist) 

The info for my ip is 

Current issues**117.219.113.30** has a missing or invalid reverse DNS **117.219.113.30** is listed in **bl.nszones.com** 
[Listed in DYN - Dynamic IPs - see [http://www.nszones.com/dyn.ip?117.219.113.30](http://www.nszones.com/dyn.ip?117.219.113.30)] **117.219.113.30** is listed in **dnsbl-2.uceprotect.net**  [Net 117.219.64.0/18 is UCEPROTECT-Level2 listed because 231 abusers  are hosted by BSNL-NIB National Internet Backbone/AS9829 there. See: [http://www.uceprotect.net/rblcheck.php?ipr=117.219.113.30](http://www.uceprotect.net/rblcheck.php?ipr=117.219.113.30)] **117.219.113.30** is listed in **dnsbl-3.uceprotect.net** [Your ISP BSNL-NIB National Internet Backbone/AS9829 is UCEPROTECT-Level3 listed for hosting a total of 55146 abusers. See: [http://www.uceprotect.net/rblcheck.php?ipr=117.219.113.30](http://www.uceprotect.net/rblcheck.php?ipr=117.219.113.30)] **117.219.113.30** is listed in **pbl.spamhaus.org** [[http://www.spamhaus.org/query/bl?ip=117.219.113.30](http://www.spamhaus.org/query/bl?ip=117.219.113.30)] **117.219.113.30** is listed in **zen.spamhaus.org** [[http://www.spamhaus.org/query/bl?ip=117.219.113.30](http://www.spamhaus.org/query/bl?ip=117.219.113.30)]

---

### Post by lisati on 2012-04-08
Did you read the information at the Spamhaus site? It gives a reason for Google to return the error message that it did instead of accepting the email.

You will likely need to set Postfix to send outgoing mails through your ISP's smarthost. Have a look here: [http://www.dnsexit.com/support/mailrelay/postfix.html](http://www.dnsexit.com/support/mailrelay/postfix.html)

---

### Post by deepakdeshp on 2012-04-08
> **lisati said:**
> You will likely need to set Postfix to send outgoing mails through your ISP's smarthost. Have a look here: [http://www.dnsexit.com/support/mailrelay/postfix.html](http://www.dnsexit.com/support/mailrelay/postfix.html)

I followed all the steps in the link quoted in this post by lisati. Even before I had followed the steps the mail had stopped raching my spam folder in Google. It is not reaching google at all now. The mail.log file is


```
Apr  8 12:49:25 ubuntu postfix/pickup[3579]: 27BC27F50B: uid=1000 from=<tejas>
Apr  8 12:49:25 ubuntu postfix/cleanup[3661]: 27BC27F50B: message-id=<20120408164925.27BC27F50B@ubuntu.tejas.com>
Apr  8 12:49:25 ubuntu postfix/qmgr[3580]: 27BC27F50B: from=<tejas@ubuntu.tejas>, size=334, nrcpt=1 (queue active)
Apr  8 12:49:25 ubuntu postfix/pipe[3665]: 27BC27F50B: to=<deepakdeshp@gmail.com>, relay=dovecot, delay=0.24, delays=0.15/0.01/0/0.09, dsn=2.0.0, status=sent (delivered via dovecot service)
Apr  8 12:49:25 ubuntu postfix/qmgr[3580]: 27BC27F50B: removed
```

The mail neither seems to bounce nor reach gmail. Are there any other logs that I could check?

---

### Post by deepakdeshp on 2012-04-09
> **lisati said:**
> 
You will likely need to set Postfix to send outgoing mails through your ISP's smarthost. Have a look here: [http://www.dnsexit.com/support/mailrelay/postfix.html](http://www.dnsexit.com/support/mailrelay/postfix.html)

It seems I need to subscribe to dnsexit mail relay service after paying their charges which I had not done. Instead I just put the name of my server in the dnsexit link above,  which is wrong as my server on which my site is hosted isnt a mail forwarder.

I had set hostname host1 and host2 on 2 of my Ubuntu 10.04  servers on my intranet. I was trying to send mail from user1@host1 to user1@host2, but the mail bounced. I had added both host1 and host2 in the /etc/hosts files of both the hosts. Any suggestions will be greatly appreciated.

---

### Post by Bushflyr on 2012-04-09
I'm a total n00b and not 100% sure what you're trying to do, but I got my server to send me emails by following [THESE INSTRUCTIONS]("http://www.cecilieokada.com/blog/web-development/sending-email-from-localhost-using-msmtp-with-gmail/"). I have a throwaway gmail account that it sends through. My MSMTP file is like this: ```

defaults tls on 
tls_starttls on 
tls_trust_file /etc/ssl/certs/ca-certificates.crt   
account default host smtp.gmail.com 
port 587 
auth on 
user username(at)gmail.com 
password mypass 
from username(at)gmail.com 
logfile /var/log/msmtp.log

```

There's more info [HERE]("http://ubuntuforums.org/showthread.php?p=11792720#post11792720") and in the first page under section 11.

---

### Post by deepakdeshp on 2012-04-12
> **Bushflyr said:**
> I'm a total n00b and not 100% sure what you're trying to do, but I got my server to send me emails by following [THESE INSTRUCTIONS]("http://www.cecilieokada.com/blog/web-development/sending-email-from-localhost-using-msmtp-with-gmail/"). 

I am trying to set up a mail server which will deliver mails from my local host to the internet addresses like gmail and yahoo etc. The mails will be generated on my local host and then should be delivered in to POP3 clients like Thunderbird.

Your solution I feel does not contain the mail server , In my case I am using Postfix, Dovecot and mysql.

---

### Post by SeijiSensei on 2012-04-12
> from=<tejas@ubuntu.tejas>

You can't just make up a top-level domain like that.  You have to use a proper fully-qualified domain name that you have legitmate rights to use.  No well-managed mail server will accept mail with a From address that doesn't have a domain portion that resolves in the domain name service.

```

[seiji@host]$ host -t any ubuntu.tejas
Host ubuntu.tejas not found: 3(NXDOMAIN)

```

---

### Post by lisati on 2012-04-12
> **deepakdeshp said:**
> It seems I need to subscribe to dnsexit mail relay service after paying their charges which I had not done. Instead I just put the name of my server in the dnsexit link above,  which is wrong as my server on which my site is hosted isnt a mail forwarder.


That sounds unnecessarily complicated and expensive to me. The kind of thing I had in mind was to configure postfix to connect to your ISP's server in a manner that, as far as your ISP is concerned, it behaves similarly to what would happen when you're using an email client like Evolution, Thunderbird or, perish the thought, Outlook. 

Post 2 of [this thread]("http://ubuntuforums.org/showthread.php?t=1007814") is similar to what I had in mind.

---

### Post by deepakdeshp on 2012-04-13
> **SeijiSensei said:**
> You can't just make up a top-level domain like that.  You have to use a proper fully-qualified domain name that you have legitmate rights to use.  No well-managed mail server will accept mail with a From address that doesn't have a domain portion that resolves in the domain name service.

```

[seiji@host]$ host -t any ubuntu.tejas
Host ubuntu.tejas not found: 3(NXDOMAIN)

```

What I understand is I will register a domain name at Godaddy, get a static external ip for my server, assign the static  ip to my server and tie up the Godaddy domain name which I registered with this ip. After this I should be able to send mails.

---

