---
title: "Simple SMPT Solution"
date: 2011-03-06
forum: Server Platforms
---

### Post by sergio-bobillier on 2011-03-06
Hello.

I will keep this simple and easy. I need a SMTP server to send email from contact forms on some websites. I installed and configured Postfix on the server and I have it running just fine however I think it is a waste of resources because I don't need IMAP, POP3 nor mail boxes I just need SMTP.

I have been looking around for some simple SMTP solution and I have tried so far Sendmail (bad mistake), and sSMTP (it doesn't seems to be what I'm looking for). I really don't know how to look for another mail solution.

If you could please suggest a simple SMTP solution to me I would appreciate it. I don't want to relay on my ISP SMTP server or anything I need a SMTP server running on my server that can delivery messages directly to gmail, hoitmail or any other domain.

Thanks in advance.

---

### Post by terazen on 2011-03-08
Use postfix setup as a satellite.  If you have postfix installed already you can reconfigure the options you initially used:
```
sudo dpkg-reconfigure postfix
```

---

### Post by bsntech on 2011-03-08
I use Exim on my systems and it works quite well.  Install it - and just a quick configuration change to allow outbound e-mails - and you are set.

sudo apt-get install exim4

After installed, go into the /etc/exim4/ directory and edit the update-exim4.conf.conf file.  Change the "dc_eximconfig_configtype" line to "internet", so it should look like this:

dc_eximconfig_configtype='internet'

Restart exim after making the change and you are good.

/etc/init.d/exim4 restart

I just did this for a customer I provide support to - and works perfect for their needs.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("dc_eximconfig_configtype")

---

### Post by hictio on 2011-03-08
Postfix will not setup nor use nor need an IMAP nor POP3 setup on a given box to simply send localhost generated emails.
IMHO, for what you need, and specifically since you don't want to use ssmtp, Postfix is a one stop thing, start it and use it.
You don't even need it, nor want it to, be listening on anything but the loopback address.
How many emails are you planning to send, because Postfix hardly consumes any resources when not doing anything.

---

### Post by sergio-bobillier on 2011-03-09
Thanks a lot for your answers. I did what terazen suggested and changed Postfix configuration to Satellite mode. It improved because now i don't have so many Postfix processes running. Still when I test the contact form on the web page I get like 5 "smpt" processes and other 5 "bounce" processes I still don't know why.... I hope it is a normal behavior.

I have it bounded to the local loopback and only 127.0.0.0/8 configured in my_networks I cant figure out why so many processes for a single delivery. But at least I don't have a lot of processes for services I wasn't using at all.

---

### Post by Iker Etxebarria on 2011-03-09
Another option could be to use an external SMTP server, for example,with a gmail account or something like that. If you only need to send emails maybe it would be better and more secure for your server.

---

