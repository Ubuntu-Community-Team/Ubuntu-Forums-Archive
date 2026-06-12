---
title: "SMTP issue"
date: 2009-11-23
forum: Server Platforms
---

### Post by guessswh0 on 2009-11-23
Hello,

I followed this guide ([https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)) on setting up postfix, and everything works great.  I installed courier, and configured it correctly.  I am able to receive e-mail over pop3 no problem.  I also installed a webmail client (squirrelmail).  That client is able to send and receive e-mail with no issues at all.

I am having issues with trying to use a regular mail client (outlook, Apple Mail, thunderbird).  The clients can connect to the server via POP3 and download their mail.  However, they are unable to send mail.

I have done the telnet localhost 25 when logged on the server, and all the correct "responses" were shown.  Anyone have any ideas?  This is starting to bother me.

Thanks for the help.

---

### Post by gombadi on 2009-11-23
> 
However, they are unable to send mail.

You do not say what the problem is when they try and send emails.

> 
have done the telnet localhost 25 when logged on the server, and all the correct "responses" were shown


This will test a connection from the server to the same server. It would be better to telnet from one of the client machines to the email server on port 25 to see if you can connect.

---

### Post by JillK on 2009-11-23
Yup, check if the port is open. Can you send emails from outside the server's network? (ie. from home)

Sometimes (my case) the ISP blocks port 25, so you could try SMTP on port 26 and see if that works.

> **guessswh0 said:**
> [U]Hello,

[COLOR="#444444"]I followed this guide ([https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)) on setting up postfix, and everything works great.  I installed courier, and configured it correctly.  I am able to receive e-mail over pop3 no problem.  I also installed a webmail client (squirrelmail).  That client is able to send and receive e-mail with no issues at all.

I am having issues with trying to use a regular mail client (outlook, Apple Mail, thunderbird).  The clients can connect to the [ubuntu dedicated server]("http://www.dedicated-server.net/hosting/tag/ubuntu/") via POP3 and download their mail.  However, they are unable to send mail.

I have done the telnet localhost 25 when logged on the server, and all the correct "responses" were shown.  Anyone have any ideas?  This is starting to bother me.

Thanks for the help.[/COLOR][/U]

---

### Post by guessswh0 on 2009-11-23
I cannot telnet in from the outside.  This is not a local server, this is a vps hosted elsewhere.  I have checked firewall rules and all traffic intended for port 25 is allowed to pass through.  When on the server I can telnet to localhost on port 25, but not from outside computer.

When it tries to connect to the smtp server, it just never does.  It sticks at trying for about a minute, and then says it couldn't connect.

---

### Post by JillK on 2009-11-23
what does the web host say?

---

