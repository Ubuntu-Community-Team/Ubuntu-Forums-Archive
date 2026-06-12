---
title: "imap"
date: 2008-01-15
forum: Server Platforms
---

### Post by kenmiles on 2008-01-15
I am running ubuntu 6.10 with apache2, postfix and my own webserver.
Mail is stored in /var/mail and I want to access it at times from the web.
Can you please advise which imap program to install that will access the linux mail accounts directly in combination with squirellmail or other webmail program.

Thanks in advance, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by MJN on 2008-01-15
Any IMAP server will suffice - Dovecot is my preference.
 
Mathew

---

### Post by HermanAB on 2008-01-15
I can second dovecot.  However, you *have* to read the manual, there are a few tricks in there that you need to be aware of.

Cheers,

Herman

---

### Post by MJN on 2008-01-15
Now you've got me worried... I never read the manual! ;)
 
Can you elaborate?
 
Mathew

---

### Post by kenmiles on 2008-01-15
Thanks for that but does Dovecot support the default /var/mail/usermail format or do I have to set it up for maildir.
Regards, Kenneth.

---

### Post by MJN on 2008-01-15
<duplicate post deleted>

---

### Post by MJN on 2008-01-15
Presumably you mean mbox format? If so, yes.
 
However, I would recommend looking at using maildir instead unless you have specific reasons not to do so. It carries many benefits in my opinion (a Google search will given you the endless debates!).
 
Mathew
 
P.S. You might be interested in having a look at [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot) - I haven't read it but it may give you useful background/guidance.

---

### Post by HermanAB on 2008-01-15
Dovecot can do anything, Mbox and Maildir.  There are some specific workarounds for MS Outlook bugs, for which you have to read the manual.

Cheers,

Herman

---

### Post by MJN on 2008-01-15
Ah, okay - they're detailed in the default config anyway.

Mathew

---

### Post by kenmiles on 2008-01-19
I have now setup Dovecot but when I test it I get the following

telnet kmiles.co.uk 143
Trying 86.132.173.43...
Connected to kmiles.co.uk.
Escape character is '^]'.
* OK Dovecot ready.
LOGIN kenneth
LOGIN BAD Error in IMAP command received by server.

Any help gladly received, Kenneth.

---

### Post by MJN on 2008-01-19
A couple of things - you need to append the password and also prefix the command with a unique string so the server can respond with the string to match the request.

Hence, try [B]a01 LOGIN kenneth <your password>

[/B]Unlike SMTP, IMAP is not really the most user-friendly protocol to test at the lower level hence you might prefer to use a mail client to test it (this is particularly necessary if you start to use TLS and/or other methods of password encryption).

Mathew

---

### Post by kenmiles on 2008-01-19
> **MJN said:**
> A couple of things - you need to append the password and also prefix the command with a unique string so the server can respond with the string to match the request.

Hence, try [B]a01 LOGIN kenneth <your password>

[/B]Unlike SMTP, IMAP is not really the most user-friendly protocol to test at the lower level hence you might prefer to use a mail client to test it (this is particularly necessary if you start to use TLS and/or other methods of password encryption).

Mathew

Thanks for that, it has let me get a bit further and ends with this message 

a01 OK Logged in.
Connection closed by foreign host.

Regards, Kenneth.

---

### Post by MJN on 2008-01-19
What, straight away?

Does your mail log (**tail /var/log/mail.log**) give any clues?

Mathew

---

### Post by kenmiles on 2008-01-19
> **MJN said:**
> What, straight away?

Does your mail log (**tail /var/log/mail.log**) give any clues?

Mathew

Yes as soon as I press enter.
There does not seem to be a log for Dovecot and it is not logged in the normal mail log.
Regards, Kenneth.

---

### Post by MJN on 2008-01-19
Strange - it normally logs via syslog by default using the mail facility (hence it should end up in mail.log).

Check your syslog and/or see what you have **log_path** set to.

Mathew

---

### Post by kenmiles on 2008-01-19
> **MJN said:**
> Strange - it normally logs via syslog by default using the mail facility (hence it should end up in mail.log).

Check your syslog and/or see what you have **log_path** set to.

Mathew

Thanks Mathew, that was where the log was and I had the mail_env = set wrong.
Thanks again for your help, now to start on Squirrelmail!

---

### Post by MJN on 2008-01-19
> **kenmiles said:**
> Thanks Mathew, that was where the log was and I had the mail_env = set wrong.

Excellent.

> Thanks again for your help, now to start on Squirrelmail!Will keep any eye out for the next query then! ;-)

Mathew

---

### Post by kenmiles on 2008-01-20
> **MJN said:**
> Excellent.

Will keep any eye out for the next query then! ;-)

Mathew

Hi Mathew
I have now got Squirrelmail set up but with one problem.
Mail is being sent by postfix and I need it to be sent by SMTP through my isp but cannot figure out where to set this.
I have set up a test account at [http://kmiles.co.uk/webmail](http://kmiles.co.uk/webmail) with a user name mailtest and password test..If you can help I would be most grateful.
Regards, Kenneth.

---

### Post by MJN on 2008-01-20
Do you mean you want Postfix to send outgoing mail via your ISP, or just mail sent from Squirrelmail?

Assuming the former, you need to use the [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") directive in Postfix's main.cf. Note from the documentation the use of [...] brackets in order to ensure Postfix does an A record lookup for the address as opposed to an MX record.

Hence, in your case, you want something **relayhost = [smtp.btcentralplus.com] **(or whatever their outgoing mail server is called).

Mathew

---

### Post by kenmiles on 2008-01-20
> **MJN said:**
> Do you mean you want Postfix to send outgoing mail via your ISP, or just mail sent from Squirrelmail?

Assuming the former, you need to use the [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") directive in Postfix's main.cf. Note from the documentation the use of [...] brackets in order to ensure Postfix does an A record lookup for the address as opposed to an MX record.

Hence, in your case, you want something **relayhost = [smtp.btcentralplus.com] **(or whatever their outgoing mail server is called).

Mathew

I can understand that but I also need to login with my username and password so I can put smtp.mail.btinternet.com as the server in squirrellmail but not the login details.
Regards, Kenneth.

---

### Post by MJN on 2008-01-20
Are you saying you only want mail sent from Squirrelmail to be sent via your ISP's mail server? Given it looks like you're using a dynamic IP address you will probably want to be send all mail via your ISP, including that sent from 'traditional' mail clients, otherwise you might find you will trip spam filters.

Even if it's just Squirrelmail you're interested in, I'm not sure I follow what the problem is - Squirrelmail supports outgoing authentication with SMTP servers under option 2 > B > 7 in {SM directory}/config/conf.pl

Of have I got the wrong end of the stick?

Mathew

P.S. Great website by the way!

---

### Post by MJN on 2008-01-20
Ah.. I think I know what you mean now. Are you saying you do want Postfix to send all mail via the ISP but you also need to authenticate with the server? If so, let me know and give me a few minutes to jot down how to achieve this.

Mathew

---

### Post by kenmiles on 2008-01-20
> **MJN said:**
> Ah.. I think I know what you mean now. Are you saying you do want Postfix to send all mail via the ISP but you also need to authenticate with the server? If so, let me know and give me a few minutes to jot down how to achieve this.

Mathew

Thanks Mathew,
I have got it working now. I had missed the setting in squirrellmail to achieve this.
Thanks again for all your help and for your kind comments about the website.
Regards, Kenneth.

---

### Post by MJN on 2008-01-20
Are you sure you only want Squirrelmail's mail to be sent via your ISP? What about other clients? Do you ever send via your Postfix server?

Mathew

---

### Post by kenmiles on 2008-01-20
> **MJN said:**
> Are you sure you only want Squirrelmail's mail to be sent via your ISP? What about other clients? Do you ever send via your Postfix server?

Mathew

I use kmail and I can select which method to send mail in the kmail settings so I have not had this problem before.
Thanks again, Kenneth.

---

