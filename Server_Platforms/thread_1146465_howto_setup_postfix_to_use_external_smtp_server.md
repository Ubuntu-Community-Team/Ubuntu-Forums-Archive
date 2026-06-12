---
title: "howto setup postfix to use external smtp server"
date: 2009-05-02
forum: Server Platforms
---

### Post by jdcnosse on 2009-05-02
I have Charter for my ISP, so I would like to use their smtp server to send my e-mails from postfix on my ubuntu 8.04 server.

I know the smtp address for charter (smtp.charter.net) but I don't know how to stick that into postfix.

---

### Post by gombadi on 2009-05-02
Add the following to /etc/postfix/main.cf and reload postfix

```

relayhost = [smtp.charter.net]

```

Reference - [http://www.postfix.org/postconf.5.html#relayhost](http://www.postfix.org/postconf.5.html#relayhost)

---

### Post by dipeshmehta on 2009-05-03
you may look at [http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver) for step-by-step guide.

---

### Post by tonyyarusso on 2009-05-03
It's actually for GMail, but you can probably get some idea of what you need from my config - [http://files.tonyyarusso.com/postfix_config_gmail.tar.gz](http://files.tonyyarusso.com/postfix_config_gmail.tar.gz)

---

