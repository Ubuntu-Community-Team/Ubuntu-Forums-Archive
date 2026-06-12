---
title: "Courier SMTP Problem"
date: 2009-03-28
forum: Server Platforms
---

### Post by jonnale on 2009-03-28
Hello everyone,

I just set up an Ubuntu 8.10 server, which purpose is to act as a web server and e-mail server.

I have courier installed (courier-imap + courier-imap-ssl), and I also want to use courier as my smtp server (courier-mta and courier-mta-ssl).

I configured Courier (using the web admin gui) and installed squirrelmail for a webmail client. I configured squirrelmail, and it is running flawlessly. I can send mail, receive mail, etc. No problems whatsoever.

However, most of the people that will be using this server use Microsoft Outlook or Thunderbird. I tested both Outlook and Thunderbird, and although both can receive mail, neither can send mail.

So my first thought was to make sure telnet could connect. Telnet does connect on port 25 and 465, and I was even able to send an e-mail via telnet commands.

I then ran:
$lsof -i :25
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
couriertc 1397 daemon    3u  IPv6 497068       TCP *:smtp (LISTEN)

$ lsof -i :465
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
couriertc 1432 daemon    3u  IPv6 497107       TCP *:ssmtp (LISTEN)

When I try sending an e-mail via Thunderbird or Outlook, here is what is in /var/log/mail.log:

Mar 28 13:01:27 lucy imapd: LOGIN, user=jonnale, ip=[::ffff:66.24.215.191], port=[57210], protocol=IMAP

Thunderbird+outlook gives me the error that the SMTP server is rejecting connections. Also, Thunderbird+Outlook never even prompt me for my SMTP password. Does this mean I am not authenticating, despite it saying I am logging in in mail.log?

Any help or suggestions are greatly appreciated, this is very frustrating!

---

### Post by primaxx on 2009-03-28
Hello there, and welcome to the forum! :-)

I have actually never touched Courier, but after looking at this howto:
[http://theclimber.fritalk.com/post/2009/01/27/Tutorial-:-Setup-your-mail-server-(courier-imap-postfix-postgresql](http://theclimber.fritalk.com/post/2009/01/27/Tutorial-:-Setup-your-mail-server-(courier-imap-postfix-postgresql))
I would like to know the output of
```
$ authtest [email]email@example.com[/email] secretpassword
```

As far as I understand, the message you posted from mail,log just tells you that IMAP is working, it doesn't say anything about smtp.

---

### Post by jonnale on 2009-03-28
> **primaxx said:**
> 
I would like to know the output of
```
$ authtest [email]email@example.com[/email] secretpassword
```


$ authtest jonnale ^mypasswordhere^
Authentication succeeded.

Authenticated: jonnale  (system username: jonnale)
Home Directory: /home/jonnale
Maildir: (none)
Quota: (none)
Encrypted Password: ^long encryption here^
Options: (none)

I just checked this on our old e-mail server, and it prints the same results (the old server worked with tbird+olook).

---

### Post by jonnale on 2009-03-28
I think I found the problem.

The server is located on my school's campus. The way I was testing telnet was by sshing to a server on campus, and then running the telnet command. This works great.

However, when I try to telnet from the machine I am currently on, I cannot connect to the server.

So either:
a.) There is a setting I am missing to allow telnet from outside connections

or

b.) My college has telnet 25 disabled on the subnet the server is on. I am not sure why this would be the problem, seeing as the old mail server was located in the same room (same subnet).

---

### Post by primaxx on 2009-03-28
There might be another problem, and that is that your college's gateway/router routes traffic on port 25 to another computer than yours?

---

### Post by jonnale on 2009-03-28
> **primaxx said:**
> There might be another problem, and that is that your college's gateway/router routes traffic on port 25 to another computer than yours?

Yep, this is the problem.

Sigh, I worked on trying to fix this for like 6 hours! At least it was a good learning experience.

](*,)

:P

---

### Post by HermanAB on 2009-03-29
Generally there are two solutions:
1. Make an extra listener on the mail server so it can also receive mail on port 2525.
2. Use SMTP over SSL on port 465.

---

### Post by jonnale on 2009-03-29
> **HermanAB said:**
> Generally there are two solutions:
1. Make an extra listener on the mail server so it can also receive mail on port 2525.
2. Use SMTP over SSL on port 465.

From my home computer, I cannot even telnet to the server on port 465. However, if I ssh to a server on campus and then telnet on port 465, it works.

This server is also being used as a web server, and I CAN access that off campus.

hmm...

---

