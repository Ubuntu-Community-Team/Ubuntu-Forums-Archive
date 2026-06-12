---
title: "how to change the default sendmail reply-to and sent-from email address"
date: 2008-07-07
forum: Server Platforms
---

### Post by skunkbad on 2008-07-07
I set up sendmail because I like to use a simple contact form on my websites, and also so that ddclient can email me. I noticed that the reply-to and sent-from email address that ddclient uses is [email]root@servername.domain.net[/email], and I believe php sends it as [email]servername@domain.net[/email]. How can I change what the reply-to and sent-from email addresses are?

---

### Post by windependence on 2008-07-07
You should be using something other than sendmail, like postfix. It is a drop in replacement for sendmail, there should be little or no configuring necessary to use the php function. It IS, however, MUCH easier to config for things like what you want to do, than sendmail.

-Tim

---

### Post by skunkbad on 2008-07-07
ok, I installed postfix. I'll post again if I have problems.

---

### Post by skunkbad on 2008-07-07
This is really strange to me.

I did the following:

sudo apt-get remove sendmail
sudo apt-get install postfix

there were some errors when installing postfix ... something about not being able to find some files.

Email can be sent from php and ddclient. I assumed that postfix must have installed at least enough to send email, however:

ps aux doesn't show postfix, but it does show sendmail:MTA.

So I tried to remove sendmail again, and it says that it doesn't exist, and I tried to remove postfix, and it says it doesn't exist either.

So, if neither exist, why is sendmail:MTA running, and what do I do from here?

---

### Post by windependence on 2008-07-07
Ay NOOOOO! Don't uninstall sendmail. Postfix is meant to be installed along side it. Also pay attention to any config messages you get when it's finished installing.

-Tim

---

### Post by skunkbad on 2008-07-07
> **windependence said:**
> Ay NOOOOO! Don't uninstall sendmail. Postfix is meant to be installed along side it. Also pay attention to any config messages you get when it's finished installing.

-Tim

I'm too tired to mess around with this. I uninstalled postfix, and reinstalled sendmail, and I can send mail again. I'll try again tomorrow or sometime when I feel like torturing myself :)

---

### Post by Spaander on 2008-07-26
This works with Centos51 without postfix, so hopefully it will work for you:
In Centos sendmail uses the first entry it locates in /etc/hosts
thus reordering the entries in the file from
127.0.0.1 localhost.localnet somepc.somedomain
to 
127.0.0.1 somepc.somedomain localhosst.localnet

has the desired effect the reply-to and sent-from email addresses.

This works on a number of our pc at work (centos / fedora)

Hopefully it should work for you as it is quick to check?

Regards

---

