---
title: "SMS on Aquarius 4.5 Ubuntu shows wrong contact name"
date: 2015-04-20
forum: Ubuntu Phone and Tablet
---

### Post by rolandbreedveld on 2015-04-20
Messages client shows wrong contact names from my address-book on incoming SMS messages which are not in my address-book
SMS messages from people which are present, are showing the right names.

Running Ubuntu 14.10-r21 on Aquarius 4.5 Ubuntu Edition

---

### Post by _march_ on 2015-04-20
Hi :)

I'd the same issue. Did you also import your contacs via vcf-file and added later contacts via your phone? in my case it helped to delete the contact I'd added manually. Now everything works fine. That seems to be a bug.

---

### Post by rolandbreedveld on 2015-04-21
Hi March
no manually added contacts, I imported all contacts via google-contacts, for unknown contacts in SMS, it take one of the first contacts,
after deleting that contact, it takes the next, and so on.
for all SMS-es which are not in my address list it always takes the same (wrong) contact.

---

### Post by _march_ on 2015-04-23
Hi,
I've opened a bug report on [launchpad.net]("https://bugs.launchpad.net/address-book-app/+bug/1447700"). Perhaps you can add further informations and also confirm that you're affected, too.

Regards

---

### Post by rolandbreedveld on 2015-04-25
Thanxz march, info is updated

---

### Post by nogmo on 2015-05-15
I had this bug but when I looked at the contact that was affected there  was an empty phone field. When the empty phone field was deleted all the  affected sms immediately corrected e.g. showed the name of the courier,  shop etc (don't know what you call it when a company can display their  name automatically) but previous to this correction I would not have  been able to reply to an unknown sms as the number displayed would have  been that of the affected contact.
I did not receive any sms from "normal" unknown contacts - normal people who don't automatically display their name.
I had added all my contacts manually.
hth
(have also added this to the launchpad bug page)

---

