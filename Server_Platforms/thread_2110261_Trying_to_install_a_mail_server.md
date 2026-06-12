---
title: "Trying to install a mail server"
date: 2013-01-29
forum: Server Platforms
---

### Post by MG2R on 2013-01-29
I have been trying to do this for a couple of years now... I want my own mail server (you know, to have an awesome address like [EMAIL="first@lastname.com"]first@lastname.com[/EMAIL]).

I followed the instructions for Postfix and Dovecot on help.ubuntu.com and according to the tests they made me perform (telnetting into the server), everything should be working splendidly. I redirected my domain name MX records to my IP-adress but I fail to log into my account via Thunderbird (that can't find the service running on my computer).

That said, I never explicitly *made* an account in postfix/dovecot, so I'm not sure what to expect.

Any help?

---

### Post by sanderj on 2013-01-29
You know the difference between sending mail (postfix) and reading mail (dovecot)?

Which is not working?

Do you know which ports they run? Checked with telnet?

---

### Post by MG2R on 2013-01-29
I (think I) know how the whole mailing system works theoretically. So yes, I know Dovecot is for reading mail.

As for the ports:
The help-site said to forward these for IMAP: 143 and 993. I configured thunderbird to try to connect to username@domain where username is my Ubuntu username on the server. I say I want to use SSL/TLS security on port 993 for IMAP and SSL/TLS security on port 465 for SMTP.

I just wanted to check telnet again so I booted up my server (which, at the moment, is my laptop for testing purposes). Now I can't get it to connect via telnet (telnet localhost imap2). Something else must be wrong :/

Thanks for the help so far!

--
EDIT: I am able to connect on port 993 and 143

---

### Post by SeijiSensei on 2013-01-29
Have you told both Postfix and dovecot to listen on all the interfaces and not just localhost?  By default, for security reasons, neither server will bind to anything other than 127.0.0.1.  In Postfix, you need to change the "[mynetworks]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from")" directive; in dovecot, you need to uncomment the "listen = *" directive as described [here](https://help.ubuntu.com/community/Dovecot).

---

### Post by lourendo on 2013-01-30
Did you remember to port forward the mail ports on your router?

---

### Post by sanderj on 2013-01-30
> **MG2R said:**
> I (think I) know how the whole mailing system works theoretically. So yes, I know Dovecot is for reading mail.

As for the ports:
The help-site said to forward these for IMAP: 143 and 993. I configured thunderbird to try to connect to username@domain where username is my Ubuntu username on the server. I say I want to use SSL/TLS security on port 993 for IMAP and SSL/TLS security on port 465 for SMTP.

I just wanted to check telnet again so I booted up my server (which, at the moment, is my laptop for testing purposes). Now I can't get it to connect via telnet (telnet localhost imap2). Something else must be wrong :/

Thanks for the help so far!

--
EDIT: I am able to connect on port 993 and 143

a 'telnet localhost imap2' will connect to port 143, and if that works, that's good, isn't it? Are you able to get mail?

Does it work to send mail (via localhost's SMTP port 25)?

The secure service 'imaps' (note the s) is on port 993. However, to make that really work, you need to setup SSL. For SSH that's made easy, but I don't know if that's easy for dovecot.

---

### Post by HermanAB on 2013-01-30
Note that you can install a Citadel mail server using their Easy Install script in about 20 minutes, as opposed to the weeks/months/years required to make Postfix work.

[http://citadel.org](http://citadel.org)

---

### Post by MG2R on 2013-01-30
Progress so far: 

Uncommented *listen=** in the Covecot config file. Tried using SMTP on port 25. This time, thunderbird did ask for my password, but sending the message did not work. (stuck at 'copying message to sent folder')

Tried using port 143 (both with SSL and insecure) for IMAP, now thunderbird gave a message about too many connections on the server (it was gone before I could fully read it).

So, slowly we are getting there...

BTA: I just noticed there isn't a ~/Maildir, despite the fact that I am using Maildir.

My main problem is finding an easy to understand piece of documentation about what I need to do and what that does to the system to make it work. The whole mailing system seems either a) quite undocumented or b) documented very cryptically.

Or is it just me?


> **HermanAB said:**
> Note that you can install a Citadel mail server using their Easy Install script in about 20 minutes, as opposed to the weeks/months/years required to make Postfix work.

[http://citadel.org](http://citadel.org)

I will look into this! Thanks!

---

