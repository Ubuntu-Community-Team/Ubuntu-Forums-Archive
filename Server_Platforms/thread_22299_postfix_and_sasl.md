---
title: "postfix and sasl"
date: 2005-03-26
forum: Server Platforms
---

### Post by lee_connell on 2005-03-26
i have a problem.  i've got my email system all up and running.  i am using sasl with postfix to authenticate my users.  everything works locally even if i take my local network out of "mynetworks" with authenticating against postfix.

However ANY outside client/host cannot send email to my domain/email server.  for instance email from my hotmail account to my connell-tech.com server i just built returns an error:

Mar 26 23:00:07 localhost postfix/smtpd[3348]: connect from bay18-f7.bay18.hotmail.com[65.54.187.57]
Mar 26 23:00:07 localhost postfix/smtpd[3348]: NOQUEUE: reject: RCPT from bay18-f7.bay18.hotmail.com[65.54.187.57]: 554 <lee@connell-tech.com>: Recipient address rejected: Access denied; from=<lee_connell@hotmail.com> to=<lee@connell-tech.com> proto=ESMTP helo=<hotmail.com>
Mar 26 23:00:07 localhost postfix/smtpd[3348]: disconnect from bay18-f7.bay18.hotmail.com[65.54.187.57]

I've attached main.cf

---

### Post by alastair on 2005-03-26
Err ... that config is still loopback only, no? i.e.

inet_interfaces = loopback-only

So .... this would seem like a good reason "hotmail.com" cannot send mail through it.  

Be very careful setting up a mail server and double check you are not an open relay.

---

### Post by lee_connell on 2005-03-27
Oops, wrong config file sorry.  Here is the real one.

---

### Post by alastair on 2005-03-27
You have :

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject

So, only allow a connection through SMTPD if SASL auth occurs.

How are you doing auth from a hotmail account? Is this something configurable in hotmail? How do do know auth is attempted?

I would try and look at the connection conversation in more detail i.e. look at :

debug_peer_list = <IP/doman>

and 

master.cf :
smtpd -v

Then look at the logs as the connection is made.

See : [http://www.postfix.org/DEBUG_README.html](http://www.postfix.org/DEBUG_README.html)

---

### Post by lee_connell on 2005-03-27
thanks for your help.  It looks like i was missing other commands in main.cf.  I didn't want hotmail to have to auth if it were sending to the local domain.

broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_client_restrictions = permit_mynetworks, reject_rbl_client relays.ordb.orgsmtpd_sender_restrictions = permit_mynetworks
smtpd_data_restrictions = reject_unauth_pipelining, permit

Also:  do you know what user is trying to read from /var/run/saslauthd from the cyrus server?  i added cyrus to the sasl group and it still says permission denied on that directory i can temporarily fix it by adding +x to that directory but when ever saslauthd starts back up it changes permissions back and i would assume this is a good reason.  How can i tell which user is trying to access that dir?

Lee

---

### Post by alastair on 2005-03-28
I'm glad it is working but am not sure why - looking at your config. Anyway .... I use and like Postfix but have never used SASL with it.

I would :

a) Look at any installed Postfix docs e.g. anything under :

/usr/share/doc/Postfix* 

b) Check the postfix docs on its homepage i.e.

[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

---

### Post by lee_connell on 2005-03-28
smtpd_sender_restrictions = permit_mynetworks

i would think that's the line that made it work.  I will play with it later to see which command actually did make it work.  I added the user cyrus to sasl group using:

usermod -Gsasl cyrus, i guess that didn't work.  i then went into webmin and added cyrus to group sasl and everything started to work the way it should as far as permissions on the pipes goes.

---

