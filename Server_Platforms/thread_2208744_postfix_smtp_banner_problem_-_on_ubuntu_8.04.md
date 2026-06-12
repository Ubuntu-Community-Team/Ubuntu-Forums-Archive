---
title: "postfix smtp banner problem - on ubuntu 8.04"
date: 2014-03-02
forum: Server Platforms
---

### Post by Reza_Zand on 2014-03-02
Hi
I'm using ubuntu 8.04 server and use postfix. my smtp banner always show:

220 ***************

but I check main.cf file and this line is exist:

smtpd_banner = $myhostname ESMTP $mail_name

how can i fix this?

---

### Post by Reza_Zand on 2014-03-02
I found how solve this problem myself.
my server is behind the cisco asa firewall.
global policy ESMTP inspection prevent smtp banner and other command in "telnet mail.example.com 25".
for solve this we must disable esmtp inspection  in global policy of  firewall and allow TLS ESMTP in another policy.

---

