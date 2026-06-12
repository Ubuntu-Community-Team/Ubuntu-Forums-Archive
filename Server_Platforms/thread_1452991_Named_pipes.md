---
title: "Named pipes"
date: 2010-04-12
forum: Server Platforms
---

### Post by dado prso on 2010-04-12
Hello,

Does anyone have an idea of how I could save all of the mail sendmail processes to a named pipe?

Thanks,
Dado

---

### Post by dado prso on 2010-04-13
bump

---

### Post by Bachstelze on 2010-04-13
You can do that with a simple procmail rule.

---

### Post by KB1JWQ on 2010-04-13
In postfix this can be done via transport_maps.

Not a clue how Sendmail handles this;  might look into how you'd pass messages to procmail and alter accordingly?

---

### Post by dado prso on 2010-04-13
> **Bachstelze said:**
> You can do that with a simple procmail rule.

Can I just add a new mailer under MAILER_DEFINITIONS?

maybe 

MAILER('Named Pipe', 'location') 

?
Thanks,
Dado

---

### Post by dado prso on 2010-04-14
bump

---

