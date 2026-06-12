---
title: "local mail not working on server install 8.10"
date: 2009-01-14
forum: Server Platforms
---

### Post by finite9 on 2009-01-14
I noticed that local mail does not work by default on Ubuntu server 8.10, and I am used to getting mails from stuff like LogWatch and ddclient and mdadm on CentOS 5.2, so I installed sendmail and nail, but I cannot receive mails.  I simply installed them with "apt-get install sendmail nail" and then I type:

mail root@localhost (or simply root)
"Subject:" pops up and I type in test and enter
then i type in the body, go to new line and ctrl-D to send.  It does not complain but I do not receive the mail when I do "sudo mail"

I am missing something?  Do I need to configure sendmail/nail?  Or do I need something else besides sendmail MTA and nail client?

I am not getting any mails att all from Logwatch.

---

### Post by RealPSL on 2009-01-16
I have done the same thing but instead using postfix and it works fine. During installation it asked me how I wanted it configured and I said Local Mail only and it works great. Are you opposed to switching to postfix?

---

### Post by finite9 on 2009-01-20
no not at all.  I have been reading up quite a bit about this, and wondered if I needed an MDA as well as an MTA?  sendmail is an MTA only from what I understand, and Dovecot is an MDA.  Is this the missing link or am I just missing "configuration".  As I have already installed the server and do not want to re-install, will I get the same choice of local mail if I manually install postfix with apt-get install?

Heard that postfix was "better" anyhow, so I have nothing against using it for local mail.

---

### Post by HermanAB on 2009-01-20
Postfix and Dovecot work well together.

Cheers,

Herman

---

### Post by RealPSL on 2009-01-20
Yes during the apt-get install process you get prompted to choose the configuration.

---

### Post by finite9 on 2009-01-23
Ok, I installed postfix and got rid of sendmail and I can now mail myself, however...

Feels a bit poor that local mail / logwatch and logrotate are not installed OOTB on Ubuntu server.

---

### Post by RealPSL on 2009-01-28
I missed logrotate myself but there is only so much you can fit on 1 CD and installing it post is very easy.

---

### Post by finite9 on 2009-02-06
i still had issues, but it turns out that I had mistakenly removed procmail.  Really, on fresh ubuntu server install, you only need postfix and procmail to be able to send/receive mail.  Then of course I had to edit the conf files for mdadm, logwatch, rkhunter et all so they mailed me and not root.

---

### Post by sullam on 2009-02-06
finite9,
I am disappointed that you didn't stick with sendmail so I could use your solution. I am having the exact problem with the same applications that you listed as your original problem. I am using Ubuntu 8.04 server. I'm not ready to give up on sendmail yet. 
There are other things that I am not that pleased with Ubuntu coming from redhat based distros, like the way the firewall works. When I use the init script ufw for starting the firewall, it doesn't start the iptables forwarding rules. Also it doesn't mesh well with webmin which I like to use. Also apache2 is set up differently.

---

