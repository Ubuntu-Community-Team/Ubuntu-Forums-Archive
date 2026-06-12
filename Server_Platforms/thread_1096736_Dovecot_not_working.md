---
title: "Dovecot not working"
date: 2009-03-15
forum: Server Platforms
---

### Post by Jack1989 on 2009-03-15
Hi, I've installed Dovecot on my Ubuntu server. But I cannot receive any mail.

I use Roundcube mail and can login to the IMAP-server, I can connect to Dovecot via telnet both local and from a remote host.

Everything seems to work perfect, but when I send an email, I don't get it, and no error message ether. If i check the server at pingability.com I get an error.

What's wrong?

mx1.diehard.nu is going to the servers ip
MX record at diehard.nu is going to mx1.diehard.nu
ports: 143, 993

---

### Post by hictio on 2009-03-15
Ok, what is the [MTA](http://en.wikipedia.org/wiki/Mail_transfer_agent) on that server?
Have you tried if its running?
Have you tried if the SMTP port (25 TCP) is open on the server? (so it can actually receive emails?)

---

### Post by Jack1989 on 2009-03-15
I just read about MTA on the internet, and yes I have a MTA, it's Postfix and it's running, but if it's configured correctly, I don't know!

Isn't port 25 for sending emails? I cannot use this port, my ISP blocks it.

---

### Post by hictio on 2009-03-15
Are you handling the email for a domain?

> 
Everything seems to work perfect, but when I send an email, I don't get it, and no error message ether. If i check the server at pingability.com I get an error.


You mean send it from another box onto an address of your domain, or you mean sending the email from the same box that you are having the problems with Dovecot?

---

### Post by Jack1989 on 2009-03-15
Both, in the local network, outside the network, from [email]jackej@diehard.nu[/email] to [email]jackej@diehard.nu[/email] and from other domains.

Dovecot seems to work perfect, it could be Postfix, how can I test so it's configured right?

---

### Post by hictio on 2009-03-15
Cool, your domain does have an MX record:

```

% dig mx diehard.nu 

; <<>> DiG 9.3.5-P2 <<>> mx diehard.nu
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 48646
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;diehard.nu.                    IN      MX

;; ANSWER SECTION:
diehard.nu.             3600    IN      MX      1 mx1.diehard.nu.

;; AUTHORITY SECTION:
diehard.nu.             3600    IN      NS      ns3.loopia.se.
diehard.nu.             3600    IN      NS      ns4.loopia.se.

;; ADDITIONAL SECTION:
ns4.loopia.se.          67856   IN      A       194.9.95.245
ns3.loopia.se.          67856   IN      A       194.9.94.245

;; Query time: 464 msec
;; SERVER: 10.120.10.1#53(10.120.10.1)
;; WHEN: Sun Mar 15 19:58:32 2009
;; MSG SIZE  rcvd: 125

```

Which is good, but, then, I can't connect to your mail server to send email:

```

% telnet mx1.diehard.nu 25
Trying 83.254.146.142...
telnet: connect to address 83.254.146.142: Operation timed out
telnet: Unable to connect to remote host
% 

```

In order to receive emails for that domain (specially from the public internet), you have to have the SMTP port open; or set the MX record to point to another box/ domain that can do that.

That's for **receiving** emails.

For  **sending** emails from a box on your network, if you can't send emails directly from your own server (blocked ports, ISP restrictions) it is very usual to use its SMTP server as the proxy. That is, you don't send the email directly, but thru its server.
On Sendmail's MTA, that it's called 'SMART_HOST'.

---

### Post by Jack1989 on 2009-03-15
Thanks for the info, I use the ISP's SMTP server, so that's no problem.
Why do I need the SMTP port open to receive mails? And can I use another port instead?

Can I use this solution:
[http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=blockingisp#blockingisp](http://rimuhosting.com/support/settingupemail.jsp?mta=postfix&t=blockingisp#blockingisp)

I want to receive mail directly to the server, not via another mail account. I will do that too, but with an old account, with fetchmail.

EDIT:

I was going to add port 25 to my router, but it already was there, portforwarding to another computer in the network. The service name was "INCOMING", so maybe it works now! : )

---

### Post by Jack1989 on 2009-03-15
If I try to send an email, I get an error message: Undelivered Mail Returned to Sender.

That's different.

If I try to connect via telnet from my computer in the network:
```

jack@jack-laptop:~$ telnet mx1.diehard.nu 25
Trying 83.254.146.142...
Connected to mx1.diehard.nu.
Escape character is '^]'.
220 skysel-server ESMTP Postfix (Ubuntu)

```

I can connect local, but not from a remote host. Is that right? And how do I change it?

---

### Post by Jack1989 on 2009-03-16
It works now! Just added diehard.nu to main.cf and restarted.

Thanks for your help!

---

