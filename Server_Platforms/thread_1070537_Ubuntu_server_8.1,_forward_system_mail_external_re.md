---
title: "Ubuntu server 8.1, forward system mail external recipient"
date: 2009-02-15
forum: Server Platforms
---

### Post by p.becks on 2009-02-15
Hello,

I am using ubuntu 8.1 and i want to forward all system-mail that is send to root or [user] to a EXTERNAL email-adress.

I tried several packages (postfix/sendmail/..) but no sigar..

What steps should i take to get things working? ( i send several test-mails to the external email-adres but they don't arrive!)

What ports should i open up in the firewall?

ps: i added a ~/.forward to the homedir of root and [user] so that mail will be forwared (when things work that is)


By the way: i have NO intension of receiving mail from a external email-adress on the server. I just what to send from the server to external...

ps: port 25 is closed by my isp...

---

### Post by brian_p on 2009-02-17
> **p.becks said:**
> 

I am using ubuntu 8.1 and i want to forward all system-mail that is send to root or [user] to a EXTERNAL email-adress.

Using exim4 I have

```
root: user@gmail.com
```

in /etc/aliases.

> 
```
What steps should i take to get things working? ( i send several test-mails to the external email-adres but they don't arrive!)
```


In addition to the above: Set up your MTA to use you ISP's mail server as a smarthost.

> What ports should i open up in the firewall?

You block outgoing connections? I'd unblock all ports.

> ps: port 25 is closed by my isp...

Incoming?

---

