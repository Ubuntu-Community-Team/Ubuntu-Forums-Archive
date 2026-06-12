---
title: "sending email recommendation"
date: 2012-09-05
forum: Ubuntu Application Development
---

### Post by jochesfor on 2012-09-05
Hello everybody.

I'm developing an application and i need to send emails after processing some info, that info it's stored in a mysql table and i need to check that info every 1 min, asking for new records with sent status in 0 for unsent messages, i only need to know what's the better, faster and optimized way to send several emails.

I wrote a java program and works fine, but i'm breaking my head thinking in a better way to do it.

maybe cron task?

thank you all.

---

### Post by einonm on 2012-09-24
Although you don't describe the code in great detail, it sounds like you're implementing a poll mechanism for sending emails. A more efficient mechanism would be event based, where the email would get sent when an unsent message is encountered during processing.

Providing the code would be much more helpful to getting advice.

---

