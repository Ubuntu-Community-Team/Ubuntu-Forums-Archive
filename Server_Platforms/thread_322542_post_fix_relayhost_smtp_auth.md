---
title: "post fix relayhost smtp auth"
date: 2006-12-20
forum: Server Platforms
---

### Post by eradicator_006 on 2006-12-20
Hi all,

I'm in the process of moving my Gentoo server over to Ubuntu.  On Gentoo I am using qmail with tls, virtual users and smtp auth.  I've managed to get virtual users, tls and smtp auth working ok using postfix on dapper.  I am having one problem though.  I need to relay all outgoing mail through my ISP.  My ISP requires smtp auth.  smtp auth works fine for my clients connecting to my mail server but i cannot get it working for my server to authenticate to my isps server.  I basically followed the howto at [http://high5.net/howto/](http://high5.net/howto/).  I added 'smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd' to my main.cf file, created a sasl_passwd file and ran postmap on it. Here's what my mail.info tells me:

postfix/smtp[4115]: 4B9048B41C: to=<me@xxx.xx>, relay=smtp.myisp.com[x.x.x.x], delay=0, status=bounced (host smtp.myisp.com[x.x.x.x] said: 530 5.7.0 No AUTH command has been given. (in reply to MAIL FROM command))

It looks to me like sasl is ignoring the password map file and looking in the sql database for the info.  sasl is configured to use saslauth and saslauth is configured to use mysql_pam.  Any suggestions on how I can get both smtp auth for my clients and also use smtp auth to relay to my ISP?

---

### Post by chrisfay on 2006-12-20
Sounds like you're missing some of the main.cf directives you need. I outlined it in this thread:

[http://ubuntuforums.org/showthread.php?t=316711](http://ubuntuforums.org/showthread.php?t=316711)

Disregard the fact that its for relaying through an Exchange server. It's the same for any relayhost.

---

### Post by eradicator_006 on 2006-12-20
> **chrisfay said:**
> Sounds like you're missing some of the main.cf directives you need. I outlined it in this thread:

[http://ubuntuforums.org/showthread.php?t=316711](http://ubuntuforums.org/showthread.php?t=316711)

Disregard the fact that its for relaying through an Exchange server. It's the same for any relayhost.

Yup that was it, thanks.  I didn't realize there were seperate directives for both smtp and smtpd.  I had the smtpd directives (this handles incoming auth) and not the smtp (outgoing) directives.  Thanks a bunch.

---

### Post by chrisfay on 2006-12-20
Np ;)

---

