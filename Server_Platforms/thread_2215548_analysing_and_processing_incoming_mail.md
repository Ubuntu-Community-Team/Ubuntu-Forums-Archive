---
title: "analysing and processing incoming mail"
date: 2014-04-07
forum: Server Platforms
---

### Post by frankerooney on 2014-04-07
Hi All,
  Does anyone know of a system with a method for applying filtering rules to incoming mail from a mailbox (using imap or pop3, OR native exchange protocols since our mail system is backended by exchange 2003 but this is heading away into tricky territory afaik with linux). I want to watch incoming subject titles or mail content and maybe tuck away the information into a mysql database, run a script or similar. It's all internal to our infrastructure so security isn't a huge concern.
Thanks
Andy

---

### Post by nerdtron on 2014-04-07
Emails in Linux are mostly just text files. You can try running the "grep" on the email bodies to see if it catches what you want to see.

---

### Post by SeijiSensei on 2014-04-07
**Procmail** is the best solution for processing mail based on message characteristics. See [http://linux.die.net/man/5/procmailrc](http://linux.die.net/man/5/procmailrc) and [http://linux.die.net/man/5/procmailex](http://linux.die.net/man/5/procmailex) for details.

---

