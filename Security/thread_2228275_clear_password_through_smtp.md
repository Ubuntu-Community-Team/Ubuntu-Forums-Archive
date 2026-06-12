---
title: "clear password through smtp?"
date: 2014-06-06
forum: Security
---

### Post by Dragon777 on 2014-06-06
Hi, 

I've installed postfix on my server and now I can receive and send mails from my client.

The problem I have is that I configured thunderbird like this with "Authentication method: Normal password". If I try "encrypted password" it does not work. Does that mean that my password is going from the client to the server as plain text? If thats the case, how can I change that?

Thanks


[IMG]http://s21.postimg.org/vamjps9qf/Capture_d_e_cran_2014_06_06_a_19_16_56.png[/IMG]

---

### Post by CharlesA on 2014-06-07
You are using STARTTLS, so it will not be sending the password in the clear, even if you select "normal password"

---

### Post by SeijiSensei on 2014-06-09
Is this a home or office network?  How likely is it that someone will be running software on your network to sniff passwords?

I have no password or encryption on the SMTP server in my office.  The only ones connecting to it are me and my daughter, and we know each others' passwords already!

---

