---
title: "mail sending  problem"
date: 2010-07-23
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-23
I am having a small problem.
I have a computer in a domain on which some applications need to send email to the outside users.The SMTP server is not in my control.It is managed by some other persons.
In my application I need to enter IP of SMTP,Port,My username and password.
After this the documentation says it will work i.e. the application should be able to send emails.
I did as the documentation says but sending of test emails from the application failed.
There is an option in the application to test the SMTP settings
and it said that SMTP mail sending failed.
Here is the [link]("http://www.thoughtworks-studios.com/mingle/2.3/help/configure_smtp_connection.html")
Is this way of sending emails wrong or do I need to do some thing else on my part so that my application can send emails.

---

### Post by lisati on 2010-07-23
Sometimes email servers require you to connect through another port instead of the "standard" port 25. One common alternative is 587.

---

### Post by tapas_mishra on 2010-07-23
1. From the computer where application is running, opened a command prompt 
2. Typed

telnet <smtpserver> 25 
3.  get a message that says 
 that starts with the number 220 followed by a greeting. 
4. Typed

HELO <smtpserver> 
5. Saw a message starting with the number 250  (Does That means every thing is Ok upto here)
6. Typed in the following next 

MAIL FROM:noreply@my.application.instance.com 
7. Saw message starting with the number 250. (Does That means every thing is Ok upto here)
8. Then to send a notification to, typed 
RCPT TO:email@example.com 
9.  see a message starting with the number 250. (Does That means every thing is Ok upto here)
10. Type

DATA 
11.  see a message starting with the number 354 followed by instructions to enter the email message. (Does That means every thing is Ok upto here)
12. Type

Test message 
.

Note that the last line contains a period (dot) alone. (This signals that I  am done typing the message.)
 to end the message sequence the server informed me about in step 11. I was not clear with <CRLF>.<CRLF>

 I tried pressing Enter followed by a dot and then again pressing enter
got an error number 503.Googled that but was of no use so not clear as to if what does <CRLF>

means.

But some how when I typed exit was able to exit and got an email in the account.

---

### Post by cdenley on 2010-07-23
What kind of mail server? Are you sure you are sending "<CRLF>.<CRLF>" and not "<LF>.<LF>"?
```

nc -C <smtpserver> 25

```

---

### Post by tapas_mishra on 2010-07-23
> **cdenley said:**
> What kind of mail server?

From the telnet reply I get message
```

Microsoft ESMTP MAIL Service

```So I it is  MS based thing.
The machine on which application is running is a Ubuntu 10.04 server.
What exactly do you want to know in this.
> **cdenley said:**
> 
 Are you sure you are sending "<CRLF>.<CRLF>" and not "<LF>.<LF>"?

This thing I could not understand your question
after I got a message in Step 

Queued mail for delivery after Step 11
I pressed enter and a dot and then again a enter after which I got following error
```

500 5.3.3 Unrecognized command

```So pressing enter followed by a dot (.) and then enter did not worked.I guess what do you feel.
> **cdenley said:**
> 
nc -C <smtpserver> 25

Ok I did 
```

  nc -C <smtp> 25

```Got following
```

220 smtp Microsoft ESMTP MAIL Service, Version: 6.0.3790.3959 ready at  
```So what next to check?

---

### Post by cdenley on 2010-07-23
The "-C" option with netcat should ensure carriage returns are sent. As you probably know, Linux systems typically don't use carriage returns, but Windows sometimes expects it. I'm not sure if telnet sends them. Do exactly what you did with telnet, except with the netcat command I gave. A period between two carriage return and line feed sequences should end the data.

---

### Post by tapas_mishra on 2010-07-23
I repeated the above steps with nc -C option and at the end of Carridge returns got the same response.

.
500 5.3.3 Unrecognized command

I pressed enter 2 times with a . between them is there any thing else I need to test in.

---

### Post by cdenley on 2010-07-23
> **tapas_mishra said:**
> I repeated the above steps with nc -C option and at the end of Carridge returns got the same response.

.
500 5.3.3 Unrecognized command

I pressed enter 2 times with a . between them is there any thing else I need to test in.

So you type "DATA", it gives a 354 response, then you type:
"Test message<enter>.<enter>"
then it immediately gives you a 500 response? That doesn't make any sense to me, and if that is correct, I am out of ideas.

---

### Post by tapas_mishra on 2010-07-23
> **cdenley said:**
> So you type "DATA", it gives a 354 response, then you type:
"Test message<enter>.<enter>"
then it immediately gives you a 500 response? That doesn't make any sense to me, 

Yes this is happening.The user whose email was used in FROM MAIL and RCPT MAIL was able to get the DATA
"Test message<enter>.<enter>"

At least mail server is sending mails when I telnet or use nc.
Even I am not getting as why the application is failing to send emails.

---

