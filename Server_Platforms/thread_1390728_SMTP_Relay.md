---
title: "SMTP Relay"
date: 2010-01-25
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-25
I've search high and low.. does anyone know how to configure Postfix/Dovecot to use another SMTP server (i.e. smtp.comcast.net) as my ISP blocks port 25?

---

### Post by ian dobson on 2010-01-26
Hi,

Have a look at [http://www.linuxquestions.org/questions/linux-software-2/postfix-to-relay-through-my-isps-smtp-with-no-tls-problem-519903/](http://www.linuxquestions.org/questions/linux-software-2/postfix-to-relay-through-my-isps-smtp-with-no-tls-problem-519903/) you need to setup postfix to use a "smarthost".

Regards
Ian Dobson

---

### Post by trentscott4 on 2010-01-26
And is there an easy way to install/configure a web server solely from Webmin?

---

