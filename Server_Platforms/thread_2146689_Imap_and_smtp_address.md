---
title: "Imap and smtp address"
date: 2013-05-19
forum: Server Platforms
---

### Post by mirceabondar on 2013-05-19
Hy. My mx server have address mail.andortipo.ro. When i try to login my mail account in thunderbird, the imap server and smtp have this address: mail.andortipo.ro. How to change this to imap.andortipo.ro and smtp.andortipo.ro (thunderbird search automaticaly for configuration).. I have postfix, dovecot with mysql.

---

### Post by CharlesA on 2013-05-19
Do you really need to change it to whatever defaults Thunderbird uses? If it works when you use mail.andortipo.ro, then use it. :)

I've been using mail.charlesa.net for a long time even though thunderbird said the defaults were different.

---

### Post by mirceabondar on 2013-05-20
problem resolve...i added two a records...imap and smtp into zone file. thx for help

---

