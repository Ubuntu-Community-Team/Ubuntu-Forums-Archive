---
title: "Exim4 receive mail"
date: 2009-02-10
forum: Server Platforms
---

### Post by mystro on 2009-02-10
Hello,
I'm trying to configure exim4 to receive mail. I've run exim4-config with the following settings:

The server is located at my university and I am wondering if perhaps some port is blocked, but I'm not sure what to ask them about. 

Out going mail sends fine, but I can't seem to receive incoming mail 

I'm using one of the dynamic hosting websites for my ip such that my hostname is (something.dyndns.com)

* internet site 
system mail name: something.dyndns.com
ip address to listen on: my assigned static ip address 
other destinations: something.dyndns.com
domains/machines to relay mail for is empty
dial-on-demand off
Maildir format
Split config yes 

when I send mail out, I see it appear in /var/log/exim4/ but when I try to send mail to myself I see nothing
any help would be appreciates

---

### Post by mystro on 2009-02-11
bump :)

---

### Post by Ed1000 on 2009-03-22
Can you send mail with these setting?

What would your receive address be? is that something like 'you@dyndns.com'?
Does dyndns.com know what to do with the incoming mailmessage (i.e. send it to your server). Is port 25 set up to forward it to the right place?

---

### Post by Ed1000 on 2009-03-22
oops I am sorry, you also have a static IP address. So what is the format of the emailaddress that you are sending to?
is that

[email]yourname@dyndns.com[/email]
yourname@staticipno
[email]yourname@a-known-domain.com[/email]
?

---

### Post by Ed1000 on 2009-03-22
I must be sleeping while reading your question, as you already said you could send out mail. My other questions however remain.

---

