---
title: "Postfix + Courier"
date: 2006-02-18
forum: Server Platforms
---

### Post by alamba on 2006-02-18
Hi,

I'm looking at building an email server for a client, the requirements are must have POP3 and webmail. I'm considering postfix and courier for this.

Any comments? Would you suggest this or another email smtp/pop3 pair?Could someone post a configuration steps/howto url?

Akshay

---

### Post by heimo on 2006-02-18
**[[FONT=Arial][SIZE=1] 		Ubuntu + Postfix + Courier IMAP + MySQL  		+ Amavisd-new + SpamAssassin + ClamAV  		+ SASL + TLS + SquirrelMail + Postgrey[/SIZE][/FONT]]("http://flurdy.com/docs/postfix/")**

---

### Post by alamba on 2006-02-18
Thanks heimo. Just wondering if it's possible to use the OS users for mail sending and delivery rather than sql database. Since this is a dedicated server I'll rather not use virtual domains.

A

---

### Post by jinacio on 2006-02-18
look at [Dovecot]("http://www.dovecot.org/") for pop3/imap, its extremely easy to install and configure.

i'm not familiar with any webmail interface but i am pretty sure there are many to choose from.

---

### Post by alamba on 2006-02-19
Thanks. Davecot does make me rethink courier.

A

---

