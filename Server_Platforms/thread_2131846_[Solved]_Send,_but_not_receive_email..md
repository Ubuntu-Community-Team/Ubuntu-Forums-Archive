---
title: "[Solved] Send, but not receive email."
date: 2013-04-03
forum: Server Platforms
---

### Post by tiagovieira on 2013-04-03
I followed the tutorial:

[http://www.howtoforge.com/perfect-se...ot-ispconfig-3](http://www.howtoforge.com/perfect-se...ot-ispconfig-3)

To configure my Ubuntu 12.04 VPS Server, the mail server sending this email only but do not receive any email provider.

What might be happening?

/etc/postfix/main.cf
[http://pastebin.com/CXM215vk](http://pastebin.com/CXM215vk)

/etc/postfix/master.cf
[http://pastebin.com/zFVskBTx](http://pastebin.com/zFVskBTx)

mailq:
```
[FONT=Ubuntu Mono]Mail queue is empty[/FONT]
```

telnet mail.techmall.com.br 25
```
root@server:~# telnet mail.techmall.com.br 25Trying 198.199.65.44...
Connected to techmall.com.br.
Escape character is '^]'.
220 server.techmall.com.br ESMTP Postfix (Ubuntu)
QUIT
221 2.0.0 Bye
Connection closed by foreign host.
```

iptables -L
[http://pastebin.com/jz5XjLN2](http://pastebin.com/jz5XjLN2)


Thanks

---

### Post by sanderj on 2013-04-03
Looks good to me:

```
sander@appelboor:~$ host techmall.com.br
techmall.com.br has address 198.199.65.44
techmall.com.br mail is handled by 10 mail.techmall.com.br.techmall.com.br.
techmall.com.br mail is handled by 1 mail.techmall.com.br.techmall.com.br.
sander@appelboor:~$ 
```

(BTW: the double MX is not correct. And the FQDN looks strange, ugly and/or incorrect ... maybe you forgot a dot at the end of the MX FQDN name?)

and mail is accepted:


```

sander@appelboor:~$ echo "Hello, this is a test" | mailsend -smtp mail.techmall.com.br.techmall.com.br -f blabla@gmail.com -t root@techmall.com.br -sub Testing -v
Connecting to mail.techmall.com.br.techmall.com.br:25
libmsock: using getaddrinfo
 AF_INET IPv4
 IPv4 address: 198.199.65.44
 EINPROGRESS=115,EWOULDBLOCK=11
 connect(): socket=3,rc=-1, errno=115
 Try socket 3
[S] 220 server.techmall.com.br ESMTP Postfix (Ubuntu)
[C] EHLO localhost
[S] 250-server.techmall.com.br
[S] 250-PIPELINING
[S] 250-SIZE 10240000
[S] 250-VRFY
[S] 250-ETRN
[S] 250-STARTTLS
[S] 250-AUTH PLAIN LOGIN
[S] 250-AUTH=PLAIN LOGIN
[S] 250-ENHANCEDSTATUSCODES
[S] 250-8BITMIME
[S] 250 DSN
[C] MAIL FROM: <blabla@gmail.com>
[S] 250 2.1.0 Ok
[C] RCPT TO: <root@techmall.com.br>
[S] 250 2.1.5 Ok
[C] DATA
[S] 354 End data with <CR><LF>.<CR><LF>
Subject: Testing
From: blabla@gmail.com
Date: Wed, 03 Apr 2013 07:36:08 +0200
To: root@techmall.com.br
X-Mailer: @(#) mailsend v1.17b4 (Unix)
X-Copyright: GNU GPL. It is illegal to use this software for Spamming

[C] Hello, this is a test

[C] .
[S] 250 2.0.0 Ok: queued as 441E3121110
[C] QUIT
[S] 221 2.0.0 Bye
Mail sent successfully
sander@appelboor:~$

```

---

### Post by tiagovieira on 2013-04-03
Really the FQDN this with duplicate field, I do not know why. In my setup the DNS MX Records this only "mail.techmall.com.br."


Still not getting any email, is it any configuration of ISPConfig? For I am creating email accounts for it.

---

### Post by sanderj on 2013-04-03
Is 198.199.65.44 your system? If so ... you've got mail in the mailbox of "root" ... check that.

If not: correct your MX settings ...

---

### Post by tiagovieira on 2013-04-03
Checked and has no email. And yes, this is my server IP.

I left only one address MX with priority 1, but not specified in the "host techmall.com.br"


Reinciei postfix and keeps me returning the duplicate MX yet.

---

### Post by darkod on 2013-04-03
Where is the domain registered? I think you will need to go into the registrars control panel and tell it to use your DNS server as nameserver. Otherwise I'm not sure any configuration you create for the domain is applied.

Also, ISPConfig might not have created everything correctly. That's why GUI tools are rarely used on servers, sometimes they use config files differently. I remember a case few weeks ago when the guy used ISPConfig to create DNS configuration and the program didn't create the A records necessary. So we spent a lot of time troubleshooting what went wrong until he found it.

Make sure you have the hosts correctly, and everything.

---

### Post by tiagovieira on 2013-04-03
As I put earlier in the post, I followed a tutorial for configuring the server, everything is working correctly, only the email that I get.


The domain is hosted by an institution in Brazil (ondeu I live) and it takes a while to update DNS. But this where I put my VPS MX Records in the entire address is not? "mail.techmall.com.br"? Or just "mail"? For me it seems that this is now adding the ". Techmall.com.br" automatically, as seen in "host techmall.com.br"


The ISPConfig is creating all Maildir / to the emails that I'm creating.

---

### Post by darkod on 2013-04-03
But what else is working correctly? The DNS is the most important part. You can send outgoing email with postfix without any DNS config and without even a real registered domain. I've done it with local test domain at home.

But when someone tries to send you email, the DNS service has to be able to find your server to deliver it. That part is obviously not working. Which points to DNS issue.

If you use the control panel of the institution, you can simply make the mail host poiting to your public IP, and the MX record to point to the mail host. You never need your own DNS.

If you do want to use your own DNS, in most cases you have to set in the institution control panel to forget about its own nameservers and to use your nameservers as main for that domain. And you will have the mail host and MX records defined in your DNS setup.

---

### Post by tiagovieira on 2013-04-03
Got it.


I did the following:




My VPS is in digitalocean.com, they provided the DNS:


ns1.digitalocean.com
ns2.digitalocean.com
ns3.digitalocean.com


I went where my domain is hosted and put these addresses as DNS. In the control panel digitalocean.com signed up and registered my domain MX Records as the "mail.techmall.com.br."

The DNS configuration as follows in this control panel digitalocean.com:

**Domain:**
techmall.com.br

**A Records**
Hostname: @
IP Address: 198..199.65.44

**CNAME Records**
Hostname(techmall.com.br): www
Hostname: @
Hostname(techmall.com.br): *
Hostaname: @

**MX Records**
Priority: 1
Hostanem: mail.techmall.com.br

**TXT Records**
nothing

**SRV Records**
nothing

**NS Records**
NS1.DIGITALOCEAN.COM
NS2.DIGITALOCEAN.COM
NS3.DIGITALOCEAN.COM



The DNS is being pointed at my site, because the site is working properly.

---

### Post by Cheesemill on 2013-04-03
You have an MX record that points to mail.techmall.com.br, but you don't have a record that resolves mail.techmall.com.br to an IP address.

You need to add an A record that points mail.techmall.com.br to your IP address.

---

### Post by tiagovieira on 2013-04-03
Ok, I believe this was the same problem. Now when I send an email it returns me with the following content:

[FONT=arial]This is the mail system at host [/FONT][server.techmall.com.br]("http://server.techmall.com.br/")[FONT=arial].[/FONT]

[FONT=arial]I'm sorry to have to inform you that your message could not[/FONT]
[FONT=arial]be delivered to one or more recipients. It's attached below.[/FONT]

[FONT=arial]For further assistance, please send mail to postmaster.[/FONT]

[FONT=arial]If you do so, please include this problem report. You can[/FONT]
[FONT=arial]delete your own text from the attached returned message.[/FONT]

[FONT=arial]                   The mail system[/FONT]

[FONT=arial]<[/FONT][EMAIL="vendas@techmall.com.br"]vendas@techmall.com.br[/EMAIL][FONT=arial]>: unknown user: "vendas"[/FONT]

[FONT=arial]Final-Recipient: rfc822; [/FONT][EMAIL="vendas@techmall.com.br"]vendas@techmall.com.br[/EMAIL]
[FONT=arial]Original-Recipient: [/FONT][EMAIL="rfc822%3Bvendas@techmall.com.br"]rfc822;vendas@techmall.com.br[/EMAIL]
[FONT=arial]Action: failed[/FONT]
[FONT=arial]Status: 5.1.1[/FONT]
[FONT=arial]Diagnostic-Code: X-Postfix; unknown user: "vendas"

[/FONT]What can it be now? I'm creating the emails by ISPConfig.




Thank you! We're almost solving ... hehehe

---

### Post by tiagovieira on 2013-04-03
Solved. I was with my domain in mydestination in / etc / postfix / main.cf retired and is working.


Now this checked because this slow in sending and receiving emails.


Thank you all.

---

