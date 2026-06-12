---
title: "Exim4 forwarding to other SMTP server (with auth and SSL)"
date: 2009-04-01
forum: Server Platforms
---

### Post by hkusulja on 2009-04-01
Hi!
I have exim4 defaulty installed on my Debian 5.0 ...

I want configure E-mail SMTP server with this settings:
 - bind to only 127.0.0.1  (so nobody can sand e-mail except from the server local)
 - local server applications (for example php) should use this settings
 - ALL e-mails should go to GMAIL SMTP
	- smtp.gmail.com, port: 465, SSL/TLS enabled, Auth: [email]myusername@gmail.com[/email] Pass: abc123
 - if my computer name is  srv1.example.org , i want that email which is addressed to [email]root@example.org[/email] goes through GMAIL SMTP
(other server are serving example.org e-mail service)

i just need to config SMTP on localhost which will forwared ALL requests to GMAIL SMTP..

can you help me ? 

thank you

---

### Post by smeerbartje on 2009-04-02
Did you see [this post]("http://ubuntuforums.org/showthread.php?t=1113809")?

---

### Post by hkusulja on 2009-04-02
> **smeerbartje said:**
> Did you see [this post]("http://ubuntuforums.org/showthread.php?t=1113809")?
no i did not, but this is for postfix, and i am asking for exim4

if it is necesary, i will remove exim4, and install postfix..

and i forgot to say, i don't want local mail :)

---

### Post by smeerbartje on 2009-04-02
> **hkusulja said:**
> no i did not, but this is for postfix, and i am asking for exim4

if it is necesary, i will remove exim4, and install postfix..

and i forgot to say, i don't want local mail :)

Excuse me for being noob, but exim4 is only a SMTP server?? (so you don't have local email accouns)

---

### Post by hkusulja on 2009-04-02
> **smeerbartje said:**
> Excuse me for being noob, but exim4 is only a SMTP server?? (so you don't have local email accouns)

no i am noob :)

once again.., on my local server, i don't want any access to mail (niether smtp, pop3, imap), and no local mail for local users...

i just want to setup that every application (for example php, or by using mail command in shell) , that all mail should be sent to gmail SMTP server, by using local SMTP which listens on 127.0.0.1 ...

---

### Post by smeerbartje on 2009-04-02
> **hkusulja said:**
> no i am noob :)

once again.., on my local server, i don't want any access to mail (niether smtp, pop3, imap), and no local mail for local users...

i just want to setup that every application (for example php, or by using mail command in shell) , that all mail should be sent to gmail SMTP server, by using local SMTP which listens on 127.0.0.1 ...

All right, I want EXACTLY the same. Can anyone help us what the best way is to achieve this? Thanks big time!

---

### Post by M1GEO on 2009-06-16
Anyone?  I also have the same problem.  I am trying to set up a similar system.  I wish to have exim4 forward any mail not for a local user to BT's mail server (which requres authentification).

I am pretty close - When sending mail, I get the following error;

> 
2009-06-17 01:48:42 1MGjKU-0000KP-Bk ** [email]MY_EMAIL@btinternet.com[/email] R=smarthost T=remote_smtp_smarthost: SMTP error from remote mail server after MAIL FROM:<>: host pop-smtp1-f.bt.mail.vip.ird.yahoo.com [217.146.188.192]: 530 authentication required - "Your email could not be sent. To fix this you must make a simple change to your email (known as SMTP authentication). For advice visit www.btyahoo.com/smtp"


Any help would be greatly appreciated...

George Smart

---

### Post by matthewboh on 2009-06-18
I want to do exactly the same thing - forward error messages / status reports to a mail server so I can get them.

---

### Post by jamessnell on 2009-07-27
Indeed, this is a popular topic for sure.

I'm trying to nail this down right now. I'm kind of annoyed by how long it's taking me to figure it out. I've setup actual mail servers way back in the day and while that took me a good while to figure out, I'd think that the level of functionality we're going for here is so typical it would nearly work out of the box, I mean all we really should have to do is give SMTP creds for somewhere..

At least there's [this doc]("http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/"), at first I thought perhaps that'd lead me to logging in plaintext, but the smtp port number used for google there is an ssl port, so I think it's cool, If you're in doubt, there's always wireshark!

Anyway, by following that guide I've now got my exim4 ubuntu setup sending through gmail.. So I'm happy, mission accomplished!

---

