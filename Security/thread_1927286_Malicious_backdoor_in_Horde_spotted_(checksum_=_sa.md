---
title: "Malicious backdoor in Horde spotted (checksum = safe?)"
date: 2012-02-17
forum: Security
---

### Post by nrundy on 2012-02-17
Saw this article on Ars: [http://arstechnica.com/business/news/2012/02/malicious-backdoor-in-open-source-messaging-apps-not-spotted-for-4-months.ars](http://arstechnica.com/business/news/2012/02/malicious-backdoor-in-open-source-messaging-apps-not-spotted-for-4-months.ars)

If someone downloaded the messaging app, but hashed it and then compared the hash to what the creators listed as the "proper hash" it would have showed up as different, right? Or in other words, users could have discovered that the app was modified from the creators original version because the checksums would have been different?

Would comparing checksums have alerted users to this messaging app being tainted?

---

### Post by Dangertux on 2012-02-17
It depends on when the checksum was created . If it was created prior to the injection of the backdoor yes. if not, than no.

---

### Post by nrundy on 2012-02-17
> **Dangertux said:**
> It depends on when the checksum was created . If it was created prior to the injection of the backdoor yes. if not, than no.

Yeah. But when you read the article it sounds like the checksum would have been created before the malware infected the code.

---

