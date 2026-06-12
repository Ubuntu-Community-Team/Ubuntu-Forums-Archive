---
title: "PHPMailer smtp vs sendmail"
date: 2012-01-18
forum: Server Platforms
---

### Post by mlinux on 2012-01-18
In PHPMailer, when I choose using sendmail to send html email $message, the message ended up with extra or missing characters. However, when I choose using smtp with the same $message, no problem at all.

The suspect is "sendmail". Anyone can confirm?

---

### Post by deonis on 2012-01-18
not sure ... it will probably depend on characters, but sendmail works fine with me ... I am using Ubuntu 11.10

---

