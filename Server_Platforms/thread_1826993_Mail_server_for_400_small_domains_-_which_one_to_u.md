---
title: "Mail server for 400 small domains - which one to use?"
date: 2011-08-17
forum: Server Platforms
---

### Post by joker535 on 2011-08-17
I am going to try and replace our crappy Windows/imail server with a new ubuntu 10.04 LTS based machine. It will end up with about 400 domains on it with around 3000 users total. 96% of the domains have very light use. 4% of the domains have heavy use but do not send any bulk mail. 

Can someone here recommend a mail server software package that would be easy to administrate and easy to backup/replicate? All we need is POP with webmail. We do not need IMAP or want any group/collaborative functions. 

What do you usually use for anti-spam on a linux mail server? We want to keep it all open source if possible.

For hardware we are looking at an HP DL360 G5 with dual Xeons, 4G of ram, and the P400 controller with 6 SAS 15k drives. Do you think a server like this will be able to handle the mail on linux? Volume is around 400k messages a day inbound with about 10% being legit/90% being spam. The server will be dedicated to mail hosting and will not host websites.

Any help/advice/direction would be appreciated.

Thanks

Bob

---

### Post by dinu90 on 2011-08-17
Hi,

I would recommend to use postfix with postfixadmin as the web interface. You can use MySQL as backend for storing the virtual domains/users. It is very easy to manage/replicate/backup.

A good anti-spam would be MailScanner with SpamAssassin, ClamAV, dcc, pyzor, razor2, other plugins. You can use MailWatch as the MailScanner web interface.

Not sure about if the server will be able to handle the load though.

Let me know if you have any questions

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

