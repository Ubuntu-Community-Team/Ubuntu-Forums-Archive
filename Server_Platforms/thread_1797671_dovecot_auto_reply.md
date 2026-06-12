---
title: "dovecot auto reply"
date: 2011-07-05
forum: Server Platforms
---

### Post by Jay89 on 2011-07-05
Hey,
   Does anyone know of a way to configure dovecot for Auto-Reply Out of Office messages? Preferably one that clients can do on their own from their PCs but any suggestion would be appreciated. 

Thank You

---

### Post by SeijiSensei on 2011-07-05
> **Jay89 said:**
> Hey,
   Does anyone know of a way to configure dovecot for Auto-Reply Out of Office messages? Preferably one that clients can do on their own from their PCs but any suggestion would be appreciated. 

Thank You

I ended up writing one from scratch for a client.  People enter the start and end dates of the vacation and an auto-reply message in a web form; the information is stored in a PostgreSQL database.  Each night a script runs from cron that searches for new or expiring vacations.  When a vacation begins, I activate a .forward file that sends the out-of-office message using the "[vacation]("http://packages.ubuntu.com/lucid/vacation")" program.  When the vacation ends, the .forward file is deleted.

**procmail** can be used as an simple auto-responder.  See "[man procmailex]("http://www.cims.nyu.edu/cgi-comment/man.cgi?section=5&topic=procmailex")" for details.

---

