---
title: "postfix/thunderbird and SSL or TSL?"
date: 2009-12-01
forum: Server Platforms
---

### Post by bmhm on 2009-12-01
Hi everyone!

I set up a certificate for my server, so I can use TLS and SSL for connection purposes.

I can setup Thunderbird to use TLS, then I get this
```
Port: 110
Dec  1 18:29:53 golf764 pop3d: LOGIN, user=<user>@<domain>, ip=[::ffff:xx.21.xx.195], port=[56089]
Dec  1 18:29:53 golf764 pop3d: LOGOUT, user=<user>@<domain>, ip=[::ffff:xx.21.xx.195], port=[56089], top=0, retr=0, rcvd=12, sent=39, time=0, stls=1
```


When I select "SSL" in thunderbird, it switches to:
```
Port: 995
Dec  1 18:29:31 golf764 pop3d-ssl: LOGIN, user=<user>@<domain>.de, ip=[::ffff:xx.21.xx.195], port=[48668]
Dec  1 18:29:31 golf764 pop3d-ssl: LOGOUT, user=<user>@<domain>.de, ip=[::ffff:xx.21.xx.195], port=[48668], top=0, retr=0, rcvd=12, sent=39, time=0
```


On one hand, Wikipedia says TLS is more recent than SSL (in fact TLS is SSLv3.1). But on the H ([http://www.h-online.com/](http://www.h-online.com/)) and c't magazine I read, Thunderbird mixes things up a little. On the other hand, my log output makes me believe it doesn't.

Well, does it, then? So put "ssl" or "tls" into my account's settings?

Thanks for your input in advance.
Regards,
Ben

---

### Post by Ilalmi on 2009-12-02
There is an article on mozillaZine.org that should answer your question:
[http://kb.mozillazine.org/Secure_connections_-_Thunderbird](http://kb.mozillazine.org/Secure_connections_-_Thunderbird)

---

### Post by bmhm on 2009-12-02
For those who find this thread: This is a good answer (shortened to the facts):
[LIST]
[*]TLS and "TLS, if av" are mislabeld and should be: "STARTTLS" and "STARTTLS if av"
[*]They will in fact start an insecure connection and try to upgrade it to something encrypted. 
[*]For **Thunderbird 2.0,** it is recommended that if your mail server supports both TLS and SSL you choose SSL since it's just as secure, and it will always either make a secure connection or fail.
[*]Its recommended that you use just a secure connection if you have a choice since using two different ciphers to **double encrypt data can sometimes make it far less secure**.
[/LIST]

I have heard of the last fact before, so don't be confused. It's true.

Thanks for the link.

---

