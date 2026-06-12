---
title: "[SOLVED] denyhosts smtp problem"
date: 2008-08-04
forum: Server Platforms
---

### Post by skep on 2008-08-04
Hello!

I'm using ubuntu 8.04 server edition with working exim4 and mailx. Now I have installed denyhosts, which is working fine (does sync and does block & purge ip's), except it doesn't send me an email with new blocked ip's.

The part in my denyhost config is:
ADMIN_EMAIL = [email]skep@xxx.xxx[/email]
SMTP_HOST = mail.xxx.xxx
SMTP_PORT = 25
SMTP_USERNAME=xxx
SMTP_PASSWORD=xxx

The data for smtp-host/port ect. is correct and just to be sure i've tried with and without smtp-authenticaion as well as TLS and SSL (different ports) but no luck, not even a hint in the logs why it doesn't work. So do i miss something here?

---

### Post by skep on 2008-08-05
Problem solved!

After switching from exim4 to postfix all worked out fine.

---

### Post by hyper_ch on 2008-08-05
btw, you know what you can configure denyhosts to drop all connections to any port from a banned IP?

---

### Post by gtdaqua on 2008-08-05
> **hyper_ch said:**
> btw, you know what you can configure denyhosts to drop all connections to any port from a banned IP?

are you asking or suggesting? I wud be interested to know how to block all connections from a banned IP.

---

### Post by hyper_ch on 2008-08-05
edit the denyhost config. Right now it's set to SSH and you can set it to ALL. ;)

---

### Post by gtdaqua on 2008-08-06
Thanks, will try.

---

