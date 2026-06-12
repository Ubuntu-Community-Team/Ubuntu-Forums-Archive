---
title: "exim4 configuration issue - auth not advertised when I want it to be"
date: 2013-04-25
forum: Server Platforms
---

### Post by andrea01 on 2013-04-25
Hello.  I was hoping someone could help me figure out what I am doing wrong with my exim4 configuration.  I want to have users be able to send mail outside of my domain.  I am running Ubuntu Desktop 12.04 64 bit.

So far I have installed exim4 from the repository and successfully configured exim4 to use maildir and can receive mail and send mail from mutt on the server.  Now I am trying to set up the relay and authorization.  I have enabled TLS and do get the STARTTLS command advertised and it looks like it works but then my auth commands are not advertised.  (I have configured these auth types in the auth/30_exim4-config_examples file:  plain_saslauthd_server & login_saslauthd_server).

I suspect my mail server is challenging my telnet requests in some way that my requests are failing so it doesn't offer the AUTH commands or maybe the server can't find my certificates.  But I am out of ways to try to test this theory.

Is there anyone who can help me try to debug this issue?

My exim4 config file is set like this:
- General type of mail configuration: internet site; mail is sent and received directly using SMTP
- System mail name: mydomain.com
- IP-addresses to listen on for incoming SMTP connections: <blank>
- Other destinations for which mail is accepted: <blank>
- Domains to relay mail for: mydomain.com
- Machines to relay mail for: <blank>
- Dial-on-Demand? No
- Delivery method for local mail: Maildir
- Split configuration into small files?: No

Any help would be appreciated.  Thanks.

---

### Post by andrea01 on 2013-04-26
Okay, I figured out why AUTH was not being advertised ...

I had made the changes for the authentication methods in the /etc/exim4/conf.d/auth/30_exim4-config_example file but when I looked at the /etc/exim4/exim4.conf.template file I could see the plain_saslauthd_server & login_saslauthd_server authentication methods were not uncommented.  So I uncommented them in the exim4.conf.template file, ran 'sudo update-exim4.conf' and restarted the mail server and I am now getting the AUTH options advertised.

I am not sure why my changes are not being picked up in the files in the conf.d directory but I am glad to be able to finally get this working.  If anyone knows why I would like to know but otherwise I would consider this thread as resolved.

Thanks.

---

