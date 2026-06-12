---
title: "postfix problem"
date: 2019-04-09
forum: Server Platforms
---

### Post by tomdf on 2019-04-09
Hello guys, 

i have a webserver running with apache 2 postfix and ubuntu 18.04

in the /var/log/syslog i get the following error.

```

[COLOR=#202124][FONT=Roboto]Apr  9 21:40:03 server1 postfix/smtps/smtpd[6633]: connect from localhost[127.0.0.1][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr  9 21:40:03 server1 postfix/smtps/smtpd[6633]: SSL_accept error from localhost[127.0.0.1]: lost connection[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr  9 21:40:03 server1 postfix/smtps/smtpd[6633]: lost connection after CONNECT from localhost[127.0.0.1][/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Apr  9 21:40:03 server1 postfix/smtps/smtpd[6633]: disconnect from localhost[127.0.0.1] commands=0/0[/FONT][/COLOR]

```

can anyone help me with that problem maybe?

thanks in advance for your help

Tom

---

### Post by SeijiSensei on 2019-04-09
Use port 25 (SMTP). You don't need SSL for a communication between the machine and itself.

Do you get a prompt if you type "telnet localhost 25" on the server?

---

### Post by tomdf on 2019-04-09
Hi,
thanks for your answer.
if i type telnet localhost 25 i get:

```

[COLOR=#202124][FONT=Roboto]Trying 127.0.0.1...[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Connected to localhost.[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]Escape character is '^]'.[/FONT][/COLOR]

```
how can i use port 25 only for communication between the machine and itself.
i am running domains and webspace so a secure ssl is needed at least for the domains. 

thank you for helping me

---

### Post by SeijiSensei on 2019-04-09
I assume you're trying to send mail from a web application.  The transaction between the application and Postfix takes place internally on the server over the "localhost" interface. It has nothing to do with how the message is eventually sent to remote servers.  That depends on how Postfix is configured as a client. In essence, the application forwards the mail to Postfix in clear text, and Postfix may or may not use SSL to relay the message to the remote server depending on how it is configured. 

If you've never looked at the full headers of an email, you should.  You'll see a succession of "Received:" headers marking each step along the way between the origin of the message and its final delivery.  I suggest looking at a variety of messages in your inbox if you've never done this before.

Securing web sites requires certificates as I'm sure you know.  But that is entirely independent of mail.

I don't know what you did to tell the application to use SSL, but you probably have the application configured to talk to localhost on port 465.  Use localhost and port 25 instead.

---

### Post by tomdf on 2019-04-13
Hi,
thanks for your kind answer.
on this VPS there is only running ISPConfig and Zabbix as application. 
Is there a way to find out which user is using the process ID or how to find out which program tries to send an email?
```

Apr 13 16:30:02 server1 postfix/smtps/smtpd[8578]: connect from localhost[127.0.0.1]
Apr 13 16:30:02 server1 postfix/smtps/smtpd[8578]: SSL_accept error from localhost[127.0.0.1]: lost connection



```

---

### Post by SeijiSensei on 2019-04-14
```
ps aux
```

Will show the usernames each proceess runs under.

If you're sending mail from a web app, the likely user is www-data the pseudo-user who owns the Apache process.

---

### Post by LHammonds on 2019-04-16
postfix is a full mail server.  If you are just wanting to send email from apache, you can configure it to use a lightweight mail-sending application to an existing "full" mail server.  If you just want to add the ability to send email, it is not a good idea to install a full mail service to do that...unless you are planning on it receiving email too...but mail server setups are not typically "simple" to install and require a lot of work to do properly.  If I needed a full mail server, I would still set it up on a separate server and configure my web app to point to it.

Here is how I have configured my apache web servers so I can send mail from PHP applications and from the command-line: [http://hammondslegacy.com/forum/viewtopic.php?f=40&t=257](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=257)

There are many different ways to accomplish this.  I did it this way and documented how I did it so I can repeat the process later. ;)

LHammonds

---

### Post by tomdf on 2019-04-21
thanks for your quick answer and sorry i am so late in reply.
i need postfix because i have some domains running on the server who need to send email ;)

this is the connect i want to find out which user is using the process id. i send again because the id changed:

```

Apr 21 18:50:02 server1 postfix/smtps/smtpd[28335]: SSL_accept error from localhost[127.0.0.1]: lost connection
Apr 21 18:50:02 server1 postfix/smtps/smtpd[28335]: lost connection after CONNECT from localhost[127.0.0.1]
Apr 21 18:50:02 server1 postfix/smtps/smtpd[28335]: disconnect from localhost[127.0.0.1] commands=0/0



```

with ps aux i get the following information about this process id:

```

postfix  28335  2.0  0.1 100464 10264 ?        S    18:55   0:00 smtpd -n smtp -

```

What i can see is that postfix is running this process id.

Is there a possibility that i can see which program tries to send the email from localhost with SSL?

thanks in advance for your patience.

---

### Post by SeijiSensei on 2019-04-21
As I said before, it's almost certainly the "www-data" user that originates the mail if it is coming from a web application.

smtpd is the Postfix process that accepts mail.

---

