---
title: "Sending emails to mail server IP"
date: 2012-01-07
forum: The Cafe
---

### Post by Lr103 on 2012-01-07
Hello,

Here's a question that has bugged me for a while. If I set up a cPanel hosting account, can I send an email to [cPanelUsername]@[ServerIP] and pick it up at the other end?

Example: If my username is pklsmnei and the IP of the server I am hosted on is 176.31.147.43, can I send mail to pklsmnei@176.31.147.43? How would I read it? (176.31.147.43:2095 rejects as invalid my login attempts as pklsmnei@176.31.147.43)

---

### Post by Bachstelze on 2012-01-07
You Can't Do That™. E-mail and DNS are closely related, e-mail can only be sent to a name, not to an IP address.

---

### Post by whiskeylover on 2012-01-07
Email needs special DNS entries called MX records. That is why you can point your MX records to a different host and have your email handled by it. For example, create MX records pointing to google and read all your email using google apps.

---

### Post by Lr103 on 2012-01-07
> **Bachstelze said:**
> You Can't Do That™. E-mail and DNS are closely related, e-mail can only be sent to a name, not to an IP address.

[http://www.youtube.com/watch?v=SvlEWr8be60](http://www.youtube.com/watch?v=SvlEWr8be60)

---

