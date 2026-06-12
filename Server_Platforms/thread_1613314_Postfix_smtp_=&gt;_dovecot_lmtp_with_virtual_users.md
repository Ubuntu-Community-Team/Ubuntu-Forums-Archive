---
title: "Postfix smtp =&gt; dovecot lmtp with virtual users"
date: 2010-11-04
forum: Server Platforms
---

### Post by Fragzero on 2010-11-04
Hello


I'm trying to setup a postfix smtp server which uses dovecot 2.0 as it's internal lmtp. 


What i've used trying to meet the requirements

=> Dovecot wiki (2 since i use version 2)
=> postfix how to's
=> and offcourse our endless friend google.

What i tried so far (which i think is correct)

[http://wiki2.dovecot.org/HowTo/PostfixDovecotLMTP](http://wiki2.dovecot.org/HowTo/PostfixDovecotLMTP)

Enable lmtp, create the unix socket and configure postfix to use lmtp-socket

problem here is quite easy => mails for my user accounts still get delivered after stopping dovecot, it's not using it :s 

Any idea what i'm doing wrong??



2)

At a certain point i had it working (with very very messy config files) but then i had problems with the virtual users. 

Suggestions about what i should use?There is so much choice it's really confusing.

What i want to achieve: server recieves a mail user1@domain and sends it to /var/vmail/user1/ using the maildir format. ofc i want to keep track of the users which can recieve mail on the server (not just every possible XXX@domain). Any suggestions?

I had it working postfix => dovecot but my config files were so bad (i tinkered everywhere) i decided to purge and startover).

==

And before i get the remark, yes this is an assignement i got at school. The assignement however was very unclear and we never had any explanation about it, this was on purpose so we would learn more by figuring it out ourselfs. They encourage reading the documentation and even asking question in communities like this.

---

