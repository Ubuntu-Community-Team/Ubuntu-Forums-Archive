---
title: "Round cube error after restart dovecot"
date: 2013-07-18
forum: Server Platforms
---

### Post by mirceabondar on 2013-07-18
Why roundcube return "connection server storage failed" after restart dovecot? Before restart dovecot roundcube and thunderbird work fine..

---

### Post by nerdtron on 2013-07-18
What have you done before restarting the dovecot service? Also, did the dovecot service restarted successfully?
Usually, that error comes when there are authentication or permission problems.

---

### Post by mirceabondar on 2013-07-19
Thx for reply..Solved: A few days ago, for more php security i added fsock in disabled_extension..

---

