---
title: "exim 503 sender not yet given"
date: 2008-11-24
forum: Server Platforms
---

### Post by bluethundr on 2008-11-24
Hi Guys, 

 I have googled my head off, lurked endlessly on IRC and have not yet been able to get any help with this problem.

 I recently installed exim 4.2 onto Ubuntu 8.10 and am getting no love. 

 I was, but am no longer able to send mail messages to the local domain. I am also not able to send email to anyone off my domain.

 I am able to telnet to mail.mydomain.com 25 from another machine on my network and issue commands to the MTA.

 But if I issue the commands:

 rcpt to:<user@externaldomain.com>

 The response I get is "503 sender not yet given"

 Also, if I try to issue the command:

 rcpt to:<user@mylocaldomain.com>

 I get the same response. 503 Sender not yet given.

 In addition, I have successfully setup evolution to use my own exim server and I am able to receive mail at my own homebrew address from anywhere on the Internet. That tells me that my MTA is doing it's job, at least partially.

 But sending mail from evolution does not work. I get a "Mail cannot relay" mistake.

 Ideally I would like to send email to anywhere on the Internet without using an external smarthost. Yet, I want to ensure that the mail system is secure without allowing to the extent I can spammers to use my machine as a relay. 
 
 Security is desired. But not allowing to send external emails at ALL? THAT'S just overkill!

Thanks in advance!
-t

---

### Post by CrucifiedEgo on 2008-11-24
Are you issuing HELO and MAIL FROM: before RCPT TO:?  i get a 503 response from postfix if i just send RCPT TO: without either.

---

### Post by bluethundr on 2008-11-24
Thanks for the speedy reply! No I am not using those commands in front of the rcpt command. I will give that a try when I get home tonight (telnet and ssh is blocked at my job). 

But please note that not only does this appear to not work, I am not able to send mail externally from evolution using my homebrew mail server. I get a relay error message (sorry, I can't remember the _exact_ relay error message, as I mentioned I'm at work).

I suspect this is a config file issue. Also, I noticed a number of different config files in my /etc/exim4 directory. I'm not sure which one I need to be working with.

Any assistance here would be appreciated.
-t

---

### Post by bluethundr on 2008-11-24
Okay, so I got home and headed straight to my laptops to test the mail setup.

This is the result of the commands I have input. 


---------------------------------


myforeignhost:~ bluethundr$ telnet mail.mydomain.com 25
Trying 123.456.789.1...
Connected to mail.mydomain.com.
Escape character is '^]'.
220 nylsd ESMTP Exim 4.69 Mon, 24 Nov 2008 18:58:27 -0500
ehlo localhost
250-mydomain Hello desu-desu7b8.dyn.optonline.net [123.456.789.1]
250-SIZE 52428800
250-PIPELINING
250-STARTTLS
250 HELP
mail from:<bluethundr@mydomain.com>
250 OK
rcpt to:<bluethundr@mydomain.com>
250 Accepted
rcpt to:<bluethundr@foreigndomain.com>
550 relay not permitted


--------------------------------------------

So as you can see, I can go to another laptop on my network, telnet into the machine that is hosting my mail server at port 25 and issue MTA commands. 

So I assume that the mail from and rcpt commands are simulated mail commands, not actually sending and receiving messages.

So, it appears from this output that my MTA is more than happy to deliver mail to my local account, but is not permitting relays off the network.

But HOLD THE PHONE!!! I tried issuing the command:

exim -odq [email]bluethundr@foreigndomain1.com[/email] [email]bluethundr@foreigndomain2.com[/email]

I just checked my foreigndomain1 account and lo and behold I had a message with no subject from my new toy mail server!

foreigndoman2 however, has yet to receive the test message.

But STILL if I try to send messages from evolution I get

------------------------

Error while performing operation.

RCPT TO <bluethundr@foreigndomain1.com> failed: relay not permitted
#this is the same domain that DID receive a message from the exim -odq command

RCPT TO <bluethundr@foreigndomain2.com> failed: relay not permitted
#this is the next domain run with the exim -odq command and did NOT receive the test message as of yet...(and yes I did look in the spam folder! I'm expecting that I haven't gotten my static IP yet.. next week for that!)

-----------------------------------------------


HELP!!!! :confused:

---

### Post by bluethundr on 2008-11-24
woops! Anonymization FAIL! :lolflag:

---

### Post by CrucifiedEgo on 2008-11-24
This is 100% expected.  MAIL FROM and RCPT TO are the commands that SMTP clients and servers communicate with.  What's happening here is your server is accepting your request to send mail to mydomain.com since it's considered "local" delivery.  However, it's denying you relay access to send to anywhere else.  This is good, so spammers don't user your mailserver to send out millions of messages and get you blacklisted.  The reason the command line mail works is that you're doing it from localhost, which is usually trusted.  I'm not an expert on exim, perhaps someone else (maybe even google) can show you how to enable SMTP Authorization(Login via smtp) in exim.  It may already be enabled -- try enabling SMTP Auth in your mail client and go from there.

---

### Post by bluethundr on 2008-11-24
thanks.. the best resource I found so far is this guide:

[http://www.debian-administration.org/articles/280](http://www.debian-administration.org/articles/280)

and I followed all the steps in it to the letter and STILL can't send to external addresses. Any further advice?

:(

---

### Post by bluethundr on 2008-11-24
hmmmmm... okay, so as I said I performed everything in the link. 

Then I went to my evolution client and enabled the site certificate. 

Then it tries to send... and send.. and send... and send.. and send.. 

And just takes bloody forever and finally times out.

And if I telnet in and try to issue a rcpt to:<bluethundr@foreignhost.com> it still refuses to relay.

---

### Post by bluethundr on 2008-11-25
I think I may have smtp auth disabled but I am not sure. 

I tried to test with swaks.

swaks --tls --auth-user --to [email]bluethundr@gmail.com[/email] --server mail.nylsd.com


and when it asks me to authenticate, authentication fails. This is the output I get:

----------------------------
Username: bluethundr
Password: mYpAsSiNcLeArTxT
=== Trying mail.nylsd.com:25...
=== Connected to mail.nylsd.com.
<-  220 nylsd ESMTP Exim 4.69 Tue, 25 Nov 2008 05:13:20 -0500
 -> EHLO nylsd
<-  250-nylsd Hello desu-desub8.dyn.optonline.net [123.456.789.1]
<-  250-SIZE 52428800
<-  250-PIPELINING
<-  250-STARTTLS
<-  250 HELP
 -> STARTTLS
<-  220 TLS go ahead
=== TLS started w/ cipher DHE-RSA-AES256-SHA
 ~> EHLO nylsd
<~  250-nylsd Hello ool-457d77b8.dyn.optonline.net [123.456.789.1]
<~  250-SIZE 52428800
<~  250-PIPELINING
<~  250-AUTH PLAIN
<~  250 HELP
 ~> AUTH PLAIN AGJsdWV0aHVuZHIAaSQ3IW5LNHU=
<~* 435 Unable to authenticate at present
*** No authentication type succeeded
 ~> QUIT
<~  221 nylsd closing connection
=== Connection closed with remote host.
----------------------------------------------------

how can I most easily determine if I have SMTP AUTH installed and turned on, and how can I correct it if it's not?

---

