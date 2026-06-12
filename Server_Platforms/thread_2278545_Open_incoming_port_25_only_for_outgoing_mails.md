---
title: "Open incoming port 25 only for outgoing mails?"
date: 2015-05-17
forum: Server Platforms
---

### Post by lars10 on 2015-05-17
Hey,

I was just wondering whether I have to open port 25 for incoming connections in my firewall when I'm just sending mails via postfix (for example for a WordPress installation) but not receiving on this server (MX records for the server FQDN are different anyway).

Are there any other things I have to worry about when setting up postfix? Obviously I Don't want to set up an open relay. Only my server itself is supposed to send mail, no one else, but AFAIK postfix is configured like this by default in the Ubuntu server repos, isn't it?

Thanks for your help!
Lars

---

### Post by darkod on 2015-05-17
As far as I know you do not need incoming port 25 for outgoing emails. Your mail server will connect to the destination server to deliver the email, which is outgoing connection.

As for the open relay, I also think postfix by default is not an open relay but I haven't had much experience with it.

---

### Post by SeijiSensei on 2015-05-17
Postfix is configured to listen on the localhost (127.0.0.1) interface by default and no others.  In this configuration it is not visible to the outside world.

You do not need to open port 25 to send mail, though it will be open on the localhost interface.

---

### Post by lars10 on 2015-05-17
Hey,
Thanks for your answers.
The reason I'm asking is because I have postfix set up right now only for outgoing but not incoming mails only from localhost (so basically standard configuration). My server is configured to send a daily logwatch report to my mail, which is working.

Under the postfix section though I can see entries like:

2 hostname abs-static-xyz.aircel.co.in does not resolve to address 118.xxx...

1 hostname xyz.cyrusone.com does not resolve to address 198.58.xx.xxx: Name...

      1      hostname xyz.ip.prominic.net does not resolve to address 199.103.x.xxx: N...

(I censored them here a bit).

Are these caused by servers connecting to postfix (basically port scanners / bots) and then automatically disconnecting when they notice that they're not allowed to send mails? Or is it something that I have to worry about?
Though this should stop anyways when I close port 25, shouldn't it?

Thanks!

---

### Post by Ron_Greve on 2015-05-17
I m not sure about the daily mail. But this looks like message from the syslog. It means a mailserver is connecting to your server but when your mail server does a reverse lookup (using the ip to get the hostname) it gets a different hostname than what the remote mailserver claims to be.

This, in itself, doesn't say much (my own mailserver doesn't reverse resolve to the same hostname because my ISP is not my registrar (so the reverse lookup goes to my ISP (and I cannot change the hostname to a name that is not a subdomain of theirs) to ask the hostname while a forward lookup goes to the registrar to get the ip.

Regards, Ron

---

### Post by SeijiSensei on 2015-05-17
I was wrong in my original assumption about it being limited to localhost.  By default, postfix listens on all interfaces because of the directive in /etc/postfix/main.cf
```
inet_interfaces = all
```
However it ignores traffic on anything but localhost because the "mynetworks" parameter is set to accept connections only from 127.0.0.0/8 and its IPv6 permutations.  You can limit the server to just localhost with
```
inet_interfaces = 127.0.0.1
```

---

### Post by lars10 on 2015-05-17
Yeah well, I just closed port 25 so I guess I don't have to worry about all of this then, or do I? Sending mails still seems to work just fine and since this isn't a real production server anyway, I don't really care.

---

