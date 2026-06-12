---
title: "Where can I find the sms data base on my Ubuntu phone."
date: 2016-06-26
forum: Ubuntu Phone and Tablet
---

### Post by kj.curry on 2016-06-26
Greetings,
 I recently acquired my MX Pro5 Ubuntu Edition phone. (Ubuntu 15.04 (OTA-11)). I'm new to the Ubuntu Touch interface / apps etc. I'm not new to Ubuntu Linux. I need to retrieve / copy the sms database from the phone to my PC (both Linux w VMware (Windows)), where I can work with the db. Further are there any tools I can load up to review and dissect the sms db.

I thank you in advance for your considered replies.

Cheers

---

### Post by donquichot2016 on 2016-06-27
The SMS messages and call logs are stored in **.local/share/history-service/history.sqlite** . You can use the sqlite3 program to view/edit it:
sqlite3 .local/share/history-service/history.sqlite

You can find a bit more info in this book, but database structure should be fairly self-explanatory:
[https://www.gitbook.com/download/pdf/book/gurucubano/bq-aquaris-e-4-5-ubuntu-phone?lang=en](https://www.gitbook.com/download/pdf/book/gurucubano/bq-aquaris-e-4-5-ubuntu-phone?lang=en)

---

### Post by kj.curry on 2016-06-27
[SIZE=3][COLOR=#0000cd]**Awesome **[/COLOR][/SIZE]- Thanks for both!
Kevin :D

---

