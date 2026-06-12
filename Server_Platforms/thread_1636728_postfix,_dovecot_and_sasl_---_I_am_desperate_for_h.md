---
title: "postfix, dovecot and sasl --- I am desperate for help!"
date: 2010-12-03
forum: Server Platforms
---

### Post by schworak on 2010-12-03
I have followed the instructions at the following sites to the best of my abilities and still I don't get sasl authentication. It is driving me nuts!

[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)
[https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Here are the configuration segments that I have come up with for my config files. They look like they should work. The dovecot contig creates the socket right where it should and postfix doesn't complain but it doesn't deliver the proper auth headers either.

/etc/dovecot.conf: (copied/pasted comment lines removed)

auth default {
  mechanisms = plain login
  passdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb sql {
    args = /etc/dovecot/dovecot-sql.conf
  }
  user = root
  socket listen {
    client {
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
  !include_try /etc/dovecot/auth.d/*.auth
}



/etc/postfix/main.cf  (copied/pasted comment lines removed)

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_inet_interfaces permit_sasl_authenticated
smtpd_sasl_exceptions_networks = $mynetworks



I tried telnet but thought that the auth would be skipped because of the last line in my main.cf config. So I went to [http://www.wormly.com/test_smtp_server](http://www.wormly.com/test_smtp_server)

Here is what I get...

Resolving hostname...
Connecting...
SMTP -> FROM SERVER:
220 mail.schworak.com ESMTP Postfix (Ubuntu)
SMTP -> FROM SERVER: 
250-mail.schworak.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
[COLOR=Red]250-AUTH PLAIN LOGIN
[/COLOR]250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: [EMAIL="glenn@schworak.com"]glenn@schworak.com[/EMAIL]
SMTP -> FROM SERVER:
250 2.1.0 Ok
RCPT TO: [EMAIL="glenn@bestlittlehairhouse.info"]glenn@bestlittlehairhouse.info[/EMAIL]
SMTP -> FROM SERVER:
250 2.1.5 Ok
Sending Mail Message Body...
SMTP -> FROM SERVER:
354 End data with .
SMTP -> FROM SERVER:
250 2.0.0 Ok: queued as F0AC31C0576
Message completed successfully.



I expected this to fail because I am sending as if I am from an internal account but not from an internal IP address. I see the AUTH request in the transaction but it still lets me send the email. WHY????

Can I force all mail being sent from internal addresses to authenticate? In the test above I am sending from internal to internal email accounts. I tried it with an internal to external and it worked as expected. Here is the trace for that...


Resolving hostname...
Connecting...
SMTP -> FROM SERVER:
220 mail.schworak.com ESMTP Postfix (Ubuntu)
SMTP -> FROM SERVER: 
250-mail.schworak.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: [EMAIL="glenn@schworak.com"]glenn@schworak.com[/EMAIL]
SMTP -> FROM SERVER:
250 2.1.0 Ok
RCPT TO: [EMAIL="schworakgj@gmail.com"]schworakgj@gmail.com[/EMAIL]
SMTP -> FROM SERVER:
554 5.7.1 : Relay access denied
SMTP -> ERROR: RCPT not accepted from server: 554 5.7.1 : Relay access denied


Of course, I tried it from external to internal and that worked just fine as expected.

Resolving hostname...
Connecting...
SMTP -> FROM SERVER:
220 mail.schworak.com ESMTP Postfix (Ubuntu)
SMTP -> FROM SERVER: 
250-mail.schworak.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: [EMAIL="schworakgj@gmail.com"]schworakgj@gmail.com[/EMAIL]
SMTP -> FROM SERVER:
250 2.1.0 Ok
RCPT TO: [EMAIL="glenn@schworak.com"]glenn@schworak.com[/EMAIL]
SMTP -> FROM SERVER:
250 2.1.5 Ok
Sending Mail Message Body...
SMTP -> FROM SERVER:
354 End data with .
SMTP -> FROM SERVER:
250 2.0.0 Ok: queued as 339C11C0393
Message completed successfully.

Message sending failed.

Odd thing, even if I send from my phone with the correct user name/password set, all mail is rejected as being relayed.

There must be some settings that I am missing. I really need help understanding what I have missed in this process.

---

### Post by schworak on 2010-12-04
So very close!

Things are mostly working by setting this one item in /etc/postfix/main.cf
smtpd_recipient_restrictions = permit_sasl_authenticated reject_unauth_destination 


Here is my current status (internal/external refers to email address)

exteranl -> internal w/o authentication --- Sent (**[COLOR=DarkGreen]good[/COLOR]**)
internal (external IP) -> external w/o authentication --- Failed ([COLOR=DarkGreen]**good**[/COLOR])
internal (internal IP) -> external w/o authentication --- Failed ([COLOR=DarkGreen]**good**[/COLOR])
internal (internal IP) -> internal w/o authentication --- Sent (**[COLOR=DarkOrange]*I guess it is ok*[/COLOR]**)
 internal (external IP) -> internal w/o authentication --- Sent (**[COLOR=Red]very bad[/COLOR]**)
  internal (any IP) -> external with authentication --- Sent ([COLOR=DarkGreen]**good**[/COLOR])
  internal (any IP) -> internal with authentication --- Sent ([COLOR=DarkGreen]**good**[/COLOR])


[B][COLOR=Red]Now how to stop email from going to an internal mailbox to another internal mailbox without authentication? Especially when it is really coming from an external IP address?
[/COLOR][/B]

**[COLOR=DarkGreen]Any help would be greatly appreciated![/COLOR]**

---

### Post by HermanAB on 2010-12-04
Howdy,

This is why I gave up with Postfix years ago and rather use Citadel.  It installs in about 20 minutes and Just Works (TM).

---

### Post by schworak on 2010-12-04
> **HermanAB said:**
> Howdy,
This is why I gave up with Postfix years ago and rather use Citadel.  It installs in about 20 minutes and Just Works (TM).

Thanks but that doesn't help me configure postfix. It only offers me a way to replace it with a different program now that post fix is all set up (except this one issue)

I am sure the answer is related to SMTPD_SENDER_RESTRICTIONS but I am not understanding how to set it yet. The language on the postfix site is not very user friendly. Reads like a legal document.

---

### Post by schworak on 2010-12-05
SOLVED!

exteranl -> internal w/o authentication --- Sent (**[COLOR=DarkGreen]good[/COLOR]**)
internal (external IP) -> external w/o authentication --- [COLOR=Red]Failed[/COLOR] ([COLOR=DarkGreen]**good**[/COLOR])
internal (internal IP) -> external w/o authentication --- [COLOR=Red]Failed[/COLOR] ([COLOR=DarkGreen]**good**[/COLOR])
internal (internal IP) -> internal w/o authentication --- [COLOR=Red]Failed[/COLOR] ([COLOR=DarkGreen]**good**[/COLOR])
 internal (external IP) -> internal w/o authentication --- [COLOR=Red]Failed[/COLOR] (**[COLOR=DarkGreen]good[/COLOR]**)
  internal (any IP) -> external with authentication --- Sent ([COLOR=DarkGreen]**good**[/COLOR])
  internal (any IP) -> internal with authentication --- Sent ([COLOR=DarkGreen]**good**[/COLOR])

I am using Dovecot for my SASL authentication and directly accessing the MySQL database for the list of senders that need authentication before they can send.

Excerpt from /etc/postfix/main.cf

```
# SASL Authentication (require authentication to send outbound email)
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated reject_unauth_destination

# make even local users authenticate - just because you use my router doesn't mean you are totally trusted
smtpd_sasl_exceptions_networks = 

# Reject email from known senders that don't authenticate
smtpd_sender_login_maps = mysql:/etc/postfix/smtpd_sender_login_maps.cf
smtpd_sender_restrictions = reject_sender_login_mismatch
```Excerpt from /etc/postfix/smtpd_sender_login_maps.cf

```
user = realuser
password = realpassword
hosts = localhost
dbname = mytable
query = SELECT username FROM mailbox WHERE username='%s' and active='1'
```Exceprt from /etc/dovecot.conf

```
auth default 
{
  mechanisms = plain login
  passdb sql 
  {
    args = /etc/dovecot/dovecot-sql.conf
  }
  userdb sql 
  {
    args = /etc/dovecot/dovecot-sql.conf
  }
  user = root
  socket listen 
  {
    client 
    {
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }
  !include_try /etc/dovecot/auth.d/*.auth
}
```

---

